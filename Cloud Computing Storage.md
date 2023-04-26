## Cloud Computing Storage

[Video](https://www.youtube.com/watch?v=4Qd2pThNTtY&list=PLmPJQXJiMoUWFW2JxRSAfhcsQ0Cr9qbv-&index=2) 

### Why are there different storage types?

Say you have file1 you open daily, and file2 you want to open monthly. file1 will need low latency and more performance oriented, but on file 2 doesn't matter as much and you can compromise on cost for higher latency. AWS offers different storage options related to this. 

In the AWS console, do a search for AWS Budgets. Make a budget to make sure you're not spending more than $0 in AWS. 

Click Create Budget. Use Simplified Template, and select Zero Spend Budget. Create a budget name. Add a email address for email alerts. Click Create Budget to finish  

### EBS, EFS, and S3

Click Services and go to Storage to check these 3 things out

1. EBS: Elastic Block Storage. Say you want to use an Amazon computer from AWS to process your ML engine or an application, or anything you want to put on this server to process it. You initialize something called an EC2 instance, which is a machine that Amazon rents to you to do your work essentially. There will be a disk and memory associated with any computer you "rent". The memory that get associated with that EC2 instance is called EBS volume. Cost depends on what kind of storage service you're using
2. EFS: Elastic File System. This is a common shared hard/network drive You use this if you want storage that can be used by multiple people, computers, servers in the network. You're asking Amazon for like 100GB for the multiple entities to access. Higher cost
3. S3: common repository for static files, where you can store whatever you want. Cheaper

### S3: Versioning, Intelligent Tier Archive Config, Bucket Policy, Lifecycle Rule, Replication rule


Versioning - 
Go to Amazon Console and go to Services > S3. You'll end back where you made a bucket.

Click on a bucket and go to Properties of the bucket. There's a section for versioning, which keeps multiple variants of your object in the same bucket. We only uploaded one object, and versioning will help you have multiple versions of the one object. If you go back to the bucket and click the object, there's a versions tab. By default, versioning is disabled, so you'll want to enable that within the bucket itself. Go back to bucket, click properties, and go to edit bucket versioning. Select enable and save changes. Now you can go back to the bucket and upload the same file again. Go to the object and click versions to see the new version information. *Very important to enable versioning*

Intelligent Tier Archive Config - 
You use this if you're storing some object and you want to access it very fast, or in the main drive, or maybe less frequently, etc. 

Go to bucket > properties and scroll to Intelligent Tier Archive Config. Click Create Config. Create name, select "applies to all objects in this bucket". There's an option called Archive Access Tier that will archive things that haven't been access in 90 days (or you can edit the number of days). Good to select that. You could also use Deep Tier Archiving, for longer days unaccessed, which has a lower cost for storage. Click Create. So this will save costs on files that aren't accessed frequently. 

Bucket Policy -
Determines access to the bucket. 

Life Cycle Rule-
Defines actions you want the S3 to take during an object's lifetime, like transitioning to another archive class or evetually deleting them. Unlike Intelligent Tier, it moves to a different storage class altogether, like S3 Glacier (archive storage). Sounds like this is also determined by when the objects were last accessed. 

Go to bucket > management. Create lifecycle rule. Add name and apply to all objects in the bucket. Select all the actions you want (move current version). For Choose storage class transitions, you can choose something like Standard-IA, and set days after object creationt to 40; click add transition. Then you could add intelligent tiering after 90 days, and glacier deep archive after 300 days. There is a cost associated with glacier storage, and there's a note about it. Click create rule.

*This is different from Intelligent Tier* because we are moving between storage classes, while with intelligent you're in S3 only.  

Replication Rules - 
copies content from one bucket to another bucket. 

Create another bucket real quick for the example. Go to original bucket > management to find replication rules, and create new replication rule. Name rule. For source bucket section, click apply to all objects in the bucket. For destination section, you can click browse S3 to look for the bucket you want to replicate into. May have a message to enable versioning in bucket. Keep choose from existing IAM role selected, and pick Create new role from the dropdown. Click create rule. Click replicate existing objects. For completion report section, need to add the path of the destination bucket. Make take some time to replicate
