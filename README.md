# ️ RKE2 Kubernetes Home Lab

Self-hosted 6-node RKE2 cluster (3 control-plane, 3 workers) untuk development & research.
Dibangun di atas Proxmox VE dengan fokus pada high availability, automated ingress routing, dan horizontal scaling.

## Tech Stack
- **Orchestrator:** RKE2 (Kubernetes v1.34)
- **Load Balancer:** MetalLB (L2 mode)
- **Ingress Controller:** NGINX Ingress Controller
- **Monitoring/Scaling:** HPA (CPU-based)
- **Virtualization:** Proxmox VE

## Architecture
[Internet] → HAProxy (External LB) → MetalLB → Ingress-NGINX → Pods (php56/nginx)
↑
RKE2 Cluster (3 CP + 3 Worker)

## Deployment Steps
1. Ensure the RKE2 cluster is running and kubectl is properly configured
2. Apply MetalLB:  
	$ kubectl apply -f metallb/
3. Apply Ingress Controller:
	$ kubectl apply -f ingress-nginx/
4. Deploy app
	$ kubectl apply -f apps/php56-legacy/

