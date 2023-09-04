In Laravel's Eloquent ORM, you can define different types of relationships between your database tables using methods provided by the Eloquent models. Here's how you can create each type of relationship: 

1. **One-to-Many Relationship:**
   
   In a one-to-many relationship, one record in the parent table (e.g., `User`) is associated with many records in the child table (e.g., `Order`). To define this relationship:

   - In the parent model (`User`), use the `hasMany` method:

   ```php
   class User extends Model {
       public function orders() {
           return $this->hasMany(Order::class);
       }
   }
   ```

   - In the child model (`Order`), use the `belongsTo` method:

   ```php
   class Order extends Model {
       public function user() {
           return $this->belongsTo(User::class);
       }
   }
   ```

2. **One-to-One Relationship:**

   In a one-to-one relationship, one record in the parent table (e.g., `User`) is associated with one record in the child table (e.g., `Profile`). To define this relationship:

   - In the parent model (`User`), use the `hasOne` method:

   ```php
   class User extends Model {
       public function profile() {
           return $this->hasOne(Profile::class);
       }
   }
   ```

   - In the child model (`Profile`), use the `belongsTo` method:

   ```php
   class Profile extends Model {
       public function user() {
           return $this->belongsTo(User::class);
       }
   }
   ```

3. **Many-to-Many Relationship:**

   In a many-to-many relationship, records in one table (e.g., `User`) are associated with multiple records in another table (e.g., `Product`) through an intermediate pivot table (e.g., `Cart`). To define this relationship:

   - In both models (`User` and `Product`), use the `belongsToMany` method to define the relationship:

   ```php
   class User extends Model {
       public function products() {
           return $this->belongsToMany(Product::class, 'cart')
               ->withPivot('quantity'); // If you need to store additional data in the pivot table
       }
   }
   ```

   ```php
   class Product extends Model {
       public function users() {
           return $this->belongsToMany(User::class, 'cart')
               ->withPivot('quantity'); // If you need to store additional data in the pivot table
       }
   }
   ```

   Here, `'cart'` is the name of the pivot table that links `User` and `Product`. The `withPivot` method is used to specify any additional columns you want to access in the pivot table.

Once you've defined these relationships, you can easily query and retrieve related data using Laravel's Eloquent ORM methods. These relationships make it convenient to work with complex data structures in your application.
