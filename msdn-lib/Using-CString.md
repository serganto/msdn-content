[Source](https://msdn.microsoft.com/en-us/library/ms174288.aspx "Permalink to Using CString")

# Using CString

The topics in this section describe how to program with **CString**. For reference documentation about the **CString** class, see the documentation for [CStringT][1].

To use **CString**, include the **atlstr.h** header.

The **CString**, **CStringA**, and **CStringW** classes are specializations of a class template called [CStringT][1] based on the type of character data they support.

A **CStringW** object contains the **wchar_t** type and supports Unicode strings. A **CStringA** object contains the **char** type, and supports single-byte and multi-byte (MBCS) strings. A **CString** object supports either the **char** type or the **wchar_t** type, depending on whether the **MBCS** symbol or the **UNICODE** symbol is defined at compile time.

A **CString** object keeps character data in a **CStringData** object. **CString** accepts **null**-terminated C-style strings, but does not retain the **null** character in the stored character data. Instead, **CString** tracks string length. **CString** does provide a null terminator when it exports a C-style string. You can insert a **null** in a **CString**, but it may produce unexpected results.

The following set of string classes can be used without linking an MFC library, with or without CRT support: **CAtlString**, **CAtlStringA**, and **CAtlStringW**.

**CString** is used in native projects. For managed-code (C++/CLI) projects, use **System::String**.

To add more capabilities than **CString**, **CStringA**, or **CStringW** currently offer, you should create a subclass of **CStringT** that contains the additional features.

The following code shows how to create a **CString** and print it to standard output:

    #include 

    int main() {
        CString aCString = CString(_T("A string"));
        _tprintf(_T("%s"), (LPCTSTR) aCString);
    }

##In This Section
###[Basic CString Operations][2]
Describes basic CString operations, including creating objects from C literal strings, accessing individual characters in a CString, concatenating two objects, and comparing CString objects.

###[String Data Management][3]
Discusses using Unicode and MBCS with CString.

###[CString Semantics][4]
Explains how CString objects are used.
###[CString Operations Relating to C-Style Strings][5]
Describes manipulating the contents of a CString object like a C-style null-terminated string.
###[Allocating and Releasing Memory for a BSTR][6]
Discusses using memory for a BSTR and COM objects.
###[CString Exception Cleanup][7]
Explains that explicit cleanup in MFC 3.0 and later is no longer necessary.
###[CString Argument Passing][8]
Explains how to pass CString objects to functions and how to return CString objects from functions.
###[Unicode and Multibyte Character Set (MBCS) Support][9]
Discusses how MFC is enabled for Unicode and MBCS support.

###Reference
##[CStringT][10]
Provides reference information about the CStringT class.
##[CSimpleStringT Class][11]
Provides reference information about the CSimpleStringT class.
###Related Sections
##[Strings (ATL/MFC)][12]
Contains links to topics that describe several ways to manage string data.
##[Class Template Instantiation][13]
CString is a typedef based on CStringT, an instance of a specialization of a class template.
##[Strings (ATL/MFC)][14]

[1]: https://msdn.microsoft.com/en-us/library/5bzxfsea.aspx
[2]: https://msdn.microsoft.com/en-us/library/72b2swax.aspx
[3]: https://msdn.microsoft.com/en-us/library/72b2swax.aspx
[4]: https://msdn.microsoft.com/en-us/library/sy280zek.aspx
[5]: https://msdn.microsoft.com/en-us/library/awkwbzyc.aspx
[6]: https://msdn.microsoft.com/en-us/library/xda6xzx7.aspx
[7]: https://msdn.microsoft.com/en-us/library/ky89wkz5.aspx
[8]: https://msdn.microsoft.com/en-us/library/acttytz3.aspx
[9]: https://msdn.microsoft.com/en-us/library/ey142t48.aspx 
[10]: https://msdn.microsoft.com/en-us/library/sddk80xf.aspx
[11]: https://msdn.microsoft.com/en-us/library/sddk80xf.aspx
[12]: https://msdn.microsoft.com/en-us/library/kda99ffc.aspx
[13]: https://msdn.microsoft.com/en-us/library/7y5ca42y.aspx
[14]: https://msdn.microsoft.com/en-us/library/kda99ffc.aspx 