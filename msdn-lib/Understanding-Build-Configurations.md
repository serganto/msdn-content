
[Source](https://msdn.microsoft.com/en-us/library/vstudio/kkz9kefa(v=vs.140).aspx)

# Understanding Build Configurations


You can store different configurations of solution and project properties to use in different kinds of builds. To create, select, modify, or delete a configuration, you can use the **Configuration Manager**. To open it, on the menu bar, choose **Build**, **Configuration Manager**, or just type **Configuration** in the **Quick Launch** box. You can also use the **Solution Configurations** list on the **Standard** toolbar to select a configuration or open the **Configuration Manager**.

By default, Debug and Release configurations are included in projects that are created by using Visual Studio templates. A Debug configuration supports the debugging of an app, and a Release configuration builds a version of the app that can be deployed. For more information, see [How to: Set Debug and Release Configurations][2]. You can also create custom solution configurations and project configurations. For more information, see [How to: Create and Edit Configurations][3].

A solution configuration specifies how projects in the solution are to be built and deployed. To modify a solution configuration or define a new one, in the **Configuration Manager**, under **Active solution configuration**, choose **Edit** or **New**.

Each entry in the **Project contexts** box in a solution configuration represents a project in the solution. For every combination of **Active solution configuration** and **Active solution platform**, you can set how each project is used. (For more information about solution platforms, see [Understanding Build Platforms][4].)


>When you define a new solution configuration and select the **Create new project configurations** check box, Visual Studio automatically assigns the new configuration to all of the projects. Likewise, when you define a new solution platform and select the **Create new project platforms** check box, Visual Studio automatically assigns the new platform to all of the projects. Also, if you add a project that targets a new platform, Visual Studio adds that platform to the list of solution platforms and assigns it to all of the projects.

>You can still modify the settings for each project.

The active solution configuration also provides context to the IDE. For example, if you're working on a project and the configuration specifies that it will be built for a mobile device, the **Toolbox** displays only items that can be used in a mobile device project.

##Project Configurations

The configuration and platform that a project targets are used together to specify the properties to use when it's built. A project can have a different set of property definitions for each combination of configuration and platform. To modify the properties of a project, you can use its Property Pages. (In **Solution Explorer**, open the shortcut menu for the project and then choose **Properties**.)

For each project configuration, you can define configuration-dependent properties as needed. For example, for a particular build, you can set which project items will be included, and what output files will be created, where they will be put, and how they will be optimized.

Project configurations can differ considerably. For example, the properties of one configuration might specify that its output file be optimized to occupy the minimum space, while another configuration might specify that its executable runs at the maximum speed.

Project configurations are stored by solution—not by user—so that they can be shared by a team.

Although project dependencies are configuration-independent, only the projects that are specified in the active solution configuration will be built.

##How Visual Studio Assigns Project Configurations

When you define a new solution configuration and don't copy settings from an existing one, Visual Studio uses the following criteria to assign default project configurations. The criteria are evaluated in the order shown.

1. If a project has a configuration name (_<configuration name=""> <platform name="">_) that exactly matches the name of the new solution configuration, that configuration is assigned. Configuration names are not case-sensitive.

2. If the project has a configuration name in which the configuration-name part matches the new solution configuration, that configuration is assigned, whether the platform portion matches or not.

3. If there is still no match, the first configuration that's listed in the project is assigned.

##How Visual Studio Assigns Solution Configurations
When you create a project configuration (in the **Configuration Manager**, by choosing **New** on the drop-down menu in the **Configuration** column for that project) and select the **Create new solution configurations** check box, Visual Studio looks for a like-named solution configuration to build the project on each platform it supports. In some cases, Visual Studio renames existing solution configurations or defines new ones.

Visual Studio uses the following criteria to assign solution configurations.

* If a project configuration doesn't specify a platform or specifies just one platform, then a solution configuration whose name matches that of the new project configuration is either found or added. The default name of this solution configuration does not include a platform name; it takes the form `_<project configuration="" name="">_.`
* If a project supports multiple platforms, a solution configuration is either found or added for each supported platform. The name of each solution configuration includes both the project configuration name and the platform name, and has the form `_<project configuration="" name=""> <platform name="">_`.

##See Also
[Walkthrough: Building an Application][6]

[Compiling and Building in Visual Studio][7]

[Solutions and Projects in Visual Studio][8]

[C/C++ Building Reference][9]

[Devenv Command Line Switches][10]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/vstudio/wx0123s5.aspx
[3]: https://msdn.microsoft.com/en-us/library/vstudio/kwybya3w.aspx
[4]: https://msdn.microsoft.com/en-us/library/vstudio/ms165407.aspx
[5]: https://i-msdn.sec.s-msft.com/dynimg/IC101471.jpeg "System_CAPS_note"

[6]: https://msdn.microsoft.com/en-us/library/vstudio/jj730426.aspx
[7]: https://msdn.microsoft.com/en-us/library/vstudio/cyz1h6zd.aspx
[8]: https://msdn.microsoft.com/en-us/library/vstudio/b142f8e7.aspx
[9]: https://msdn.microsoft.com/en-us/library/vstudio/91621w01.aspx
[10]: https://msdn.microsoft.com/en-us/library/vstudio/xee0c8y7.aspx