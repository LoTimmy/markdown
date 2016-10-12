
最後更新： 2016-08-26         

![](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/images/overview_getting_started.png)

----------
### ec2-api-tools

```console
shell> brew cask install java
shell> brew install ec2-api-tools
shell> brew install ec2-ami-tools

shell> export AWS_ACCESS_KEY=your-aws-access-key-id
shell> export AWS_SECRET_KEY=your-aws-secret-key

shell> file /etc/alternatives/java
shell> export JAVA_HOME=/usr/lib/jvm/java-7-openjdk-armhf/jre
shell> $JAVA_HOME/bin/java -version
```

```
java version "1.7.0_75"
OpenJDK Runtime Environment (IcedTea 2.5.4) (7u75-2.5.4-1~deb7u1+rpi1)
OpenJDK Zero VM (build 24.75-b04, mixed mode)
```

```console
shell> export EC2_HOME=/usr/local/ec2/ec2-api-tools-1.7.1.1
shell> export PATH=$PATH:$EC2_HOME/bin
```
```console
shell> ec2-describe-regions
```

```
REGION	ap-south-1	ec2.ap-south-1.amazonaws.com
REGION	eu-west-1	ec2.eu-west-1.amazonaws.com
REGION	ap-southeast-1	ec2.ap-southeast-1.amazonaws.com
REGION	ap-southeast-2	ec2.ap-southeast-2.amazonaws.com
REGION	eu-central-1	ec2.eu-central-1.amazonaws.com
REGION	ap-northeast-2	ec2.ap-northeast-2.amazonaws.com
REGION	ap-northeast-1	ec2.ap-northeast-1.amazonaws.com
REGION	us-east-1	ec2.us-east-1.amazonaws.com
REGION	sa-east-1	ec2.sa-east-1.amazonaws.com
REGION	us-west-1	ec2.us-west-1.amazonaws.com
REGION	us-west-2	ec2.us-west-2.amazonaws.com
```

```
REGION	eu-central-1	 ec2.eu-central-1.amazonaws.com
REGION	sa-east-1	     ec2.sa-east-1.amazonaws.com
REGION	ap-northeast-1	 ec2.ap-northeast-1.amazonaws.com
REGION	eu-west-1	     ec2.eu-west-1.amazonaws.com
REGION	us-east-1	     ec2.us-east-1.amazonaws.com
REGION	us-west-1	     ec2.us-west-1.amazonaws.com
REGION	us-west-2	     ec2.us-west-2.amazonaws.com
REGION	ap-southeast-2	 ec2.ap-southeast-2.amazonaws.com
REGION	ap-southeast-1	 ec2.ap-southeast-1.amazonaws.com
```

```console
shell> export EC2_URL=https://<service_endpoint>  
shell> export EC2_URL=https://ec2.us-west-1.amazonaws.com
```

Create a Key Pair
```console
shell> ec2-create-keypair my-key-pair
```

```console
shell> ec2-create-group my-security-group -d "My security group"
shell> ec2-authorize my-security-group -p 3389 -s 203.0.113.25/32
shell> ec2-authorize my-security-group -p 22 -s 203.0.113.25/32

shell> ec2-create-group websrv -d "Web Servers"
shell> ec2-authorize websrv -P tcp -p 80 -s 192.0.2.0/24
shell> ec2-authorize websrv -P tcp -p 80 -s 0.0.0.0/0

shell> ec2-run-instances ami-xxxxxxxx -t t1.micro -k my-key-pair -g my-security-group

Ubuntu Server 14.04 LTS (HVM), SSD Volume Type
shell> ec2-run-instances ami-a7fdfee2 -t t2.micro -k my-key-pair -g my-security-group

shell> ec2-describe-instances
~~~~~~~~~~
Connecting to Your Linux Instance Using SSH
```console
shell> ssh -i my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com
shell> ssh -i my-key-pair.pem ubuntu@ec2-54-183-170-94.us-est-1.compute.amazonaws.com
~~~~~~~~~~

```console
shell> ec2-stop-instances i-afb4bcf1
shell> ec2-start-instances i-afb4bcf1
shell> ec2-terminate-instances i-afb4bcf1
~~~~~~~~~~

---


### :books: 參考網站：
- [AccessingInstancesLinux](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)
- [ec2-cli-launch-instance](http://docs.aws.amazon.com/AWSEC2/latest/CommandLineReference/ec2-cli-launch-instance.html)
s- [cli](https://aws.amazon.com/tw/cli/)
- [cli](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)
- [cli-chap-getting-started](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)
- [describe-images](http://docs.aws.amazon.com/cli/latest/reference/ec2/describe-images.html)
- [AMIs](http://docs.aws.amazon.com/zh_cn/AWSEC2/latest/UserGuide/AMIs.html)



