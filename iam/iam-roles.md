---
description: When AWS service needs some permissions.
---

# IAM - Roles

{% hint style="info" %}
Also, a role does not have standard long-term credentials such as a password or access keys associated with it. Instead, when you assume a role, it provides you with temporary security credentials for your role session.
{% endhint %}

* Some AWS service will need to perform actions on your behalf. To do so, we will assign permissions to AWS services with IAM Roles
* Common roles you might require creating:&#x20;
  * EC2 Instance Roles&#x20;
  * Lambda Function Roles&#x20;
  * Roles for CloudFormation

An IAM identity that you can create in your account that has specific permissions. An IAM role has some similarities to an IAM user. Roles and users are both AWS identities with permissions policies that determine what the identity can and cannot do in AWS. However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.&#x20;

## Role chaining

Role chaining is when you use a role to assume a second role through the AWS CLI or API. For example, `RoleA` has permission to assume `RoleB`. You can enable User1 to assume `RoleA` by using their long-term user credentials in the AssumeRole API operation. This returns `RoleA` short-term credentials. With role chaining, you can use `RoleA`'s short-term credentials to enable User1 to assume `RoleB`

Role chaining limits your AWS CLI or AWS API role session to a maximum of one hour. When you use the [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API\_AssumeRole.html) API operation to assume a role, you can specify the duration of your role session with the `DurationSeconds` parameter. You can specify a parameter value of up to 43200 seconds (12 hours), depending on the [maximum session duration setting](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use.html#id\_roles\_use\_view-role-max-session) for your role. However, if you assume a role using role chaining and provide a `DurationSeconds` parameter value greater than one hour, the operation fails.

## Delegation

The granting of permissions to someone to allow access to resources that you control. Delegation involves setting up a trust between two accounts. The first is the account that owns the resource (the trusting account). The second is the account that contains the users that need to access the resource (the trusted account). The trusted and trusting accounts can be any of the following:

* The same account.
* Separate accounts that are both under your organization's control.
* Two accounts owned by different organizations.

To delegate permission to access a resource, you [create an IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_create\_for-user.html) in the trusting account that has two [policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_terms-and-concepts.html#term\_policy) attached. The _permissions policy_ grants the user of the role the needed permissions to carry out the intended tasks on the resource. The _trust policy_ specifies which trusted account members are allowed to assume the role.

When you create a trust policy, you cannot specify a wildcard (\*) as a principal. The trust policy is attached to the role in the trusting account, and is one-half of the permissions. The other half is a permissions policy attached to the user in the trusted account that [allows that user to switch to, or assume the role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_use\_permissions-to-switch.html). A user who assumes a role temporarily gives up his or her own permissions and instead takes on the permissions of the role. When the user exits, or stops using the role, the original user permissions are restored. An additional parameter called [external ID](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_roles\_create\_for-user\_externalid.html) helps ensure secure use of roles between accounts that are not controlled by the same organization.

