# 2554840 – Comunicaciones II

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Comunicaciones II
* **Código de Curso:** 2554840
* **Nivel:** 8
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería / Redes
* **Créditos Académicos:** 3
* **Pre-requisitos:** 2554610 – Comunicaciones y Laboratorio
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Network Security Essentials: Applications and Standards* (William Stallings), *Building Microservices* (Sam Newman - Comunicación asíncrona y gRPC).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Módulo I: Desarrollo de Aplicaciones en Red y Arquitecturas Móviles**
   * Paradigmas de programación de red avanzados: sockets no bloqueantes e I/O multiplexado (**epoll / select**).
   * Comunicación bidireccional en tiempo real: protocolo **WebSockets (RFC 6455)** frente a polling HTTP.
   * Protocolos eficientes para dispositivos móviles y entornos IoT:
     * **MQTT (Message Queuing Telemetry Transport)**: arquitectura Publish/Subscribe, niveles de calidad de servicio (QoS 0, 1, 2) y brokers (Mosquitto).
     * **gRPC y Protocol Buffers (Protobuf)**: comunicación binaria de alto rendimiento sobre HTTP/2, streaming unidireccional y bidireccional.
2. **Módulo II: Seguridad Perimetral y Redes Seguras**
   * Fundamentos de seguridad perimetral; arquitectura de una **Zona Desmilitarizada (DMZ)**.
   * Tipos y evolución de **Firewalls**:
     * Filtrado de paquetes sin estado (*Stateless Packet Filtering*).
     * Inspección de estado (*Stateful Inspection Firewalls* con `iptables / nftables`).
     * Firewalls de Aplicación Web (**WAF**) y Proxies inversos.
   * Redes Privadas Virtuales (**VPNs**):
     * Protocolo **IPsec**: modos transporte y túnel, protocolos AH y ESP, intercambio de llaves IKE.
     * VPNs de capa de aplicación: **OpenVPN** y **WireGuard**.
   * Detección y Prevención de Intrusos (**IDS / IPS**): Arquitectura de firmas y anomalías con **Snort / Suricata**.
   * Auditoría de seguridad y escaneo de puertos y vulnerabilidades con **Nmap**.
3. **Módulo III: Redes Inalámbricas y Móviles**
   * Estándares **IEEE 802.11 (Wi-Fi)**: 802.11ac (Wi-Fi 5), 802.11ax (Wi-Fi 6), bandas de 2.4 GHz y 5 GHz.
   * Seguridad en redes inalámbricas: debilidades de WEP, protocolo WPA2 (Handshake de 4 vías y vulnerabilidad KRACK), y estándar moderno **WPA3** (SAE - Simultaneous Authentication of Equals).
   * Autenticación empresarial: protocolo 802.1X y servidores **RADIUS**.
   * Tecnologías inalámbricas para IoT: redes de área amplia y baja potencia (**LoRaWAN**), Zigbee y Bluetooth Low Energy (BLE).
   * Evolución de las redes celulares: de 4G LTE a 5G (Network Slicing, latencia ultra-baja URLLC).

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Laboratorio de Seguridad Perimetral: Firewall Stateful, DMZ y Detección de Intrusos (IDS)
* **Problema a Resolver:** Aislar y proteger los servidores de producción de una empresa simulando ataques reales (escaneo de puertos, fuerza bruta SSH, flooding) y bloqueándolos automáticamente en el perímetro.
* **Correspondencia con el PDF:**
  * Módulo II: Configuración de Stateful Firewall (`iptables`), arquitectura DMZ con 3 interfaces de red, VPN segura con WireGuard/OpenVPN y despliegue del IDS Suricata/Snort.
* **Requerimientos Funcionales y Técnicos:**
  1. **Topología de Red Virtualizada (en Docker o VirtualBox/Vagrant):**
     * Red Pública (WAN simulada con host atacante).
     * Red DMZ (servidor Web Nginx público).
     * Red Interna / LAN (servidor de base de datos privado y usuarios internos).
  2. **Firewall Stateful (Linux `nftables` / `iptables`):**
     * Reglas estrictas: Política por defecto `DROP`.
     * Permitir tráfico de salida y conexiones establecidas (`ESTABLISHED,RELATED`).
     * Redirigir puertos WAN al servidor web DMZ (*Port Forwarding* con NAT).
     * Aislar completamente la base de datos para que solo acepte peticiones originadas en la DMZ.
  3. **Sistema IDS (Suricata / Snort):**
     * Configurar reglas de detección de escaneos sigilosos de Nmap (`SYN Scan`).
     * Detección automática de ataques de denegación de servicio (DoS) y generación de alertas en tiempo real en logs de auditoría.
  4. **Túnel VPN con WireGuard:** Configurar acceso remoto seguro para que administradores se conecten a la LAN interna cifrando el tráfico de extremo a extremo.
* **Stack Tecnológico:** Linux (Debian/Ubuntu), `nftables`, Suricata, WireGuard, Docker / Vagrant, Nmap.
* **Valor en Entrevistas Técnicas:** Esencial para roles de **Ciberseguridad**, **Security Engineer**, **DevSecOps** y Administrador de Redes.

---

### Proyecto 2: Sistema de Telemetría IoT en Tiempo Real con MQTT, WebSockets y gRPC
* **Problema a Resolver:** Ingerir miles de métricas de sensores remotos distribuidos con bajo consumo de ancho de banda y proyectarlas en un dashboard web en tiempo real sin recargar la página.
* **Correspondencia con el PDF:**
  * Módulo I: Protocolo MQTT (Publish/Subscribe con QoS), comunicación de alto rendimiento gRPC con Protocol Buffers y transmisión continua a navegadores con WebSockets.
* **Requerimientos Funcionales:**
  1. Emulador de 100 sensores de IoT que transmiten lecturas de temperatura, humedad y estado a un Broker **Mosquitto MQTT** usando QoS 1.
  2. Microservicio Backend consumidor (en Go o Node.js) que se suscribe a los topics MQTT y procesa los datos en streaming.
  3. Servidor de streaming interno en **gRPC** para comunicar microservicios backend a alta velocidad serializando con Protobuf.
  4. Gateway WebSocket que transmite las lecturas en vivo a un dashboard web interactivo con gráficos en tiempo real.
* **Stack Tecnológico:** Go o Node.js, Eclipse Mosquitto (MQTT), gRPC / Protobuf, WebSockets, Chart.js / Grafana.
* **Valor en Entrevistas Técnicas:** Demuestra dominio de arquitecturas modernas de streaming de eventos, IoT y microservicios reactivos.
