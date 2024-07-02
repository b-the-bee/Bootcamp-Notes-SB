#data-engineering #aws

---
# S3
---

## S3 - Simple Storage Service

- Secure, durable, highly scalable object store
- Safe place to store files
- **Object**-based storage
- Files can be 0 bytes to 5TB
- **Unlimited** storage, you pay for what you use
- Files are stored in **buckets** (basically a folder)
- Globally distributed

## S3 - Objects

S3 is object-based. Think of objects just like files. They consist of the following:

**Key**: The name of the object

**Value**: The sequence of bytes containing the data

**Version ID**: For versioning

**Metadata**: Data about data you're storing

## S3 Guarantee Model

- Up to 99.99% availability
- Up to 99.999999999% durability (11x 9s)

99.99% availability equates to 52.60 minutes of downtime per year.

99.999999999% durability means that if you store 10 million objects then you expect to lose a single object of your data every 10,000 years.

## S3 - Advanced Features

- Object versioning
- Storage class: trade durability/availability for cost
- Lifecycle policies: manage the lifetime of your files automatically
- Encryption at-rest
- MFA Delete
- Bucket policies to control who can access them