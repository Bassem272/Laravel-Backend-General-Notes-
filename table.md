Certainly! Below are the code snippets for creating the migration files for each table in your Laravel application. You can use these migrations to generate the corresponding database tables by running Laravel's `php artisan migrate` command.

**User Table Migration:**
```bash
php artisan make:migration create_users_table
```

```php
// In the generated migration file (create_users_table.php)
public function up()
{
    Schema::create('users', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->string('email')->unique();
        $table->string('password');
        $table->string('role'); // You can adjust this column to match your roles.
        $table->timestamps();
    });
}
```

**Product Table Migration:**
```bash
php artisan make:migration create_products_table
```

```php
// In the generated migration file (create_products_table.php)
public function up()
{
    Schema::create('products', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->text('description');
        $table->decimal('price', 10, 2);
        $table->integer('stock');
        $table->string('image');
        $table->unsignedBigInteger('category_id');
        $table->enum('status', ['active', 'inactive']);
        $table->timestamps();

        $table->foreign('category_id')->references('id')->on('categories');
    });
}
```

**Category Table Migration:**
```bash
php artisan make:migration create_categories_table
```

```php
// In the generated migration file (create_categories_table.php)
public function up()
{
    Schema::create('categories', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->timestamps();
    });
}
```

**Order Table Migration:**
```bash
php artisan make:migration create_orders_table
```

```php
// In the generated migration file (create_orders_table.php)
public function up()
{
    Schema::create('orders', function (Blueprint $table) {
        $table->id();
        $table->string('order_number')->unique();
        $table->unsignedBigInteger('customer_id');
        $table->dateTime('order_date');
        $table->string('order_status');
        $table->timestamps();

        $table->foreign('customer_id')->references('id')->on('users');
    });
}
```

**OrderItem Table Migration:**
```bash
php artisan make:migration create_order_items_table
```

```php
// In the generated migration file (create_order_items_table.php)
public function up()
{
    Schema::create('order_items', function (Blueprint $table) {
        $table->id();
        $table->unsignedBigInteger('order_id');
        $table->unsignedBigInteger('product_id');
        $table->integer('quantity');
        $table->decimal('item_price', 10, 2);
        $table->decimal('subtotal', 10, 2);
        $table->timestamps();

        $table->foreign('order_id')->references('id')->on('orders');
        $table->foreign('product_id')->references('id')->on('products');
    });
}
```

**Cart Table Migration (Pivot Table):**
```bash
php artisan make:migration create_cart_table
```

```php
// In the generated migration file (create_cart_table.php)
public function up()
{
    Schema::create('cart', function (Blueprint $table) {
        $table->id();
        $table->unsignedBigInteger('user_id');
        $table->unsignedBigInteger('product_id');
        $table->integer('quantity');
        $table->timestamps();

        $table->foreign('user_id')->references('id')->on('users');
        $table->foreign('product_id')->references('id')->on('products');
    });
}
```

**Profile Table Migration (Optional for One-to-One with User):**
```bash
php artisan make:migration create_profiles_table
```

```php
// In the generated migration file (create_profiles_table.php)
public function up()
{
    Schema::create('profiles', function (Blueprint $table) {
        $table->id();
        $table->unsignedBigInteger('user_id');
        // Add columns for additional profile information as needed.
        $table->timestamps();

        $table->foreign('user_id')->references('id')->on('users');
    });
}
```

Once you have created these migration files, you can run the `php artisan migrate` command to execute the migrations and create the corresponding database tables. Make sure to adjust the migrations to match your specific database requirements and customize the columns as needed.
