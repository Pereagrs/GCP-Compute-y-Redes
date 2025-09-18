# Practicas GCP & GKE – YAML Files

Este repositorio contiene los archivos YAML utilizados para desplegar y configurar la práctica de infraestructura en Google Cloud Platform (GCP) y un clúster privado de Kubernetes (GKE).  

Los archivos reflejan toda la infraestructura creada, incluyendo red, subredes, firewalls, Bastion Host, Cloud NAT, y los recursos de Kubernetes para desplegar la aplicación HelloWorld.  

---

## Contenido del repositorio

### **Infraestructura en GCP**
| Archivo | Descripción |
|---------|-------------|
| `red.yaml` | Configuración de la VPC `gke-vpc`. |
| `subnet.yaml` | Subred del clúster `gke-subnet`. |
| `firewall-allow-ssh-bastion.yaml` | Regla de firewall para permitir SSH al Bastion Host. |
| `firewall-allow-bastion-to-gke.yaml` | Regla de firewall para permitir comunicación del Bastion al clúster GKE. |
| `router.yaml` | Configuración del Cloud Router utilizado para Cloud NAT. |
| `nat.yaml` | Configuración del Cloud NAT para acceso a Internet desde nodos privados. |
| `instancia.yaml` | Descripción de la máquina virtual Bastion Host. |

### **Recursos de Kubernetes**
| Archivo | Descripción |
|---------|-------------|
| `helloworld.yaml` | Deployment de la aplicación de ejemplo HelloWorld. |
| `helloworld-service.yaml` | Service tipo LoadBalancer que expone la aplicación HelloWorld al exterior. |
| `nginx-deployment.yaml` | Deployment adicional de Nginx (si se aplicó). |

### **Roles y permisos**
| Archivo | Descripción |
|---------|-------------|
| `custom_storage_role.yaml` | Rol personalizado creado para la práctica. |

---

## Uso de los archivos

1. **Infraestructura GCP**  
   Los archivos de infraestructura son descriptivos (generados con `gcloud ... --format yaml`) y se usan para documentar la configuración aplicada.  

2. **Kubernetes**  
   Para desplegar la aplicación HelloWorld en un clúster GKE privado:  
   ```bash
   kubectl apply -f helloworld.yaml
   kubectl apply -f helloworld-service.yaml
