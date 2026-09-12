# 1. Add the official Docker provider
devpod provider add docker

# 2. Point it at Podman
devpod provider set-options docker \
  --option DOCKER_PATH=/usr/bin/podman

# 3. (Important for rootless) set the socket
devpod provider set-options docker \
  --option DOCKER_HOST=unix://$XDG_RUNTIME_DIR/podman/podman.sock

# 4. Make it the default
devpod provider use docker

-------

# Always name workspaces per client
devpod up . --id client-acme

# Stop when finished
devpod stop client-acme

# Completely remove when the job is done
devpod delete client-acme


------------------------
# Podman (if not already installed)
# (use your distro's package manager)

# Enable the rootless socket
systemctl --user enable --now podman.socket

# Install DevPod CLI
```bash
curl -L -o devpod "https://github.com/loft-sh/devpod/releases/latest/download/devpod-linux-amd64"
sudo install -c -m 0755 devpod /usr/local/bin/devpod
devpod version
```

```bash
devpod provider add docker
devpod provider set-options docker --option DOCKER_PATH=/usr/bin/podman
devpod provider set-options docker --option DOCKER_HOST=unix://$XDG_RUNTIME_DIR/podman/podman.sock
devpod provider use docker
```

```bash
mkdir -p ~/clients/demo-client
cd ~/clients/demo-client
git init
```

```bash
mkdir -p ~/.config/containers
vi ~/.config/containers/containers.conf
```
```ini
[containers]
label = false
```

```bash
devpod up . --id demo-client
devpod ssh demo-client
```
