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
- I created a file called index.html and a file called error.html
- Returned to best practices document
- The best practices document used a Route53 hosted site
- I purchased a domain from amazom (butterno1.com)
- Page 567 of the document shows how to set up a bucket and set a policy using YAML. It also adds a no deletion policy which I do not want. (Creating an Amazon S3 bucket for website hosting and with a DeletionPolicy)
- Page 553 shows the YAML code for setting up a static website but did not include a bucket policy so I needed to add the policy from the previous document to my template (I changed S3Bucket to RootBucket in the code)
- I changed the error file to error.html rather than 404.html as I had created and saved a file called error.html in my manual practice
- My console has defaulted EU-North-1 so I needed to add my region and I had to Google the hosted zone id
- I elected to remove all other regions so I could test with just my region
- I also saved the code to Notepad++ as the template screen to small to see the indentation alignments
- I named my S3HostedStaticWebsite, added the tag Project with a value S3StaticWebsite and added my domain buttersno1.com

    Branch 4a - change website endpoint - Correction 1
- My stack did not work - I received a DNS error - the alias target name does not live within the code
- I asked Chat GPT what I had done wrong as I had edited the zone exactly
- ChatGPT advised that for my region EU-North-1 the website endpoint format was website"."eu NOT website"-"eu
- I deleted the original stack
- I imported the template this time from Notepad++
- I named my S3HostedStaticWebsite, added the tag Project with a value S3StaticWebsite and added my domain buttersno1.com

     Branch 4b - changed hosted zone - Correction 2
- My stack did not work - I received another DNS error
- I asked Chat GPT what I had done wrong now as I was meticulous in the change
- ChatGPT advised that for my hostedzoneid was incorrect
- I located a source document from aws with all websiteendpoint formats and hostedzone ids
- Source: https://docs.aws.amazon.com/general/latest/gr/s3.html
- I named my S3HostedStaticWebsite, added the tag Project with a value S3StaticWebsite and added my domain buttersno1.com
- The stack worked correctly: it created two s3 Buckets and a website url
- I clicked on the website URL and received a 404 error -> This was a success as it had created a static website but I did not have any content at this point
- I then added my index.html and error.html files to my root bucket
- When I refreshed the browser I could read the index.html content
- I tested buttersno.1.com and I saw the contents of index.html again
- However when I tested www.buttersno1.com - I received an AccessDenied error

     Branch 4c - changed myDNS settings for WWWBucket  - Correction 3
- I asked Chat GPT what could possibly be wrong with my setup as I had followed the tutorial and validated the code each time
- Chat GPT told me to look at my Route53 settings
- Everything was correct under record names - including www.buttersno1.com
- The type was CNAME and the TTL was 900 as configured in my code
- Still lost - I told Chat GPT I couldn't see anything obvious as type and TTL for my two buckets matched in Route 53 and in my code
- Chat GPT then said the DNS setting should point to the s3 website endpoint
- I know Ruth had said that tutorials could have errors but I needed to see and understand before making a change
- In the AWS document for manual configuration both the Record Sets, for the Root and the Sub, should point to the S3 website which is Type A, and no TTL setting is needed
- Source: https://docs.aws.amazon.com/AmazonS3/latest/userguide/website-hosting-custom-domain-walkthrough.html#root-domain-walkthrough-add-record-to-hostedzone 
   Step 11: Add an alias for your root domain and subdomain
- I changed the code in my YAML file to match the type and alias target of the sub domain to the root domain
- I removed the TTL and the Resource Reocrds lines per the tutorial
- As my Stack was working, I used a change set to make a change to the template code
- I uploaded the YAML and checked the change
- I proceeded with the update and waited for the changes to complete
- I tested the domain and the url again and they were still working
- When I tested wwww.butterno1.com it was blocked by my administrator but when I tested on my phone I could see the index.html content
- I asked another person to do the same. It was blocked as they were on their work laptop but they could see the index.html content on their phone
  

  
  
