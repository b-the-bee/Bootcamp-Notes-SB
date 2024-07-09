#data-engineering 

---

## CloudFormation is great 🎉

But wait. There's more!

---

### More Features - Functions

CloudFormation has a number of built-in `Functions`

Functions allow values in the template to be manipulated when it is deployed.

As with functions in Python, CloudFormation functions take an `input`, and return an `output`.

### Functions

Some Functions:

- `!Ref` - Gets a Reference to another resource
- `Fn::Sub` - Substitutes placeholders in a value with other values
- `Fn::Join` - Joins a set of values together into one value
- `Fn::Select` - Selects a single value from a list by index

There are [many functions available](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html)


### Function Example - Ref

We have already seen an example of `Ref` in adding a security group to our webserver:

```yml
Resources:
  Ec2Instance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: ami-0db188056a6ff81ae
      SecurityGroups:
        - !Ref WebSecurityGroup # <-- Security Group Referenced Here

  WebSecurityGroup: # <-- Security Group Defined Here
    Type: AWS::EC2::SecurityGroup
```

- `!Ref` here finds the ID value for the security group
- The ID value is necessary to assign the security group to the EC2 instance
- The ID value is not generated until the template is deployed, which is why this must be resolved with a function at deploy-time

### More Features - Parameters

Information can be passed into a stack from outside with `Parameters`

Parameters allow the stack to be customised:

- Resource options such as EC2 instance size can be specified
- Names for resources like S3 bucket can specified

This avoids the need to hard-code values that may need to change

👉 Parameters help make a stack more `generic` and `reusable`

Notes: Stack parameters are very much like args into a python program, or args into a Unix script.

With parameters, we can avoid having to edit the stack body itself to make changes.

### Parameter Example

```yml
Parameters: # <-- Parameters block
  TeamName: # <-- TeamName Parameter
    Type: String
    Description: Dev team name for this deployment
    Default: your-team-name

Resources:
  CafeDataS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      AccessControl: Private
      # Parameter is used:
      BucketName: !Sub generation-${TeamName}-cafe-data-bucket
```

- `TeamName` can be provided to the stack as an argument on the CLI
- If you add `Default`(s) then command line overrides are optional
- Using the `!Sub` function, the TeamName parameter is substituted into the value for BucketName

Notes: From this example we can see how this same template could be used for multiple teams without needing to actually edit the template itself.

A more usual industry scenario for this pattern would be to parametrise based on the deployment target environment, e.g. dev bucket, test bucket, prod bucket.