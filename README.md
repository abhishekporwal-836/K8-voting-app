# Web Voting App Deployment Using AWS EKS

# Implementation PDF: [Click here! ](https://drive.google.com/file/d/1TUlL7gFjL09gjHvrMJoXOIZgbDGjVR9s/view?usp=sharing)

## Architecture Diagram
<div align="center">
  <img src="./Documents/architecture-diagram.gif" alt="Logo" width="100%" height="100%">
</div>

## Kubernetes Resources

To deploy and manage this application effectively, we leverage Kubernetes and a variety of its resources:

- **Namespace**: Kubernetes namespaces are utilized to create isolated environments for different components of the application, ensuring separation and organization.

- **Secret**: Kubernetes secrets store sensitive information, such as API keys or credentials, required by the application securely.

- **Deployment**: Kubernetes deployments define how many instances of the application should run and provide instructions for updates and scaling.

- **Service**: Kubernetes services ensure that users can access the application by directing incoming traffic to the appropriate instances.

- **StatefulSet**: For components requiring statefulness, such as the MongoDB replica set, Kubernetes StatefulSets are employed to maintain order and unique identities.

- **PersistentVolume and PersistentVolumeClaim**: These Kubernetes resources manage the storage required for the application, ensuring data persistence and scalability.


## Table of Contents
1. [Setting up IAM Roles and Policies](#1-setting-up-iam-roles-and-policies)
2. [Creating EKS Cluster](#2-creating-eks-cluster)
3. [Setting up EC2 Instance](#3-setting-up-ec2-instance)
4. [Installation and Configuration](#4-installation-and-configuration)
5. [Node Creation](#5-node-creation)
6. [Context Configuration](#6-context-configuration)
7. [Accessing Pods](#7-accessing-pods)
8. [Deploying MongoDB](#8-deploying-mongodb)
9. [Exposing MongoDB Pods](#9-exposing-mongodb-pods)
10. [Namespace Configuration](#10-namespace-configuration)
11. [Data Loading](#11-data-loading)
12. [Creating Secret and Deploying API](#12-creating-secret-and-deploying-api)
13. [Testing API](#13-testing-api)
14. [Frontend Deployment](#14-frontend-deployment)
15. [Accessing Application](#15-accessing-application)
16. [Application Testing](#16-application-testing)


## 1. Setting up IAM Roles and Policies:
- *Creation of IAM Roles:*
   Developed IAM roles such as Eksaccess, myEksNodeRolePolicy, and myEksClusterRolePolicy with specific permissions tailored for EKS operations.
- *Assignment of Policies:*
  Associated appropriate permission policies with each IAM role to ensure they have the necessary access to resources within AWS.
- *Role Testing:*
  Verified the effectiveness of each role by simulating common tasks and ensuring they can perform required actions without encountering permission errors.

## 2. Creating EKS Cluster:
- *Cluster Configuration:*
  Defined the desired configuration for the EKS cluster, including node types, networking, and Kubernetes version.
- *Provisioning Cluster:*
  Utilized AWS Management Console or CLI tools to provision the EKS cluster named "Cluster1" based on the specified configuration.
- *Verification:*
  Ensured the cluster was properly provisioned and operational by checking its status and components.

## 3. Setting up EC2 Instance:
- *Instance Launch:*
  Launched an EC2 instance named "Project-Server" with appropriate specifications and configuration needed for hosting application components.
- *Connection Establishment:*
  Established a connection to the newly launched EC2 instance to facilitate further setup and installation steps.
- *Security Configuration:*
  Implemented security measures such as configuring security groups and applying IAM roles to the EC2 instance to restrict access and ensure compliance.
## 4. Installation and Configuration:
- *Kubectl Installation:*
  Installed the Kubernetes command-line tool (kubectl) on the Project Server to interact with the EKS cluster.
- *AWS CLI Setup:*
  Configured AWS CLI on the server to enable seamless interaction with various AWS services and resources.
- *Git Repository Cloning:*
  Cloned the Git repository containing the web voting application codebase to the server for further deployment and customization.

## 5. Node Creation:
- *Node Configuration:*
  Defined the specifications and attributes of the Kubernetes nodes to be added to the EKS cluster.
- *Node Deployment:*
  Initiated the process of creating and adding nodes to the EKS cluster, ensuring they were properly integrated and functional.
- *Scaling Considerations:*
  Determined the appropriate scaling strategy for the cluster nodes based on workload requirements and expected traffic patterns.

## 6. Context Configuration:
- *Context Addition:*
  Added the necessary context to the server environment to enable seamless communication and interaction with the EKS cluster.
- *Authentication Setup:*
  Configured authentication mechanisms to authenticate the server's access to the EKS cluster, ensuring security and integrity.
- *Context Verification:*
  Validated the added context to ensure it was correctly configured and functional for subsequent operations.

## 7. Accessing Pods:
- *Error Identification:*
  Identified any errors or issues encountered while attempting to access pods within the EKS cluster.
- *ConfigMap Implementation:*
  Implemented ConfigMaps to resolve permissions-related errors, granting necessary access to pods and resources.
- *ConfigMap Adjustment:*
  Modified ConfigMap settings as needed to fine-tune access control and ensure compatibility with cluster requirements.

## 8. Deploying MongoDB:
- *StatefulSet Creation:*
  Defined the MongoDB deployment configuration using StatefulSets to ensure data persistence and reliability.
- *Manifest Application:*
  Applied the manifest file (mongo-stateful.yaml) within the designated namespace (e.g., "cloudchamp") to deploy MongoDB components.
- *Health Checks:*
  Verified the health and status of MongoDB pods to ensure they were successfully deployed and functioning as expected within the cluster.

## 9. Exposing MongoDB Pods:
- *Service Creation:*
  Created a Kubernetes service to expose MongoDB pods internally within the cluster for communication and interaction.
- *Headless Service Configuration:*
  Configured the service as headless to allow direct access to individual MongoDB pods for specific use cases.
- *Endpoint Verification:*
  Confirmed the availability and accessibility of MongoDB endpoints to ensure seamless connectivity for application components.

## 10. Namespace Configuration:
- *Namespace Definition:*
  Defined and configured the "cloudchamp" namespace to organize and isolate resources related to the web voting application.
- *Namespace Assignment:*
  Assigned relevant components and deployments to the "cloudchamp" namespace to maintain organization and improve management.
- *Namespace Verification:*
  Verified the successful creation and configuration of the "cloudchamp" namespace to ensure proper isolation and resource allocation.

## 11. Data Loading:
- *Data Preparation:*
  Prepared the necessary data to be loaded into the MongoDB database, ensuring it aligned with the schema and requirements of the application.
- *Data Loading Process:*
  Executed the data loading process, transferring data from external sources into the MongoDB database using appropriate tools or scripts.
- *Data Validation:*
  Validated the loaded data within the MongoDB database to ensure accuracy, completeness, and consistency for use by the web voting application.

## 12. Creating Secret and Deploying API:
- *Secret Generation:*
  Generated a Kubernetes secret containing sensitive information such as database credentials or API tokens required for secure communication.
- *Secret Deployment:*
  Deployed the created secret within the Kubernetes cluster to make it accessible to authorized components and services.
- *API Deployment:*
  Deployed the API components and services required to interact with the MongoDB database securely, leveraging the previously created secret for authentication and authorization.

## 13. Testing API:
- *Load Balancer Setup:*
  Configured a load balancer service to distribute incoming traffic across multiple instances of the API for scalability and high availability.
- *API Access Testing:*
  Tested the functionality and performance of the API endpoints by sending various requests and validating the responses against expected outcomes.
- *Load Balancer Verification:*
  Verified the proper functioning and accessibility of the API endpoints through the configured load balancer, ensuring consistent and reliable service availability.

## 14. Frontend Deployment:
- *Manifest Application:*
  Applied the manifest file containing the frontend deployment configuration to deploy the web voting application's frontend components within the Kubernetes cluster.
- *Resource Allocation:*
  Allocated appropriate resources such as CPU, memory, and storage to the frontend components based on expected usage and performance requirements.
- *Health Monitoring:*
  Monitored the health and status of the deployed frontend components to detect and address any issues or failures promptly.

## 15. Accessing Application:
- *Load Balancer DNS:*
  Obtained the DNS endpoint of the frontend load balancer to access the deployed web voting application securely over the internet.
- *Endpoint Accessibility:*
  Accessed the web voting application using the provided DNS endpoint, ensuring connectivity and functionality across different devices and networks.
- *User Interaction:*
  Interacted with the web voting application through its user interface to perform various actions such as voting, viewing results, and managing preferences.
## 16. Application Testing:
- *Functionality Testing:*
  Tested the core functionality of the web voting application, including user authentication, voting process, result calculation, and data persistence.
- *Performance Evaluation:*
  Evaluated the performance of the
