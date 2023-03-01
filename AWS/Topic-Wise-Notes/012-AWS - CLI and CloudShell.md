AWS - CLI & Cloud Shell
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q01: In how many ways, can the users access AWS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    There are 3 ways by which users can access AWS
        a.  AWS Management Console (protected by password + MFA)
        b.  AWS Command Line Interface (CLI): protected by access keys
        c.  AWS Software Development Kit (SDK): for code: protected by access keys
    
    Note: 
    Access keys are generated using the AWS console
    Users manage their own access keys (access keys id ~= username; secret access key ~= password), 
    so every IAM user can have their own keys

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q02: How to configure AWS CLI on windows?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps:
        a.  Download the AWSCLI version for windows and install on your machine.
        b.  To verify, if it was installed correctly, you can type 'aws --version' on the 
            windows command prompt & the output should look like the following

            C:\Users\samarth>aws --version
            aws-cli/2.9.19 Python/3.9.11 Windows/10 exe/AMD64 prompt/off

        c.  Now, its time to configure aws cli on the windows machine, you will neeed the following
            a.  Your access key
            b.  Your secret key
            c.  Region (select the one closest (for training purposes))
        d.  Execute 'aws configure' on the windows command prompt

            C:\Users\samarth>aws configure
                AWS Access Key ID [None]: MyAccessKey
                AWS Secret Access Key [None]: MySecretKey
                Default region name [None]: us-east-1
                Default output format [None]:
            C:\Users\samarth>
        6.  Now the AWS CLI is configured, we run the following command to see, if it returns an output.

            C:\Users\samarth>aws iam list-users

            {
                "Users": [
                    {
                        "Path": "/",
                        "UserName": "Samarth-Admin",
                        "UserId": "AIDA*************",
                        "Arn": "arn:aws:iam::*************:user/Samarth-Admin",
                        "CreateDate": "2023-01-29T15:31:41+00:00",
                        "PasswordLastUsed": "2023-01-29T16:36:37+00:00"
                    },
                    {
                        "Path": "/",
                        "UserName": "Samarth-Developer",
                        "UserId": "AIDA*************",",
                        "Arn": "arn:aws:iam::*************:user/Samarth-Developer",
                        "CreateDate": "2023-01-29T13:59:14+00:00",
                        "PasswordLastUsed": "2023-01-29T16:35:12+00:00"
                    }
                ]
            }
            C:\Users\samarth>
        
    Important Note: AWS-CLI is just another method of accessing the data, the data shows will always be same across 
                    management console and CLI
    
    For e.g.:- If we go ahead and remove the policy 'IAM FullAccess' from the group 'AWS-Developer', which IAM user 
    'Samarth-Developer' is a part of, And then execute the same command (aws iam list-users) from windows command prompt, 
    their will be no output, same can be validated by going to the Management console, under users page, you will see 
    'You need Permissions' message.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q03: What is AWS CloudShell?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    AWS CloudShell is a browser-based shell that makes it easier to securely manage, explore, and interact with 
    your AWS resources. 
    CloudShell is pre-authenticated with your console credentials.

    {So if you are logged in as 'samarth-developer', the same credentials will be used by default}
    For an IAM user to be able to use the AWS CloudShell, the user must have the 'AWS CloudShellFullAccess' 
    permission policy attached to the user id either by a group policy or a user policy.

    Note: The username for cloudshell is:- cloudshell-user

        [cloudshell-user@ip-10-0-124-229]$aws iam list-users

        {
            "Users": [
                {
                    "Path": "/",
                    "UserName": "Samarth-Admin",
                    "UserId": "AIDA*************",
                    "Arn": "arn:aws:iam::*************:user/Samarth-Admin",
                    "CreateDate": "2023-01-29T15:31:41+00:00",
                    "PasswordLastUsed": "2023-01-29T16:36:37+00:00"
                },
                {
                    "Path": "/",
                    "UserName": "Samarth-Developer",
                    "UserId": "AIDA*************",",
                    "Arn": "arn:aws:iam::*************:user/Samarth-Developer",
                    "CreateDate": "2023-01-29T13:59:14+00:00",
                    "PasswordLastUsed": "2023-01-29T16:35:12+00:00"
                }
            ]
        }
        [cloudshell-user@ip-10-0-124-229]$

-----------------------------------------------------------------------------------------------------------------------------------------------------------