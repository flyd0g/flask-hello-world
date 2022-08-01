# Use Alpine as base image
FROM alpine:latest

# Copy the Zscaler certificate to container image 
COPY ZscalerRootCertificate-2048-SHA256.crt /tmp/ZscalerRootCertificate-2048-SHA256.crt

# Make apk work with ssl
RUN cat /tmp/ZscalerRootCertificate-2048-SHA256.crt >> /etc/ssl/certs/ca-certificates.crt

# Install Python and Pip with apk
RUN apk add --no-cache python3-dev
RUN apk add --no-cache py3-pip

# Install ca-certificates
RUN apk add --no-cache ca-certificates
RUN cp /tmp/ZscalerRootCertificate-2048-SHA256.crt /usr/local/share/ca-certificates/
RUN update-ca-certificates

# Make pip work with ssl
ENV CERT_PATH=/etc/ssl/certs/
ENV	CERT_DIR=/etc/ssl/certs/
ENV	SSL_CERT_FILE=${CERT_PATH} 
ENV	SSL_CERT_DIR=${CERT_DIR}
ENV REQUESTS_CA_BUNDLE=${CERT_PATH} 

# Install Flask framework with Pip
RUN pip install flask