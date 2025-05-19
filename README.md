<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Host a Website on Amazon S3

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-host-a-website-on-s3)

**Author:** Jeffrey Osamor  
**Email:** jeffreyosamor93@gmail.com

---

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Introducing Today's Project!

In this project, I will demonstrate how we'll be creating an S3 bucket to store pictures and files needed in your very own website. I'm doing this project to learn Amazon s3 function.

### Tools and concepts

Services I used were Amazon S3 (Simple Storage Service)... Key concepts I learnt include:
•	Buckets – Containers for storing data.
•	Objects – Files like index.html stored inside buckets.
•	Static Website Hosting – Used S3 to serve a website 
    directly to the web.
•	Permissions & Security – Controlled access with:
	•	Bucket policies
	•	Object-level permissions
	•	Public access settings

### Project reflection

This project took me approximately 6 min to complete this project... The most challenging part was understaning the function of creating bucket ploicy... It was most rewarding to how the Amazon S3 (Simple Storage Service) work and the functions...

---

## How I Set Up an S3 Bucket

Creating an S3 bucket took me less than 3min

The Region I picked for my S3 bucket was United States (North Virginia). because it is the closest region to the country am in...

S3 bucket names are globally unique! This means that no two S3 buckets across all AWS accounts and regions worldwide can have the same name....

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_ba6d42ad)

---

## Upload Website Files to S3

### index.html and image assets

I uploaded two files to my S3 bucket - they were HTML file and Zip file containing the website content...

Both files are necessary for this project as they help with our website content.

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_a265af88)

---

## Static Website Hosting on S3

Website hosting means what makes your website public on the internet.

To enable website hosting on my S3 bucket, Step-by-Step:
	1.	Go to the S3 console
→ https://s3.console.aws.amazon.com/s3/
	2.	Click your bucket name
Example: nextwork-website-project-jeffrey-osamor
	3.	Go to the “Properties” tab
	4.	Scroll down to “Static website hosting” section
	5.	Click “Edit”
	6.	Choose “Enable”
	7.	Under Hosting type, choose:
    ✅ “Host a static website”
	8.	Specify the index document: index.html
9.	Click “Save changes”

An ACL is a set of rules that decides who can get access to a resource. I did enable the ACLs Object Ownership

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_c22c54c0)

---

## Bucket Endpoints

Once static website is enabled, S3 produces a bucket endpoint URL, which is a bucket website endpoint just like a regular website URL. It lets people visit your S3 bucket's files as a website.

When I first visited the bucket endpoint URL, I saw 403 Forbidden: Access Denied. The reason for this error was  telling me that my static website is being hosted by S3, but the actual HTML/image files i've uploaded are still private...

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_22ce4daf)

---

## Success!

To resolve this 403 Forbidden error, by providing the bucket policy which is written in JSON format.

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_5d4474f9)

---

## Bucket Policies

An alternative to ACLs are bucket policies, which are a type of access control policy used in services like Amazon S3. It defines who or what can access the resources (buckets and objects) within a bucket and what actions they are allowed to perform.... The benefit of using bucket policies is it operate at the bucket level, allowing you to define access permissions for entire buckets and control who can perform specific actions on objects within them.... while ACLs are useful for when you need to control access on a per-object basis...

My bucket policy does, It blocks deletion of the index.html file by anyone, including: IAM users, Root users (unless they have an explicit allow and no other deny), AWS services and even your own CLI/SDK actions if the request matches this policy... I tested this by Replace <object-name> with the name of your HTML file i.e. index.html... and Notice that your index.html file is listed in the Failed to delete panel at the bottom of the page...

![Image](http://learn.nextwork.org/excited_olive_swift_blue_tang/uploads/aws-host-a-website-on-s3_sm2sm2sm)

---

---
