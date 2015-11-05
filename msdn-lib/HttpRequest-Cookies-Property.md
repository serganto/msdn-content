
[Source](https://msdn.microsoft.com/en-us/library/tekf049c(l=en-us,v=vs.110).aspx "Permalink to HttpRequest.Cookies Property (System.Web)")

# HttpRequest.Cookies Property (System.Web)

Gets a collection of cookies sent by the client.

**Namespace:**
[System.Web][2]  
**Assembly:**
System.Web (in System.Web.dll)
##Syntax
    public HttpCookieCollection Cookies { get; }

####Property Value
Type: [System.Web.HttpCookieCollection][7]

An [HttpCookieCollection][8] object representing the client's cookie variables.

##Remarks
ASP.NET includes two intrinsic cookie collections. The collection accessed through the Cookies collection of [HttpRequest][3] contains cookies transmitted by the client to the server in the **Cookie** header. The collection accessed through the [Cookies][4] collection of [HttpResponse][5] contains new cookies created on the server and transmitted to the client in the **Set-Cookie** header.

>After you add a cookie by using the [HttpResponse.Cookies][4] collection, the cookie is immediately available in the HttpRequest.Cookies collection, even if the response has not been sent to the client.

The following code example loops through all cookies sent by the client and sends the name, expiration date, security parameter, and values of each cookie to the HTTP output.

    int loop1, loop2;
    HttpCookieCollection MyCookieColl;
    HttpCookie MyCookie;

    MyCookieColl = Request.Cookies;

    // Capture all cookie names into a string array.
    String[] arr1 = MyCookieColl.AllKeys;

    // Grab individual cookie objects by cookie name.
    for (loop1 = 0; loop1 &lt; arr1.Length; loop1++)
    {
       MyCookie = MyCookieColl[arr1[loop1]];
       Response.Write("Cookie: " + MyCookie.Name + "<br>");
       Response.Write ("Secure:" + MyCookie.Secure + "<br>");

       //Grab all values for single cookie into an object array.
       String[] arr2 = MyCookie.Values.AllKeys;

       //Loop through cookie Value collection and print all values.
       for (loop2 = 0; loop2 &lt; arr2.Length; loop2++)
       {
          Response.Write("Value" + loop2 + ": " + Server.HtmlEncode(arr2[loop2]) + "<br>");
       }
    }

##Version Information
**.NET Framework**  
Available since 1.1  

##See Also
<p><a href="https://msdn.microsoft.com/en-us/library/system.web.httprequest.validateinput(v=vs.110).aspx">ValidateInput</a><br><a href="https://msdn.microsoft.com/en-us/library/system.web.httprequest.form(v=vs.110).aspx"><span xmlns="">Form</span></a><br><a href="https://msdn.microsoft.com/en-us/library/system.web.httprequest.querystring(v=vs.110).aspx"><span xmlns="">QueryString</span></a><br><a href="https://msdn.microsoft.com/en-us/library/system.web.httprequest(v=vs.110).aspx">HttpRequest Class</a><br><a href="https://msdn.microsoft.com/en-us/library/system.web(v=vs.110).aspx">System.Web Namespace</a><br></p>

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.web(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.web.httprequest(v=vs.110).aspx
[4]: https://msdn.microsoft.com/en-us/library/system.web.httpresponse.cookies(v=vs.110).aspx
[5]: https://msdn.microsoft.com/en-us/library/system.web.httpresponse(v=vs.110).aspx
[6]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.jpeg "System_CAPS_note"
[7]: https://msdn.microsoft.com/en-us/library/system.web.httpcookiecollection(v=vs.110).aspx
[8]: https://msdn.microsoft.com/en-us/library/system.web.httpcookiecollection(v=vs.110).aspx