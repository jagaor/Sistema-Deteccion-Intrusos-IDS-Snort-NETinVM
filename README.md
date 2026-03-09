# Implementación de un Sistema de Detección de Intrusos (IDS) con Snort

## 📝 Descripción General
Este proyecto, enmarcado en el módulo de "Hacking Ético", se enfoca en el estudio y la implementación práctica de mecanismos de defensa perimetral en redes corporativas. Utilizando el entorno de simulación de redes NETinVM, se ha desplegado y configurado el motor de detección de intrusos **Snort**. El objetivo principal es monitorizar el tráfico en tiempo real y generar alertas ante comportamientos anómalos o firmas de ataques conocidos.

## 🎯 Objetivos del Proyecto
* Comprender la arquitectura de red de NETinVM (separación entre red externa, DMZ y red interna).
* Instalar y configurar Snort como Sistema de Detección de Intrusos (IDS) en el nodo que actúa como firewall/pasarela.
* Diseñar e implementar reglas personalizadas de detección basadas en el comportamiento del tráfico de red.
* Detectar de forma activa fases de reconocimiento de red (Information Gathering) como escaneos ICMP (Ping).
* Identificar y alertar sobre intentos de acceso no autorizados a rutas sensibles en servidores web (fuerza bruta o enumeración de directorios).

## 🛠️ Tecnologías y Herramientas
* **Entorno de Simulación**: NETinVM (sobre hipervisor VMware/KVM).
* **Nodos Virtuales**: Linux (Debian) configurados como atacante (exta), firewall (fw) y servidor víctima (dmza/inta).
* **Motor IDS**: Snort (Versión 2.9.x).
* **Herramientas de Auditoría**: Ping, cURL y utilidades de red por línea de comandos.

## ⚙️ Detalles de Implementación Destacados
* **Configuración del Entorno (`snort.conf`)**: Se establecieron las variables de red principales para segmentar el tráfico, definiendo explícitamente la red externa (atacantes potenciales), la DMZ (servidores expuestos) y la red local.
* **Reglas de Detección ICMP**: Se programaron alertas específicas para monitorizar el tráfico entrante hacia la DMZ. Cuando la máquina atacante generó paquetes ICMP (Ping), Snort interceptó el tráfico y registró la alerta de reconocimiento en la consola.
* **Reglas de Detección HTTP**: Se añadieron firmas personalizadas al motor de Snort para examinar el contenido de las peticiones HTTP (Capa 7). El sistema fue capaz de detectar intentos de acceso mediante `curl` a paneles de administración restringidos y rutas críticas de bases de datos.
* **Validación de Alertas**: Se comprobó la eficacia del sistema lanzando ataques controlados desde la red externa y verificando los registros del daemon de Snort en el nodo firewall.

## 📄 Documentación Completa
Para ver el desarrollo completo de la práctica, los comandos de instalación, la sintaxis exacta de las reglas creadas y las capturas de pantalla de la terminal mostrando la detección de intrusos en tiempo real, consulta la memoria técnica del proyecto:

👉 [Enlace al Informe Técnico en Google Drive](https://docs.google.com/document/d/1hEbXomk3tiVCxOoHgzYjo3FrCJ1StskPc1a7GWIOwIo/edit?usp=sharing)

## ⚠️ Aviso Legal / Ética
*La configuración de sistemas IDS/IPS y las pruebas de intrusión aquí documentadas se han realizado en una red virtualizada (NETinVM) estrictamente aislada. Este proyecto tiene una finalidad exclusivamente académica para el aprendizaje de técnicas de Blue Teaming y defensa de redes.*
