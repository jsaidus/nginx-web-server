# Linux Web Server Deployment — DevOps Project 1

## Project Overview

This project demonstrates the deployment and management of an Nginx web server on Ubuntu Server 26.04 LTS, running inside Oracle VirtualBox.

The development workstation uses Pop!_OS Linux, with SSH for remote administration, SCP for secure file transfers, Git for version control, and GitHub for source code hosting.

## Technologies Used

- Ubuntu Server 26.04 LTS
- Pop!_OS Linux
- Oracle VirtualBox
- Nginx
- SSH and SCP
- Git and GitHub
- Visual Studio Code
- HTML and CSS

## Lab Architecture

Development workstation (Pop!_OS)

↓ SSH / SCP

Ubuntu Server VM (VirtualBox)

↓ Nginx Web Server

Local website accessible at `http://192.168.56.101`

GitHub stores the website source code and commit history.

## Implementation Summary

1. Configured an Ubuntu Server virtual machine in VirtualBox.
2. Configured NAT and host-only networking.
3. Verified network connectivity and SSH access.
4. Installed and configured Nginx.
5. Deployed a custom HTML website.
6. Verified the website from the Pop!_OS browser.
7. Transferred the website source code using SCP.
8. Initialized a local Git repository.
9. Configured Git author identity.
10. Created the initial Git commit.
11. Created a GitHub repository and configured a remote.
12. Configured GitHub authentication and pushed the source code.

## Troubleshooting Experience

### Git Author Identity Unknown

**Issue:** Git rejected the initial commit because the author identity was not configured.

**Resolution:** Configured Git `user.name` and `user.email`, then successfully created the commit.

### GitHub HTTP 403 — Permission Denied

**Issue:** GitHub rejected the push operation.

**Resolution:** Reviewed the fine-grained personal access token, selected the correct repository, and granted Contents read/write permission.

### GitHub Authentication Failure

**Issue:** GitHub rejected an authentication attempt using an invalid credential or password.

**Resolution:** Used a properly configured personal access token for HTTPS authentication.

## Skills Demonstrated

- Linux server administration
- Virtual networking
- Remote server management
- Web server deployment
- Secure file transfer
- Git version control
- GitHub repository management
- Authentication and access troubleshooting

## Future Improvements

- Git branching and pull requests
- Automated deployment scripts
- GitHub Actions CI/CD
- Automated testing
- Containerization with Docker
- Monitoring and logging

## Project Status

Initial web server deployment and GitHub integration completed. CI/CD automation is planned.