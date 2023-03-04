Budget and Billing
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: Can an IAM user access the Billing and Cost Management Dashboard by default?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    No, the only user who can access Billing and Cost Management Dashboard by default is the root user.
    The root user needs to provide permissions to IAM user - so that they can also access Billing and Cost information

    Following are the steps for the root user to allow access.
    Note:   This approach only works for an IAM user with Administrator Access

    a.  Login as the root user
    b.  On the top right click on Login name and then click on 'Account'
    c.  Once navigated to the new page, look for 'IAM User and Role Access to Billing Information'
    d.  Click on 'Edit' and then 'Activate IAM Access'
    e.  Refresh the page and now log in as the IAM user with Administrator Access
    f.  Click on the top right on login name and then click on 'Billing Dashboard'
    h.  Since the IAM access has been activated, this IAM user will now be able to see the AWS Billing Dashboard

    To provide 'AWS Billing Dashboard' Access to a non-administrative IAM user, the steps are different

    a.  Login as the root user
    b.  Navigate to the IAM dashboard by simply searching IAM on the search bar
    c.  Under 'Access Management' click on 'User Groups'
    d.  Click the group, to which the non-administrative IAM user belongs to
    e.  Click on 'Permissions'
    f.  Search for 'Billing' permission policy and attach this policy to this group.
    8.  Now the 'Non-administrative' IAM User should also have access to the AWS Billing dashboard.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
Q02: How to create a Budget?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Login to the management console as an Administrative / root user
-----------------------------------------------------------------------------------------------------------------------------------------------------------
        a.  On the top right click on Login name and then click on 'Billing Dashboard'
        b.  On the left vertical menu (side bar), click on 'Budgets' under 'Cost Management'
        c.  On the 'Budgets' page, click on 'Create a Budget'
        d.  Their are two budget set up types, 'Use a template (simplified)' and 'Customize (advanced)'
        e.  Select 'Use a Template (simplified)'
        f.  Their are multiple templates, namely (Radio Buttons)
            1.  'Zero spend budget':    {Create a budget that notified you once your spending exceeds $0.01 which is above the AWS free tier limits}
            2.  'Monthly Cost Budget':  {Create a monthly budget that notified you if you exceed, or are forecasted to exceed, the budget amount}
            3.  'Daily Savings Plans Coverage budget':  {Create a coverage budget for your savings plans that notifies you when you fall below the 
                defined target}
            4.  'Daily reservation utilization budget': {Create a utilization budget for your reservations that notifies you when you fall below the 
                defined target}
        g.  Click on 'Monthly Cost Budget'
        h.  Provide the following values
            1.  Budget Name
            2.  Enter your budgeted amount ($)
            3.  Email Recipients:   {To receive threshold alerts}
        i.  Once the budget is created, 

-----------------------------------------------------------------------------------------------------------------------------------------------------------