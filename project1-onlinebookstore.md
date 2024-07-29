project-1

1.installed jenkins : 

sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf upgrade
# Add required dependencies for the jenkins package
sudo dnf install fontconfig java-17-openjdk
sudo dnf install jenkins
sudo systemctl daemon-reload

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins

2.installed tomcat :

sudo apt install default-jdk
sudo groupadd tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
cd /tmp
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.91/bin/apache-tomcat-9.0.91.tar.gz
sudo chgrp -R tomcat /opt/tomcat
sudo chmod -R g+r conf
sudo chmod g+x conf
sudo chown -R tomcat webapps/ work/ temp/ logs/
sudo nano /opt/tomcat/conf/server.xml 
port=8081



3.installed maven
sudo apt-get install maven

4.MySQL Server on windows

5.MySQL Bench on windows

create database if not exists onlinebookstore;

use onlinebookstore;

create table if not exists books(barcode varchar(100) primary key, name varchar(100), author varchar(100), price int, quantity int);

create table if not exists users(username varchar(100) primary key,password varchar(100), firstname varchar(100),
    lastname varchar(100),address text, phone varchar(100),mailid varchar(100),usertype int);

insert into books values('9780134190563','The Go Programming Language','Alan A. A. Donovan and Brian W. Kernighan',400,8);
insert into books values('9780133053036','C++ Primer','Stanley Lippman and Josée Lajoie and Barbara Moo',976,13);
insert into books values('9781718500457','The Rust Programming Language','Steve Klabnik and Carol Nichols',560,12);
insert into books values('9781491910740','Head First Java','Kathy Sierra and Bert Bates and Trisha Gee',754,23);
insert into books values('9781492056300','Fluent Python','Luciano Ramalho',1014,5);
insert into books values('9781720043997','The Road to Learn React','Robin Wieruch',239,18);
insert into books values('9780132350884','Clean Code: A Handbook of Agile Software Craftsmanship','Robert C Martin',288,3);
insert into books values('9780132181273','Domain-Driven Design','Eric Evans',560,28);
insert into books values('9781951204006','A Programmers Guide to Computer Science','William Springer',188,4);
insert into books values('9780316204552','The Soul of a New Machine','Tracy Kidder',293,30);
insert into books values('9780132778046','Effective Java','Joshua Bloch',368,21);
insert into books values('9781484255995','Practical Rust Projects','Shing Lyu',257,15);
insert into users values('demo','demo','Demo','User','Demo Home','42502216225','demo@gmail.com',2);
insert into users values('Admin','Admin','Mr.','Admin','Haldia WB','9584552224521','admin@gmail.com',1);
insert into users values('shashi','shashi','Shashi','Raj','Bihar','1236547089','shashi@gmail.com',2);

commit;


6.Installed git

sudo apt install git

9.

git clone https://github.com/shashirajraja/onlinebookstore.git
cd onlinebookstore
ls
mvn clean install

http://localhost:8081/onlinebookstore

10.Connect to the database server

cd	/home/ubuntu/onlinebookstore/src/main/resources/application.resources
edit the details with the database details

11.run manually

cd /onlinebookstore
mvn clean install
cp /target/onlinebookstore.war /opt/tomcat/webapps/onlinebookstore.war
http://localhost:8081/onlinebookstore/

12.Run using jenkins

http://localhost:8080
freestyle project-1
clone repository using git
install maven plugin
install deploy ear/war container
install ssh
input the details

done succesfully

errors occured

1.failed to login with user credentials in the online bookstore java application
because i didnt added manager-gui details in 
vi /opt/tomcat/conf/tomcat_users.xml
<role rolename="manager-script"/>
 roles="manager-script,manager-gui"
 
2.failed to start tomacat:
because jenkins and tomcat where running same port
to change
vim /opt/tomcat/conf/server.xml
port=8081
and also due to java version change

3.failed to run jenkins freestyle project-1
due to incorrect port connectivity of database with application
corrected it by changing port :
vim /onlinebookstore/src/main/resources/application/application.resources
