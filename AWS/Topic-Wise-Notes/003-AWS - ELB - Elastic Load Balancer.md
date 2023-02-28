ELB : Elastic Load Balancer
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q01: What is a load balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Load balancer are servers that forward the internet traffic to multiple servers (EC2 instances) downstream.
        a.  Load Balancers can scale but not instantaneosuly - contact AWS for a "Warm-Up"
        b.  Troubleshooting an ELB:
            1.  4xx errors are client induced errors
            2.  5xx errors are application induced errors
            3.  Load Balancer Errors 503 means 'at capacity' or no registered target
            4.  If the LB can't connect to your application, check your security groups
        c.  Monitoring an ELB:
            1.  ELB Access logs will log all access requests (so you can debug per request)
            2.  CloudWatch metrics will give you aggregate statistics (e.g; Connections Count)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q02: Why use a load balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the reasons for using a load balancer
        a.  To spread the load across multiple downstream instances
        b.  Expose a single point of access (DNS) to your application
        c.  Seamlessly handle failures of downstream instances
        d.  Do regular health checks to your instances
        e.  Provide SSL termination (HTTPS) for your websites
        f.  Enforce stickiness with cookies
        g.  High availability across AZs (Assuming your Loadbalancer is spread across different AZs)
        h.  Separate public facing traffic from private facing traffic.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q03: Why use an EC2 Load Balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    An ELB (Elastic Load Balacer / EC2 Load Balancer) is a MANAGED load balancer
        a.  AWS guarantees that it will be working
        b.  AWS takes care of upgrades, maintenance, high availability
        c.  AWS provides only a few configuration knobs to the user.
    
    Special Notes:
        1.  Its costs less to set up your own load balancer but its lot of effort to set it up
        2.  ELB is integrated with many AWS offerings / Services
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q04: Why are Health Checks important?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
Health checks are crucial for load balancers,and enable them to know if the instances it forwards traffic to are healthy (Basically checking, if the instances are available to reply to the requests) The health check is done on a port (for e.g. 7066) or a route (/health) If the response is not 200 (OK), then the instance is deemed 'Unhealthy' and the Load Balancer will stop sending traffic to this instance. This health check usually happens usually every 5 seconds, but is a configurable value.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q05: How many types of Load Balancers are their in AWS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    AWS has 3 different types of MANAGED load balancers
        a.  CLASSIC Load Balancer:  (v1- Old Generation - 2009)
            This supports: HTTP, HTTPS, and TCP
        b.  Application Load Balancer: (v2- New Generation - 2016)
            This supports: HTTP, HTTPS, WebSocket
        c.  Network Load Balancer:  (v2- New Generation - 2017)
            This supports: TCP, TLS (secure TCP) & UDP
        
        Elastic Load Balancer can be set up as internal (private) ELB or external (public) ELB

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q06: Explain Load Balancer Security Group?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following is the explanation

                (HTTPS/ HTTPS from anywhere)        (HTTP restricted to/from ELB)
        USERS   ----------------------------->  ELB ----------------------------->  EC2
                <-----------------------------      <-----------------------------
        
        In this design:
        a.  The Load balancer is exposed to the public internet and hence it can accept incoming traffic at
            Port 80 over HTTP
            Port 443 over HTTPS
            So, the load balancer security will have these two rules (1 for port 80 another for port 443)
                type        :   HTTP
                Protocol    :   TCP
                PortRange   :   80
                Source      :   Custom: 0.0.0.0/0 (Anywhere)

        b.  Now the load balancer needs to forward the incoming traffic to the EC2 instance, so we will need another security group
            That will be used to forward the traffic to EC2
                LoadBalancerProtocol:   HTTP
                LoadBalancerPort    :   80
                InstanceProtocol    :   HTTP
                InstancePort        :   80

        c.  The EC2 instance is only exposed to the load balancer and hence can accept incoming traffic at
            Port 80 over HTTP only from the LOAD BALANCER SECURITY GROUP
    
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q07: What is a Classic Load Balancer(v1)?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Classic Load Balancer are generation 1 load balancers and support HTTP, HTTPS and TCP protocols.
        TCP is a layer4, while HTTP and HTTPS are layer7 protocols.
        a.  Health checks are TCP or HTTP based.
        b.  Classic LB provide you with a fixed hostname: e.g; : xxx.region.elb.amazonaws.com

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q08: How to create a CLASSIC load Balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    For creation of CLASSIC load balancer, we will need atleast 2 EC2 instance to be able to see if CLB is forwarding traffic correctly
        a.  Login to the EC2 Dashboard
        b.  Under 'Network & Security' click on 'Security' and create a new 'security-group' with inbound rule to allow 
            http at port 80 from anywhere
        c.  Create two new EC2 instances and select this newly created security as their security group.
        d.  In the left side vertical menu, under 'Load Balancing' click on 'Load Balancers' then click on 'Create Load Balancer'
        e.  select 'Classic Load Balancer' and click on create.
        f.  on the 'Define Load Balancer': Provide a Name to the Load Balancer in the default VPC.
            1. LoadBalancerProtocol:   HTTP
            2. LoadBalancerPort    :   80
            3. InstanceProtocol    :   HTTP
            4. InstancePort        :   80
        g.  Since this will be a public facing ELB, DO NOT select 'Create an internal Load Balancer'.
        h.  On the 'Assign Security Group' select the security group that was create in step (b)
        i.  Since we have HTTP protocol and not HTTPS, AWS will show a warning message.
        j.  On the 'Configure Health Check'
            1. Ping Protocol: HTTP
            2. Ping Port: 80
            3. Ping Path: can be '/' or '/index.html' depending on if you have HTTPD enabled and have a index.html in 
                /var/www/html/index.html
            4. Response Timeout: 5 seconds
            5. Interval: 30 seconds
            6. Unhealthy Threshold: 2 seconds
            7. Healthy Threshold: 10
        k.  Select the instances that you want to map to this classic load balancer.
        l.  Review and create and then 'Create' the Classic Load Balancer.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
        
Q09: What does ELB status 'Out-of-Service' means?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    The status 'Out-of-Service' will be shown on the EC2 dashboard for the ELB, when
        a.  The instance is newly created and the EC2 instances are still being registered with the ELB
        b.  The instance is unhealthy and the healthchecks have failed consecutively.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q10: What is an Application Load Balancer(v2)?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Application load balancers operate at layer 7 (HTTP)
        a.  Load Balancing to multiple HTTP applications across machines (called as Target Groups)
        b.  Load Balancing to multiple applications on the same machine (e.g. Containers)
        c.  Support for HTTP/2 and WebSocket
        d.  Supports redirects (from HTTP to HTTPS).
        e.  Supports routing based on path in URL (example.com/users & example.com/posts)
        f.  Supports routing based on hostname in URL (one.example.com & other.example.com)
        g.  Supports routing based on query string, headers (example.com/users?id=123&order=false)
    
        Special Note: 
            a.  ALBs are great fit for microservices & container-based applications (e.g; Docker & Amazon ECS), 
                because these have a port mapping feature to redirect to a dynamic port in ECS (Elastic Container Service).
            b.  ALBs also provide a fixed hostname like Classic LBs (XXX.region.elb.amazonaws.com)
            c.  The application servers dont see the IP of the client directly, rather the true information of the 
                clients are in the headers
                1. X-Forwarded-For: ClientIP
                2. X-Forwaded-port: Port
                3. X-Forwaded-Proto: Protocol
            d.  Latency for ALBs is around 400ms
        
        ALBs can route traffic to: (IP Addresses - MUST BE PRIVATE IPS)
            a.  EC2 instances (can be managed by an Auto Scaling Group) - HTTP
            b.  ECS tasks (managed by ECS itself) - HTTP
            c.  Lambda Functions - HTTP Request is translated into a JSON format.
            d.  Multiple Target groups, and health checks are at the target level.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q11: How to create a Application Load Balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps:
        a.  Login to the EC2 Dashboard
        b.  In the left side vertical menu, under 'Load Balancing' click on 'Load Balancers' then click on 'Create Load Balancer'
        c.  select 'Application Load Balancer' and click on create.
        d.  On the 'Configure Load Balancer' - Basic configuration
            1.  Provide a name for the application load balancer
            2.  Scheme :    Internet-Facing
            3.  IP Address Type: IPv4
            4.  Listeners : A listener is a process that checks for connection requests, using the protocol and port that is configured
                i.  Load Balancer Protocol: HTTP
                ii. Load Balancer Port: 80
            5.  For Availability Zone:
                i.  Select the default VPC
                ii. Select the AZs which you want to configure for the ALB.
            6.  On the 'AWS global accelerator, do noting.
        e.  On the 'Configure Security Settings'
            Since we used HTTP port instead of HTTPS: AWS will show a security warning.
            Now, you can either create a new security group that will accept traffic from 'Anywhere' to ALB-port 80 with HTTP protocol.
            OR, if you already have one, you can use it. Make a note, which security group was configured.
        f.  On the 'Configure Routing' page
            1.  Target Group:   New Target Group
            2.  Name        :   Provide a target group name
            3.  Target Type :   We will select 'Instance' since we will map EC2 instance to this ALB
                            :   Valid values are 'Instance', 'IP' , 'Lambda Function' (Radio Button Selection)
            4.  Protocol    :   HTTP
            5.  Port        :   80
            6.  Protocol Ver:   HTTP1 {Send requests to targets using HTTP/1.1; supported when the request is HTTP/1.1 or 1.2}
                                Valid values are: HTTP2 and gRPC
            7.  healthchecks:
                            protocol: HTTP
                            path    : /
            8.  Advanced Health Check settings
                i.  Port                :   traffic port (Other valid value is override)
                ii. Healthy Threshold   :   3
                iii.Unhealthy Threshold :   2
                iv. Timeout             :   5
                v.  Interval            :   30
                vi. Success Codes       :   200
        g.  On the 'Register Targets'
            Whatever number of instances that you select will be added to one target group.
            For e.g.: If you have 3 instances and you selected only 2, then these 2 instances will be part for the first target group
            The 3rd instance can be added to the ALB later on, as another target group.

            This is one of the important upgraded features of ALB, and then you can route traffic to these target groups based on a 
            variety or parameters in the routing rules.
        h.  Once the targets are registered, click on create and 'ALB' will be created.
        i.  Now navigate to the 'Load Balancer' on the left vertical menu and look for your newly created ALB.
        j.  Under ALB - 'Description' look for 'DNS Name': This is the url that be used to access the ALB from anywhere.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q12: How to add a new target group to an existing ALB?
    Following are the steps
        a.  Login to the EC2 Dashboard
        b.  In the left side vertical menu, under 'Load Balancing' click 'Target Groups'
        c.  'Create target group'
            Under Basic configuration:
            1.  Target Group:   New Target Group
            2.  Name        :   Provide a target group name
            3.  Target Type :   We will select 'Instance' since we will map EC2 instance to this ALB
                            :   Valid values are 'Instance', 'IP' , 'Lambda Function' (Radio Button Selection)
            4.  Protocol    :   HTTP
            5.  Port        :   80
            6.  Protocol Ver:   HTTP1 {Send requests to targets using HTTP/1.1; supported when the request is HTTP/1.1 or 1.2}
                                Valid values are: HTTP2 and gRPC
            7.  healthchecks:
                            protocol: HTTP
                            path    : /
            8.  Advanced Health Check settings
                i.  Port                :   traffic port (Other valid value is override)
                ii. Healthy Threshold   :   3
                iii.Unhealthy Threshold :   2
                iv. Timeout             :   5
                v.  Interval            :   30
                vi. Success Codes       :   200
        d.  On the 'Register Targets' page
            1.  Select the instance you want to add to this new target group
            2.  Click on 'Include as pending below'
            3.  Under 'Targets': This new entry will show as 'Pending'
        e.  Now we have a new target group created, it can now be added to the ALB.
        f.  In the left side vertical menu, under 'Load Balancing', click on 'Load Balancers'
        g.  Once the 'Load Balancer' page opens, select the ALB that you want to modify.
        h.  Click 'Listeners' and then 'Add Listeners'
        j.  Under 'Rules' click on 'view/edit' rules.
        k.  On the 'Rules' page, click on '+' on the header.
        l.  Add the 'Add Condition'd for IF and 'Add action' for THEN and click save.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q13: What is NLB or Network Load Balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Network Load balancers operate at layer 4, and allow you to 
        a.  Forward TCP and UDP traffic to your instances.
        b.  Handle millions of requests per seconds, so extremely high performance
        c.  Very low latency ~ 100ms
        d.  Supported protocols (TCP, TLS, UDP)
    
    Special Note:
        1.  NLB has ONE STATIC IP per AZ, and supports assigning Elastic IP (Helpful for whitelisting specific IP)
        2.  NLBs are used for extreme performance, TCP or UDP traffic.
        3.  Not included in the Free-Tier

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q14: How to create a Network Load Balancer?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Following are the steps
        a.  Login to the EC2 Dashboard
        b.  In the left side vertical menu, under 'Load Balancing' click on 'Load Balancers' then click on 'Create Load Balancer'
        c.  select 'Network Load Balancer' and click on create.
        d.  Under 'Basic Configuration'
            1.  Provide a name for your 'Load Balancer'
            2.  Select a valid scheme (valid values are 'Internet-Facing or Internal)
            3.  Select a valid 'IP Address Type' (valid values are IPV4, DualStack)
            4.  Network-Mapping:
                i.  Select the default VPC.
                ii. Mappings: Select the AZs you wish to attach to the NLB.
                iii.When you select the AZ, under particular AZ you will have an option of 'IPV4 Address'
                    This will have two valid values ('Assigned by AWS' and 'Use an elastic IP address')
                    ** This is a special feature only for NLB to have a dedicated static IP for whitelisting.
            5.  Under 'Listeners and Routing'
                Protocol:   TCP
                Port    :   80
                Default Action: Foward to - Select a Target Group here (if you have one existing, else create on.)
                Click on 'Add Listener.
            6.  Advanced Health Check settings
                i.  Port                :   traffic port (Other valid value is override)
                ii. Healthy Threshold   :   3
                iii.Unhealthy Threshold :   2
                iv. Timeout             :   5
                v.  Interval            :   30
                vi. Success Codes       :   200
        e.  Under 'Register Targets', select the instance and then 'Include as pending below'
        f.  The EC2 instance may show as 'Unhealthy' depending on, if correct security groups are not mapped.
        g.  Make sure, correct security groups are added to the Instances.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q15: What is Load Balancer Stickiness?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Load Balancer stickiness is the mechanism that ensures the same client is always redirected to the same instances behind LB
        This options works on both the CLB and ALB.
        This mechanism is implemented with the help of 'cookie' which has an expiration date that you can control.
        Enabling stickiness may bring imbalance to the load over the backend EC2 instances.

        Special Note:
            USE CASE: Make sure the user doesn't lose his/her session data.
            1.  Stickiness for CLB: Can be enabled at the CLB level
            2.  Stickiness for ALB: Can be enabled at the Target Group level.
        
        Once you enable the stickiness, you have to provide the duration for the stickiness after which stickiness will expire
        The minimum value is 1 second while the maxixum value is 7 days.

-----------------------------------------------------------------------------------------------------------------------------------------------------------
    
Q16: What is cross-zone load balancing?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    Consider the following scenario:
        You have two AZs: AZ1 and AZ2; and AZ1 has LB as LB1, while AZ2 has LB as LB2.
        Now, LB1 has two EC2 instances attached to it and LB2 has 8 instances attached to it.
        So, over all we have 10 EC2 instances with two different LBs, this is a highly imbalanced situation for traffic.

        With Cross Zone Load balancing:
        Even if the client is sending equal (50%) traffic to both the LBs, each LB will distribute even (10%) traffic each EC2 instance.

        Without Cross Zone load balacing:
        With client sending equal(50%) traffic to both the LBs, LB1, will eventually end up sending 25% of traffic to each EC2 in AZ1, while LB2 
        will send 6.25% traffic to each instance in AZ2

        Special Note:  Cross Zone Load Balacing is Enabled or Disabled by default, depending on the type of the LB.
        a.  CLB:
            1.  If the CLB is created from the management console, 'Cross Zone Load Balancing' is enabled by default.
            2.  If the CLB is creted by 'CLI/API', 'Cross Zone Load Balancing' is disabled by default.
            3.  No Additional Charges are incurred between inter AZ data {when Cross Zone Load Balancing is enabled}
        
        b.  ALB:
            1.  'Cross Zone Load Balacing' is always ON and cannot be disabled.
            2.  No Additional Charges are incurred between inter AZ data
        
        c.  NLB:
            1.  'Cross Zone Load Balancing' is DISABLED by default, but can be 'Enabled'
            2.  Additional charges are incurred for inter AZ data {when Cross Zone Load Balancing is enabled}

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q17: Explain SSL/TLS?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    An SSL certificate allows the traffic between your clients and your load balancer to be encrypted in transit (in-flight encryption)
        a.  SSL refers to the 'Secure Socket Layer', used to encrypt connections.
        b.  TLS refers to Transport Layer security, which is a newer version.
        
        Now a days, TLS certificates are mainly used
        Public certificates are issued by Certificate Authorities (CA): Symantec, GoDaddy, Digicert etc.

        Special Note: SSL certificates have an expiration date and must be renewed. 

        Load Balancer SSL certificates

                    (HTTPS encrypted over www)          (HTTP over private VPC)
        USERS   ----------------------------->  ELB ----------------------------->  EC2
                <-----------------------------      <-----------------------------
        
        a.  Load Balancer uses an X.509 certificate (SSL/TLS Server Certificate)
        b.  You can manage certificates using ACM (AWS Certificate Manager)
        c.  You can create / upload your own certificates as well.
        d.  You must configure HTTPS listener for your ELB
            1.  You must specificy a default certificate.
            2.  You can add an optional list of certs to support multiple domains
            3.  Clients can use SNI (Server Name Indication) to specify the hostname they want to reach
            4.  Ability to specify a security policy to support older versions of SSL/TLS (legacy clients)

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q18. What is SNI (Server Name Indication)?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    SNI (Server Name Indication) solves the problem of loading multiple SSL certificates onto one web server (to serve multiple websites)
        Its a newer protocol and requires the client to indicate the hostname of the target server in the initial SSL handshake
        The server will then find the correct certificate, or return the default one.

        Special Note: SNI only works with ALB, NLB and CloudFront.
        Does NOT work with CLB.

        ELB with SSL Certificates:
        a.  CLB:
            1.  Supports only one SSL certificate
            2.  Must use multiple CLBs for multiple hostname with multiple SSL certificates.
        b.  ALB:
            1.  Supports multiple listeners with multiple SSL certificates.
            2.  Uses server name indication (SNI) to make it work
        c.  NLB:
            1.  Supports multiple listeners with multiple SSL certificates.
            2.  Uses server name indication (SNI) to make it work

-----------------------------------------------------------------------------------------------------------------------------------------------------------

Q19: What is Connection Draining in CLB or Deregistration Delay in ALB/NLB?
-----------------------------------------------------------------------------------------------------------------------------------------------------------
    'Connection Draining in CLB' or 'Deregistration Delay in ALB/NLB' refers to the 'Time to complete "In-flight requests", 
    while the instance is de-registering or unhealthy.

        While this phenomena happens:
        a.  ELB will stop sending new requests to the instances that is 'de-registering'
        b.  The default configuration to handling existing requests while the instance is 'de-registering' is 300 seconds, but can be between 1s to 1HR
        c.  This configuration can be disbaled as well.
        d.  This number should be configured based on your application behaviour.

-----------------------------------------------------------------------------------------------------------------------------------------------------------