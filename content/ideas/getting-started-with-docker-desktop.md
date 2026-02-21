<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

----


# Docker Desktop Installation on Ubuntu
* [Install Docker Desktop on Ubuntu](https://dev.to/meghasharmaaaa/install-docker-desktop-on-ubuntu-3kf6)
* [Install Docker Desktop on Ubuntu](https://docs.docker.com/desktop/setup/install/linux/ubuntu/)
* **Claude Code Prompt:** How do I install docker desktop on Ubuntu? Give me instruction in markdown file.

## Before You Begin
**Will Docker Desktop conflict with previously installed Docker Engine, Docker Compose, or Portainer?**

**Docker Desktop includes Docker Engine and Docker Compose**,
so there's potential for conflict if you already have these installed via `apt`.

**Key points:**

1. **Docker Engine conflict**: Docker Desktop uses its own Docker Engine instance.
   If you have Docker installed via apt (`docker.io` or `docker-ce`),
   they can coexist but you'll have two separate Docker daemons.
   This can cause confusion about which one you're using.
2. **Docker Compose**: Docker Desktop bundles Docker Compose v2 (the `docker compose` plugin).
   If you have standalone `docker-compose` v1 installed, both will work but you'll have two versions.
3. **Portainer**: No conflict. Portainer is just a management UI that connects to Docker's API.
   It will work with either Docker Engine or Docker Desktop.

**Recommended approach:**

* If you already have Docker Engine + Docker Compose working well,
  you probably don't need Docker Desktop (which is mainly beneficial for its GUI and easier VM management)
* If you want Docker Desktop, uninstall existing Docker packages first:

  ```bash
  # uninstall docker
  sudo apt remove docker docker-engine docker.io containerd runc docker-compose
  ```

## Migrating from Docker Engine to Docker Desktop on Ubuntu
This guide helps you migrate from a standalone Docker Engine installation to Docker Desktop while preserving your containers, images, and volumes.

### Pre-Migration Checklist

#### 1. Back up your Docker data

```bash
# List running containers
docker ps

# List all containers (including stopped)
docker ps -a

# List images
docker images

# List volumes
docker volume ls

# Export important container configurations
docker inspect <container_name> > container_backup.json
```

#### 2. Export containers you want to keep (optional)

```bash
# Commit running containers to images
docker commit <container_name> <backup_image_name>

# Or export containers as tar files
docker export <container_name> > container_backup.tar

# Save images as tar files
docker save -o myimages.tar image1:tag image2:tag
```

#### 3. Back up volumes (if critical data)

```bash
# Back up a specific volume
docker run --rm -v <volume_name>:/data -v $(pwd):/backup ubuntu tar czf /backup/volume_backup.tar.gz /data
```

## Migration Steps

#### Step 1: Stop Docker services

```bash
sudo systemctl stop docker
sudo systemctl stop docker.socket
sudo systemctl stop containerd
```

#### Step 2: Note your Docker data location

By default, Docker stores data in `/var/lib/docker`. Check if you've customized this:

```bash
docker info | grep "Docker Root Dir"
```

#### Step 3: Remove Docker Engine packages

```bash
# Remove Docker packages but keep data
sudo apt-get remove docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Or remove older package names if applicable
sudo apt-get remove docker docker-engine docker.io containerd runc docker-compose

# Do NOT run apt-get purge or remove /var/lib/docker manually yet
```

#### Step 4: Install Docker Desktop

Follow the installation steps from the main guide:

```bash
# Add Docker's apt repository (if not already done)
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# Download and install Docker Desktop
wget https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb
sudo apt-get install ./docker-desktop-amd64.deb
```

#### Step 5: Start Docker Desktop

```bash
systemctl --user start docker-desktop
```

Wait for Docker Desktop to fully start (check the system tray icon or run `docker ps`).

#### Step 6: Verify your data

```bash
# Check if your images are still there
docker images

# Check volumes
docker volume ls

# Check containers
docker ps -a
```

## Important Notes

#### Data Persistence

* Docker Desktop on Linux uses a VM but typically **preserves data from `/var/lib/docker`** during migration
* Images, volumes, and stopped containers should carry over automatically
* Running containers will need to be restarted

#### If Data Doesn't Appear

If your images/volumes don't show up after migration:

```bash
# Check Docker Desktop's data location
docker info | grep "Docker Root Dir"

# Import saved images
docker load -i myimages.tar

# Import exported containers
docker import container_backup.tar
```

#### Restore volumes if needed

```bash
# Restore a backed-up volume
docker run --rm -v <volume_name>:/data -v $(pwd):/backup ubuntu tar xzf /backup/volume_backup.tar.gz -C /
```

## Post-Migration

#### 1. Restart your containers

```bash
# Start individual containers
docker start <container_name>

# Or use docker-compose if you have compose files
docker compose up -d
```

#### 2. Update Portainer connection (if applicable)

If you're using Portainer:

```bash
# Portainer should automatically detect the new Docker socket
# Default socket location: /var/run/docker.sock (same as before)

# If you need to reconnect Portainer:
docker run -d -p 9000:9000 \
  --name=portainer --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
```

#### 3. Update shell aliases or scripts

If you have scripts or aliases pointing to docker-compose v1, update them:

```bash
# Old: docker-compose
# New: docker compose (note the space - it's now a plugin)
```

### Rollback Plan

If you need to go back to Docker Engine:

```bash
# Stop Docker Desktop
systemctl --user stop docker-desktop

# Uninstall Docker Desktop
sudo apt-get remove docker-desktop

# Reinstall Docker Engine
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Start Docker
sudo systemctl start docker
```

### Comparison: What Changes?

| Aspect | Docker Engine | Docker Desktop |
|--------|--------------|----------------|
| Docker daemon | Runs natively on host | Runs in a VM |
| GUI | None | Included |
| Resource limits | System-wide | Configurable via GUI |
| Docker Compose | Separate install | Bundled |
| Kubernetes | Separate install | Optional built-in |
| Updates | Via apt | Via GUI or apt |
| Performance | Slightly faster | Minimal overhead |

### When to Stay with Docker Engine

Consider keeping Docker Engine if:
* You're running Docker in production servers
* You don't need the GUI
* You want minimal overhead
* You're comfortable with CLI-only management

Docker Desktop is better for:
* Development environments
* Testing with Kubernetes
* Easier resource management
* GUI preferences

----

## Docker Desktop Prerequisites

* Ubuntu 22.04 LTS or later (64-bit)
* KVM virtualization support
* QEMU version 5.2 or newer

Ensure your system meets the following requirements:
* **Ubuntu Version:** 64-bit version of 22.04 LTS, 24.04 LTS, or newer.
* **CPU Virtualization:** Must be enabled in BIOS.
* **RAM:** At least 4 GB.
* **KVM Support:** Docker Desktop requires KVM.

To verify KVM support, run:

```bash
lsmod | grep kvm
```

## Installation Steps

### 1. Set up Docker's apt repository

```bash
# Add Docker's official GPG key
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to apt sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
```

### 2. Download and install Docker Desktop

Download the latest DEB package from the [Docker Desktop release page](https://docs.docker.com/desktop/install/ubuntu/), or use:

```bash
# For Ubuntu 22.04 or later
wget https://desktop.docker.com/linux/main/amd64/docker-desktop-amd64.deb
sudo apt install ./docker-desktop-amd64.deb
```

### 3. Launch Docker Desktop

```bash
systemctl --user start docker-desktop
```

Or launch it from your applications menu.

## Post-Installation

### Enable Docker Desktop to start on boot

```bash
systemctl --user enable docker-desktop
```

### Verify installation

```bash
docker --version
docker compose version
```

## Troubleshooting

If you encounter issues with KVM:

```bash
# Check KVM availability
kvm-ok

# Add your user to the kvm group
sudo usermod -aG kvm $USER
```

Log out and back in for group changes to take effect.
