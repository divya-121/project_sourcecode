# Install Jenkins on AWS EC2
Jenkins is a self-contained Java-based program, ready to run out-of-the-box, with packages for Windows, Mac OS X and other Unix-like operating systems. As an extensible automation server, Jenkins can be used as a simple CI server or turned into the continuous delivery hub for any project.

### Prerequisites
1. EC2 Instance
With Internet Access
Security Group with Port'8080' open for internet

2. Java 17 should be installed

## Install Jenkins
Go to jenkins official website
Get the latest version of jenkins https://pkg.jenkins.io/redhat-stable/ and start installing

To use this repository, run the following command:
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

Install the latest version of java: 
yum install java -y #on redhat
Start installing the jenkins:
yum install jenkins -y

### Start Jenkins
Start the jenkins service:
#enbling the service:
systemctl enable jenkins

#starting the service:
systemctl start jenkins

To verify the service is up or not:
systemctl status jenkins

### Accessing Jenkins
By default jenkins runs at port 8080, You can access jenkins at:
http://YOUR-SERVER-PUBLIC-IP:8080

### Configure Jenkins
1. The default Username is 'admin'
2. Grab the default password
Password Location:'/var/lib/jenkins/secrets/initialAdminPassword'
3. 'Skip' Plugin Installation; We can do it later

4. Change admin password
'Admin' > 'Configure' > 'Password'
5. Configure 'java' path
'Manage Jenkins' > 'Global Tool Configuration' > 'JDK'
6. Create another admin user id

### Test Jenkins Jobs
Create “new item”
1. Enter an item name – `My-First-Project`
   - Chose `Freestyle` project
2. Under the Build section
	Execute shell: echo "Welcome to Jenkins Demo"
3. Save your job 
4. Build job
5. Check "console output"
