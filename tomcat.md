#Tomcat Inatallation on Linux
'''sh
sudo yum update -y
'''

#download and install java
yum install -y java-1.8*
#Go to web site https://tomcat.apache.org/download-90.cgi
#based on Your OS downlaod image
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
#to change port open server.xml 
vi /opt/apache-tomcat-9.0.19/conf/server.xml
#<connector port="8080"
tomcatdown
tomcatup

# to manage the tomcat from other ip we need to add those ip in content.xml file and comment the following
#/opt/apache-tomcat-9.0.19/webapps/host-manager/META-INF/context.xml
#/opt/apache-tomcat-9.0.19/webapps/manager/META-INF/context.xml

  <!--<Valve className="org.apache.catalina.valves.RemoteAddrValve"
         allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1" /> -->
 tomcatdown
 tomcatup
 
#create users in /conf/tomcat-user.xml




