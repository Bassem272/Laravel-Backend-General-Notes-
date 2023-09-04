To establish different types of relationships in your database tables (One-to-Many, One-to-One, and Many-to-Many) using Laravel migrations, you'll need to define foreign keys and pivot tables where necessary. Here's how you can create these relationships in your database tables:

1. **One-to-Many Relationship in Tables:**

   For a one-to-many relationship, you typically have a foreign key in the child table that references the primary key of the parent table. Let's consider an example where a "User" can have many "Orders":

   ```php
   // Create the Users table migration
   Schema::create('users', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('name');
       $table->string('email')->unique();
       $table->timestamps();
   });

   // Create the Orders table migration with a foreign key
   Schema::create('orders', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->unsignedBigInteger('user_id'); // Foreign key referencing 'users' table
       $table->timestamps();

       // Define the foreign key constraint
       $table->foreign('user_id')->references('id')->on('users');
   });
   ```

2. **One-to-One Relationship in Tables:**

   In a one-to-one relationship, one table's primary key directly references another table's primary key. Let's consider an example where each "User" has one "Profile":

   ```php
   // Create the Users table migration
   Schema::create('users', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('name');
       $table->string('email')->unique();
       $table->timestamps();
   });

   // Create the Profiles table migration with a foreign key
   Schema::create('profiles', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->unsignedBigInteger('user_id'); // Foreign key referencing 'users' table
       $table->timestamps();

       // Define the foreign key constraint
       $table->foreign('user_id')->references('id')->on('users');
   });
   ```

3. **Many-to-Many Relationship in Tables:**

   For a many-to-many relationship, you need an intermediate pivot table that connects two tables. Let's consider an example where "Users" can have many "Products" through a "Cart" table:

   ```php
   // Create the Users table migration
   Schema::create('users', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('name');
       $table->string('email')->unique();
       $table->timestamps();
   });

   // Create the Products table migration
   Schema::create('products', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('name');
       $table->decimal('price', 10, 2);
       $table->timestamps();
   });

   // Create the Cart (pivot) table migration
   Schema::create('cart', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->unsignedBigInteger('user_id'); // Foreign key referencing 'users' table
       $table->unsignedBigInteger('product_id'); // Foreign key referencing 'products' table
       $table->integer('quantity');
       $table->timestamps();

       // Define the foreign key constraints
       $table->foreign('user_id')->references('id')->on('users');
       $table->foreign('product_id')->references('id')->on('products');
   });
   ```

With these database migrations, you've defined the necessary foreign key constraints to establish the desired relationships in your tables. Laravel will use these foreign keys to maintain referential integrity when working with Eloquent models.
