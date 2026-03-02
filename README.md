using System;
using System.Collections.Generic;
using System.Linq;

class Product
{
    public int ProductId { get; set; }
    public string ProductName { get; set; }
    public string Category { get; set; }
    public double Price { get; set; }
}

class Program
{
    static void Main()
    {
        List<Product> products = new List<Product>
        {
            new Product { ProductId = 1, ProductName = "Laptop", Category = "Electronic", Price = 65000 },
            new Product { ProductId = 2, ProductName = "Mobile", Category = "Electronic", Price = 30000 },
            new Product { ProductId = 3, ProductName = "Dove", Category = "Cosmetic", Price = 90 },
            new Product { ProductId = 4, ProductName = "Lipstick", Category = "Cosmetic", Price = 500 },
            new Product { ProductId = 5, ProductName = "Chair", Category = "Furniture", Price = 2000 },
            new Product { ProductId = 6, ProductName = "Table", Category = "Furniture", Price = 5000 }
        };

        // Category-wise Count
        var categoryCount = products
            .GroupBy(p => p.Category)
            .Select(g => new { Category = g.Key, Count = g.Count() });

        Console.WriteLine("Category Wise Count:");
        foreach (var item in categoryCount)
            Console.WriteLine($"{item.Category} - {item.Count}");

        // Category-wise Max Price
        var categoryMaxPrice = products
            .GroupBy(p => p.Category)
            .Select(g => new { Category = g.Key, MaxPrice = g.Max(p => p.Price) });

        Console.WriteLine("\nCategory Wise Max Price:");
        foreach (var item in categoryMaxPrice)
            Console.WriteLine($"{item.Category} - {item.MaxPrice}");
    }
}
