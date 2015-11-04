[Source](https://msdn.microsoft.com/en-us/library/z5z9kes2.aspx "Permalink to implicit (C# Reference)")

# implicit (C# Reference)


The **implicit** keyword is used to declare an implicit user-defined type conversion operator. Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.

    public class PowersOf2
    {
        static void Main()
        {
            // Display powers of 2 up to the exponent of 8:
            foreach (int i in Power(2, 8))
            {
                Console.Write("{0} ", i);
            }
        }

        public static System.Collections.Generic.IEnumerable Power(int number, int exponent)
        {
            int result = 1;

            for (int i = 0; i < exponent; i++)
            {
                result = result * number;
                yield return result;
            }
        }

        // Output: 2 4 8 16 32 64 128 256
    }

By eliminating unnecessary casts, implicit conversions can improve source code readability. However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results. In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness. If a conversion operator cannot meet those criteria, it should be marked explicit. For more information, see [Using Conversion Operators][3].

##C# Language Specification
For more information, see the [C# Language Specification][2]. The language specification is the definitive source for C# syntax and usage.

##See Also
[C# Reference][4]

[C# Programming Guide][5]

[C# Keywords][6]

[explicit (C# Reference)][7]

[operator (C# Reference)][8]

[How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)][9]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/ms228593.aspx
[3]: https://msdn.microsoft.com/en-us/library/85w54y0a.aspx

[4]: https://msdn.microsoft.com/en-us/library/618ayhy6.aspx
[5]: https://msdn.microsoft.com/en-us/library/67ef8sbd.aspx
[6]: https://msdn.microsoft.com/en-us/library/67ef8sbd.aspx
[7]: https://msdn.microsoft.com/en-us/library/xhbhezf4.aspx
[8]: https://msdn.microsoft.com/en-us/library/s53ehcz3.aspx
[9]: https://msdn.microsoft.com/en-us/library/s53ehcz3.aspx