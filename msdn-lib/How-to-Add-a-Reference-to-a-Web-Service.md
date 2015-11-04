[Source](https://msdn.microsoft.com/en-us/library/bb628649.aspx "Permalink to Add a Reference to a Web Service")

# Add a Reference to a Web Service


XML Web Services, also known as ASMX services, were the predecessor of Windows Communication Foundation (WCF). You can access Web services by adding a service reference just as you would for any other WCF service. Any references added in this manner will target the latest version of the .NET Framework.

For applications that were created in an earlier version of Visual Studio, you can still add a Web reference that targets version 2.0 of the .NET Framework. To do this, follow the procedure that is described in the following section.

### To add a Web reference to a project

1. In Solution Explorer, right-click the name of the project that you want to add the service to, and then click Add Service Reference.

The Add Service Reference dialog box appears.

2. In the Add Service Reference dialog box, click the Advanced button.

The Service Reference Settings dialog box appears.

3. In the Service Reference Settings dialog box, click Add Web Reference.

The Add Web Reference dialog box appears.

4. In the URL box, enter the URL of the Web service to use. If you do not know the URL, use the links in the browse pane to locate the Web service you want.

>If you are developing a Web application on a computer that is behind a firewall, and your application will consume Web services from outside the firewall, you must include the address and port of your network's proxy server in the URL. Ask your network administrator to furnish this part of the URL path. For more information, see [The proxy settings on this computer are not configured correctly for Web discovery.][3].

5. In the Web services found at this URL box, select the Web service to use.

6. Verify that your project can use the Web service, and that any external code provided is trustworthy.

>When you open a project for editing that includes a Web reference, a local proxy file for the Web service consumed runs in a process of Devenv.exe started by a trusted user, yourself. Opening projects or components in the integrated development environment (IDE) can execute code on the local computer. For more information, see [Code Access Security][5].


7. In the Web reference name field, enter a name that you will use in your code to access the selected Web service programmatically.

>By default, Web references are assigned a namespace that corresponds to their server name. You can change this value and enter a custom namespace name. There are some limitations on acceptable namespace names. For more information about characters that are not allowed in a Web reference name, see [Add Web Reference Dialog Box][6]. A namespace based on the Web reference name is created by building a nested folder hierarchy. Inside the innermost folder, a .wsdl file that references the Web service is created, together with supporting files, such as discovery (.disco and .discomap) files, that include information about where the Web service is located.


8. Click Add Reference.

If your project site does not already have one, Visual Studio creates a WebReferences folder. It then creates files that are required for the proxy class using the name that you provided in step 7.

##See Also
#### Tasks
[How to: Add, Update, or Remove a Service Reference][7]
#### Reference
[Add Service Reference Dialog Box][8]
#### Concepts
[Windows Communication Foundation Services and WCF Data Services in Visual Studio][9]
#### Other Resources
[Consuming ASMX and WCF Services Sample][10]

[Web References in Visual Studio][11]

[2]: https://i-msdn.sec.s-msft.com/areas/global/content/clear.gif "Note"
[3]: https://msdn.microsoft.com/en-us/library/03seed2h.aspx
[4]: https://i-msdn.sec.s-msft.com/areas/global/content/clear.gif "Security note"
[5]: https://msdn.microsoft.com/en-us/library/930b76w0.aspx
[6]: https://msdn.microsoft.com/en-us/library/8dcbc50t.aspx

[7]: https://msdn.microsoft.com/en-us/library/bb628652.aspx
[8]: https://msdn.microsoft.com/en-us/library/bb386382.aspx
[9]: https://msdn.microsoft.com/en-us/library/bb907578.aspx
[10]: https://msdn.microsoft.com/en-us/library/bb384510.aspx
[11]: https://msdn.microsoft.com/en-us/library/tydxdyw9.aspx
