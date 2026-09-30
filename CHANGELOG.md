# Changelog

Todos los cambios importantes del proyecto se documentan aquí.

## [1.0.1] - 2026-09-30

### Añadido
- Tarjeta de **IP local** con puerto y botón de copiar en el detalle del servidor.
- **IP pública de Playit.gg**: se detecta desde la salida del agente, se muestra y se guarda como última dirección conocida.
- **RAM usada en tiempo real** en el panel del servidor.

### Corregido
- El servidor no arrancaba con el error `dl failure` / `libc++_shared.so not found`. Ahora se instala la librería faltante y los runtimes ya instalados se reparan solos al iniciar.

## [1.0.0]

- Primera versión: servidores Java y Bedrock (experimental), consola, plugins, backups, Playit.gg y servicio en segundo plano.
