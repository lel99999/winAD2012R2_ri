# winAD_ri
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
