<div align="center">
  <br />
  <h1>🚀 AUTO DEPLOY HUB</h1>
  <p>
    <em>A lightweight cloud deployment service that enables users to upload and host frontend websites <br /> 
    using REST APIs, Dockerized builds and AWS infrastructure.</em>
  </p>

  <p>
    <img src="https://img.shields.io/badge/Node.js-black?style=for-the-badge&logo=node.js&logoColor=white&color=339933" alt="Node.js" />
    <img src="https://img.shields.io/badge/TypeScript-black?style=for-the-badge&logo=typescript&logoColor=white&color=3178C6" alt="TypeScript" />
    <img src="https://img.shields.io/badge/AWS%20S3-black?style=for-the-badge&logo=amazon-aws&logoColor=white&color=FF9900" alt="AWS S3" />
    <img src="https://img.shields.io/badge/Docker-black?style=for-the-badge&logo=docker&logoColor=white&color=2496ED" alt="Docker" />
    <img src="https://img.shields.io/badge/Postman-black?style=for-the-badge&logo=postman&logoColor=white&color=FF6C37" alt="Postman" />
  </p>
  <div>
    <a href="https://deploy-hub.netlify.app/" target="_blank">
      <img src="https://img.shields.io/badge/Live_Site-Deploy_Hub-28a745?style=for-the-badge&logo=vercel&logoColor=white" alt="Live Site" />
    </a>
  </div>

  <br>
  <div>
    <a href="https://youtu.be/GdX-LqlLm1g" target="_blank">
      <img src="https://github.com/MohitChamyal/Auto-Deploy-Hub/blob/master/static/landing_page.png" alt="DeployHub Demo Video Thumbnail" width="800" />
    </a>
  </div>
  
  <br />
  <div>
    <a href="https://youtu.be/GdX-LqlLm1g" target="_blank">
      <img src="https://img.shields.io/badge/Watch_Demo_Video-YouTube-red?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch Demo Video" />
    </a>
  </div>
</div>


---

## ✨ What is Auto Deploy Hub?

DeployHub is a deployment service that:
- Accepts frontend project uploads or repositories via RESTful APIs  
- Uses a Docker-based build server to generate static builds  
- Pushes them to AWS S3 for hosting  
- Serves content via a custom reverse proxy mapped to subdomains  

It simulates the core behaviors of a CI/CD deployment flow in a clean and modular way.

---

## 🔐 Subdomain Mapping via Reverse Proxy

- DeployHub uses a custom reverse proxy to map subdomains (like app1.deployhub.com) to specific S3 buckets or prefixes
- This setup does not rely on client-side JavaScript for routing or navigation
- The proxy:
  - Validates requests
  - Fetches from S3
  - Handles custom headers, caching, and redirects

---

## Core Services Overview

| Service              | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **api-server**        | Receives file uploads or repo info, triggers ECS task for building         |
| **build-server**      | Dockerized service to build and push apps to AWS S3                        |
| **s3-reverse-proxy**  | Maps subdomains/domains to S3 and serves static content via proxy          |

---

## Tech Stack

- **Node.js** – REST API server and custom reverse proxy logic  
- **Docker** – Containerized build environments  
- **AWS S3, ECS, ECR** – Cloud storage and container execution  
- **Postman** – API testing and validation  

---

## Architecture Overview

- Upload request hits `api-server`  
- ECS task is triggered with `build-server` container  
- The container clones the project, builds it, and pushes output to **AWS S3**  
- `s3-reverse-proxy` handles routing of domains to the correct S3 bucket  

---

