The two lines of code you provided are used to query the "Product" model in Laravel based on the "name" column. However, there are differences in how they perform the query:

1. `$product = Product::where('name', 'LIKE', '%'.$name.'%')->get();`

   This line of code uses the `LIKE` operator with wildcard characters (`%`) to perform a partial string match on the "name" column. It will retrieve all records where the "name" contains the value of `$name` anywhere in the name. For example, if `$name` is "apple," this query would return records with names like "Apple Pie," "Red Apple," etc. It returns a collection of matching records.

2. `$product = Product::where('name', $name)->get();`

   This line of code performs an exact match query on the "name" column. It will retrieve records where the "name" column exactly matches the value of `$name`. It does not perform partial matching or use wildcard characters. If `$name` is "apple," it will only return records with the exact name "apple." It also returns a collection of matching records.

In summary, the key difference is in how they match the "name" column:

- The first line (`LIKE` with wildcards) is used for partial matching and is more flexible when you want to find records containing a specific substring within the name.
- The second line is used for exact matching and is suitable when you want to find records with an exact match to the provided name.

- To work with a collection in Laravel, you can use various collection methods and techniques to extract, manipulate, and iterate through the data. Here are some common operations you can perform on a Laravel collection:

1. **Looping Through the Collection:**

   You can iterate through the collection using loops like `foreach`. For example:

   ```php
   foreach ($product as $item) {
       // Access individual item properties, e.g., $item->name
   }
   ```

2. **Plucking Specific Columns:**

   You can extract specific columns from the collection using the `pluck` method. For example, to extract an array of all "name" values:

   ```php
   $names = $product->pluck('name')->toArray();
   ```

3. **Filtering Data:**

   You can filter the collection based on specific criteria using the `filter` method. For example, to get products with a specific condition:

   ```php
   $filteredProducts = $product->filter(function ($item) {
       return $item->price > 100;
   });
   ```

4. **Mapping Data:**

   You can transform the data in the collection using the `map` method. For example, to format the names:

   ```php
   $formattedNames = $product->map(function ($item) {
       return strtoupper($item->name);
   });
   ```

5. **Counting Items:**

   You can count the number of items in the collection using the `count` method:

   ```php
   $count = $product->count();
   ```

6. **Sorting Data:**

   You can sort the collection based on specific criteria using the `sortBy` method. For example, to sort by "name" in ascending order:

   ```php
   $sortedProducts = $product->sortBy('name');
   ```

7. **Getting First and Last Item:**

   You can get the first and last items in the collection using the `first` and `last` methods:

   ```php
   $firstItem = $product->first();
   $lastItem = $product->last();
   ```

These are just some examples of what you can do with Laravel collections. Laravel provides many other useful collection methods that you can explore in the [official documentation](https://laravel.com/docs/8.x/collections).
