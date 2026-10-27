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
  
