# Current Stable Tools for CI/CD

Widely used, actively maintained tools across each stage of a CI/CD pipeline.

> **How do these fit together?** See the [Integration Guide](INTEGRATION_GUIDE.md) for the full flow diagram and step-by-step configuration.

![CI/CD tools integration flow](../resources/cicd_tools_integration_flow.svg)

## CI/CD Platforms

| Tool | Type | Notes |
|------|------|-------|
| [GitHub Actions](https://github.com/features/actions) | Hosted | Native to GitHub, YAML workflows, huge marketplace |
| [GitLab CI/CD](https://docs.gitlab.com/ee/ci/) | Hosted / Self-hosted | Built into GitLab, strong DevSecOps features |
| [Jenkins](https://www.jenkins.io/) | Self-hosted | Open source, plugin ecosystem, Jenkinsfile pipelines |
| [CircleCI](https://circleci.com/) | Hosted | Fast builds, orbs for reusable config |
| [Azure Pipelines](https://azure.microsoft.com/products/devops/pipelines) | Hosted | Part of Azure DevOps, multi-platform |
| [Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) | Hosted | Built into Bitbucket |
| [AWS CodePipeline](https://aws.amazon.com/codepipeline/) | Hosted | Native AWS, pairs with CodeBuild/CodeDeploy |

## Source Control

| Tool | Notes |
|------|-------|
| [Git](https://git-scm.com/) | Version control standard |
| [GitHub](https://github.com/) / [GitLab](https://gitlab.com/) / [Bitbucket](https://bitbucket.org/) | Repository hosting |

## Build & Package (Node.js)

| Tool | Notes |
|------|-------|
| [Node.js LTS](https://nodejs.org/) | Always use an LTS release in pipelines |
| [npm](https://www.npmjs.com/) | Use `npm ci` for reproducible installs |
| [pnpm](https://pnpm.io/) | Fast, disk-efficient package manager |
| [Yarn](https://yarnpkg.com/) | Alternative package manager |

## Testing & Code Quality

| Tool | Notes |
|------|-------|
| [Jest](https://jestjs.io/) / [Vitest](https://vitest.dev/) | Unit testing |
| [Playwright](https://playwright.dev/) / [Cypress](https://www.cypress.io/) | End-to-end testing |
| [ESLint](https://eslint.org/) / [Prettier](https://prettier.io/) | Linting and formatting |
| [SonarQube](https://www.sonarsource.com/products/sonarqube/) | Code quality and static analysis |

## Security Scanning

| Tool | Notes |
|------|-------|
| [Trivy](https://trivy.dev/) | Container image, filesystem, and IaC scanning |
| [Snyk](https://snyk.io/) | Dependency and container vulnerabilities |
| [Dependabot](https://docs.github.com/code-security/dependabot) | Automated dependency updates |
| [CodeQL](https://codeql.github.com/) | Semantic code analysis on GitHub |
| [Gitleaks](https://github.com/gitleaks/gitleaks) | Detect secrets committed to repos |

## Containers & Registries

| Tool | Notes |
|------|-------|
| [Docker](https://www.docker.com/) | Build and run containers |
| [Docker Compose](https://docs.docker.com/compose/) | Multi-container local/server setups |
| [Docker Hub](https://hub.docker.com/) | Public/private image registry |
| [GitHub Container Registry (GHCR)](https://docs.github.com/packages/working-with-a-github-packages-registry/working-with-the-container-registry) | Registry tied to GitHub |
| [Amazon ECR](https://aws.amazon.com/ecr/) | AWS image registry |

## Orchestration & Deployment

| Tool | Notes |
|------|-------|
| [Kubernetes](https://kubernetes.io/) | Container orchestration |
| [Helm](https://helm.sh/) | Kubernetes package manager |
| [Argo CD](https://argo-cd.readthedocs.io/) | GitOps continuous delivery for Kubernetes |
| [Flux](https://fluxcd.io/) | GitOps toolkit for Kubernetes |
| [PM2](https://pm2.keymetrics.io/) | Node.js process manager on VPS |

## Infrastructure as Code & Config

| Tool | Notes |
|------|-------|
| [Terraform](https://www.terraform.io/) / [OpenTofu](https://opentofu.org/) | Provision cloud infrastructure |
| [Ansible](https://www.ansible.com/) | Server configuration and deployment |
| [Pulumi](https://www.pulumi.com/) | IaC in real programming languages |

## Web Server, Proxy & SSL

| Tool | Notes |
|------|-------|
| [Nginx](https://nginx.org/) | Reverse proxy, load balancer |
| [Caddy](https://caddyserver.com/) | Web server with automatic HTTPS |
| [Traefik](https://traefik.io/) | Cloud-native reverse proxy for containers |
| [Certbot / Let's Encrypt](https://certbot.eff.org/) | Free SSL certificates |

## Secrets Management

| Tool | Notes |
|------|-------|
| [GitHub Secrets](https://docs.github.com/actions/security-guides/using-secrets-in-github-actions) | Encrypted secrets for Actions |
| [HashiCorp Vault](https://www.vaultproject.io/) | Centralized secrets management |
| [AWS Secrets Manager](https://aws.amazon.com/secrets-manager/) | Managed secrets on AWS |

## Monitoring & Logging

| Tool | Notes |
|------|-------|
| [Prometheus](https://prometheus.io/) | Metrics collection |
| [Grafana](https://grafana.com/) | Dashboards and alerting |
| [Loki](https://grafana.com/oss/loki/) / [ELK Stack](https://www.elastic.co/elastic-stack) | Log aggregation |
| [Sentry](https://sentry.io/) | Error tracking |
| [Uptime Kuma](https://github.com/louislam/uptime-kuma) | Self-hosted uptime monitoring |

## Typical Node.js Pipeline Stack

```
Git → GitHub Actions → npm ci + Jest + ESLint → Trivy → Docker → GHCR/Docker Hub → VPS (Docker Compose / PM2) → Nginx + Certbot → Grafana/Uptime Kuma
```
