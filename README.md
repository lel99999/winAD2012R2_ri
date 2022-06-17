# winAD2016_ri
Windows Active Directory (AD) Reference Implementation

### Configuring Windows 2012 R2 for Active Directory and Certificate Server Services:
***NOTES***:  We are going to build out a complete Windows Active Directory Enterprise Server, to service as our Kerberos System (KDC and LDAP Realm) 

#### Step 1  ![Step 1](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 1")
***Login***
UID/PWD:   For userid Administrator or vagrant, the password is vagrant 

![Login Screen](https://github.com/lel99999/winAD_ri/blob/master/images/firstLogin.png "Login Screen")
      
#### Step 2  ![Step 2](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 2")
***Initial Desktop***
View Windows 2012 R2 Desktop

***Notice*** Windows License has expired

![Initial Desktop](https://github.com/lel99999/winAD_ri/blob/master/images/firstDesktop.png "Initial Desktop")

#### Step 3  ![Step 3](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 3")
***Open Powershell to Upgrade Expired License*** <br/>
License has expired, so we will use a temporary license to enable features and allow us to test Active Directory and Certificate Services, type the following: <br/>
***dism /online /set-edition:ServerStandard /productkey: \<product key\>***

![Powershell]( https://github.com/lel99999/winAD_ri/blob/master/images/powershell.png "Powershell")

#### Step 4  ![Step 4](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 4")
***Windows Status***

![Windows Status](https://github.com/lel99999/winAD_ri/blob/master/images/addfeatures_status.png "Windws Status")

#### Step 5  ![Step 5](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 5")
***View Desktop***

Windows now is ***fully functional*** for 30 days – If you need to run this for more than the evaluation period, 
you will either need to get a valid license, or contact Microsoft for an extension/another eval key.

![Upgraded Desktop](https://github.com/lel99999/winAD_ri/blob/master/images/upgradedDesktop.png "Upgraded Desktop")

#### Step 6  ![Step 6](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 6")
***Open Server Manager*** <br/>
![Click on Server Manager in Toolbar](https://github.com/lel99999/winAD_ri/blob/master/images/desktop_smallbar.jpg "Click on Server Manager in Toolbar")

We will be adding 2 server roles, Active Directory Domain Services and Certificate Services

![Server Manager Dashboard](https://github.com/lel99999/winAD_ri/blob/master/images/servermanagerDashboard.png "Server Manager Dashboard")

#### Step 7  ![Step 7](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 7")
***Fix Date and Time/Time Zone*** <br/>
First we need to get the correct time, so the time zone needs to be corrected.

Right mouse button click on the bottom right corner, and change the time zone from UTC to Eastern time

This is important as Kerberos relies on NTP, so clocks have to be in sync  … in this case we have not set the NTP for windows 2012 R2 …
(to be determined)


![Fix Time/Time Zone](https://github.com/lel99999/winAD_ri/blob/master/images/timezone.png "Fix Time/Time Zone")

#### Step 8  ![Step 8](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 8")
***Add Roles*** <br/>
Once time zone fixed, click on Add roles and features

Add Roles and Features Wizard - 01

Click Next

![Add Roles](https://github.com/lel99999/winAD_ri/blob/master/images/addRole.png "Add Roles")

#### Step 9  ![Step 9](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 9")
***Add Roles and Features - Wizard-02*** <br/>

Click Next

![Add Roles and Features](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_02.png "Add Roles and Features")


#### Step 10 . ![Step 10](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 10")
***Add Roles and Features - Wizard–03

Select Active Directory Domain Services  <br/>

Click Next

![Add Roles and Features](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_03.png "Add Roles and Features - Select AD Domain Services")

#### Step 11  ![Step 11](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 11")
***Add Roles and Features - Wizard–04*** <br/>

Add .Net Framework 4.5 and Features

![Add .Net Framework 4.5](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_04.png "Add .Net Framework 4.5")

#### Step 12 . ![Step 12](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 12")
***Add Roles and Features - Wizard–05*** <br/>

Active Directory Domain Service

![Active Directory Domain Services](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_05.png "Active Directory Domain Services")

#### Step 13 . ![Step 13](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 13")
***Add Roles and Features - Wizard–06*** <br/>

Confirm Selection

Click Install

![Confirm Selection](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_06.png "Confirm Selection")

#### Step 14  ![Step 14](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 14")
***Add Roles and Features - Wizard–07*** <br/>

Results.  View Installation Progress.

Once the installation has completed

Click Close


![Active Directory Domain Services](https://github.com/lel99999/winAD_ri/blob/master/images/addRole_wizard_07.png "Active Directory Domain Services")

#### Step 15  ![Step 15](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 15")
***Post Deployment Config***

Click on the yellow triangle with the exclamation point, and there are post-deployment configurations that needs to be done, namely to promote the server to a domain controller

Click on the link that says Promote this server to a domain  controller

![Post Deployment Config](https://github.com/lel99999/winAD_ri/blob/master/images/postDeploymentConfig.png "Post Deployment Config")

#### Step 16  ![Step 16](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 16")
***Add New AD Forest***

Active Directory Domain Service Configuration 
Wizard - 01

Select Add a new forest

Type in HDPDEV.COM (or whatever name suits you) for the Root domain name

Click Next

![Add New AD Forest](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-01.png "Add New AD Forest")


#### Step 17  ![Step 17](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 17")
***Add New AD Forest - Domain Controller Options*** <br/>
Active Directory Domain Service Configuration 
Wizard - 02

Keep defaults

Type in the DSRM Password:  we are using P@ssw0rd ***(Which is generally BAD, but we'll just use it for this example)***

Click Next

![Domain Controller Options](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-02.png "Domain Controller Options")



#### Step 18  ![Step 18](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 18")
***DNS Option*** <br/>
Active Directory Domain Service Configuration 
Wizard – 03
DNS Options

Keep defaults

Click Next

![DNS Option](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-03.png "DNS Option")

#### Step 19  ![Step 19](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 19")
***Additional Options*** <br/>
Active Directory Domain Service Configuration 
Wizard – 04
Additional Options


The NetBIOS domain name is automatically take from the domain name:   HDPDEV

Click Next

![Additional Options](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-04.png "Additional Options")

#### Step 20  ![Step 20](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 20")
***Service Configuration*** <br/>
Active Directory Domain Service Configuration 
Wizard – 05
Paths

Keep Defaults

Click Next

![Service Configuration](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-05.png "Service Configuration")

#### Step 21  ![Step 21](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 21")
***Review Options*** <br/>
Active Directory Domain Service Configuration 
Wizard – 06
Review Options

Keep Defaults

Click Next

![Review Options](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-06.png "Review Options")

#### Step 22  ![Step 22](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 22")
***Prerequisites Check*** <br/>
Active Directory Domain Service Configuration 
Wizard – 07
Prerequisites Check

All checks should pass with a couple of warnings

Click Install

![Prerequisites Check](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-07.png "Prerequisites Check")

#### Step 23  ![Step 23](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 23")
***Complete Wizard*** <br/>
Complete Wizard
Server Manager Dashboard with AD DS

![Complete Wizard](https://github.com/lel99999/winAD_ri/blob/master/images/ad_newforest_wizard-complete.png "Complete Wizard")

#### Step 24  ![Step 24](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 24")
***Users and Computers*** <br/>
Click on Tools->Menu
Select Active Directory Users and Computers

![Users and Computers](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers.png "Users and Computers")

#### Step 25  ![Step 25](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 25")
***Active Directory Users and Computers*** <br/>
Active Directory Users and Computers

![Users and Computers](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-01.png "Users and Computers")

#### Step 26  ![Step 26](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 26")
***Add Organizational Unit*** <br/>
Add Organizational Unit 

Right mouse HDPDEV.COM -> 
New ->
Organization Unit

![Add Organizational Unit](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-OU.png "Add Organizational Unit")

#### Step 27  ![Step 27](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 27")
***Add Organizational Unit - Name*** <br/>
Add Organizational Unit

Type Name: Hadoop \<or a name of your choice\>

Click Ok

![Add Organizational Unit - Name](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-OU-01.png "Add Organizational Unit - Name")


#### Step 28  ![Step 28](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 28")
***Add User*** <br/>
Add User

On the folder Hadoop, Right mouse button and click New -> User

![Add User](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-adduser.png "Add User")

#### Step 29  ![Step 29](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 29")
***Add User - Specify*** <br/>
Add User

Type in hadoopadmin for First name, and make sure User logon name is hadoopadmin@HDPDEV.COM

![Add User - Specify](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-adduser-01.png "Add User - Specify")

#### Step 30  ![Step 30](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 30")
***Add User - Set Password*** <br/>
Add User -Set Password

Set/confirm password as:
***P@ssw0rd***

Click on User cannot change password and Password never expires
(usually not a best practice, but this is for testing!)

![Add User - Set Password](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-adduser-02-setpwd.png "Add User - Set Password")

#### Step 31  ![Step 31](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 31")
***Add User - Finish*** <br/>
Click Finish

![Add User - Finish](https://github.com/lel99999/winAD_ri/blob/master/images/ad_users-computers-adduser-03-finish.png "Add User - Finish")

#### Step 32  ![Step 32](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 32")
***Delegation of Control*** <br/>
Delegation of control

Allows hadoopadmin principal to create objects under the OU Hadoop

Right mouse on Hadoop folder, select Delegate Control

![Delegation of Control](https://github.com/lel99999/winAD_ri/blob/master/images/ad_delcontrol-01.png "Delegation of Control")


#### Step 33  ![Step 33](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 33")
***Delegation of Control - Wizard01*** <br/>
Delegation Control Wizard - 01

Click Next

![Delegation of Control - Wizard01](https://github.com/lel99999/winAD_ri/blob/master/images/ad_delcontrol-wiz-01.png "Delegation of Control - Wizard01")

#### Step 34  ![Step 34](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 34")
***Delegation of Control - Wizard02*** <br/>
Delegation Control Wizard – 02

Under the Enter the object names to select -> type in hadoopadmin then click Check Names

Click OK

![Delegation of Control - Wizard02](https://github.com/lel99999/winAD_ri/blob/master/images/ad_delcontrol-wiz-02.png "Delegation of Control - Wizard02")

#### Step 35  ![Step 35](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 35")
***Delegation of Control - Wizard03*** <br/>
Delegation Control Wizard – 03

Tasks to Delegate

Select Create, delete, and manage user accounts

**This allows the hadoopadmin to have admin rights on the OU Hadoop

Click Next

![Delegation of Control - Wizard03](https://github.com/lel99999/winAD_ri/blob/master/images/ad_delcontrol-wiz-03.png "Delegation of Control - Wizard03")

#### Step 36  ![Step 36](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 36")
***Delegation of Control - Finish*** <br/>
Delegation Control Wizard – 04

Click Finish

![Delegation of Control - Wizard04](https://github.com/lel99999/winAD_ri/blob/master/images/ad_delcontrol-wiz-04-finish.png "Delegation of Control - Wizard04")

#### Step 37  ![Step 37](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 37")
***Advanced Features*** <br/>
Select HDPDEV.COM

Go to View Menu -> Advanced Features 

This view shows more advanced details and features of domain 

![Advanced Features](https://github.com/lel99999/winAD_ri/blob/master/images/ad_advancedfeatures.png "Advanced Features")

#### Step 38  ![Step 38](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 38")
***Advanced Features - Child Objects*** <br/>
Select domain HDPDEV.COM, 
Right mouse, properties
->	Security tab
->	Select hadoopadmin
Click Allow on:
-> Create all child objects
-> Delete all child objects

Click Apply

![Advanced Features - Child Objects](https://github.com/lel99999/winAD_ri/blob/master/images/ad_advancedfeatures-childobjectcreation.png "Advanced Features - Child Objects")

#### Step 39  ![Step 39](https://github.com/lel99999/winAD_ri/blob/master/images/arrow_down_25x25.png "Step 39")
***Advanced Features - Distinguished Name*** <br/>
Click on Attribute Editor Tab

Look at Distinguieshed Name:  OU=Hadoop, DC=HDPDEV, DC=COM

Click OK

![Advanced Features - Distinguished Name](https://github.com/lel99999/winAD_ri/blob/master/images/ad_advancedfeatures-distinguishedname.png "Advanced Features - Distinguished Name")
