# 🛡️ Segmentación de Red e Implementación de ACLs Extendidas en Cisco Packet Tracer

## 📌 Descripción del Proyecto
Este proyecto demuestra el diseño, la segmentación y el hardening de una arquitectura de red corporativa dividida en tres zonas mediante VLANs. Se implementa enrutamiento Inter-VLAN (Router-on-a-Stick) y se aplican **Listas de Control de Acceso (ACLs) extendidas** para aplicar el principio de mínimo privilegio sobre el tráfico de la red.

---

## 📐 Arquitectura de Red y Segmentación

| VLAN | Nombre | Subred | Propósito / Dispositivos |
| :--- | :--- | :--- | :--- |
| **VLAN 10** | ADMIN | `192.168.10.0/24` | Equipos de administración y gestión |
| **VLAN 20** | EMPLEADOS | `192.168.20.0/24` | Estaciones de trabajo operativas |
| **VLAN 30** | SERVIDORES | `192.168.30.0/24` | Servidores y servicios compartidos |

---

## 🔒 Políticas de Seguridad e Implementación de ACL

Se configuró una ACL extendida nombrada (`SEGURIDAD_EMPLEADOS`) aplicada en la subinterfaz de entrada de la VLAN Empleados (`Gi0/0.20`):

1. **Permitir Tráfico Web:** Acceso vía HTTP (TCP 80) y HTTPS (TCP 443) hacia la subred/servidor de destino (`192.168.30.0/24`).
2. **Aislamiento de Red:** Denegación explícita de todo tráfico IP/ICMP hacia la VLAN de Administración (`192.168.10.0/24`) y resto de zonas restringidas.

---

## 🧪 Pruebas de Validación

* **Denegación de Tráfico ICMP:** Intento de `ping` desde `pc-empleados` (`192.168.20.10`) hacia `pc-admin` (`192.168.10.10`) resultando en `Destination host unreachable` (100% de paquetes bloqueados por el router).
* **Acceso HTTP Exitoso:** Navegación exitosa desde `pc-empleados` hacia el servidor web (`http://192.168.30.10`).

---

## 🛠️ Tecnologías Utilizadas
* **Cisco Packet Tracer**
* **Cisco IOS CLI** (Switching L2, Trunking 802.1Q, Subinterfaces Router-on-a-Stick, Extended Named ACLs)
