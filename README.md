# L00205876_CloudFormation
DevOps Pipeline CloudFormation Lab 1

Reviewed CloudFormation Lab
- Downloaded aws User Guide AWS CloudFormation - API Version 2010-05-15
- Watched Ruth's video for guidance
- Confirmed understanding with ChatGPT
- Invited Ruth as a collaborator

Practiced Cloud Formations Module Creating a stack
- Created a Stack - MyTestStack
- Checked that it would run
- Found my public ip address on https://www.whatismyip.com/
- Realised T2.micro does not work with my tier and removed it from code to complete practice
- Discussed best way to document in GitHub with ChatGPT (did not ask for any code)

Branch 1 - Code of Conduct
- Added Code of Conduct and Merged back to Main
- Source: https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-code-of-conduct-to-your-project
- Variance - added to branch rather than directly to main

Branch 2 - Website_L00205786_Sandy-Gallagher
- Using the AWs Guide referenced above I created a Build Template in AWS and Created a Stack
- I only used T3.Micro as my allowable source
- Per the assignment requirements I changed the html code so the Header read "L00205876 Sandy Gallagher"
- I also added the line "This is my website for my CloudFormations Lab"
- I also verified my public ip address again on https://www.whatismyip.com/. It was unchanged but I will need to verify this going forward.
- Initially it did not work and I created a Troubleshoot build template. I thought a may have cut some code off when copying from the pdf
- My initial stack was actually fine - I just needed to wait for the EC2 instance to pass it's checks
- Note for future trouble shooting: if running from the stack outputs tab fails - check the status of the EC2 Instance

 Branch 3 - Modify Linux Version to Linux 2023
- I received an email alert advising Linux 2 support had been discontinued
- Modified the original code to use Linux 2023 as documented on p. 237 of tutorial doc
- Named the stack "Website-L00205876-Sandy-Gallagher"
- Added my ip address from https://www.whatismyip.com/
- Added the tag "website"
- Waited for stack to complete and tested websit
- Test was a success

  Branch 4 - Change to S3 Static Website
- Realised I needed to Host my Website using an S3 Bucket
- Refreshed my memory using a manual build: https://docs.aws.amazon.com/AmazonS3/latest/userguide/HostingWebsiteOnS3Setup.html
- Returned to best practices document
- The best practices document used a Route53 hosted site
- I purchased a domain from amazom (butterno1.com)
- Page 567 of the document shows how to set up a bucket and set a policy using YAML. It also adds a no deletion policy which I do not want. (Creating an Amazon S3 bucket for website hosting and with a DeletionPolicy)
- Page 553 shows the YAML code for setting up a static website but did not include a bucket policy so I needed to add the policy from the previous document to my template (I changed S3Bucket to RootBucket in the code)
- My console has defaulted EU-North-1 so I needed to add my region and I had to Google the hosted zone id
- I elected to remove all other regions so I could test with just my region
- I also saved the code to Notepad++ as the template screen to small to see the indentation alignments
- I named my S3HostedStaticWebsite, added the tag Project with a value S3StaticWebsite and added my domain buttersno1.com

   Branch 4a
- My stack did not work - I received a DNS error - the alias target name does not live within the code
- I asked Chat GPT what I had done wrong as I had edited the zone exactly
- ChatGPT advised that for my region EU-North-1 the website endpoint format was website"."eu NOT website"-"eu
- I deleted the original stack
- I imported the template this time from Notepad++
- I named my S3HostedStaticWebsite, added the tag Project with a value S3StaticWebsite and added my domain buttersno1.com

  
  
