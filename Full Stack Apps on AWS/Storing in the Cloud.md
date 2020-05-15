# Storing Data in the Cloud

## Understanding Persistence
### RAM 
Data can be accessed quickly, but is erased once the server restarts. It may be okay to use RAM when prototyping and replace it with a database.
### Hard Disk Drive
Data remains after the server restarts but is specific to that server.
### Race Condition
When an application's behavior is dependent on other uncontrollable events. This is an issue with storing data on disks or RAM of multiple servers.
### Relational database
Can store at scale improve search runtime and maintain relationships between data fields.

## Database Basics
**B-Tree** A generalization of a binary search tree, which stores sorted data, but can have more than 2 child nodes.

**Bloom Filters** A data structure that is useful for determining if an item is probably in a data set, or definitely no in the data set. Bloom filters don't actually store the data themselves.

**Primary key and foreign key** The primary consists of one or more columns in a table that are unique to each record. A foregin key in a table contains the primary key of another table.

## Provisioning a Cloud Database
### Configuring AWS RDS
    
## Filestore Basics

    - file stores allow for archiving data. in AWS the file store is called S3, and the archive resource is called "glacier"
    - CDN are a network of proxy servers close to end users, which reduces latency.
    - SignedURLs allow clients to send and receive data by directly communicating with the file store. This saves the server from using its bandwidth to serve as the intermediary that transmits data to and fro the client; this is faster for clients as well.
    - Buckets a simple directory like system in which to store data.
## Creating an S3 Filestore Bucket

    - Create "dev" resources: Use the "dev" set of infrastructure for development and  separate set of infrastructure for production.
    - AUS 256: Advanced Encryption Standard with a 256-bit key. This is a popular encryption standard.
    - CORS: Cross Origin Resource Sharing: defines how a  client can interact with a resource and what the client can and cannot do with that resource. Setting the CORS policy of our S3 bucket allows our client to communicate with the S3 bucket using the SignedURL pattern.

#### Bucket CORS Policy
You'll need this policy to create a bucket where we can use the SignedURL pattern.
```
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="https//s3.amazonaws.com/doc/2006-03-01/">
<CORSRule>
    <AllowedOrigin>*</AllowedOrigin>
    <AllowedMethod>POST</AllowedMethod>
    <AllowedMethod>GET</AllowedMethod>
    <AllowedMethod>PUT</AllowedMethod>
    <AllowedMethod>DELETE</AllowedMethod>
    <AllowedMethod>HEAD</AllowedMethod>
    <AllowedHeader>*</AllowedHeader>
</CORSRule>
</CORSConfiguration>
```

## Understanding Secrets

    - HIPAA (Health Insurance Portability and Accountability Act) is a law in the U.S that requires data privacy and security for medical information.
    - Use environment variables to store your username and password, to avoid hard-coding username and password information in your code.
    - A Voice committing your passwords to git. Use .gitignore to define files that you do not want to commit to git.
    - IAM user role: an IAM role can give a user a set of permissions to access one or more services
    - IAM service role: an IAM role gives a service a set of permissions to access one or more services.
    - It's beneficial to create a role that contains a policy group (a set of permissions) rather than to assign individual permissions to a specific user. Imagine if a user leaves the company and a new hire takes their place instead of reassigning all the permissions for their job you can just assign the existing IAM role to that new employee.

### New in AWS - Batch Operations
When creating a service profile and selecting all s3 actions, there will be a new field in the resources section to limit which jobs can be invoked on the bucket. Your options are to
    - select any so that this bucket has the right to call any job
    - Create a job and reference it by its ARN
    - limiting the Policy actions.

> have a seperate user outside of your root user to use for daily tasks.

***AWS Configuration Files*** 
The `aws configure` command creates two new files on your computer to save credentials and configurations.

Each of these can contain settings for multiple proles which are defined by using hard brackets containing the profile name preceding the variables i.i. `[profile1]` In example, if you are working on 2-3 systems you will need installed credentials for each. You can modify these files in a text editor. 

