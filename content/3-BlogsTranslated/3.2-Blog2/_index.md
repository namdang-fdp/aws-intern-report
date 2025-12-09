---
title: "Preventing unintended encryption of Amazon S3 objects"
date: 2025-01-15
weight: 3
chapter: false
pre: " <b> 3.2. </b> "
---

Post date: Jan 15, 2025 – Authors: Steve de Vera, Jennifer Paz in [Amazon S3](https://aws.amazon.com/blogs/storage/category/storage/amazon-s3/), [Security, Identity, & Compliance](https://aws.amazon.com/blogs/security/), [Best Practices](https://aws.amazon.com/blogs/architecture/category/best-practices/).

-   **Update March 18, 2025:** This post has been updated to include additional guidance on monitoring and detection.
-   **Update January 17, 2025:** We updated this post to emphasize the importance of using short-term credentials to mitigate risks from unauthorized access techniques similar to the one described in this post.

At Amazon Web Services (AWS), security for customer data is our top priority—and it always will be. Recently, the AWS Customer Incident Response Team (CIRT), along with our automated security monitoring systems, detected an unusual increase in encryption activity involving Amazon Simple Storage Service (Amazon S3) buckets.

It is important to note that these actions **did not exploit a vulnerability in any AWS service**—rather, they required valid credentials used by unauthorized users in an unintended manner. While these actions fall within the customer's responsibility under the shared responsibility model, AWS recommends several steps customers can take to prevent or mitigate the impact of this type of activity.

Working with customers, our security teams detected an increase in S3 data encryption events using **Server-Side Encryption with Customer-Provided Keys (SSE-C)**. While this is a feature used by many customers, we identified a pattern where a large volume of `S3 CopyObject` operations using SSE-C began overwriting objects, effectively re-encrypting customer data with a new encryption key. Our analysis indicates this was performed by malicious actors who obtained valid customer credentials and used them to re-encrypt objects.

Using active defense tools, we deployed automatic mitigations that helped prevent this type of unauthorized activity in many cases. However, because threat actors used valid credentials, it is difficult for AWS to definitively distinguish between legitimate and malicious use. Therefore, we recommend customers adhere to security best practices to mitigate risk.

We recommend customers implement four key security practices to protect against unauthorized use of SSE-C:

1.  Implement short-term credentials.
2.  Implement data recovery procedures.
3.  Monitor AWS resources for anomalous access patterns.
4.  Block the use of SSE-C, unless your application specifically requires it.

---

### 1. Implement Short-Term Credentials

Although the technique above uses SSE-C encryption, the root cause of this issue—like the majority of security incidents—stems from the exposure or compromise of long-term access keys. The most effective way to mitigate the risk of compromised credentials is to not create long-term credentials in the first place.

-   **IAM Roles**: Allow applications to securely send signed API requests from Amazon EC2, Amazon ECS, Amazon EKS, or Lambda using short-term credentials.
-   **IAM Roles Anywhere**: Allows systems outside the AWS Cloud environment to make authenticated calls without using long-term credentials.
-   **AWS IAM Identity Center**: Enables developer workstations to obtain short-term credentials protected by long-term user identities—reinforced by multi-factor authentication (MFA).

These technologies rely on the **AWS Security Token Service (AWS STS)** to issue temporary security credentials.

---

### 2. Implement Data Recovery Procedures

Without data protection mechanisms in place, data recovery times can be prolonged. We recommend protecting data from being overwritten and maintaining a second copy of critical data.

-   **S3 Versioning**: Enable this to keep multiple versions of an object in a bucket, helping to recover objects that are accidentally deleted or overwritten. Use **S3 Lifecycle** to manage old versions and control costs.
-   **S3 Replication**: Copy critical data to another bucket (potentially in a different account or AWS Region). This service provides SLAs for stricter RPO and RTO requirements.
-   **AWS Backup for S3**: A managed service that automates periodic backups for S3 buckets.

---

### 3. Monitor AWS Resources for Anomalous Access Patterns

Without monitoring mechanisms, unauthorized actions on S3 buckets may go undetected.

-   **AWS CloudTrail**: Records events across multiple AWS services. You can check CloudTrail logs for the `requestParameters.x-amz-server-side-encryption-customer-algorithm` value in S3 data events to determine if SSE-C is being used.
-   **Amazon CloudWatch**: Create alarms based on specific metrics or logs.
-   **Amazon EventBridge & AWS Lambda**: Set up automation to perform remediation actions.
-   **Amazon GuardDuty**: Configure GuardDuty and enable **S3 Protection** with **Extended Threat Detection**. This helps GuardDuty detect potential data leakage activities or potential ransomware attempts performed via SSE-C encryption.

---

### 4. Block the Use of SSE-C

If your application does not use SSE-C as an encryption method, you can block the use of SSE-C by applying a resource policy to the S3 bucket or a Resource Control Policy (RCP) within AWS Organizations.

**S3 Bucket Policy**

The example below illustrates a bucket policy blocking SSE-C requests for a bucket named `<your-bucket-name>`:

```json
{
    "Version": "2012-10-17",
    "Id": "S3-Console-Auto-Gen-Policy",
    "Statement": [
        {
            "Sid": "DenySSE-C",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::<your-bucket-name>/*",
            "Condition": {
                "Null": {
                    "s3:x-amz-server-side-encryption-customer-algorithm": "false"
                }
            }
        }
    ]
}
```

AWS Organizations Resource Control Policy (RCP)

RCP allows customers to define maximum access permission limits applied to resources across the entire organization. The following example illustrates an RCP blocking SSE-C requests for all buckets in the organization:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "DenySSE-C",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:PutObject",
            "Resource": "*",
            "Condition": {
                "Null": {
                    "s3:x-amz-server-side-encryption-customer-algorithm": "false"
                }
            }
        }
    ]
}
```

Conclusion

The most important and valuable thing you can do to protect your AWS environment from common threats is to eliminate or minimize the use of long-term credentials. While your security team works tirelessly to protect your systems, rest assured that multiple AWS teams—including AWS CIRT, Amazon Threat Intelligence, and the Amazon S3 team—are continuously innovating to protect your valuable data.

If you suspect unauthorized activity, contact AWS Support immediately for assistance.
