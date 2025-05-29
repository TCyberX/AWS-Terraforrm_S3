<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Create S3 Buckets with Terraform

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-terraform1)

**Author:** Albert  
**Email:** tapcyberx@gmail.com

---

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use Terraform to launch an S3 bucket.
The goal is to walk through the full process from installing and configuring Terraform, to troubleshooting setup issues (like CLI installation errors), and finally, to successfully applying a Terraform configuration that provisions an S3 bucket on AWS.

This project highlights the power of Infrastructure as Code (IaC) and how tools like Terraform can help automate and streamline cloud resource deployment.

### Tools and concepts

Services I used were Amazon S3, AWS IAM, Terraform and AWS CLI.
Key concepts I learnt include infrastructure as code creating configuration file , modularity of code, using providers, plugins, state files, lock files (Terraform).



### Project reflection

This project took me approximately 3H between taking my notes and studies those concepts. The most challenging part was customizing Terraform. It was most rewarding to see how you can work in your local computer and automatically set up everything with touch your AWS Console.

I did this project because I’m genuinely interested in gaining hands-on experience with Terraform and learning how to automate infrastructure using code.

The project completely met my goals, I was able to deploy resources using Terraform, interact with AWS services through the CLI, and manage everything directly from my local terminal. It was a great opportunity to strengthen both my IaC and AWS skills in a real-world setup.

---

## Introducing Terraform

Terraform is an Infrastructure as Code (IaC) tool used to manage cloud and IT resources through declarative configuration files. These files define the desired state of your infrastructure such as services, networks, or storage.

Terraform can then create, update, or delete resources automatically to match that state. This makes it incredibly useful for automation, consistency, and repeatability across environments.

Terraform is one of the most popular tools for Infrastructure as Code (IaC) a method of managing IT infrastructure using code instead of manual steps.

Rather than setting up resources manually through the AWS Console or CLI, IaC automates the entire process, ensuring consistency, repeatability, and easier version control. 

Terraform allows you to define your infrastructure in code, making deployments faster, more reliable, and easier to manage at scale.

Terraform uses configuration files to understand the desired state of the infrastructure. ( main.tf ) is the main configuration file that I use in Terraform to describe tha the desired state.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_9i0j1k2l)

---

## Configuration files

The configuration is structured in separate blocks instead of one large block to support modularity. This approach allows you to organize and update different parts of the main.tf file independently such as providers, resources, and variables without impacting unrelated sections.

It also makes collaboration easier, especially for teams, since multiple people can work on different parts of the configuration at the same time with better clarity and fewer conflicts.

### My main.tf configuration has three blocks

The first block indicates that I'm using AWS as a provider for the infrastructure. The second block provisions an Amazon S3 bucket and gives it a unique name. The third block manages the bucket's permission.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_ljvh9876)

---

## Customizing my S3 Bucket

For my project extension, I visited the official Terraform documentation to explore how I could customize my S3 bucket configuration further.

The documentation provides detailed examples, a list of available parameters for each resource, and clear usage rules. It’s a valuable resource for understanding how to fine-tune infrastructure and follow best practices when writing Terraform code.

I chose to customize my bucket by adding tags, which helps with resource identification and organization. Tagging allows me to clearly label the bucket based on the project or purpose it was created for making it easier to manage later on.

After launching the bucket, I verified my customization by checking the Tags panel in the S3 console, where the tag I defined appeared as expected.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_ffe757cd3)

---

## Terraform commands

I ran 'terraform init' to initialize Terraform. This means getting it set up the backend to store state files and install the necessary plugins (AWS provider).



Next, I ran terraform plan to have Terraform compare the desired infrastructure defined in the main.tf file against the current state of the existing infrastructure.

This step generates an execution plan, showing what actions Terraform will take such as creating, updating, or destroying resources so I can review and confirm the changes before applying them.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_3g4h5i6j)

---

## AWS CLI and Access Keys

When I tried to run terraform plan, I encountered an error message stating that no valid credentials file was found.

This happened because my local terminal wasn’t yet configured with AWS credentials which are required for Terraform to authenticate and use the AWS provider plugin. To fix this, I needed to properly set up my AWS access credentials so Terraform could interact with my cloud environment.


To resolve the error, I first installed the AWS CLI, which is a command-line tool that allows you to interact with your AWS environment using text-based commands.

Instead of navigating through the AWS Management Console, the CLI provides a faster and more scriptable way to manage services perfect for configuring credentials and automating workflows like Terraform deployments in this case in my local computer.

I set up AWS access keys to enable CLI access to my AWS account from my local machine. Using the aws configure command, I entered my Access Key ID and Secret Access Key, which securely authenticated my terminal session.

Once configured, my local terminal had the credentials needed for Terraform to interact with AWS resources allowing me to proceed with planning and applying my infrastructure changes.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_7j8k9l0m)

---

## Lanching the S3 Bucket

In this step, I ran terraform apply to execute the changes that were outlined during the terraform plan phase.

Running this command directly affects my AWS account by provisioning the resources defined in the configuration. In this case, Terraform created two resources: an S3 bucket and its corresponding permission settings (bucket policy) bringing my desired infrastructure state to life.



The sequence of running terraform init, plan, and apply is crucial because I need to initialize terraform first before I get to make any comparisons between main.tf and my current infrastructure, or connect to AWS in the first place.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_1q2w3e4r)

---

## Uploading an S3 Object

I created a new resource block to upload an image called image.png into the S3 bucket.
The image will upload straight away without being nested in a subfolder in the S3 bucket.



We need to run terraform apply again because I updated the Terraform configuration file, which means there are changes that Terraform needs to reviews and compare with my infrastructure again. This time only one new resource is created (image).



To validate that I've updated my configuration successfully, I checked the S3 bucket and confirmed that a new image is inside . I also downloaded the image back to us, and confirmed that it was the correct image that was initially uploaded.



![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/aws-devops-terraform1_9o0p1a2s)

---

---
