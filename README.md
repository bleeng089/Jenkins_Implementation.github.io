# Class 6: Implementing Jenkins

## Step 1: Create an account in Docker Hub and install Docker Desktop 
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image1.png)

## Step 2: Open Docker Desktop
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image2.png)

## Step 3: Search for Jenkins and Pull it
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image3.png)

## Step 4: Open your terminal and log in to Docker
### *docker login*
- Since your using Docker Desktop, credentials are automatically saved to the native keychain of your operating system: https://docs.docker.com/reference/cli/docker/login/#credential-stores
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image4.png)

### *docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts-jdk11*
- You can change the host machine's port mappings and volume mount mappings, e.g., my image illustrates docker run -p 8081:8080 -p 50001:50000 -v jenkins_home2:/var/jenkins_home jenkins/jenkins:lts-jdk11
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image5.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image6.png)
- Here's the output to your password as well as its path
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image7.png)
-  We have successfully set up a Jenkins server in a Docker container with specific port mappings and storage configurations

## Step 5: Log in to your Jenkins server through a web browser
### *localhost:"local machines mapped port number"*
- If you configured *"-p 8080:8080"* then it's -> *localhost:8080*. I configured *"-p 8081:8080"* so it's -> *localhost:8081*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image8.png)

## Step 6: Install suggested plugins
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image9.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image10.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image11.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image12.png)

## Step 7: In your AWS console, go to IAM and create a new user for Jenkins
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image14.png)
- Create Access Keys for Jenkins for CLI access
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image15.png)

## Step 8: Go back to Jenkins and install your plugins
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image16.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image17.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image18.png)

### AWS
- AWS Credentials
- Pipeline: AWS Steps
- Amazon EC2
- Amazon Elastic Container Service (ECS) / Fargate
- Amazon S3 Bucket Credentials
- AWS CodeBuild
- AWS CodeDeploy
- AWS Lambda
- AWS CodePipeline
- AWS Secrets Manager SecretSource
- Configuration as Code AWS SSM secrets
- CloudFormation
- AWS SAM

### Terraform
- Terraform

### Google
- Kubernetes
- Google Cloud Storage
- Google Kubernetes Engine
- Google Cloud Platform SDK::Auth
- Pipeline: GCP Steps

### DevSecOps
- Snyk Security

### Sonar
- SonarQube Scanner

### Aqua
- Aqua Security Scanner
- Aqua MicroScanner
- Aqua Security Serverless Scanner

### GitHub
- GitHub Integration
- GitHub Authentication
- Pipeline: GitHub
- Pipeline GitHub Notify Step

## Step 9: Log into your Jenkins container via the terminal
- Your Jenkins container should be on since you just used it

### *docker ps*
- Verify that your Jenkins container is running
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image19.png)

### *docker exec -it --user root "container name or id"*
- Mine is *"docker exec -it --user root dreamy_clarke bash"*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image20.png)

## Step 10: Install the AWS CLI and Terraform
### *apt update && apt install -y awscli*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image21.png)
### *curl -fsSL https://releases.hashicorp.com/terraform/1.5.7/terraform_1.5.7_linux_amd64.zip -o /usr/local/bin/terraform.zip*
### *unzip /usr/local/bin/terraform.zip -d /usr/local/bin*
### *rm /usr/local/bin/terraform.zip*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image22.png)
### *env*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image23.png)
- If you don't see *"/usr/local/bin"* then input:
### *export PATH=/usr/local/bin:$PATH*

## Step 11: Exit the container and head to github https://github.com/bleeng089/autoScale.git
- Fork this repo and clone the forked repo
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image24.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image25.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image26.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image27.png)
- Line 11 in "Jenkinsfile" is what we'll name the Access Key ID in Jenkins. This will allow Jenkins to reference our AWS Access Keys in order to build infrastructure
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image28.png)

## Step 12: Head back to Jenkins and define the AWS Acess Keys
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image29.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image30.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image31.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image32.png)
- Access Key ID must reflect line 11 in the "Jenkinsfile" file from the repo
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image33.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image34.png)

## Step 13: Pipeline time
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image35.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image36.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image37.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image38.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image39.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image40.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image41.png)

## Step 14: Clean up
### Log into your Jenkins container
- Review step 9 for logging into your Jenkins container
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image42.png)

## Step 15: Set environmental variables for AWS
### *export AWS_ACCESS_KEY_ID=your_access_key_id*
### *export AWS_SECRET_ACCESS_KEY=your_secret_access_key*
### *export AWS_DEFAULT_REGION=your_preferred_region*
### *env* to check if it worked
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image43.png)

## Step 16: Find the Terraform directory
### *find / -name ".tf"*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image44.png)

## Step 17: Navigate to the directory and destroy the infrastructure
### *cd /var/jenkins_home/workspace/Chewbaka*
### *terraform destroy -auto-approve*
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image45.png)
![Jenkins Implementation](https://github.com/bleeng089/Jenkins_Implementation.github.io/raw/main/image46.png)
