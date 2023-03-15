---
description: securing users
---

# IAM – Password

## Password Policy

* Strong passwords = higher security for your account&#x20;
* In AWS, you can setup a password policy:&#x20;
* Set a minimum password length.&#x20;
* Require specific character types:&#x20;
  * including uppercase letters&#x20;
  * lowercase letters&#x20;
  * numbers&#x20;
  * non-alphanumeric characters&#x20;
* Allow all IAM users to change their own passwords.&#x20;
* Require users to change their password after some time (password expiration)&#x20;
* Prevent password re-use.

## Multi Factor Authentication - MFA

* Users have access to your account and can possibly change configurations or delete resources in your AWS account.
* You want to protect your Root Accounts and IAM users.
* MFA = password you know + security device you own
* Main benefit of MFA: if a password is stolen or hacked, the account is not compromised.
