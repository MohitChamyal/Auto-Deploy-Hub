#  Auto Deploy Hub 🚀 

A modular, containerized deployment system designed to automate frontend project builds and delivery using cloud-native services. It provides an API-driven interface to upload code, trigger builds inside Dockerized environments, and host output seamlessly on AWS S3—served via a custom reverse proxy.

---

## ✨ What is DeployHub?

DeployHub is a deployment platform that:

- Accepts *frontend project uploads* or *Git repositories* via REST APIs  
- Triggers *Docker-based builds* using AWS ECS tasks  
- *Pushes static output* to AWS S3 for public hosting  
- *Serves builds via a no-JS reverse proxy*, mapped to custom subdomains  

It simulates key behaviors of a modern CI/CD workflow in a *clean, decoupled, and **production-ready* manner.

---

## 🧱 Core Services Overview

| Service            | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| api-server       | RESTful interface for uploading zip files or Git repo links                 |
| build-server     | Containerized build runner (triggered by ECS task), builds & uploads to S3 |
| s3-reverse-proxy | Maps subdomains/domains to S3 buckets and proxies static content            |

---

## ⚙ Tech Stack

- *Node.js* – API server and reverse proxy logic  
- *Docker* – Build environments containerized for reproducibility  
- *AWS S3* – Static file hosting  
- *AWS ECS + ECR* – Container execution and image management  
- *Postman* – API testing and validation

---

## 🚧 Example Flow

1. *Upload your project*:
   - POST /upload (with zip file or Git repo)
2. *DeployHub* triggers an ECS task
3. *build-server* pulls the code, installs dependencies, and builds the frontend app (e.g., npm run build)
4. *Output is pushed to AWS S3*, under a bucket or path named after your app
5. *Content is served via subdomain*: https://your-app.deployhub.com through the reverse proxy

---

## 🔐 Subdomain Mapping via Reverse Proxy

- DeployHub uses a custom reverse proxy to map subdomains (like app1.deployhub.com) to specific S3 buckets or prefixes
- This setup does not rely on client-side JavaScript for routing or navigation
- The proxy:
  - Validates requests
  - Fetches from S3
  - Handles custom headers, caching, and redirects

---

## 📦 API Endpoints

| Method | Endpoint       | Description                          |
|--------|----------------|--------------------------------------|
| POST   | /upload      | Upload a ZIP file or Git repo URL    |
| GET    | /status/:id  | Get build and deployment status      |
| POST   | /redeploy    | Rebuild and redeploy an existing app |

---
 ## 🤝 Contributing

We welcome and appreciate contributions from the community.

If you’d like to get involved, you can:

- Open an issue to report a bug, suggest an enhancement, or request a new feature
- Submit a pull request with improvements or fixes
- Propose support for additional Git providers or deployment targets
- Enhance security, logging, or observability features

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).  
You are free to use, modify, and distribute this software under the terms of the license.

---
