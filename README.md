
# Quickstart - Serverless by Example

To get the example running you need to create a couple of AWS resources and follow a few simple steps. You'll create a S3 bucket, a DynamoDB table, an API Gateway and two Lambda functions.

1. Clone the project - `git clone https://github.com/amohrhard/javamagazin-serverless.git`
2. Build the project with `mvn clean package`
2. Log in the AWS console and create the following resources (all in the same region):
  1. a DynamoDB table named `tmp-lambda-gallery` Partition key: String id. Sort key Number ts
  2. a S3 bucket for uploading pictures
  3. a API Gateway named `lambda-gallery`

Now for the lambda functions:

The first lambda function will trigger the metadata extraction. When creating choose the "blank function". The assistant will ask for a trigger. Choose S3 as a integration point and configure it, so it matches the S3 bucket and images you want to upload.

The second lambda will supply data from the DynamoDB table to the api gateway. Create it using the blank function again. When asked for a trigger select API Gateway and select the previously created lambda-gallery API gateway. Name the lambda function `feed` as this will be the path (/feed).

The handler functions are as follows:

Feed Lambda: `biz.cosee.talks.lambda.demo.feed.FeedHandler`
Upload Lambda:
`biz.cosee.talks.lambda.demo.s3.UploadHandler`

When asked for a package select the jar file from target/.


