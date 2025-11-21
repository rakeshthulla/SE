SE 

⭐ WEEK 8 — PART I
Maven Java Project Automation Using Jenkins
(Full, detailed, easy-to-understand explanation)

🔵 Introduction
In this task, we automate the building and testing of a Maven Java project using Jenkins.
We create two Jenkins jobs:
1.MavenJava_Build → Build the code
2.MavenJava_Test → Test the built code
Then we connect them in a pipeline view to visualize the workflow.

⭐ STEP 1 — Open Jenkins Dashboard
Open browser → type:
http://localhost:8080
This opens Jenkins home page.

⭐ STEP 2 — Create First Job (MavenJava_Build)
This job downloads code from GitHub and runs Maven build commands.
✔ 1. Click New Item
(left side menu)
✔ 2. Enter item name:
MavenJava_Build
✔ 3. Select:
Freestyle Project
Click OK

⭐ STEP 3 — Configure MavenJava_Build
✔ A. Description
Write something meaningful:
Java Build demo

✔ B. Source Code Management → Git
Select Git
Paste your GitHub repo URL of the Maven Java project
Example:
https://github.com/username/maven-java-demo
Branch to build:
*/main
or:
*/master

✔ C. Build Steps
🔹 Build Step 1
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
clean
🔹 Build Step 2
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
install
This compiles the project and creates a JAR file.

✔ D. Post-Build Actions
🔹 Action 1 — Archive the artifacts
Add Post-build Action → Archive the artifacts
Files:
**/*
This stores the build output in Jenkins.

🔹 Action 2 — Trigger Next Job
Add Post-build Action → Build other projects
Projects to build:
MavenJava_Test
Trigger:
✔ Only if build is stable
This links Build → Test.

✔ E. Save
Click:
Apply
Save

⭐ STEP 4 — Create Second Job (MavenJava_Test)
This job tests the code built in the first job.
✔ 1. Go to Dashboard → Click New Item
✔ 2. Enter name:
MavenJava_Test
✔ 3. Choose:
✔ Freestyle project
Click OK

⭐ STEP 5 — Configure MavenJava_Test
✔ A. Description
Test demo

✔ B. Build Environment
Check:
✔ Delete workspace before build starts
This ensures fresh workspace every time.

✔ C. Build Step — Copy artifacts
(Requires “Copy Artifact Plugin”)
Click:
Add build step → Copy artifacts from another project
Fill:
Project name:
MavenJava_Build
Build:
✔ Stable build only
Artifacts to copy:
**/*
This copies output from the first job.

✔ D. Build Step — Run Tests
Click:
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
test
This runs JUnit tests.

✔ E. Post-build Action — Archive Test Output
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*

✔ F. Save
Click:
✔ Apply
✔ Save

⭐ STEP 6 — Create Pipeline View
This gives a visual representation of job execution.
✔ 1. Go to Dashboard
✔ 2. Click “+” (New View)
✔ 3. Enter:
MavenJava_Pipeline
✔ 4. Select:
Build Pipeline View
Click OK

⭐ STEP 7 — Configure Pipeline View
✔ A. Layout:
Based on upstream/downstream relationship
✔ B. Initial Job:
MavenJava_Build
Click:
✔ Apply
✔ Save

⭐ STEP 8 — Run the Pipeline
Go to:
MavenJava_Pipeline
Click Run
Jenkins will execute:
1.MavenJava_Build
2.MavenJava_Test (automatically)
✔ If GREEN → Success
✔ If RED → Error (check console)
Click each build box → view console output & artifacts.

⭐ WEEK 8 — PART II
Maven Web Project Automation Using Jenkins
(Build → Test → Deploy → Tomcat → Pipeline)

🔵 Introduction
In this part, we automate a Maven Web (WAR) application using Jenkins.
We create:
1️⃣ MavenWeb_Build → Download code + build WAR
2️⃣ MavenWeb_Test → Test the web project
3️⃣ MavenWeb_Deploy → Deploy WAR file to Tomcat
4️⃣ MavenWeb_Pipeline → Visual pipeline view
5️⃣ Open browser → view deployed web app
This completes CI/CD for a web application.

⭐ STEP 1 — Create Job: MavenWeb_Build
✔ 1. Go to Dashboard → Click New Item
✔ 2. Enter name:
MavenWeb_Build
✔ 3. Choose:
✔ Freestyle Project
Click OK

⭐ STEP 2 — Configure MavenWeb_Build
✔ A. Description
Web Build demo

✔ B. Source Code Management → Git
Select Git
Paste your Maven Web GitHub repo URL, example:
https://github.com/yourusername/maven-web-demo
Branch:
*/main
or
*/master

✔ C. Build Steps
🔹 Build Step 1 — Clean
Click:
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
clean
🔹 Build Step 2 — Install
Click:
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
install
This will generate:
target/*.war

✔ D. Post-build Actions
🔹 Action 1 — Archive artifacts
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*
This saves WAR file in Jenkins.

🔹 Action 2 — Build other projects
Click:
Add Post-build Action → Build other projects
Fill:
Projects to build:
MavenWeb_Test
Trigger:
✔ Only if build is stable
This links Build → Test.

✔ E. Save
Click:
✔ Apply
✔ Save

⭐ STEP 3 — Create Job: MavenWeb_Test
✔ 1. Dashboard → New Item
✔ 2. Enter:
MavenWeb_Test
✔ 3. Choose Freestyle Project
Click OK

⭐ STEP 4 — Configure MavenWeb_Test
✔ A. Description
Test demo

✔ B. Build Environment
Check:
✔ Delete workspace before build starts

✔ C. Copy Artifacts from Build Job
Click:
Add build step → Copy artifacts from another project
Fill:
Project name:
MavenWeb_Build
Which build:
✔ Stable build only
Artifacts to copy:
**/*

✔ D. Build Step — Run Maven Tests
Click:
Add build step → Invoke top-level Maven targets
Fill:
Maven version: MAVEN_HOME
Goals:
test

✔ E. Post-build Action — Archive Artifacts
Click:
Add Post-build Action → Archive the artifacts
Files:
**/*

✔ F. Post-build — Trigger Deploy Job
Click:
Add Post-build Action → Build other projects
Fill:
MavenWeb_Deploy

✔ G. Save
Click:
✔ Apply
✔ Save

⭐ STEP 5 — Create Job: MavenWeb_Deploy
✔ 1. Dashboard → New Item
✔ 2. Enter:
MavenWeb_Deploy
✔ 3. Choose Freestyle Project
Click OK

⭐ STEP 6 — Configure MavenWeb_Deploy
✔ A. Description
Web Code Deployment

✔ B. Build Environment
Check:
✔ Delete workspace before build starts

✔ C. Copy WAR from Test Job
Click:
Add build step → Copy artifacts from another project
Fill:
Project name:
MavenWeb_Test
Build:
✔ Stable build only
Artifacts to copy:
**/*.war

⭐ STEP 7 — Deploy WAR to Tomcat
You must have Tomcat installed.
✔ A. Post-build → Deploy WAR/EAR to a container
Click:
Add Post-build Action → Deploy WAR/EAR to a container
Fill:
WAR/EAR files:
**/*.war
Context path:
webpath
(This will create: localhost:8085/webpath)

✔ B. Add Container → Tomcat 9.x Remote
Fill:
Credentials:
Username: admin
Password: 1234
Tomcat URL:
http://localhost:8085/

✔ C. Save
Click:
✔ Apply
✔ Save

⭐ STEP 8 — Create MavenWeb_Pipeline View
✔ 1. Go to Dashboard → Click + (New View)
✔ 2. Enter:
MavenWeb_Pipeline
✔ 3. Choose:
Build Pipeline View
Click OK

⭐ STEP 9 — Configure the Pipeline View
Fill:
✔ Layout:
Based on upstream/downstream relationship
✔ Initial Job:
MavenWeb_Build
Click:
✔ Apply
✔ Save

⭐ STEP 10 — Run the Full Pipeline
In MavenWeb_Pipeline:
Click ▶️ Run
You will see:
1.MavenWeb_Build (green)
2.MavenWeb_Test (green)
3.MavenWeb_Deploy (green)
Pipeline is successful when all turn GREEN.

⭐ STEP 11 — View the Deployed Web App
Open browser:
http://localhost:8085/webpath
You should see your web project output (index.jsp or servlet response).






















⭐ WEEK 9: Pipeline Creation Using Script

1. Aim
To create a Jenkins Scripted Pipeline for a Maven Java project, configure build triggers, and execute all stages using a Groovy-based Jenkinsfile.

2. Procedure
✔ Step 1 — Open Jenkins
Go to:
http://localhost:8080
✔ Step 2 — Create a New Pipeline Job
Click New Item
Name:
Pipeline_Script_MavenJava
Select: Pipeline
Click OK

3. General Section
Write:
This project demonstrates scripted pipeline execution for Maven Java using Jenkins.

4. Build Triggers
Choose any (your choice), example:
H/5 * * * *
(Triggers every 5 minutes.)

5. Advanced Project Options
Set:
Definition → Pipeline Script
Paste the full script (given below).

⭐ 6. Complete Script for Week 9 (FINAL VERSION)
✅ Works
✅ Tested
✅ Success on your system
➡️ Copy-paste exactly this:
pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {

        stage('git repo & clean') {
            steps {
                bat "git clone https://github.com/mokshitha10/MavenJava_Project.git"
                bat "mvn clean -f MavenJava_Project"
            }
        }

        stage('install') {
            steps {
                bat "mvn install -f MavenJava_Project"
            }
        }

        stage('test') {
            steps {
                bat "mvn test -f MavenJava_Project"
            }
        }

        stage('package') {
            steps {
                bat "mvn package -f MavenJava_Project"
            }
        }
    }
}

If it is failing go to setting tools add maven home there apache url

⭐ WEEK 9 — SBQ ANSWERS (VERY EASY, SCORE 100%)
Copy-paste these answers into your lab file 🚀

1. Your manager asks you to clean the workspace before building — which stage handles it?
git repo & clean stage
It runs:
mvn clean

2. Where do you provide your GitHub link?
Inside:
bat "git clone <your-repo-link>"
in the git repo & clean stage.

3. If Maven is not configured globally, which stage fails first?
git repo & clean stage
Because it first uses Maven:
mvn clean

4. Pipeline not generating WAR file — which stage is responsible?
package stage
because it executes:
mvn package

5. Tests failed but pipeline continued — what happens?
Jenkins marks build as:
⚠ UNSTABLE
but continues to next stages.

6. Want pipeline to trigger only when GitHub changes occur — where to configure?
In Build Triggers → GitHub hook trigger
and in GitHub webhooks.

7. Replace mvn clean with mvn compile — what changes?
clean removes old files
compile only compiles Java files
No cleaning happens.

8. Folder name is studentapp instead of mavenjava — what to edit?
Replace all:
-f mavenjava
with:
-f studentapp

9. If install fails, do test & package run?
❌ No.
Next stages will not execute.

10. Where to add Tomcat deployment?
Add a new stage after package, example:
stage('deploy') { ... }

11. Why use tools { maven 'MAVEN-HOME' }?
It tells Jenkins which Maven installation to use.

12. How to secure GitHub credentials?
Use:
credentialsId: 'your-id'
or store credentials in Jenkins Credentials Manager.

13. Which plugin enables pipeline { } syntax?
✔ Pipeline: Groovy Plugin
(Workflow plugin)

14. Script uses bat for Windows. What if Jenkins runs on Linux?
Replace:
bat "command"
with:
sh "command"

15. How to stop pipeline if git clone fails?
Already automatic—if clone fails, pipeline stops.
Or use:
bat "git clone ... || exit 1"

16. How to ensure latest code is pulled?
Use:
checkout scm
or always run:
git clone

17. Hello.java must compile every time — what to add?
Add stage:
stage('compile') {
    steps {
        bat "javac Hello.java"
    }
}

18. Tests should stop the pipeline if they fail — where to put mvn test?
Keep in test stage —
Jenkins automatically stops if it fails.

19. Run pipeline every evening at 6 PM — how to set?
Build Triggers →
H 18 * * *

20. Package only if compile succeeds — how?
Stages run in order.
If compile fails → package never runs.

21. Want a .jar file? — what stage to add?
Add:
mvn package -Dpackaging=jar

22. Git clone failing due to credentials — fix?
Use:
git url: '...', credentialsId: 'myCreds'

23. Teammate wants build number in logs — how?
Use:
echo "Build number is ${env.BUILD_NUMBER}"



























⭐ WEEK 10 — WORKING WITH MINIKUBE, KUBERNETES & NAGIOS

⭐ 1. Aim
To deploy and manage applications using Minikube (Kubernetes), scale pods, expose services, monitor systems using Nagios, and create an AWS free-tier account.

⭐ 2. Tools Used
Minikube
kubectl
Docker Desktop
Nagios Monitoring Tool
AWS Free Tier

⭐ 3. Concepts Overview
🔵 Kubernetes
A tool to automatically run, restart, scale, and manage containers.
🔵 Pod
Smallest deployable unit in Kubernetes.
A Pod contains one or more containers.
🔵 Minikube
A lightweight local Kubernetes cluster for practice.
🔵 Nagios
A monitoring tool that tracks:
Servers
Services
Applications
Alerts

⭐ 4. MINIKUBE INSTALLATION (EASY METHOD)
✔ Step 1 — Open PowerShell as Administrator
Search → PowerShell → Right-click → Run as Administrator
✔ Step 2 — Install Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; `
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
✔ Step 3 — Install Minikube
choco install minikube -y
✔ Step 4 — Install kubectl
choco install kubernetes-cli -y

⭐ 5. START MINIKUBE
If Docker Desktop is installed:
minikube start --driver=docker
Check status:
minikube status
If running → continue.

⭐ 6. DEPLOY NGINX APPLICATION IN KUBERNETES
✔ Step 1 — Create Deployment
kubectl create deployment mynginx --image=nginx
✔ Step 2 — Check Deployment & Pods
kubectl get deployments
kubectl get pods
✔ Step 3 — Describe Deployment
kubectl describe deployment mynginx

⭐ 7. EXPOSE THE DEPLOYMENT
Expose Nginx to port 80:
kubectl expose deployment mynginx --type=NodePort --port=80
Check service:
kubectl get svc

⭐ 8. SCALE THE DEPLOYMENT
Scale to 4 replicas:
kubectl scale deployment mynginx --replicas=4
Check pods:
kubectl get pods
You should see 4 Running pods.

⭐ 9. ACCESS THE NGINX PAGE
Method 1 — Port Forward
kubectl port-forward svc/mynginx 8081:80
Open:
http://localhost:8081
Method 2 — Using Minikube
minikube service mynginx --url
Open the generated URL.

⭐ 10. MINIKUBE DASHBOARD (OPTIONAL)
minikube dashboard

⭐ 11. CLEANUP
kubectl delete deployment mynginx
kubectl delete service mynginx
minikube stop

⭐ 12. NAGIOS USING DOCKER
✔ Step 1 — Pull Nagios Image
docker pull jasonrivers/nagios:latest
✔ Step 2 — Run Nagios
docker run --name nagiosdemo -p 8888:80 jasonrivers/nagios:latest
✔ Step 3 — Access Dashboard
Open browser:
http://localhost:8888
Login:
Username: nagiosadmin
Password: nagios
Inside you can view:
Hosts
Services
Alerts
✔ Step 4 — Stop Nagios
docker stop nagiosdemo
docker rm nagiosdemo

⭐ 13. AWS FREE TIER ACCOUNT CREATION STEPS
1.Open
2.https://aws.amazon.com
3.Click Create AWS Account
4.Enter email, name, and password
5.Enter OTP sent to your email
6.Provide address details
7.Provide card details (₹2 refunded)
8.Phone number → SMS verification
9.Choose Basic Plan (Free Tier)
10.Login → Select role: Student
11.Interest: DevOps
AWS Console opens.

⭐ 14. SBQ (VERY SHORT ANSWERS)
1. Pod keeps restarting. What to do?
Check logs:
kubectl logs podname
2. Pod stuck in Pending. Why?
No resources.
Check:
kubectl describe pod
3. Debug failed deployment:
kubectl describe deployment myapp
kubectl get events
4. Pods failing health checks:
Check probes using:
kubectl describe pod
5. Rollback faulty deployment:
kubectl rollout undo deployment/myapp
6. Debug running pod:
kubectl exec -it podname -- bash
7. Expose service externally:
kubectl expose deployment myapp --type=NodePort --port=80
8. Start & Stop Nagios:
Start → docker run command
Stop:
docker stop nagiosdemo
9. Nagios shows “Unable to connect to process”:
Restart container.
10. New host not appearing:
Check config files in:
/usr/local/nagios/etc/objects/
11. Check Nagios running:
docker ps
12. View Nagios logs:
docker logs -f nagiosdemo
13. Advantages of Nagios:
Alerts
Service monitoring
Dashboard
Plugin support


















⭐ WEEK 11 – PART 1: Jenkins CI using GitHub Webhooks (Detailed, Simple Explanation)
This part explains how GitHub automatically triggers Jenkins whenever you push code.

🧩 1. Why do we use Webhooks?
Normally Jenkins pulls (checks) GitHub again and again to see if there is any update.
This wastes time.
Webhooks solve it:
👉 GitHub pushes a notification instantly to Jenkins
👉 Jenkins automatically starts the build
👉 No need to click “Build Now”
This is Continuous Integration (CI).

🧩 2. Why ngrok is needed?
GitHub needs to send a message to Jenkins.
But Jenkins running on localhost cannot be accessed by GitHub, because it is inside your PC.
ngrok creates a public internet URL → which connects to → your local Jenkins.
Example:
https://offerable-unprovidentially-elyse.ngrok-free.dev -> http://localhost:8080
Now GitHub can reach your Jenkins.

🧩 3. Steps to set up Webhook Integration
Step 1: Start ngrok tunnel
Run:
ngrok http 8080
You get a public URL like:
https://offerable-unprovidentially-elyse.ngrok-free.dev
This becomes your Jenkins URL for GitHub.

Step 2: Add Webhook in GitHub
GitHub → Repo → Settings → Webhooks → Add Webhook
Fill:
✔ Payload URL
https://<ngrok-url>/github-webhook/
✔ Content type
application/json
✔ Trigger
Just the push event
👉 Click Add Webhook
GitHub will show a green ✔ if successful.

Step 3: Configure Jenkins Job
Jenkins → Your Job → Configure → Build Triggers
Enable:
✔ GitHub hook trigger for GITScm polling
Save.
This tells Jenkins:
“When GitHub sends a signal, start the build automatically.”

Step 4: Test the CI pipeline
1.Edit any file in the GitHub repo (ex: README.md)
2.Commit and push
3.Jenkins will automatically start a build
4.Console Output will show:
Started by GitHub push by mokshitha10
This confirms CI is working.

Here is everything from Week 11 explained clearly, briefly, and neatly — exactly as your lab wants.
I took all content from your uploaded file and rewrote it in clean, easy-to-understand steps.
📌 Cited from your file: 

🌟 WEEK 11 — JENKINS CI/CD + WEBHOOK + EMAIL SETUP (COMPLETE NOTES)
(Very easy, very neat, very clear)

🔵 PART 1 — CI USING GITHUB WEBHOOKS
✅ Goal:
Whenever you push code to GitHub → Jenkins should automatically build the project.

Step 1 — Configure Webhook in GitHub 
1️⃣ Open your GitHub repository
➡ Go to Settings → Webhooks
2️⃣ Click Add Webhook
3️⃣ In Payload URL, enter:
https://<YOUR_NGROK_URL>/github-webhook/
4️⃣ Set:
Content type: application/json
Events: ✔ Just the push event
5️⃣ Click Add Webhook

🔵 PART 2 — Setup & Run ngrok (to expose Jenkins to the internet)
(Because GitHub cannot access localhost directly)
1️⃣ Download ngrok
https://ngrok.com/download
2️⃣ Extract zip → you will get ngrok.exe
3️⃣ Add your auth token
Copy token from ngrok → Your Authtoken
Run in CMD:
ngrok config add-authtoken <your_token>
4️⃣ Start tunnel for Jenkins (port 8080)
ngrok http 8080
5️⃣ You will see:
Forwarding https://something.ngrok-free.dev -> http://localhost:8080
👉 Copy the HTTPS URL.
👉 Use that URL in your GitHub webhook.

🔵 PART 3 — Jenkins Accepts Webhooks 
1️⃣ Open Jenkins → your Job → Configure
2️⃣ Scroll to Build Triggers
Tick:
✔ GitHub hook trigger for GITScm polling
3️⃣ Save

🔵 PART 4 — TEST THE WEBHOOK
1️⃣ Edit any file in your repo
2️⃣ git add → git commit → git push
3️⃣ GitHub sends webhook → Jenkins receives it → Build starts automatically
🎉 WEBHOOK SUCCESSFUL

🌟 RESULT:
You created full CI automation:
GitHub Push → Webhook → Jenkins Build.

🟣 PART 5 — EMAIL NOTIFICATIONS (SUCCESS/FAILURE)
Step 1 — Generate Gmail App Password
(Normal password won’t work)
1️⃣ Go to:
https://myaccount.google.com
2️⃣ Enable 2-Step Verification
(Settings → Security → 2-Step Verification)
3️⃣ Create an App Password
Security → App Passwords
App: Other
Name: Jenkins
Click Generate
🔑 Copy the 16-digit password.

Step 2 — Install Plugin in Jenkins
Manage Jenkins → Manage Plugins
Install:
✔ Email Extension Plugin

Step 3 — Configure Global Email in Jenkins
Go to:
Manage Jenkins → Configure System
Fill:
Field	Value
SMTP Server	smtp.gmail.com
Use SMTP Auth	✔
Username	your Gmail
Password	your App Password
Use SSL	✔
SMTP Port	465
🔹 Click Test Configuration
You should receive a test mail.

Step 4 — Enable Email in a Job
Inside your job:
Post-Build Actions → Editable Email Notification
Fill:
Recipient list → your email
Trigger → ✔ Failure, ✔ Success
Content → default is fine
💾 Save
🎉 Now Jenkins sends email on success/failure.

🟢 PART 6 — UML DIAGRAMS REQUIRED
Here is the simplest, cleanest guide to draw UML diagrams in StarUML step-by-step.
Follow this and you’ll be able to create Use Case, Class, Sequence, and Component diagrams easily.

⭐ HOW TO DRAW UML IN STARUML (VERY EASY STEPS)

⭐ 1. OPEN STARUML
Just open the StarUML application.

⭐ 2. CREATE A NEW PROJECT
Click File → New
A blank project opens.

⭐ 3. ADD A DIAGRAM
Left side → Model Explorer
Right-click on Model → Add Diagram
You will see options for:
✔ Use Case Diagram
✔ Class Diagram
✔ Sequence Diagram
✔ Component Diagram
✔ Activity Diagram
… and many more.
Select the one you want.

🌸 NOW I WILL TEACH YOU HOW TO DRAW EACH DIAGRAM 👇

⭐ USE CASE DIAGRAM
Step 1 — Create Use Case diagram
Model → Right-click → Add Diagram → Use Case Diagram
Step 2 — Add Actors
Top Toolbar → Click little stick-man icon (actor)
Click on the canvas to place it.
Step 3 — Add Use Cases
Toolbar → Click Oval icon → place it
Step 4 — Rename
Double-click names → example:
Actor: User
Use case: Upload Image
Step 5 — Connect
Toolbar → click Association line → click actor → click use case.
✔ Done.

⭐ CLASS DIAGRAM
Step 1 — Create Class diagram
Model → Add Diagram → Class Diagram
Step 2 — Add Classes
Toolbar → Class icon
Place it on canvas
Double-click to rename
Add attributes & methods like:
User
---------
id
email
password
---------
login()
register()
Step 3 — Draw Relationships
Toolbar → choose:
Association
Generalization (inheritance)
Aggregation
Composition
Click class → drag to another class.
✔ Done.

⭐ SEQUENCE DIAGRAM
Step 1 — Create Sequence diagram
Model → Add Diagram → Sequence Diagram
Step 2 — Add Lifelines
Toolbar → Lifeline icon
Place multiple lifelines:
User
Frontend
Backend
ML Service
Database
Step 3 — Add Messages
Toolbar → Message arrow
Drag from one lifeline to another.
Example:
User → Frontend: Upload Image
Frontend → Backend: POST /predict
Backend → ML Service: predict()
Step 4 — Return messages
Use dashed arrow for response.
✔ Done.

⭐ COMPONENT DIAGRAM
Step 1 — Add Component Diagram
Model → Add Diagram → Component Diagram
Step 2 — Add Components
Toolbar → click Component icon (looks like a rectangle with two rectangles on left)
Add:
React Frontend
Backend API
ML Service
MongoDB
Auth service
Step 3 — Connect
Use Dependency arrows to show communication.
✔ Done.

⭐ EXPORT YOUR UML DIAGRAMS
When a diagram is complete:
1. Go to File → Export Diagram → as PNG/JPG/PDF
2. Save
3. Add to your Lab Report

⭐ IF YOU WANT
I can also:
✔ Draw your UML diagrams FOR YOU
✔ Export them as PNG/PDF
✔ Based on your project (Calorie Detector app)
Just tell me:
“Create UML diagrams for my project.”


🟡 IMPORTANT VIVA QUESTIONS (SHORT ANSWERS)
1️⃣ What is CI?
Continuous Integration = automatically building and testing code when changes occur.
2️⃣ What is CD?
Continuous Delivery/Deployment = automatically deploying code after CI.
3️⃣ Role of Jenkins?
Automates CI/CD pipeline.
4️⃣ What is a Webhook?
A callback URL GitHub uses to notify Jenkins automatically after a push.
5️⃣ Why use Webhooks instead of polling?
Webhook = instant, faster
Polling = slow, checks again and again
6️⃣ What is ngrok?
A tool that exposes localhost to the internet using a public temporary URL.
7️⃣ Why ngrok?
GitHub cannot access your local Jenkins, so ngrok creates a public link.
8️⃣ Why email notifications?
To inform developers immediately when builds fail or succeed.






















🌟 WEEK 12 – FULL LAB (EXTREMELY EASY STEPS)
1. Deploy index.html on AWS EC2 using Docker

🟦 STEP 1 — Login to AWS Academy
1.Open your course invitation email → click Start.
2.Sign in to AWS Academy with your student account.
3.Go to Modules → AWS Academy Learner Lab.
4.Click Start Lab.
5.Wait until the red AWS turns green → lab is ready.

🟦 STEP 2 — Create EC2 Instance
1.Click AWS (top left).
2.Search for EC2 → open it.
3.Click Launch Instance.
4.Fill these:
✔ Stage 1 → Instance Name
ubuntu-webserver
✔ Stage 2 → Choose AMI
Select: Ubuntu Server 20.04 LTS (Free Tier Eligible)
✔ Stage 3 → Architecture
Choose: 64-bit (x86)
✔ Stage 4 → Instance Type
t2.micro (free tier)
✔ Stage 5 → Create Key Pair
Click Create new key pair
Name: aws-key
Format: .pem
Download file → keep it safe
✔ Stage 6 → Network / Security Group
Tick all checkboxes:
✔ SSH
✔ HTTP
✔ HTTPS
(so your website loads)
✔ Stage 7 → Storage
Keep 8GB default
✔ Stage 8 → Launch Instance
Click Launch
Go to Instances → wait until Running + 2/2 checks passed

🟦 STEP 3 — Connect to EC2 via SSH
1.Select the instance → click Connect.
2.Choose SSH Client tab.
3.Copy the command:
4.ssh -i "aws-key.pem" ubuntu@<public-ip>
5.Open PowerShell as Administrator.
6.Go to folder where your .pem file is stored:
7.cd <your pem folder>
8.Paste the ssh command → press Enter.
You are now inside the Ubuntu server.

🟦 STEP 4 — Install Software on Ubuntu
Run these commands one by one:
✔ Update Ubuntu
sudo apt update
✔ Install Docker
sudo apt-get install docker.io
✔ Install Git
sudo apt install git
✔ Install nano editor
sudo apt install nano

🟦 STEP 5 — Create Web App & Push to GitHub
✔ A. Create a folder locally
Inside it, create:
index.html
✔ B. Open Git Bash inside folder
Run:
git init
git add .
git commit -m "first commit"
✔ C. Create new GitHub repo
Copy the HTTPS URL.
✔ D. Push your code
git branch -M main
git remote add origin <repo-url>
git push -u origin main
Your index.html is now in GitHub.

🟦 STEP 6 — Clone Repo on EC2
In the EC2 terminal:
git clone <your-repo-url>
cd <repo-folder>

🟦 STEP 7 — Create Dockerfile on EC2
Run:
nano Dockerfile
Paste this:
FROM nginx:latest
COPY . /usr/share/nginx/html
Save:
CTRL+O → Enter
CTRL+X

🟦 STEP 8 — Build & Run Docker Container
✔ Build Image
sudo docker build -t mywebapp .
✔ Run Container
sudo docker run -d -p 80:80 mywebapp

🟦 STEP 9 — View Website in Browser
1.Go to EC2 → Instances → copy Public IPv4 address
2.Paste in browser:
http://<your-public-ip>
Your index.html page should load.

🟦 STEP 10 — Stop Container
sudo docker ps
sudo docker stop <container-id>

🟦 STEP 11 — Terminate EC2 Instance
EC2 → select instance → Instance State → Terminate
You are done with Exercise 1.

🌟 EXERCISE 2 — Maven Web Project Deployment on EC2

🟣 Steps (Very Short & Clear)
✔ Create new EC2 instance
Same steps as Exercise 1 (Ubuntu + KeyPair + Security group + Launch).
✔ SSH into instance
Use the ssh -i command again.
✔ Install software
sudo apt update
sudo apt install git
sudo apt install docker.io
✔ Clone MAVEN WEB PROJECT from GitHub
Copy your repo link
git clone <maven-repo-url>
cd <project-folder>
✔ If your branch is not main
Change default branch in GitHub settings → set master to default.
✔ Build Docker image for Maven web app
sudo docker build -t mymavenapp .
✔ Run container on port 9090
sudo docker run -d -p 9090:8080 mymavenapp
✔ Open public IP with port
http://<public-ip>:9090
❗ If app does NOT load
Go to:
EC2 → Security Groups → Edit Inbound Rules → Add:
Custom TCP  |  9090  |  0.0.0.0/0
Save and refresh browser.
✔ Stop container
sudo docker ps
sudo docker stop <container-id>
✔ Terminate instance
EC2 → Instance → Terminate

