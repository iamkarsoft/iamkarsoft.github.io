

### 



```
public function redirect($service, Request $request) {
        return Socialite::driver($service)->redirect();
    }

    public function callback($service, Request $request) {
        $serviceUser = Socialite::driver($service)->user();
      
        $user = User::where('provider_id', $serviceUser->getId())->first();

        if (!$user):
         $user = User::create([
             'email' => $githubUser->getEmail(),
             'name' => $githubUser->getName(),
             'provider_id' => $githubUser->getId(),
         ]);
        endif;

        $user = $this->getExistingUser($serviceUser, $service);

        //login user
        auth()->login($user, true);
        return redirect('dashboard');
    }

```