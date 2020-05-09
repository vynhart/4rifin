---
layout: post
title:  "Authentication in Laravel"
categories: laravel
date:   2020-05-09 19:00:00 +0700
permalink: /authentication-in-laravel/
---
Authentication in laravel is done in many ways, here is some of the possible way to do the authentication:

# Authentication in Controller

The most common method of doing the authentication will probably by handles it via controller. To do that, the first thing you need to do is to add the `auth` middleware into controller's constructor. for example:

```
class AddressController extends Controller
{
    public function __construct() {
        $this->middleware('auth');
    }
    
    .....
```

by doing this, any non-logged in access into your controller will automatically be redirected to login page.

# Conditional Authorization

In the real world, you will want to restrict access to resources so that it can only be accessed to users that's owned it. For example, address A should be available to be accessed by user X.

Laravel serves several ways to enable this authorization

## Authorize user in controller's method

To do the authorization checking directly in controller's method, you can do this simply by using laravel `abort` helper.

```
    public function show(Address $address)
    {
        if($address->owner_id !== auth()-user_id()) {
            abort(403);
        }
        
        // your logic
    }
```

or, using `abort_if`

```
    public function show(Address $address)
    {
        abort_if($address->owner_id !== auth()-user_id());
        
        // your logic
    }
```

## Authorize user via policy

Another method you can use to specify authorization is via policy. To do that, you can make a new policy that's corresponding to certain model. For example, if you want to specify policy to `Address` model, then you can make it via php artisan command:

```
php artisan make:policy AddressPolicy --model Address
```

by running that command now you should have a new file in `App/Policies/AddressPolicy.php` with a predefined methods. Here is the content of the file should looked like:

```
<?php

namespace App\Policies;

use App\User;
use App\Address;
use Illuminate\Auth\Access\HandlesAuthorization;

class AddressPolicy
{
    .....
```

In that file you're supposed to see all the functions with similar name with the function in your controller. This is intended as you're expected to have a unique policy for each of your controller's function.

For example, to give an authorization check in edit method of your AddressController, so that the Address that can be edited is only the Address that's owned by the corresponding user, you can do this.

```
class AddressPolicy
{
    public function edit(User $user, Address $address)
    {
        return $address->owner_id === $user->id
    }
```

and then, in your AddressController now you can use the `authorize` method like following:

```
class AddressController
{
    .....
    
    public function edit(Address $address)
    {
        $this->authorize('edit', $address);
    }
}
```

The `authorize('edit', $address')` means that you use the `edit` method in your AddressPolicy (determined by $address variable you passed in the second parameter) to determine if user can access this particular address or not.
