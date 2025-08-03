# Secure-Access-With-Azure-Active-Directory

Azure AD: User, Group, and SSPR Setup

This documentation outlines steps to manage Azure Active Directory (Azure AD, now Microsoft Entra ID) users and groups, and to enable self-service password reset (SSPR) for a pilot group. These tasks demonstrate common administrative operations and include security best-practices and notes for clarity.

## Scenario ##
- Northwind  has created a new department called DevSupport. Three new employees, John, Dave, and Jeff, have joined as part of the new department. You are responsible for creating user accounts for these employees on Azure Active Directory (Azure AD.) You should also create a group for the department and assign the users to the new group.
- Northwind's employees regularly call the support team to reset their passwords. This adds to the workload of support teams and delays employees in their duties. You are responsible for enabling self-service password reset so that users of the organization can self-authenticate with Azure AD to reset their own passwords.
- Northwind has decided to enhance the security of its systems and data. You have been assigned to enable and configure multifactor authentication for the new employees to facilitate this.

## Task 1: Add a new user in Azure AD ##
1. Sign in to the [Azure portal](https://portal.azure.com/) with your login credentials. Navigate to **Microsoft Entra ID**. Select **Roles and administrators** under the Manage blade.
<img width="1675" height="727" alt="Roles and administrators" src="https://github.com/user-attachments/assets/9340a8c4-a969-42db-beac-6044de466890" />

2.	To create a user, check your role. If your role is listed as **Global Administrator**, you can manage all aspects of Azure AD.
<img width="1679" height="795" alt="GlobalAdministrator" src="https://github.com/user-attachments/assets/f5fef0d5-f271-4fc2-8467-67285a76d506" />

3.	Navigate back to **Microsoft Entra ID**, under the **Manage** blade, select **Users**. Select **Create new user** from the **New user** menu to add a new user.
<img width="1694" height="547" alt="Create new user" src="https://github.com/user-attachments/assets/f9e27339-4a51-46b2-8516-417c9ad0f7de" />

4.	Add a User principal name as **John** and a Display name as **John** .
5.	The Username and Display name are required.  The domain part of the username must use either the initial default domain name, __<yourdomainname>.onmicrosoft.com__, or a custom domain name.
6.	Copy the auto-generated password that was provided in the box. (You will need to provide this password to the user for their initial login). 
7.	Click **Review + create**.
<img width="1694" height="547" alt="Create new user" src="https://github.com/user-attachments/assets/6aa05220-ede1-4638-b838-427ef432fed4" />

8.	Verify the information and then select Create to create a new user.  
<img width="1694" height="547" alt="Create new user" src="https://github.com/user-attachments/assets/3358d2e1-33a4-4151-83d5-8cf5e8963e5f" />

9.	The user is created and added to your Azure AD organization.
10.	Repeat the steps for the other two users, Dave and Jeff.
<img width="1628" height="632" alt="Create all users" src="https://github.com/user-attachments/assets/397087d2-fc39-4379-8d08-0a51d5b508d7" />




## Task 2: Create a group called DevSupport and add memeber ##
Creating a security group in Azure AD lets you assign access or permissions collectively. In this task, we create a group named DevSupport and add users who provide developer support.
1. Navigate back to **Microsoft Entra ID**, under the **Manage** blade, select **Groups**.
<img width="1612" height="788" alt="Manage Groups" src="https://github.com/user-attachments/assets/3b316526-b361-4515-8b0a-dc40898826b3" />

2. Select **New group**.
<img width="1608" height="858" alt="Create new group" src="https://github.com/user-attachments/assets/c9607b3d-3aac-4e5a-b458-6af5cc48db46" />

3. Select the desired group type, in this case **Microsoft 365** from the drop-down menu. This will enable the shared email address for the group.
4. Provide the Group information.
<img width="1593" height="922" alt="Add Group Information" src="https://github.com/user-attachments/assets/c126d5ed-c939-4d54-ae31-a36ef298e416" />

5. To add members, click on the link under **Members** selected. Choose the desired names from the list and click **Select**.
<img width="1681" height="924" alt="Add Group Members" src="https://github.com/user-attachments/assets/9e487cae-96dc-4227-9be9-cee38e538aa9" />

6.	Verify the information and select Create to create the group. 
7.	Your Group is successfully created. Click on the name of the group to see total of members.


## Task 3: Enable self-service password reset ##
Self-service password reset (SSPR) allows users to reset their Azure AD passwords securely without helpdesk involvement. Best practice is to enable SSPR gradually (e.g. a pilot group) before turning it on for all users
In this task we enable SSPR for the DevSupport group created above.
1. Navigate to Microsoft Entra ID, select **Password reset**.
<img width="1682" height="903" alt="image" src="https://github.com/user-attachments/assets/70b698a7-c388-4f07-8665-5ad8f8f870f1" />
2. From the Properties page, under the option Self service password reset enabled, choose **Selected**
<img width="1106" height="695" alt="image" src="https://github.com/user-attachments/assets/6043311a-979e-4622-bffc-296904234b8b" />

3.	Choose Selected Group from the options shown to restrict password resets to a limited group of users.
4.	Click the select group link under Select Group to populate your list of available groups.
5.	Choose DevSupport and click Select.
6.	Click Save to enable self-service password reset (SSPR).


## Task 4: Test self-service password reset  ##
After enabling SSPR for a group (e.g., DevSupport), it’s important to test the functionality from an end-user perspective. This ensures users can reset their own passwords and that the feature is properly scoped and working.
1. To test the manual registration process from an end-user's perspective, open a new browser window in InPrivate or incognito mode, and browse to [https://aka.ms/ssprsetup](url)
2. Sign in with the username of a test user, like Jeff. 
<img width="1669" height="938" alt="Sign In Jeff" src="https://github.com/user-attachments/assets/31c2d342-9e29-4638-ad5d-bc114e3daa17" />

3. On the next page, you will be prompted to enter your credentials, click **Forgot password**. 
<img width="1674" height="850" alt="Jeff Forgot Password" src="https://github.com/user-attachments/assets/5b1af1c7-b3d5-45e6-ad0e-104dc8f3dbed" />

4.Enter the test user's account information, the characters from the CAPTCHA, and then select Next.
<img width="1686" height="741" alt="CApcha" src="https://github.com/user-attachments/assets/13ce67ea-94ce-40f3-8431-622b17bd5b9b" />

5. Follow the verification steps to reset your password.

## Task 5: Task 5: Enable and configure multifactor authentication for a user ##
Multi-Factor Authentication adds an additional layer of security by requiring users to verify their identity using a second method beyond just a password.
1. Navigate to **Microsoft Entra ID**
2. Click on **Security** under the **Manage** blade
<img width="1326" height="878" alt="image" src="https://github.com/user-attachments/assets/80fd92cb-1ff5-41b4-8198-d2c515ee3990" />

3. Click on **Multifactor authentication**.
<img width="1148" height="771" alt="image" src="https://github.com/user-attachments/assets/364ee696-38c9-4381-a5ca-02207a70126a" />

4. Select **Additional cloud-based multifactor authentication settings**.
<img width="1150" height="630" alt="image" src="https://github.com/user-attachments/assets/4068fb23-e559-4653-a5e0-d548c54dd2c0" />
5. Under Service settings, scroll down to Verication options
6. Check the box Allow users to remember mutilfation authentication on devices they trust (between one to 365 days) and click **Save.**
<img width="1624" height="919" alt="image" src="https://github.com/user-attachments/assets/d18dd20b-b63c-4b69-927e-50ee61acbcb9" />

7. If you enable "Remember multi-factor authentication on trusted device", users can mark a device as trusted when they sign in by selecting Don't ask again.
8. Navigate back to **Microsoft Entra ID** > Select Users 
<img width="2110" height="635" alt="users overview" src="https://github.com/user-attachments/assets/c09ea454-f865-4ca0-93f4-bac4a7e351af" />

9.  Click on Per-user MFA
10. Check the boxes for the desired users to enable
11. Once completed, you can view the user state on the multi-factor authentication page. You can see the user has been enabled with multifactor authentication
<img width="2038" height="684" alt="Enforce MFA" src="https://github.com/user-attachments/assets/cc870140-7e64-4eb6-a361-19c895ecccc4" />

## Notes & Tips: ##

  - **Security:** Require at least two authentication methods for password reset to prevent unauthorized resets
    learn.microsoft.com
    . For example, require phone + email or mobile app + PIN.

  - **User guidance:** Communicate to DevSupport members how to register their authentication methods at https://aka.ms/ssprsetup (they’ll be prompted on next sign-in) and how to reset at https://aka.ms/sspr if needed.

  - **Audit and monitoring:** Track SSPR usage via the Azure AD Password Reset Registration Activity report to ensure users are registering and using it correctly
    learn.microsoft.com
    . Monitoring helps detect any abuse or issues early.
