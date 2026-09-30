<div align="center">

# 🟣 Inuyaxs Server Management

**Crea y administra servidores de Minecraft directamente desde tu teléfono Android.**
Sin PC, sin Termux, sin configurar nada a mano.

[![Última versión](https://img.shields.io/github/v/release/herreralucianoalberto-star/inuyaxs-server-management?style=for-the-badge&color=8B7CFF&label=versi%C3%B3n)](https://github.com/herreralucianoalberto-star/inuyaxs-server-management/releases/latest)
[![Descargas](https://img.shields.io/github/downloads/herreralucianoalberto-star/inuyaxs-server-management/total?style=for-the-badge&color=3DDC84&label=descargas)](https://github.com/herreralucianoalberto-star/inuyaxs-server-management/releases)
[![Licencia](https://img.shields.io/github/license/herreralucianoalberto-star/inuyaxs-server-management?style=for-the-badge&color=blue)](LICENSE)
![Android 5.0+](https://img.shields.io/badge/Android-5.0%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![Kotlin](https://img.shields.io/badge/Kotlin-Jetpack%20Compose-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)
![Material 3](https://img.shields.io/badge/Material-3-6750A4?style=for-the-badge&logo=materialdesign&logoColor=white)

### [⬇️ Descargar el APK](https://github.com/herreralucianoalberto-star/inuyaxs-server-management/releases/latest)

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

1. Ve a **[Releases](https://github.com/herreralucianoalberto-star/inuyaxs-server-management/releases/latest)** y descarga el `.apk` de la última versión.
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
- **OpenJDK aarch64** (17/21, compilado para Android) se descarga de los paquetes oficiales del repositorio de Termux. Solo se bajan los archivos; Termux no hace falta y no se usa.
- Java se ejecuta con `ProcessBuilder` desde la carpeta privada de la app, y se genera un almacén de certificados a partir de los de Android para que Java pueda usar HTTPS.
- El agente de Playit se descarga una vez y se detiene junto con el servidor.

## 🛠️ Compilar desde Termux (solo para compilar)

<details>
<summary>Ver los pasos</summary>

1. OpenJDK 17 y utilidades:
   ```bash
   pkg update && pkg install openjdk-17 wget unzip git
   ```
2. Android SDK (command-line tools para Linux ARM):
   ```bash
   mkdir -p ~/android-sdk/cmdline-tools && cd ~/android-sdk/cmdline-tools
   wget https://dl.google.com/android/repository/commandlinetools-linux-11076708_latest.zip
   unzip commandlinetools-linux-*.zip && mv cmdline-tools latest
   export ANDROID_HOME=$HOME/android-sdk
   export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin
   yes | sdkmanager --licenses
   ```
3. Plataforma y build-tools:
   ```bash
   sdkmanager "platforms;android-35" "build-tools;35.0.0" "platform-tools"
   ```
4. Gradle 8.10 / Wrapper:
   ```bash
   pkg install gradle          # o descarga Gradle 8.10 manualmente
   gradle wrapper --gradle-version 8.10
   chmod +x gradlew
   ```
5. AAPT2 para ARM (los binarios de Maven son x86):
   ```bash
   pkg install aapt2
   echo "android.aapt2FromMavenOverride=$PREFIX/bin/aapt2" >> gradle.properties
   echo "sdk.dir=$HOME/android-sdk" > local.properties
   ```
6. Compilar:
   ```bash
   ./gradlew assembleRelease
   ```
7. APK resultante (firmado con la clave debug para poder instalarlo):
   `app/build/outputs/apk/release/Inuyaxs Server Management.apk`

</details>

## 🐛 Problemas y sugerencias

¿Algo no funciona o quieres proponer una mejora? Abre un [issue](https://github.com/herreralucianoalberto-star/inuyaxs-server-management/issues/new/choose). Si es un error, incluye tu versión de Android, la versión de la app y lo que muestra la consola del servidor.

## 📄 Licencia

Distribuido bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE).

## ⚠️ Aviso

Proyecto independiente. **No está afiliado, aprobado ni patrocinado por Mojang Studios, Microsoft, PaperMC, GeyserMC ni Playit.gg.** Minecraft es una marca registrada de Mojang Studios.

---

<div align="center">Hecho con 💜 por <b>Inuyaxs</b></div>
