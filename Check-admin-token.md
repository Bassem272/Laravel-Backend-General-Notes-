Yes, the approach I provided can also be used to check if a user is an admin. To perform an admin check, you would typically have a role or attribute in the user model that specifies the user's role (e.g., "admin" or "customer"). Here's how you can adapt the code to perform an admin check:

Assuming you have a `role` attribute in your `User` model:

```php
use Illuminate\Http\Request;
use App\Http\Controllers\Controller;
use App\Models\User;

class YourController extends Controller
{
    public function someMethod(Request $request)
    {
        $token = str_replace('Bearer ', '', $request->header('Authorization'));
        $user = User::where('api_token', $token)->first();

        if ($user && hash_equals($user->api_token, $token)) {
            // Token is valid, and the user is authenticated

            // Check if the user has the "admin" role
            if ($user->role === 'admin') {
                // User is an admin, you can perform admin-specific actions
            } else {
                // User is not an admin, you can return an unauthorized response
                return response()->json(['error' => 'Unauthorized'], 403);
            }
        } else {
            // Token is invalid or user not found
            return response()->json(['error' => 'Unauthorized'], 401);
        }

        // Your code here...

        return response()->json(['message' => 'Success'], 200);
    }
}
```

In this example, if the user has the role "admin," you can perform admin-specific actions, and if they don't have the "admin" role, you can return a 403 Forbidden response to indicate that they are not authorized to perform admin actions.
