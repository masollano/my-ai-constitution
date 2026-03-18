# Infrastructure & DevOps Context

## Environments

* Windows Server (IIS, nginx for Windows)
* Linux Ubuntu Servers (nginx)

## Reverse Proxy

* nginx (primary)
* IIS (secondary in Windows environments)

## CI/CD

* Jenkins (primary pipeline tool)
* Self-hosted Git (Gogs)

## Deployment Characteristics

* Multi-environment deployments
* Manual + evolving CI/CD pipeline
* Reverse proxy routing across services

## Expectations

When discussing DevOps / CI-CD:

* Prefer solutions compatible with Jenkins
* Avoid GitHub Actions / GitLab-specific assumptions
* Consider both Windows and Linux deployment targets
* Account for reverse proxy configurations

## Focus Areas

* Deployment reliability
* Pipeline automation
* Environment consistency
* System observability (logs, monitoring)
