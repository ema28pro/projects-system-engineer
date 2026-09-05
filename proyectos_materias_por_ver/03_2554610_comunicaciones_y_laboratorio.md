# 2554610 – Comunicaciones y Laboratorio

## 1. Ficha Técnica Oficial (UdeA)
* **Nombre de la Asignatura:** Comunicaciones y Laboratorio
* **Código de Curso:** 2554610
* **Nivel:** 6
* **Unidad Académica:** Facultad de Ingeniería – Departamento de Ingeniería de Sistemas
* **Área:** Básicas de Ingeniería
* **Créditos Académicos:** 4
* **Pre-requisitos:** Ninguno | **Co-requisitos:** Ninguno
* **Modalidad:** Virtual / Presencial
* **Libros Guía Oficiales:** *Computer Networking: A Top-Down Approach* (Kurose & Ross), *Computer Networks* (Tanenbaum & Wetherall).

---

## 2. Ejes Temáticos y Saberes Oficiales (según PDF)
1. **Introducción y Modelos de Red**
   * Historia, tipos de redes (LAN, MAN, WAN), topologías y medios físicos.
   * Concepto de protocolo, estándares y arquitectura en capas.
   * Comparación formal entre el **Modelo OSI de 7 capas** y la pila **TCP/IP de 4 capas**.
   * Proceso de encapsulamiento y desencapsulamiento de Unidades de Datos de Protocolo (PDU: Datos, Segmento, Paquete, Trama, Bits).
2. **Nivel de Aplicación**
   * Paradigmas de comunicación: Cliente-Servidor y Peer-to-Peer (P2P).
   * Servicios y protocolos fundamentales: **DNS** (resolución recursiva e iterativa, registros A, CNAME, MX), **HTTP/HTTPS** (métodos, cabeceras, códigos de estado), **SMTP, IMAP, POP3** para correo electrónico.
   * Programación de aplicaciones de red con la **API de Sockets** (flujo de sockets de flujo TCP vs datagramas UDP).
3. **Nivel de Transporte**
   * Multiplexación y demultiplexación mediante números de puerto.
   * Protocolo no orientado a conexión: **UDP** (cabecera ligera, casos de uso).
   * Protocolo orientado a conexión confiable: **TCP**:
     * Establecimiento y finalización de conexión (*Three-Way Handshake* y *Four-Way Teardown*).
     * Transferencia confiable de datos (números de secuencia, reconocimientos ACK, temporizadores de retransmisión).
     * Control de flujo mediante **Ventana Deslizante (*Sliding Window*)**.
     * Control de congestión: algoritmos **Slow-Start, Congestion Avoidance, Fast Retransmit y Fast Recovery**.
   * Protocolos auxiliares de arranque y configuración: BOOTP, **DHCP**, TFTP y PXE.
4. **Nivel de Red**
   * Funciones del nivel de red: conmutación (*forwarding*) y enrutamiento (*routing*).
   * El protocolo **IPv4**: estructura del datagrama, campos TTL, fragmentación y reensamblado.
   * Esquemas de direccionamiento: clases históricas, **Subnetting**, direccionamiento sin clases **CIDR** y máscaras de longitud variable **VLSM**.
   * Concepto y hardware de Routers y Switches de Nivel 3.
   * Protocolos de resolución y control: **ARP** (Address Resolution Protocol), RARP, **ICMP** (Ping, Traceroute).
   * Algoritmos y protocolos de enrutamiento dinámico:
     * Interior Gateway Protocols (IGP): Vector Distancia (**RIP**) y Estado de Enlace (**OSPF** con algoritmo de Dijkstra).
     * Exterior Gateway Protocols (EGP): Protocolo de Puerta de Enlace de Frontera (**BGP**).
5. **Nivel de Enlace de Datos**
   * Detección y corrección de errores en tramas (CRC, paridad, Checksum).
   * Técnicas de Control de Acceso al Medio (MAC): Redes compartidas, protocolo **CSMA/CD** (detección de colisiones y retroceso exponencial) en estándares IEEE 802.3 Ethernet.
   * Dispositivos de interconexión L2: Repetidores, Hubs, Puentes (*Bridges*) y **Switches L2** (aprendizaje transparente de direcciones MAC, tablas CAM).
   * Redes de Área Local Virtuales (**VLANs - IEEE 802.1Q**) y Spanning Tree Protocol (**STP - IEEE 802.1D**).
6. **Nivel Físico**
   * Medios guiados (par trenzado UTP Cat 5e/6, cable coaxial, fibra óptica monomodo y multimodo) e inalámbricos.
   * Técnicas de modulación y señalización: Banda Base (codificación Manchester, NRZ) vs Banda Ancha.
   * Comunicaciones seriales sincrónicas y asincrónicas.

---

## 3. Proyectos de Portafolio Recomendados

### Proyecto 1: Servidor Web HTTP/1.1 Concurrente y Sniffer de Paquetes desde Cero (Sockets Nativos)
* **Problema a Resolver:** Comprender exactamente cómo viajan los bytes a través de los sockets del sistema operativo sin depender de servidores prefabricados (como Nginx o Apache) e inspeccionar el tráfico de red en crudo.
* **Correspondencia con el PDF:**
  * Niveles de Aplicación, Transporte y Enlace: Programación con sockets TCP/UDP, parsing manual del protocolo HTTP/1.1, concurrencia (multi-hilo o select/epoll) y captura de paquetes promiscuos en crudo (*Raw Sockets*).
* **Requerimientos Funcionales y Técnicos:**
  1. **Servidor HTTP Concurrente (en C, Python o Rust con Sockets puros):**
     * Manejo de conexiones entrantes concurrentes mediante pool de hilos o I/O asíncrono no bloqueante.
     * Parser del protocolo HTTP: métodos `GET`, `POST`, `HEAD`, cabeceras `Host`, `Content-Type`, `Content-Length`, `Cookie` y `Connection: keep-alive`.
     * Servir archivos estáticos (HTML, CSS, imágenes binarias) con sus MIME types correctos y devolver errores estándar (`404 Not Found`, `400 Bad Request`, `500 Internal Error`).
  2. **Sniffer / Analizador de Paquetes Ligero (Mini-Wireshark en terminal):**
     * Capturar paquetes usando *Raw Sockets* o librería `pcap`.
     * Desensamblar manualmente: Cabecera Ethernet L2 (MAC origen y destino) $	o$ Cabecera IPv4 L3 (IP origen, IP destino, TTL, Protocolo) $	o$ Cabecera TCP/UDP L4 (Puertos, banderas SYN/ACK/FIN).
     * Imprimir los paquetes formateados en consola con decodificación de texto ASCII.
* **Stack Tecnológico:** C o Python (usando módulo `socket` y `struct`), Wireshark para validación.
* **Valor en Entrevistas Técnicas:** Demuestra entendimiento de redes a bajo nivel, llamadas al sistema (*syscalls*) de red y protocolos reales de Internet.

---

### Proyecto 2: Diseño, Simulación y Subnetting VLSM de una Red Corporativa en Cisco Packet Tracer / GNS3
* **Problema a Resolver:** Diseñar la infraestructura de red completa para una organización con 4 sedes regionales, garantizando aislamiento de tráfico por departamentos, enrutamiento dinámico y redundancia sin bucles.
* **Correspondencia con el PDF:**
  * Niveles de Red y Enlace: Subnetting VLSM, CIDR, VLANs (IEEE 802.1Q), Enrutamiento Inter-VLAN (Router-on-a-stick), OSPF multi-área, DHCP, NAT y STP.
* **Requerimientos Técnicos:**
  1. Diseño de direccionamiento usando una red base privada (ej. `172.16.0.0/16`), calculando tablas VLSM para optimizar el desperdicio de direcciones IP.
  2. Configuración de Switches L2: Creación de VLANs (VLAN 10: Administrativos, VLAN 20: Servidores, VLAN 30: Wi-Fi Invitados), puertos en modo Trunk y Access, y árbol de expansión Spanning Tree (STP) para evitar tormentas de broadcast.
  3. Enrutamiento dinámico entre sedes mediante **OSPFv2** con cálculo del costo de enlace basado en ancho de banda.
  4. Configuración de servidor **DHCP** con exclusión de IPs estáticas y pools dedicados por VLAN.
  5. Traducción de Direcciones de Red (**NAT / PAT**) para permitir acceso a la WAN pública de Internet.
  6. Lista de Control de Acceso (**ACL**) que impida a los usuarios de la VLAN de invitados acceder a la red de servidores.
* **Herramientas:** Cisco Packet Tracer o GNS3.
* **Valor en Entrevistas Técnicas:** Esencial para certificaciones de la industria (CCNA) y roles de NetOps, DevOps e Infraestructura Cloud.

---

### Proyecto 3: Simulador de Transferencia Confiable sobre UDP (Emulador de Ventana Deslizante y Control de Congestión)
* **Problema a Resolver:** UDP no garantiza entrega, ni orden, ni control de flujo. Implementar una capa sobre UDP que emule los mecanismos de fiabilidad de TCP demuestra comprensión exhaustiva del nivel de transporte.
* **Correspondencia con el PDF:**
  * Nivel de Transporte: Protocolo de Ventana Deslizante (Go-Back-N o Selective Repeat), temporizadores de retransmisión por timeout, ACKs acumulativos y Slow-Start.
* **Requerimientos Funcionales:**
  1. Cliente y Servidor comunicándose exclusivamente por datagramas UDP.
  2. Fragmentar un archivo grande en paquetes con cabeceras propias: `[SeqNum, AckNum, Flags, Checksum, Payload]`.
  3. Emulador de canal ruidoso: inyectar aleatoriamente una tasa de pérdida de paquetes del 10% y corrupción de checksums.
  4. Mecanismo de retransmisión por tiempo límite (*Timeout*) recalculando el RTT estimado.
  5. Ajuste dinámico del tamaño de la ventana de congestión ($cwnd$) demostrando gráficamente las fases de *Slow Start* y *Congestion Avoidance* (gráfico en diente de sierra de TCP).
* **Stack Tecnológico:** Python o Java.
