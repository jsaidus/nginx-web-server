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

Successfully implemented and tested GitHub Actions CI and CD workflows. Automated HTML validation, secure SCP deployment to Ubuntu Server, and post-deployment SSH/HTTP verification have completed successfully.
## Automated CI/CD Pipeline — GitHub Actions

### Overview

This project extends a manually configured Ubuntu and Nginx web server into an automated deployment environment using GitHub Actions.

The project demonstrates Linux administration, Git version control, continuous integration, continuous deployment, SSH authentication, and deployment verification.

### Architecture

```text
Developer / Pop!_OS
        |
        v
GitHub Repository
        |
        +---------------------------+
        |                           |
        v                           v
CI Workflow                    CD Workflow
GitHub-hosted Runner           Self-hosted Linux Runner
        |                           |
Check index.html               Checkout Repository
Validate HTML Content               |
        |                      Secure SCP Transfer
        v                           |
CI Result                      Ubuntu Server
                                    |
                               Nginx Web Server
                                    |
                            SSH + HTTP Verification
```

### Continuous Integration (CI)

Workflow: `.github/workflows/ci.yml`

The CI pipeline runs on GitHub-hosted Ubuntu runners when code is pushed to `main` or a pull request targets `main`.

The pipeline:

1. Checks out the repository.
2. Verifies that `index.html` exists.
3. Checks for required HTML tags.
4. Verifies the expected DevOps content.
5. Reports successful validation.

### Continuous Deployment (CD)

Workflow: `.github/workflows/deploy.yml`

The deployment workflow uses a self-hosted Linux runner to transfer the website to an Ubuntu server.

Deployment command:

```bash
scp -i ~/.ssh/devops_deploy \
  -o BatchMode=yes \
  -o StrictHostKeyChecking=yes \
  index.html deploy@192.168.56.101:/var/www/html/index.html
```

### Deployment Verification

The workflow uses SSH to confirm that the deployed HTML file exists and that the local Nginx HTTP service responds successfully.

Verification includes:

```bash
test -s /var/www/html/index.html
curl -fsS http://localhost/ > /dev/null
```

Successful verification produces:

```text
Nginx deployment successful!
```

### Verified Results

- GitHub Actions CI validation completed successfully.
- GitHub Actions deployment workflow completed successfully.
- Secure SCP file transfer succeeded.
- Remote SSH verification completed successfully.
- The Nginx HTTP endpoint responded successfully.

### Skills Demonstrated

- Ubuntu Server administration
- VirtualBox virtual networking
- Nginx web server configuration
- Git and GitHub
- GitHub Actions CI/CD
- Self-hosted runners
- Bash scripting
- SSH key authentication
- Secure file transfer using SCP
- Automated deployment verification
- Technical troubleshooting

### Future Improvements

- Make deployment conditional on successful CI checks.
- Add comprehensive HTML validation.
- Introduce automated deployment rollback.
- Improve monitoring and logging.
- Add deployment tests for website content.
- Expand security checks for the CI/CD pipeline.
