# aws-event-driven-architecture

Uses events to decouple an application’s components

Sample usecase:
1. Event producer: AWS S3 bucket
2. Event ingestion: AWS SNS
3. Event stream: AWS SQS
4. Event consumer: AWS lambda

![image](https://github.com/user-attachments/assets/4c3de10f-d207-48a0-bbd5-b9730d96c2b1)


## Steps:

1. Create S3 bucket.
2. Crete SNS Topic standard
3. Create SQS queues (2 queues)
4. Create Lambda function (2 Lambda functions)
5. Update Policies for SNS, SQS and Lambda
- Update SNS access policy (advanced)-because S3 bucket and SQS Queue need acccess on SNS
- Update SQS access policy for 2 queues (advanced)-because SNS Topic and Lambda need acccess on SQS
- Update lambda role permisions - need access to cloudwatch and SQS
6. Connect all components
- Create event notification in S3 bucket properties which notifies SNS (connection from S3 to SNS)
- Create subscriptions, add 'Subscription filter policy' in both subscriptions of SNS (connection from SNS to SQS)
- Create Lambda triggers in SQS for both Queues(connection from SQS to Lambda)

7. Now test the setup by uploading files into S3 bucket and check cloudwatch logs
- Put objects
- Copy objects

![image](https://github.com/user-attachments/assets/19bc38ec-177f-4ccf-bfe9-62321b528cae)

![image](https://github.com/user-attachments/assets/c95e27ef-ccb7-4617-8fd2-a85986a39d42)

![image](https://github.com/user-attachments/assets/c40286a9-60c4-4bf4-b13f-5c0deb8b7d2e)

![image](https://github.com/user-attachments/assets/10dbae79-b4e0-4164-8d0e-1105b72f0a0a)

![image](https://github.com/user-attachments/assets/53e11427-449c-4ed8-9656-bf5720701972)

![image](https://github.com/user-attachments/assets/8bd26323-4093-4df3-83b4-4331eade5799)

