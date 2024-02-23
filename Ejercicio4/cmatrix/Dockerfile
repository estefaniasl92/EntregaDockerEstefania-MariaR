# Use an official Ubuntu as a parent image
FROM ubuntu:latest

# Actualiza los paquetes del repositorio
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    cmatrix \
    && rm -rf /var/lib/apt/lists/*

# Define el comando predeterminado para ejecutar cmatrix
CMD ["cmatrix"]



