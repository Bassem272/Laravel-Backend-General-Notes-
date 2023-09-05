In Laravel, you can extract the token and other headers from the HTTP request using the `request()` object, which is an instance of the `Illuminate\Http\Request` class. Here's how you can extract the token and the role from the request headers:

1. **Extracting the Authorization Token**:

   To extract the authorization token (usually in Bearer Token format) from the request headers, you can use the `header()` method on the `Request` object:

   ```php
   $token = $request->header('Authorization');
   ```

   This will give you the entire authorization header, including the "Bearer " prefix and the token itself. If you want to extract just the token without the "Bearer " prefix, you can further manipulate the string, like so:

   ```php
   $authorizationHeader = $request->header('Authorization');
   $token = str_replace('Bearer ', '', $authorizationHeader);
   ```

2. **Extracting the User Role**:

   To extract the user role from a custom header (e.g., `X-User-Role`) in the request headers, you can use the `header()` method similarly:

   ```php
   $userRole = $request->header('X-User-Role');
   ```

   This code will extract the value of the `X-User-Role` header from the request headers.

Once you've extracted the token and user role, you can use them in your authentication and authorization logic. For example, you can use Laravel's built-in middleware like `auth` and create custom middleware to check the token and role before allowing access to specific routes or controller methods.
