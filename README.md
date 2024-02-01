# AWS-ASG
The following is a guide on creating an Amazon Web Services Automatic Scaling Group (ASG), a supplemental service to load balancers. Compared to load balancers which only balance incoming traffic to various instances, ASGs utilize the best aspects of cloud: scaling and elasticity.

ASGs can be setup to scale automatically based off many factors and needs. One example could be to automatically increase the number of instances used based on historical network data. For example sales during special events or holidays such as Black Friday, Cyber Monday or Christmas can result in more clients visiting webservers and higher applications usage. In such a case, instances could be added just before these seasonal events. Another example would be to automatically increase/decrease gaming server capacity based off current network usage.

Here's how I setup an ASG on AWS:

1. First, I'm going to delete (terminate) my instances from the previous demo on load balancers.

<p align="center">
 <img src="https://i.imgur.com/9sUQsBW.png">
</p>

2. Next, I'll create an Automatic Scaling Group

<p align="center">
 <img src="https://i.imgur.com/M4V8SwI.png">
</p>

3. Configuring:

I add an ASG name, and below I will create a launch template.

<p align="center">
 <img src="https://i.imgur.com/NaB8kvW.png">
</p>

As usual, if you're copying these steps, when making a new template or policy, you have to refresh before selecting your newly established setup. 

<p align="center">
 <img src="https://i.imgur.com/szVj90T.png">
</p>

Here, I select all available Availability Zones (AZ).

<p align="center">
 <img src="https://i.imgur.com/5uMA8BP.png">
</p>

Since I have a load balancer setup from before I'll attach to an esisting load balancer. If you'd like to see how to set one up, follow [my previous guide](https://github.com/hann-cyber/AWS-LoadBalancer)

<p align="center">
 <img src="https://i.imgur.com/xryZc29.png">
</p>

Once it's setup, you can see the ASG setting up its resources, up to my specified capacity of 2 instances.

<p align="center">
 <img src="https://i.imgur.com/RLZJX2f.png">
</p>

In the instance activity you can see 2 successful instance launches.

<p align="center">
 <img src="https://i.imgur.com/Csl6yZh.png">
</p>

If I visit my public load balancer name and refresh multiple times we can see the 2 different instance IPs, just as before, while only exposing the load balancer to the public.

<p align="center">
 <img src="https://i.imgur.com/tA4sYYT.png">
</p>

<p align="center">
 <img src="https://i.imgur.com/PsW5xag.png">
</p>

The benfit to an ASG though, is that it will automatically scale based on demands. For example, I'll terminate one of my instances to illustrate a failed instances.

<p align="center">
 <img src="https://i.imgur.com/QRYW4i0.png">
</p>

The following image illustrates the terminated instance being replaces automatically within the activity history.

<p align="center">
 <img src="https://i.imgur.com/IgMZhgU.png">
</p>

