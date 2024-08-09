# DevOps-Project-session-replication-tomcat

![image](https://github.com/user-attachments/assets/f3b1f999-471e-4640-8c4a-9ece6c4112af)

**Session Replication** comes into the picture when same application runs on two servers and they access the same session information.
<br><br/>
In this demonstration I used terraform to launch two EC2 Instances and an Application LoadBalancer. In order to Install Tomcat and configure session replication I have used Ansible. As shown in the Architecture diagram above the source code is present in the GitHub Repository https://github.com/kamalmohan217/tomcat-session-replication.git. Jenkins is used as a CI/CD tool, for code analysis SonaQube has been used and Maven is the build tool. Nexus Artifactory has been used to store the Artifacts. Finally the war file will be deployed in the Tomcat Server.
<br><br/>
```
The source code web.xml must keep <distriburable/> as show in the screenshot below.
```
![image](https://github.com/user-attachments/assets/d0ecbfd6-f1fd-426b-9e65-be19bc5fc4e4)

Here I have used session replication in EC2 Instances with StaticMembership rather than Multicast. The Jenkinsfile which I have used for CI/CD deployment is availabe with this Repository. 

Create the database jwt and table USER in MySQL as shown in the screenshot below before running the Jenkins Job.
![image](https://github.com/user-attachments/assets/4befe8b8-4ca8-4d2f-88ec-9a6efa8be6f6)
![image](https://github.com/user-attachments/assets/c54917fe-cc65-40fc-95e7-acb1956e7015)
![image](https://github.com/user-attachments/assets/f7a1ed0d-be24-4d98-8090-aaa294c97130)

Before running the Jenkins Job make sure the endpoint of MySQL is updated at the path tomcat-session-replication/src/main/webapp/userRegistration.jsp and Breadcrumbstomcat-session-replication/src/main/webapp/login.jsp in the source code as shown in the screenshot below.
![image](https://github.com/user-attachments/assets/d6ae97fc-7390-4d58-92d2-b5e89d989c7d)
![image](https://github.com/user-attachments/assets/fcff4357-b08b-4a5e-9efb-bb9833609a7a)

After running the Jenkins Job the screenshot for SonarQube, Nexus Artifactory and entry inside the database jwt's USER table is as shown below.

![image](https://github.com/user-attachments/assets/d6a1e71d-c93a-4ced-aa28-f5432041cd2c)
![image](https://github.com/user-attachments/assets/73fcefab-dbfa-4d97-bef7-f86fe84ee224)
![image](https://github.com/user-attachments/assets/2c428b00-73b4-43cb-8338-e3fa4b23ef79)

To run the Jenkins Job successfully webhook had been created in SonarQube and modified the /etc/resolv.conf file on SonarQube and on Jenkins Slave Node as shown in the screenshot below (You can also achieve this by creating a new DHCP option set, I had already discussed regarding this in earlier project You can refer https://github.com/kamalmohan217/DevOps-Project-2tier-WebApp-Deployment/blob/main/Complications-which-you-may-face/complications.md ).
![image](https://github.com/user-attachments/assets/1f290de4-8925-4cf7-8f9b-efba7f3e2495)
![image](https://github.com/user-attachments/assets/f0afde40-329b-42e9-9d25-c539a9fc0683)
![image](https://github.com/user-attachments/assets/b7f7dddb-c9ec-4f89-9c14-9741f6962215)

The entry for Route53 to create the record set in hosted zone is as shown below.
![image](https://github.com/user-attachments/assets/7529d35a-9027-42e3-bb7e-0138ff6a25b4)

Finally access the newly created URL as shown in the screenshot below.
![image](https://github.com/user-attachments/assets/e99872bb-92ac-40b7-b31a-8d1a73cd48e5)
![image](https://github.com/user-attachments/assets/4a440956-8d5e-41c6-a749-f5130822dae3)
![image](https://github.com/user-attachments/assets/8309b7a3-c8c5-4a8f-8d34-a5dde86005ed)

Now open the Tomcat Manager as shown in the screenshot below and be asured about the session replication.
![image](https://github.com/user-attachments/assets/a5f2a0a1-4a8b-4e32-ab0b-406f536369aa)
![image](https://github.com/user-attachments/assets/f24b064e-405c-4dd6-8671-a73cc133f6d2)
![image](https://github.com/user-attachments/assets/4785f08d-7fae-48a1-91be-6f5d687e190c)
![image](https://github.com/user-attachments/assets/d360cf42-934a-4bb1-b462-fea824e106f9)

Here stickiness is enabled.

<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
Source Code:- https://github.com/kamalmohan217/tomcat-session-replication.git 
```
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
References

https://ashok198510.hashnode.dev/cloud-native-two-tier-application-deployment-with-eks-tomcat-and-rds-in-aws
https://github.com/Ashoksana/aws-rds-java.git
https://tomcat.apache.org/tomcat-8.5-doc/cluster-howto.html
```
