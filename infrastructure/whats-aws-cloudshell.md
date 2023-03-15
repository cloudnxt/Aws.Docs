# What's AWS Cloudshell?

AWS CloudShell is a browser-based, pre-authenticated shell that you can [launch directly ](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html#how-to-get-started)from the AWS Management Console.&#x20;

You can run AWS CLI commands against AWS services using your preferred shell, such as Bash, PowerShell, or Z shell.&#x20;

{% hint style="info" %}
You can do this without needing to download or install command line tools.
{% endhint %}

{% hint style="info" %}
With AWS CloudShell, you can use up to 1 GB of persistent storage for each AWS Region at no additional cost. Persistent storage is located in your home directory (`$HOME`) and is private to you. Unlike ephemeral environment resources that are recycled after each shell session ends, data in your home directory persists between sessions.
{% endhint %}

{% hint style="info" %}
The AWS CloudShell environment and its users are protected by specific security features such as IAM permissions management, shell session restrictions, and Safe Paste for text input.
{% endhint %}

When you launch AWS CloudShell, a [compute environment](https://docs.aws.amazon.com/cloudshell/latest/userguide/vm-specs.html#vm-configuration) that's based on Amazon Linux 2 is created. Within this environment, you can access an [extensive range of pre-installed development tools](https://docs.aws.amazon.com/cloudshell/latest/userguide/vm-specs.html#pre-installed-software), [options for uploading and downloading files](https://docs.aws.amazon.com/cloudshell/latest/userguide/working-with-cloudshell.html#files-storage), and [file storage that persists between sessions](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html#persistent-storage).

(Try it now: [Tutorial: Getting started with AWS CloudShell](https://docs.aws.amazon.com/cloudshell/latest/userguide/getting-started.html).)
