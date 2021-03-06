# jenkins-pipeline
A barebone jenkins pipeline of a java app using docker

My intent was to create a local CI/CD pipeline to support development of a classic java app.
The dev cycle is to develop in a Windows laptop using several tools and at a command (in a browser in this case) run a pipeline that deploys the app in a local VM.
I use maven for compile/test/package
The application is deployed and run inside a docker container

I use jenkins to run the pipeline. Jenkins also runs in a docker container and all the steps in the pipeline are executed in containers. 
This arrangement avoids to install plugins for maven or other tools, docker downloads the images of the tools needed.
You only needs to install two plugins in Jenkins:
1. Pipeline 
2. File System SCM (or your favorite local source control tool)

In the pipeline configure the file system SCM to point to where you installed the app.

Files in this repo:\
vm/... I use vagrant and virtualbox to run my local VM. Very convenient as I can share folders between my Windows 10 host and my VM and do all the editing using Windows tools. Move the vagrantfile to the root of this repo if you want to setup the vm\
k8s. templates to create the service in kubernetes. tested with minikube. Edit setup.bat to point to the directory where you cloned the repo. You can see how I set up minikube in the repo http://github.com/mulargui/healthylinkx-k8s \
jenkins.docker/... how to dockerize jenkins\
src/... my simple java app\
src.docker/... how to dockerize the java app\
pipeline/... contains all the different pipeline files\
  Jenkinsfile. Describes the compile/test/package/deploy/run pipeline\
  Jenkinsfile.k8s. A similar pipeline to run on k8s\
  Jenkinsfile.mvn. A first attempt using maven as a plugin instead of a container\

Enjoy!
