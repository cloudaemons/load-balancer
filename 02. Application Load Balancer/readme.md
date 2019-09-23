# APPLICATION LOAD BALANCER SETUP

## DEFINITIONS
----

### Load balancer

A load balancer serves as the single point of contact for clients. The load balancer distributes incoming application traffic across multiple targets, such as EC2 instances, in multiple Availability Zones. This increases the availability of your application.

## STEPS
---

1. CREATE APPLICATION LOAD BALANCER


* Navigate to **EC2**.
* Select **Load Balancers** in the left-hand menu.
* Click **Create Load Balancer**.
* Choose **Application Load Balancer** , then click **Create**.
* Give the name for your balancer **ALB**
* Leave the settings in the Listeners section as-is.
* In the Availability Zones section, select the your VPC
* Select both **Availability Zones** and public subnets created by you ealier 
* Click **Next: Configure Security Settings**.
* Click **Next: Configure Security Groups.**
* Select the security group whose name is **mySgWeb**.
* Click **Next: Configure Routing.**
* Set as **Target group** **New target group**
* Set name to **myTargetGroup**
* As a target type set **Instance**
* Set protocol to **HTTP**
* Set Port to **80**
* Click **Next: Register Targets**
* Select instances created previously in this lab
* Click **Add to registered**
* Click Next: Review.
* Click Create.


2. TEST

* Navigate to **EC2**.
* Select **Load Balancers** in the left-hand menu.
* Select your load balancer
* Find the **DNS name** of your load balancer
* Copy it and open in a web browser
* Refresh the page several times. you should see that web page is sent from different load balancers

## END OF LAB