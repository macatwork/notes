# Building and Deploying

## Organising Code and Working with Larger Systems
### Designing the application to be extensible

#### Features and Modularity
The process of splitting code into logical "features". This is a way of describing modular programming where code which relates to one task is grouped together. In this example the `/feed` and `/auth` endpoints are the features. All routing, models, business login and helper functions for these modules should be separated as much as possible. This way you can gain an understanding of what code is where just by looking at the general structure.

Often one feature may depend on another. For example user authentication will be needed within the feed. These dependencies should be kept loose and consistent with only a few methods being consumed. The goal as the system continues to grow is to minimize refactoring outside of specific features as you continue to learn cloud and explore microservices. OFten entire features may be ported to their own server's infrastructure.
## Connecting RDS Database In Node
ORM is a way of connecting Databases to Node. Sequelize is the name of the ORM used here.

### Models
A model is the data representation of some group of data. In object-oriented programming terms, a model is an object and is represented by a new class. It should usually represent a noun like user, item, etc. The `@Table` decorator is used.

### Parameters
The model contains instance parameters. These can be other models or primitive fields. Use the `@Column` decorator to link parameters to the table columns. The bang symbol `!` specifies if the field in the table can be null. Sequelize handles the datatype mappings from TypeScript types to postgres column data types.

ORMS makes it easy to switch to a different SQL dialect without having to modify the code that interacts with the databaseWriting SQL queries directly instead of using an orm would require the modification of SQL queries so they are compatible with the database being used. 

#### Migrations
- Migration refers to modifying the database to a newer version.
- Up migration is upgrading the db to a newer state
- Down migration is downgrading

#### Seeding 
Seeds are default rows of data that will be inserted upon database formation. This may be helpful when provisioning databases frequently for specific applications and having welcome data populated, or when running tests on staging systems to simulate real world conditions.

### Using Sequelize in Node RestAPI 

**Decorators**
Also known as annotations are a feature of sequelize-typescript which allows the linking of database features with models. 

### Associations
Associations allow models to reference other models. 

## Connection S3 Filestore in Node

## Handling Secrets with Environment

## Permissions for Elastic Beanstalk

## Deploying Server to the Cloud
