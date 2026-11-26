# YozhProxificator para Mac

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · Español · [Português](README.pt.md) · [Tiếng Việt](README.vi.md) · [Bahasa Indonesia](README.id.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md)

El tráfico de su Mac a través de proxies: todo el Mac o solo las aplicaciones que elija.

- **Todo el Mac.** «Todo el tráfico» envía por el proxy todo lo que envía el Mac, incluso las aplicaciones que ignoran los ajustes de proxy.
- **Cada aplicación a su manera.** Puede enviar una aplicación por su propio proxy o cadena, directamente o sin red alguna, y hacer lo mismo con listas enteras de sitios.
- **Sin fugas.** El corte de emergencia no deja que una aplicación con regla salga a la red si no es por su proxy, incluso cuando la conexión está desactivada. En «Todo el tráfico», el propio proxy encuentra las direcciones de los sitios, así que una prueba de fugas de DNS muestra el lado del proxy.
- **Cualquier proxy.** HTTP, HTTPS y SOCKS5; enlaces y suscripciones de VLESS, VMess, Trojan, Shadowsocks y Hysteria2; cadenas de dos proxies.
- **Comprobación con un clic.** «Comprobar» muestra si un proxy funciona, con qué rapidez se conecta y en qué país sale.
- **Para clientes de CyberYozh.** Sus proxies comprados se cargan con la clave de API. El generador crea proxies de rotación por país, ciudad y proveedor, y puede darles un SO elegido y la huella TLS de un navegador. Los proxies móviles cambian de IP con un clic.

## Descarga

Este enlace siempre da la última versión:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Requisitos: un Mac con Apple silicon, macOS 15 o posterior.

La descarga es una imagen de disco. Contiene la aplicación y un acceso directo a la carpeta Aplicaciones, nada más. Abra
la imagen y arrastre YozhProxificator a Aplicaciones, o abra la aplicación desde la imagen: le ofrece moverse allí por sí
misma. La aplicación se actualiza desde este repositorio; las actualizaciones están firmadas y las comprobaciones
automáticas se pueden desactivar en sus ajustes.

## Compruebe lo que descargó

Cada versión pública, `vX.Y.Z`, tiene un archivo `SHA256SUMS` con el SHA-256 de sus archivos. Descárguelo en la carpeta
donde está la imagen y ejecute, en Terminal, en esa carpeta:

    shasum -a 256 -c SHA256SUMS --ignore-missing

Una compilación de prueba de la versión `acceptance` tiene en cambio un archivo `SHA256SUMS-X.Y.Z` propio: descargue ese
junto a la imagen y ponga su nombre en el comando.

La imagen está firmada con Developer ID y notarizada por Apple. Ponga el nombre de su archivo en lugar de
`YozhProxificator.dmg`:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

Responde `accepted` y `source=Notarized Developer ID`.

## Código fuente

YozhProxificator es software libre bajo la GNU GPL v3, sin garantía. Cada versión pública `vX.Y.Z` y cada compilación de
prueba de la versión `acceptance` incluye el código fuente completo de lo que distribuye:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — la aplicación, su componente del sistema y los scripts de compilación;
- `yozh-xray-<commit>-source.tar.gz` — el motor de proxy, una bifurcación de Xray-core, en el commit que fija la
  compilación (`<commit>` son los primeros doce caracteres de ese commit);
- `sparkle-<version>-source.tar.gz` — el framework de actualizaciones.

## Cómo desinstalar

1. En **Configuración → Todo el tráfico** de la aplicación, pulse **Eliminar componente**.
2. Mueva la aplicación a la Papelera.
3. Si las aplicaciones se quedan sin red, abra **Yozh Unblock** desde Aplicaciones. Si tras la eliminación se pierde la
   red, ejecute `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` en Terminal.

## Los canales de actualización

La aplicación lee un canal —una lista de versiones, con las imágenes y las notas a las que apuntan— para saber si existe
una versión más reciente. Hay dos canales, cada uno en una versión propia:

- `acceptance` es una versión preliminar con las compilaciones de prueba internas (0.9.x) y su canal, no para uso
  general. Cada compilación viene con sus archivos de código fuente y su propio `SHA256SUMS-X.Y.Z`; un archivo del motor
  o del framework que comparten varias compilaciones se guarda una sola vez. Las compilaciones de prueba leen este
  canal, y 1.0.0 también se publica en él, así que con ella pasan al canal público.
- `updates` es el canal de las versiones públicas. Es para la aplicación, no para descargar; el código fuente de cada
  versión que contiene está en la versión `vX.Y.Z` correspondiente.
