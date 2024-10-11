# Lab 1: Discover sensitive data present in S3 bucket using Amazon Macie

**What is Amazon Macie ?**
* Amazon Macie uses pattern matching and machine learning to protect the sensitive data stored in S3 buckets.

* It detects a list of data types including PII (Personally identifiable information) such as names, addresses, credit card numbers, etc.

* Along with detecting data, it gives you complete visibility of your S3 buckets and its information like publicly accessible buckets, unencrypted buckets, and buckets shared with other accounts.

* To get started with Amazon Macie, you can use its free trial of 30 days for bucket evaluation.

* The free trial does not include the discovery of sensitive data present in S3 buckets.

## Steps
1) Sign in to AWS Management Console.
2) Enable Macie for the account.
    * Navigate to the Macie service.
    * Follow the prompts to enable Macie for your AWS account.
4) Create a Macie job.
    * Select the S3 buckets to be evaluated.
    * Choose the type of data to discover.
    * Set up any additional job parameters, such as frequency.
6) Macie job run and findings.
   * Start the job and wait for it to complete.
   * Once the job is finished, review the findings to see any sensitive data detected and the security status of the S3 buckets.

#  Result
Successfully created and executed a Macie job, leading to the discovery of sensitive data in the S3 buckets.
Gained insights into bucket configurations and potential security risks.

