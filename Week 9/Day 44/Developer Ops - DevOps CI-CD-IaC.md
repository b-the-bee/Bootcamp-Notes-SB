#data-engineering 

## Overview

- Introduction to DevOps
- Continuous Integration / Continuous Delivery (CI/CD)
- Infrastructure as Code (IaC)

## Learning Objectives

- Explain the role DevOps plays in modern software
- Identify the role CI/CD plays in modern software
- Create a Continuous Integration workflow with GitHub Actions

## DevOps - A History

Developers and IT Ops professionals had separate (and often competing) objectives, department leadership, key performance indicators, and often worked on separate floors or even separate buildings.

Developers looked after building the system, IT Ops looked after supporting and monitoring the system.

This resulted in siloed teams concerned only with their processes and releases.

These silos often meant miscommunication, delayed deliveries and strains on morale and relationships.

## **What is DevOps?**

A combination of **culture, practises** and **tools** that increases an organisation's ability to deliver services at high velocity.

More succinctly, it is a set of practices that combines software development (Dev) and IT operations (Ops).

Under a DevOps model, dev and ops are no longer siloed.

Both are merged into a single team where engineers work across the entire application lifecycle, from development and test to deployment to operations, and develop a range of skills not limited to a single function.

## DevOps Culture

- **Increased collaboration** as a team as opposed to silos
- **Share responsibility** across the whole team so no one process is looked after by specific people, thus spreading the knowledge and pain
- **No silos** between development and operations
- Give power to **autonomous teams** to enable them to make their own decisions in order to collaborate effectively, and remove convoluted decision making processes
- **Build quality into the development process**
- **Value feedback** to continuously improve ways of working
- **Automate** as much as you can

## DevOps Practices

- Continuous Integration
- Continuous Delivery
- Infrastructure as Code
- Microservices
- Monitoring and Logging
- Communication and Collaboration

In this module, we will be looking into Continuous Integration (CI), Continuous Delivery (CD) and Infrastructure as Code (IaC).


![[Pasted image 20240703095535.png]]

## DevOps Tools

- Source Control (Git)
- Collaboration / communication tools (Slack, Jira, Trello)
- Issue tracking (Jira, Trello, ZenDesk)
- Configuration tools (Puppet, Chef)
- CI/CD tools (we will come onto these)
- And plenty more!

## Benefits of DevOps

**Speed**: Microservices and continuous delivery lets teams take ownership of services and then release updates to them quicker.

**Rapid delivery**: Increase the frequency and pace of releases so you can innovate and improve your product faster.

The quicker you can release new features and fix bugs, the faster you can respond to your customers' needs and build competitive advantage.

**Reliability**: Quality of application updates and infrastructure changes so you can reliably deliver at a faster pace while maintaining a positive experience for end users.

**Better internal culture**: DevOps practises lead to better communication, increased productivity and agility.

### Why does software need to change?

- Features
- Bug fixes
- Security patches
- Contract changes
- Performance optimisations

### What does software need to be able to operate?

- Server
- Database
- Cache
- Storage
- APIs
- Networking


---
# Environments
---

### What is an environment?

An **environment** is the place where our software runs.

Environments are comprised of the resources and infrastructure that support the operation of a software system.

### Who needs access to an environment?

- Developers
- Operations
- Testers
- Product Owner
- Client's support team
- End users


## Types of environments

**Development**: maximise developer productivity, usually local.

**Testing**: hosted, similar to customer-facing environment, for more complex integration and E2E tests.

**UAT(User Acceptance Testing)/Staging**: as stable and production-like as possible, used for customer demos and wider service integration.

**Production**: live, end-user-facing environment. _You must protect it at all costs_.

Different people scrutinising the product at various stages reduces the risk of severe defects.

### Promoting software through our environments

Having multiple environments helps find bugs in our software before it's released to the public.

Changes to the software require deployments up the chain, all the way to production.

### A recipe to deploy software reliably

- Make change
- Build code
- Run unit tests
- Run code quality metrics
- Install the required dependencies in the target environment
- Install our software in the target environment


### Maintaining environments is hard work

- Repetition without automation = more manual work
- Manual work = time wasted
- Manual work = potential differences in environments
- Differences in environments = constant breakage
- Constant breakage = downtime + longer wait to go live

How can we best alleviate this?


---
## Continuous Integration

---


> Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. By integrating regularly, you can detect errors quickly, and locate them more easily.
> 
> -- _ThoughtWorks_

CI has three stages of workflow.

Notes: Bugs and regressions are minimised because they're detected early on and automatically.

### 1. Integrating changes to the main branch (every day)

- All about ensuring code gets into the main branch, as that branch is used for releasing software
- Easiest to do technically, hardest to do culturally
- Integrating code continually means branches are short-lived, which means code is going into main faster

### 2. Rely on automated tests

- Run an automated suite of tests on each integration to the main branch
- Instantly gives you information about failing tests, therefore failing software
- Can help spot bugs or errors
- Only run tests that are important, keep build time low

### 3. Prioritise broken builds

- If a build fails (code didn't compile, tests failed etc.), make fixing it the priority before doing any other tasks
- Everyone can see the same broken build which means better visibility of when something goes wrong

### The enemies of CI

- Knowledge silos
- Manual work
- Inconsistent environments
- Big PRs

Notes:

1. Knowledge silos means teams aren't communicating effectively
2. Manual work means more human errors
3. Inconsistency means it's hard to verify things work or don't work as intended
4. Big PRs means more time spent figuring out what the PR is doing, and easier for bugs to be introduced

---

## Continuous Deployment


---

### What is CD?

- A way of getting your changes (features, bug fixes etc.) into production in a quick and sustainable way
- Code is checked to be in a deployable state by the CI stage

Notes: These methodologies allow you to catch bugs and errors early in the development cycle, ensuring that all the code deployed to production complies with the code standards you established for your app. Big-bang releases which introduce risk and instability and make rollbacks harder.

### Principles of CD

**Frequent, small deployments**: Deploying smaller changes rather than an accumulation of changes means less chance of something going wrong.

**Automation**: Computers are infinitely better at repetitive tasks. Deployment steps can be automated so that we reduce human errors. Things like Infrastructure as Code (IaC) can help.

**Keep improving**: Always look to improve the deployment process. Are you manually doing anything that can be automated?

**Shared responsibility**: Everyone in the team is responsible for creating safe, fast and deterministic delivery of the deployed product, it shouldn't be siloed between devs and ops.

### What is a pipeline?

_A route, channel, or process along which something passes or is provided at a steady rate._

### Build Pipeline

- Provides a steady supply of changes to our end-users
- Automates the integration and delivery flow of your software

### Gated Releases

- A stage in the build pipeline that must be triggered manually to deploy to the next stage
- Allows you to ensure everything is how it should be in the stage before deploying to production

### CI/CD Terms

**Pipeline**: automated stream of work that verifies, integrates and deploys software.

**Build**: a full cycle through the pipeline, triggered when a change is merged into the repo's stable branch.

**Job**: an individual step in the pipeline that carries out one or more tasks.

**Task**: a script run in a job.

### CI/CD Software

- GitHub Actions
- CircleCI
- Jenkins
- Concourse
- And plenty more!