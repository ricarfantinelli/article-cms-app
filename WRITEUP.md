# Write-up Template

### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

VM
---
  Costs: it's more expensive than App Service, however if your application doesn't run 24/7 it may be a good option, as you can pay   
         only for what you utilize.
  Scalability: you can scale out to a hundreds of instances.
  Availability: virtual machine scale sets and load balancers.
  WorkFlow:
  
App Service:   
------------
  Costs: the cost varies depends on the plan you choose. There are three tiers: Dev/Test (free), Production and Isolated.
         As the application is just a test I can use the free option. You pay for the server even if the application isn't running.
  Scalability:  autoscalling is a built-in service in App Service. Can scale horizontaly or vertically.
  Availability: 
  WorkFlow:
  
  
I've chosen App Service as it is easier to deploy a simple web app. App Service handles the whole deployment for the developer. 
  For this particular project I don't need a high performance compute, so I chose Dev/Test tier, which is free and meet my needs.
  So, no need to spend a lot of time setting up a VM for it.
  

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 

In case I'd developed a webapp for a huge number of users and had to deploy it to production, 
  with peaks in particular timeframes each day, I'd choose VM instead of App Service.