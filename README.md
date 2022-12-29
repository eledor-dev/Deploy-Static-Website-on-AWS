# Deploy-Static-Website-on-AWS
This guides you to hosting a Static Website on AWS and distributing it using CloudFront.

## Pre-requesites
 * AWS Account.
 * A Starter code base (Clone ["Starter Code"](https://github.com/eledor-dev/Static-Web-Starter-Code) here)

## STEP 1

<br>

 *  Create an S3 bucket

    1. Navigate to the AWS Console Management and search "S3" in the service find box and select "S3"

    <br>

    !["S3-Nav"](./Assets/s3-Nav.png "S3-Nav")

    <br>

    2.  On the S3 Dashboard, Select "create bucket"
    
    <br>

    !["S3-create"](/Assets/s3-create.png "S3-create")

    <br>

    3. In the General configuration, enter a “Bucket name” and a region of your choice. Note: Bucket names must be globally  unique.
    
    <br>

    !["S3-create1"](/Assets/s3-create1.png "S3-create1")

    <br>
    
    4. In the Bucket settings for Block Public Access section, uncheck the “Block all public access”. It will enable the public access to the bucket objects via the S3 object URL.

       <br>

          Note - We are allowing the public access to the bucket contents because we are going to host a static website in this bucket. Hosting requires the content should be publicly readable.
    
    !["S3-create2"](./Assets/s3-create2.png "S3-create2")

    5. Click “Create bucket”.
    
    6. Once the bucket is created, click on the name of the bucket to open the bucket to the contents.

   <br>

## STEP 2

<br>

 * Upload files to the S3 bucket

    1. Once the bucket is open to its contents, click the “Upload” button.
        
    2. Click the "Add files" and “Add folder” button, and upload the ["Starter Code"](https://github.com/eledor-dev/Static-Web-Starter-Code) folder content from your local computer to the S3 bucket.

    <br>
    
    !["S3-upload"](./Assets/s3-upload.png "S3-upload")

    <br>

        Click "Add files" to upload the index.html file, and click "Add folder" to upload the css, img, and vendor folders.
    <br>

## STEP 3

<br>

 * Secure the bucket via IAM

    1. Click on the “Permissions” tab.

    <br>

    !["S3-secure"](./Assets/s3-secure.png "S3-secure")

    <br>
            Go to the Permissions tab. See that the bucket allows public access for hosting.

    <br>

    2. The “Bucket Policy” section shows it is empty. Click on the Edit button.

     <br>

    !["S3-policy"](./Assets/s3-policy.png "S3-policy")

    <br>
    3. Enter the following bucket policy replacing your-website with the name of your bucket and click “Save”.

    ```
        {
        "Version":"2012-10-17",
        "Statement":[
        {
        "Sid":"AddPerm",
        "Effect":"Allow",
        "Principal": "*",
        "Action":["s3:GetObject"],
        "Resource":["arn:aws:s3:::your-website/*"]
         }
        ]
        }
    ```
            You will see warnings about making your bucket public, but this step is required for static website hosting.
    
## STEP 4
 * Configure the S3 bucket
## STEP 5
 * Distribute Website via CloudFront
## STEP 6
 * Access the Website in your Web Browser