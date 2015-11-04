[Source](https://msdn.microsoft.com/en-us/library/dd648127.aspx "Permalink to Installing and Configuring Test Agents and Test Controllers")

# Installing and Configuring Test Agents and Test Controllers

For test scenarios using Visual Studio 2015 and Visual Studio Online (VSO) or Team Foundation Server (TFS) 2015, you won't need a test controller because Agents for Microsoft Visual Studio 2015 handle orchestration by communicating with VSO or TFS 2015. For example, you're running automated tests with your build and release workflows in VSO or TFS 2015.

If you need your test agent or test controller to work with TFS 2013, use Agents for Microsoft Visual Studio 2013 Update 5 and configure the test controller.

Where do I get the test controller and test agents?

These installers are available as ISO files (virtual CD) for easy installation on virtual machines. Can I mix versions of TFS, Microsoft Test Manager, the test controller, and test agent?

**What system requirements do I need to install my test controller and test agents?**

|  |  |
| ----- |-----|
| Controller | <ul><li>Windows 8, Windows 8.1</li><li>Windows 7 Service Pack 1</li><li>Windows Server 2012, Windows Server 2012 R2</li><li>Windows Server 2008 Release 2, Service Pack 1</li></ul> |
| Agent | <ul><li>Windows 8, Windows 8.1</li><li>Windows 7 Service Pack 1</li><li>Windows XP Service Pack 3</li><li>Windows Server 2012, Windows Server 2012 R2</li><li>Windows Server 2008 Release 2, Service Pack 1</li></ul> |
|.NET Framework|.NET Framework 4.5|

#Tasks
To run tests using a test controller and test agents, you must also configure a test settings file after you set up those controllers and agents. In that file, you assign roles to your test agents. Those role values determine the machines that your test controller will use to run each test. See [Setting Up Machines and Collecting Diagnostic Information Using Test Settings][2].

<table>
                <tbody><tr>
                  <th>
                    <p>To</p>
                  </th>
                  <th>
                    <p>See</p>
                  </th>
                </tr>
                <tr>
                  <td>
                    <p>Set up and manage test controllers and test agents for remote and distributed automated testing using Visual Studio.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/hh546459.aspx">Setting Up Test Controllers and Test Agents to Manage Tests with Visual Studio</a>
                          </span>
                        </p>
                      </li>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ff469838.aspx">Assigning Roles to a Test Controller and Test Agent for Automated Testing in Visual Studio</a>
                          </span>
                        </p>
                      </li>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/dd695837.aspx">Managing Test Controllers and Test Agents with Visual Studio</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Run a test controller or test agents in Microsoft Azure Cloud Services.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/hh546459.aspx">Setting Up Test Controllers and Test Agents to Manage Tests with Visual Studio</a>
                          </span>
                        </p>
                      </li>
                      <li>
                        <p>Also, read this blog: <a href="http://blogs.msdn.com/b/visualstudioalm/archive/2014/01/13/hosting-testcontroller-and-testagents-on-azure.aspx">Hosting Test Controller and Test Agents on Azure</a></p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Set up test controllers and configure security for test controllers and test agents in lab environments.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/hh546460.aspx">Setting Up Test Controllers in Lab Environments</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Set up test controllers and test agents to distribute load tests to multiple machines.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ee390841.aspx">Using Test Controllers and Test Agents with Load Tests</a>
                          </span>
                        </p>
                      </li>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ff937706.aspx">Test Controller and Test Agent Requirements for Load Testing</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Configure test agents to run remote or distributed tests that interact with the desktop, such as coded UI tests.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ee291332.aspx">How to: Set Up Your Test Agent to Run Tests that Interact with the Desktop</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Reconfigure the default ports that test controllers and test agents use to communicate so you can handle firewall restrictions and software conflicts.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ff652627.aspx">Configuring Ports for Test Controllers and Test Agents</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Configure test controllers and test agents on machines with multiple network adapters.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ff934571.aspx">How to: Bind a Test Controller or Test Agent to a Network Adapter</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
                <tr>
                  <td>
                    <p>Specify how long a test controller or test agent must wait for a response when communicating before failing with an error. Configure these settings if the default timeout settings are causing software conflicts in your topology.</p>
                  </td>
                  <td>
                    <ul>
                      <li>
                        <p>
                          <span>
                            <a href="https://msdn.microsoft.com/en-us/library/ff934570.aspx">How to: Specify Timeout Periods for Test Controllers and Test Agents</a>
                          </span>
                        </p>
                      </li>
                    </ul>
                  </td>
                </tr>
              </tbody></table>
			  
##Q & A

###Can I mix versions of TFS, Microsoft Test Manager, the test controller, and test agent?
A: Yes, here are the compatible and supported combinations:
<table>
                    <tbody><tr>
                      <th>
                        <p>
                          <span class="label">TFS</span>
                        </p>
                      </th>
                      <th>
                        <p>
                          <span class="label">Microsoft Test Manager, with Lab Center</span>
                        </p>
                      </th>
                      <th>
                        <p>
                          <span class="label">Controller</span>
                        </p>
                      </th>
                      <th>
                        <p>
                          <span class="label">Agent</span>
                        </p>
                      </th>
                    </tr>
                    <tr>
                      <td>
                        <p>2015: upgrade from 2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                    </tr>
                    <tr>
                      <td>
                        <p>2015: new install</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                    </tr>
                    <tr>
                      <td>
                        <p>2015: upgrade from 2015 or new install</p>
                      </td>
                      <td>
                        <p>2015</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                    </tr>
                    <tr>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2015</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                      <td>
                        <p>2013</p>
                      </td>
                    </tr>
                  </tbody></table>

##See Also
Concepts

[Setting Up Test Machines to Run Tests or Collect Data][3]

[1]: https://i-msdn.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635810750817785875
[2]: https://msdn.microsoft.com/en-us/library/dd286743.aspx
[3]: https://msdn.microsoft.com/en-us/library/dd293551.aspx