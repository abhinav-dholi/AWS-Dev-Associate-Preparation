# Section 7: AWS Fundamentals: ELB + ESG #

## Scalability and High Availability ##

* Scalability means that an application / system can handle greater loads by adapting.
* There are two kinds of scalability
  * Vertical Scalability
  * Horizontal Scalability
* **Scalability is linked but different to high availability**

## Elastic Load Balancing (ELB) ##

* Load Balancers are servers that forward traffic to multiple servers (eg.. EC2 instances) downstream.

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_1.png"  width="80%" height="40%">

## Why to use a Load Balancer? ##

* Spread load across multiple downstream instances
* Expose a single point of access (DNS) to your application
* Seamlessly handle failures of downstream instances
* Do regular health checks to your instances
* Provide SSL termination (HTTPS) for your websites
* Enforce stickiness with cookies
* High availablity across zones
* Separate public traffic from private traffic

## Why to use an ELB? ##

* An Elastic Load Balancer is a managed load balancer
  * AWS guarantees that it will be working
  * AWS takes care of upgrades, maintainance, high availability
  * AWS provides only a few configuration knobs
* It costs less to setup your own load balancer but it will be more effort at your end
* It is integrated with many AWS offerings / services
  * EC2, EC3 Auto Scaling Groups, Amazon ECS
  * AWS Certificate Manager (ACM), CloudWatch
  * Route 53, AWS WAF, AWS Global Accelerator


## Health Checks ##

* Health Checks are crucial for Load Balancers
* They enable the load balancer to know if instances it forwards traffic are available to reply to requests 
* The health check is done on a port and a route (/health is common)
* If the response is not 200 (OK), then the instance will be marked as unhealthy

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_2.png"  width="80%" height="40%">

## Types of Load Balancer on AWS ##

* AWS has 4 kinds of managed Load Balancers
* **Classic Load Balancer** (v1 - old generation) - 2009 - CLB
    * HTTP, HTTPS, TCP, SSL (secure TCP)
  * **Application Load Balancer (ALP)** (v2 - new generation) - 2016 - ALB
    * HTTP, HTTPS, WebSocket
  * **Network Load Balancer (NLB)** (v2 - new generation) - 2017 - NLB
    * TCP, TLS (secure TCP), UDP
  * **Gateway Load Balancer** - 2020 - GWLB
    * Operates at Layer 3 (Network Layer) - IP Protocol
  * Overall, it is recommended to use the newer generation of load balancers as they provide more features
  * Some load balancers can be setup as internal (private) or external (public) ELBs

## Load Balancer Security Groups ##

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_3.png"  width="80%" height="40%">

## Classic Load Balancer (v1) ## - Depricated and not in exam

## Application Load Balancer (v2) ##

* Application load balancers is Layer 7 (HTTP)
* Load Balancing to multiple HTTP applications across machines (target groups)
* Load Balancing to multiple applications on the same machine (ex. containers)
* Support for HTTP/2 and WebSocket
* Support redirects (from HTTP to HTTPS for example)
* Routing tables to different target groups: 
  * Routing based on path in URL (example.com/**users &** example.com/**posts**)
  * Routing based on hostname in URL (**one.example.com** & **other.example.com**)
  * Routing based on Query String, Headers (example.com/**users?id=123&order=false**)
* ALB are great fit for microservices & container-based application (example: Docker & Amazon ECS)
* Has a port mapping feature to redirect to a dynamic port in ECS.
* In comparison, we'd need multiple Classic Load Balancer per application

## HTTP Based Traffic ##
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_4.png"  width="80%" height="40%">

## Target Groups ##

* EC2 instances (can be managed by an Auto Scaling Group) - HTTP 
* ECS tasks (managed by ECS itself) - HTTP 
* Lambda functions - HTTP request is translated into a JSON event
* IP Addresses - must be private IPs
* ALB can route to multiple target groups 
* Health checks are at the target group level

## Query Strings / Parameters Routing ##
<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_5.png"  width="80%" height="40%">

## Good to Know ##

* Fixed hostname (XXX.region.elb.amazonaws.com)
* The application servers don’t see the IP of the client directly
  * The true IP of the client is inserted in the header X-Forwarded-For
  * We can also get Port (X-Forwarded-Port) and proto (X-Forwarded-Proto)

<img src="https://github.com/abhinav-dholi/AWS-Dev-Associate-Preparation/blob/main/Stephane%20Maarek%20Course/Pictures/ELB_6.png"  width="80%" height="40%">


