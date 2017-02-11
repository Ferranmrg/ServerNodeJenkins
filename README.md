# ServerNodeJenkins
A Tutorial to deploy a server with centOS/Jenkins/NodeJs

In this tutorial I'll explain how to deploy a NodeJS backend with Jenkins in CentOS

## CentOS setting

I'll use CentOS 7

in root
```
$ sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
$ sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
$ sudo yum install jenkins

```

Be sure you have Java
`
 $ yum install java
`
Get the service ready
`
   $ sudo service jenkins start/stop/restart
`

lets also make it boot on the server start

`
$ sudo chkconfig jenkins on
`
Disable the firewall
`
$ firewall-cmd --zone=public --add-port=8080/tcp --permanent
$ firewall-cmd --zone=public --add-service=http --permanent
$ firewall-cmd --reload
`
With this you should be able to start jenkins on the 8080 port

Complete the jenkins setup selecting default

Let's work on jenkins security, open : configure jenkins > manage global security

check the project-based matrix security and add the user you created before

Apply and Save

Install without restart (or check if it's already installed) the following plugins:
`

    GitHub Plugin
    Clover Plugin
    Checkstyle Plug-in
    TAP Plugin
    Embeddable Build Status Plugin
    NodeJS Plugin

`
Restart Jenkins

