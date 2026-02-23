# Introducción al Red Teaming 🔴

En el mundo de la ciberseguridad, un **Red Team** (Equipo Rojo) es un grupo de profesionales de seguridad ofensiva que simulan ciberataques del mundo real contra una organización. 

A diferencia de un análisis de vulnerabilidades tradicional, el Red Team no se limita a buscar fallos; intenta explotarlos para medir la capacidad de detección y respuesta de la organización.

---

## Objetivos Principales

El propósito de un ejercicio de Red Team es poner a prueba las defensas de la empresa (conocidas como el *Blue Team*). Sus objetivos principales incluyen:

* **Identificar brechas de seguridad** físicas, lógicas y humanas.
* **Evaluar la capacidad de respuesta** del equipo de seguridad interna.
* **Simular tácticas de adversarios reales** (APTs, ransomware, etc.).
* **Mejorar la postura de seguridad global** mediante informes detallados.

---

## Herramientas y Scripts

Los miembros de un Red Team utilizan una variedad de herramientas para la fase de reconocimiento (recopilación de información). A menudo, crean sus propios scripts automatizados.

### Ejemplo: Escáner de Puertos Básico en Python

Durante la fase de reconocimiento, un atacante ético necesita saber qué puertos están abiertos en un servidor objetivo. Aquí tienes un ejemplo de un script básico en **Python** para escanear puertos:

```python
import socket

def escanear_puertos(ip, puertos):
    print(f"Iniciando escaneo en la IP: {ip}")
    
    for puerto in puertos:
        # Crear un socket IPv4 (AF_INET) y TCP (SOCK_STREAM)
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        socket.setdefaulttimeout(1) # Tiempo de espera de 1 segundo
        
        # Intentar la conexión
        resultado = sock.connect_ex((ip, puerto))
        if resultado == 0:
            print(f"[+] El puerto {puerto} está ABIERTO")
        else:
            print(f"[-] El puerto {puerto} está CERRADO")
            
        sock.close()

# Definir el objetivo y una lista de puertos comunes (ej: HTTP, HTTPS
