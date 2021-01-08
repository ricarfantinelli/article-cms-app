# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

VM
---
  Costs: it's more expensive than App Service depending on your use, though if your application doesn't run 24/7 it may be a good option, 
         as you can pay only for what you use. 
  Scalability: you can scale out to a hundreds of instances. You should use Virtual Machine scale set for auto scaling.
  Availability: To improve availability you can use: availability zones, availability sets, virtual machine scale sets (which track VMs
                across Availability zones and can scale out up to 1,000 VM instances) and load balancers.
				SLA for VMs can vary from 95% to 99.99% (two or more instances across two or more Availability Zones).
  WorkFlow: deploying VM, copy the project to the VM, installing python virtual environment and NGNIX. Setup NGNIX to redirect 
            all connections from port 80 to the web app, creating and activating virtual environment, 
			installing all requirements.txt in the virtual environment. Run the application.
  
  
App Service:   
------------
  Costs: the cost vary depending on the plan you choose. There are three tiers: Dev/Test (free), Production and Isolated.
         You pay for the server even if the application isn't running.
		 As this application is just a testing/small app I decided to used the free option.
  Scalability:  autoscalling is a built-in service in App Service for subscriptions Standard, Premium and Isolated. 
                Can scale up or scale out. Max 30 instances, depending on pricing tier and for Isolated you can scale-out up to 100 instances.
  Availability: the SLA for availability is 99.95% for all types of scriptions expect for Free and Shared.
                In order to increase availability it can be used Availability zones.
  WorkFlow: push the code of application to github. Creating App Service on Azure Portal. Go to Development Center and go to Git Hub Actions,
            pick the repository, branch and environment and then the deployment is done by Git Hub Actions. 
			Run the application after it's done.
  

Justification:  
--------------
I've chosen App Service as it is easier to deploy a simple web app and the app is small, which fits into App Service Free tier (F1). 
App Service handles the whole deployment for the developer. 
For this particular project I didn't need a high performance compute, so I chose Dev/Test tier, which is free and meet my needs.
So, no need to spend a lot of time setting up a VM for it.
  

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

In case I'd developed a webapp for a huge number of users and had to deploy it to production, 
  with peaks of use in particular timeframes on a daily basis, I'd choose VM over App Service.
  VM could give me more control over the underlying resources (SOs for instance), decrease my monthly costs by deallocating VMs when 
  they're not used and have the ability to scale out up to 1,000 instances, in case my app was huge, which is not possible 
  with App Service (maximium 100 instances in Isolated).
  