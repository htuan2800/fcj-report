---

title : "Creating an IAM User"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.2.3. </b> "
-------------------------

### 1. Search for IAM in the AWS Console Search Bar

![findIAM](/fcj-report/images/5-Workshop/5.2-Prerequisite/findIAM.png)

### 2. Create an IAM User Group

* In the **IAM user groups** interface:

  * Select **Create group**.

![IAMUserGroup](/fcj-report/images/5-Workshop/5.2-Prerequisite/IAMUserGroup.png)

* In the **Create user group** interface:

  * **User group name**: Enter `AdminGroup`.
  * **Attach permissions policies - Optional**: Search for `AdministratorAccess` and select it.

![createUserGroup](/fcj-report/images/5-Workshop/5.2-Prerequisite/createUserGroup.png)

* Scroll to the bottom of the page and select **Create user group**.

![createUserGroupNext](/fcj-report/images/5-Workshop/5.2-Prerequisite/createUserGroupNext.png)

* Verify that the IAM user group was created successfully.

![createUserGroupSuccess](/fcj-report/images/5-Workshop/5.2-Prerequisite/createUserGroupSuccess.png)

### 3. Create IAM Users

* In the **IAM users** interface:

  * Select **Create user**.

![IAMUser](/fcj-report/images/5-Workshop/5.2-Prerequisite/IAMUser.png)

* In the **Specify user details** interface:

  * **User name**: Enter `dev1`.
  * Select **Provide user access to the AWS Management Console - optional**.
  * Then, select **Next**.

![specify](/fcj-report/images/5-Workshop/5.2-Prerequisite/specify.png)

* In the **Set permissions** interface:

  * Select **Add user to group**.
  * **User groups**: Select the newly created **AdminGroup**.
  * Then, select **Next**.

![setPermission](/fcj-report/images/5-Workshop/5.2-Prerequisite/setPermission.png)

* In the **Review and create** interface:

  * Review the IAM user information.
  * Select **Create user**.

![reviewAndCreate](/fcj-report/images/5-Workshop/5.2-Prerequisite/reviewAndCreate.png)

* In the **Retrieve password** interface:

  * **Note:** Select **Download .csv file** to save the login credentials.
  * Then, select **Return to user list**.

![success](/fcj-report/images/5-Workshop/5.2-Prerequisite/success.png)

### 4. Continue Creating Accounts

* Repeat steps **2** and **3** to create additional IAM users with administrator permissions and provide the accounts to the team members for the project workshop.
