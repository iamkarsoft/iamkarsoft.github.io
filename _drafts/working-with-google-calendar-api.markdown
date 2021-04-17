---
title: working with google calendar api
layout: post
date: 
categories: tag tag
---


### Setting up relationships

#### The  Models  

<pre class="language-">
    <code class="language-">
        # user model
        class User extends Authenticatable
        {
            // ...
            public function googleAccounts()
            {
                return $this->hasMany(GoogleAccount::class);
            }
        }

        # The Google Account Model
        class GoogleAccount extends Model
{
    protected $fillable = ['google_id', 'name', 'token'];
    protected $casts = ['token' => 'json'];

    public function user()
    {
        return $this->belongsTo(User::class);
    }

    public function calendars()
    {
        return $this->hasMany(Calendar::class);
    }
}   

    # The calendar model
    class Calendar extends Model
{
    protected $fillable = ['google_id', 'name', 'color', 'timezone'];

    public function googleAccount()
    {
        return $this->belongsTo(GoogleAccount::class);
    }

    public function events()
    {
        return $this->hasMany(Event::class);
    }
}

# the event model
class Event extends Model
{
    protected $with = ['calendar'];
    protected $fillable = ['google_id', 'name', 'description', 'allday', 'started_at', 'ended_at'];

    public function calendar()
    {
        return $this->belongsTo(Calendar::class);
    }

    public function getStartedAtAttribute($start)
    {
        return $this->asDateTime($start)->setTimezone($this->calendar->timezone);
    }

    public function getEndedAtAttribute($end)
    {
        return $this->asDateTime($end)->setTimezone($this->calendar->timezone);
    }

    public function getDurationAttribute()
    {
        return $this->started_at->diffForHumans($this->ended_at, true);
    }
}

    </code>
</pre>



### The Google Class

```
<?php

namespace App\Services;

class Google {
    protected $client;

    public function __call($method, $args) {
        if (!method_exists($this->client, $method)) {
            throw new \Exception("Call to undefined method '{$method}'");
        }

        return call_user_func_array([$this->client, $method], $args);
    }

    function __construct() {
        $client = new \Google_Client();
        $client->setClientId(config('services.google.client_id'));
        $client->setClientSecret(config('services.google.client_secret'));
        $client->setRedirectUri(config('services.google.redirect_uri'));
        $client->setScopes(config('services.google.scopes'));
        $client->setApprovalPrompt(config('services.google.approval_prompt'));
        $client->setAccessType(config('services.google.access_type'));
        $client->setIncludeGrantedScopes(config('services.google.include_granted_scopes'));
        $this->client = $client;
    }

    public function service($service) {
        $classname = "Google_Service_$service";

        return new $classname($this->client);
    }

    public function connectUsing($token) {
        $this->client->setAccessToken($token);

        return $this;
    }

    public function revokeToken($token = null) {
        $token = $token ?? $this->client->getAccessToken();

        return $this->client->revokeToken($token);
    }

    
}
```

### Google as a service

<pre class="language-">
    <code class="language-">
        //config/services.php
        return [
    // ...
    
    'google' => [
        // Our Google API credentials.
        'client_id' => env('GOOGLE_CLIENT_ID'),
        'client_secret' => env('GOOGLE_CLIENT_SECRET'),
        
        // The URL to redirect to after the OAuth process.
        'redirect_uri' => env('GOOGLE_REDIRECT_URI'),
        
        // The URL that listens to Google webhook notifications (Part 3).
        'webhook_uri' => env('GOOGLE_WEBHOOK_URI'),
        
        // Let the user know what we will be using from his Google account.
        'scopes' => [
            // Getting access to the user's email.
            \Google_Service_Oauth2::USERINFO_EMAIL,
            
            // Managing the user's calendars and events.
            \Google_Service_Calendar::CALENDAR,
        ],
        
        // Enables automatic token refresh.
        'approval_prompt' => 'force',
        'access_type' => 'offline',
        
        // Enables incremental scopes (useful if in the future we need access to another type of data).
        'include_granted_scopes' => true,
    ],
];

    </code>
</pre>

  
### Connecting to google account
  
<pre class="language-php">
    <code class="language-php">
         public function index()
    {
        return view('accounts', [
            'accounts' => auth()->user()->googleAccounts,
        ]);
    }
    </code>
</pre>
  
### Redirecting google to consent screen
  
<pre class="language-php">
    <code class="language-php">
        return redirect($google->createAuthUrl());

         if (! $request->has('code')) {
        // Send the user to the OAuth consent screen.
        return redirect($google->createAuthUrl());

         // Do something with $request->get('code');
    // ...

    // Return to the account page.
    return redirect()->route('google.index');
    }
    </code>
</pre>

  
### Deleting a google account

<pre class="language-php">
    <code class="language-php">
        public function destroy(GoogleAccount $googleAccount)
{
    $googleAccount->delete();

    return redirect()->back();
}
    </code>
</pre>
   
### Revoking google token  

Telling google we won't be using the token associated

<pre class="language-php">
    <code class="language-php">
        class Google
{
    //...
    
    public function revokeToken($token = null)
    {
        $token = $token ?? $this->client->getAccessToken();

        return $this->client->revokeToken($token);
    }
}

public function destroy(GoogleAccount $googleAccount, Google $google)
{
    $googleAccount->delete();

    // Event though it has been deleted from our database,
    // we still have access to $googleAccount as an object in memory.
    $google->revokeToken($googleAccount->token);

    return redirect()->back();
}
    </code>
</pre>