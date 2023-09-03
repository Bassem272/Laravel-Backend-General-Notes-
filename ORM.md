Laravel provides a powerful ORM (Object-Relational Mapping) called Eloquent, which allows you to interact with your database tables using PHP code. Here are some common Eloquent queries and how to use them:

1. **Retrieve Records:**

   - Retrieve all records from a table:

     ```php
     $records = YourModel::all();
     ```

   - Retrieve a single record by its primary key:

     ```php
     $record = YourModel::find($id);
     ```

   - Retrieve the first record that matches a condition:

     ```php
     $record = YourModel::where('column', 'value')->first();
     ```

   - Retrieve multiple records that match a condition:

     ```php
     $records = YourModel::where('column', 'value')->get();
     ```

2. **Create Records:**

   - Create a new record and save it to the database:

     ```php
     $newRecord = new YourModel();
     $newRecord->column1 = 'value1';
     $newRecord->column2 = 'value2';
     $newRecord->save();
     ```

   - Create a new record and save it in one line using the `create` method:

     ```php
     $newRecord = YourModel::create([
         'column1' => 'value1',
         'column2' => 'value2',
     ]);
     ```

3. **Update Records:**

   - Update a specific record:

     ```php
     $record = YourModel::find($id);
     $record->column = 'new value';
     $record->save();
     ```

   - Update multiple records that match a condition:

     ```php
     YourModel::where('column', 'value')->update([
         'column1' => 'new value 1',
         'column2' => 'new value 2',
     ]);
     ```

4. **Delete Records:**

   - Delete a specific record:

     ```php
     $record = YourModel::find($id);
     $record->delete();
     ```

   - Delete multiple records that match a condition:

     ```php
     YourModel::where('column', 'value')->delete();
     ```

5. **Count Records:**

   - Count the number of records that match a condition:

     ```php
     $count = YourModel::where('column', 'value')->count();
     ```

6. **Order Records:**

   - Order records by a specific column in ascending order:

     ```php
     $records = YourModel::orderBy('column')->get();
     ```

   - Order records by a specific column in descending order:

     ```php
     $records = YourModel::orderByDesc('column')->get();
     ```

These are some of the basic Eloquent queries you can use in Laravel. Eloquent provides many other query building methods and advanced features for handling relationships, aggregations, and more. You can refer to the official Laravel documentation for a comprehensive guide on using Eloquent: https://laravel.com/docs/8.x/eloquent
