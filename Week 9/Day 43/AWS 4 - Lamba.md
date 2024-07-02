#data-engineering 

--- 
## Lambda

---

## Lambda

- 100% code, 0% infrastructure
- Run code without worrying about OS, patching, scaling, any physical hardware
- Never worry about capacity again
- Lambdas run in response to events such as data changes in S3, DB record being inserted
- You can even call them from through HTTP requests, SDK, or the AWS CLI


## Lambda Triggers

A lambda function is automatically invoked when one of its triggers is activated.

For example:

- When a record has been inserted into a DB table
- When a file has been uploaded to S3
- When a commit is pushed onto a repo hosted in CodeCommit (Git for AWS)
- When a monitoring alarm goes off

## Lambda Pricing Model

**Number of requests:** First 1 million requests per month are free, $0.20 per 1 million after (cheap!)

**Duration:** Calculated from the time your code begins until it terminates, up to the millisecond. The price depends on how much memory you allocate. Roughly $0.0000166667 for every GB-second used. The first 400,000 are free per month.

Notes: It used to be rounded to the nearest ms but is now at a per ms basis.


## Limitations

- Cold starts: Time it takes to kick off an instance (it's a container under the hood)
- Difficult to scale without understanding the concurrency execution model
- Tightly integrated to work with other AWS services so may have potential 'lock-in'
- Can be difficult to develop locally
- Unsuitable for tasks that take 15+ minutes

## Use Cases

- Tasks that take less than 15 minutes to complete
- Asynchronous, event-driven workloads
- Consistent level of traffic