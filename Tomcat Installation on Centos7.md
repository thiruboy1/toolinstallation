# Tomcat Inatallation on Centos 7
 ```sh 
sudo yum update -y
```

# download and install java
 ```sh 
yum install -y java-1.8*
 ```
#Go to web site https://tomcat.apache.org/download-90.cgi

# based on Your OS downlaod image
 ```sh 
cd ~
sudo wget http://mirrors.estointernet.in/apache/tomcat/tomcat-9/v9.0.20/bin/apache-tomcat-9.0.20.tar.gz
sudo mv apache-tomcat-9.0.20.tar.gz /opt/
sudo tar -zxvf apache-tomcat-9.0.20.tar.gz
cd /apache-tomcat-9.0.20/bin
sudo chmod +x  /opt/apache-tomcat-9.0.19/bin/startup.sh
sudo chmod +x  /opt/apache-tomcat-9.0.19/bin/shutdown.sh
echo $PATH
ln -s /opt/apache-tomcat-9.0.19/bin/startup.sh /usr/bin/tomcatup
ln -s /opt/apache-tomcat-9.0.19/bin/shutdown.sh /usr/bin/tomcatdown
tomcatup
curl localhost:8080
 ```
### To change port open server.xml 

       vi /opt/apache-tomcat-9.0.19/conf/server.xml
       #connector port="8080"
       tomcatdown
       tomcatup
 
### create users and allow manager access update following in /conf/tomcat-user.xml

```
  <role rolename="manager-gui"/>
  <role rolename="manager-script"/>
  <role rolename="manager-jmx"/>
  <role rolename="manager-status"/>
  <user username="admin" password="admin" roles="manager-gui,manager-script, manager-jmx, manager-status"/>
  <user username="deployer" password="deployer" roles="manager-script"/>
  <user username="tomcat" password="admin" roles="manager-gui"/>
```

### To manage the tomcat from other ip we need to add those ip in content.xml file and comment the following
 1. vi /opt/apache-tomcat-9.0.19/webapps/host-manager/META-INF/context.xml
 2. vi /opt/apache-tomcat-9.0.19/webapps/manager/META-INF/context.xml
 ```

           <!--<Valve className="org.apache.catalina.valves.RemoteAddrValve"
                  allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
   ```     
### Restart Tomcat     
     tomcatdown
     tomcatup
 





