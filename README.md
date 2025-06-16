# nginx-proxy
nginx proxy and loadbalancer

## Project Structure
```txt
/nginx-proxy/
├── docker-compose.yml
├── nginx/
│   ├── Dockerfile
│   ├── nginx.conf
│   ├── ssl/
│   │   ├── server.crt
│   │   ├── server.key
│   │   └── dhparam.pem
└── README.md
```


Self signed certificate generation
```bash
mkdir -p nginx/ssl
cd nginx/ssl

# Generate private key
openssl genrsa -out server.key 2048

# Generate CSR (Certificate Signing Request)
openssl req -new -key server.key -out server.csr \
    -subj "CN=nexus-proxy.domain.com"

# Generate self signed certificate (365 days)
openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

# Genrate parameters Diffie-Hellman (for DHE ciphers)
openssl dhparam -out dhparam.pem 2048

# Clean CSR
rm server.csr
```


Create and configure the needed files and start the container.

```bash
nano nginx.conf # Nginx configuration file

nano Dockerfile # File for image build

nano docker-compose.yaml # Declare docker compose configuration 

docker-compose up -d --build # Start docker container in background

docker-compose logs nginx-proxy # Check container status
```

