# AWS_Disaster_recovery_setup

Login AWS console and search service AWS Disaster Recovery

![image](https://user-images.githubusercontent.com/85988020/183416652-52d1a074-4219-4152-8ca4-37a64a0458dc.png)

choose here replication-server subnet and Replication server instance type which you want. you can also choose cross region vpc but failback is not possible in this only failover is possible.

![image](https://user-images.githubusercontent.com/85988020/183418118-98dddf93-fd86-4e5c-807f-6f302b464b00.png)

now click on next

here you have to select volumes whatever volumes you want according to your source instance.
if you choose low then changes will be fast but the slow in replication-server as per your choice.

![image](https://user-images.githubusercontent.com/85988020/183418717-61a39ace-0e7a-4240-93fe-d250b16cd10d.png)

here you can choose encryption type

![image](https://user-images.githubusercontent.com/85988020/183419194-2f6fb352-5c5a-42e9-a3fb-df24a4a25d44.png)

you can attach security groups or leave to aws as well

![image](https://user-images.githubusercontent.com/85988020/185546666-38c21c70-e42b-44d3-b35a-92bb51d665a5.png)

## please keep in mind before choosing security group:

![image](https://user-images.githubusercontent.com/85988020/185546988-8a7b19bf-3524-4d79-8772-b25a4a1903ad.png)

![image](https://user-images.githubusercontent.com/85988020/183419366-784b1b09-f372-4f23-9910-95d13b3e2c92.png)

by checking this box you can decide data transfer speed

![image](https://user-images.githubusercontent.com/85988020/183419567-026009d8-b66d-4582-96b0-67f622ed53be.png)

by clicking this you can more secure using pvt.ip

![image](https://user-images.githubusercontent.com/85988020/183419832-c205b09a-c584-4894-be75-d2e605beed3e.png)

here you can choose retentation period

![image](https://user-images.githubusercontent.com/85988020/183420031-d89393a6-963a-454d-b7c4-b2000b3010b5.png)

take a review and create

![image](https://user-images.githubusercontent.com/85988020/183420270-74b7cea7-5c2c-40fe-b202-48debe078042.png)

after creating you can change settings anytime you want 

![image](https://user-images.githubusercontent.com/85988020/183420508-2604ba51-8839-4337-9354-b2a3f80c994a.png)

you have to create an IAM user and attach permission also:

![image](https://user-images.githubusercontent.com/85988020/183421092-75615bad-e5b4-4a4d-987c-e600a7fe3a78.png)

login into source server and install the agent:

wget -O ./aws-replication-installer-init.py https://aws-elastic-disaster-recovery-us-east-1.s3.us-east-1.amazonaws.com/latest/linux/aws-replication-installer-init.py

sudo python3 aws-replication-installer-init.py

give region-name access-key and secret-access-key 

it ask choose the disks you want to replicate: choose yes

after that go to the aws-disaster-recovery-console > source server and check 

![image](https://user-images.githubusercontent.com/85988020/183422692-96af04cd-3f37-43d8-aeeb-6dab3d03db41.png)

here you can see the replication progress

![image](https://user-images.githubusercontent.com/85988020/183422855-84cde75e-b640-4d23-8590-44cf4c12867a.png)

here you can see the server:

![image](https://user-images.githubusercontent.com/85988020/183423045-35aa30cf-4dde-4eb4-8eaa-2275d52f94e9.png)

in launch setting if we choose on then aws will decide what type of instance 

![image](https://user-images.githubusercontent.com/85988020/183423694-415df5b8-9757-423c-9779-dcfcfa5368e0.png)

after waiting few minutes source server will be in ready state

![image](https://user-images.githubusercontent.com/85988020/183424360-63e9c99e-a11b-4082-b08f-6ea7da1d937b.png)

once we initiating a drill. it should launch an ec2 isntance for this we have to create a launch template

![image](https://user-images.githubusercontent.com/85988020/183424795-f077aedb-c850-4bae-8f49-a11d9c25123a.png)

![image](https://user-images.githubusercontent.com/85988020/183424929-f08bc196-89ea-43d2-9714-3b350daebdef.png)

choose any subnets for recovery 

![image](https://user-images.githubusercontent.com/85988020/183425091-6eed9eee-4581-425e-9ead-af92405f3df4.png)

be caerful don't do any changes in storage part this is very critical, then click on creating launch tempalte

source server is in ready state if you want to test it go with drill otherwise choose other option

when we go with other option it ask for snapshot date select one and cick on intiate recovery

![image](https://user-images.githubusercontent.com/85988020/183425974-4f9f65ae-5218-4f89-afdc-68337caa67ca.png)

here you can see conversion server created by aws 

![image](https://user-images.githubusercontent.com/85988020/183426368-5755a026-43ec-433a-923b-c8656228ac34.png)

here you cans see recovery server 

![image](https://user-images.githubusercontent.com/85988020/183426964-d2c0c023-d0ef-43c8-aa1e-3712a1f9438e.png)

your aws console look like this 

![image](https://user-images.githubusercontent.com/85988020/183427586-be2fe0dd-954b-49a8-bfc2-e181652fa7f1.png)

Thank you!!!






