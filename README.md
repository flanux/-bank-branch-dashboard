# Branch Dashboard - VPN Only

**Repo**: `flanux/branch-dashboard`  
**Access**: VPN Required  
**URL**: https://branch.internal.flanuxbank.com  

## Prerequisites

⚠️ **MUST be connected to branch VPN**

## Quick Start

```bash
npm install
npm start
```

Runs on port 3001.

## Environment Setup

```bash
cp .env.example .env
```

Edit `.env`:
```
REACT_APP_API_URL=https://branch-api.internal.flanuxbank.com
REACT_APP_BRANCH_ID=BR001
```

## Build for Production

```bash
npm run build
docker build -t flanux/branch-dashboard:v1.0.0 .
```

Deploy to internal Kubernetes cluster.

## Security

- VPN + 2FA required
- Can only access own branch data
- Role-based: TELLER vs MANAGER
- IP whitelisting per branch

## API Access

Can call:
- `/customers/*` (within branch)
- `/accounts/*` (within branch)
- `/transactions/*`
- `/loans/*` (process & approve)
- `/cards/*` (issue & manage)

CANNOT access:
- Other branches
- Central admin tools
- System configuration
