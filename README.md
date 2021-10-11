# Take-Home-Assignment

Based on the requirements below are my assumptions:
--------------------------------------------------
Requirement Breakdown:
---------------------
 - Infrastructure that implements the architecture 
    1. Users VPC
    2. Provides access to Infrastructure that users will interact
 - FSX fileshare VPC - (infrastructure VPC)
    1. Infrastructure that supports files sharin
    2. Users need not have access to all of the infrastructure
    3. Can provide some access to modify (read/write) objects
    4. Add Route 53 resolvers in VPC Users and Production Support
 - Production Support VPC
    1. Needs complete monitoring from all infrastructure that Users interact
        a. Cloud watch
        b. VPC flow logs
        c. Cloud trail events from all other VPCs
        d. Users will not need access to this VPC - (role based access)
 - Automation to support Business use case - CI/CD
    1. Provide a way to spin up EC2 instances in target VPC
      a. Automation that connects to file shares as the instances come up
      b. Think about options to add file shares as an option (advanced usecase)
    2. Setup IAM for specific users to perform specific tasks

 - Roles 
    1. DevOps engineer/Infrastructure Engineer
    2. User - Has ability to make some changes  to infrastructure but limited. Main usecase to deploy code/spin up EC2 instances
    3. Production support Role - access to VPC with Monitoring


  Pipelines

 - Infrastructure workflow - Pipeline
     1. Pipeline that create the above mentioned arechitecture.
 - Deployment -pipelines
    1. Pre-Req - minimum -  File share VPC is setup and accessible to any EC2 instance created 
    2. Goal:When an EC2 instance is deployed > instance with network drive comes up
        Idea: First create instance > get Instance id > send the instance ID to mount creation automation > create a mount share directory with instance id >                     attach the instance mount to instance
    3. Unit test.
