ASG: Auto Scaling Group
-----------------------------------------------------------------------------------------------------------------------------------------------------------

The load on your websites and applications change, hence we need to either scale up or scale down depending on the transaction volume.Cloud platforms provide the feasibility to add / remove servers with a click of few buttons.

The goal of Auto Scaling Group (ASG) is to:
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    a.  Scale OUT (Add EC2 Instances) to match an increased load
    b.  Scale IN (Remove EC2 Instances) to match a decreased load
    c.  Ensure we have a minimum and maximum number of machines running
    d.  Automatically register new instances to a load balancer. (Via Automation)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

    1.  Launch Configuration / Launch Templates for ASG have the following attributes:
        a.  AMI + Instance Type
        b.  EC2 User Data
        c.  EBS Volumes
        d.  Security Groups
        e.  SSH Key pairs
    2.  Minimum Size / Maximum Size / Initial capacity
    3.  Network + Subnets Information
    4.  Load Balancer Information
    5.  Scaling Policies

-----------------------------------------------------------------------------------------------------------------------------------------------------------

    Special Notes:
        a.  IAM roles attached to the ASG will automatically get assigned to the EC2 instances.
        b.  ASG is free to use, however the cost is incurred for the underlying resources being launched.
        c.  ASG does not stop or start instances, it will terminate the instance when LB marks the instance as unhealthy 
            and REPLACES them
        d.  Having instances under ASG, means that if they get terminated for whatever reason, ASG will automatically 
            create new ones as replacement.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What is an Auto Scaling Alarm?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    It is possible to scale an ASG based on CloudWatch alarms.
        A Cloudwatch alarm monitors a metric (such as an Average CPU)
        Metrics are computed for the overall ASG instances.
        Based on the alarms:
            a.  We can create scale-out policies (increase the number of instances)
            b.  We can create scale-in policies (decrease the number of instances)

                                                                            Auto Scaling Group
                                                                ---------------------------------------------
        CloudWatch --------Trigger Scaling------------------->  | EC2-1; EC2-2; EC2-3......EC2-N            |
        ALARM                                                   ---------------------------------------------
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q02: What are Auto Scaling Rules?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Its now possible to define 'Better' auto scaling rules that are directly managed by EC2, based on
        a.  Target Average CPU Usage
        b.  Number of requests on the ELB per instance. 
            (for e.g. 100 requests to one instance from ELB to trigger scaling)
        c.  Average Network In
        d.  Average Network Out
    
        Auto Scaling Custom Metrics:
        We can auto scale based on a custom metric as well (for e.g. number of connected users or based on a schedule)
        a.  Send Custom Metric from application on EC2 to CloudWatch (using PutMetric API)
        b.  Create CloudWatch alarm to react to low / high values
        c.  Use the CloudWatch alarm as the scaling policy for the ASG.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q03: How to create an Auto Scaling Group?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps:
        a.  Login to the EC2 Dashboard
        b.  In the left side vertical menu, under 'Auto Scaling' click on 'Auto Scaling Groups' --> 'Create Auto Scaling Group'
        c.  Provide a name for the 'Auto Scaling Group'
        d.  Under 'Launch Template' click on 'Create a Launch Template'
            1.  Provide a name for the launch template.
            2.  Provide a name for the template version description.
            3.  Under Launch Template Contents
                i.  Select an AMI
                ii. Select an Instance type
                iii.Select a Key-Pair OR you can create one
                iv. Under Network Settings - Select Virtual Private Cloud (VPC)
                v.  Select 'Security Groups': This must be accurate or else the EC2 instances will not be accessible by you or ELB.
                vi. Select Storage
                vii.Under Advanced details, add user data that you want to use.
        e.  Now you will be redirected to 'Launch Template' and you can select the template that you created from the drop down.
        f.  Under the 'Instance Purchase options' their are two values, select the one with which you are comfortable, based on cost.
            1.  Adhere to Launch Template: The Launch Template determines the purchase option (on-demand or spot) and instance type
            2.  Combine Purchase options and Instance types: Specify how much on-demand and spot capacity to launch and multiple 
                instance types (optional). This choise is most helpful for optimizing the scale and cost for a fleet of instances.
        g.  Under 'Network'
            1.  Select the default VPC
            2.  And for subnets, select the AZs you want the EC2 instances to be launched (you can select one or many)
        h.  Under 'Configure Advanced Options'
            1.  Load Balancing (Optional) : You can either use an ELB or not
                i.  No Load Balancer: Traffic to your auto scaling group will not be fronted by a load balancer.
                ii. Attach to an existing load balancer: Choose from your existing load balancers.
                iii.Attach to a new load balancer: Quickly create a basic load balancer to attach to your ASG.

            If you select an ALB (that was created before), you will need to select a Target group as well.

        i.  Under Health Checks (optional): Has two options:
            1.  EC2     :   Selected by Default and cannot be un-selected
            2.  ELB     :   Not Selected by default
            If you select the ALB in previous step, ELB must be selected in health checks.
            The idea is, if the EC2 instance is for some reason misbehaving and is deemed unhealth by LB, then it will deemed 
            unhealthy in ASG as well. Thereby triggering ASG to terminate the unhealthy instance and replacing it with a new one.

        j.  Under 'Configure Group Size and Scaling policies'
            1. Select the : Desited Capacity, Minimum Capacity and Maximum capacity for count of EC2 instances to be launched.
            2. Scaling Polies are optional: This helps to dynamically resize your ASG to meet the changes in demand.
                Two Valid Values: 
                i.  None
                ii. 'Target Tracking Scaling Policy': Choose a desired outcome and leave it to the scaling policy to add and remove 
                    capacity as needed to achieve the outcome.
        k.  Instance scale-in-Protection (optional)
            If protect from scale in is enabled, newly launched instanes will be protected from scale in by default.
        l.  Review and create your 'Auto Scaling Group'.
        m.  Once the 'ASG's is created, click on its name and go to 'Activity Tab' and then to 'Activity History'
            You'll see the creation and termination of EC2 instances under 'Activity History'

    Special Note:
        If you select the ELB along with Auto Scaling Group, the EC2 instances will be automatically registered with the ELB.
        If for some reason, the EC2 instance is unhealthy, ASG will terminate it and replace it with a new one, and the new 
        EC2 instance will again be automatically registered with ELB.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q04: How many ASG - Scaling Polcies are there?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    There are 3 ASG - Scaling Policies.
        a.  Target Tracking Scaling:
            e.g.:   You want the average ASG CPU to be around 40%, then ASG will scale out or scale in to match this rule 
                    depending on the CPU.
        b.  Simple / Step Scaling:
            e.g.:   When a CloudWatch alarm is triggered (if CPU > 70%), then add 2 EC2 units
                    When a CloudWatch alarm is triggered (if CPU < 30%), then remove 1 EC2 units
            This has some more control, since YOU are deciding the number of EC2 instances instead of letting ASG Decide.
        c.  Scheduled Actions:
            This policy is based on anticipation of the usage pattern.
            e.g.:   Increase the minimum capacity to 10 EC2 instances on Black Friday at 6 AM.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q05: What is ASG - Scaling Cooldowns?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    The cooldown period helps to ensure that your Auto Scaling Group doesn't launch or terminate additional instances, 
    before the previous scaling activity takes effect.

    In Addition to the default cooldown for ASG: We can create cooldowns that apply to a specific 'SIMPLE SCALING POLICY'

    USECASE:
        One common use for scaling-specific cooldowns is with a scale-in policy:
            A policy that terminates instances based on a specific criteria or metric. Because the policy terminates 
            instances, ASG needs less time to determine, whether to terminate additional instances.
            
        If the default cool down period of 300 seconds is too long:
            You can reduce costs by applying a scaling-specific cooldown period of 180 seconds to scale-in policy.
            
        If your application is scaling up and down multiple times in an hour, modify the ASG cool-down timers and the 
        CloudWatch alarm period that triggers the scale in.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
