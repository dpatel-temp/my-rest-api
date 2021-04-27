
For details on local application and configuration setup visit https://spring.io/guides/gs/rest-service/. 

* Clone code from github repository git@github.com:dpatel-temp/my-rest-api.git 
* Build maven application (e.g.  mvnw clean package)
* Perform integration testing.  
* Build using Jenkins job using maven's DEPLOY option which will upload SNAPSHOT artifact to Nexus/Artifactory repository.  
* Perform security scan using SonarScanner e.g.  mvn clean verify sonar:sonar

* Change the properties file if any as necessary before running it locally. 
* Setup maven or JVM arguments and log folder as necessary.
* Run application locally using IDE or on command line using "java -jar target/rest-service-0.0.1-SNAPSHOT.jar"
* Build docker image locally on centos 8 VM using "docker build -t rest-java-api . "
* Run local docker image using "sudo docker run -p 8080:8080 -it rest-java-api".
* Provide swagger arguments when running if using swagger to test end points.  


Branching (best suited for multiple parallel release branches):  
New project or feature enhancement:  
* Create feature branch from develop branch.  All feature branch names should contain JIRA story # as per agile project management. 
* For any long running project with multiple developers, create a project branch from develop using assigned project number and create feature branches off of this project branch. 
* * merge feature branches into project branch for each sprint and from project branch build and deploy to agile in-sprint environments for testing or setup CICD pipeline for deployment and testing. 
* Once feature or project is completed, raise merge request to merge feature or project branch into develop branch.
* Raise request to release management or development lead to approve merge request into develop branch.
* Merge approval can be setup using GitLab or GitHub UI workflow (e.g. JIRA integration) or using server side or web hookscripts.  
* Merge request approval may depend on successful completion of CICD pipeline on the source git branch. 
  

* Upon all successful merge into develop branch, create a release branch from the develop branch.  e.g. release/1.0.0

* Each merge request into develop, release and master may kick off automated CICD pipeline on the source branch that performs automated build, deploy and testing before accepting the merge request. 
* Each merge request into project, develop, release or master branch may involve performing a sync merge by means of pulling changes from target branch into the source branch before opening a merge request.


QA or UAT level defect fixes: 
* DevOps or CICD pipeline create tag from release branches to deploy to QA and/or UAT.
* DevOps will use maven's release option/plugin which will create a release tag, upload to artifactory or nexus and increment the release value in pom.xml to the next release.   
* For any defect found in release/1.0.0, create a feature branch from release/1.0.0, test as per above and merge into release/1.0.0 as well as develop branch.   
* DevOps or CICD pipeline create tags from release/1.0.0 to deploy to QA and/or UAT. 
* Upon successful testing of a tag in QA and UAT, deploy the same tag/artifact to PROD.  

* Upon successful deployment to PROD, merge release branch into master branch. 

PROD defect fixes:
* For any immediate defect fixes required in PROD, create a feature branch from master branch.  Merge back into master branch as well as develop branch.  
* Create new tag from master and test in QA and/or UAT.  Once signed off by QA and UAT, deploy to PROD.  











