
[Source](https://msdn.microsoft.com/en-us/library/w7xf6dxs.aspx "Permalink to Compiler Error CS0246")

# Compiler Error CS0246

The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)

A type or namespace that is used in the program was not found. You might have forgotten to reference ([/reference][2]) the assembly that contains the type, or you might not have correctly qualified its use by using a [using directive][3].

The following situations cause compiler error CS0246.

* Did you misspell the name of the type or namespace? Without the correct name, the compiler cannot find the definition for the type or namespace. This often occurs because the casing used in the name of the type is not correct. For example, Dataset ds; generates CS0246 because the s in Dataset must be capitalized.
* If the error is for a namespace name, did you add a reference ([/reference][2]) to the assembly that contains the namespace? For example, your code might contain the directive using Accessibility. However, if your project does not reference the assembly Accessibility.dll, error CS0246 is reported.
* If the error is for a type name, did you include the proper [using][4] directive, or, alternatively, fully qualify the name of the type? Consider the following declaration: DataSet ds. To use the **DataSet** type, you need two things. First, you need a reference to the assembly that contains the definition for the **DataSet** type. Second, you need a **using** directive for the namespace where **DataSet** is located. For example, because **DataSet** is located in the **System.Data** namespace, you need the following directive at the beginning of your code: using System.Data.

The **using** directive is not required. However, if you omit the directive, you must fully qualify the **DataSet** type when referring to it. Full qualification means that you specify both the namespace and the type each time you refer to the type in your code. If you omit the **using** directive in the previous example, you must write System.Data.DataSet ds to declare ds instead of DataSet ds.
* Did you use a variable or some other language element where a type was expected? For example, in an **is** statement, if you use a **Type** object instead of an actual type, you get error CS0246.
* Did you use a _using alias directive_ without fully qualifying the type name? A **using** alias directive does not use the **using** directives in the source code file to resolve types. The following example generates CS0246 because the type List<int> is not fully qualified. The **using** directive for System.Collections.Generic does not prevent the error.
```
    using System.Collections.Generic;

    // The following declaration generates CS0246.
    using myAliasName = List<int>;

    // To avoid the error, fully qualify List.
    using myAliasName2 = System.Collections.Generic.List<int>;
```
The following example generates CS0246 because a necessary **using** directive is missing.
```
    // CS0246.cs
    //using System.Diagnostics;

    public class MyClass
    {
        // The following line causes CS0246. To fix the error, uncomment
        // the using directive for the namespace for this attribute,
        // System.Diagnostics.
        [Conditional("A")]
        public void Test()
        {
        }

        public static void Main()
        {
        }
    }
```
The following example causes CS0246 because an object of type **Type** was used where an actual type was expected.
```
    // CS0246b.cs
    using System;

    class ExampleClass
    {
        public bool supports(object o, Type t)
        {
            // The following line causes CS0246. You must use an
            // actual type, such as ExampleClass, String, or Type.
            if (o is t)
            {
                return true;
            }
            return false;
        }
    }

    class Program
    {
        public static void Main()
        {
            ExampleClass myC = new ExampleClass();
            myC.supports(myC, myC.GetType());
        }
    }
```
[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/yabyz3h4.aspx
[3]: https://msdn.microsoft.com/en-us/library/sf0df423.aspx
[4]: https://msdn.microsoft.com/en-us/library/zhdeatwt.aspx
  </int></int></int>