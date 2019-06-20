# Devops Tool Installation & Project Guide

## Jenksin Installation on centos 7
          1. yum update -y
          2. yum install -y java-1.8*
          3. export JAVA_HOME=/usr/lib/jvm/<java version>
          4. export PATH=$PATH:$JAVA_HOME
          5. sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
          6. sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
          7. sudo yum install jenkins
          8. systemctl start jenkins
          9. systemctl enable jenkins

# Project-1
  ###   prerequest:
          1. install jenkins,install java on jenkins server and configure java_home variable
          2. install publlish over ssh, maven plugin in jenkins
          3. Install Tomcat
          4. deploy on contianers plugin
 ### Steps
         1. check java code and pom.xml in git
         2. create porject1
         3. add git url in jenkins
           3.1. For CI Add poll scm H/2 * * * *
         4. In build add "pom.xml" & in goals = clean,install,package
         5. Now save & apply and build now 
         6. Install Tomcat on node( open port,create user,create user form managing thorugh jenkins)
         7. jenikins > credeintials > global credeintials > add deployer credeintials > save
         8. jenkins>project1>build>post build>deploy war/ear
```
            war/ear file: **/*.war
            credeintials: add deployer credeintials
            tomcat url: <enter tomcat url>
```
  9.save
  10. Build Now

# Project-2
        CICD with jenkins git ansible tomcat
        1. install jenkins on server 
        2. install "publish over ssh " plugin
        3. create new projet "porject-2" > link GIT repo
        4. clean compile package using maven 
        5 in build section >select "send files or execute command over ssh"
             5.1. select server name
             5.2 source file "**/*.war" 
             5.3 remote direcotry "/opt/playbooks" 
             5.4 execute following command  "ansible-playbook /home/ansadmin/opt/copyfile.yml"
        6. save and apply 
        7. install ansible on server "follow the installation instruction of ansible file"
        8. create a playbook file to copy the .war file from ansible server to tomcat server
                  ---
                  - hosts:
                    become: true
                    task: 
                      -name: copying file to tomcat
                       copy: src=/opt/playbooks/ dest=/opt/apache-tomcat.9.91
        9. make sure u have permission to wirte file to destination
        10. build on jenkins




