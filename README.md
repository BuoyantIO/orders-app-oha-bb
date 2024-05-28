# orders-app-oha-bb
## The Orders app, in single and multi-cluster formats. Uses oha for load generation and bb as the server.
### Tom Dean | Buoyant

Last updated 5/28/24

## Introduction

This repository contains the Orders app, in single and multi-cluster formats. Uses oha for load generation and bb as the server.

Repository contents:

```bash
.
├── README.md
├── multi-cluster
│   ├── orders-hpa
│   │   ├── orders
│   │   │   ├── kustomization.yaml
│   │   │   ├── ns.yaml
│   │   │   ├── orders-central.yaml
│   │   │   ├── orders-east.yaml
│   │   │   └── orders-west.yaml
│   │   └── warehouse
│   │       ├── kustomization.yaml
│   │       ├── ns.yaml
│   │       ├── server.yaml
│   │       ├── warehouse-boston.yaml
│   │       ├── warehouse-chicago.yaml
│   │       └── warehouse-oakland.yaml
│   └── orders-nohpa
│       ├── orders
│       │   ├── kustomization.yaml
│       │   ├── ns.yaml
│       │   ├── orders-central.yaml
│       │   ├── orders-east.yaml
│       │   └── orders-west.yaml
│       └── warehouse
│           ├── kustomization.yaml
│           ├── ns.yaml
│           ├── server.yaml
│           ├── warehouse-boston.yaml
│           ├── warehouse-chicago.yaml
│           └── warehouse-oakland.yaml
└── single-cluster
    ├── orders-hpa
    │   ├── kustomization.yaml
    │   ├── ns.yaml
    │   ├── orders-central.yaml
    │   ├── orders-east.yaml
    │   ├── orders-west.yaml
    │   ├── server.yaml
    │   ├── warehouse-boston.yaml
    │   ├── warehouse-chicago.yaml
    │   └── warehouse-oakland.yaml
    └── orders-nohpa
        ├── kustomization.yaml
        ├── ns.yaml
        ├── orders-central.yaml
        ├── orders-east.yaml
        ├── orders-west.yaml
        ├── server.yaml
        ├── warehouse-boston.yaml
        ├── warehouse-chicago.yaml
        └── warehouse-oakland.yaml
```

## IMPORTANT! Building the `oha` Load Generator

_You will need build the container image for the `oha` load generator for the `orders-*` deployments._  The `cluster_setup.sh` script will import the `hatoo/oha:latest` container image from Docker for you, but it has to be in the Docker container registry first.

[oha](https://github.com/hatoo/oha)

### Step 1: Clone the `oha` GitHub Repository

Clone the repository to your machine:

```bash
git clone https://github.com/hatoo/oha.git
```

Change directory:

```bash
cd oha
```

### Step 2: Build the `oha` Container Image

```bash
docker build . -t hatoo/oha:latest
```

Check your work:

```bash
docker images
```

You should see the `hatoo/oha:latest` container image.
