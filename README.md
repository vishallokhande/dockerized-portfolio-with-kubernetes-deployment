# Cloud-Native Portfolio Website with CI/CD Automation & Kubernetes Deployment
# Cloud-Native Portfolio Website with CI/CD Automation & Kubernetes Deploymento – Cloud-Native Website Project

Welcome! This is my personal portfolio website, deployed using modern DevOps tools and cloud technology:
- **Git & GitHub**
- **GitHub Actions (CI/CD)**
- **Docker & Docker Hub**
- **AWS EC2**
- **Kubernetes** (with Calico networking)

## 🌐 Live Demo
*(If you have a live URL or your AWS public IP, add it here!)*

---

## 🚀 Features

- Simple static site (HTML/CSS/JS)
- Automatically builds & publishes Docker images to Docker Hub via GitHub Actions
- Cloud deployment & orchestration with Kubernetes (single-node EC2)
- Auto-redeploy possible on every code update (CI/CD friendly)

---

## 📦 Project Structure

my-portfolio/
├── index.html
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── .github/
└── workflows/
└── deploy.yml

text

---

## 🛠️ Getting Started

### 1. Clone the Repo

git clone https://github.com/<your-username>/my-portfolio.git
cd my-portfolio

text

### 2. Build and Run Locally (optional)

docker build -t my-portfolio .
docker run -p 8080:80 my-portfolio

Then visit http://localhost:8080
text

---

## ⚙️ GitHub Actions Setup

- On every push to `main`, a GitHub Actions workflow builds and pushes the Docker image to Docker Hub.
- Setup required _repository secrets_:  
  - `DOCKER_USER` (your Docker Hub username)
  - `DOCKER_PASSWORD` (your Docker Hub password or access token)

---

## ☁️ Deployment to AWS EC2 & Kubernetes

**Summary Steps:**
1. Launch a Ubuntu 22.04 EC2 instance with correct security groups (ports 22, 80, 6443)
2. SSH into the instance and install Docker, containerd, kubelet, kubeadm, kubectl
3. Initialize single-node Kubernetes:
    ```
    sudo kubeadm init --pod-network-cidr=10.244.0.0/16
    ```
4. Set up `kubectl` access (per `kubeadm` output)
5. Apply network add-on (Calico):
    ```
    kubectl apply -f https://docs.projectcalico.org/manifests/calico.yaml
    ```
6. Deploy your workload:
    ```
    kubectl apply -f deployment.yaml
    kubectl apply -f service.yaml
    ```
7. Access your website via the public IP (check with `kubectl get svc`).

---

#✍️ Credits

Developed by **Vishal Lokhande**  
Feel free to connect with me on www.linkedin.com/in/vishal-lokhande-devops-engineer.
