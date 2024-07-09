#data-engineering 

## Overview

- Infrastructure as Code
- CloudFormation concepts
- CloudFormation Syntax and Features
- Deploying CloudFormation to AWS
- Troubleshooting CloudFormation
- Exercise

## Learning Objectives

- Explain why Infrastructure as Code is important
- Identify the parts of a CloudFormation Template
- Be able to write and deploy CloudFormation Templates to AWS

---

## Infrastructure as Code (IaC)

> Question: What is Infrastructure as Code?

Notes: IaC may already have been covered as a concept in the DevOps module.

If this was the case, ask the learners if they remember anything about IaC.

Learners may mention:

- The management of infrastructure
- Generates the exact same environment every time through a code file
- Used in conjunction with CI/CD pipeline
- Without IaC, teams must maintain the settings of all environments individually


## What is Infrastructure as Code?

- The management of _infrastructure_ through version-controlled files
- Generates the exact same environment every time through a code file
- Used in conjunction with CI/CD pipeline
- Without IaC, teams must maintain the settings of all environments individually

## What is "Infrastructure"?

In a traditional non-cloud context:

- Application Servers
- Virtual Machines
- Databases
- Firewalls
- etc

In an AWS cloud context, "Infrastructure" could be any component of any AWS service:

- S3 Buckets
- Lambda Functions
- EC2 compute instances
- Users
- Roles
- ... and much more

👉 Almost anything you can create through the AWS web console can be considered "infrastructure"!

### Infrastructure as Code

Infrastructure as Code is an engineering principle in which we define **templates** for our **application and service infrastructure** to allow it to be created, deleted, re-created, or duplicated **consistently and predictably**

👉 There are many different IaC tools and technologies in the engineering world, but the goal and principle of IaC is always the same

Notes: IaC lets us take a template that contains everything we need for our application, and deploy multiple instances of that application side-by-side.

We don't build our application infrastructure directly, instead we build a template which can then create that infrastructure for us when deployed.

### Infrastructure from Templates


- One template can be deployed any number of times
- Deployed instances can be updated by modifying and re-deploying the template

Notes: It may be useful to use the docker analogy with the learners; the same docker image can be used to create many docker containers that run the same software in the same way.

### Without Infrastructure as Code

- Each new deployment requires lots of human work to provision 😩
- There may be mistakes that aren't noticed and cause problems 😵
- The instructions to build an application can be lost or forgotten! 😱

### With Infrastructure as Code

- Any number of deployments created automatically with little work 😃
- Every deployment is identical, since it came from the same template 🤩
- The template is in source-control, so it can never be lost! 🎉

### Infrastructure as Code Summary

- IaC makes deployments predictable and repeatable
- IaC makes collaborating with other people in your team on infrastructure easy
- You should **always** use IaC when building cloud apps and services

---

### AWS CloudFormation

- CloudFormation is an IaC tool designed by AWS for use within AWS
- It natively understands and works with (almost!) all AWS infrastructure and services
- CloudFormation runs as a service within AWS, which can orchestrate our deployments
- It is an industry-standard and popular choice for AWS development

### CloudFormation Key Concepts

- **Template** - A 'blueprint' for our infrastructure
- **Stack** - A deployed instance of a template
- **Resources** - Infrastructure components created inside a stack

### A CloudFormation Template

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: Template for a single S3 bucket

Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: academy-de-example-bucket
```

The above template creates a S3 Bucket `resource` called 'academy-de-example-bucket'

```yaml
AWSTemplateFormatVersion: "2010-09-09" # <-- Version
Description: My S3 bucket # <-- Description
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: academy-de-example-bucket
```

- **Version** (Optional)
    - Always "2010-09-09" (only one version exists 🤷‍♀️)
- **Description** (Optional)
    - Human-readable description of what this template is for

### CloudFormation Anatomy (2)

```yml
AWSTemplateFormatVersion: "2010-09-09"
Description: Template for a single S3 bucket

Resources: # <-= Resources
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: academy-de-example-bucket
```

**Resources** (Required)

- The set of infrastructure to be created by this template
	- Could be S3 buckets, EC2 instances, roles, lambda functions, or any other supported AWS resource

### CloudFormation Anatomy (3)

```yml
AWSTemplateFormatVersion: "2010-09-09"
Description: Template for a single S3 bucket

Resources:
  MyS3Bucket: # <-- Resource Name
    Type: AWS::S3::Bucket # <-- Resource Type
    Properties:
      BucketName: academy-de-example-bucket
```

#### Resource Name

- A label for this resource
- Can be anything, as long as it is unique within the template

#### Resource Type

- The type of infrastructure this resource represents
- Comes from a fixed list of possible resource types

### CloudFormation Anatomy (4)

```yml
AWSTemplateFormatVersion: "2010-09-09"
Description: Template for a single S3 bucket

Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-bucket-name # <-- Resource Properties
```

#### Resource Properties

- Configuration for this type of resource
- Possible properties for a resource type can be found in the documentation
- Some properties are required, while others are optional

Notes: Possible resource properties for an S3 bucket as example may include things like the name (specified here and required) plus optional properties such as:

- Whether encryption is applied on the bucket
- Public or Private access to bucket files
- Use of the bucket to host a website

### Points of Note

- Templates are YAML documents
- In YAML 👉 indentation is important 👈 (Just like in Python!)
- All possible AWS resource types and their possible properties can be found in the [AWS docs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)

### Deploying a Template

We have a Template that defines our Resources.

How do we turn that template into a stack in AWS?

There are two main options:

1. Deploy via AWS Web Console
2. Deploy via the AWS Command Line Interface (CLI)

### Console Deployment

A stack can be created by uploading a template file via the Web interface, by going to:

- AWS Web Console
    - CloudFormation -> Stacks -> Create Stack

While a stack is deploying, the web console can be used to see what is happening.

The web console can also be used to check what resources have been created.

Notes: Use the web console to demonstrate template deployment of the S3 bucket for the learners. You may need to change the bucket name!

Show the learners the deployment events in the console, to see what AWS is doing.

Show the learners the S3 bucket resource that has been actually created.


What if the deployment doesn't work?

```yml
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: generation_de_example_bucket
```

The above template has a problem. Errors in deployment can be viewed via the web console.

**Remember:** Identifying and understanding errors is a CRITICAL SKILL for an Engineer 👀

Notes: The intent here is to prepare the learners for diagnosing errors in their own stacks.

Deploy the above template and demonstrate where to find deployment errors under the Events tab.

Bucket creation will fail because bucket names cannot contain underscores `_`

### Deployment Errors

What if the deployment doesn't work?

```Yml
Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: generation_de_example_bucket
```

The above template has a problem. Errors in deployment can be viewed via the web console.

**Remember:** Identifying and understanding errors is a CRITICAL SKILL for an Engineer 👀

Notes: The intent here is to prepare the learners for diagnosing errors in their own stacks.

Deploy the above template and demonstrate where to find deployment errors under the Events tab.

Bucket creation will fail because bucket names cannot contain underscores `_`

### Deploy a Stack with the CLI

1. Create a deployment bucket with `s3 mb`

```sh
aws s3 mb s3://<bucket-name> --region eu-west-1
```

2. Upload a Template with `s3 cp`

```sh
aws s3 cp <template>.yml s3://<bucket-name>/<template>.yml
```

3. Create a Stack with `cloudformation create-stack`

```sh
	aws cloudformation create-stack
--stack-name <cf-stack-name>
--template-url https://<bucket-name>.s3.eu-west-1.amazonaws.com/<template>.yml
--region eu-west-1
```

Notes: It is more common to use the "deploy" sub command, as this has more functionality.

### A Different CloudFormation Template

- Let's have a look at the `handouts/webserver-start.yml` template
- What does this template define?

Notes: Ask learners what they can determine about what this template will create.

Walk learners through the template.

### Deploying the Webserver Template with the CLI

1. Upload Webserver stack template

```sh
aws s3 cp webserver.yml s3://<bucket-name>/webserver.yml
```

2. Create 'ec2-webserver' stack referencing the uploaded template

```sh
aws cloudformation create-stack
--stack-name ec2-webserver
--template-url https://<bucket-name>.s3.eu-west-1.amazonaws.com/webserver.yml
--region eu-west-1
```

Notes: Run the deployment and validate it is deployed correctly.

After deployment, the webserver will not be accessible as there is no ingress rule for HTTP. We will fix this with a stack update.

### The Webserver Doesn't Work 🙁

The webserver EC2 instance isn't able to show any content yet.

This is because it is missing a Security Group with a rule to allow network traffic from the Internet to the EC2 instance.

We can fix this by adding a SecurityGroup resource to the template.

Let's review `handouts/webserver-updated.yml`, which includes the security group updates needed.

### CloudFormation Anatomy (cont)

```yml
Resources:
  Ec2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0db188056a6ff81ae
      SecurityGroups:
        - !Ref WebSecurityGroup # <-- Security Group Referenced Here

  WebSecurityGroup: # <-- Security Group Defined Here
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Allows HTTP ingress on port 80
```

- A template can contain **any number** of `Resources` of **different types**
- When one resource depends on another resource, we can reference it by the name of the resource in the template; here 'WebSecurityGroup'

#### Point:

👉 Resources in a CloudFormation Stack are **NOT order-sensitive**

- Resources may appear in a Template in **any order**
- CloudFormation will automatically decide the correct order to create resources based on their **dependencies** on each other.

Notes: Learners may sometimes assume from their experience writing Python that CloudFormation is similarly order-sensitive like Python code - it is worth clearing up that it is not.

CloudFormation template are processed by the CloudFormation service to create a set of steps that will be run to actually create resources.

Resources in the templates themselves can appear in any order.

In our example, CloudFormation will create the Security Group first because the EC2 instance depends on it, even though the Security Group comes later in the file.

### Updating a Stack

Any CloudFormation template can be modified to add, remove or change existing resources.

The deployed stack can then be updated, to make it match the new template. 🤩

👉 Resources that require creation or modification will be updated by CloudFormation. Resources with no changes are left alone.

### Update a Stack with the CLI

1. Update a stack with `cloudformation update-stack`

```sh
aws cloudformation update-stack
--stack-name <stack-name>
--template-url https://<bucket-name>.s3.eu-west-1.amazonaws.com/webserver.yml
--region eu-west-1
```

👉 When **updating** a stack, the `stack-name` must be the name of the existing stack to update

### Updating the Webserver Stack

1. Upload the updated stack template

```sh
aws s3 cp webserver-updated.yml s3://<bucket-name>/webserver.yml
```

2. Update the existing stack to match the new template

```sh
aws cloudformation update-stack
--stack-name ec2-webserver
--template-url https://<bucket-name>.s3.eu-west-1.amazonaws.com/webserver.yml
--region eu-west-1
```

Notes: Webserver should now be accessible on its public IP

Console defaults to secure `https://` so you will need to change the link to insecure `http://` to access

### The "deploy" command

It is also common to use the `deploy` sub-command as this will do a create or update according to the state of the stack. Note here we can reference the local version of the template we want to deploy:

```sh
aws cloudformation deploy \
    --stack-name ec2-webserver \
    --template-file webserver.yml \
    --region eu-west-1
```