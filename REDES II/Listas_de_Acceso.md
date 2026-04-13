# Listas de Acceso (ACL) en Redes

## 📌 ¿Qué es una ACL?
Una **Lista de Control de Acceso (ACL - Access Control List)** es un conjunto de reglas que se utilizan en dispositivos de red (como routers y switches) para **permitir o denegar tráfico** basándose en ciertos criterios.

---

## 🎯 Objetivo
- Controlar el flujo de tráfico en la red
- Mejorar la seguridad
- Filtrar paquetes según reglas definidas

---

## ⚙️ ¿Cómo funcionan?
Las ACL evalúan los paquetes de red en orden secuencial:
1. Se compara el paquete con cada regla
2. Se aplica la primera coincidencia
3. Si no coincide con ninguna regla → **se deniega por defecto**

---

## 📂 Tipos de ACL

### 1. ACL Estándar
- Filtran solo por **dirección IP de origen**
- Menos precisas

**Ejemplo:**
access-list 10 permit 192.168.1.0 0.0.0.255


---

### 2. ACL Extendidas
- Filtran por:
  - IP de origen
  - IP de destino
  - Protocolo (TCP, UDP, ICMP)
  - Puertos
- Más seguras y específicas

**Ejemplo:**
access-list 100 permit tcp 192.168.1.0 0.0.0.255 any eq 80

---

## 📍 Ubicación de las ACL

- **ACL Estándar:** cerca del destino
- **ACL Extendida:** cerca del origen

---

## 🔑 Reglas importantes
- Se procesan de arriba hacia abajo
- Existe un **"deny any" implícito** al final
- El orden de las reglas es crítico

---

## 🧠 Conceptos clave

- **Wildcard Mask:** define qué bits comparar
- **Permit:** permite el tráfico
- **Deny:** bloquea el tráfico
- **Any:** representa cualquier dirección

---

## 📊 Ejemplo completo
access-list 100 permit tcp 192.168.1.10 0.0.0.0 any eq 80
access-list 100 deny ip any any

**Explicación:**
- Permite tráfico HTTP desde 192.168.1.10
- Bloquea todo lo demás

---

## 🚀 Conclusión
Las ACL son fundamentales para:
- Seguridad de red
- Control de acceso
- Administración del tráfico

Su correcta configuración permite proteger recursos y optimizar la red.

---
# Dirección IN y OUT en ACL (Access Control List)

## ¿Qué significan IN y OUT?

- IN (entrada): El tráfico se filtra cuando entra a la interfaz del router.
- OUT (salida): El tráfico se filtra cuando sale de la interfaz del router.

---

## Diferencia clave

- IN: Se evalúa antes de que el router procese el paquete.
- OUT: Se evalúa después de que el router decide a dónde enviarlo.

---

## Ejemplo visual

[PC] -----> (IN) [Router] (OUT) -----> [Servidor]

---

## Ejemplo de configuración

### ACL en entrada (IN)
interface GigabitEthernet0/0
 ip access-group 100 in

Filtra el tráfico antes de que el router lo procese.

---

### ACL en salida (OUT)
interface GigabitEthernet0/0
 ip access-group 100 out

Filtra el tráfico después del procesamiento del router.

---

## Reglas importantes

- Solo se puede aplicar una ACL por dirección (IN/OUT) por interfaz.
- Puede haber una ACL IN y una ACL OUT en la misma interfaz.
- El orden de aplicación afecta el comportamiento.

---

## Buenas prácticas

- Usar IN para bloquear tráfico lo antes posible.
- Usar OUT para controlar lo que el router envía.
- ACL extendidas suelen colocarse cerca del origen (IN).

---

## Ejemplo práctico

access-list 100 deny tcp any any eq 80
access-list 100 permit ip any any

interface GigabitEthernet0/0
 ip access-group 100 in

Bloquea tráfico HTTP antes de entrar al router.

---

## Conclusión

- IN: controla lo que entra
- OUT: controla lo que sale
- Elegir bien mejora seguridad y rendimiento
