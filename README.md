# Secure-Access-With-Azure-Active-Directory

Azure AD: User, Group, and SSPR Setup

This documentation outlines steps to manage Azure Active Directory (Azure AD, now Microsoft Entra ID) users and groups, and to enable self-service password reset (SSPR) for a pilot group. These tasks demonstrate common administrative operations and include security best-practices and notes for clarity.

## Scenario ##
- Northwind  has created a new department called DevSupport. Three new employees, John, Dave, and Jeff, have joined as part of the new department. You are responsible for creating user accounts for these employees on Azure Active Directory (Azure AD.) You should also create a group for the department and assign the users to the new group.
- Northwind's employees regularly call the support team to reset their passwords. This adds to the workload of support teams and delays employees in their duties. You are responsible for enabling self-service password reset so that users of the organization can self-authenticate with Azure AD to reset their own passwords.
- Northwind has decided to enhance the security of its systems and data. You have been assigned to enable and configure multifactor authentication for the new employees to facilitate this.

## Task 1: Add a new user in Azure AD ##
1. Sign in to the [Azure portal](https://portal.azure.com/) with your login credentials. Navigate to **Microsoft Entra ID**. Select **Roles and administrators** under the Manage blade.
<img width="1680" height="801" alt="image" src="https://github.com/user-attachments/assets/6157fe47-63f7-44c8-a7da-86558ea06ecd" />


2.	To create a user, check your role. If your role is listed as **Global Administrator**, you can manage all aspects of Azure AD.
<img width="1665" height="859" alt="image" src="https://github.com/user-attachments/assets/5d772e12-c00c-4f68-940c-59d33bbec3c4" />


3.	Navigate back to **Microsoft Entra ID**, under the **Manage** blade, select **Users**. Select **Create new user** from the **New user** menu to add a new user.
4.	Add a User principal name as **John** and a Display name as **John** .
5.	The Username and Display name are required.  The domain part of the username must use either the initial default domain name, __<yourdomainname>.onmicrosoft.com__, or a custom domain name.
6.	Copy the auto-generated password that was provided in the box. (You will need to provide this password to the user for their initial login). 
7.	Click **Review + create**.
8.	Verify the information and then select Create to create a new user.  
9.	The user is created and added to your Azure AD organization.
10.	Repeat the steps for the other two users, Dave and Jeff.
<img width="1728" height="844" alt="image" src="https://github.com/user-attachments/assets/25c4470c-3cc3-4f00-abaa-f9f044b19dbc" />




## Task 2: Create a group called DevSupport and add memeber ##
Creating a security group in Azure AD lets you assign access or permissions collectively. In this task, we create a group named DevSupport and add users who provide developer support.
1. Navigate back to ****Microsoft Entra ID****, under the **Manage** blade, select **Groups**.
2. Select **New group**.
3. Select the desired **Microsoft 365** from the drop-down menu. This will enable the shared email address for the group.
4. Provide the Group information.
5. To add members, click on the link under **Members** selected. Choose the desired names from the list and click ****Select****.
<img width="997" height="570" alt="image" src="https://github.com/user-attachments/assets/d810f8ee-85aa-4c5e-a44d-4daec5db8cf3" />
6.	Verify the information and select Create to create the group. 
7.	Your Group is successfully created. Click on the name of the group to see total of members.


## Task 3: Enable self-service password reset ##
Self-service password reset (SSPR) allows users to reset their Azure AD passwords securely without helpdesk involvement. Best practice is to enable SSPR gradually (e.g. a pilot group) before turning it on for all users
In this task we enable SSPR for the DevSupport group created above.




## Task 4: Test self-service password reset  ##
After enabling SSPR for a group (e.g., DevSupport), it’s important to test the functionality from an end-user perspective. This ensures users can reset their own passwords and that the feature is properly scoped and working.


## Task 5: Task 5: Enable and configure multifactor authentication for a user ##
Multi-Factor Authentication adds an additional layer of security by requiring users to verify their identity using a second method beyond just a password.



## Notes & Tips: ##


  - **Security:** Require at least two authentication methods for password reset to prevent unauthorized resets
    learn.microsoft.com
    . For example, require phone + email or mobile app + PIN.

  - **User guidance:** Communicate to DevSupport members how to register their authentication methods at https://aka.ms/ssprsetup (they’ll be prompted on next sign-in) and how to reset at https://aka.ms/sspr if needed.

  - **Audit and monitoring:** Track SSPR usage via the Azure AD Password Reset Registration Activity report to ensure users are registering and using it correctly
    learn.microsoft.com
    . Monitoring helps detect any abuse or issues early.
