                 ┌──────────────────────┐
                 │      GitHub Repo     │
                 │  (commit: CI/CD tag) │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌────────────────────────────┐
                 │   GitHub Actions Workflow  │
                 │  - Check commit message    │
                 │  - Trigger local VM        │
                 │    via SSH or Webhook      │
                 └──────────┬─────────────────┘
                            │
            ┌───────────────┴────────────────┐
            │                                │
   ┌────────▼────────┐              ┌────────▼─────────┐
   │  Vagrant (CI)   │              │  Vagrant (CD)    │
   │-----------------│              │------------------│
   │ • Jenkins (opt.)│              │ • Minikube       │
   │ • Docker Compose│              │ • Helm / kubectl │
   │ • SonarQube     │              │ • Deployment test│
   │ • Local ECR     │              │ • Health check   │
   └--------┬--------┘              └--------┬---------┘
            │                                 │
            │                                 │
     ┌──────▼──────┐                    ┌─────▼──────┐
     │ Docker      │                    │ Kubernetes │
     │ Containers  │                    │ Cluster    │
     │ (CI build)  │                    │ (CD deploy)│
     └──────┬──────┘                    └─────┬──────┘
            │                                 │
      ┌─────▼──────┐                     ┌─────▼──────┐
      │  local-ci  │                     │ local-cd   │
      │  result.txt│                     │ success.log│
      └────────────┘                     └────────────┘