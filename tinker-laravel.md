laptop home@DESKTOP-15RE749 MINGW64 /f/Laravel/artGallary (main)
$ php artisan tinker

laptop home@DESKTOP-15RE749 MINGW64 /f/Laravel/artGallary (main)
$ >>> App\Product::where('name', $keyword)->first();    
bash: syntax error near unexpected token `>'

laptop home@DESKTOP-15RE749 MINGW64 /f/Laravel/artGallary (main)
$ ^C

laptop home@DESKTOP-15RE749 MINGW64 /f/Laravel/artGallary (main)
$ php artisan tinker
Psy Shell v0.11.20 (PHP 8.2.4 — cli) by Justin Hileman  
>
> App\Product::where('name', $keyword)->first();        

   Error  Class "App\Product" not found.

> App\Models\Product::where('name',$keyword)->first();  

   WARNING  Undefined variable $keyword.

= App\Models\Product {#6586
    id: 71,
    name: null,
    description: "This is a sample product description.",
    price: "29.99",
    stock: 100,
    image: "sample-image.jpg",
    category_id: 1,
    status: "active",
    created_at: "2023-09-13 16:50:53",
    updated_at: "2023-09-13 16:50:53",
  }

> App\Models\Product::where('name','Sherman Kuhlman')->first();
= App\Models\Product {#6240
    id: 70,
    name: "Sherman Kuhlman",
    description: "Nihil sit ab voluptates autem. Totam ipsam ipsum ut. Ullam numquam voluptas omnis.",
    price: "786.00",
    stock: 64,
    image: "https://via.placeholder.com/640x480.png/001199?text=laudantium",
    category_id: 80,
    status: "active",
    created_at: "2023-09-13 16:49:43",
    updated_at: "2023-09-13 16:49:43",
  }

>
