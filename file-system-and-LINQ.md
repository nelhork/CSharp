# Взаимодействие с файловой системой. LINQ в C\#
## Взаимодействие с файловой системой
Работа с файловой системой является важной частью многих программ. В C# существуют различные классы и методы, которые облегчают эту задачу.
Примеры:
1. Чтение текстового файла:
```C#
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\Users\Username\Desktop\example.txt";
        string content = File.ReadAllText(path);
        Console.WriteLine("Содержимое файла: " + content);

        Console.ReadKey();
    }
}
```
2. Запись в текстовый файл:
```C#
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\Users\Username\Desktop\example.txt";
        string content = "Пример текста для записи";
        File.WriteAllText(path, content);
        Console.WriteLine("Данные успешно записаны в файл.");

        Console.ReadKey();
    }
}
```
Примеры с использованием try-catch.
Чтение текстового файла:
```C#
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\Users\Username\Desktop\example.txt";

        try
        {
            string content = File.ReadAllText(path);
            Console.WriteLine("Содержимое файла: " + content);
        }
        catch (IOException e)
        {
            Console.WriteLine("Ошибка чтения файла: " + e.Message);
        }
    }
}
```
Запись в текстовый файл:
```C#
using System;
using System.IO;

class Program
{
    static void Main()
    {
        string path = @"C:\Users\Username\Desktop\example.txt";

        try
        {
            string content = "Пример текста для записи";
            File.WriteAllText(path, content);
            Console.WriteLine("Данные успешно записаны в файл.");
        }
        catch (IOException e)
        {
            Console.WriteLine("Ошибка записи в файл: " + e.Message);
        }
    }
}
```
## LINQ
LINQ (Language Integrated Query) - это мощный инструмент, позволяющий выполнять структурированные запросы к различным наборам данных, таким как коллекции объектов, базы данных и другие источники.

Пример работы с LINQ:
```C#
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main()
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };

        var evenNumbers = from number in numbers
                          where number % 2 == 0
                          select number;

        Console.WriteLine("Четные числа:");
        foreach (var number in evenNumbers)
        {
            Console.WriteLine(number);
        }

        Console.ReadKey();
    }
}
```
