Step 1 - Create security group for elastic load balancer.

![IMG_9F63C94EE239-1](https://user-images.githubusercontent.com/93732510/155802594-61a63a31-6220-48a5-93c5-4a14ad877542.jpeg)

Step 2 - Create security group for tomcat EC2 instance.

![IMG_AF68B82EB44C-1](https://user-images.githubusercontent.com/93732510/155803587-9ae08ddf-3765-4397-889f-0bb65a19871d.jpeg)

Step 3 - Create a security group for the backend services (active MQ, RDS, Elastic search)

![IMG_4BE4E26DDC5A-1](https://user-images.githubusercontent.com/93732510/155803075-2ea76074-ab01-40a3-a1ac-ba92c68e51bb.jpeg)

Step 4 - Clone the source code and git check out into awsliftandshift directory.

![IMG_BA0F59838BB3-1](https://user-images.githubusercontent.com/93732510/155803715-a4388c3a-0439-44b9-840f-44becd502f04.jpeg)

Step 5 - Create a key pair 

![IMG_F458C7E44EBE-1](https://user-images.githubusercontent.com/93732510/155803956-3cdc39f1-5f15-4bf7-8743-ed02fd91fc8b.jpeg)

Step 6 - Open the bash script in sublime text to verify code accuracy

![IMG_F0373C3D473C-1](https://user-images.githubusercontent.com/93732510/155804231-a80e0da5-789b-453a-9b0f-30624c1e9f6b.jpeg)

Step 7 - Launch the backend EC2 instances first, copy the bash script from sublime text and paste in userdata box.

Step 8 - Connect to each of the backend instances to via ssh, switch to root user and check their status.

![IMG_9162](https://user-images.githubusercontent.com/93732510/155805042-283f03cb-dd5c-4df5-a06c-ac5e062510e0.jpg)

Step 9 - Setup Route 53 

![IMG_B6EF4A83C492-1](https://user-images.githubusercontent.com/93732510/155805363-00b3561c-8fb9-4d10-86b5-1756cc11aaa5.jpeg)

Step 10 -Create record for the Route 53 and add Private IP address for the three backend services.

Step 11 - Launch the EC2 instance for tomcat application server, copy its script from sublime text to paste in userdata box.

Step 12 - Open powershell to install JDk8 and Maven for build & deploy artifacts.

Step 13 - Update application.properties by going into resources directory and change db name as specified in Route 53.

![IMG_5F2F97CE5ABA-1](https://user-images.githubusercontent.com/93732510/155806294-17799bf9-eee4-44d0-9dc7-6be1a72c4323.jpeg)

Step 14 - Go to vprofile directory and install the artifacts in it using mvn install command.

![IMG_40EC898CFB42-1](https://user-images.githubusercontent.com/93732510/155806816-93d57403-ff0f-4b55-b600-7a65d3d3b0ee.jpeg)

Step 15 -Open powershell and install AWSCLI. This will enable us store the artifact in s3 bucket.

Step 16 - Create an access key in AWS IAM for the s3 bucket.

![IMG_18F0E252F3A1-1](https://user-images.githubusercontent.com/93732510/155807315-462aaec1-4379-4676-9523-049c41b7e70c.jpeg)

Step 17 - Configure AWS in git bash using command aws configure.

Step 18 - Create an s3 bucket in the command line.

![IMG_CE27D835683D-1](https://user-images.githubusercontent.com/93732510/155807628-7183852f-536f-4f0c-9b3a-c3310f0c4119.jpeg)

Step 19 - Copy the artifact in target directory and transfer into the s3 bucket created.

![IMG_59055B0DA2F6-1](https://user-images.githubusercontent.com/93732510/155807852-3f01c094-12e0-47af-901f-173fcf48fafe.jpeg)

Step 20 - Create a IAM role in order for tomcat EC2 instance to download the artifact from s3 bucket.

![IMG_FD41229571C9-1](https://user-images.githubusercontent.com/93732510/155808113-edb33bb1-00d6-4443-a7ed-cae8f9d6acf2.jpeg)

Step 21 - Log in to the tomcat EC 2 instance using ssh key.

![IMG_BFCCA57BA368-1](https://user-images.githubusercontent.com/93732510/155808435-035a4159-5ced-492a-9ecd-480fb34e392a.jpeg)

Step 22 - Create Target group and application load balancer.

![IMG_CC750A3278B8-1](https://user-images.githubusercontent.com/93732510/155808779-4637b2c9-5d4e-43dd-8ee1-da4a3c21061a.jpeg)

Step 23 - Create autoscaling for our EC2 instance.

![IMG_4DBFF57522DB-1](https://user-images.githubusercontent.com/93732510/155808860-12d57d56-a68f-4f37-a6e2-4b1120edbaaf.jpeg)

Step 24 - Finally, we can access the output via any broweser with the public IP address.

![IMG_7F38D14EB3C1-1](https://user-images.githubusercontent.com/93732510/155809149-dd05e587-5cd2-404c-b713-9eaad417121e.jpeg)

