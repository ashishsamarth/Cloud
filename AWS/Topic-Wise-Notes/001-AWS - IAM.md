IAM: Identity & Access Management
-----------------------------------------------------------------------------------------------------------------------------------------------------------

-----------------------------------------------------------------------------------------------------------------------------------------------------------
IAM is a global service in AWS. This can be verified by going to IAM Dashboard and when you try to select a region, you will see the following text 

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    'IAM does not require a region selection'
    
It also indicates that all the users that are created in a particular AWS account are available in all regions. The root user is the most powerful user (it can do anything and everything in an AWS account), hence its recommended to create new users to perform specific tasks and limit their capabilites using policies and groups. Since we must follow the principle of least privilege.

IAM allows you to manage users and their level of access to the AWS Console. It is important to understand IAM and how it works, both for the exam and for administrating a company's AWS account in real life.

Things that IAM Provides
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Centralized control of your AWS account
    b.  Shared Access to your AWS account
    c.  Granular permissions
    d.  Identity Federation (including Active Directory, Facebook, LinkedIn, etc.)
    e.  Multi-factor Authentication
    f.  Provides temporary access for users/devices and services, as necessary
    g.  Allows you to setup your own password rotation policy
    h.  Integrates with many different AWS services
    j.  Supports PCI DSS Compliance, for any applications associated with the payment card industry.
-----------------------------------------------------------------------------------------------------------------------------------------------------------

IAM Guidelines & Best Practices
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Dont Use the root account except for AWS account setup
    b.  One physical user = one AWS user
    c.  Assign users to groups and assign permissions to group
    d.  Create a strong password policy
    e.  Use and enforce the use of MFA
    f.  Create and use Roles for giving permissions for AWS services
    g.  Use Access Keys for Programmatic Access (CLI / SDK)
    h.  Audit permission of your account with the IAM credentials report
    i.  Never share IAM users and Access keys.
-----------------------------------------------------------------------------------------------------------------------------------------------------------

IAM Summary:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  USERS       :   Mapped to a physical user, has a password for AWS console   (think people).
    b.  GROUPS      :   Contains Users only (A collection of users under one set of permissions.)
    c.  POLICIES    :   A JSON document that outlines permissions for users or groups
                        Policies can be attached to either a User, a Group, or a Role. 
                        Once attached, a policy will grant to the assignee the permissions associated with that policy
    d.  ROLES       :   For EC2 instances or AWS services   (Used to assign a set of permissions to AWS resources)
    e.  SECURITY    :   MFA + Password Policy
    f.  ACCESS KEYS :   Access AWS using the CLI or SDK
    g.  Audit       :   IAM Credentials and IAM Access Advisor

    Note:   Maximum Policies that can be associate with a USER Group is : 10
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: When creating a USER, how many types of 'Access Types' can be provisioned?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their are two types of 'Access Types' that can be utilized
    a.  Programmatic Access: 
        This allows the user to use AWS API, CLI, SDK & Other development tools to be utilized via an access Key ID 
        & secret access key
    b.  AWS Management Console Access: 
        This allows the user to use the (GUI) management console access.
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q02. When creating a USER, is it necessary to Create a Group?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
No, Its not necesary to create a Group while creating a USER. However, as a best practice its recommended to have even a single user to be 
mapped to group.Since over a period of time, the number of users may grow and it will be easier to manage permissions using groups and policies.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q03: What are tags in AWS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Tags are way to organize and categorize resources in AWS.

For e.g.: Their are mulitple EC2 instances in your account, and you want to identify them based on Team names and/or Project Names to quickly identify which EC2 instance is being used for what. Tagging also helps to identify the cost accumulated by the resources which is important for Billing & Thresholds.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q04: Once the user is created, how many ways can the user get login credentials?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their are two ways a user can get hold of login credentials
        a.  via the 'Download.csv'
        b.  'Send Email' : Which has the Email Login Instructions.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q05: How can you customize the url for specific user login, Once the user is created?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the AWS console --> Go to IAM Dashboard --> on the top right under 'AWS Account' --> Look for 'Account Alias'
        a.  If you dont have an alias - It will enable the link to 'Create' an alias
        b.  If you have an alias - It will allow to 'Edit' or 'Delete' an alias

    Important Note: 
    Since IAM is a Global Service, the alias that you create must be unique for entire IAM service across all regions.
    You cannot create an alias if it already exists.

    e.g.:   https://samarth-aws.signin.aws.amazon.com/console
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q06: What is the advantage of having an alias based url for login?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the advantages
    a.  When you use an 'Alias' based url:
        1.  Your 'Account ID or Alias' is already populated for you
        2.  You can login as an IAM user, rather than selecting the radio button between 'root user' vs 'iam user'
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q07: How can you identify if a user is an IAM User vs a ROOT user, just by looking at the management console?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Once logged in, if you look at the top right of the screen where it shows the user
        a.  An IAM user will have the '@' keyword in the name:
            e.g.    samarth-developer@samarth-aws OR samarth-developer@account-id
        b.  A root user will not have the '@' keyword in the name
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q08: Explain IAM Password Policy?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    In AWS: You can set up a password policy to have
        a.  set a minimum password length
        b.  Require specific character types
            1.  including uppercase letters
            2.  including lowercase letters
            3.  including numbers
            4.  including non-alphanumeric characters
        c.  Allow all IAM users to change their own passwords
        d.  Require users to change their passwords after some time (password expiration)
        e.  Prevent password re-use
----------------------------------------------------------------------------------------------------------------------------------------------------------- 

Q09: What is the advantage of using an MFA?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    AWS recommends to protect the root and iam users by using MFA (multi-factor-authentication)
    The main benefit of using a MFA is - Even if a password is stolen or hacked, the account will not be compromised.
    Following are the supported devices for MFA in AWS:
        a.  Virtual MFA devices {e.g. Google Authenticator (works on 1 device at a time) 
            or Authy(works on multiple devices at the same time)}
        b.  Universal 2nd Factor (U2F) security key (e.g.- Yubikey)
        c.  Hardware Key fob MFA Device
            a.  For non-government cloud: Its a key fob provided by Gemalto (Thales)
            b.  For government cloud: Its a key fob provided by surepassid
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q10: How to set up a password policy?
-----------------------------------------------------------------------------------------------------------------------------------------------------------    
    Following are the steps
        a.  Login to the AWS management console (as a user having administrator access)
        b.  Navigate to IAM Dashboard
        c.  Under Access Management, look for 'Account Settings'
        d.  Click on 'Account Settings' and then click on 'Change Password Policy'
        e.  The next screen will have 'Set Password Policy' as a header with the following options
            1.  Enforce Mininum password length (It has a box to enter the number of characters)
            2.  Require at least one uppercase letter from Latin Alphabet (A-Z)
            3.  Require at least one lowercase letter from Latin Alphabet (a-z)
            4.  Require at least one number
            5.  Require at least on non-alphanumeri character (! @ # $ % ^ & * ( ) _ + - = [] {} | ')
            6.  Enable password expiration
            7.  Password expiration requires administrator reset
            8.  Allow users to change their own password
            9.  Prevent Password reuse
        f.  All the above options are checkboxes, so you can select based on your organization's guidelines
        g.  Click on 'Save Changes'
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q11: How to add MFA to the root user?
-----------------------------------------------------------------------------------------------------------------------------------------------------------    
    Once logged in as the root user
        a.  Click on the username on the top right
        b.  Under the options, click on 'My Security Credentials'
        c.  You will be navigated to a different page with the following options
            1.  Password
            2.  Multi-Factor authentication (MFA)
            3.  Access keys (access key ID and secret access key)
            4.  CloudFront key paris
            5.  X.509 certificate
            6.  Account Identifiers
        d.  Select 'Multi-Factor authentication', that will provide you with following three options (radio buttons)
            1.  Virtual MFA Device
            2.  U2F security Key
            3.  Other Hardware MFA Device
        e.  Select 'Virtual MFA Device'
            The following virtual devices are supported
            Authy, Duo Mobile, LastPass Authenticator, Microsoft Authenticator, Google Authenticator
-----------------------------------------------------------------------------------------------------------------------------------------------------------            
Q12: What are the minimum roles an IAM user must have to be able to generate their individual access keys?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the mininum roles
        a.  IAM FullAccess  :   To be able to see the roles and perform actions on individual scope
        b.  IAM UserSSHKeys :   To be able to generate their own individual access keys

    Once the iam user has these roles, then 'Security Crendentials' tab under 'Users' will show up without any errors
    and the 'Create aceess key' option will be enabled.
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q13: How to create an access key for an IAM user to be used with CLI or SDK?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Once you have the required roles (IAM FullAccess and IAM UserSSHKeys),
        a.  Click on the Top right of the aws management console on your username
        b.  Click on 'Security Credentials', it will take you to 'My Security Credentials' page
        c.  Scroll towards the bottom and look for 'Access Keys'
        d.  click on 'Create Access Keys', it will display the following options (radio buttons)
            1.  Command Line Interface (CLI)    :   
                {You plan to use this access key to enable the AWS CLI to access your account}

            2.  Local code  :   
                {You plan to use this access key to enable application code in a local development environment to 
                access your AWS account}

            3.  Application running on an AWS compute service   :   
                {You plan to use this access key to enable application code running on an AWS compute 
                service like Amazon EC2, Amazon ECS, Amazon Lambda to access your account}

            4.  Third Party service :   
                {You plan to use this access key to enable access for a third party application or service that 
                monitors or manages your AWS}

            5.  Application running outside AWS :   
                {You plan to use this access key to enable an application running on an on-premise host, or to use a 
                local AWS client or third party aws plugin}

            6.  Other:  {Youyuse case is not listed here.} 

        e.  With selection of any option, AWS will provide a potential recommendation.
        f.  Their is an optional step to create a tag to understand what this key will be used for.
        g.  On the 'Retrieve access keys' page: You will see an option to download the access keys via a 'csv' file 
            and also, save it from the GUI
        h.  Click on 'Done' and you will be navigated back to the 'User page'
        i.  Under the 'Access Keys' section, you will see the key with the tag and statu as 'Active'
        j.  If you wish to generate a new access keys, you can do that, but only one access key can be active at one time.
        k.  Their is an option to delete the keys, if you feel the need to do so.
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q14: What are the minimum policies to have on the role or the user to be able to access AWS Cloud Shell?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their is only one permission which must be assigned to the role or user to have them able to access AWS Cloud Shell
        The policy name is - AWS CloudShellFullAccess
        Once the policy is attached to the user or the role, the cloud shell will work for the user.
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q15: What are IAM roles for services?
-----------------------------------------------------------------------------------------------------------------------------------------------------------

So far, we have dealt with a username accessed by a physical person to be able to perform certain checks or tasks. The next category is to 
have applications talk to each other (similar to one microservice talking to another). For this to happen, the service which is trying to perform 
an action on another service must have the permission to do so. This is managed by IAM roles for the service (or ServiceRoles).

----------------------------------------------------------------------------------------------------------------------------------------------------------- 
    Following are few examples:
        a.  EC2 Instance roles
        b.  Lambda Function roles
        c.  Roles for CloudFormation
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q16: How to create an IAM role for a service?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the AWS management console with a User who has administrative access.
        a.  Navigate to the IAM dashboard by simply searching IAM on the search bar
        b.  From IAM dashboard, navigate to 'Roles' under 'Access Management'
        c.  If this is the first time you are trying to create a role, you will see following roles pre-existing
            1.  AWS ServiceRoleForSupport
            2.  AWS ServiceRoleForTrustedAdvisor
        d.  Click on 'Create Role'
        e.  Next Page will have a header 'Select Trusted Entity' with the following options (radio buttons)
            1.  AWS Service         
            :   {Allows AWS Services like EC2, Lambda or others to perform actions in this account}

            2.  AWS Account        
            :   {Allows entities in other AWS accounts belonging to you or a 3rd party to perform actions in this account}

            3.  Web Identity        
            :   {Allows users federated by the external web identity provider to assumer this role to perform actions 
                in this account}

            4.  SAML 2.0 Federation 
            :   {Allows users federated with SAML 2.0 from a corporate directory to perform 
                actions in this account}

            5.  Custom Trust Policy 
            :   {Create a custom trust policy to enable others to perform actions in this account}

        f.  For ease of understanding, lets create an 'AWS Service' role for an EC2 instance to read data in IAM
        g.  On the 'Add Permissions' page for this new role, search and select 'IAMReadOnlyAccess'
        h.  On the next page, provide a role name and click next
        i.  Once the role is created, it will show up on the 'Roles' page
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q17: What are IAM security tools?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Their are two security tools
        a.  IAM Credentials Report
            This is at the account-level
            Its a report that lists all accounts under your account(root) and the status of their various credentials
        
        b.  IAM Access Advisor
            This is at the user-level
            Access Advisor shows the service permissions granted to a user and when those services where last accessed
            This information can be utilized to revise the policies and implement 'principle of least privilege'
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q18: How to generate a IAM Credentials Report?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the AWS management console with a User who has administrative access.
        a.  Navigate to the IAM dashboard by simply searching IAM on the search bar
        b.  On the IAM dashboard (Left vertical bar), look for 'Credentials Report' under 'Access Report'
        c.  Click on 'Crendentials Report' and then 'Download credentials report'
        d.  The crendentials report has the following columns (per user on the account includinr <root>)
            1.  user
            2.  arn
            3.  user_creation_time
            4.  password_enabled
            5.  password_last_used
            6.  password_last_changed
            7.  password_next_rotation
            8.  mfa_active
            9.  access_key_1_active
            10. access_key_1_last_rotated
            11. access_key_1_last_used_date
            12. access_key_1_last_used_region
            13. access_key_1_last_used_service
            14. access_key_2_active
            15. access_key_2_last_rotated
            16. access_key_2_last_used_date
            17. access_key_2_last_used_region
            18. access_key_2_last_used_service
            19. cert_1_active
            20. cert_1_last_rotated
            21. cert_2_active
            22. cert_2_last_rotated
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q19: How to navigate to Access-Advisor?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the AWS management console with an IAM user
        a.  Navigate to the IAM dashboard by simply searching IAM on the search bar
        b.  On the IAM dashboard (Left vertical bar), look for 'Users'
        c.  Click on users and then click on 'Access Advisor' on the page.
        d.  Access-Advisor tells you  - 'Which particular service was accessed when and based on what policy'
        e.g.
            Service         Policies Granting Permissions       Last Accessed
            AmazonEC2       AmazonEC2FullAccess and 1 More      Today
            AWS Cloudshell  AWSCloudShellFullAccess             Today
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q20: How many types of IAM policies are available in AWS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Identity access management (IAM) is used to define user access permissions with in AWS.
        There are 3 different types of IAM policies available.
        a.  Managed Policies (also called as AWS Managed Policies)
        b.  Customer Managed Policies
        c.  Inline Policies
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q21: What are AWS Managed Policies?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
An AWS Managed Policy is an IAM policy which is created and administered by AWS. AWS provided managed Policies for common use cases based on job function 
(e.g. AmazonDynamoDBFullAccess, AWSCodeCommitPowerUser, AmazonEC2ReadOnlyAccess, etc.)
These AWS-provided policies allow you to assign appropriate permissions to your users, groups, and roles without having to write the policy yourself.
A single Managed Policy can be attached to multiple users, groups, or roles within the same AWS account and across different accounts.
        
    Important Note: You cannot change the permissions defined in an AWS Managed Policy.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q22: What are Customer Managed Policies?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
A Customer Managed Policy is a standalone policy that you create and administer inside your own AWS account. You can attach this policy to multiple users, 
groups, and roles; but only within your own account.
In order to create a Customer Managed Policy, you can copy an existing AWS Managed Policy and customize it to fit the requirements of your organization. Recommended for use cases where the existing AWS Managed Policies don't meet the needs of your environment.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q23: What are inline policies?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
An Inline Policy is an IAM policy which is actually embedded within the user, group, or role to which it applies. There is a strict 1:1 relationship between the entity and the policy.When you delete the user, group, or role in which the Inline policy is embedded, the policy will also be deleted
In most cases, AWS recommends using Managed Policies over Inline Policies. Inline Policies are useful when you want to be sure that the permissions in a policy are not inadvertently assigned to any other user, group, or role than the one for which they're intended (i.e. you are creating a policy that must only ever be attached to a single user, group, or role).

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q24: What is Policy Simulator?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Policy Simulator is a web-interface (available at: https://policysim.aws.amazon.com) that allows you to test policy against specific service and Action. If you are building your own inline policy, its always better to use the policy simulator to test your policy and make changes to get desired results.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Another way to test a policy is via the CLI using the --dry-run flag
        a. --dry-run lets you test an action, it will fail if you do not have the correct permissions.
        b.  It will error out, if the operation can be executed successfully [Request would have succeeded, but DryRun flag is set]
-----------------------------------------------------------------------------------------------------------------------------------------------------------

IAM Exam Tips:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  IAM is Global; It does not apply to regions at this time.
    b.  A Root Account is simply the account created when first setting up an AWS account. 
        It has complete Admin access and should not be used for day-to-day activities.
    c.  When first created, new users have *NO permissions. Permissions must be explicitly 
        given via a group or policy.
    d.  New users are asssigned Access Key ID & Secret Access Keys when first created. 
        These are not the same as a password and cannot be used to login to the 
        AWS Console; instead, they are used to access AWS via the APIs and Command Line.
    e.  You can only view the Access Key ID & Secret Access key once. If you lose them, 
        you must regenerate them. Save them in a secure location.
    f.  Always setup *Multifactor Authentication (MFA) on your root account.
    g.  You can create and customize your own password rotation policies.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Policy Document example
    {
        "Version": "2012-10-17",
        "Statement":
        [
            {
                "Effect": "Allow",
                "Action": "*",
                "Resource": "*"
            }
        ]
    }

