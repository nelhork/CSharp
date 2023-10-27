# CSharp
# Синтаксис объявления класса в C\#

### Что такое классы в C#?
Классы - это шаблоны для создания объектов. Каждый объект класса содержит данные (поля) и методы, которые манипулируют этими данными. Класс определяет, какие данные и какую функциональность может иметь каждый конкретный объект (экземпляр) этого класса. Например, класс, представляющий человека, может иметь поля, такие как имя, фамилия, возраст и так далее, для хранения информации о человеке.
### Синтаксис объявления класса:
```C#
class Person
{
	// Поля класса
	public string FirstName;
	public string LastName;
	public int Age;

	// Конструктор с параметрами
	public Person(string firstName, string lastName, int age)
	{
		FirstName = firstName; 
		LastName = lastName; 
		Age = age;
	}
}
```
Рассмотрим каждую часть синтаксиса:
1. **class Person**: С ключевым словом `class` начинается объявление класса. `Person` - это название класса, которое может быть выбрано произвольно. Обычно имена классов начинаются с заглавной буквы.
2. **Поля класса**: Поля класса представляют собой переменные, которые хранят данные для объектов этого класса. Они могут быть общедоступными (`public`), закрытыми (`private`), защищенными (`protected`).
3. **Конструкторы класса**: Конструкторы - это специальные методы, вызываемые при создании объекта класса. Они служат для инициализации полей класса. Класс может иметь конструктор по умолчанию (без параметров) и конструкторы с параметрами.
4. **Методы класса**: Методы класса - это функции, которые выполняют определенные действия с данными, хранящимися в полях класса. Они могут принимать параметры и возвращать значения.

**Пример использования класса:**
```C#
using System;

class Person
{
    // Поля класса
    public string FirstName;
    public string LastName;
    public int Age;

    public Person(string firstName, string lastName, int age)
    {
	// Инициализация полей класса
        FirstName = firstName;
        LastName = lastName;
        Age = age;
    }
}

class Program
{
    static void Main(string[] args)
    {
	// Создание объекта класса
        Person person1 = new Person("John", "Doe", 29);

        Console.WriteLine($"Name: {person1.FirstName} {person1.LastName}, Age: {person1.Age}");

        Console.ReadKey();
    }
}
// Обратите внимание, что в большинстве приложений точка входа представляет собой метод Main,
// который является статическим методом и может находиться внутри любого класса. Обычно создается
// класс с именем Program, и метод Main используется в качестве точки входа для вашего приложения.
```
# Модификаторы доступа в C\#
### Введение в модификаторы доступа
В C# все типы (классы, структуры, интерфейсы и другие) и их члены (поля, методы, свойства и т. д.) имеют уровень доступности, который определяет, какие части кода могут использовать их. Уровень доступности определяет видимость типов и членов извне и внутри сборки. Модификаторы доступа позволяют контролировать доступ к данным и функциональности.
### Уровни доступа в C\#
В C# существует несколько уровней доступа, начиная с самого ограниченного и заканчивая наиболее открытым. Вот основные уровни доступа и их характеристики:

1. **private**: Данные с модификатором `private` доступны только методам внутри класса, в котором они объявлены, и вложенным в него классам. Это самый ограниченный уровень доступа.
    
2. **protected**: Данные с модификатором `protected` доступны методам внутри класса, где они объявлены (и вложенным в него классам), а также методам в производных классах (наследниках). То есть, они видны только внутри класса и его наследников.
    
3. **internal**: Данные с модификатором `internal` доступны только в методах текущей сборки. Этот модификатор ограничивает доступ к членам класса извне сборки, в которой они определены.
    
4. **protected internal**: Члены класса, помеченные модификатором `protected internal`, сочетают в себе функциональность `protected` и `internal`. Они доступны внутри текущей сборки и в производных классах, независимо от того, находятся ли они в той же сборке или в другой.
    
5. **public**: Данные с модификатором `public` доступны всем методам во всех сборках. Это наиболее открытый уровень доступа.

### По умолчанию
Если вы не указываете явно модификатор доступа для класса или его членов, компилятор C# использует уровни доступа по умолчанию:

- Для членов класса: `private` (т.е., они видны только внутри класса).
- Для самого класса: `internal` (только внутри сборки).
- 
### Переопределение членов в производных классах
При наследовании, если вы хотите переопределить член базового класса в производном классе, модификатор доступа у переопределенного члена должен быть таким же или менее ограниченным, чем у базового члена. Вы не можете повысить уровень доступа при переопределении члена.

# Поля класса
### Введение в поля класса
Поля класса представляют собой переменные, которые хранят данные для объектов этого класса. Они могут хранить значения стандартных типов данных или ссылки на объекты других классов. Поля класса являются одним из важных строительных блоков для хранения информации в C#.

### Типы полей
При объявлении полей класса могут указываться следующие ключевые слова:

1. **static**: Ключевое слово `static` используется для объявления статических полей. Статические поля принадлежат не конкретному объекту, а классу в целом. Они общие для всех экземпляров класса. Доступ к статическим полям осуществляется через имя класса, например: `ClassName.StaticField`.
    
2. **const**: Ключевое слово `const` используется для объявления константных полей. Значение константных полей не может быть изменено после их инициализации. Поле с модификатором `const` должно быть проинициализировано при объявлении класса. Константные поля являются неявно статическими, поэтому обращение к ним происходит через имя типа.
    
3. **readonly**: Поля с модификатором `readonly` могут быть использованы только для чтения, и значение таких полей может быть установлено только в конструкторе или непосредственно при объявлении. Они позволяют задать значение динамически, но после этого оно не может быть изменено.

### Изменяемые и неизменяемые поля
Поля класса могут быть изменяемыми (read/write) и неизменяемыми (readonly). Изменяемые поля позволяют многократное изменение их значений во время выполнения программы. Неизменяемые поля более гибкие, чем константы, так как их значение можно задать динамически, но оно не может быть изменено после установки. Важно отметить, что неизменяемость поля ссылочного типа означает неизменность самой ссылки, но не объекта, на который она указывает.

**Пример использования полей:**
```C#
using System;

class Person
{
    public string FirstName;
    public string LastName;
    public int Age;

    private static int personCount = 0; // Статическое поле

    private const string defaultPhoneNumber = "N/A"; // Константное поле

    private readonly string email; // Неизменяемое поле

    private string phoneNumber; // Изменяемое поле

    public Person(string firstName, string lastName, int age, string phone, string email)
    {
        FirstName = firstName;
        LastName = lastName;
        Age = age;
        phoneNumber = phone;
        this.email = email; // Используем ключевое слово "this" для разрешения конфликта имён

        personCount++;
    }

    public void DisplayContactInfo()
    {
        Console.WriteLine();
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {phoneNumber}");
        Console.WriteLine($"Email: {email}");
        Console.WriteLine();
    }

    public static int GetPersonCount()
    {
        return personCount;
    }

    public void ChangePhoneNumber(string newPhoneNumber)
    {
        phoneNumber = newPhoneNumber;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person("John", "Doe", 30, "555-123-4567", "johndoe@email.com");
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.DisplayContactInfo();

        person1.ChangePhoneNumber("555-999-0000");

        person1.DisplayContactInfo();

        person2.DisplayContactInfo();

        Console.WriteLine($"\nTotal persons created: {Person.GetPersonCount()}");

        Console.ReadKey();
    }
}
```
# Конструкторы класса в C\#
## Введение в конструкторы
Конструкторы представляют собой специальные методы класса, которые вызываются неявно при создании объекта с использованием ключевого слова `new`. Они играют важную роль в инициализации объектов и проведении необходимых операций при создании экземпляра класса.

### Типы конструкторов
1. **Конструктор по умолчанию**: Этот конструктор не принимает никаких параметров и предоставляется компилятором при создании класса. Его задача - инициализировать все поля объекта значениями по умолчанию. По желанию, вы можете переопределить конструктор по умолчанию для выполнения других инициализаций.

Левый пример:
```C#
using System;

class Student
{
    string firstName;

    public Student()
    {
        firstName = "John"; // Устанавливаем имя по умолчанию
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Student's Name: {firstName}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student student = new Student(); // Используем конструктор по умолчанию

        student.DisplayInfo(); // Выводим информацию о студенте
        
		Console.ReadKey();
    }
}
```
2. **Конструктор с параметрами**: Этот конструктор принимает параметры, необходимые для инициализации полей объекта. Параметризованный конструктор позволяет передавать конкретные значения при создании объекта.

Левый пример:
```C#
using System;

class Student
{
    string firstName;

    public Student(string name)
    {
        firstName = name;
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Student's Name: {firstName}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student student = new Student("Alice"); // Используем конструктор с параметром
        student.DisplayInfo(); // Выводим информацию о студенте
        
        Console.ReadKey();
    }
}
```
3. **Статический конструктор**: Статический конструктор принадлежит классу, а не объекту, и используется для инициализации статических полей класса. Статический конструктор выполняется перед первым созданием экземпляра класса или перед первым обращением к любому статическому члену класса.
(Инициализация статических полей: Статические конструкторы могут быть использованы для инициализации значений статических полей до того, как они будут использованы в программе. Это позволяет гарантировать, что статические поля будут проинициализированы до использования класса.)

Левый пример:
```C#
using System;

class Student
{
    private static int studentCount;

    static Student() // Статический конструктор
    {
        Console.WriteLine("Static constructor is called.\n");
        studentCount = 0;
    }

    public Student()
    {
        studentCount++;
    }

    public static void DisplayStudentCount()
    {
        Console.WriteLine($"Total number of students: {studentCount}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student.DisplayStudentCount(); // Вызываем статический метод до создания объектов

        Student student1 = new Student();
        Student.DisplayStudentCount(); // Вызываем статический метод после создания объекта

        Student student2 = new Student();
        Student.DisplayStudentCount(); // Вызываем статический метод после создания объекта

        Console.ReadKey();
    }
}
```
### Важные моменты о конструкторах
- Все конструкторы, кроме статического, должны иметь модификатор доступа `public`, имя, совпадающее с именем класса и не возвращать значения.
- Конструктор по умолчанию может быть только один. Если определен пользовательский конструктор, конструктор по умолчанию автоматически не генерируется.
- Конструкторы могут быть перегружены, то есть класс может иметь несколько конструкторов с разными параметрами.
- Статический конструктор может быть определен только один раз в классе и не имеет параметров.
- Статический конструктор вызывается автоматически при первом обращении к классу.

**Пример использования конструкторов**
```C#
using System;

class Person
{
    public string FirstName;
    public string LastName;
    public int Age;

    // Поле класса
    private static int personCount = 0; // Статическое поле

    private const string DefaultPhoneNumber = "N/A"; // Константное поле

    private readonly string email; // Неизменяемое поле

    private string phoneNumber; // Изменяемое поле

    // Конструктор по умолчанию
    public Person()
    {
        FirstName = "Агаян";
        LastName = "Турабов";
        Age = 20;
        phoneNumber = DefaultPhoneNumber;
        email = "agayan@email.com";
        personCount++;
    }

    // Конструктор с параметрами
    public Person(string firstName, string lastName, int age, string phone, string email)
    {
        FirstName = firstName;
        LastName = lastName;
        Age = age;
        phoneNumber = phone;
        this.email = email;
        personCount++;
    }

    public void DisplayContactInfo()
    {
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {phoneNumber}");
        Console.WriteLine($"Email: {email}");
    }

    public static int GetPersonCount()
    {
        return personCount;
    }

    public void ChangePhoneNumber(string newPhoneNumber)
    {
        phoneNumber = newPhoneNumber;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.ChangePhoneNumber("555-999-0000");

        person1.DisplayContactInfo();
        Console.WriteLine();
        person2.DisplayContactInfo();

        Console.WriteLine($"\nTotal persons created: {Person.GetPersonCount()}");

        Console.ReadKey();
    }
}

```
# Ключевое слово `this`
### Введение в ключевое слово `this`
Ключевое слово `this` в C# представляет собой неявную ссылку на текущий экземпляр класса. Это мощный инструмент, который позволяет явно указать, какие члены класса или параметры методов используются внутри текущего объекта. `this` может быть использовано в различных контекстах, и мы рассмотрим несколько типичных случаев его использования.

### Использование `this` для разрешения конфликта имен
Один из распространенных случаев использования `this` - это разрешение конфликта имен между параметрами метода и полями класса. Когда имена параметров совпадают с именами полей, `this` помогает явно указать, что мы обращаемся к полям класса.

Левый пример:
```C#
class Student
{
    string firstName;

    public Student(string firstName)
    {
        this.firstName = firstName;
    }
}
```
### Избегание дублирования кода с использованием this
Ключевое слово this в C# используется для ссылки на текущий экземпляр класса внутри методов этого класса. Оно чаще всего используется для предотвращения дублирования кода при доступе к членам класса из разных частей класса, таких как конструкторы или методы.

Левый пример:
```C#
public class MyClass
{
    private int myValue;

    public MyClass(int myValue)
    {
        this.myValue = myValue; // Использование this для ссылки на поле myValue внутри конструктора
    }
}

```
### Передача ссылки на текущий объект методу
Это практика передачи текущего объекта в качестве параметра в методы того же класса. Этот подход может быть полезен, когда метод должен взаимодействовать с текущим объектом или когда методы имеют доступ к приватным полям текущего объекта.

Левый пример:
```C#
public class MyClass
{
    private int myValue;

    public void SetMyValue(int newValue)
    {
        UpdateValue(this, newValue); // Передача текущего объекта в метод UpdateValue
    }

    private void UpdateValue(MyClass obj, int newValue)
    {
        obj.myValue = newValue; // Использование переданного объекта для обновления значения
    }
}

```

Важно отметить, что использование `this` в статических методах запрещено, так как статические методы существуют на уровне класса и не имеют доступа к объектам класса.

Ключевое слово `this` является мощным инструментом для работы с объектами в C# и помогает избегать конфликтов имен, избыточности кода и передачи ссылок на текущий объект.

**Общий пример:**
```C#
using System;

class Person
{
    public string FirstName;
    public string LastName;
    public int Age;

    // Поле класса
    private string phoneNumber;
    private string email;

    public Person(string firstName, string lastName, int age, string phone, string email)
    {
        this.FirstName = firstName;
        this.LastName = lastName;
        this.Age = age;
        this.phoneNumber = phone;
        this.email = email; // Используем ключевое слово "this" для разрешения конфликта имён
    }

    public void DisplayContactInfo()
    {
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {phoneNumber}");
        Console.WriteLine($"Email: {email}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person("John", "Doe", 30, "555-123-4567", "johndoe@email.com");

        person1.DisplayContactInfo();

        Console.ReadKey();
    }
}
```
# Методы в классе
1. **Методы класса (Class Methods)**: Методы класса представляют собой функции, определенные внутри определения класса. Они используются для выполнения определенных операций или действий с объектами класса. Методы могут быть публичными или приватными, в зависимости от того, должны ли они быть доступны извне класса или только внутри него.
    
2. **Определение методов (Defining Methods)**: Методы могут быть определены внутри тела класса. Они могут содержать параметры, возвращаемые значения, а также код, выполняющий необходимые операции. Методы можно определить с использованием ключевых слов `public`, `private` и других модификаторов доступа.
    
3. **Передача параметров (Passing Parameters)**: Параметры могут быть переданы методу для обработки или использования внутри метода. Они могут быть переданы по значению или по ссылке. Передача по значению означает, что метод работает с копией параметра, а передача по ссылке означает, что метод работает с самим параметром.
    
4. **Возвращаемое значение (Return Value)**: Метод может возвращать значение при завершении своего выполнения. Тип возвращаемого значения должен быть объявлен в сигнатуре метода. Ключевое слово `return` используется для возврата значения из метода.
    
5. **Перегрузка методов (Method Overloading)**: Перегрузка методов позволяет определить несколько методов с одним и тем же именем, но с разными наборами параметров. Это позволяет создавать методы с одинаковыми именами, но разными поведениями, в зависимости от переданных параметров.
    
Внесем некоторые изменения, чтобы продемонстрировать концепцию перегрузки методов. Давайте добавим перегрузку методов и возвращаемое значение:
```C#
using System;

class Person
{
    public string FirstName;
    public string LastName;
    public int Age;

    // Поле класса
    private static int personCount = 0; // Статическое поле

    private const string DefaultPhoneNumber = "N/A"; // Константное поле

    private readonly string email; // Неизменяемое поле

    private string phoneNumber; // Изменяемое поле

    // Конструктор по умолчанию
    public Person()
    {
        FirstName = "John";
        LastName = "Doe";
        Age = 30;
        phoneNumber = DefaultPhoneNumber;
        email = "johndoe@email.com";
        personCount++;
    }

    public void DisplayContactInfo()
    {
        Console.WriteLine();
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {phoneNumber}");
        Console.WriteLine($"Email: {email}");
        Console.WriteLine();
    }

    public void ChangePhoneNumber(string newPhoneNumber)
    {
        phoneNumber = newPhoneNumber;
    }

    // Перегрузка метода ChangePhoneNumber
    public void ChangePhoneNumber(int countryCode, string newPhoneNumber)
    {
        phoneNumber = $"+{countryCode} {newPhoneNumber}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        person1.DisplayContactInfo();

        person1.ChangePhoneNumber("555-999-0000");
        person1.DisplayContactInfo();

        // Использование перегруженного метода ChangePhoneNumber
        person1.ChangePhoneNumber(1, "555-999-0000");
        person1.DisplayContactInfo();

        Console.ReadKey();
    }
}
```
## ref, out параметры
В C# параметры методов могут быть переданы по значению, по ссылке или с использованием ключевых слов ref и out. Вот обзор концепций ref и out:

ref параметры:
- Параметры передаются по ссылке.
- Используются для передачи переменных с возможностью изменения значения в вызывающем коде.
- При использовании ref переменная должна быть инициализирована до передачи в метод.

out параметры:
- Требуют, чтобы метод присваивал значение переменной до ее возврата.
- Используются для возврата нескольких значений из метода.
- Переменная, переданная как out параметр, может быть не инициализирована.

```C#
using System;

class Program
{
    // Пример с ref параметром
    public static void ModifyValue(ref int value)
    {
        value = value * 2;
    }

    // Пример с out параметрами
    public static void GetValues(out int first, out int second)
    {
        first = 10;
        second = 20;
    }

    static void Main(string[] args)
    {
        // Пример с ref параметром
        int number = 5;
        Console.WriteLine($"Исходное значение: {number}");
        ModifyValue(ref number);
        Console.WriteLine($"Измененное значение с ref: {number}");

        // Пример с out параметрами
        int result1, result2;
        GetValues(out result1, out result2);
        Console.WriteLine($"Первое значение с out: {result1}");
        Console.WriteLine($"Второе значение с out: {result2}");

        Console.ReadKey();
    }
}

```

# Создание методов с переменным количеством аргументов
В C# можно создавать методы с переменным количеством аргументов, используя ключевое слово params. Вот пример цельной программы, демонстрирующий использование метода с переменным числом аргументов:
```C#
using System;

class Program
{
    // Метод с переменным количеством аргументов
    public static void PrintValues(params int[] values)
    {
        Console.WriteLine("Вывод значений:");
        foreach (int val in values)
        {
            Console.WriteLine(val);
        }
    }

    static void Main(string[] args)
    {
        // Использование метода с переменным количеством аргументов
        PrintValues(1, 2, 3, 4, 5);
        PrintValues(6, 7, 8);
        PrintValues(9);

        Console.ReadKey();
    }
}

```
Ключевое слово `params` в C# позволяет определить метод с переменным числом аргументов одного типа. Это позволяет методу принимать переменное количество аргументов одного типа, не требуя явного указания количества аргументов при вызове метода. Это удобно, когда необходимо передать переменное количество аргументов в метод.

# Свойства
В C# свойства get и set используются для определения методов доступа для чтения и записи значений в приватные поля класса. Это позволяет контролировать доступ к полям класса и управлять проверкой или преобразованием значений перед их установкой или возвратом. Вот пример программы, демонстрирующей использование свойств get и set:

```C#
using System;

public class Person
{
    private string name;
    private int age;

    public string Name
    {
        get { return name; }
        set { name = value; }
    }

    public int Age
    {
        get { return age; }
        set
        {
            if (value >= 0)
            {
                age = value;
            }
            else
            {
                Console.WriteLine("Возраст не может быть отрицательным!");
            }
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person = new Person();

        // Установка значения через свойство set
        person.Name = "John Doe";
        person.Age = 30;

        // Получение значения через свойство get
        Console.WriteLine($"Имя: {person.Name}, Возраст: {person.Age}");

        // Попытка установить отрицательный возраст
        person.Age = -5;

        Console.ReadKey();
    }
}

```

### Автоматические свойства, инициализация
Автоматические свойства в C# представляют сокращенный синтаксис для создания свойств класса без явного объявления соответствующих закрытых полей. Они автоматически создают закрытые поля во время компиляции, что упрощает их использование и позволяет сосредоточиться на более важных аспектах разработки.

```C#
using System;

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Создание объекта с использованием конструктора
        Person person = new Person("John Doe", 30);

        // Вывод значений свойств
        Console.WriteLine($"Имя: {person.Name}, Возраст: {person.Age}");

        Console.ReadKey();
    }
}

```
Использование автоматических свойств в C# во многом аналогично созданию приватных полей и публичных методов-сеттеров и геттеров. Однако автоматические свойства значительно упрощают синтаксис, делая код более читаемым и понятным, особенно в случае, когда у класса большое количество свойств.

Использование автоматических свойств также позволяет избежать дублирования кода и уменьшить вероятность ошибок при написании сеттеров и геттеров вручную.

# Пространства имен
Пространства имен (namespaces) в языке программирования C# используются для организации и группировки логически связанных классов, интерфейсов, делегатов и других типов. Они предоставляют средство для управления областями видимости и предотвращения конфликтов имен в больших проектах. Пространства имен также позволяют создавать иерархию и группировать код логически для улучшения его читаемости и обеспечения удобного доступа.

Вот некоторые ключевые моменты по использованию пространств имен:

1. **Область видимости**: Пространства имен помогают избежать конфликтов имен, позволяя разработчикам использовать одинаковые имена для различных классов в разных пространствах имен.

2. **Организация кода**: Пространства имен позволяют логически группировать код, что упрощает его организацию и улучшает читаемость.

3. **Повторное использование**: Пространства имен могут содержать множество классов и других типов, которые могут быть повторно использованы в разных частях приложения.

Пример использования пространств имен в C#:

```C#
using System;

namespace MyNamespace
{
    class MyClass
    {
        public void MyMethod()
        {
            Console.WriteLine("This is a method in MyClass.");
        }
    }
}

namespace MyOtherNamespace
{
    class MyOtherClass
    {
        public void MyOtherMethod()
        {
            Console.WriteLine("This is a method in MyOtherClass.");
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        MyNamespace.MyClass myObject = new MyNamespace.MyClass();
        myObject.MyMethod();

        MyOtherNamespace.MyOtherClass myOtherObject = new MyOtherNamespace.MyOtherClass();
        myOtherObject.MyOtherMethod();

        Console.ReadKey();
    }
}
```

В этом примере создаются два пространства имен: `MyNamespace` и `MyOtherNamespace`. Каждое пространство имен содержит собственный класс, который имеет методы для вывода текста. В `Main` методе создаются объекты каждого класса и вызываются соответствующие методы. использование ключевого слова `using` позволяет использовать пространства имен без полного указания их имени при каждом использовании класса.
