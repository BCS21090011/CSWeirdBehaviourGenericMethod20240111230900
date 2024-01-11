# CSWeirdBehaviourGenericMethod20240111230900

## Which is the output for this code?

Code:

```C#
using System;
using System.Collections.Generic;

public class HelloWorld
{
    public static void Main(string[] args)
    {
        Console.WriteLine("Hello world!");
        Console.WriteLine();
        
        Methods obj = new Methods();
        
        Methods.Display("Not List:");
        Methods.DownIndentationLvl();
        Methods.Display("int:");
        Methods.DownIndentationLvl();
        obj.Func(3);
        Methods.UpIndentationLvl();
        Methods.Display("string");
        Methods.DownIndentationLvl();
        obj.Func("String");
        Methods.UpIndentationLvl(2);
        
        Console.WriteLine();
        
        Methods.Display("List:");
        Methods.DownIndentationLvl();
        Methods.Display("ints:");
        List<int> ints = new List<int>{1, 2, 3};
        Methods.DownIndentationLvl();
        obj.Func(ints);
        Methods.UpIndentationLvl(2);
        
        Console.WriteLine();

        Methods.Display("List of lists:");
        Methods.DownIndentationLvl();
        Methods.Display("lstInts:");
        List<List<int>> lstInts = new List<List<int>>{
            new List<int>{1, 2, 3},
            new List<int>{4, 5, 6},
            new List<int>{7, 8, 9}
        };
        Methods.DownIndentationLvl();
        obj.Func(lstInts);
        Methods.UpIndentationLvl(2);
        
        Console.WriteLine();
        Console.WriteLine("Bye world!");
    }
}

public class Methods
{
    private static int _indentationLvl = 0;
    
    public static void Display(string text, string indent="->")
    {
        string indents = "";
        
        for(int i=0; i<_indentationLvl; i++)
        {
            indents += indent;
        }
        
        Console.WriteLine($"{indents}{text}");
    }
    
    public static void UpIndentationLvl(int lvlCount=1)
    {
        _indentationLvl -= lvlCount;
        
        // Ensure lvl >= 0.
        if(_indentationLvl < 0)
        {
            _indentationLvl = 0;
        }
    }
    
    public static void DownIndentationLvl(int lvlCount=1)
    {
        _indentationLvl += lvlCount;
    }
    
    public void Func<T>(T value)
    {
        Display($"Type: [{typeof(T)}]\tValue: [{value}]");
    }
    
    public void Func<T>(List<T> lst)
    {
        for(int i=0; i<lst.Count; i++)
        {
            Display($"i: {i}");
            DownIndentationLvl();
            this.Func(lst[i]);
            UpIndentationLvl();
        }
    }
}
```

* [ ] Output A:
    ```Output
    Hello world!
    
    Not List:
    ->int:
    ->->Type: [System.Int32]	Value: [3]
    ->string
    ->->Type: [System.String]	Value: [String]
    
    List:
    ->ints:
    ->->Type: [System.Collections.Generic.List`1[System.Int32]]	Value: [System.Collections.Generic.List`1[System.Int32]]
    
    List of lists:
    ->lstInts:
    ->->Type: [System.Collections.Generic.List`1[System.Collections.Generic.List`1[System.Int32]]]	Value: [System.Collections.Generic.List`1[System.Collections.Generic.List`1[System.Int32]]]
    
    Bye world!
    ```

* [ ] Output B: 
  ```Output
  Hello world!
  
  Not List:
  ->int:
  ->->Type: [System.Int32]	Value: [3]
  ->string
  ->->Type: [System.String]	Value: [String]
  
  List:
  ->ints:
  ->->i: 0
  ->->->Type: [System.Int32]	Value: [1]
  ->->i: 1
  ->->->Type: [System.Int32]	Value: [2]
  ->->i: 2
  ->->->Type: [System.Int32]	Value: [3]
  
  List of lists:
  ->lstInts:
  ->->i: 0
  ->->->Type: [System.Collections.Generic.List`1[System.Int32]]	Value: [System.Collections.Generic.List`1[System.Int32]]
  ->->i: 1
  ->->->Type: [System.Collections.Generic.List`1[System.Int32]]	Value: [System.Collections.Generic.List`1[System.Int32]]
  ->->i: 2
  ->->->Type: [System.Collections.Generic.List`1[System.Int32]]	Value: [System.Collections.Generic.List`1[System.Int32]]
  
  Bye world!
  ```

* [ ] Output C:
  ```Output
  Hello world!
  
  Not List:
  ->int:
  ->->Type: [System.Int32]	Value: [3]
  ->string
  ->->Type: [System.String]	Value: [String]
  
  List:
  ->ints:
  ->->i: 0
  ->->->Type: [System.Int32]	Value: [1]
  ->->i: 1
  ->->->Type: [System.Int32]	Value: [2]
  ->->i: 2
  ->->->Type: [System.Int32]	Value: [3]
  
  List of lists:
  ->lstInts:
  ->->i: 0
  ->->->i: 0
  ->->->->Type: [System.Int32]	Value: [1]
  ->->->i: 1
  ->->->->Type: [System.Int32]	Value: [2]
  ->->->i: 2
  ->->->->Type: [System.Int32]	Value: [3]
  ->->i: 1
  ->->->i: 0
  ->->->->Type: [System.Int32]	Value: [4]
  ->->->i: 1
  ->->->->Type: [System.Int32]	Value: [5]
  ->->->i: 2
  ->->->->Type: [System.Int32]	Value: [6]
  ->->i: 2
  ->->->i: 0
  ->->->->Type: [System.Int32]	Value: [7]
  ->->->i: 1
  ->->->->Type: [System.Int32]	Value: [8]
  ->->->i: 2
  ->->->->Type: [System.Int32]	Value: [9]
  
  Bye world!
  ```
