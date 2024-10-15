# Event-Driven Image Upload Notification System

## Project Description

This project demonstrates a simple **Event-Driven Architecture (EDA)** using AWS services such as **Amazon S3**, **AWS Lambda**, and **Amazon SNS (Simple Notification Service)**. The primary goal is to create an **Image Upload Notification System** where, whenever an image is uploaded to an S3 bucket, a Lambda function is triggered to process the event, and a notification is sent through SNS to notify subscribers.

This setup helps improve your skills in **cloud computing**, **serverless architecture**, and **AWS services**.

---

## Table of Contents
- [Project Architecture](#project-architecture)
- [Prerequisites](#prerequisites)
- [Steps to Build the Project](#steps-to-build-the-project)
  1. [Set Up an AWS Account](#step-1-set-up-an-aws-account)
  2. [Create an S3 Bucket](#step-2-create-an-s3-bucket)
  3. [Create an SNS Topic](#step-3-create-an-sns-topic)
  4. [Create an SNS Subscription](#step-4-create-a-subscription)
  5. [Create a Lambda Function](#step-5-create-a-lambda-function)
  6. [Add an S3 Trigger to Lambda](#step-6-add-s3-trigger)
  7. [Write Lambda Function Code](#step-7-write-lambda-function-code)
  8. [Test the System](#step-8-test-the-system)
- [Expected Outcome](#expected-outcome)
- [Future Enhancements](#future-enhancements)
- [Conclusion](#conclusion)

---

## Project Architecture

The architecture consists of the following components:

1. **Amazon S3**: Storage for images.
2. **AWS Lambda**: A serverless function that processes the S3 event.
3. **Amazon SNS**: A notification service that sends alerts to subscribers when an image is uploaded.

![Project Architechure](https://github.com/Kishor-Bibin/AWS-Projects/blob/f6ed997de68cd8d3976222ddb94e6c7b25db8234/Project%205/Images/EDA_Architecture.png)


---

## Prerequisites

Before starting this project, ensure you have the following:

- An active **AWS account**.
- **AWS CLI** installed (optional, for command-line operations).
- Basic understanding of **AWS S3**, **Lambda**, and **SNS** services.
- Familiarity with writing **Lambda functions** in **Python**.

---

## Steps to Build the Project

### Step 1: Set Up an AWS Account

If you don’t already have an AWS account, sign up at [aws.amazon.com](https://aws.amazon.com/). Ensure that your account has the necessary permissions to use **S3**, **Lambda**, and **SNS**.

### Step 2: Create an S3 Bucket

1. Go to the **S3 Management Console**.
2. Create a new S3 bucket:
   - Bucket Name: Eg:`eda-project-123`
   - Region: Choose your preferred region.
3. Note the bucket name and region as you’ll need this information later.

### Step 3: Create an SNS Topic

1. Navigate to **SNS (Simple Notification Service)** in the AWS Management Console.
2. Create a new SNS topic:
   - **Topic Name**: `ImageUploadNotification`
   - **Type**: Standard
3. Note the **ARN (Amazon Resource Name)** of the SNS topic for later use.

### Step 4: Create a Subscription

1. In the **SNS console**, go to the **Subscriptions** section.
2. Create a new subscription:
   - **Protocol**: Choose email, SMS, or any other available protocol.
   - **Endpoint**: Provide the email address or phone number where the notifications should be sent.
   - **Topic ARN**: Select the ARN of the `ImageUploadNotification` topic created earlier.
3. Confirm the subscription via the email or SMS received.

### Step 5: Create a Lambda Function

1. Go to **Lambda** in the AWS console.
2. Create a new Lambda function:
   - **Function Name**: `ImageUploadProcessor`
   - **Runtime**: Python 3.9 (or any version you prefer).
   - **Execution Role**: Ensure the Lambda function has permission to access S3 and SNS.
3. Create the function.

### Step 6: Add S3 Trigger to Lambda

1. In the **Lambda** console, under your function (`ImageUploadProcessor`), click on **Add Trigger**.
2. Choose **S3** as the trigger source.
3. Select the **bucket** (`amc-eda-project-123`) created earlier.
4. Configure the trigger for events:
   - **Event type**: `ObjectCreated`
   - **Prefix**: (optional) You can specify the folder path if needed.
5. Save the trigger settings.

### Step 7: Write Lambda Function Code

In the **Lambda** function editor, paste the following code:


Replace `'arn:aws:sns:your-region:your-account-id:ImageUploadNotification'` with the actual SNS Topic ARN from Step 3.

### Step 8: Test the System

1. Upload an image to the **S3 bucket** (`amc-eda-project-123`).
2. Check the **SNS subscription endpoint** (email, SMS, etc.) to confirm if you received a notification.
3. You can also check the Lambda logs in **CloudWatch** to see the event processing details.

---

## Expected Outcome

After completing this project, you should have an event-driven image upload notification system where:

1. When an image is uploaded to the S3 bucket, an event is triggered.
2. The Lambda function processes the event and sends a notification through SNS.
3. Subscribers receive a message notifying them about the new image upload.
   ![Result Example](https://github.com/Kishor-Bibin/AWS-Projects/blob/cb2971ef847af666b71147917e2b40a749c3b219/Project%205/Images/Screenshot%202024-10-14%20210805.png)

---

## Future Enhancements

- **Image Resizing**: You can extend the Lambda function to resize images when they are uploaded.
- **File Type Validation**: Implement validation to ensure only certain file types (e.g., JPG, PNG) are allowed.
- **Logging & Monitoring**: Enhance the system with more detailed logging and monitoring using **AWS CloudWatch**.
- **Notifications for Multiple Events**: Add more triggers, such as notifications for file deletions or modifications.

---

## Conclusion

This project illustrates the basic principles of **Event-Driven Architecture** using AWS services. It is scalable and can be expanded with additional functionality as your understanding of AWS grows.


--- 

## Author
**Kishor Bibin**  
LinkedIn: [Your LinkedIn Profile](https://www.linkedin.com/in/kishor-bibin)  
GitHub: ![Your GitHub Profile](https://github.com/your-github-profile)

---

