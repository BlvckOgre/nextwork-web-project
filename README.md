# 🚀 Full CI/CD Web App Deployment Pipeline on AWS

## 📖 Overview
This project demonstrates the implementation of a **fully automated CI/CD pipeline** for deploying a Java-based web application using **AWS DevOps services**.  

The pipeline integrates **source control, build automation, artifact management, continuous delivery, and deployment** into a streamlined workflow, ensuring faster and more reliable software delivery.

---

## 🏗️ Architecture Diagram
![Architecture Diagram](./architecture-complete%20(1).png)

---

## 🔎 Architecture Explanation

1. **IAM User & Key Pair**  
   - Developers authenticate to AWS using an IAM user with an associated key pair.  
   - This ensures secure access and role-based permissions for managing resources.

2. **Development Environment**  
   - Core project files:  
     - `settings.xml` → Maven settings for dependency management.  
     - `buildspec.yml` → Instructions for AWS CodeBuild (compilation, packaging, and tests).  
     - `appspec.yml` → Deployment instructions for AWS CodeDeploy.  
     - Application code (`index.jsp`, `script`, etc.).  

3. **Source Control with GitHub**  
   - The web application source code is stored and versioned in GitHub.  
   - Integrated with AWS via **CodeConnection** for automated webhook triggers.  

4. **AWS CodeArtifact & Policies**  
   - Used for securely storing and retrieving dependencies.  
   - CodeArtifact policies define permissions for who/what can access packages.  

5. **AWS CodeBuild**  
   - Retrieves source from GitHub.  
   - Uses `buildspec.yml` to build, test, and package the application.  
   - Uploads build artifacts to **Amazon S3** for storage.  

6. **Amazon S3 (Artifact Storage)**  
   - Stores build artifacts from CodeBuild.  
   - Acts as a staging area before deployment.  

7. **AWS CodeDeploy**  
   - Pulls artifacts from S3.  
   - Uses `appspec.yml` to define deployment steps (e.g., stop old app, install new version).  
   - Deploys to **EC2 instances** running inside a **VPC**.  

8. **AWS CloudFormation**  
   - Automates infrastructure provisioning (VPC, EC2 instances, IAM roles, etc.).  
   - Ensures infrastructure consistency and repeatability.  

9. **Web Server & Live Website**  
   - EC2 hosts the web app, deployed by CodeDeploy.  
   - The result is a fully operational **live website** accessible via the internet.  

10. **AWS CodePipeline (CI/CD Orchestration)**  
    - Connects all services (GitHub → CodeBuild → S3 → CodeDeploy).  
    - Ensures automated end-to-end delivery whenever new code is pushed.  

---

## 📚 Project Phases

### 🔶 Phase 1: Web App Setup in AWS
- Configure IAM user and key pair.  
- Deploy initial Java app manually to EC2.  
- Validate app accessibility via browser.  

### 🔶 Phase 2: GitHub Integration
- Push project codebase to GitHub.  
- Connect GitHub repo to AWS CodePipeline.  
- Enable webhook triggers for automated builds.  

### 🔶 Phase 3: Secure Dependencies with CodeArtifact
- Set up a private package repository in CodeArtifact.  
- Configure Maven to pull dependencies securely from CodeArtifact.  
- Attach CodeArtifact policy to control access.  

### 🔶 Phase 4: Continuous Integration with CodeBuild
- Define build steps in `buildspec.yml`.  
- Run automated builds and unit tests.  
- Upload build artifacts to S3.  
- Monitor build logs in CodeBuild console.  

### 🔶 Phase 5: Automated Deployment with CodeDeploy
- Create `appspec.yml` with deployment lifecycle hooks.  
- Automate deployment to EC2 instances.  
- Enable rollback on failure for reliability.  

### 🔶 Phase 6: Full CI/CD Pipeline with CodePipeline
- Connect all components into a pipeline: GitHub → CodeBuild → S3 → CodeDeploy.  
- Achieve a fully automated source-build-deploy workflow.  
- Deliver updates instantly upon code commit.  

---

## 🛠️ Tech Stack
- **Language:** Java (JSP)  
- **Version Control:** GitHub  
- **CI/CD Tools:** AWS CodePipeline, CodeBuild, CodeDeploy  
- **Artifact Management:** AWS CodeArtifact, Amazon S3  
- **Infrastructure as Code:** AWS CloudFormation  
- **Hosting:** Amazon EC2 (inside VPC)  
- **Access & Security:** IAM, Key Pair Authentication  

---

## ✅ Key Features
- End-to-end **automated CI/CD pipeline**.  
- Secure **dependency management** with CodeArtifact.  
- Full **infrastructure automation** with CloudFormation.  
- Scalable deployment on **EC2 in VPC**.  
- Rollback and monitoring built into deployment lifecycle.  

---

## 📌 References
- [AWS CodePipeline Documentation](https://docs.aws.amazon.com/codepipeline/)  
- [AWS CodeBuild Documentation](https://docs.aws.amazon.com/codebuild/)  
- [AWS CodeDeploy Documentation](https://docs.aws.amazon.com/codedeploy/)  
- [AWS CodeArtifact Documentation](https://docs.aws.amazon.com/codeartifact/)  

---

## 🙏 Acknowledgements
Special thanks to the [NEXTWORK team](https://community.nextwork.org/c/all-aws-projects-e6e5db/devops-projects) for their structured 7-day guidance and resources.  

