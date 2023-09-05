The reason the `AdminMiddleware` is working when you try to register a new user is that you have applied this middleware to the entire 'api' middleware group in your `Kernel.php` file:

```php
protected $middlewareGroups = [
    'api' => [
        ...
        \App\Http\Middleware\AdminMiddleware::class,
        \App\Http\Middleware\CustomerMiddleware::class,
    ],
];
```

This means that any request to routes defined in the 'api' group will go through both the `AdminMiddleware` and `CustomerMiddleware`, including the registration route.

If you want these middlewares to only apply to specific routes, you should move their assignment from the `'api'` middleware group to the individual routes where they should be used. For example:

```php
Route::middleware('auth:sanctum')->group(function () {
    // Protected routes that require authentication
    Route::middleware('admin')->group(function () {
        // Routes for admin-only access
    });

    Route::middleware('customer')->group(function () {
        // Routes for customer-only access
    });

    // Other protected routes
});
```

This way, you can apply the `AdminMiddleware` and `CustomerMiddleware` only to the routes where they are relevant, and the registration route will not be affected by them.

Here's how you can modify your routes in the `api.php` file to achieve this:

```php
Route::middleware('auth:sanctum')->get('/user', function (Request $request) {
    return $request->user();
});

// Routes for admin-only access
Route::middleware('auth:sanctum', 'admin')->group(function () {
    // Define your admin-only routes here
});

// Routes for customer-only access
Route::middleware('auth:sanctum', 'customer')->group(function () {
    // Define your customer-only routes here
});

// Other protected routes
Route::post('/tokens/create', function (Request $request) {
    $token = $request->user()->createToken($request->token_name);
    return ['token' => $token->plainTextToken];
});
```

With this structure, the `AdminMiddleware` and `CustomerMiddleware` will only apply to the routes you specify, and the registration route remains accessible to all users.
