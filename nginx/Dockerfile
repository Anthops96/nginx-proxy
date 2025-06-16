FROM nginx:alpine

# Copy nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Copy ssl certificates
COPY ssl/server.crt /etc/nginx/ssl/server.crt
COPY ssl/server.key /etc/nginx/ssl/server.key
COPY ssl/dhparam.pem /etc/nginx/ssl/dhparam.pem

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]