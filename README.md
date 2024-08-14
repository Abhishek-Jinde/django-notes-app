# Simple Notes App for CI-CD
This is a simple notes app built with React and Django.

## Tools Required
1. Docker
```
sudo apt install docker.io
```

2. Jenkins
```
sudo apt install openjdk-17-jre -y
```
# Add Jenkins repository key and install Jenkins
```
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins -y
```

3. Docker Compose
```
sudo apt-get install docker-compose
```

## Steps 
1. Configure User Permissions
Add users to the Docker group to grant appropriate permissions:
```
sudo usermod -aG docker $USER
sudo usermod -aG docker jenkins
sudo reboot
```
Creating the CI/CD Pipeline
Step 1: Create a New Pipeline Job
In the Jenkins dashboard, click on "New Item" to create a new job:

Name: notes-app-cicd
Project: Pipeline
Click "OK" and configure the pipeline:


Step 2: Configure Pipeline
In the pipeline configuration:

Check ✅GitHub project: and paste the GitHub URL: https://github.com/ShubhamSoni-1/Notes-app
Check ✅GitHub hook trigger for GIT SCM polling

Step 3: Configure DockerHub Credentials
To push the Docker image to DockerHub, configure the credentials in Jenkins:

Go to Dashboard > Manage Jenkins > Credentials > System > Global Credentials
Add DockerHub credentials and save

Step 4: Finalize and Run the Pipeline
Save the pipeline configuration and trigger a build. You should see the stages execute in sequence with green boxes indicating success.


