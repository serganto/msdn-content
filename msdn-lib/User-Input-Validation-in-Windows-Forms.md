
[Source](https://msdn.microsoft.com/en-us/library/ms229603(v=vs.110).aspx)

# User Input Validation in Windows Forms



When users enter data into your application, you may want to verify that the data is valid before your application uses it. You may require that certain text fields not be zero-length, that a field be formatted as a telephone number or other type of well-formed data, or that a string not contain any unsafe characters that could be used to compromise the security of a database. Windows Forms provides several ways for you to validate input in your application.

##Validation with the MaskedTextBox Control
If you need to require users to enter data in a well-defined format, such as a telephone number or a part number, you can accomplish this quickly and with minimal code by using the [MaskedTextBox][2] control. A _mask_ is a string made up of characters from a masking language that specifies which characters can be entered at any given position in the text box. The control displays a set of prompts to the user. If the user types an incorrect entry, for example, the user types a letter when a digit is required, the control will automatically reject the input.

The masking language that is used by [MaskedTextBox][2] is very flexible. It allows you to specify required characters, optional characters, literal characters, such as hyphens and parentheses, currency characters, and date separators. The control also works well when bound to a data source. The [Format][3] event on a data binding can be used to reformat incoming data to comply with the mask, and the [Parse][4] event can be used to reformat outgoing data to comply with the specifications of the data field.

For more information, see [MaskedTextBox Control (Windows Forms)][5].

##Event-Driven Validation
If you want full programmatic control over validation, or need to perform complex validation checks, you should use the validation events built into most Windows Forms controls. Each control that accepts free-form user input has a [Validating][6] event that will occur whenever the control requires data validation. In the [Validating][6] event-handling method, you can validate user input in several ways. For example, if you have a text box that must contain a postal code, you can perform the validation in the following ways:

* If the postal code must belong to a specific group of zip codes, you can perform a string comparison on the input to validate the data entered by the user. For example, if the postal code must be in the set {10001, 10002, 10003}, then you can use a string comparison to validate the data.
* If the postal code must be in a specific form you can use regular expressions to validate the data entered by the user. For example, to validate the form ##### or #####-####, you can use the regular expression ^(d{5})(-d{4})?$. To validate the form A#A #A#, you can use the regular expression [A-Z]d[A-Z] d[A-Z]d. For more information about regular expressions, see [.NET Framework Regular Expressions][7] and [Regular Expression Examples][8].
* If the postal code must be a valid United States Zip code, you could call a Zip code Web service to validate the data entered by the user.

The [Validating][6] event is supplied an object of type [CancelEventArgs][9]. If you determine that the control's data is not valid, you can cancel the [Validating][6] event by setting this object's [Cancel][10] property to **true**. If you do not set the [Cancel][10] property, Windows Forms will assume that validation succeeded for that control, and raise the [Validated][11] event.

For a code example that validates an e-mail address in a [TextBox][12], see [Validating][6].

###Data Binding and Event-Driven Validation

Validation is very useful when you have bound your controls to a data source, such as a database table. By using validation, you can make sure that your control's data satisfies the format required by the data source, and that it does not contain any special characters such as quotation marks and back slashes that might be unsafe.

When you use data binding, the data in your control is synchronized with the data source during execution of the [Validating][6] event. If you cancel the [Validating][6] event, the data will not be synchronized with the data source.

>If you have custom validation that takes place after the [Validating][6] event, it will not affect the data binding. For example, if you have code in a [Validated][11] event that attempts to cancel the data binding, the data binding will still occur. In this case, to perform validation in the [Validated][11] event, change the control's **Data Source Update Mode** property (**under (Databindings)****(Advanced)**) from **OnValidation** to **Never**, and add _Control_.DataBindings["_<yourfield>_"].WriteValue() to your validation code.


###Implicit and Explicit Validation

So when does a control's data get validated? This is up to you, the developer. You can use either implicit or explicit validation, depending on the needs of your application.

####Implicit Validation

The implicit validation approach validates data as the user enters it. You can validate the data as the data is entered in a control by reading the keys as they are pressed, or more commonly whenever the user takes the input focus away from one control and moves to the next. This approach is useful when you want to give the user immediate feedback about the data as they are working.

If you want to use implicit validation for a control, you must set that control's [AutoValidate][14] property to **true**. If you cancel the [Validating][6] event, the behavior of the control will be determined by what value that you assigned to [AutoValidate][14]. If you assigned [EnablePreventFocusChange][15], canceling the event will cause the [Validated][11] event not to occur. Input focus will remain on the current control until the user changes the data to a valid input. If you assigned [EnableAllowFocusChange][15], the [Validated][11] event will not occur when you cancel the event, but focus will still change to the next control.

Assigning [Disable][15] to the [AutoValidate][14] property prevents implicit validation altogether. To validate your controls, you will have to use explicit validation.

####Explicit Validation

The explicit validation approach validates data at one time. You can validate the data in response to a user action, such as clicking a Save button or a Next link. When the user action occurs, you can trigger explicit validation in one of the following ways:

* Call [Validate][16] to validate the last control to have lost focus.
* Call [ValidateChildren][17] to validate all child controls in a form or container control.
* Call a custom method to validate the data in the controls manually.

####Default Implicit Validation Behavior for Windows Forms Controls

Different Windows Forms controls have different defaults for their [AutoValidate][14] property. The following table shows the most common controls and their defaults.

<table><tbody><tr><th><p>Control</p></th><th><p>Default Validation Behavior</p></th></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.containercontrol(v=vs.110).aspx">ContainerControl</a></p></td><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.autovalidate(v=vs.110).aspx">Inherit</a></p></td></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.form(v=vs.110).aspx">Form</a></p></td><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.autovalidate(v=vs.110).aspx">EnableAllowFocusChange</a></p></td></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.propertygrid(v=vs.110).aspx">PropertyGrid</a></p></td><td><p>Property not exposed in Visual Studio</p></td></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.toolstripcontainer(v=vs.110).aspx">ToolStripContainer</a></p></td><td><p>Property not exposed in Visual Studio</p></td></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.splitcontainer(v=vs.110).aspx">SplitContainer</a></p></td><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.autovalidate(v=vs.110).aspx">Inherit</a></p></td></tr><tr><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.usercontrol(v=vs.110).aspx">UserControl</a></p></td><td><p><a href="https://msdn.microsoft.com/en-us/library/system.windows.forms.autovalidate(v=vs.110).aspx">EnableAllowFocusChange</a></p></td></tr></tbody></table>

##Closing the Form and Overriding Validation
When a control maintains focus because the data it contains is invalid, it is impossible to close the parent form in one of the usual ways:

* By clicking the **Close** button.
* By selecting **Close** in the **System** menu.
* By calling the [Close][18] method programmatically.

However, in some cases, you might want to let the user close the form regardless of whether the values in the controls are valid. You can override validation and close a form that still contains invalid data by creating a handler for the form's [Closing][19] event. In the event, set the [Cancel][10] property to **false**. This forces the form to close. For more information and an example, see [Form.Closing][19].

>If you force the form to close in this manner, any data in the form's controls that has not already been saved is lost. In addition, modal forms do not validate the contents of controls when they are closed. You can still use control validation to lock focus to a control, but you do not have to be concerned about the behavior associated with closing the form.

##See Also
[Control.Validating][21]

[Form.Closing][22]

[System.ComponentModel.CancelEventArgs][23]

[MaskedTextBox Control (Windows Forms)][24]

[Regular Expression Examples][25]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/system.windows.forms.maskedtextbox(v=vs.110).aspx
[3]: https://msdn.microsoft.com/en-us/library/system.windows.forms.binding.format(v=vs.110).aspx
[4]: https://msdn.microsoft.com/en-us/library/system.windows.forms.binding.parse(v=vs.110).aspx
[5]: https://msdn.microsoft.com/en-us/library/bbabas53(v=vs.110).aspx
[6]: https://msdn.microsoft.com/en-us/library/system.windows.forms.control.validating(v=vs.110).aspx
[7]: https://msdn.microsoft.com/en-us/library/hs600312(v=vs.110).aspx
[8]: https://msdn.microsoft.com/en-us/library/kweb790z(v=vs.110).aspx
[9]: https://msdn.microsoft.com/en-us/library/system.componentmodel.canceleventargs(v=vs.110).aspx
[10]: https://msdn.microsoft.com/en-us/library/system.componentmodel.canceleventargs.cancel(v=vs.110).aspx
[11]: https://msdn.microsoft.com/en-us/library/system.windows.forms.control.validated(v=vs.110).aspx
[12]: https://msdn.microsoft.com/en-us/library/system.windows.controls.textbox(v=vs.110).aspx
[13]: https://i-msdn.sec.s-msft.com/dynimg/IC160177.jpeg "System_CAPS_important"
[14]: https://msdn.microsoft.com/en-us/library/system.windows.forms.containercontrol.autovalidate(v=vs.110).aspx
[15]: https://msdn.microsoft.com/en-us/library/system.windows.forms.autovalidate(v=vs.110).aspx
[16]: https://msdn.microsoft.com/en-us/library/4wf8t2at(v=vs.110).aspx
[17]: https://msdn.microsoft.com/en-us/library/ms158374(v=vs.110).aspx
[18]: https://msdn.microsoft.com/en-us/library/system.windows.forms.form.close(v=vs.110).aspx
[19]: https://msdn.microsoft.com/en-us/library/system.windows.forms.form.closing(v=vs.110).aspx
[20]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.jpeg "System_CAPS_note"

[21]: https://msdn.microsoft.com/en-us/library/system.windows.forms.control.validating(v=vs.110).aspx
[22]: https://msdn.microsoft.com/en-us/library/system.windows.forms.form.closing(v=vs.110).aspx
[23]: https://msdn.microsoft.com/en-us/library/system.componentmodel.canceleventargs(v=vs.110).aspx
[24]: https://msdn.microsoft.com/en-us/library/bbabas53(v=vs.110).aspx
[25]: https://msdn.microsoft.com/en-us/library/kweb790z(v=vs.110).aspx