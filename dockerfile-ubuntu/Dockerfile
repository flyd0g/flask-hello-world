# Use Ubuntu as base image
FROM ubuntu:latest

# Copy the Zscaler certificate to container image 
COPY ./ZscalerRootCertificate-2048-SHA256.crt /tmp/ZscalerRootCertificate-2048-SHA256.crt

# Install Python and Pip with apt
RUN apt update
RUN apt install -y python3 
RUN apt install -y python3-pip

# Make Pip work with ssl
RUN cat /tmp/ZscalerRootCertificate-2048-SHA256.crt >> /etc/ssl/certs/ca-certificates.crt

# Install Flask framework with Pip
RUN pip install flask