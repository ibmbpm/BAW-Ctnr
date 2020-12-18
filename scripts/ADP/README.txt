 IBM Aria Content Project Deployment Service Scripts Readme
© Copyright IBM Corporation 2020.

Readme file for: IBM® Aria Content Project Deployment Service Scripts
Update name: 
Publication date: 2 November 2020
Last modified date: 2 November 2020

Project Deployment Scripts
	cpds_getOSInitStat.sh
	cpds_deployProj.sh
	cpds_getDeployedProjSnapshot.sh
	cpds_getDeploymentRec.sh
	
	helper_getUMSToken.sh

Project Deployment properties sample file

	cpds.properties.sample
	
General Overview
     The Project Deployment Scripts provide unix shell script samples using the Content Project Deployment Service REST API.
     The scripts provided give samples on how to 	deploy a project version to a Test/Staging/Production environment, monitor the deployment,
     and check the Object Store to verify the Content Project Deployment Initialization has been performed.
             
     The cpds.properties.sample are a list of properties which can be input used as input in to the scripts 
     
     The four main scripts are:
     	cpds_getOSInitStat.sh - checks the initialization status on the Object Store
	    cpds_deployProj.sh - deploys a content project deployment project version
	    	cpds_getDeployedProjSnapshot.sh - returns the project version information for the deployed snapshot/version
		cpds_getDeploymentStatus.sh - returns the deployment record for the deployment project version
	    
	 helper_getUMSToken.sh is the UMS authentication script used by all the scripts to login to the ums server and provider a bearer token. 
	    

Deploying a Project Version
	cpds_deployProj.sh 
	This script is intended for the Test/Staging/Production environment. A Document Processing Designer project and version from the 
	Development Environment is deployed into the Test/Staging/Production (runtime) environment. The project is deployed to the Content Platform Engine
	Object Store and associated Content Analyzer runtime environment.
	
	Documentation in the Knowledge Center will provide more information for the POST /v1/deployment/projects/{projectIdentifier}/branches/{branchName}/snapshots/{snapshotName} 
	
Gets the Deployment of the Project Version
	cpds_getDeployedProjSnapshot.sh
	The deployment of a project version may take a few minutes and the script provides return the project version id and lasted deployment record id
	for the snapshot/version deployed.	This script can be run about 20 seconds after the deployment has started. The deployment record id, which is the latestDeploymentRecordId in the output, should be entered as input to the
	cpds_getDeploymentStatus.sh script, to get deployment status.  
	
	Documentation in the Knowledge Center will provide more information for the GET /v1/deployment/projects/{projectIdentifier}/branches/{branchName}/snapshots/{snapshotName} 
	
Returns the Deployment Record for the Project Version
	cpds_getDeploymentStatus.sh
	The deployment of a project version may take a few minutes and the script provides the ability to monitor the progress of the deployment. Since the deployment can take a
	few minutes, this script can be used to poll the status of the deployment.
	
	Documentation in the Knowledge Center will provide more information for the GET /v1/deploymentrecords/{deploymentRecordId}
		

Object Store Initialization Status
	cpds_getOSInitStat.sh
	Runs the Content Project Deployment Service REST Get initialization endpoint which verify Content Project Deployment Initialization 
	has been run on the Content Platform Engine Object Store.
	
	Documentation in the Knowledge Center will provide more information for the GET /v1/repositories/{repositoryIdentifier}/initialization 
