# DevOps-Project-session-replication-tomcat

![image](https://github.com/user-attachments/assets/f3b1f999-471e-4640-8c4a-9ece6c4112af)

**Session Replication** comes into the picture when same application runs on two servers and they access the same session information.
<br><br/>
In this demonstration I used terraform to launch two EC2 Instances and an Application LoadBalancer. In order to Install Tomcat and configure session replication I have used Ansible. As shown in the Architecture diagram above the source code is present in the GitHub Repository https://github.com/singhritesh85/tomcat-session-replication.git. Jenkins is used as a CI/CD tool, for code analysis SonaQube has been used and Maven is the build tool. Nexus Artifactory has been used to store the Artifacts. Finally the war file will be deployed in the Tomcat Server.
<br><br/>
The source code web.xml must keep **<distriburable/>** as show in the screenshot below.
![image](https://github.com/user-attachments/assets/d0ecbfd6-f1fd-426b-9e65-be19bc5fc4e4)
