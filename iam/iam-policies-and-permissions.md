---
description: This policies will help us to define access
---

# IAM: Policies and Permissions

* Users or Groups can be assigned JSON documents called policies.&#x20;
* These policies define the permissions of the users.&#x20;
* In AWS you apply the least privilege principle: don’t give more permissions than a user needs.

Here we allow user to describe ec2 and few access to CloudWatch.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## IAM Policies Structure

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### Consists of&#x20;

* <mark style="color:red;">**Version**</mark><mark style="color:red;">: policy language version, always include “2012 -10-17”</mark>
* <mark style="color:orange;">**Id**</mark><mark style="color:orange;">: an identifier for the policy (optional) \*</mark>
* <mark style="color:red;">**Statement**</mark><mark style="color:red;">: one or more individual statements (required)</mark>&#x20;

### Statements consists of&#x20;

* <mark style="color:orange;">**Sid**</mark><mark style="color:orange;">: an identifier for the statement (optional) \*</mark>
* <mark style="color:yellow;">**Effect**</mark><mark style="color:yellow;">: whether the statement allows or denies access (Allow, Deny)</mark>&#x20;
* <mark style="color:green;">**Principal**</mark><mark style="color:green;">: account/user/role to which this policy applied to</mark>&#x20;
* <mark style="color:purple;">**Action**</mark><mark style="color:purple;">: list of actions this policy allows or denies</mark>&#x20;
* <mark style="color:green;">**Resource**</mark><mark style="color:green;">: list of resources to which the actions applied to</mark>&#x20;
* <mark style="color:orange;">**Condition**</mark><mark style="color:orange;">: conditions for when this policy is in effect (optional) \*</mark>
