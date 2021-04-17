---
title: Laravel validation rules
layout: post
date: 
categories: laravel tips
---

### Laravel validation rules

<pre class="language-php">
    <code class="language-php">
         $request->validate([
                'name' => 'required',

                # validation for phone
                'phone' => 'required|regex:/^([0-9\s\-\+\(\)]*)$/|min:10', 
                'phone' => 'required|digits:10',

                #validation for email
                'email' => 'required|email|unique:users'

                # Checking if field value not equal to another field
                'primaty_id' => 'required',
                'secondary_id' => 'required|different:primaty_id'

                #validating time
                'time_start' => 'date_format:H:i',
                'time_end' => 'date_format:H:i|after:time_start',
            ]);
    </code>
</pre>
