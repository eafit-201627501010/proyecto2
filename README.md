# Proyecto 2 - Cluster Kubernetes

## Descripción del Proyecto
Este proyecto consiste en desplegar una aplicación monolítica (WordPress) en un clúster Kubernetes de alta disponibilidad utilizando microk8s. La implementación se realiza en Google Cloud Platform (GCP), con un clúster compuesto por tres máquinas virtuales.

## Contexto de Despliegue
La aplicación se despliega en un entorno de nube IaaS, utilizando servidores virtuales en GCP. El proyecto incluye el manejo de volúmenes compartidos mediante un servidor NFS y el acceso al clúster a través de un balanceador de cargas.

## Requerimientos
- Desplegar un clúster Kubernetes con microk8s en al menos tres máquinas virtuales.
- Implementar alta disponibilidad en la capa de aplicación, base de datos y almacenamiento.
- Configurar un balanceador de cargas.
- Permitir el aumento dinámico de nodos en el clúster Kubernetes.
- Desplegar una base de datos de alta disponibilidad en Kubernetes.
- Configurar un servidor NFS para los servicios stateful.
- Implementar un dominio para el servicio: https://proyecto2.dominio.tld

## Arquitectura del Proyecto
![Diagrama de Arquitectura](https://console.cloud.google.com/compute/instances?onCreate=true&project=proyecto2-423217)

## Pasos para la Instalación del Clúster Kubernetes con microk8s
1. **Preparación de las Máquinas Virtuales:**
   - Crear tres máquinas virtuales en GCP.
   - Configurar las máquinas virtuales con Ubuntu 20.04 LTS.

2. **Instalación de microk8s:**
   ```bash
   sudo snap install microk8s --classic
   microk8s status --wait-ready
   sudo usermod -a -G microk8s $USER
   sudo chown -f -R $USER ~/.kube
