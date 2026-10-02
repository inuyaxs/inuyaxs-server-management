<div align="center">

# 🔴 Inuyaxs Server Management

**Crea y administra servidores de Minecraft directamente desde tu teléfono Android.**
Sin PC y sin configurar nada a mano.

[![Última versión](https://img.shields.io/github/v/release/inuyaxs/inuyaxs-server-management?style=for-the-badge&color=E53935&label=versi%C3%B3n)](https://github.com/inuyaxs/inuyaxs-server-management/releases/latest)
[![Descargas](https://img.shields.io/github/downloads/inuyaxs/inuyaxs-server-management/total?style=for-the-badge&color=C62828&label=descargas)](https://github.com/inuyaxs/inuyaxs-server-management/releases)
[![Licencia](https://img.shields.io/github/license/inuyaxs/inuyaxs-server-management?style=for-the-badge&color=B71C1C)](LICENSE)
![Android 5.0+](https://img.shields.io/badge/Android-5.0%2B-D32F2F?style=for-the-badge&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack%20Compose-E53935?style=for-the-badge&logo=kotlin&logoColor=white)
![Material 3](https://img.shields.io/badge/Material-3-C62828?style=for-the-badge&logo=materialdesign&logoColor=white)

### [⬇️ Descargar el APK](https://github.com/inuyaxs/inuyaxs-server-management/releases/latest)

</div>

---

## ✨ ¿Qué es?

**Inuyaxs Server Management** es una app para Android que convierte tu teléfono en un servidor de Minecraft. Elige la versión, pulsa **Iniciar Servidor** y listo: la app descarga y prepara Java y Paper por ti, y mantiene el servidor vivo en segundo plano.

<!-- Cuando tengas capturas, súbelas a docs/screenshots y descomenta esta tabla:
<div align="center">
<img src="docs/screenshots/detalle.jpg" width="240"> <img src="docs/screenshots/crear.jpg" width="240"> <img src="docs/screenshots/playit.jpg" width="240">
</div>
-->

## 🚀 Funciones

| | Función | Detalle |
|---|---|---|
| ☕ | **Servidores Java** | Paper con las versiones 1.18.2, 1.19.4, 1.20.4, 1.20.6, 1.21.1 y 1.21.4. Java 17 o 21 se elige solo según la versión. |
| 🪨 | **Bedrock** *(experimental)* | Paper + Geyser + Floodgate instalados y configurados automáticamente (UDP 19132). |
| 🖥️ | **Consola en vivo** | Mira el log y envía comandos al servidor desde la app. |
| 📊 | **Panel del servidor** | Jugadores conectados, **RAM usada en tiempo real** y tiempo encendido. |
| 🌐 | **IP del servidor** | Muestra tu **IP local** con el puerto y botón de copiar. |
| 🔗 | **Playit.gg** | Juega online sin abrir puertos. La app detecta y muestra la **IP pública de tu túnel**. |
| 🔌 | **Plugins** | Instala archivos `.jar` con el selector de archivos. |
| 💾 | **Backups** | Copias manuales y automáticas programables. |
| ⚙️ | **Ajustes** | Modo de juego, máximo de jugadores, modo cracked, mensajes automáticos y más. |
| 🔔 | **Segundo plano** | Servicio en primer plano: el servidor sigue corriendo con la pantalla apagada. La descarga de Java y Paper también corre en segundo plano, con progreso y tiempo estimado. |

## 📲 Instalación

1. Ve a **[Releases](https://github.com/inuyaxs/inuyaxs-server-management/releases/latest)** y descarga el `.apk` de la última versión.
2. Ábrelo. Si Android lo pide, permite **instalar apps de fuentes desconocidas** para tu navegador.
3. Abre la app, crea tu servidor y pulsa **Iniciar Servidor**.

> La primera vez necesitas internet: la app descarga Java, Paper y, si lo activas, el agente de Playit.

### Requisitos

- Android 5.0 o superior.
- Procesador **64 bits (arm64-v8a)**: es un requisito del Java que usa la app.
- Espacio libre para Java, el servidor y tus mundos (varios cientos de MB como mínimo).
- RAM: cuanta más tengas libre, mejor. La app limita la RAM del servidor según la memoria disponible del dispositivo.

## 🌍 Jugar online con Playit.gg

1. Crea una cuenta gratis en [playit.gg](https://playit.gg) y copia el **Secret** de tu agente.
2. En la app, abre tu servidor → pestaña **Playit** → pega el token, activa y guarda.
3. Crea en playit.gg un túnel de **Minecraft Java** (TCP) o **Bedrock** (UDP) hacia tu agente.
4. Inicia el servidor: la app muestra la dirección pública en la tarjeta de IP, lista para copiar y compartir.

Sin Playit, solo pueden entrar jugadores conectados a tu misma red (usa la **IP local** de la tarjeta).

## 🔐 Permisos

| Permiso | Motivo |
|---|---|
| `INTERNET`, `ACCESS_NETWORK_STATE` | Descargar Paper, Java, Geyser, Floodgate y el agente de Playit; túnel Playit |
| `FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_SPECIAL_USE` | Mantener vivos los servidores en segundo plano |
| `WAKE_LOCK` | Evitar que el procesador se suspenda con servidores activos |
| `POST_NOTIFICATIONS` | Notificación persistente de servidores activos (Android 13+) |
| `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS` | Permite excluir la app del ahorro de batería |
| `READ_EXTERNAL_STORAGE` (hasta API 32) | Elegir plugins `.jar` con el selector del sistema |

Los datos de los servidores se guardan en el almacenamiento interno de la app (`files/minecraft_servers/`).

## 🧩 Cómo funciona por dentro

- **Paper** se descarga desde la API oficial.
- **OpenJDK aarch64** (17/21, compilado para Android) se descarga de paquetes oficiales la primera vez que se necesita.
- Java se ejecuta con `ProcessBuilder` desde la carpeta privada de la app, y se genera un almacén de certificados a partir de los de Android para que Java pueda usar HTTPS.
- El agente de Playit se descarga una vez y se detiene junto con el servidor.

## 🐛 Problemas y sugerencias

¿Algo no funciona o quieres proponer una mejora? Abre un [issue](https://github.com/inuyaxs/inuyaxs-server-management/issues/new/choose). Si es un error, incluye tu versión de Android, la versión de la app y lo que muestra la consola del servidor.

## 📄 Licencia

Distribuido bajo la licencia **Source-available. All rights reserved.**. Consulta el archivo [LICENSE](LICENSE).

## ⚠️ Aviso

Proyecto independiente. **No está afiliado, aprobado ni patrocinado por Mojang Studios, Microsoft, PaperMC, GeyserMC ni Playit.gg.** Minecraft es una marca registrada de Mojang Studios.

---

<div align="center">Hecho con ♥️ por <b>Inuyaxs</b></div>
