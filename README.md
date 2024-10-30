# aws-event-driven-architecture

Uses events to decouple an application’s components

Sample usecase:
1. Event producer: AWS S3 bucket
2. Event ingestion: AWS SNS
3. Event stream: AWS SQS
4. Event consumer: AWS lambda

![image](https://github.com/user-attachments/assets/82b76f92-3125-4e94-929c-a9e6d86c4e33)

## Steps:

1. Create S3 bucket with default settings.
2. Crete SNS Topic standard
3. Create SQS queues (2 queues)
4. Create Lambda function (2 Lambda functions)
- Update SNS access policy (advanced)-because S3 bucket and SQS Queue need acccess on SNS
- Update SQS access policy for 2 queues (advanced)-because SNS Topic and Lambda need acccess on SQS
- Update lambda role permisions - need access to cloudwatch and SQS
5. connect all components
- Create event notification in S3 bucket properties which notifies SNS (connection from S3 to SNS)
- Create subscriptions, add 'Subscription filter policy' in both subscriptions of SNS (connection from SNS to SQS)
- Create Lambda triggers in SQS for both Queues(connection from SQS to Lambda)

6. Now test the setup by uploading files into S3 bucket and check cloudwatch logs
- Put objects
- Copy objects
