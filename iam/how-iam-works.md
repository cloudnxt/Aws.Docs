# How IAM works?

IAM provides the infrastructure necessary to control authentication and authorization for your AWS account.&#x20;

First, a human user or an application uses their sign-in credentials to authenticate with AWS. Authentication is provided by matching the sign-in credentials to a principal (an IAM user, federated user, IAM role, or application) trusted by the AWS account.

Next, a request is made to grant the principal access to resources. Access is granted in response to an authorization request. For example, when you first sign in to the console and are on the console Home page, you are not accessing a specific service. When you select a service, the request for authorization is sent to that service and it looks to see if your identity is on the list of authorized users, what policies are being enforced to control the level of access granted, and any other polices that might be in effect. Authorization requests can be made by principals within your AWS account or from another AWS account that you trust.

Once authorized, the principal can take action or perform operations on resources in your AWS account. For example, the principal could launch a new Amazon Elastic Compute Cloud instance, modify IAM group membership, or delete Amazon Simple Storage Service buckets.

### Terms <a href="#intro-structure-terms" id="intro-structure-terms"></a>

In the previous illustration we used specific terminology to describe how to obtain access to resources. These IAM terms are commonly used when working with AWS:

#### IAM Resources

The user, group, role, policy, and identity provider objects that are stored in IAM. As with other AWS services, you can add, edit, and remove resources from IAM.

#### IAM Identities

The IAM resource objects that are used to identify and group. You can attach a policy to an IAM identity. These include users, groups, and roles.

#### IAM Entities

The IAM resource objects that AWS uses for authentication. These include IAM users and roles.

#### Principals

A person or application that uses the AWS account root user, an IAM user, or an IAM role to sign in and make requests to AWS. Principals include federated users and assumed roles.

#### Human users

Also known as _human identities_; the people, administrators, developers, operators, and consumers of your applications.

#### Workload

A collection of resources and code that delivers business value, such as an application or backend process. Can include applications, operational tools, and components.
