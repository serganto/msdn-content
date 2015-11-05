#How to: Display Localized Date and Time Information to Web Users
Because a Web page can be displayed anywhere in the world, operations that parse and format date and time values should not rely on a default format (which most often is the format of the Web server's local culture) when interacting with the user. Instead, Web forms that handle date and time strings input by the user should parse the strings using the user's preferred culture. Similarly, date and time data should be displayed to the user in a format that conforms to the user's culture. This topic shows how to do this.

## To parse date and time strings input by the user

1. Determine whether the string array returned by the [HttpRequest.UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is populated. If it is not, continue to step 6.  
2. If the string array returned by the [UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is populated, retrieve its first element. The first element indicates the user's default or preferred language and region.  
3. Instantiate a [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object that represents the user's preferred culture by calling the[CultureInfo.CultureInfo(String, Boolean)](https://msdn.microsoft.com/en-us/library/7h898a16(v=vs.110).aspx) constructor.  
4. Call either the **TryParse** or the **Parse** method of the [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime(v=vs.110).aspx) or [DateTimeOffset](https://msdn.microsoft.com/en-us/library/system.datetimeoffset(v=vs.110).aspx) type to try the conversion. Use an overload of the **TryParse** or the **Parse** method with a _provider_ parameter, and pass it either of the following: 
    - The [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object created in step 3. 
    - The [DateTimeFormatInfo](https://msdn.microsoft.com/en-us/library/system.globalization.datetimeformatinfo(v=vs.110).aspx) object that is returned by the [DateTimeFormat](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.datetimeformat(v=vs.110).aspx) property of the [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object created in step 3. 
 
5. If the conversion fails, repeat steps 2 through 4 for each remaining element in the string array returned by the[UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property.  
6. If the conversion still fails or if the string array returned by the [UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is empty, parse the string by using the invariant culture, which is returned by the [CultureInfo.InvariantCulture](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.invariantculture(v=vs.110).aspx) property.  

## To parse the local date and time of the user's request

1. Add a [HiddenField](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.hiddenfield(v=vs.110).aspx) control to a Web form.  
2. Create a JavaScript function that handles the **onClick** event of a **Submit** button by writing the current date and time and the local time zone's offset from Coordinated Universal Time (UTC) to the [Value](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.hiddenfield.value(v=vs.110).aspx) property. Use a delimiter (such as a semicolon) to separate the two components of the string.  
3. Use the Web form's [PreRender](https://msdn.microsoft.com/en-us/library/system.web.ui.control.prerender(v=vs.110).aspx) event to inject the function into the HTML output stream by passing the text of the script to the [ClientScriptManager.RegisterClientScriptBlock(Type, String, String, Boolean)](https://msdn.microsoft.com/en-us/library/bahh2fef(v=vs.110).aspx) method.  
4. Connect the event handler to the **Submit** button's **onClick** event by providing the name of the JavaScript function to the **OnClientClick** attribute of the **Submit** button.  
5. Create a handler for the **Submit** button's [Click](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.button.click(v=vs.110).aspx) event.  
6. In the event handler, determine whether the string array returned by the [HttpRequest.UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is populated. If it is not, continue to step 14.  
7. If the string array returned by the [UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is populated, retrieve its first element. The first element indicates the user's default or preferred language and region.  
8. Instantiate a [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object that represents the user's preferred culture by calling the[CultureInfo.CultureInfo(String, Boolean)](https://msdn.microsoft.com/en-us/library/7h898a16(v=vs.110).aspx) constructor.  
9. Pass the string assigned to the [Value](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.hiddenfield.value(v=vs.110).aspx) property to the [Split](https://msdn.microsoft.com/en-us/library/b873y76a(v=vs.110).aspx) method to store the string representation of the user's local date and time and the string representation of the user's local time zone offset in separate array elements.  
10. Call either the [DateTime.Parse](https://msdn.microsoft.com/en-us/library/kc8s65zs(v=vs.110).aspx) or [DateTime.TryParse(String, IFormatProvider, DateTimeStyles, DateTime)](https://msdn.microsoft.com/en-us/library/9h21f14e(v=vs.110).aspx) method to convert the date and time of the user's request to a [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime(v=vs.110).aspx) value. Use an overload of the method with a_provider_ parameter, and pass it either of the following: 
    - The [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object created in step 8. 
    - The [DateTimeFormatInfo](https://msdn.microsoft.com/en-us/library/system.globalization.datetimeformatinfo(v=vs.110).aspx) object that is returned by the [DateTimeFormat](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.datetimeformat(v=vs.110).aspx) property of the [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object created in step 8. 
 
11. If the parse operation in step 10 fails, go to step 13. Otherwise, call the [UInt32.Parse(String)](https://msdn.microsoft.com/en-us/library/b23e5abt(v=vs.110).aspx) method to convert the string representation of the user's time zone offset to an integer.  
12. Instantiate a [DateTimeOffset](https://msdn.microsoft.com/en-us/library/system.datetimeoffset(v=vs.110).aspx) that represents the user's local time by calling the[DateTimeOffset.DateTimeOffset(DateTime, TimeSpan)](https://msdn.microsoft.com/en-us/library/bb351980(v=vs.110).aspx) constructor.  
13. If the conversion in step 10 fails, repeat steps 7 through 12 for each remaining element in the string array returned by the [UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property.  
14. If the conversion still fails or if the string array returned by the [UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is empty, parse the string by using the invariant culture, which is returned by the [CultureInfo.InvariantCulture](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.invariantculture(v=vs.110).aspx) property. Then repeat steps 7 through 12.  

The result is a [DateTimeOffset](https://msdn.microsoft.com/en-us/library/system.datetimeoffset(v=vs.110).aspx) object that represents the local time of the user of your Web page. You can then determine the equivalent UTC by calling the [ToUniversalTime](https://msdn.microsoft.com/en-us/library/system.datetimeoffset.touniversaltime(v=vs.110).aspx) method. You can also determine the equivalent date and time on your Web server by calling the [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](https://msdn.microsoft.com/en-us/library/bb396765(v=vs.110).aspx) method and passing a value of [TimeZoneInfo.Local](https://msdn.microsoft.com/en-us/library/system.timezoneinfo.local(v=vs.110).aspx) as the time zone to convert the time to.

The following example contains both the HTML source and the code for an ASP.NET Web form that asks the user to input a date and time value. A client-side script also writes information on the local date and time of the user's request and the offset of the user's time zone from UTC to a hidden field. This information is then parsed by the server, which returns a Web page that displays the user's input. It also displays the date and time of the user's request using the user's local time, the time on the server, and UTC.

```
<%@ Page Language="C#" %>
<%@ Import Namespace="System.Globalization" %>
<%@ Assembly Name="System.Core" %>

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<script runat="server">

    protected void OKButton_Click(object sender, EventArgs e)
    {
        string locale = "";
        DateTimeStyles styles = DateTimeStyles.AllowInnerWhite | DateTimeStyles.AllowLeadingWhite |
                                       DateTimeStyles.AllowTrailingWhite;
        DateTime inputDate;
        DateTime localDate = DateTime.Now;
        DateTimeOffset localDateOffset = DateTimeOffset.Now;
        int integerOffset;
        bool result = false;

        // Exit if input is absent.
        if (string.IsNullOrEmpty(this.DateString.Text)) return;

        // Hide form elements.
        this.DateForm.Visible = false;

        // Create array of CultureInfo objects
        CultureInfo[] cultures = new CultureInfo[Request.UserLanguages.Length + 1];
        for (int ctr = Request.UserLanguages.GetLowerBound(0); ctr <= Request.UserLanguages.GetUpperBound(0);
             ctr++)
        {
            locale = Request.UserLanguages[ctr];
            if (! string.IsNullOrEmpty(locale))
            {

                // Remove quality specifier, if present.
                if (locale.Contains(";"))
                   locale = locale.Substring(locale.IndexOf(';') -1);
                try
                {
                    cultures[ctr] = new CultureInfo(Request.UserLanguages[ctr], false);
                }
                catch (Exception) { }
            }
            else
            {
                cultures[ctr] = CultureInfo.CurrentCulture;
            }
        }
        cultures[Request.UserLanguages.Length] = CultureInfo.InvariantCulture;
        // Parse input using each culture.
        foreach (CultureInfo culture in cultures)
        {
            result = DateTime.TryParse(this.DateString.Text, culture.DateTimeFormat, styles, out inputDate);
            if (result) break;
        }
        // Display result to user.
        if (result)
        {
            Response.Write("<P />");
            Response.Write("The date you input was " + Server.HtmlEncode(this.DateString.Text) + "<BR />");
        }
        else
        {
            // Unhide form.
            this.DateForm.Visible = true;
            Response.Write("<P />");
            Response.Write("Unable to recognize " + Server.HtmlEncode(this.DateString.Text) + ".<BR />");
        }

        // Get date and time information from hidden field.
        string[] dates= Request.Form["DateInfo"].Split(';');

        // Parse local date using each culture.
        foreach (CultureInfo culture in cultures)
        {
            result = DateTime.TryParse(dates[0], culture.DateTimeFormat, styles, out localDate);
            if (result) break;
        }
        // Parse offset 
        result = int.TryParse(dates[1], out integerOffset);
        // Instantiate DateTimeOffset object representing user's local time
        if (result) 
        {
            try
            {
                localDateOffset = new DateTimeOffset(localDate, new TimeSpan(0, -integerOffset, 0));
            }
            catch (Exception)
            {
                result = false;
            }
        }
        // Display result to user.
        if (result)
        {
            Response.Write("<P />");
            Response.Write("Your local date and time is " + localDateOffset.ToString() + ".<BR />");
            Response.Write("The date and time on the server is " + 
                           TimeZoneInfo.ConvertTime(localDateOffset, 
                                                    TimeZoneInfo.Local).ToString() + ".<BR />");
            Response.Write("Coordinated Universal Time is " + localDateOffset.ToUniversalTime().ToString() + ".<BR />");
        }
        else
        {
            Response.Write("<P />");
            Response.Write("Unable to recognize " + Server.HtmlEncode(dates[0]) + ".<BR />");
        }
    }

    protected void Page_PreRender(object sender, System.EventArgs e)
    {
        string script = "function AddDateInformation() { \n" +
                  "var today = new Date();\n" +
                  "document.DateForm.DateInfo.value = today.toLocaleString() + \";\" + today.getTimezoneOffset();\n" +
                  " }";
        // Register client script
        ClientScriptManager scriptMgr = Page.ClientScript;
        scriptMgr.RegisterClientScriptBlock(this.GetType(), "SubmitOnClick", script, true);
    }

</script>

<html xmlns="http://www.w3.org/1999/xhtml">
<head id="Head1" runat="server">
    <title>Parsing a Date and Time Value</title>
</head>
<body>
    <form id="DateForm" runat="server">
    <div>
    <center>
       <asp:Label ID="Label1" runat="server" Text="Enter a Date and Time:" Width="248px"></asp:Label>
       <asp:TextBox ID="DateString" runat="server" Width="176px"></asp:TextBox><br />
    </center>       
    <br />
    <center>
    <asp:Button ID="OKButton" runat="server" Text="Button"  
            OnClientClick="AddDateInformation()" onclick="OKButton_Click" />
    <asp:HiddenField ID="DateInfo"  Value=""  runat="server" />
    </center>
    <br />
    </div>
    </form>
</body>
</html>
```
The client-side script calls the JavaScript **toLocaleString** method. This produces a string that follows the formatting conventions of the user's locale, which is more likely to be successfully parsed on the server.

The [HttpRequest.UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) property is populated from the culture names that are contained in **Accept-Language**headers included in an HTTP request. However, not all browsers include **Accept-Language** headers in their requests, and users can also suppress the headers completely. This makes it important to have a fallback culture when parsing user input. Typically the fallback culture is the invariant culture returned by [CultureInfo.InvariantCulture](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.invariantculture(v=vs.110).aspx). Users can also provide Internet Explorer with culture names that they input in a text box, which creates the possibility that the culture names may not be valid. This makes it important to use exception handling when instantiating a [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object.

When retrieved from an HTTP request submitted by Internet Explorer, the [HttpRequest.UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx) array is populated in order of user preference. The first element in the array contains the name of the user's primary culture/region. If the array contains any additional items, Internet Explorer arbitrarily assigns them a quality specifier, which is delimited from the culture name by a semicolon. For example, an entry for the fr-FR culture might take the form**fr-FR;q=0.7**.

The example calls the [CultureInfo](https://msdn.microsoft.com/en-us/library/7h898a16(v=vs.110).aspx) constructor with its _useUserOverride_ parameter set to **false** to create a new [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx)object. This ensures that, if the culture name is the default culture name on the server, the new [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object created by the class constructor contains a culture's default settings and does not reflect any settings overridden by using the server's **Regional and Language Options** application. The values from any overridden settings on the server are unlikely to exist on the user's system or to be reflected in the user's input.

Because this example parses two string representations of a date and time (one input by the user, the other stored to the hidden field), it defines the possible [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) objects that may be required in advance. It creates an array of[CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) objects that is one greater than the number of elements returned by the [HttpRequest.UserLanguages](https://msdn.microsoft.com/en-us/library/system.web.httprequest.userlanguages(v=vs.110).aspx)property. It then instantiates a [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx) object for each language/region string, and also instantiates a [CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo(v=vs.110).aspx)object that represents [CultureInfo.InvariantCulture](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.invariantculture(v=vs.110).aspx).

Your code can call either the [Parse](https://msdn.microsoft.com/en-us/library/kc8s65zs(v=vs.110).aspx) or the [TryParse](https://msdn.microsoft.com/en-us/library/9h21f14e(v=vs.110).aspx) method to convert the user's string representation of a date and time to a [DateTime](https://msdn.microsoft.com/en-us/library/system.datetime(v=vs.110).aspx) value. Repeated calls to a parse method may be required for a single parsing operation. As a result, the[TryParse](https://msdn.microsoft.com/en-us/library/9h21f14e(v=vs.110).aspx) method is better because it returns **false** if a parse operation fails. In contrast, handling the repeated exceptions that may be thrown by the [Parse](https://msdn.microsoft.com/en-us/library/kc8s65zs(v=vs.110).aspx) method can be a very expensive proposition in a Web application.

## Compiling the Code

To compile the code, create an ASP.NET Web page without a code-behind. Then copy the example into the Web page so that it replaces all the existing code. The ASP.NET Web page should contain the following controls:

- A [Label](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.label(v=vs.110).aspx) control, which is not referenced in code. Set its [Text](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.textbox.text(v=vs.110).aspx) property to "Enter a Number:". 
- A [TextBox](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.textbox(v=vs.110).aspx) control named DateString. 
- A [Button](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.button(v=vs.110).aspx) control named OKButton. Set its [Text](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.button.text(v=vs.110).aspx) property to "OK". 
- A [HiddenField](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.hiddenfield(v=vs.110).aspx) control named DateInfo. 

## .NET Framework Security

To prevent a user from injecting script into the HTML stream, user input should never be directly echoed back in the server response. Instead, it should be encoded by using the [HttpServerUtility.HtmlEncode](https://msdn.microsoft.com/en-us/library/w3te6wfz(v=vs.110).aspx) method.

## [See Also]()

[Performing Formatting Operations](https://msdn.microsoft.com/en-us/library/bb762912(v=vs.110).aspx)  
[Standard Date and Time Format Strings](https://msdn.microsoft.com/en-us/library/az4se3k1(v=vs.110).aspx)  
[Custom Date and Time Format Strings](https://msdn.microsoft.com/en-us/library/8kb3ddd4(v=vs.110).aspx)  
[Parsing Date and Time Strings in the .NET Framework](https://msdn.microsoft.com/en-us/library/2h3syy57(v=vs.110).aspx)