<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Dumanyie Chamberlain  
**Email:** dumanyiechamberlain@gmail.com

---

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project I will be using the AWS IAM ( Identity Access Management) service to control authentication and authorization of AWS accouts.

### Tools and concepts

In this project, I learned how to use several core AWS services and important security concepts, including:

Amazon EC2 – Launching and managing virtual servers to increase computing power.

IAM (Identity and Access Management) – Creating users, groups, and policies to control access to AWS resources.

IAM Policies – Writing and attaching policies to define what actions users are allowed or denied.

IAM User Groups – Managing permissions efficiently by assigning policies to groups instead of individual users.

Account Alias – Creating a user-friendly login URL for easier AWS console access.

Principle of Least Privilege – Granting only the permissions necessary (development access only, restricting production).

Access Testing & Authorization – Verifying permissions by logging in as a different user and observing access restrictions.

This project strengthened my understanding of cloud security, access control, and resource management in AWS.

### Project reflection

This project took me approximately 1-2 hours to complete. (Documentation included)

The most challenging part was configuring IAM policies correctly and ensuring the permissions were precise enough to allow access to the development instance while restricting access to the production instance. Understanding how policies, user groups, and resource tags work together required careful attention to detail.

It was most rewarding to successfully test the intern’s access and confirm that the security controls worked exactly as intended. Seeing the principle of least privilege enforced in practice gave me a stronger understanding of real-world cloud security management.

---

## Tags

### What I did in this step

in this step I am going to handle increased website traffic from new students and support onboarding a new intern with secure access, launch two Amazon EC2 instances to boost NextWork’s computing capacity while maintaining resource security.

### Understanding tags

Tags in AWS are user-defined, key-value pair labels (metadata) assigned to resources like EC2 instances or S3 buckets to enable organization, cost allocation, security management, and automation. They are critical for filtering, searching, and managing resources based on purpose, owner, or environment (e.g., Environment: Production)

### My tag configuration

The tag I’ve used on my EC2 instances is called Env The value I’ve assigned for my instances are...

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

As I onboard the new intern, I need to make sure they have the correct level of access. They should be able to work freely in the development EC2 instance, where testing and experimentation are safe.
However, they must not have access to the production instance. I want to prevent any accidental shutdowns or unintended changes to the live environment while they’re still learning.
To control this properly, I’ll use AWS IAM to define exactly what they’re allowed to access.
In this step, I will:
Create an IAM policy that grants access to the development EC2 instance only.

### Understanding IAM policies

AWS Identity and Access Management (IAM) policies are JSON documents that define permissions, controlling which actions users, roles, or services can perform on AWS resources. They enforce security by explicitly allowing or denying access, facilitating the Principle of Least Privilege. Policies can be attached to identities (users/roles) or resources. 

### The policy I set up

For this project, I’ve set up a policy using JSON, it is for customizing policies using JSON, you can define specific permissions, actions, and resources that users or roles can access

### Policy effect

### Understanding Effect, Action, and Resource

---

## My JSON Policy

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this stepNow that I’ve set up the permission policy and restricted access to the development instance, everything is secure and ready on the IAM side.
The intern is eager to get started and access the AWS account. Before sharing login details, I want to make sure the sign-in process is simple, clear, and professional.

Instead of using the long default AWS account ID in the login URL, I’ll create an Account Alias to make the login link easier to remember and use.
In this step, I will:
Create an AWS Account Alias to simplify user login to my AWS account., I will... because...

### Understanding account aliases

An account alias is...When you create an AWS account, AWS gives you a login link that looks something like this:

https://123456789012.signin.aws.amazon.com/console/

But An Account Alias is just a nickname for your AWS account. Instead of using the complex login link above i can simply use: nextwork-alias-chamberlain.

### Setting up my account alias

Creating an account alias took me less than a minute. Now, my new AWS console sign-in URL is: nextwork-alias-chamberlain

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

To keep things structured and secure, I’m going to set up proper IAM organization instead of assigning permissions randomly.

First, I’ll create a dedicated IAM group for all NextWork interns. This will allow me to manage permissions for every intern in one central place. If I ever need to adjust access, I can update the group once instead of changing each user individually.

Next, I’ll create a dedicated IAM user account for the new intern, so they have their own secure way to log in and access the development environment.

In this step, I will:

Create an IAM group specifically for NextWork interns.

Create an IAM user for the new intern and prepare their login access.

### Understanding user groups

An IAM user group is a way to manage permissions for multiple users at once. Instead of giving permissions to each person individually, I can:
Create a group
Attach permissions (policies) to that group
Add users to the group
Anyone in the group automatically gets those permissions.

### Attaching policies to user groups

Every user inside that group automatically gets the permissions defined in that policy.
You don’t need to attach the policy to each user individually.

### Understanding IAM users

An IAM user is a person or identity that is allowed to log in and use your AWS account.
It represents:
A real person (like you, a developer, or an intern) Or sometimes an application/service that needs access.

---

## Logging in as an IAM User

### Sharing sign-in details

Share the Console Login Link + Username/Password
If the user needs AWS Management Console access (web login).
You provide:
The account login URL
(either using the Account ID or your Account Alias).
Their IAM username.
Their temporary password.

Share Access Keys (For CLI or Programmatic Access)
If the user needs to use:
AWS CLI
SDKs (Python, Java, etc.)
Automation scripts
You provide:
Access Key ID.
Secret Access Key.


### Observations from the IAM user dashboard

I logged into the AWS Console using the new IAM user I created for development access. As soon as I landed on the dashboard, I noticed that some panels were showing “Access Denied.”
At first, that might look like something is broken — but it’s actually working exactly as intended.

Because I intentionally restricted this user’s permissions, they only have access to specific resources (like the development EC2 instance). They do not have full access to the entire AWS account.
This confirms that the IAM policies I configured are doing their job: limiting access to only what’s necessary.

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

Before sharing the login details, I tested the intern’s IAM user to ensure the permissions were correctly configured.

I logged into AWS using the intern’s credentials and navigated to the EC2 dashboard. I confirmed that the intern could access and manage the development instance, but was restricted from stopping or modifying the production instance.

This verified that the IAM policy was working as intended, granting necessary access while protecting production resources.

### Testing policy actions

### Stopping the production instance

When I attempted to stop the EC2 instance tagged as production, the action failed and an authorization error was displayed in the AWS Console. The system showed an “Access Denied” message indicating that I was not authorized to perform the stop action on that instance.

The red banner signifying an error occured. This occurred because the IAM policy attached to my user (through a group) explicitly restricts stopping any EC2 instance with the production tag. Although I have permissions to manage development resources, the policy was intentionally designed to prevent changes to production resources.

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my proIn this step, I used the IAM Policy Simulator to test and validate permissions without making any real changes to AWS resources.

The Policy Simulator is a built-in AWS tool that allows you to check whether a user, group, or role is allowed or denied from performing specific actions. Instead of actually stopping an instance or modifying resources, the simulator predicts the result based on the attached policies.ject, I'm going to... I'm doing this because...

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is used to test and validate permissions safely before applying them in the real AWS environment.

### How I used the simulator

I set up a simulation to validate policies without affecting your actual AWS resources. The results for the permmssions where both denied until I had to adjust  the instance, adding development to indicate that you want to run the simulation for the instances with that tag.

![Image](http://learn.nextwork.org/sparkling_blue_joyful_nopal/uploads/aws-security-iam_069d8a621)

---

---
