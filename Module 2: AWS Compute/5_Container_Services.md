# Container Services

## What are Containers?

**Container:** Standardized unit packaging code and dependencies to run reliably on any platform

### Key Benefits
- **Portability** - Run anywhere (dev, test, prod, on-premises, cloud)
- **Fast startup** - Almost instant compared to VMs
- **Lightweight** - Share host OS and kernel
- **Consistency** - Same environment across deployments

## Containers vs Virtual Machines

| Aspect | Containers | Virtual Machines |
|--------|------------|------------------|
| **OS** | Share host OS/kernel | Each has own OS |
| **Startup** | Almost instant | Minutes |
| **Resources** | Lightweight | More overhead |
| **Isolation** | Process-level | Hardware-level |

## Container Orchestration

### Challenges at Scale
- Container placement on instances
- Handling container/instance failures
- Monitoring deployments
- Auto-scaling

### AWS Solutions
- **Amazon ECS** - AWS native orchestration
- **Amazon EKS** - Managed Kubernetes

## Amazon ECS (Elastic Container Service)

### Key Components
- **Task Definition** - JSON blueprint describing containers
- **Task** - Running instance of task definition
- **Service** - Manages multiple tasks
- **Container Instance** - EC2 with ECS agent

### Hosting Options
- **EC2 instances** - More control, manage infrastructure
- **AWS Fargate** - Serverless, AWS manages infrastructure

### Sample Task Definition
```json
{
  "family": "webserver",
  "containerDefinitions": [{
    "name": "web",
    "image": "nginx",
    "memory": "100",
    "cpu": "99"
  }],
  "requiresCompatibilities": ["FARGATE"],
  "networkMode": "awsvpc",
  "memory": "512",
  "cpu": "256"
}
```

## Amazon EKS (Elastic Kubernetes Service)

### Overview
- Managed Kubernetes service
- No need to install/maintain Kubernetes control plane
- Compatible with existing Kubernetes tools

### Key Differences from ECS
| Component | ECS | EKS |
|-----------|-----|-----|
| **Compute** | Container Instance | Worker Node |
| **Workload** | Task | Pod |
| **Technology** | AWS Native | Kubernetes |

### Best For
- Existing Kubernetes users
- Advanced orchestration needs
- Fine-grained infrastructure control