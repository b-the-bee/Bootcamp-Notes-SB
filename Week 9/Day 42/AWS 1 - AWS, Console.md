#data-engineering #aws


## Overview

- What is AWS?
- AWS Console
- IAM (Identity and Access Management)
- AWS CLI (Command Line Interface)
- EC2 (Elastic Compute Cloud)
- S3 (Simple Storage Service)
- Lambda

## Learning Objectives

- Define the role AWS plays in modern software development
- Identify the different use cases for the console and CLI
- Implement services such as IAM, EC2, S3 and Lambda


## What is the cloud?

- "The cloud" refers to servers that are accessed over the Internet, and the software and databases that run on those servers
- Cloud servers are located in data centers all over the world
- By using cloud computing, users and companies do not have to manage physical servers themselves or run software applications on their own machines

Notes: Ask the learners for ideas why running applications on their own machines is a bad idea.

E.g.:

- they turn it off / runs out of battery
- runs out of storage / processing capacity
- many concurrent connections


## What is AWS?

- **Amazon Web Services** is a cloud computing platform
- Offerings encompass computing power, database storage, content delivery, logging and monitoring - if you need to do a thing, there's an AWS product for it
- At last count, there were over 200 AWS products to choose from...


## Regions

- A physical location somewhere in the world where AWS data centers are clustered
- Each group of logical data centres within a Region is called an **Availability Zone**
- Multiple geographic Regions, including North America, South America, Europe, China, Asia Pacific, South Africa, and the Middle East
- Regions have a code name, such as `eu-west-1` which represents the Irish region

## Availability Zones

- One (or more) discrete data center(s) in an AWS region
- AZs in a region are physically-separate, but within 100km of each other - high-bandwidth, low-latency networking
- Gives customers the ability to operate production applications and databases that are more highly available, fault tolerant, and scalable than would be possible from a single data center
- If an application is partitioned across AZ's, companies are better isolated and protected from issues such as power outages, lightning strikes, tornadoes, earthquakes, and more

Notes: Data centres are just enormous buildings that operate a vast amount of computer machinery, with its own cooling and power setup.

Currently 33 AWS regions, containing 105 AZs.

London (eu-west-2) has 3 AZs.

This is a useful tool to visualise it: https://aws.amazon.com/about-aws/global-infrastructure

Example of outage: London 2022 heatwave caused data centres to power down to protect servers - https://www.protocol.com/bulletins/google-oracle-cloud-uk-heat


## The AWS Management Console

- The standard graphical interface to AWS
- AWS make changes to it regularly, so don't be surprised if things move every few months!
- The home page has a list of your commonly used services, account summary info, and announcements

## The AWS Management Console

- The full list of services can be accessed from the tab at the top 
- There are many(!) services, and each of them have been built by different teams (or even companies) around the world
- As such, many of the services have a very different look and feel when using them in the Management Console

---

## AWS Services

Services tend to be grouped under one of several categories, including:

- File storage (e.g. `S3`)
- Compute (e.g. `EC2`, `Lambda`)
- Security & identity (e.g. `IAM`)
- Databases (e.g. `RDS (Relational Database Service)`)

We'll be covering some of these in more detail in this session.

---
## IAM

- **Identity and Access Management**
- Manage users and their level of access to the CLI or console
- Manage roles and permissions for the roles
- Manage authentication for users or applications accessing AWS
- Free to use - you can create as many roles as you wish

## IAM Features

- Granular permission - user or app can access service X but not service Y
- Identity Federation (login with Facebook, Google, Active Directory etc.)
- MFA
- Password rotation policy
- Integrates with many different AWS services

## IAM Key Terms

- Users
- Groups
- Roles
- Policies

We will dive into what each means.

### IAM - Users

- End users such as people, employees etc.
- Accounts with username and password
- Can define level of access to AWS services
- Manage the permissions of what the user can perform
- Manage their security credentials (MFA etc.)
- You are either the account owner (root) or an IAM user.

Notes: Example: Each learner is an IAM user.

### IAM - Groups

- A collection of users, where you can define permissions for all of them in an easier way
- A group can contain many users, and a user can belong to multiple groups
- Groups can't be nested; they can contain only users, not other groups
- There's no default group that automatically includes all users in the AWS account

### IAM - Roles

- Similar to an IAM user, except a role is intended to be assumed by anyone or any service that needs it
- Provides temporary security credentials for the length of the session, as opposed to a username and password
- Specific permissions on AWS services and resources
- Policies are attached to roles to grant them access/privilege

### IAM - Policies

- You manage access in AWS by creating policies and attaching them to IAM identities (users, groups, roles) or AWS resources
- A policy is an object that, when associated with an identity/resource, defines their permissions
- These permissions determine if a request is allowed or denied
- Most policies are stored as JSON

### IAM - Best Practices

- Create **individual** users
- Manage permissions with groups
- Use IAM roles for as many actions
- Grant **least privilege** with permissions
- Configure a **strong** password policy
- Enable MFA for privileged users

### IAM - Best Practices II

- Setup audits with AWS CloudTrail.
- CloudTrail logs for exactly who did what, when, and from where
- Use IAM roles to allow users and services to share access to another service
- Rotate security credentials **regularly**
- Restrict privileged access further with conditions (for instance, only allowing a range of IPs that a request must come from)
- Reduce use of root (mostly used for billing and locking down account securely)