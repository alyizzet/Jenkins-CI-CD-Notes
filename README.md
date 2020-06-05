# jenkinsNotes
This is a cheatsheet I have compiled for jenkins CI/CD, feel free to use it! 

JENKINS
CI/CD tools written in Java. It is an automation server basically.
Continuous Integration: means merging all the developer working copies into a mainline several times a day. Software is produced in short cycles. 
All developers must commit at least once a day and Jenkins pushes their changes to a version control system. 
Jenkins itself does not merge code. 
Jenkins can publish every build of your software. 
Tests: Unit, Integration, Regression, User Acceptance et cetera. 
SDLC Code → Build → Test → Release → Deploy 

Alternatives: Drone CI, TeamCity, Wercker, Travis, Gitlab, Github, CircleCI, CodeShip,AWS CI/CD tools …

Ubuntu is preferred here. In the course the guy uses DigitalOcean droplet and installs docker and jenkins inside there. 
Can you simulate it on the local though? 
Docker isolates the binary with all the dependencies 
No more “works on my machine!”
If you create an image of an app you can use it pretty much anywhere.
Go is pretty much immature and circlejerky with no robust libraries at all, learn node.js instead!  
Node.js App on Jenkins CI/CD 
You first install the dependencies and run tests “npm install && npm test” 
Docker basically does what go does when you create a shippable binary. 
Jenkins has a lot of plugins for binary creation from a sample node.js app. 
Jenkins has a great UI which you can use to do all the docker deployment of images. 
However if you use the UI you can not track the history of changes so one should use CLI to create an audit trail. 
There are Jenkins administrators and developers need to ask for permission.
Developers should do version control of their own build files. 
Jenkins Job DSL(Domain specific language)
Plugin uses groovylike scripting language. When you have a lot of jobs(apps) you need to use this. 

Jenkins DSL 
you need to approve scripts beforehand. 
You can integrate it with Slack, Github, Bitbucket, Emails etc.

Jenkins Pipelines 
Build steps are written in code build ---> test ---> deploy 
Basically you automate the build test deploy cycle.
Probably Gitlab CI/CD is better!. 
 You can write this in Jenkins DSL or Groovy. 

Example Jenkins Pipeline 
Node: Worker node which node will run this pipeline.
Stage: Build,test,deploy stages. 


For a Node.js project a Jenkins Pipeline


 A visual representation of a Jenkins Pipeline



You can run an already built docker container in jenkins. 
You can also test database integration with Jenkins pipelines. 
For example in the below example you pull a MySQL image and do an integration test and then remove the container if the test succeeds. 

Docker Images used in Jenkins Pipelines

For every pull and push you can set up notifications via email, slack et cetera. 
You can do this with Jfrog, Custom APIs and Sonarqube as well. 
You use webhooks for Slack and Custom API integrations
Sonarqube is the “Code Quality Checker” that basically enforces best practices and you can also integrate this to your pipelines. 

Advanced Jenkins Topics
One Droplet = One node 
Jenkins web UI on one node and worker nodes to do the work(Jenkins Slaves)
You can scale manually during working hours when a lot of the code is being developed. 
You can also use automatic plugins for scaling. (Uses AWS EC2 API or Docker Plugin or DigitalOcean plugin and many others for this purpose)
Builds can only run on a specific node.
Always use slaves for economical practices.  
Master node connects to the slave using SSH 
or Slave connects to master using JNLP
Blue Ocean is a frontend for Jenkins to replace the Web UI. Better Visualization this is a plugin. 
ssh-agent ---> this is used so the slaves can be configured automatically.
use a firewall for Jenkins to protect business tools no need for external access.
Whitelist IPs for buckets
If you use it as exposed to the public networks you can get HACKED! 
Onelogin is used for authentication to Jenkins. Matrix based authentication or there are other plugins too. 
SAML is used for authentication. Onelogin is not cheap!!
