## AWS Clouding Computing for Beginners

Shoutout to Unfold Data Science. [Video](https://www.youtube.com/watch?v=0SYV7o_fd50&list=PLmPJQXJiMoUWFW2JxRSAfhcsQ0Cr9qbv-) for reference

# What is cloud computing?
Why do we need cloud computing? 
* Scalability (back end and server)
* Secure
* Flexibility (migrate data, add pages)
* Reliable (accessible in different countries)

Cloud computing lets you focus on your speciality and expertise and AWS will take care of the above issues. It takes care of IT side of business while you take care of product side of business. 

Cloud service provider (CSP) is an organization or entity that provides Cloud Computing services. Includes AWS, GCP (Google), and Azure; these take up 70% of the market, AWS is 33% of global market capture. 

What does taking care of IT mean?
It takes care of normal IT infrastructure, but it also makes it 'smart'; allows you to have low latency on frequently accessed files
Say you have two different files:
* Daily workout schedule: you open 30 times a month. You want low latency on this file, so that it opens fast (more expensive files)
* Monthly expense calculator: you open 1 time a month, so you don't need to open it fast, and you coulf afford high latency (less expensive files)

Everything that happens on their platform is called cloud-computing. 

# 3 different kinds of services from cloud computing

These services take into consideration these factors:
1. Application: where content is hosted
2. Data: user data, addition of users, file formats
3. Runtime: when app runs, it should run quickly where front-end users are not facing any issues
4. Middleware: is it calling to an API? Or communicating with backend? 
5. O/S: what operating system is it running on? 
6. Virtualization: not always needed, but is it running on VM (virtual servers?)
7. Servers: what servers are being used?
8. Storage
9. Network

Some of these factors will not be applicable with all 3 services

The 3 services:
1. IAAS: infrastructure as a service. This is 1 through 5 above in cloud. Least use of cloud, the business manages most of IT. Just infrastructure provided by CPS. Want to keep data to themselves and keep the control to themselves. (CRM, invoicing)
2. PAAS: platform as a service. 3 through 9 in cloud. Like if you're a developer and want to host your app on a platform. You manage code, data. (Heroku)
3. SAAS: software as a service. Everything managed through CSP, you just use their software as an end user. You're just using the frontend. (Dropbox, Microsoft 365, Cisco Webex)

***Potential interview question***: 
If someone is running a website by themselves, what are they responsible for? All 9 of the factors listed above
If they decide once their business grows to use cloud computing for at least part of their IT (say, 1 through 5 above), but they want help on the 6 through 9, they can get CSP to help. This is IAAS

# Public and private cloud

There are public clouds, private clouds, and hybrid clouds.

If you're hosting just like classes online that don't use a lot of sensitive information and don't care about data security, you could use public cloud to host it. It's cheaper. CPS is allowing you to host in a public space where somebody else can host their application. Many customers can use the application. There's still security, but not as intensive. Owner is the CPS. More scalable and flexible

But if you're a bank, it's very sensitive, so you'd need the private cloud. The company is the owner of the cloud

Most organizations will be a mix of both, so the hybrid cloud. Owner is the company itself. More rigid and less flexibile, more regulations

# Now we go to AWS Console

They provide a lot of services. If you go to the services pane you can see everything, like storage > AWS backup. There are different service levels, like all the options under Storage, which cater to different businesses

Go to Storage > S3. This is a simple storage service in cloud. there are 2 concepts used in S3:
1. Bucket: common repository. you can have multiple objects. You can have mulitple different object types in a bucket
2. Object: like an actual file within the bucket (video, text). You cannot store a file in AWS without creating a bucket

In AWS console, click Create Bucket. Name bucket and in this case, block all public access for now. Then create bucket. Now you can go to the bucket and upload a file. 

In the bucket, if you select the uploaded file, there's an option called Copy S3 URI, which stands for Uniform Resource Identifier. You can also copy the public URL, but you can't access it if public access is blocked. You can go to your bucket and click permissions to make it publicly accessible.

You'll also have to edit the bucket policy to make it accessible in open internet. You update the policy using a JSON file, but you can use the policy generator option to make it easier
1. Select S3 bucket policy type
2. Effect = Allow
3. Principal = *
4. Actions = All Actions (can be dangerous, because this can give the public permissions to delete the bucket, update the bucket, etc.)
5. Amazon Resource Name (ARN) = already generated. Go back to the Edit Bucket Policy Page and it will be there for you to copy and paste in
6. Click Add statement, then Generate Policy. Copy the command and paste into the Edit Policy page
7. Click Save Changes

Now you can refresh, but the public access is given only to the *bucket*, not the objects. You can go into the bucket policy and edit the JSON to add "/*" to the end of the "Resource" variable so that the objects within the bucket are accessible. 

Now you can access the object publicly
