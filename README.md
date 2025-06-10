# 🔗 Kutt - Acortador de URLs en Producción con Docker

**Kutt** es una aplicación web de código abierto para **acortar URLs**, similar a servicios como Bitly o TinyURL, pero que puedes **hospedar tú mismo**. Está construida con Node.js, MongoDB y Redis, y es ideal para quienes desean tener **control total sobre sus enlaces cortos**.


### ✅ Ventajas de Kutt

* **Código abierto y gratuito**
  No dependes de servicios externos ni de licencias de pago.

* **Autohospedado**
  Puedes usar tu propio dominio (por ejemplo, `go.codadry.com`) para los enlaces.

* **Privacidad total**
  Tú controlas todos los datos y estadísticas generadas.

* **Interfaz moderna y fácil de usar**
  Incluye panel de administración, estadísticas básicas y soporte para extensiones.

Este repositorio contiene la configuración lista para producción del acortador de enlaces [**Kutt**](https://github.com/thedevs-network/kutt), usando Docker Compose, MongoDB, Redis y variables de entorno seguras.

---

## 🚀 ¿Qué hace este proyecto?

- Despliega **Kutt** como acortador de URLs bajo tu dominio personalizado.
- Solo **usuarios autorizados** pueden iniciar sesión y acortar enlaces.
- Desactiva el registro público de usuarios.
- Se integra fácilmente con Nginx Proxy Manager y HTTPS.

---

## 📦 Servicios incluidos

| Servicio  | Imagen Docker        | Descripción                          |
|-----------|----------------------|--------------------------------------|
| `mongodb` | `mongo:5`            | Base de datos principal para Kutt    |
| `redis`   | `redis:alpine`       | Cache para rendimiento               |
| `kutt`    | `kutt/kutt`          | Aplicación principal                 |

---

## 🛠 Requisitos

- Docker y Docker Compose
- Red externa llamada `general-net` (ya creada)
- Nginx Proxy Manager configurado apuntando a `kutt-app`
- Un dominio tipo `tu.dominio.com` con CNAME activo

---

## 🔒 Seguridad en Producción

Este entorno está diseñado para **uso privado**, sólo por el administrador:

```env
ADMIN_EMAILS=admin@codadry.com
DISALLOW_REGISTRATION=1
````

---


## ⚙️ Uso

1. Clona el repositorio:

```bash
git clone https://github.com/codadry/kutt.git
cd kutt
```

2. Asegúrate de tener una red Docker llamada `general-net`:

```bash
docker network create general-net
```

3. Levanta los servicios:

```bash
docker compose up -d
```

4. Accede a tu dominio (pero tambien configuralo en Nginx Proxy Manager):
   `https://tu.dominio.com`

---

## ✉️ ¿Y los correos?

La configuración de correo actual es *dummy*.
Si necesitas activar recuperación de contraseñas o notificaciones, reemplaza `MAIL_*` por los datos reales de tu servidor SMTP (por ejemplo: Mailtrap, Gmail, Sendinblue, etc.).

---

## 📸 Capturas
![image](https://github.com/user-attachments/assets/3ee095cb-bac0-4f60-8e8f-71e7b23c3ae2)

![image](https://github.com/user-attachments/assets/19c82fe4-d2dc-4c42-9b06-cf60443d9c5a)


---

## 🤝 Créditos

Proyecto basado en:
👉 [https://github.com/thedevs-network/kutt](https://github.com/thedevs-network/kutt)

Configurado por [Codadry](https://www.youtube.com/@Codadry)
🎓 Canal educativo sobre programación, Java, Docker y más.

