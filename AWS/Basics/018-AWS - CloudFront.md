-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS - Cloud Front
-----------------------------------------------------------------------------------------------------------------------------------------------------------

AWS CloudFront is a globally-distributed network offered by Amazon Web Services, which securely transfers content such as software, SDKs, videos, etc., to 
the clients, with high transfer speed. Its a content delivery network, and improves read performance since content is cached at the edge locations.
This also provides the following
    a.  DDoS Protection
    b.  Integration with Shield
    c.  AWS Web application firewalld
    d.  Provides a way to front your applications when you deploy applications globally
    e.  Allows you to expose HTTPS and can talk to Internal HTTPS backends, by loading the certificates.

    Consider the following example:
    Say we have an S3 bucket in Australia, and a user in USA wants to access it. So the User in USA will access an edge location close to it (in USA) and then 
    the edge location network will be trasmitted all the way to the S3 bucket in Australia via a 'Private Link' and the content will be cached.
    The idea of caching here is, if their are more users in USA who want the same content, then the cached content will be available to them very quickly and 
    the content will be delivered to them directly from USA. Similarly a user in any other geography will have the same experience, since the content will be 
    made available to the user(s) closest edge location.
    This basically allows the content to be read from all around the world, improves a lot on the latency and reduces the load on your S3 bucket.

    Q01: What are different CloudFront: Origins?
    A01: Following is the list
        a.  S3 Bucket:  CloudFront in front of S3 bucket (very common pattern)
            1.  For distributing files and caching them at the edge
            2.  Enhanced Security with CloudFront : Origin Access Identity
                i.  OAI : Allows communication to S3 only from CloudFront and from nowhere else
            3.  CloudFront can be used as an Ingress (to Upload Files to S3)
        
        b.  Custom Origin (HTTP:)   :
            1.  Can be an Application Load Balancer
            2.  EC2 instance
            3.  S3 website (* Must enable the S3 bucket as a static S3 Website)
            4.  Any HTTP backend you want {For e.g.: It can be any HTTP backend even from your own premise}

    Q02: Explain how cloud front works?
    A02: We have a bunch of edge locations all around the globe and they are connected to an origin (can be any origins mentioned above) and the clients wants
        to access our CloudFront distribution. For this the client will send a 'HTTP Request' (Their will be a URL with some query string parameters, some hearders) 
        directly to CloudFront. The Cloud front will send this request with the headers to the origin (can be any origins mentioned above). The origin then responds 
        to the edge location, the edge location will 'cache' the response based on the configuration and return the response to the clients.
        The next time another client makes the same request, the edge location will first look into the cache before forwarding the request to the Origin

        ![](https://d2908q01vomqb2.cloudfront.net/5b384ce32d8cdef02bc3a139d4cac0a22bb029e8/2022/07/15/CF-S3-active-active-geo-proximity-architecture-1024x636.png)