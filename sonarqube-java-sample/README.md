# SonarQube Java Sample Lab

## Overview

This lab shows how I, Azeem Hafeez M, set up SonarQube on an Ubuntu 22.04 server in AWS and analyzed a simple Java Maven project using SonarQube.

## Objectives

- Launch an Ubuntu 22.04 EC2 instance and open required ports (22 for SSH, 9000 for SonarQube).
- Install Java 17 and SonarQube on the server.
- Create a simple Java Maven project.
- Analyze the project with SonarQube and view code quality issues.

## Prerequisites

- AWS account.
- Windows 10/11 laptop.
- Git Bash installed (from Git for Windows).
- Java 17 (OpenJDK) installed and configured.
- Apache Maven installed and on the PATH.
- GitHub account.

## Part 1 – SonarQube on AWS (to be done)

1. Create EC2 instance:
   - AMI: Ubuntu Server 22.04 LTS.
   - Instance type: t2.medium.
   - Security group: allow SSH (22) from my IP, custom TCP (9000) from 0.0.0.0/0.
2. Connect via SSH from Git Bash:
   - `ssh -i my-key.pem ubuntu@<EC2_PUBLIC_IP>`
3. Install Java and unzip:
   - `sudo apt update -y`
   - `sudo apt install openjdk-17-jre unzip -y`
4. Download and run SonarQube:
   - `wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.3.0.82913.zip`
   - `unzip sonarqube-10.3.0.82913.zip`
   - `cd sonarqube-10.3.0.82913/bin/linux-x86-64/`
   - `./sonar.sh start`
5. Access web UI:
   - Browser: `http://<EC2_PUBLIC_IP>:9000`
   - Login: admin / admin, then change password.

## Part 2 – Java Maven Project

1. Clone repo from GitHub:
   - `git clone https://github.com/hafeesumahju-star/sonarqube-java-sample.git`
2. Generate Maven project:
   - `mvn archetype:generate -DgroupId=com.example -DartifactId=sonarqube-java-sample -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false`
3. Build:
   - `cd sonarqube-java-sample`
   - `mvn clean package`

## Part 3 – SonarQube Analysis (to be done)

1. In SonarQube UI, create a new project (manually) with key `sonarqube-java-sample`.
2. Choose "Locally" and copy the Maven command with the token.
3. From the project folder, run:
   - `mvn clean verify sonar:sonar -Dsonar.projectKey=sonarqube-java-sample -Dsonar.host.url=http://<EC2_PUBLIC_IP>:9000 -Dsonar.login=<TOKEN>`
4. Open SonarQube UI → Projects → view bugs, vulnerabilities, and code smells.

## Screenshots

Later I will add screenshots of:
- SonarQube dashboard.
- Issues list for this project.
