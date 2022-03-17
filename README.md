# Assignmnet-DevOps

#Dockerize a simple Hello World Flask Application

1. Create a directory with a name "Flask-Docker"
mkdir Flask-Docker-App

2. Navigate to the newly created directory
cd Flask-Docker-App


3. Create a virtual environment
python3 -m venv venv

4. Activate the environment
source venv/bin/activate

5 .Install Flask
pip install Flask

6. Create the required files
Create files; app.py, Dockerfile and requirements.text
touch app.py Dockerfile requirements.text

7 .Install the requirements
pip install -r requirements.txt

#Write code in [app.py](https://github.com/SMUSADDIQH/Assignmnet-DevOps/blob/master/app.py)

8. Run the application
python app.py

#Write [Dockerfile](https://github.com/SMUSADDIQH/Assignmnet-DevOps/blob/master/Dockerfile)

9. Build Docker Image
docker build -t flask-python .

10. Run the image as a container in detached mode mapping the port 5000:5000
docker run -d -p 5000:5000 python-docker

#Obtain the output as Hello World!

11. To see the containers running
docker ps

------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Deploy the docker image to AWS ECR.
#Create a Repositiry in ECR
#Create a Role in IAM and Attach that to the EC2 Instance

#Follow The push commands

1. Retrieve an authentication token and authenticate your Docker client to your registry.
   Use the AWS CLI:

2. aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/c3a8s7r4
   Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.
   Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:

3. docker build -t flask-python .
   Note: If the image is build skip this step
   After the build completes, tag your image so you can push the image to this repository:

4. docker tag flask-python:latest public.ecr.aws/c3a8s7r4/docker-assignment:latest
   Run the following command to push this image to your newly created AWS repository:

   docker push public.ecr.aws/c3a8s7r4/docker-assignment:latest

#After we push we can see the [image deployed](https://gallery.ecr.aws/c3a8s7r4/docker-assignment) in ECR.

------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Push the Repository to github

1. Add the files to Stagging Area
git add .

2. Commit the files to Local repo
git commit -m ""

3. Connect to GitHub
git remote add origin <URL>

4. Push to GitHub
git push -u origin master
  
------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Create a workflow for CI/CD pipeline in GitHub
  
1. Create The directories for workflow
Assignmnet-DevOps/.github/workflow/pyhton-linter.yaml



------------------------------------------------------------------------------------------------------------------------------------------------------------------
#Setup a workflow which would [deploy the given ECR image](https://docs.github.com/en/actions/deployment/deploying-to-your-cloud-provider/deploying-to-amazon-elastic-container-service) to ECS on EC2 instance or Fargate.
  
1. Create a workflow to deploy
Assignmnet-DevOps/.github/workflow/ECS.yaml
