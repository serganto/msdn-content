
[Source](https://msdn.microsoft.com/en-us/library/system.collections.ienumerable(v=vs.110).aspx)

# IEnumerable Interface (System.Collections)

Exposes an enumerator, which supports a simple iteration over a non-generic collection.

To browse the .NET Framework source code for this type, see the [Reference Source][2].

**Namespace: **[System.Collections][3]  

**Assembly: **mscorlib (in mscorlib.dll)

##Syntax

    [GuidAttribute("496B0ABE-CDEE-11d3-88E8-00902754C43A")]
    [ComVisibleAttribute(true)]
    public interface IEnumerable

##Methods
| Name | Description |
| :----- | :----- |
| [GetEnumerator()][5] | Returns an enumerator that iterates through a collection.|

##Extension Methods

<table id="idExtensionMethods">
<tbody>
<tr>
<th class="iconColumn"></th>
<th class="nameColumn">Name</th>
<th class="descriptionColumn">Description</th>
</tr><tr><td><span><img id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-pubmethod" alt="System_CAPS_pubmethod" src="https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg" title="System_CAPS_pubmethod" xmlns=""></span></td><td><a href="https://msdn.microsoft.com/en-us/library/dd413237(v=vs.110).aspx">AsParallel<span xmlns="">()</span></a></td><td><div class="section"><p>Overloaded. Enables parallelization of a query.(Defined by <a href="https://msdn.microsoft.com/en-us/library/system.linq.parallelenumerable(v=vs.110).aspx">ParallelEnumerable</a>.)</p></div></td></tr><tr><td><span><img id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-pubmethod" alt="System_CAPS_pubmethod" src="https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg" title="System_CAPS_pubmethod" xmlns=""></span></td><td><a href="https://msdn.microsoft.com/en-us/library/bb353734(v=vs.110).aspx">AsQueryable<span xmlns="">()</span></a></td><td><div class="section"><p>Overloaded. Converts an <span class="selflink">IEnumerable</span> to an <a href="https://msdn.microsoft.com/en-us/library/system.linq.iqueryable(v=vs.110).aspx">IQueryable</a>.(Defined by <a href="https://msdn.microsoft.com/en-us/library/system.linq.queryable(v=vs.110).aspx">Queryable</a>.)</p></div></td></tr><tr><td><span><img id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-pubmethod" alt="System_CAPS_pubmethod" src="https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg" title="System_CAPS_pubmethod" xmlns=""></span></td><td><a href="https://msdn.microsoft.com/en-us/library/bb341406(v=vs.110).aspx">Cast<span xmlns="">&lt;TResult&gt;</span><span xmlns="">()</span></a></td><td><div class="section"><p>Casts the elements of an <span class="selflink">IEnumerable</span> to the specified type.(Defined by <a href="https://msdn.microsoft.com/en-us/library/system.linq.enumerable(v=vs.110).aspx">Enumerable</a>.)</p></div></td></tr><tr><td><span><img id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-pubmethod" alt="System_CAPS_pubmethod" src="https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg" title="System_CAPS_pubmethod" xmlns=""></span></td><td><a href="https://msdn.microsoft.com/en-us/library/bb360913(v=vs.110).aspx">OfType<span xmlns="">&lt;TResult&gt;</span><span xmlns="">()</span></a></td><td><div class="section"><p>Filters the elements of an <span class="selflink">IEnumerable</span> based on a specified type.(Defined by <a href="https://msdn.microsoft.com/en-us/library/system.linq.enumerable(v=vs.110).aspx">Enumerable</a>.)</p></div></td></tr></tbody></table>

##Remarks
>To view the .NET Framework source code for this type, see the [Reference Source][2]. You can browse through the source code online, download the reference for offline viewing, and step through the sources (including patches and updates) during debugging; see [instructions][7].

IEnumerable is the base interface for all non-generic collections that can be enumerated. For the generic version of this interface see [System.Collections.Generic.IEnumerable<t>][8]. IEnumerable contains a single method, [GetEnumerator][5], which returns an [IEnumerator][9]. [IEnumerator][9] provides the ability to iterate through the collection by exposing a [Current][10] property and [MoveNext][11] and [Reset][12] methods.

It is a best practice to implement IEnumerable and [IEnumerator][9] on your collection classes to enable the **foreach** (**For Each** in Visual Basic) syntax, however implementing IEnumerable is not required. If your collection does not implement IEnumerable, you must still follow the iterator pattern to support this syntax by providing a **GetEnumerator** method that returns an interface, class or struct. When using Visual Basic, you must provide an [IEnumerator][9] implementation, which is returned by **GetEnumerator**. When developing with C# you must provide a class that contains a **Current** property, and **MoveNext** and **Reset** methods as described by [IEnumerator][9], but the class does not have to implement [IEnumerator][9].

##Examples
The following code example demonstrates the best practice for iterating a custom collection by implementing the IEnumerable and [IEnumerator][9] interfaces. In this example, members of these interfaces are not explicitly called, but they are implemented to support the use of **foreach** (**For Each** in Visual Basic) to iterate through the collection. This example is a complete Console app. To compile the Visual Basic app, change the **Startup object** to **Sub Main** in the project's **Properties** page.

For a sample that shows how to implement the IEnumerable interface, see [Implementing the IEnumerable Interface in a Collection Class][13]

    using System;
    using System.Collections;

    // Simple business object.
    public class Person
    {
        public Person(string fName, string lName)
        {
            this.firstName = fName;
            this.lastName = lName;
        }

        public string firstName;
        public string lastName;
    }

    // Collection of Person objects. This class
    // implements IEnumerable so that it can be used
    // with ForEach syntax.
    public class People : IEnumerable
    {
        private Person[] _people;
        public People(Person[] pArray)
        {
            _people = new Person[pArray.Length];

            for (int i = 0; i &lt; pArray.Length; i++)
            {
                _people[i] = pArray[i];
            }
        }

    // Implementation for the GetEnumerator method.
        IEnumerator IEnumerable.GetEnumerator()
        {
           return (IEnumerator) GetEnumerator();
        }

        public PeopleEnum GetEnumerator()
        {
            return new PeopleEnum(_people);
        }
    }

    // When you implement IEnumerable, you must also implement IEnumerator.
    public class PeopleEnum : IEnumerator
    {
        public Person[] _people;

        // Enumerators are positioned before the first element
        // until the first MoveNext() call.
        int position = -1;

        public PeopleEnum(Person[] list)
        {
            _people = list;
        }

        public bool MoveNext()
        {
            position++;
            return (position &lt; _people.Length);
        }

        public void Reset()
        {
            position = -1;
        }

        object IEnumerator.Current
        {
            get
            {
                return Current;
            }
        }

        public Person Current
        {
            get
            {
                try
                {
                    return _people[position];
                }
                catch (IndexOutOfRangeException)
                {
                    throw new InvalidOperationException();
                }
            }
        }
    }

    class App
    {
        static void Main()
        {
            Person[] peopleArray = new Person[3]
            {
                new Person("John", "Smith"),
                new Person("Jim", "Johnson"),
                new Person("Sue", "Rabon"),
            };

            People peopleList = new People(peopleArray);
            foreach (Person p in peopleList)
                Console.WriteLine(p.firstName + " " + p.lastName);

        }
    }

    /* This code produces output similar to the following:
     *
     * John Smith
     * Jim Johnson
     * Sue Rabon
     *
     */

**Universal Windows Platform**

Available since 4.5

  
**.NET Framework**

Available since 1.1

  
**Portable Class Library**

Supported in:

[portable .NET platforms][14]  
**Silverlight**

Available since 2.0

  
**Windows Phone Silverlight**

Available since 7.0

  
**Windows Phone**

Available since 8.1

  
##See Also
<p><a href="https://msdn.microsoft.com/en-us/library/system.collections.ienumerator(v=vs.110).aspx">IEnumerator</a><br><a href="https://msdn.microsoft.com/en-us/library/9eekhta0(v=vs.110).aspx">System.Collections.Generic<span xmlns="">.</span>IEnumerable<span xmlns="">&lt;T&gt;</span></a><br><a href="https://msdn.microsoft.com/en-us/library/system.collections(v=vs.110).aspx">System.Collections Namespace</a><br><a href="http://code.msdn.microsoft.com/Implementing-the-e1708a24">Implementing the IEnumerable Interface in a Collection Class</a><br><a href="https://msdn.microsoft.com/en-us/library/dscyy5s0(v=vs.110).aspx">Iterators (C# and Visual Basic)</a><br></p>

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: http://referencesource.microsoft.com/#mscorlib/system/collections/ienumerable.cs#9be451ac13d86a97
[3]: https://msdn.microsoft.com/en-us/library/system.collections(v=vs.110).aspx
[4]: https://i-msdn.sec.s-msft.com/dynimg/IC91302.jpeg "System_CAPS_pubmethod"
[5]: https://msdn.microsoft.com/en-us/library/system.collections.ienumerable.getenumerator(v=vs.110).aspx
[6]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.jpeg "System_CAPS_note"
[7]: http://referencesource.microsoft.com/
[8]: https://msdn.microsoft.com/en-us/library/9eekhta0(v=vs.110).aspx
[9]: https://msdn.microsoft.com/en-us/library/system.collections.ienumerator(v=vs.110).aspx
[10]: https://msdn.microsoft.com/en-us/library/system.collections.ienumerator.current(v=vs.110).aspx
[11]: https://msdn.microsoft.com/en-us/library/system.collections.ienumerator.movenext(v=vs.110).aspx
[12]: https://msdn.microsoft.com/en-us/library/system.collections.ienumerator.reset(v=vs.110).aspx
[13]: http://code.msdn.microsoft.com/Implementing-the-e1708a24
[14]: https://msdn.microsoft.com/en-us/library/gg597391.aspx
  </t>