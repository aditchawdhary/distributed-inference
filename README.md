# Distributed Inference

## Installation

1. Installing Rust

``` bash
% curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Verify Rust and Cargo installation, run:

``` bash
% source ~/.zshenv  
% rustc --version
% cargo --version
```

Should print the installed version in my case it was

``` bash
rustc 1.90.0 (1159e78c4 2025-09-14)
cargo 1.90.0 (840b83a10 2025-07-30)
```


2. Install Docker Desktop

<ul>
<li>
Download from docker.com
</li>
<li>
Open Docker Desktop

Go to Settings → Kubernetes

Check "Enable Kubernetes"
</li>
<li>
Click "Apply & Restart"
Wait for the green dot next to "Kubernetes"
</li>
</ul>

3. Install kubectl
```
% brew install kubectl

Warning: kubernetes-cli 1.34.1 is already installed and up-to-date.
achawdhary@macbookpro distributed-inference % kubectl config use-context docker-desktop

Switched to context "docker-desktop".

% kubectl 
config current-context

docker-desktop

% kubectl cluster-info

Kubernetes control plane is running at https://127.0.0.1:6443
CoreDNS is running at https://127.0.0.1:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

% kubectl get nodes

NAME             STATUS   ROLES           AGE    VERSION
docker-desktop   Ready    control-plane   7m4s   v1.27.2

 % kubectl get pods -n kube-system

NAME                                     READY   STATUS    RESTARTS   AGE
coredns-5d78c9869d-97xsq                 1/1     Running   0          7m31s
coredns-5d78c9869d-9mfrc                 1/1     Running   0          7m31s
etcd-docker-desktop                      1/1     Running   0          7m31s
kube-apiserver-docker-desktop            1/1     Running   0          7m36s
kube-controller-manager-docker-desktop   1/1     Running   0          7m34s
kube-proxy-49l2b                         1/1     Running   0          7m31s
kube-scheduler-docker-desktop            1/1     Running   0          7m35s
storage-provisioner                      1/1     Running   0          7m29s
vpnkit-controller                        1/1     Running   0          7m29s
```

4. Create your project:
```bash
cargo new distributed-inference --bin
cd distributed-inference
git init
```

5. Verify python and pip version
```
% python3 --version
Python 3.12.1
% pip3 --version
pip 25.2 from /Library/Frameworks/Python.framework/Versions/3.12/lib/python3.12/site-packages/pip (python 3.12)
```

6. Verify NVIDIA GPU drivers and check CUDA installation:

```bash
# Check if CUDA is installed
nvcc --version

# Check NVIDIA driver
nvidia-smi
```

7. Create a virtual environment for Python
```bash
% python3 -m venv venv
% source venv/bin/activate
```

```bash
% tree -a -L 2
.
├── .DS_Store
├── .env.example
├── .git
│   ├── HEAD
│   ├── config
│   ├── description
│   ├── hooks
│   ├── info
│   ├── objects
│   └── refs
├── .gitignore
├── Cargo.lock
├── Cargo.toml
├── README.md
├── benchmarks
├── docker-compose.yml
├── docs
├── k8s
│   └── monitoring
├── python_kernels
├── src
│   └── main.rs
├── target
│   ├── .rustc_info.json
│   ├── CACHEDIR.TAG
│   └── debug
└── venv
    ├── bin
    ├── include
    ├── lib
    └── pyvenv.cfg
```

