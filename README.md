# toolinstallation
All tools installation guide

# Project-1
  ###   prerequest:
          1. install jenkins
          2. install publlish over ssh, maven plugin in jenkins
          3. Install Tomcat
 ### Steps
 1. check java code and pom.xml in git
 2. create porject1
 3. add git url in jenkins
 4.

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




