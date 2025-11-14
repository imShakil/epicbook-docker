# EpicBook Application Containerization

We will dockerized epicbook application and access it with traefik routing. 

## Getting Started

### Option 0: Install Docker

```sh
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
sudo usermod -aG docker ubuntu 2>/dev/null || true

# test
sudo su - $USER
docker ps
```

### Option 1: Clone Entire Repository

```bash
git clone https://github.com/imShakil/docker-practices.git
cd docker-practices/docker-compose
```

### Option 2: Sparse Checkout (Recommended)

```bash
# Clone repository without files
git clone --no-checkout https://github.com/imShakil/docker-practices.git
cd docker-practices

# Enable sparse checkout
git sparse-checkout init --cone
git sparse-checkout set epicbook-app-containerization

# Checkout files
git checkout
cd epicbook-app-containerization
```

## Step-by-Step Setup

### 1. Create Environment File

```bash
# Create .env file with required variables
cat > .env << EOF
MYSQL_ROOT_PASSWORD=my-secret-pw
MYSQL_USER=pravin
MYSQL_PASSWORD=Demo12@Test23
MYSQL_HOST=mysql
EOF
```

### 2. Build and Run

```bash
# Build and start all services
docker compose up --build

# Or run in background
docker compose up --build -d
```

### 3. Access Application

- **Frontend**: http://localhost or VM public IP
- **Database**: localhost:27017 (if needed)

### 4. Test the Application

1. Open http://localhost or http://<vm-public-ip> in browser
2. Add your name and favorite movie
3. Click "Share Movie"
4. See your movie in the shared list