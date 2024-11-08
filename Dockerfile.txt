# Use an official Nginx image from Docker Hub as the base
FROM nginx:alpine

# Maintainer label (optional)
LABEL maintainer="sammed18@example.com"

# Expose port 80 for the Nginx server
EXPOSE 80
