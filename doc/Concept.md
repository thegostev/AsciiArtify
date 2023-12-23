In this document you may find a decision making process for selecting a tool for deploying Kubernetes clusters on local environment.

As the result of the rigorous selection process k3d is selected. It’s also important to actively managing technical and legal risks.

| Parameter / Tool | Minikube | Kind (Kubernetes IN Docker) | k3d |
| --- | --- | --- | --- |
| OS Supported | Windows, macOS, Linux | Windows, macOS, Linux | Windows, macOS, Linux |
| Architecture | VM-based (e.g., VirtualBox) | Docker-based | Docker-based |
| Automation Possibilities | Limited (Primarily VM setup) | Moderate (Docker-based) | Moderate (Docker-based) |
| Ease of Deployment | Easy | Easy | Easy |
| Monitoring of K8s Cluster | Basic, integration with addons | External tools integration | External tools integration |
| Management of K8s Cluster | Basic, integration with addons | kubectl, Docker CLI | kubectl, Docker CLI |
| Deployment Speed | Moderate (VM setup time) | Fast | Fast |
| Stability / Resilience | Generally stable  | Stable | Stable |
| Documentation | Well-documented | Well-documented | Well-documented |
| Community Support | Active | Active | Active |
| Ease of Use | User-friendly with GUI (dashboard) | User-friendly with simple commands | User-friendly with simple commands |

# Selected tool

k3d

## Justification

1. Minikube is the only VM-based tool. This type of architecture if it’s not required provides disadvantages comparing to Kind and k3d.
2. While there may be nuanced differences between Kind and k3d, their fundamental design principles contribute to the similarities observed in the comparison table.
    1. Between Kind and k3d I have more experience using k3d.
    2. k3d already used as an infrastructure for PoC.

## Demo

https://github.com/k3d-io/k3d

# Risks

## **Resource Constraints**

[HIGH] Running a Kubernetes cluster within a VM on a local machine imposes resource constraints. Depending on the host machine's capacity, users might experience performance issues or limitations.

## Docker licensing risks

1. [HIGH] **Docker Desktop License for Commercial Use:** Docker Desktop, which is the foundation for Kind and k3d, has a changed license for commercial use after version 2.0. Docker Desktop is a paid product for enterprises and commercial users.
2. [LOW] **License Restrictions and Offline Mode:** Docker may require an internet connection to verify the license.
3. [HIGH] **License for Docker Images:** When using official Docker images for Kubernetes, AsciiArtify should check the licensing terms of these images. Some images may have restrictions or distribution requirements.
4. [HIGH] **Licensing of Docker-Compose and Docker CLI:** If AsciiArtify decides to use Docker-Compose or Docker CLI to manage containers, they should pay attention to the licensing terms for these tools.

## Podman as an alternative to Docker as a licensing risk avoidance strategy

Selected tool k3d is a Docker based tool, Postman can’t be used with it. The same goes for Kind.

If we’d decide to use Podman with Kubernetes, we might want to explore other Kubernetes tools that are designed to work with Podman, such as "k0s" or using a more manual approach with Kubernetes components and Podman containers.

### Proposed risk mitigation strategy is risk transfer

We could transfer Docker licensing risks to a hosting company that’ll provide own infrastructure for Kubernetes deployment.
