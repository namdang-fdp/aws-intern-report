---
title: "How to use AWS Transfer Family and GuardDuty to protect against malware"
date: 2025-04-30
weight: 2
chapter: false
pre: " <b> 3.1. </b> "
---

Post date: 2025-04-30 – Authors: James Abbot, Suhas Pasricha, Santhosh Srinivasan in [Security, Identity, & Compliance](https://aws.amazon.com/blogs/security/), [Advanced (300)](https://aws.amazon.com/blogs/learning-levels/advanced-300/), [Technical How-to](https://aws.amazon.com/blogs/post-types/technical-how-to/).

Organizations often need to securely share files with external parties over the internet. Allowing public access to a file transfer server exposes the organization to potential threats, such as malware-infected files uploaded by malicious actors or inadvertently by legitimate users. To mitigate this risk, companies can take steps to ensure that files received via public channels are scanned for malware before processing.

This article demonstrates how to use AWS Transfer Family and Amazon GuardDuty to scan files uploaded via an SFTP (secure FTP) server for malware as part of an overall file transfer workflow. For readers who may have read a previous blog post on this topic, the key difference is that this solution is fully managed and requires no compute resource deployment. GuardDuty automatically updates malware signatures every 15 minutes instead of using a container image for scanning, avoiding the need for manual patching to keep signatures up to date.

---

**Prerequisites**

To deploy the solution in this article, you will need:

-   **An AWS Account**: You need access to AWS to deploy this solution. If you do not have an account, refer to Getting Started with AWS.
-   **AWS CLI**: Install and configure the AWS Command Line Interface (AWS CLI) to authenticate with your AWS account. Set up environment variables for your AWS account using your access token and secret access key.
-   **Git**: You will use Git to download the example source code from GitHub.
-   **Terraform**: You will use Terraform to run automation. Follow the Terraform installation instructions to download and set it up.

---

**Solution Overview**

This solution uses Transfer Family and GuardDuty. Transfer Family provides a secure file transfer service that you can use to set up an SFTP server, and GuardDuty is an intelligent threat detection service. GuardDuty monitors for malicious activity and anomalous behavior to protect AWS accounts, workloads, and data. At a high level, the solution uses the following steps:

1. A user uploads a file via the Transfer Family SFTP server.
2. A workflow managed by Transfer Family invokes AWS Lambda to execute an AWS Step Functions workflow. This workflow only starts after the file is successfully uploaded.
3. Partial uploads to the SFTP server invoke an error-handling Lambda function to report the incomplete upload.
4. An AWS Step Functions state machine invokes a Lambda function to move uploaded files to an Amazon Simple Storage Service (Amazon S3) bucket for processing and then initiates a GuardDuty scan.
5. GuardDuty scan results are sent as a callback to AWS Step Functions.
6. Infected files are moved or sanitized.
7. The workflow sends results to the user via an Amazon Simple Notification Service (Amazon SNS) topic. This could be a notification about an error, malware detection during the scan, or a notification of a successful upload and a clean file ready for further processing.

---

**Solution Architecture and Detailed Walkthrough**

This solution leverages the Malware Protection for S3 feature of GuardDuty to scan newly uploaded objects to an S3 bucket. You can use this GuardDuty feature to set up a malware protection plan for an S3 bucket at the bucket level or to monitor specific object prefixes.

![Solution Architecture](/images/3-BlogsTranslated/Blog2/img1.jpg)

The following steps (refer to Figure 1) describe the workflow of this solution, starting from when the file is uploaded until it is scanned and marked as safe or infected, leading to customizable next steps based on your use case.

1. A file is uploaded using the SFTP protocol via Transfer Family.
2. If the file upload is successful, Transfer Family uploads the file to an S3 bucket named Unscanned, and the Managed Workflow Complete process is triggered. This process is used to handle successful uploads and invokes the Step Function Invoker Lambda function.
3. The Step Function Invoker starts the state machine and initiates the first step in the process by calling the GuardDuty – Scan Lambda function.
4. The GuardDuty – Scan function moves the file to the Processing bucket. This is the bucket from which files will be scanned.
5. When an object upload event is detected, GuardDuty automatically scans that object. In this implementation, a malware protection plan is created for the Processing bucket.
6. When the scan is complete, GuardDuty publishes the scan results to Amazon EventBridge.
7. An EventBridge rule triggers a Callback Lambda function whenever a scan complete event occurs. EventBridge calls the function with an event containing the scan results.
8. The Callback Lambda function notifies the GuardDuty – Scan task using the callback task integration pattern. The Amazon GuardDuty scan results are returned to the GuardDuty – Scan function, and these results are passed to the Move File task.
9. If the result is a clean scan with no threats detected, the Move File task places the file into the Clean S3 bucket, indicating the file was successfully scanned and is safe for further processing. At this point, the Move File function publishes a message to the Success SNS topic to notify subscribers.
10. If the result indicates the file is malicious, the Move File function instead moves the file to the Quarantine S3 bucket for further investigation. The function also deletes the file from the Processing bucket and publishes a message to the Error SNS topic to notify users of a potentially malicious file upload.
11. If the file upload fails and is not fully completed, Transfer Family triggers the Managed Workflow Partial process. Managed Workflow Partial is an error-handling process that calls the Error Publisher function, used to report errors occurring anywhere in the workflow. The Error Publisher function determines the error type—whether due to a partial upload or an issue elsewhere—and sets the corresponding error state. It then publishes an error message to the Error Topic on SNS.
12. The GuardDuty – Scan task has a timeout to ensure an event is published to the Error Topic requiring manual intervention if the file is not successfully scanned. If the GuardDuty – Scan task fails, the Error clean up Lambda function is invoked.
13. Finally, an S3 Lifecycle policy is attached to the Processing bucket. This ensures that no files are left in the Processing bucket for more than one day.

---

**Source Repository**

The AWS-samples repository on GitHub contains a sample implementation developed using Terraform and Python-based Lambda functions to execute this solution. A similar solution can also be deployed using AWS CloudFormation. The source code includes the necessary components to deploy the entire workflow to illustrate the capabilities of Transfer Family and GuardDuty's malware protection plan.

---

**Deploying the Solution**

Use the following steps to deploy this solution into your test environment.

1. Clone the repository to your working directory using Git.
2. Navigate to the root directory of the project you just cloned.
3. Update the Terraform `locals.tf` file with your chosen values for S3 bucket names, SFTP server name, and other variables.
4. Run `terraform plan`. If everything looks correct, run `terraform apply` and enter `yes` to create the resources.

---

**Cleanup**

After testing and exploring the solution, it is important to clean up the resources you created to avoid incurring unnecessary costs. To delete the resources created by this solution, navigate to the root directory of the cloned project and run the following command:

`terraform destroy`

This command will delete the resources created by Terraform, including the SFTP server, S3 buckets, Lambda functions, and other components. Confirm the deletion by entering yes when prompted.

---

**Conclusion**

By using the approach outlined in this article, you can ensure that files received via SFTP and uploaded to your S3 bucket are scanned for threats and are safe for further processing. This solution reduces the risk surface by ensuring that publicly uploaded files are scanned in a secure environment before they are sent to other components of your system. If you have feedback about this post, submit comments in the Comments section below.

---

| ![James Abbott](/images/3-BlogsTranslated/Blog2/author1.jpg)        | **James Abbott** James is a Principal Solutions Architect at AWS, working in Global Financial Services. Outside of work, he enjoys mountain biking in North Carolina.                                                                                                                                                                                                               |
| :------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Suhas Pasricha](/images/3-BlogsTranslated/Blog2/author2.jpg)      | **Suhas Pasricha** Suhas is a Sr. Cloud Application Architect within the AWS Professional Services team. His primary expertise lies in building and modernizing large-scale enterprise applications on the cloud, with a particular focus on the financial services sector.                                                                                                         |
| ![Santhosh Srinivasan](/images/3-BlogsTranslated/Blog2/author3.jpg) | **Santhosh Srinivasan** Santhosh is a Cloud Infrastructure Architect at AWS within the AWS Professional Services team. He has experience in web development and infrastructure automation. At Amazon, he has helped customers establish and operate cloud environments and landing zones at an enterprise scale. In his free time, he enjoys reading books and playing video games. |
