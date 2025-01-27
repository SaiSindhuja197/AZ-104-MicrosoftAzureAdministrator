# Lab 01 - Manage Microsoft Entra ID Identities

## Lab Overview

This lab focuses on users and groups as the foundation of an identity solution. You'll work on provisioning users and groups for a pre-production lab environment, incorporating automated group memberships based on job titles to streamline management.

## Lab objectives
In this lab, you will complete the following tasks:

+ Task 1: Create and configure Entra ID users
+ Task 2: Create Entra ID groups with assigned and dynamic membership
+ Task 3: Create a Microsoft Entra ID tenant
+ Task 4: Manage Entra ID guest users

## Exercise 1: Microsoft Entra ID Identities

In this exercise, you will learn how to create and manage Microsoft Entra ID identities. You will explore the process of provisioning users, assigning roles, and configuring essential properties for managing access to cloud resources. This exercise will help you understand the foundational concepts of identity management within the Microsoft Entra ID ecosystem.

### Task 1: Create and configure Entra ID users

In this task, you will set up and customize Microsoft Entra ID users by creating user accounts and configuring their properties to align with the organization's identity management requirements.

1. In the Azure portal, search for **Microsoft Entra ID (1)** and select **Microsoft Entra ID (2)**.

    ![](../Labs/media/lab1-image1.png)

1. On the **Microsoft Entra ID** blade, scroll down to the **Manage** section, click **User settings**, and review available configuration options.

   ![](../Labs/media/lab1-image2.png)

1. From the **User settings**  blade, in the **Manage** section, click **Users**.

    ![](../Labs/media/lab1-image3.png)

1. Click your user account to display its **Profile** settings. 

     ![](../Labs/media/lab1-image4.png)

1. Click **Edit properties**. 

     ![](../Labs/media/lab1-image5.png)
   
1. Click **Settings (1)** tab and make sure that **Usage location** set to **United States (2)**, if not select  **Usage location** to **United States** and click **Save** to apply the change.

     ![](../Labs/media/lab1-image6.png)

    >**Note**: This is necessary in order to assign a Microsoft Entra ID Premium P2 license to your user account later in this lab.
  
1. Navigate back to the **Users - All users** blade, and then click **+ New user (1)** then select **+ Create new user (2)**.

     ![](../Labs/Images/newuser.png)

1. Create a new user on the **Basics (1)** tab with the following settings (leave others with their defaults) and select **Next: properties (6) >**.

    | Setting | Value |
    | --- | --- |
    | User principal name | **az104-01a-aaduser1 (2)**  |
    | Display Name | **az104-01a-aaduser1 (3)** |
    | Auto-generate password | unchecked **(4)** |
    | Password | **Provide a secure password (5)** |
    | Account enabled | **Checked (7)** |
    
      >**Note**: **Copy to clipboard** the full **User Principal Name** (user name plus domain) and record the password. You will need it later in this task.
    
      ![image](../media/az104-mod3-image30.png)
    
 1. On  the **Properties** tab specify the following settings (leave others with their defaults):  

    | Setting | Value |
    | --- | --- |
    | Job title  | **Cloud Administrator (1)** |
    | Department | **IT (2)** |
    | Usage location | **United States (3)** |
    
      ![](../Labs/media/lab1-image8.png)
     
      ![](../Labs/media/lab1-image9.png)
    
1. Click on **Review + create** and then **Create**.

1. In the list of users, click the newly created user account to display its blade.

   ![](../Labs/media/lab1-image10.png)

1. From the left navigation pane, click **Assigned roles**.

     ![image](../media/az104-mod3-image31.png)

1.  Then click **+ Add assignment (1)** button and search and select **User administrator (2)(3)** role and click **Add (4)** to assign role to **az104-01a-aaduser1**.

    >**Note**: You also have the option of assigning Entra ID roles when provisioning a new user.

     ![image](../media/az104-mod3-image32.png)
     
1. Open an **InPrivate** browser window and sign in to the [Azure portal](https://portal.azure.com) using the newly created user account. When prompted to update the password, change the password to a secure password of your choosing. 

    >**Note**: Rather than typing the user name (including the domain name), you can paste the content of Clipboard.
   
1. In the **InPrivate** browser window, in the Azure portal, search for and select **Microsoft Entra ID**.
      
    >**Note**: While this user account can access the Azure Active Directory tenant, it does not have any access to Azure resources. This is expected since such access would need to be granted explicitly by using Azure Role-Based Access Control. 

1. In the **InPrivate** browser window, on the Entra ID blade, scroll down to the **Manage** section, click **User settings**, note that you do not have permission to modify any configuration options, and sign out of the user account **az104-01a-aaduser1** and close the InPrivate window.

1. In the Azure portal, search for and select **Microsoft Entra ID**, in the **Manage** section, click **Users**, then click **+ New user (1)** then select **+ Create new user (2)**.

     ![](../Labs/Images/newuser.png)

1. Create a new user on the **Basics** tab with the following settings (leave others with their defaults) and select **Next: properties>**.

    | Setting | Value |
    | --- | --- |
    | User principal name | **az104-01a-aaduser2** |
    | Display Name | **az104-01a-aaduser2** |
    | Auto-generate password | unchecked |
    | Password | **Provide a secure password** |
    | Account enabled | **Checked** |
    
     >**Note**: **Copy to clipboard** the full **User Principal Name** (user name plus domain) and record the password. You will need it later in this task.
    
 1. On **Properties** tab specify the following settings (leave others with their defaults):
    
    | Setting | Value |
    | --- | --- |
    | Job title | **System Administrator** |
    | Department | **IT** |
    | Usage location | **United States** |
    
1. Click on **Review + create** and then **Create**.

    >**Note**: If the users are already created then you can skip this task and continue further. 

### Task 2: Create Entra ID groups with assigned and dynamic membership

In this task, you will create Azure Active Directory groups with assigned and dynamic membership. Assigned groups require manually adding members, while dynamic groups automatically update memberships based on attributes like job titles or departments. This approach ensures efficient and automated group management.

1. Back in the Azure portal where you are signed in with your **user account**, navigate back to the **Overview** blade of the Entra ID tenant and, in the **Manage** section, click **Licenses**.

      ![image](../media/az104-mod3-image35.png) 

1. Under **Manage** section click on **All products**. Notice the **Microsoft Entra ID P2** is listed and assigned to the odl user.

      ![image](../media/az104-mod3-image34.png)

   >**Note**: Microsoft Entra ID P2 are required in order to implement dynamic groups.
    
    >**Note**: From here you can purchase a license, manage the licenses you have, and assign licenses to users and groups. Select **Licensed features** to see what is available.
    
    >**Note**: Please review the document to enhance your understanding of Microsoft Entra ID P2. You can find it at: https://learn.microsoft.com/en-us/entra/fundamentals/licensing
    
1. In the Azure portal, navigate back to the Entra ID tenant blade and click **Groups**.

    ![](../Labs/Images/grp.png)        

1. Use the **+ New group** button to create a new group with the following settings:

    | Setting | Value |
    | --- | --- |
    | Group type | **Security (1)** |
    | Group name | **IT Cloud Administrators (2)** |
    | Group description | **Contoso IT cloud administrators (3)** |
    | Membership type | **Dynamic User (4)** |
   
     >**Note**: If the **Membership type** drop-down list is grayed out, wait a few minutes and refresh the browser page.

1. Click **Add dynamic query (5)**.

    ![](../Labs/Images/grp1.png)  

1. On the **Configure Rules** tab of the **Dynamic membership rules** blade, create a new rule with the following setting by clicking on **+ Add expression (1)** and **Save (5)**.

    | Setting | Value |
    | --- | --- |
    | Property | **jobTitle (2)** |
    | Operator | **Equals (3)** |
    | Value | **Cloud Administrator (4)** |

   ![image](../media/az104-mod3-image36.png) 
   
1. Back on the **New Group** blade, click **Create**.

    ![image](../media/az-11.png)

1. Back on the **Groups - All groups** blade of the Entra ID tenant, click the **+ New group** button and create a new group with the following settings:

    | Setting | Value |
    | --- | --- |
    | Group type | **Security** |
    | Group name | **IT System Administrators** |
    | Group description | **Contoso IT system administrators** |
    | Membership type | **Dynamic User** |

1. Click **Add dynamic query**.

1. On the **Configure Rules** tab of the **Dynamic membership rules** blade, create a new rule with the following setting by clicking on **+ Add expression** and **Save**.

    | Setting | Value |
    | --- | --- |
    | Property | **jobTitle** |
    | Operator | **Equals** |
    | Value | **System Administrator** |

1. Back on the **New Group** blade, click **Create**.

1. Back on the **Groups - All groups** blade of the Entra ID tenant, click the **+ New group** button, and create a new group with the following settings:

    | Setting | Value |
    | --- | --- |
    | Group type | **Security** |
    | Group name | **IT Lab Administrators** |
    | Group description | **Contoso IT Lab administrators** |
    | Membership type | **Assigned** |

1. Click **No members selected (1)**. From the **Add members** blade, under **Groups (2)** tab search and select the **IT Cloud Administrators** and **IT System Administrators** groups **(3)** and click on **Select (4)**.

    ![](../Labs/media/lab1-image17.png)
   
1. Back on the **New Group** blade, click **Create**.

1. Back on the **Groups - All groups** blade, click the entry representing the **IT Cloud Administrators** group and, select **Members** blade. Verify that the **az104-01a-aaduser1** appears in the list of group members.

     ![image](../media/az104-mod3-image39.png)

    >**Note**: You might experience delays with updates of the dynamic membership groups. To expedite the update, navigate to the group blade, display its **Dynamic membership rules** blade, **Edit** the rule listed in the **Rule syntax** textbox by adding whitespace at the end, and **Save** the change.

1. Navigate back to the **Groups - All groups** blade from the left navigation pane, click the entry representing the **IT System Administrators** group and, then display its **Members** blade. Verify that the **az104-01a-aaduser2** appears in the list of group members.

### Task 3: Create an Microsoft Entra ID tenant

In this task, you will create a new Microsoft Entra ID tenant, which serves as a dedicated instance of Microsoft Entra ID for managing your organization's identity and access needs. 

1. In the Azure portal in the main browser window, search for and select **Microsoft Entra ID**.
   
1. Click **Manage tenant** from the top navigation pane, and then on the next screen, click **+ Create**, and specify the following setting:
   
    | Setting | Value |
    | --- | --- |
    | Select a tenant type | **Microsoft Entra ID** |    
    
1. Click **Next: Configuration** then Click **Review + create (4)**

    | Setting | Value |
    | --- | --- |
    | Organization name | **Contoso Lab (1)** |
    | Initial domain name | any valid DNS name consisting of lower case letters and digits and starting with a letter **(2)** | 
    | Country/Region | **United States (3)** |
    

    ![](../Labs/Images/crttenant2.png)   
   
   > **Note**: The **Initial domain name** should not be a legitimate name that potentially matches your organization or another. The green checkmark in the **Initial domain name** text box will indicate that the domain name you typed in is valid and unique.

1. On **Review + create** page Click **Create**. Enter the captcha and click **Submit**.

   ![](../Labs/Images/catche.png)   

    >**Note**: After clicking on Submit, please wait for 2 minutes before proceeding to the next step. You may not receive any notifications during this time then after some time procced with next step.

    >**Note**: There is a known issue with the Captcha verification in the lab environment. If you receive the error **Creation failed. Too many requests, please try later**, do the following:<br>
    >- Try the creation a few times.<br>
    >- Check the **Manage tenant** section to ensure the tenant wasn't created in the background. <br>
    >- Open a new **InPrivate** window and use the Azure Portal and try to create the tenant from there.<br>
    >- Use the **[interactive lab simulation](https://mslabs.cloudguides.com/guides/AZ-104%20Exam%20Guide%20-%20Microsoft%20Azure%20Administrator%20Exercise%201)** to view the steps. <br>
    >- You can try this task later, but creating a tenant isn't required in other labs. 

1. In the Azure portal search and select **Microsoft Entra ID**.
    
1. Select **Manage tenants** to display the blade of the newly created Entra ID tenant and select **Settings (1)** button in the Azure portal toolbar and, click on **Switch (2)**.

     ![](../Labs/media/az-12.png)

### Task 4: Manage Entra ID, guest users.

In this task, you will create Entra ID guest users, allowing external users to access resources within your organization's Azure environment. You will configure the necessary permissions and roles to grant these guest users secure access to specific resources in an Azure subscription, enabling collaboration while maintaining control over the environment's security.

1. In the Azure portal displaying the Contoso Lab Entra ID tenant, in the **Manage** section, click **Users**, and then click **+ New user** then select **Create new user**.

1. Create a new user on the **Basics** tab with the following settings (leave others with their defaults) and select **Next: properties>**.

    | Setting | Value |
    | --- | --- |
    | User principal name | **az104-01b-aaduser1** |
    |  Display Name | **az104-01b-aaduser1** |
    |  Auto-generate password | uncheck |
    |  Password | **Provide a secure password** |
    | Account enabled | **Checked** |
       
    >**Note**: **Copy to clipboard** the full **User Principal Name** (user name plus domain) and record the password. You will need it later in this task.

 1. on **Properties** tab specify the following settings (leave others with their defaults).

    | Setting | Value |
    | --- | --- |
    | Job title | **System Administrator** |
    | Department | **IT** |

1. Click on **Review + create** and then **Create**.       
1. Click on the newly created profile.

    >**Note**: **Copy to clipboard** the full **User Principal Name** (user name plus domain). You will need it later in this task.

1.  Search and select Entra ID page.
1. Click **Manage tenants**.
1. Check the box next to the first tenant **(1)**, then select **Switch (2)**.

    ![](../Labs/media/lab1-image19.png)

1. Open **Microsoft Entra ID**, from the left navigation pane, under **Manage** select **Users** blade, click **+ New user (1)** then select **Invite external user (2)**.

    ![](../Labs/Images/exuserinv.png)  
    
1. Create a new user on **Basics** tab with the following settings (leave others with their defaults) and select **Next: properties>**.

    | Setting | Value |
    | --- | --- |
    | Email address | the User Principal Name you copied earlier in this task **(1)** |
    | Display Name | **az104-01b-aaduser1 (2)** |
    

      ![](../Labs/Images/exuser.png)  
    
 1. On the **Properties** tab specify the following settings (leave others with their defaults).    
   
    | Setting | Value |
    | --- | --- | 
    | Job title | **Lab Administrator** |
    | Department | **IT** |
    | Usage location | **United States** |

1. Click **Review + Invite** and then **Invite**. 

1. Back on the **Users - All users** blade, click the entry representing the newly created guest user account.

1. On the **az104-01b-aaduser1 - Profile** blade, click **Groups**.

1. Click **+ Add membership** and add the guest user account to the **IT Lab Administrators** group.

   <validation step="f05516fb-26d1-48f6-a20f-e2f9c0616ec2" />
   
  > **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
  > - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed with the next lab.
  > - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
  > - If you need any assistance, please contact us at labs-support@spektrasystems.com. We are available 24/7 to help

### Review

In this lab, you have completed the following tasks:

- Created and configured Entra ID users, including setting up user accounts and configuring essential properties for identity management.
- Created Entra ID groups with both assigned and dynamic membership, configuring assigned groups for manual membership and dynamic groups for automatic membership based on user attributes.
- Created a Microsoft Entra ID (AD) tenant, setting up a dedicated instance for managing your organization's identity and access in Azure.
- Managed Entra ID guest users, allowing external users to access specific resources in an Azure subscription by assigning them appropriate roles and permissions.

### You have successfully completed the lab
