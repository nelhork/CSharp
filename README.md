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

	// Конструктор
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
class Program
{
	static void Main(string[] args)
	{
		Person person1 = new Person("John", "Doe", 29);
		Console.WriteLine($"Name: {person1.FirstName} {person1.LastName}, Age: {person1.Age}");
		Console.ReadKey();
	}

}
class Person
{
	// Поля класса
	public string FirstName;
	public string LastName;
	public int Age;

	public Person(string firstName, string lastName, int age)
	{
		FirstName = firstName; 
		LastName = lastName; 
		Age = age;
	}
}
```
# Модификаторы доступа в C\#
### Введение в модификаторы доступа
В C# все типы (классы, структуры, интерфейсы и другие) и их члены (поля, методы, свойства и т. д.) имеют уровень доступности, который определяет, какие части кода могут использовать их. Уровень доступности определяет видимость типов и членов извне и внутри сборки. Модификаторы доступа позволяют контролировать доступ к данным и функциональности.
### Уровни доступа в C\#
В C# существует несколько уровней доступа, начиная с самого ограниченного и заканчивая наиболее открытым. Вот основные уровни доступа и их характеристики:

1. **private**: Данные с модификатором `private` доступны только методам внутри класса, в котором они объявлены, и вложенным в него классам. Это самый ограниченный уровень доступа.
    
2. **protected**: Данные с модификатором `protected` доступны методам внутри класса, где они объявлены (и вложенным в него классам), а также методам в производных классах (наследниках). То есть, они видны только внутри класса и его наследников.
    
3. **internal**: Данные с модификатором `internal` доступны только в методах текущей сборки. Этот модификатор ограничивает доступ к членам класса извне сборки, в которой они определены.
    
4. **protected internal**: Данные с модификатором `protected internal` доступны только методам вложенного или производного типа класса и любым методам текущей сборки. Это сочетание уровней `protected` и `internal`, что позволяет доступ как наследникам, так и внутри текущей сборки.
    
5. **public**: Данные с модификатором `public` доступны всем методам во всех сборках. Это наиболее открытый уровень доступа.
### По умолчанию
Если вы не указываете явно модификатор доступа для класса или его членов, компилятор C# использует уровни доступа по умолчанию:

- Для членов класса: `private` (т.е., они видны только внутри класса).
- Для самого класса: `internal` (только внутри сборки).
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

    // Поле класса
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
        Person person1 = new Person("John", "Doe", 30, "555-123-4567", "johndoe@email.com");
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.GetPersonCount()}");

        person1.ChangePhoneNumber("555-999-0000");
        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.GetPersonCount()}");

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
3. **Статический конструктор**: Статический конструктор принадлежит классу, а не объекту, и используется для инициализации статических полей класса. Он вызывается только один раз, до первого обращения к классу или его членам, и не требует модификаторов доступа.

Левый пример:
```C#
using System;

class Student
{
    private static int studentCount = 0;

    static Student() // Статический конструктор
    {
        Console.WriteLine("Static constructor is called.");
        studentCount = 1;
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
        Student student2 = new Student();

        Student.DisplayStudentCount(); // Вызываем статический метод после создания объектов
        
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
### Избегание дублирования кода с использованием `this`
Другим важным случаем использования `this` является избегание дублирования кода при инициализации членов класса. Обычно в классе существует главный конструктор, который содержит код инициализации, а остальные конструкторы вызывают его с различными параметрами, используя `this`.

Левый пример:
```C#
using System;

class Student
{
    private string firstName;
    private string lastName;

    public Student(string firstName, string lastName)
    {
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public void PrintFullName()
    {
        Console.WriteLine($"Full Name: {this.firstName} {this.lastName}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student student1 = new Student("John", "Doe");
        Student student2 = new Student("Alice", "Smith");

        student1.PrintFullName();
        student2.PrintFullName();
    }
}
```
### Передача ссылки на текущий объект методу
Иногда требуется передать методу ссылку на текущий объект. В этом случае `this` используется для передачи ссылки на текущий объект методу.

Левый пример:
```C#
using System;

class Student
{
    private string firstName;

    public Student(string firstName)
    {
        this.firstName = firstName;
    }

    public void Greet()
    {
        Console.WriteLine($"Hello, my name is {this.firstName}.");
    }

    public void IntroduceYourself(Student otherStudent)
    {
        Console.WriteLine($"Hi {otherStudent.firstName}, I'm {this.firstName}.");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Student student1 = new Student("John");
        Student student2 = new Student("Alice");

        student1.Greet();
        student2.Greet();

        student1.IntroduceYourself(student2);
        student2.IntroduceYourself(student1);
    }
}
```

**Индексаторы и ключевое слово `this`**
`this` также применяется для объявления индексаторов, но это будет рассмотрено в более поздних уроках.

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
    }
}
```
# Методы в классе
1. **Методы класса (Class Methods)**: Методы класса представляют собой функции, определенные внутри определения класса. Они используются для выполнения определенных операций или действий с объектами класса. Методы могут быть публичными или приватными, в зависимости от того, должны ли они быть доступны извне класса или только внутри него.
    
2. **Определение методов (Defining Methods)**: Методы могут быть определены внутри тела класса. Они могут содержать параметры, возвращаемые значения, а также код, выполняющий необходимые операции. Методы можно определить с использованием ключевых слов `public`, `private` и других модификаторов доступа.
    
3. **Передача параметров (Passing Parameters)**: Параметры могут быть переданы методу для обработки или использования внутри метода. Они могут быть переданы по значению или по ссылке. Передача по значению означает, что метод работает с копией параметра, а передача по ссылке означает, что метод работает с самим параметром.
    
4. **Возвращаемое значение (Return Value)**: Метод может возвращать значение при завершении своего выполнения. Тип возвращаемого значения должен быть объявлен в сигнатуре метода. Ключевое слово `return` используется для возврата значения из метода.
    
5. **Перегрузка методов (Method Overloading)**: Перегрузка методов позволяет определить несколько методов с одним и тем же именем, но с разными наборами параметров. Это позволяет создавать методы с одинаковыми именами, но разными поведениями, в зависимости от переданных параметров.
    

Используя пример кода, который вы предоставили, давайте внесем некоторые изменения, чтобы продемонстрировать некоторые из этих концепций. Давайте добавим перегрузку методов и возвращаемое значение:
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

    // Перегрузка метода ChangePhoneNumber
    public void ChangePhoneNumber(int countryCode, string newPhoneNumber)
    {
        phoneNumber = $"+{countryCode} {newPhoneNumber}";
    }

    // Метод с возвращаемым значением
    public string GetFullName()
    {
        return $"{FirstName} {LastName}";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.GetPersonCount()}");

        // Использование перегруженного метода ChangePhoneNumber
        person1.ChangePhoneNumber(1, "555-999-0000");
        person1.DisplayContactInfo();
        Console.WriteLine($"Full Name: {person1.GetFullName()}");
        Console.WriteLine($"Total persons created: {Person.GetPersonCount()}");
    }
}
```
## ref, out параметры
Модификаторы `ref` и `out` используются для передачи аргументов методам по ссылке вместо копирования значений. Их использование особенно полезно, когда требуется изменить значение переменной в вызывающем коде из вызванного метода. Основные различия между ними заключаются в том, что переменная, переданная с модификатором `ref`, должна быть инициализирована перед передачей в метод, в то время как переменная, переданная с модификатором `out`, может оставаться неинициализированной и должна быть инициализирована в методе перед возвратом.

Давайте изменим ваш код, чтобы продемонстрировать использование модификаторов `ref` и `out`:
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

    // Перегрузка метода ChangePhoneNumber
    public void ChangePhoneNumber(int countryCode, string newPhoneNumber)
    {
        phoneNumber = $"+{countryCode} {newPhoneNumber}";
    }

    // Метод, использующий модификатор ref
    public void ModifyAge(ref int newAge)
    {
        if (newAge > 0)
        {
            Age = newAge;
        }
        else
        {
            Console.WriteLine("Invalid age input.");
        }
    }

    // Метод, использующий модификатор out
    public void GetNextAge(out int nextAge)
    {
        nextAge = Age + 1;
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        int newAge = 35;
        Console.WriteLine($"Initial age: {person1.Age}");

        // Использование модификатора ref
        person1.ModifyAge(ref newAge);
        Console.WriteLine($"New age after modification: {person1.Age}");

        // Использование модификатора out
        int nextAge;
        person1.GetNextAge(out nextAge);
        Console.WriteLine($"Next age: {nextAge}");
    }
}

```
В этом примере были добавлены два метода: `ModifyAge` использует модификатор `ref`, чтобы изменить значение переменной `newAge`, переданной в метод, а метод `GetNextAge` использует модификатор `out`, чтобы возвращать новое значение, не инициализируя его перед вызовом метода. В `Main` методе были внесены соответствующие изменения для демонстрации использования этих модификаторов.
# Создание методов с переменным количеством аргументов

```C#
class Program
{
	static void Main(string[] args)
	{
		Console.WriteLine("Сумма = " + Sum(new int[] { 1,
			2, 3, 4, 5 }));
	}
	private static int Sum(int[] arr)
	{
		int res = 0;
		foreach (int i in arr)
		res += i;
		return res;
	}
}
```
Ключевое слово `params` в C# позволяет определить метод с переменным числом аргументов одного типа. Это позволяет методу принимать переменное количество аргументов одного типа, не требуя явного указания количества аргументов при вызове метода. Это удобно, когда необходимо передать переменное количество аргументов в метод.
```C#
class Program
{
	static void Main(string[] args)
	{
		Console.WriteLine("Сумма = " + Sum( 1,
			2, 3, 4, 5 ));
	}
	private static int Sum(params int[] arr)
	{
		int res = 0;
		foreach (int i in arr)
		res += i;
		return res;
	}
}
```

# Свойства
В C# свойства позволяют создавать удобные методы доступа для закрытых полей класса. Они позволяют контролировать доступ к полям, что обеспечивает большую гибкость и безопасность при работе с классами. Свойства позволяют определить методы доступа (геттеры и сеттеры) для чтения и записи значений в поля класса.

Свойства имеют следующие характеристики:

1. **Геттер (Getter)**: Возвращает значение свойства.
2. **Сеттер (Setter)**: Устанавливает значение свойства.

Преимущества использования свойств:

1. Обеспечение контроля доступа к полям класса.
2. Дополнительная логика при получении и установке значений.
3. Легкость в использовании и понимании.

Пример использования свойств в вашем классе Person:
```C#
using System;

class Person
{
    // Поля класса
    private static int personCount = 0; // Статическое поле
    private const string DefaultPhoneNumber = "N/A"; // Константное поле
    private readonly string email; // Неизменяемое поле
    private string phoneNumber; // Изменяемое поле

    // Свойства класса
    public string FirstName { get; set; }
    public string LastName { get; set; }
    public int Age { get; set; }

    public string Email
    {
        get { return email; }
    }

    public static int PersonCount
    {
        get { return personCount; }
    }

    public string PhoneNumber
    {
        get { return phoneNumber; }
        set { phoneNumber = value; }
    }

    // Конструкторы класса
    public Person()
    {
        FirstName = "John";
        LastName = "Doe";
        Age = 30;
        phoneNumber = DefaultPhoneNumber;
        email = "johndoe@email.com";
        personCount++;
    }

    public Person(string firstName, string lastName, int age, string phone, string email)
    {
        FirstName = firstName;
        LastName = lastName;
        Age = age;
        PhoneNumber = phone;
        this.email = email;
        personCount++;
    }

    // Методы класса
    public void DisplayContactInfo()
    {
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {PhoneNumber}");
        Console.WriteLine($"Email: {Email}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.PersonCount}");

        person1.PhoneNumber = "555-999-0000";
        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.PersonCount}");
    }
}
```
В этом примере поля `FirstName`, `LastName`, `Age`, `PhoneNumber` были преобразованы в свойства, а также было добавлено свойство `Email` и статическое свойство `PersonCount`. Конструкторы были изменены для использования свойства `PhoneNumber` вместо прямого доступа к полю.
### Автоматические свойства, инициализация
Автоматические свойства в C# представляют сокращенный синтаксис для создания свойств класса без явного объявления соответствующих закрытых полей. Они автоматически создают закрытые поля во время компиляции, что упрощает их использование и позволяет сосредоточиться на более важных аспектах разработки.

Для создания автоматических свойств в C# используется следующий синтаксис:

csharpCopy code

`public dataType PropertyName { get; set; }`

где:

- `dataType` - тип данных свойства.
- `PropertyName` - имя свойства.

Инициализация автоматических свойств происходит с помощью конструкторов класса или непосредственно при объявлении свойства.

Преобразуем предоставленный вами пример, чтобы продемонстрировать использование автоматических свойств:
```C#
using System;

class Person
{
    // Статическое поле
    private static int personCount = 0;

    // Константное поле
    private const string DefaultPhoneNumber = "N/A";

    // Неизменяемое поле
    private readonly string email = "johndoe@email.com";

    // Изменяемое автоматическое свойство
    public string PhoneNumber { get; set; }

    // Автоматические свойства
    public string FirstName { get; set; } = "John";
    public string LastName { get; set; } = "Doe";
    public int Age { get; set; } = 30;
    public string Email { get { return email; } }

    // Статическое автоматическое свойство
    public static int PersonCount { get { return personCount; } }

    // Конструкторы класса
    public Person()
    {
        personCount++;
        PhoneNumber = DefaultPhoneNumber;
    }

    public Person(string firstName, string lastName, int age, string phone, string email)
    {
        FirstName = firstName;
        LastName = lastName;
        Age = age;
        PhoneNumber = phone;
        personCount++;
    }

    // Методы класса
    public void DisplayContactInfo()
    {
        Console.WriteLine($"Name: {FirstName} {LastName}");
        Console.WriteLine($"Age: {Age}");
        Console.WriteLine($"Phone: {PhoneNumber}");
        Console.WriteLine($"Email: {Email}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Person person1 = new Person();
        Person person2 = new Person("Alice", "Smith", 25, "555-987-6543", "alice@email.com");

        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.PersonCount}");

        person1.PhoneNumber = "555-999-0000";
        person1.DisplayContactInfo();
        Console.WriteLine($"Total persons created: {Person.PersonCount}");
    }
}

```
В этом примере использованы автоматические свойства для определения свойств `FirstName`, `LastName`, `Age` и `Email`, а также использовано автоматическое свойство `PhoneNumber` для представления номера телефона. Инициализация значений осуществляется через конструкторы класса.
### Null-conditional оператор
Понимание Null-conditional оператора в C# является важным аспектом разработки на этом языке. Null-conditional оператор предоставляет удобный способ безопасной навигации по цепочкам объектов, когда один или несколько из них могут быть равны `null`. Он предотвращает возникновение исключений `NullReferenceException` при попытке доступа к членам объекта, который может быть `null`.

Синтаксис Null-conditional оператора в C#:

`object?.SomeMember`

где:

- `object` - объект, доступ к членам которого может быть небезопасным из-за возможного значения `null`.
- `SomeMember` - член объекта, к которому происходит доступ, если `object` не равен `null`.

Основные преимущества использования Null-conditional оператора:

1. **Безопасная навигация**: Позволяет избежать исключений при доступе к членам объекта, который может быть `null`.
2. **Улучшение читаемости кода**: Упрощает проверку на `null` и делает код более лаконичным и понятным.
3. **Уменьшение сложности кода**: Позволяет сократить количество условий проверки на `null` и облегчить чтение и поддержку кода.

Понимание и использование Null-conditional оператора поможет вам писать более безопасный и читаемый код, особенно когда имеется дело с цепочками объектов, которые могут быть `null`. Это важный инструмент для предотвращения ошибок и обеспечения более надежной работы ваших приложений.
# Пространства имен
Пространства имен (namespaces) в языке программирования C# используются для организации и группировки логически связанных классов, интерфейсов, делегатов и других типов. Они предоставляют средство для управления областями видимости и предотвращения конфликтов имен в больших проектах. Пространства имен также позволяют создавать иерархию и группировать код логически для улучшения его читаемости и обеспечения удобного доступа.

Вот некоторые ключевые моменты по использованию пространств имен:

1. **Область видимости**: Пространства имен помогают избежать конфликтов имен, позволяя разработчикам использовать одинаковые имена для различных классов в разных пространствах имен.

2. **Организация кода**: Пространства имен позволяют логически группировать код, что упрощает его организацию и улучшает читаемость.

3. **Повторное использование**: Пространства имен могут содержать множество классов и других типов, которые могут быть повторно использованы в разных частях приложения.

Пример использования пространств имен в C#:

```csharp
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
    }
}
```

В этом примере создаются два пространства имен: `MyNamespace` и `MyOtherNamespace`. Каждое пространство имен содержит собственный класс, который имеет методы для вывода текста. В `Main` методе создаются объекты каждого класса и вызываются соответствующие методы. использование ключевого слова `using` позволяет использовать пространства имен без полного указания их имени при каждом использовании класса.
