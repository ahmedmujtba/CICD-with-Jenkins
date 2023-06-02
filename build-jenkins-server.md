# How to Build a Jenkins Server

We can follow the steps below to build a Jenkins server:

3. We will deploy jenkins on EC2 by creating an SSH conection with our EC2, downloading and isntalling jenkins and confugure jenkins.

4.

Commands used in setting up jenkins within aws ec2

sudo apt-get update -y
sudo apt-get upgrade -y
sudo wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update -y
sudo apt upgrade -y

manually download java Dk

sudo apt-get install openjdk-11-jre
java --version
export PATH=$PATH:/usr/lib/jvm/java-11-openjdk-amd64/bin/java
sudo apt-get install net-tools
sudo netstat -antup | grep 8080
sudo systemctl start jenkins
sudo systemctl status jenkins

to get jenkins password:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword
