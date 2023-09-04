Sure, let's illustrate the differences between one-to-one and one-to-many relationships in Laravel using code examples.

**One-to-One Relationship in Laravel:**

Let's consider an example where each "User" has one "Profile." This is a one-to-one relationship where a user has a single associated profile.

1. **Migrations:**

   In your migrations, you can set up the tables like this:

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
       $table->unsignedBigInteger('user_id')->unique(); // Foreign key referencing 'users' table
       $table->timestamps();

       // Define the foreign key constraint
       $table->foreign('user_id')->references('id')->on('users');
   });
   ```

2. **Eloquent Models:**

   In your Eloquent models, you can define the one-to-one relationship like this:

   ```php
   // User model
   class User extends Model {
       public function profile() {
           return $this->hasOne(Profile::class);
       }
   }

   // Profile model
   class Profile extends Model {
       public function user() {
           return $this->belongsTo(User::class);
       }
   }
   ```

   Here, the `hasOne` method is used in the `User` model to define the relationship with the `Profile` model, and the `belongsTo` method is used in the `Profile` model to specify the reverse relationship.

**One-to-Many Relationship in Laravel:**

Let's consider an example where each "User" can have many "Posts." This is a one-to-many relationship where a user can have multiple associated posts.

1. **Migrations:**

   In your migrations, you can set up the tables like this:

   ```php
   // Create the Users table migration
   Schema::create('users', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('name');
       $table->string('email')->unique();
       $table->timestamps();
   });

   // Create the Posts table migration with a foreign key
   Schema::create('posts', function (Blueprint $table) {
       $table->id(); // Primary key
       $table->string('title');
       $table->text('content');
       $table->unsignedBigInteger('user_id'); // Foreign key referencing 'users' table
       $table->timestamps();

       // Define the foreign key constraint
       $table->foreign('user_id')->references('id')->on('users');
   });
   ```

2. **Eloquent Models:**

   In your Eloquent models, you can define the one-to-many relationship like this:

   ```php
   // User model
   class User extends Model {
       public function posts() {
           return $this->hasMany(Post::class);
       }
   }

   // Post model
   class Post extends Model {
       public function user() {
           return $this->belongsTo(User::class);
       }
   }
   ```

   Here, the `hasMany` method is used in the `User` model to define the relationship with the `Post` model, and the `belongsTo` method is used in the `Post` model to specify the reverse relationship.

These code examples demonstrate the setup of one-to-one and one-to-many relationships in Laravel, including migrations and Eloquent model definitions.
