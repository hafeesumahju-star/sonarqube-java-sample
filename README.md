# SonarQube + Ansible Java Sample Lab

## Overview
Azeem Hafeez M's end-to-end lab: SonarQube on AWS EC2 + Java Maven analysis + Ansible automation from WSL.

## SonarQube Setup (Completed)
- EC2: Ubuntu 24.04, t3.medium, Mumbai (dynamic IP: latest 65.0.17.13)
- Install: Java 17, SonarQube 10.3, kernel tuning, swap
- UI: http://65.0.17.13:9000 (admin pw changed)
- Steps/screenshots: See below.

## Java Maven Project
- Repo: https://github.com/hafeesumahju-star/sonarqube-java-sample
- Build: mvn clean package
- Analysis: mvn sonar:sonar -Dsonar.projectKey=sonarqube-java-sample -Dsonar.host.url=http://65.0.17.13:9000 -Dsonar.login=<token>

## Ansible Extension (New)
- Control node: WSL Ubuntu on Windows
- Managed node: SonarQube EC2
- Playbook: install_packages.yml (apt: htop, git)
- Inventory: inventory.ini
- Test: ansible-playbook -i inventory.ini install_packages.yml
- Ping: SUCCESS "pong"

## Detailed Steps
[Keep original Part 1-3 from remote, update IP to 65.0.17.13]

## Screenshots
[Keep all images refs]

## Skills
- AWS EC2, Linux admin, SonarQube, Maven, GitHub
- Ansible: inventory, SSH keys, apt module, playbooks [web:13]
