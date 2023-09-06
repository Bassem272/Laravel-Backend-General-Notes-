Certainly, here are the Laravel Artisan commands related to migrations that you can run in the console:

1. **Creating a Migration File:**
   ```bash
   php artisan make:migration NameOfMigration
   ```

2. **Running Migrations:**
   ```bash
   php artisan migrate
   ```

3. **Rolling Back Migrations:**
   ```bash
   php artisan migrate:rollback
   ```
   To roll back a specific number of batches (e.g., 2 batches):
   ```bash
   php artisan migrate:rollback --step=2
   ```

4. **Resetting Migrations:**
   ```bash
   php artisan migrate:reset
   ```
   Or, to roll back and re-run all migrations:
   ```bash
   php artisan migrate:refresh
   ```

5. **Status of Migrations:**
   ```bash
   php artisan migrate:status
   ```

6. **Creating and Running Seeders:**
   ```bash
   php artisan make:seeder NameOfSeeder
   ```
   To run all seeders:
   ```bash
   php artisan db:seed
   ```
   To run a specific seeder class (replace `NameOfSeeder`):
   ```bash
   php artisan db:seed --class=NameOfSeeder
   ```

7. **Refreshing the Database (Rolling Back and Re-running Migrations with Seeding):**
   ```bash
   php artisan migrate:refresh --seed
   ```

8. **Rolling Back and Re-running Migrations:**
   ```bash
   php artisan migrate:refresh
   ```

These commands should cover most of your migration-related needs in Laravel. You can run them in your terminal or command prompt within your Laravel project directory.
In Laravel, you can use Artisan commands to work with database seeders. Here's a list of commonly used Artisan commands for seeding the database:

1. **Creating a New Seeder:**
   ```bash
   php artisan make:seeder NameOfSeeder
   ```
   This command generates a new seeder class in the `database/seeders` directory.

2. **Running All Seeders:**
   ```bash
   php artisan db:seed
   ```
   This command runs all seeders that you've defined.

3. **Running a Specific Seeder Class:**
   ```bash
   php artisan db:seed --class=NameOfSeeder
   ```
   Replace `NameOfSeeder` with the name of the seeder class you want to run. This is useful when you want to run a specific seeder.

4. **Refreshing and Seeding the Database:**
   ```bash
   php artisan migrate:refresh --seed
   ```
   This command resets the database by rolling back migrations, re-running migrations, and then seeding the database. It's useful for resetting and reseeding the entire database.

5. **Rolling Back and Re-running Seeders:**
   ```bash
   php artisan db:seed --class=NameOfSeeder
   ```
   If you've made changes to a specific seeder class and want to re-run it without affecting other seeders, you can specify the seeder class to run.

6. **Seeding a Specific Database Connection:**
   ```bash
   php artisan db:seed --database=connection_name
   ```
   If your application uses multiple database connections, you can specify the connection name to seed a particular database.

These are the primary Artisan commands related to seeding the database in Laravel. You can run these commands in your terminal or command prompt within your Laravel project directory.
