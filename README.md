
 Healthcare Project – Resilient Deployment & Monitoring

In healthcare, consistency and oversight are critical. This project demonstrates a fully automated system where the application is deployed safely, and the system’s health is always visible. Manual setup or accidental downtime is completely avoided through automation.

🚀 How It Operates
Infrastructure

--> Terraform provisions three servers:

--> Master Node – orchestrates automation and manages deployments.

--> Worker Node – runs the healthcare application.

--> Monitoring Node – gathers metrics and tracks system performance.

⚙️ Setup & Deployment

--> Ansible installs and configures all essential software on the Master node.

--> Developers push updates to Git.

--> Jenkins automates the build process.

--> Docker packages the application into containers.

--> Kubernetes deploys and runs the app on the Worker node.

📊 Observability

--> Prometheus collects real-time system metrics.

--> Grafana visualizes performance and operational health.

🔄 Workflow

--> Terraform → Creates Master, Worker, and Monitoring servers.

--> Ansible → Configures the Master node with all necessary tools.

--> Jenkins → Builds the application from Git commits.

--> Docker → Packages the application into containers.

--> Kubernetes → Deploys the app on the Worker node.

--> Prometheus + Grafana → Monitor system metrics and health.

🌐 Application Access

The healthcare application runs on port 3007.
  
 ```
              ┌─────────────────────────┐
              │       Developers        │
              │   Push code to GitHub   │
              └─────────────┬───────────┘
                            │
                            ▼
              ┌─────────────────────────┐
              │        Master Node       │
              │  (Provisioned by IaC -   │
              │   Terraform + Ansible)   │
              ├─────────────────────────┤
              │ Jenkins  | CI/CD         │
              │ Docker   | Build Images  │
              │ K8s Ctrl | Manage Cluster│
              └──────────┬───────────────┘
                         │ Schedules Pods
                         │
                         ▼
              ┌─────────────────────────┐
              │        Worker Node       │
              │ (K8s Kubelet + Pod runs) │
              │   Application on :8080   │
              └─────────────────────────┘
                         │
       ┌─────────────────┴─────────────────┐
       │                                   │
       ▼                                   ▼
┌─────────────────────────┐         ┌─────────────────────────┐
│   Monitoring Node        │        │    End Users            │
│ (Prometheus + Grafana)   │ <────► │ Access App on :8080     │
│ Collect & visualize data │        │ Banking Web Application │
└─────────────────────────┘         └─────────────────────────┘



 ```  
