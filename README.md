# AWS S3 Lambda Function

AWS Lambda function that listens for S3 put events for a specified S3 bucket, retrieves the uploaded image file, creates the thumbnail, and puts them back to the specified S3 bucket's 'thumbnails' folder with the same key structure.

### Install dependencies with pip
```bash
pip install Pillow
```

Install the `Pillow` module in the thumbnail-s3-lambda directory. 

### Create Lambda Function
Create the S3 Lambda function with the following configuration settings:

```bash
Runtime: Python 2.7
Handler: thumbnail-genrator.lambda_handler
Triggers: S3: bucket-media
Prefix: media/

```

The prefix is used to avoid cyclic loop for put events in the same parent bucket.

Zip the contents of the `thumbnail-s3-lambda`.  Upload the zip file to the lambda function.

### Improvements
1. Add logging.  Eg. post the log messages to loggly