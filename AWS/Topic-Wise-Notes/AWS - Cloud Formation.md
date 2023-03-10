-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS - Cloud Formation
-----------------------------------------------------------------------------------------------------------------------------------------------------------
CloudFormation is a service that allows you to 
    a.  manage
    b.  configure
    c.  provision your AWS infrastructure as code.

    Special Note:
    a.  Resources are defined using a CloudFormation template.
    b.  CloudFormation interprets the template and makes the appropriate API calls to create the resources you have defined
    c.  Supports YAML or JSON

Benefits of CloudFormation:
    a.  Infrastructure is provisioned consistently, with fewer mistakes
    b.  Less time and effort than configuring things manually
    c.  You can version control and peer review your templates
    d.  Free to use (charged for what you create)
    e.  Can be used to manage updates and dependencies
    f.  Can be used to rollback and delete the entire stack as well.

CloudFormation Template:
    a.  YAML or JSON template used to describe the endstate of infrastructure you are either provisioning or changing.
    b.  After creating the template, you upload it to CloudFormation using S3.
    c.  CloudFormation reads the template and makes the API calls on your behalf.
    d.  The resulting resources are called a stack.