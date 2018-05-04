## Deploying website into ec2 from s3 bucket.

my bucket name is : s3://arjun-testing

### -  Put your complete webpages inside your bucket(s3://arjun-testing)

### -  DO NOT make your bucket public.

### -  Create an IAM role called 'deploy-from-s3'

### - Assign amazonS3readonly policy to 'deploy-from-s3'

### - Create Ec2 instance with the following userdata.

```
#!/bin/bash
yum update -y
yum install httpd24 php55 mysql-server -y
service httpd restart
service mysqld restart
chkconfig httpd on
chkconfig mysqld on
aws s3 cp --recursive s3://BUCKET-NAME  /var/www/html/
```


Above script can be found in the >> bootstrap-instruction.txt <<
