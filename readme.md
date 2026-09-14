# ⚡ DevOps Webpage CI/CD

### From `git push` → Jenkins → Docker → Kubernetes → HTTPS

<p align="center">
  <img src="https://img.shields.io/badge/CI%2FCD-Jenkins-red?style=for-the-badge&logo=jenkins&logoColor=white" alt="Jenkins"/>
  <img src="https://img.shields.io/badge/Container-Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Orchestration-Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Kubernetes"/>
  <img src="https://img.shields.io/badge/Local_Cluster-Minikube-9439FF?style=for-the-badge&logo=kubernetes&logoColor=white" alt="Minikube"/>
  <img src="https://img.shields.io/badge/Ingress-NGINX-009639?style=for-the-badge&logo=nginx&logoColor=white" alt="NGINX"/>
  <img src="https://img.shields.io/badge/Protocol-HTTPS-2EA44F?style=for-the-badge&logo=letsencrypt&logoColor=white" alt="HTTPS"/>
</p>

<p align="center">
  <b>A hands-on DevOps project that automates the complete journey of a web application from source-code change to a highly available, autoscaled and HTTPS-enabled Kubernetes deployment.</b>
</p>

---

## 🚀 What This Project Does

This project starts with one intentionally simple webpage and focuses on everything that happens **around the application**.

A developer changes the HTML and pushes to GitHub.

From there, Jenkins takes over:

```text
                    ┌──────────────────────┐
                    │      Developer       │
                    │                      │
                    │   Change index.html  │
                    └──────────┬───────────┘
                               │
                         git push main
                               │
                               ▼
                    ┌──────────────────────┐
                    │       GitHub         │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │       Jenkins        │
                    │                      │
                    │  ① Checkout          │
                    │  ② Docker Build      │
                    │  ③ Container Test    │
                    │  ④ Minikube Load     │
                    │  ⑤ Kubernetes Check  │
                    │  ⑥ Deploy            │
                    └──────────┬───────────┘
                               │
                               ▼
                 ┌───────────────────────────┐
                 │        Kubernetes         │
                 │         Minikube          │
                 │                           │
                 │  ┌─────────────────────┐  │
                 │  │     Deployment      │  │
                 │  │                     │  │
                 │  │  Pod 1    Pod 2     │  │
                 │  │    │        │       │  │
                 │  └────┬────────┬───────┘  │
                 │       │        │          │
                 │       └───┬────┘          │
                 │           ▼               │
                 │       Service             │
                 │           │               │
                 │           ▼               │
                 │    NGINX Ingress          │
                 │           │               │
                 │       TLS / HTTPS         │
                 └───────────┼───────────────┘
                             │
                             ▼
                    🌐 myweb.local
```

### The result

```text
GitHub
   ↓
Automated Jenkins pipeline
   ↓
Versioned Docker image
   ↓
Kubernetes rolling deployment
   ↓
Self-healing application
   ↓
Automatic horizontal scaling
   ↓
NGINX Ingress
   ↓
TLS / HTTPS
   ↓
🌐 Web Application
```

---

# ✨ Why I Built This

The application itself is deliberately simple.

The goal was not to build another complex frontend.

The goal was to understand what happens **after a developer writes code**:

> How does that code become a deployable artifact?
> How is it tested?
> How does Kubernetes deploy it?
> What happens if a pod dies?
> How does a new version reach users?
> How do we roll back?
> How does the application scale?
> How do users access it securely?

This project answers those questions through an actual working implementation.

---

# 🧩 DevOps Capabilities Demonstrated

| Capability              | Implementation               |
| ----------------------- | ---------------------------- |
| 📦 Source Control       | Git + GitHub                 |
| 🔨 CI/CD                | Jenkins Declarative Pipeline |
| 🐳 Containerization     | Docker + NGINX Alpine        |
| ☸️ Orchestration        | Kubernetes                   |
| 🧪 Container Validation | Docker + curl                |
| 🔄 Rolling Deployment   | Kubernetes RollingUpdate     |
| ❤️ Health Management    | Readiness + Liveness Probes  |
| 🩹 Self-Healing         | Kubernetes Deployment        |
| ↩️ Rollback             | Kubernetes Rollout History   |
| 📈 Autoscaling          | Kubernetes HPA               |
| 🌐 Service Exposure     | LoadBalancer Service         |
| 🚦 Traffic Routing      | NGINX Ingress                |
| 🔐 Secure Traffic       | HTTPS / TLS                  |
| 🖥️ Local Environment   | Minikube + Docker Driver     |

---

# 🔥 The Interesting Part

This isn't just:

```text
Jenkins → Docker → Kubernetes
```

The deployment lifecycle includes several operational capabilities:

```text
                   ┌────────────────────┐
                   │    New Git Commit  │
                   └─────────┬──────────┘
                             ▼
                       Jenkins CI/CD
                             │
                             ▼
                      Docker Image
                             │
                             ▼
                    Kubernetes Deploy
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
          Health Checks   Rolling Update    HPA
              │              │              │
              ▼              ▼              ▼
        Self-Healing      Zero planned    2 → 5
                           unavailable     replicas
              │
              ▼
         NGINX Ingress
              │
              ▼
          TLS / HTTPS
              │
              ▼
         🌐 Application
```

---

# 🛠️ Technology Stack

### Development

* HTML5
* NGINX

### Source Control

* Git
* GitHub

### CI/CD

* Jenkins
* Jenkinsfile
* Declarative Pipeline

### Containers

* Docker
* NGINX Alpine

### Kubernetes

* Kubernetes
* Minikube
* kubectl
* Kubernetes Deployment
* Kubernetes Service
* Kubernetes HPA
* NGINX Ingress Controller
* Kubernetes TLS Secret

### Environment

* Windows 11
* Docker Desktop
* PowerShell
* Visual Studio Code

---

# 📁 Repository Structure

```text
devops-webpage-cicd/
│
├── 📄 index.html
├── 🐳 Dockerfile
├── 🔨 Jenkinsfile
├── 🚫 .gitignore
│
├── ☸️ k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
└── 📂 resources/
```

### What each file does

| File              | Purpose                                          |
| ----------------- | ------------------------------------------------ |
| `index.html`      | Application webpage                              |
| `Dockerfile`      | Creates the NGINX container image                |
| `Jenkinsfile`     | Defines the CI/CD pipeline                       |
| `deployment.yaml` | Kubernetes Deployment configuration              |
| `service.yaml`    | Kubernetes Service configuration                 |
| `ingress.yaml`    | HTTP/HTTPS routing configuration                 |
| `.gitignore`      | Prevents sensitive/local files from entering Git |

---

# 🔨 Jenkins Pipeline

The pipeline is intentionally straightforward and readable.

```text
┌─────────────────────┐
│  Checkout Source    │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Build Docker Image  │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Test Container      │
│                     │
│ curl → HTTP 200     │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Load Image into     │
│ Minikube            │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Check Kubernetes    │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Apply K8s manifests │
│                     │
│ Update image        │
└──────────┬──────────┘
           ▼
┌─────────────────────┐
│ Rollout Status      │
└─────────────────────┘
```

---

# 🐳 Docker Image Versioning

Each Jenkins build creates a uniquely tagged image:

```text
my-webpage:<JENKINS_BUILD_NUMBER>
```

For example:

```text
my-webpage:29
my-webpage:30
```

This gives every pipeline execution a traceable deployment artifact.

Instead of simply deploying:

```text
my-webpage:latest
```

the pipeline knows which Jenkins build produced the deployed version.

---

# ☸️ Kubernetes Deployment

The application runs with:

```yaml
replicas: 2
```

So the desired state is:

```text
                Deployment
                    │
             ┌──────┴──────┐
             ▼             ▼
          Pod #1         Pod #2
```

If one pod disappears, Kubernetes reconciles the desired state and creates a replacement.

---

# ❤️ Application Health Checks

Two Kubernetes probes are configured.

### Readiness

```yaml
readinessProbe:
  httpGet:
    path: /
    port: 80
```

The pod only becomes ready for traffic after the application responds successfully.

### Liveness

```yaml
livenessProbe:
  httpGet:
    path: /
    port: 80
```

The probe allows Kubernetes to detect an unhealthy container and restart it when necessary.

---

# 🩹 Self-Healing Test

This wasn't left as configuration only.

A running pod was deliberately deleted:

```bash
kubectl delete pod <pod-name>
```

Kubernetes detected that the Deployment no longer had the desired number of replicas.

It automatically created a replacement.

```text
Before:

Pod A ✅
Pod B ✅

        ↓

Delete Pod A

        ↓

Pod B ✅

        ↓ Kubernetes reconciliation

Pod B ✅
Pod C ✅
```

### Result

**Self-healing verified successfully.**

---

# 🔄 Rolling Updates

The Deployment uses:

```yaml
strategy:
  type: RollingUpdate

  rollingUpdate:
    maxUnavailable: 0
    maxSurge: 1
```

This means Kubernetes can create a new pod before removing an old one.

```text
Version 1

Pod A ────────┐
Pod B ────────┤
              │
              ▼
         Rolling Update
              │
              ▼
Version 2

Pod A
Pod B
Pod C ← new version

              ↓

Old pod removed

              ↓

Pod B
Pod C
```

The rollout is monitored with:

```bash
kubectl rollout status deployment/my-webpage
```

---

# ↩️ Rollback

Deployment history is available through Kubernetes:

```bash
kubectl rollout history deployment/my-webpage
```

A previous version can be restored:

```bash
kubectl rollout undo deployment/my-webpage --to-revision=<REVISION>
```

This was tested during the project by rolling the application back to an earlier image version.

### Deployment recovery flow

```text
New Version
     │
     ▼
Production Issue
     │
     ▼
Check rollout history
     │
     ▼
Select known-good revision
     │
     ▼
kubectl rollout undo
     │
     ▼
Previous version restored
```

---

# 📈 Horizontal Pod Autoscaling

The application includes Kubernetes HPA.

Configuration:

```text
Minimum replicas → 2
Target CPU        → 50%
Maximum replicas  → 5
```

The Deployment also defines CPU resources:

```yaml
resources:
  requests:
    cpu: "10m"

  limits:
    cpu: "200m"
```

Metrics Server was enabled in Minikube.

```bash
minikube addons enable metrics-server
```

Metrics can be inspected using:

```bash
kubectl top pods
kubectl top nodes
```

---

# 🔥 HPA Load Test

A temporary CPU workload was created:

```bash
kubectl run cpu-load \
  --image=busybox \
  --restart=Never \
  -- /bin/sh -c "while true; do :; done"
```

The increased CPU utilization caused the application to scale:

```text
2 replicas
     ↓
3 replicas
     ↓
4 replicas
     ↓
5 replicas
```

After the CPU workload was removed:

```text
5 replicas
     ↓
4 replicas
     ↓
3 replicas
     ↓
2 replicas
```

### Result

**Horizontal scaling and scale-down behavior were both verified.**

---

# 🌐 Kubernetes Service

The application is exposed through a `LoadBalancer` Service.

```yaml
apiVersion: v1
kind: Service

metadata:
  name: my-webpage

spec:
  type: LoadBalancer

  selector:
    app: my-webpage

  ports:
    - port: 80
      targetPort: 80
```

For the local Minikube environment, `minikube tunnel` provides the LoadBalancer behavior.

---

# 🚦 NGINX Ingress

NGINX Ingress Controller handles incoming application traffic.

The configured hostname is:

```text
myweb.local
```

Traffic is routed to:

```text
my-webpage:80
```

```text
                    Incoming Request
                           │
                           ▼
                 ┌─────────────────┐
                 │  NGINX Ingress  │
                 └────────┬────────┘
                          │
                    Host: myweb.local
                          │
                          ▼
                 ┌─────────────────┐
                 │ my-webpage svc  │
                 └────────┬────────┘
                          │
                 ┌────────┴────────┐
                 ▼                 ▼
              Pod #1             Pod #2
```

---

# 🔐 HTTPS / TLS

HTTPS was implemented using a Kubernetes TLS Secret.

The local hostname is:

```text
myweb.local
```

The Ingress references:

```yaml
tls:
  - hosts:
      - myweb.local
    secretName: myweb-tls
```

The traffic flow becomes:

```text
Browser
   │
   │ HTTPS
   ▼
NGINX Ingress
   │
   │ TLS termination
   ▼
Kubernetes Service
   │
   ▼
Application Pods
```

---

# 🧪 HTTPS Verification

The final deployment was tested with:

```bash
curl.exe -vk \
  --resolve myweb.local:8443:127.0.0.1 \
  https://myweb.local:8443/
```

Expected response:

```text
HTTP/1.1 200 OK
```

Application response:

```html
<h1>Welcome to DevOps CI/CD!</h1>
<p>Version 3 deployed automatically through Jenkins.</p>
```

### Verified

```text
✅ DNS / hostname resolution
✅ TLS handshake
✅ HTTPS connection
✅ SNI / Host routing
✅ NGINX TLS termination
✅ Ingress routing
✅ Kubernetes Service
✅ Pod response
```

---

# 🔐 Security Note

The TLS private key is **not committed to GitHub**.

The local TLS directory is ignored through `.gitignore`:

```text
tls/
```

This prevents files such as:

```text
myweb.local.key
myweb.local.crt
```

from being accidentally committed.

> ⚠️ The self-signed certificate is used only for this local learning environment.

For production, this implementation should be replaced with a managed certificate solution such as cert-manager + ACME/Let's Encrypt or an enterprise certificate/secrets-management system.

---

# 🧪 Validation Matrix

| Test                  | Expected Result           | Status |
| --------------------- | ------------------------- | ------ |
| Docker image build    | Image created             | ✅      |
| Container startup     | NGINX starts              | ✅      |
| HTTP container test   | HTTP response             | ✅      |
| Kubernetes deployment | Pods Running              | ✅      |
| Readiness probe       | Pod becomes Ready         | ✅      |
| Liveness probe        | Health monitored          | ✅      |
| Pod deletion          | Replacement created       | ✅      |
| Rolling update        | New version deployed      | ✅      |
| Rollback              | Previous version restored | ✅      |
| HPA scale-up          | 2 → 5 pods                | ✅      |
| HPA scale-down        | 5 → 2 pods                | ✅      |
| LoadBalancer          | Service exposed           | ✅      |
| Ingress               | Host routing              | ✅      |
| TLS                   | HTTPS handshake           | ✅      |
| Final application     | HTTP 200                  | ✅      |
| Jenkins pipeline      | SUCCESS                   | ✅      |

---

# 🧠 Real Troubleshooting Done

This project wasn't only about following commands. Several integration problems had to be diagnosed.

### Jenkins → Minikube

Jenkins initially could not communicate correctly with the Minikube environment.

The Jenkins execution environment was configured with the required Kubernetes configuration and Minikube environment variables.

---

### HPA CPU Metrics

HPA initially reported missing CPU requests.

The Deployment was updated with:

```yaml
resources:
  requests:
    cpu: "10m"
```

After this, HPA could calculate CPU utilization correctly.

---

### Minikube + Docker Networking

Direct access to the Minikube IP from Windows was affected by the Docker driver networking model.

Minikube service forwarding and Kubernetes port-forwarding were used to test the application reliably.

---

### HTTPS Local Access

The HTTPS Ingress itself was functioning, but local Windows access required the correct host mapping and port-forwarding arrangement.

Final verification confirmed the complete TLS → Ingress → Service → Pod path.

---

# 📸 Project Evidence

Recommended screenshots for this repository:

```text
docs/
│
├── 01-github.png
├── 02-jenkins-success.png
├── 03-jenkins-stages.png
├── 04-docker-image.png
├── 05-kubernetes-pods.png
├── 06-rolling-update.png
├── 07-rollback.png
├── 08-hpa-scale-up.png
├── 09-hpa-scale-down.png
├── 10-ingress.png
├── 11-https.png
└── 12-final-application.png
```

---

# 🚀 Quick Start

## 1️⃣ Clone

```bash
git clone https://github.com/santhoshsk3722/devops-webpage-cicd.git

cd devops-webpage-cicd
```

## 2️⃣ Start Minikube

```bash
minikube start --driver=docker
```

## 3️⃣ Enable Ingress

```bash
minikube addons enable ingress
```

## 4️⃣ Enable Metrics Server

```bash
minikube addons enable metrics-server
```

## 5️⃣ Build image

```bash
docker build -t my-webpage:1.0 .
```

## 6️⃣ Load into Minikube

```bash
minikube image load my-webpage:1.0
```

## 7️⃣ Deploy

```bash
kubectl apply -f k8s/
```

## 8️⃣ Verify

```bash
kubectl get pods
kubectl get svc
kubectl get ingress
kubectl get hpa
```

---

# 🔄 CI/CD Demo

Change:

```html
<p>Version 3 deployed automatically through Jenkins.</p>
```

to:

```html
<p>Version 4 deployed automatically through Jenkins.</p>
```

Then:

```bash
git add .
git commit -m "Update application version"
git push origin main
```

Jenkins handles the rest.

```text
       git push
          │
          ▼
       GitHub
          │
          ▼
       Jenkins
          │
          ├── Build
          ├── Test
          ├── Docker
          ├── Kubernetes
          └── Rollout
                │
                ▼
          New Version
```

---

# 📊 Project Outcome

The final implementation demonstrates a complete local DevOps delivery workflow:

```text
                    SOURCE
                      │
                   GitHub
                      │
                      ▼
                     CI
                   Jenkins
                      │
            ┌─────────┴─────────┐
            ▼                   ▼
       Docker Build          Test
            │                   │
            └─────────┬─────────┘
                      ▼
                  DELIVERY
                      │
                  Kubernetes
                      │
       ┌──────────────┼──────────────┐
       ▼              ▼              ▼
   Self-Healing   Rolling Update     HPA
                                      │
                                   2 → 5
       │              │              │
       └──────────────┼──────────────┘
                      ▼
                   Ingress
                      │
                   TLS/HTTPS
                      │
                      ▼
                🌐 Application
```

---

# 🎯 What This Project Demonstrates

### CI/CD

Automated application build, testing and deployment using Jenkins.

### Containerization

Packaging the application into a reproducible Docker image.

### Kubernetes

Running the application using a declarative Deployment.

### Reliability

Using probes, replica management and self-healing.

### Deployment Safety

Using RollingUpdate and rollback capabilities.

### Scalability

Using HPA to dynamically scale application replicas.

### Networking

Using Kubernetes Service and NGINX Ingress.

### Security

Using HTTPS/TLS at the Ingress layer.

### Troubleshooting

Diagnosing Jenkins, Kubernetes, HPA, networking and TLS integration issues.

---

# 🔮 Next Improvements

This project intentionally uses a local Kubernetes environment. The next production-oriented iteration could add:

* [ ] Docker Hub / private container registry
* [ ] Trivy image vulnerability scanning
* [ ] SonarQube code quality checks
* [ ] Prometheus metrics
* [ ] Grafana dashboards
* [ ] Alertmanager
* [ ] cert-manager + Let's Encrypt
* [ ] External Secrets / Vault
* [ ] Helm charts
* [ ] Separate Dev / Test / Prod environments
* [ ] Jenkins approval gates
* [ ] Blue/Green deployment
* [ ] Canary deployment
* [ ] AWS EKS or Azure AKS deployment
* [ ] Terraform infrastructure provisioning

---

# 👨‍💻 Author

## Santhosh Kumar P S

**DevOps Engineer**

`AWS` · `Azure` · `Linux` · `Docker` · `Kubernetes` · `Jenkins` · `Terraform` · `CI/CD`

---

### ⭐ If you found this project useful

Feel free to explore the implementation, raise an issue, or suggest an improvement.

**Built to learn. Built to troubleshoot. Built to deploy. 🚀**
