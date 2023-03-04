AWS - Development-CLI-SDK
-----------------------------------------------------------------------------------------------------------------------------------------------------------

Assuming that you have your access-key and secret key. and the local os has the 'aws configure' executed. Following are few useful CLI commands to perform
tasks using the CLI (without even logging in to the Management Console)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
S3 - CLI

-----------------------------------------------------------------------------------------------------------------------------------------------------------

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: ls  :   The ls command is used to list the buckets or the contents of the buckets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   List existing S3 buckets on your account
    Command :   aws s3 ls

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    */
    ***********************************************************************************************************************************

    SCN#02  :   List all the files inside a S3 bucket
    Command :   aws s3 ls s3://samarth-ashish-aws-developer-021223
    Syntax  :   aws s3 ls s3://<bucket-name>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 20:46:49          6 Test-File.txt.txt
    */
    ***********************************************************************************************************************************

    SCN#03  :   List the contents of child directory in a S3 Bucket
    Command :   aws s3 ls s3://samarth-ashish-aws-developer-021223/my_multi_upload/
    Syntax  :   aws s3 ls s3://<bucket_name>/<child_dir_name>/
    Note    :   a '/' is needed at the end, otherwise, S3 will only show the result as the child directory instead of the files inside it

    /*
    C:\Users\samarth\Downloads>aws s3 ls s3://samarth-ashish-aws-developer-021223/my_multi_upload/
    2023-02-15 06:32:41          1 1.txt
    2023-02-15 06:32:41          1 2.txt
    2023-02-15 06:32:41          1 3.txt
    */

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: cp  :   The cp command simply copies the data to and from S3 buckets. It can be used to copy files from local to S3, 
            from S3 to local, and between two S3 buckets. There are a lot of other parameters that you can supply with the commands.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Copy a single file from local directory to S3 bucket
    command :   aws s3 cp Test-File.txt s3://samarth-ashish-aws-developer-021223
    Syntax  :   aws s3 cp <local_file_name_in_current_dir> s3://<bucket-name>

    /*
    C:\Users\samarth\Downloads\aws s3 cp Test-File.txt.txt s3://samarth-ashish-aws-developer-021223
    2023-02-14 20:46:49          6 Test-File.txt.txt
    */
    ***********************************************************************************************************************************

    SCN#02  :   Copy all files from local directory to S3 bucket
    Command :   aws s3 cp . s3://samarth-ashish-aws-developer-021223 --recursive
    Syntax  :   aws s3 cp <current_directory> s3://<bucket_name> --recursive

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 cp . s3://samarth-ashish-aws-developer-021223 --recursive
    upload: .\3.txt to s3://samarth-ashish-aws-developer-021223/3.txt
    upload: .\1.txt to s3://samarth-ashish-aws-developer-021223/1.txt
    upload: .\2.txt to s3://samarth-ashish-aws-developer-021223/2.txt
    */
    ***********************************************************************************************************************************

    SCN#03  :   Copy a directory (having multiple files) to a S3 Bucket in a sub-directory
    Command :   aws s3 cp my_multi_upload s3://samarth-ashish-aws-developer-021223/my_multi_upload --recursive
    Syntax  :   aws s3 cp <local_folder_name_to_be_uploaded> s3://<bucket_name>/<new_folder_name> --recursive

    /*
    C:\Users\samarth\Downloads>aws s3 cp my_multi_upload s3://samarth-ashish-aws-developer-021223/my_multi_upload --recursive
    upload: my_multi_upload\3.txt to s3://samarth-ashish-aws-developer-021223/my_multi_upload/3.txt
    upload: my_multi_upload\1.txt to s3://samarth-ashish-aws-developer-021223/my_multi_upload/1.txt
    upload: my_multi_upload\2.txt to s3://samarth-ashish-aws-developer-021223/my_multi_upload/2.txt 
    */
    ***********************************************************************************************************************************

    SCN#04  :   Copy a single file from local directory to S3 bucket - IA (infrequent Access)
    Command :   aws s3 cp file_name.txt s3://bucket_name/file_name_2.txt --storage-class STANDARD_IA 
    ***********************************************************************************************************************************

    SCN#05  :   Copy data between s3 buckets
    Command :   aws s3 cp s3://samarth-ashish-aws-developer-021223/5.txt s3://samarth-ashish-aws-developer-021523
    Syntax  :   aws s3 cp s3://<bucket_name_1>/<file_to_be_copied_over> s3://<bucket_name_2>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    2023-02-15 07:05:06 samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-15 07:10:21          1 1.txt
    2023-02-15 07:10:21          1 2.txt
    2023-02-15 07:10:21          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 cp s3://samarth-ashish-aws-developer-021223/5.txt s3://samarth-ashish-aws-developer-021523
    copy: s3://samarth-ashish-aws-developer-021223/5.txt to s3://samarth-ashish-aws-developer-021523/5.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021523
    2023-02-15 07:11:37          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    */


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: mv  :   The mv command simply moves the data to and from S3 buckets. Just like the cp command, mv command is used to move data 
            from local to S3, S3 to local, or between two S3 buckets.
            The only difference between the mv and the cp command is that when using the mv command the file is deleted from the 
            source. AWS moves this file to the destination. There are a lot of options that you can specify with the command
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Move a specific file from local storage to s3 bucket
    Command :   aws s3 mv 3.txt s3://samarth-ashish-aws-developer-021223/
    Syntax  :   aws s3 mv <local_file_name> s3://<bucket_name>/
    Note    :   The difference between 'cp' and 'mv' is: mv will delete the file from the source and place it in s3 bucket, while cp 
                does not delete the file from the source

    /*
    C:\Users\samarth\Downloads\my_multi_upload>dir
    Volume in drive C has no label.
    Volume Serial Number is 00AF-4A73

    Directory of C:\Users\samarth\Downloads\my_multi_upload

    02/14/2023  08:50 PM    <DIR>          .
    02/14/2023  08:50 PM    <DIR>          ..
    02/14/2023  08:51 PM                 1 1.txt
    02/14/2023  08:51 PM                 1 2.txt
    02/14/2023  08:51 PM                 1 3.txt
                3 File(s)              3 bytes
                2 Dir(s)  409,548,005,376 bytes free

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 mv 3.txt s3://samarth-ashish-aws-developer-021223/
    move: .\3.txt to s3://samarth-ashish-aws-developer-021223/3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>dir
    Volume in drive C has no label.
    Volume Serial Number is 00AF-4A73

    Directory of C:\Users\samarth\Downloads\my_multi_upload

    02/15/2023  06:49 AM    <DIR>          .
    02/15/2023  06:49 AM    <DIR>          ..
    02/14/2023  08:51 PM                 1 1.txt
    02/14/2023  08:51 PM                 1 2.txt
                2 File(s)              2 bytes
                2 Dir(s)  409,547,026,432 bytes free

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-15 06:49:01          1 3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    */
    ***********************************************************************************************************************************

    SCN#02  :   Move a specific file from s3 bucket to local storage
    Command :   aws s3 mv s3://samarth-ashish-aws-developer-021223/3.txt 5.txt
    Syntax  :   aws s3 mv s3://<bucket_name>/<s3_file_name> <new_file_name>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>dir
    Volume in drive C has no label.
    Volume Serial Number is 00AF-4A73

    Directory of C:\Users\samarth\Downloads\my_multi_upload

    02/15/2023  06:49 AM    <DIR>          .
    02/15/2023  06:49 AM    <DIR>          ..
    02/14/2023  08:51 PM                 1 1.txt
    02/14/2023  08:51 PM                 1 2.txt
                2 File(s)              2 bytes
                2 Dir(s)  409,545,854,976 bytes free

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-15 06:49:01          1 3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 mv s3://samarth-ashish-aws-developer-021223/3.txt 5.txt
    move: s3://samarth-ashish-aws-developer-021223/3.txt to .\5.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>dir
    Volume in drive C has no label.
    Volume Serial Number is 00AF-4A73

    Directory of C:\Users\samarth\Downloads\my_multi_upload

    02/15/2023  06:55 AM    <DIR>          .
    02/15/2023  06:55 AM    <DIR>          ..
    02/14/2023  08:51 PM                 1 1.txt
    02/14/2023  08:51 PM                 1 2.txt
    02/15/2023  06:49 AM                 1 5.txt
                3 File(s)              3 bytes
                2 Dir(s)  409,545,535,488 bytes free

    C:\Users\samarth\Downloads\my_multi_upload>
    */
    ***********************************************************************************************************************************

    SCN#03  :   Move a specific file from one S3 bucket to another s3 bucket
    Command :   aws s3 mv s3://samarth-ashish-aws-developer-021223/2.txt s3://samarth-ashish-aws-developer-021523
    Syntax  :   aws s3 mv s3://<bucket_name_1>/<file_name_to_be_moved> s3://<bucket_name_2>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    2023-02-15 07:05:06 samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-15 07:10:21          1 1.txt
    2023-02-15 07:10:21          1 2.txt
    2023-02-15 07:10:21          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021523
    2023-02-15 07:11:37          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>
    aws s3 mv s3://samarth-ashish-aws-developer-021223/2.txt s3://samarth-ashish-aws-developer-021523
    
    move: s3://samarth-ashish-aws-developer-021223/2.txt to s3://samarth-ashish-aws-developer-021523/2.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-15 07:10:21          1 1.txt
    2023-02-15 07:10:21          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021523
    2023-02-15 07:14:19          1 2.txt
    2023-02-15 07:11:37          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    */
    ***********************************************************************************************************************************

    SCN#04  :   Move a specific file from local to s3 bucket -IA (Infrequent Access)
    Command :   aws s3 mv file_name.txt s3://bucket_name/file_name_2.txt --storage-class STANDARD_IA 


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: rm  :   The rm command is simply used to delete the objects in S3 buckets. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Remove a single file from S3 bucket
    Command :   aws s3 rm s3://samarth-ashish-aws-developer-021223/Test-File.txt.txt
    Syntax  :   aws s3 rm s3://<bucket_name>/file_name

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rm s3://samarth-ashish-aws-developer-021223/Test-File.txt.txt
    delete: s3://samarth-ashish-aws-developer-021223/Test-File.txt.txt
    */
    ***********************************************************************************************************************************

    SCN#02  :   Remove all files from the S3 bucket
    Command :   aws s3 rm s3://samarth-ashish-aws-developer-021223/ --recursive
    Syntax  :   aws s3 rm s3://<bucket_name> --recursive

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rm s3://samarth-ashish-aws-developer-021223/ --recursive
    delete: s3://samarth-ashish-aws-developer-021223/1.txt
    delete: s3://samarth-ashish-aws-developer-021223/2.txt
    delete: s3://samarth-ashish-aws-developer-021223/3.txt
    */
    ***********************************************************************************************************************************

    SCN#03  :   Remove specific files from the S3 bucket
    Command :   aws s3 rm s3://samarth-ashish-aws-developer-021223/ --recursive --exclude "3.txt"
    Syntax  :   aws s3 rm s3://<bucket_name> --recursive --exclude "Filename-You-Wish-do-not-delete"

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 21:14:23          1 1.txt
    2023-02-14 21:14:23          1 2.txt
    2023-02-14 21:14:23          1 3.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rm s3://samarth-ashish-aws-developer-021223/ --recursive --exclude "3.txt"
    delete: s3://samarth-ashish-aws-developer-021223/1.txt
    delete: s3://samarth-ashish-aws-developer-021223/2.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 21:14:23          1 3.txt
    */

    Command :   aws s3 rm s3://samarth-ashish-aws-developer-021223 --recursive --include "1.txt" --include "2.txt" --exclude "3.txt"
    Syntax  :   aws s3 rm s3://<bucket_name> --recursive --include "Filename-you-wish-to-delete" --exclude "Filename-you-wish-to-not-delete"

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 21:22:52          1 1.txt
    2023-02-14 21:22:52          1 2.txt
    2023-02-14 21:22:52          1 3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rm s3://samarth-ashish-aws-developer-021223 --recursive --include "1.txt" --include "2.txt" --exclude "3.txt"
    delete: s3://samarth-ashish-aws-developer-021223/1.txt
    delete: s3://samarth-ashish-aws-developer-021223/2.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 21:22:52          1 3.txt
    */
    ***********************************************************************************************************************************

    SCN#04  :   Empty a S3 bucket
    Command :   aws s3 rm s3://samarth-ashish-aws-developer-021223 --recursive
    Syntax  :   aws s3 rm s3://<bucket_name> --recursive

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223
    2023-02-14 21:22:52          1 3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rm s3://samarth-ashish-aws-developer-021223 --recursive
    delete: s3://samarth-ashish-aws-developer-021223/3.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls s3://samarth-ashish-aws-developer-021223

    C:\Users\samarth\Downloads\my_multi_upload>
    */
    ***********************************************************************************************************************************
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: mb  :   The mb command is simply used to create new S3 buckets. This is a fairly simple command but to create new buckets, 
            the name of the new bucket should be unique across all the S3 buckets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Create a new bucket in S3
    Command :   aws s3 mb s3://samarth-ashish-aws-developer-021523
    Syntax  :   aws s3 mb s3://<new_bucket_name>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 mb s3://samarth-ashish-aws-developer-021523
    make_bucket: samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    2023-02-15 07:05:06 samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    */

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: rb  :   The rb command is simply used to delete S3 buckets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Remove a s3 bucket
    Command :   aws s3 rb s3://samarth-ashish-aws-developer-021523              [If the bucket is empty]
    Syntax  :   aws s3 rb s3://<bucket_name_to_be_deleted>

    Command :   aws s3 rb s3://samarth-ashish-aws-developer-021523 --force      [If the bucket is not empty]
    Syntax  :   aws s3 rb s3://<bucket_name_to_be_deleted> --force

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    2023-02-15 07:05:06 samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rb s3://samarth-ashish-aws-developer-021523
    remove_bucket failed: s3://samarth-ashish-aws-developer-021523 An error occurred (BucketNotEmpty) when calling the DeleteBucket operation: 
                        The bucket you tried to delete is not empty

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 rb s3://samarth-ashish-aws-developer-021523 --force
    delete: s3://samarth-ashish-aws-developer-021523/1.txt
    delete: s3://samarth-ashish-aws-developer-021523/5.txt
    delete: s3://samarth-ashish-aws-developer-021523/2.txt
    remove_bucket: samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223

    C:\Users\samarth\Downloads\my_multi_upload>
    */

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: sync    :   The sync command copies and updates files from the source to the destination just like the cp command. 
                It is important that we understand the difference between the cp and the sync command. When you use cp 
                it copies data from source to destination even if the data already exists in the destination.
                It will also not delete files from the destination if they are deleted from the source. However, sync looks 
                at the destination before copying your data and only copies the new and updated files. The sync command is 
                similar to committing and pushing changes to a remote branch in git. The sync command offers a lot of 
                options to customize the command. 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Sync files between two s3 buckets
    Command :   aws s3 sync s3://samarth-ashish-aws-developer-021223 s3://samarth-ashish-aws-developer-021523
    Syntax  :   aws s3 sync s3://<source_bucket_name> s3://<target_bucket_name>

    /*
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls
    2023-02-12 18:59:47 samarth-ashish-aws-developer-021223
    2023-02-15 07:05:06 samarth-ashish-aws-developer-021523

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls samarth-ashish-aws-developer-021223
    2023-02-15 07:10:21          1 1.txt
    2023-02-15 07:10:21          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls samarth-ashish-aws-developer-021523
    2023-02-15 07:14:19          1 2.txt
    2023-02-15 07:11:37          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws 
    s3 sync s3://samarth-ashish-aws-developer-021223 s3://samarth-ashish-aws-developer-021523
    
    copy: s3://samarth-ashish-aws-developer-021223/1.txt to s3://samarth-ashish-aws-developer-021523/1.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls samarth-ashish-aws-developer-021523
    2023-02-15 07:38:04          1 1.txt
    2023-02-15 07:14:19          1 2.txt
    2023-02-15 07:11:37          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>aws s3 ls samarth-ashish-aws-developer-021223
    2023-02-15 07:10:21          1 1.txt
    2023-02-15 07:10:21          1 5.txt

    C:\Users\samarth\Downloads\my_multi_upload>
    */ 

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: presign :   The presign command generates a pre-signed URL for a key in the S3 bucket. You can use this command to generate URLs 
                that can be used by others to access a file in the specified S3 bucket key.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Generate a pre-signed url
    Command :   aws s3 presign s3://bucket_name/samplePrefix/file_name.png --expires-in 3600
    
    /*
    Sample Output:
    Output:
    https://s3.ap-south-1.amazonaws.com/bucket_name/samplePrefix/file_name.png?
    X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIA4MCZT73PAX7ZMVFW%2F20220314%2Fap-south-1%2Fs3%2Faws4_request&X-Amz-Date=20220314T054113Z&X-Amz-Expires=3600
    &X-Amz-SignedHeaders=host&X-Amz-Signature=f14608bbf3e1f9f8d215eb5b439b87e167b1055bcd7a45c13a33debd3db1be96
    */

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: website:    The website command is used to configure the S3 static website hosting for your bucket.
                You specify the index and the error files and the S3 gives you a URL where you can view the file
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    SCN#01  :   Configure a static webssite
    Command :   aws s3 website s3://bucket_name --index-document index.html --error-document error.html


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
s3: MFA-Delete:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    MFA [Multi Factor Authentication] forces user to generate a code on a device (usually a mobile phone or hardware) before doing 
    import operations on S3

    To use MFA-Delete, enable versioning on the S3 bucket
    You will need MFA to
        a.  Permanently delete an object version
        b.  suspend versioning on the bucket
    
    You wont need MFA for
        a.  enabling versioning
        b.  listing deleted versions
    
    Only the bucket owner (root account) can enable / disable MFA-Delete
    MFA-Delete currently can only be enabled using the CLI, and the pre-requisite it to have MFA Device configured on your 
    account (under IAM)

-----------------------------------------------------------------------------------------------------------------------------------------------------------
STS - CLI
-----------------------------------------------------------------------------------------------------------------------------------------------------------
STS: Security Token Service

AWS STS is an AWS service that allows you to request temporary security credentials for your AWS resources, for IAM authenticated users and users that are 
authenticated in AWS such as federated users via OpenID or SAML2.0
You use STS to provide trusted users with temporary access to resources via API calls, your AWS console or the AWS command line interface (CLI)
The temporary security credentials work exactly like regular long term security access key credentials allocated to IAM users only the lifecycle of the access 
credentials is shorter.

Typically an application will make an API request to AWS STS endpoint for credentials, these access keys are not stored with the user, they are instead 
dynamically generated by STS when the request is made. The STS generated credentials will expire at which point the user can request new ones as long as they 
still have permission to do so.

Once the generated credentials expire they cannot be reused which reduces the risk of having your resource access compromised and removes the need to embed 
security tokens within your code. The STS token lifecycle is determined by you and can be anywhere from 15 minutes to 36 hours

AWS STS security tokens are typically used for identity federation, providing cross-account access and for resources related to EC2 instances that require access 
by other applications

Usage on CLI:
Scenario: If you run a command on the CLI which generates and error with an encoded failure message, we can use STS to decode that message
Command : aws sts decode-authorization-message -encoded-message <paste your encoded message here>

-----------------------------------------------------------------------------------------------------------------------------------------------------------
EC2 Instance Metadata - CLI
-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS EC2 instance metadata allows EC2 instance to 'learn about themselves' without using an IAM role for that purpose. The URL for the metadata endpoint is
http://169.254.169.254/latest/meta-data/ and it only works from inside the ec2 instance.

Note: You can retrieve the IAM role name from the metadata, but you cannot retrieve the IAM policy.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
EC2 :   Metadata    :   Check all available options via meta-data api
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/
    ami-id
    ami-launch-index
    ami-manifest-path
    block-device-mapping/
    events/
    hibernation/
    hostname
    iam/
    identity-credentials/
    instance-action
    instance-id
    instance-life-cycle
    instance-type
    local-hostname
    local-ipv4
    mac
    managed-ssh-keys/
    metrics/
    network/
    placement/
    profile
    public-hostname
    public-ipv4
    public-keys/
    reservation-id
    security-groups
    services/
    system[ec2-user@ip-172-31-62-238 ~]$

    ***********************************************************************************************************************************
    SCN#01  :   Get Hostname for the EC2 Instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/hostname; echo -e "\n"
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /* 
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/hostname; echo -e "\n"
    ip-172-31-62-238.ec2.internal
    */

    ***********************************************************************************************************************************
    SCN#02  :   Get Security-Groups for the EC2 Instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/security-groups; echo -e "\n"
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /*
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/security-groups; echo -e "\n"
    Public-Access-HTTP-80-Inbound-EC2
    launch-wizard-1
    */

    The output indicates, that this particular EC2 instance, has two security groups attached to it.

    ***********************************************************************************************************************************
    SCN#03  :   Get Instance-Type for the EC2 Instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/instance-type; echo -e "\n"
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /*
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/instance-type; echo -e "\n"
    t2.micro
    */

    ***********************************************************************************************************************************
    SCN#04  :   Get IAM permissions details for the EC2 Instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/iam/info; echo -e "\n"
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /*
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/iam; echo -e "\n"
    info
    security-credentials/

    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/iam/info; echo -e "\n"
    {
    "Code" : "Success",
    "LastUpdated" : "2023-02-16T11:56:17Z",
    "InstanceProfileArn" : "arn:aws:iam::494645329569:instance-profile/IAM-Role-EC2-Full-Access",
    "InstanceProfileId" : "AIPAXGKUU6GH4SLA3BKEV"
    }

    [ec2-user@ip-172-31-62-238 ~]$
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/iam/security-credentials; echo -e "\n"
    IAM-Role-EC2-Full-Access
    */

    ***********************************************************************************************************************************
    SCN#05  :   Get Private IP address of the EC2 instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/local-ipv4; echo -e "\n"
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /*
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/local-ipv4; echo -e "\n"
    172.31.62.238
    */

    ***********************************************************************************************************************************
    SCN#06  :   Get Instance-Id of the EC2 instance using the metadata service
    Command :   curl http://169.254.169.254/latest/meta-data/instance-id; echo -e "\n"   
    Syntax  :   curl <meta-data-url>/<api_name> ; echo <new-line-character>

    /*
    [ec2-user@ip-172-31-62-238 ~]$ curl http://169.254.169.254/latest/meta-data/instance-id; echo -e "\n"
    i-0b4ee75b7d98b93c7
    */

-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS : Configure Multiple Profiles
-----------------------------------------------------------------------------------------------------------------------------------------------------------
If you are user, that manages multiple AWS accounts and would need to run CLI operations for these different accounts, its better to have a different profile
usually, if we configure AWS CLI on local machine we run the following

    aws configure

    Then we have to provide
        a.  AWS Access Key ID
        b.  AWS Secret Access Key
        c.  Default region name
        d.  Default output format

When this is done, it CREATES two files having the following data with [default entries]

    File#1: Credentials
    Content:
        [default]
        aws_aceess_key_id = <some_value>
        aws_secret_access_key = <some_value>
    
    File#2: config
    Content:
        [default]
        region = <some_value>

Now; if you manage different accounts, you should be able to manage this other account (which is not the default account). For this to be done, you need to
configure this account (using a profile, so that the profile is loaded everytime you use this other account). To configure, run the following

    aws configure --profile <whatever-you-want-to-name-this-profile>

    Then we have to provide
        a.  AWS Access Key ID
        b.  AWS Secret Access Key
        c.  Default region name
        d.  Default output format

When this is done, it MODIFIES two files having the following data with [default entries] with additional data for the new profile

    File#1: Credentials
    Content:
        [default]
        aws_aceess_key_id = <some_value>
        aws_secret_access_key = <some_value>
        [whatever-you-want-to-name-this-profile]
        aws_aceess_key_id = <some_value>
        aws_secret_access_key = <some_value>        
    
    File#2: config
    Content:
        [default]
        region = <some_value>
        [whatever-you-want-to-name-this-profile]
        region = <some_value>
    
Practical Usage:

    a.  If you run 'aws s3 ls' ; this will run against the [default] profile and list the S3 buckets in that default profile
    b.  If you run 'aws s3 ls --profile <whatever-you-want-to-name-this-profile> ; this will run against the 
        <whatever-you-want-to-name-this-profile> profile

This way you can run any command, against the default profile or a specific profile

-----------------------------------------------------------------------------------------------------------------------------------------------------------
MFA : CLI
-----------------------------------------------------------------------------------------------------------------------------------------------------------
To use MFA with the CLI, you must create a temporary session
To do so, you must run the STS GetSession Token API call

aws sts get-session-token --serial-number arn-of-the-mfa-device --token-code code-from-token --duration-seconds 3600

{
    "Credentials": {
        "SecretAccessKey": "secret-access-key",
        "SessionToken" : "temporary-session-token",
        "Expiration": "expiration-date-time",
        "AccessKeyId": "access-key-id"
    }
}

-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS :   LIMITS (Quotas)
-----------------------------------------------------------------------------------------------------------------------------------------------------------
API Rate LIMITS

    a.  DescribeInstance API for EC2 has a limit of 100 calls per seconds
    b.  GetObject on S3 has a limit of 5500 GET per second per samplePrefix
    c.  For intermittent errors: Implement Exponential BackOff
    d.  For consistent errors: Request an API throttling limit increase

Service Quota (Service Limits)

    a.  Running On-Demand standard Instance: 1152 VCPUs

Exponential Backoff:

    Exponential backoff is an algorithm that uses feedback to multiplicatively decrease the rate of some process, in order to 
    gradually find an acceptable rate. These algorithms find usage in a wide range of systems and processes, with radio networks 
    and computer networks being particularly notable

        For e.g.: If you are running an API call against an api and it responds back with a 5XX response code.
        Then instead of try every second, which will quickly hit the API limit on AWS, with every retry you double the time to wait
            1st Retry:  After 2 seconds
            2nd Retry:  After 4 seconds
            3rd Retry:  After 8 seconds
            4th Retry:  After 16 seconds
            5th Retry:  After 32 seconds

        So that
            a.  You are not bombarding the API even when its not responding
            b.  Managing the API rate limit in a better way to not exhaust the limit

    ************************************************************************************************************************************
    SCN#01  :   When to use Exponential Backoff (any AWS service)
    Response:   If you get 'ThrottlingException' intermittently then you should use Exponential BackOff.
        If you are using AWS SDK, then the retry mechanism is already included in the AWS SDK API calls. However if you are using AWS API 
        then you must implement the exponential backoff

    Exam Question   :   Which type of errors should you retry for an exponential backoff?
    Answer          :   Retries must be only implemented for 5xx errors and Throttling. You SHOULD not use retry or exponential back 
                        on of 4xx client errors

-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS :   CLI Credentials Provider Chain
-----------------------------------------------------------------------------------------------------------------------------------------------------------

    Following is the priority order for CLI to look for Credentials
    1st priority    :   Command Line options            :   --region; --output; --profile
    2nd priority    :   Environment Variables           :   AWS_ACCESS_KEY; AWS_SECRET_KEY; AWS_SESSION_TOKEN
    3rd priority    :   CLI credentials file            :   ~/.aws/credentials : on Linux & Mac
                                                            C:\Users\user\.aws\credentials  :   on Windows
    4th priority    :   CLI configuration file          :   ~/.aws/config   :   on Linix & Mac
                                                            C:\Users\USERNAME\.aws\config   :   on Windows
    5th priority    :   Container Credentials           :   For ECS tasks
    6th priority    :   Instance Profile Credentials    :   For EC2 Instance Profiles


Consider the Following Scenario:

An application deployed on an EC2 isntance is using environment variables with credentials from an IAM user to call the S3 API
The IAM user has S3FullAccess permissions.
The application only uses one S3 bucket, so according to best practices:

    a.  An IAM Role & EC2 instance profile was created for the EC2 instance
    b.  The role was assigned the minimum permissions to access that one S3 bucket

Question:   The IAM instance profile was assigned to the EC2 instance, but it still had access to all S3 buckets, Why?

    This happened because, the credentials chain is still giving priorities to the environment variables. To deal with this 
    scenario, you have to unset the environment variables, and then the IAM instance profile will become the only active 
    priority in the credentials chain and the issue will be fixed


    BEST Practices:
        a.  Never store your credentials in the code
        b.  Credentials must be inherited from the credentials chain
        c.  Use IAM roles as much as possible
            1.  EC2 roles for EC2 instances
            2.  ECS roles for ECS tasks
            3.  Lambda roles for lambda functions
        d.  If working outside of AWS, use environment variables / named profiles

-----------------------------------------------------------------------------------------------------------------------------------------------------------
AWS : Signing API Requests
-----------------------------------------------------------------------------------------------------------------------------------------------------------

When you call the AWS http API, you sign the request so that AWS can identify you, using your AWS credentials (access key & secret key)
If you use SDK or CLI, the HTTP requests are signed for you

Note: Some requests to S3 dont need to be signed

You should sign an AWS HTTP request using Signature V4 (SigV4)

SigV4 Request Examples:

    a.  Using HTTP header option (Visible under browser network logs or postman console etc)
    b.  Query String option (e.g.: S3 pre-signed URLs)
