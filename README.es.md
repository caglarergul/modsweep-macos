[English](README.md) · [Türkçe](README.tr.md) · [Deutsch](README.de.md) · **Español**

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.png">
    <img src="assets/logo-light.png" alt="modsweep" width="460">
  </picture>
</p>

<p align="center"><b>Limpia tus proyectos. Sigue construyendo.</b><br>
Encuentra, analiza y limpia con seguridad los <code>node_modules</code> de tus proyectos JavaScript — una app nativa de macOS.</p>

<p align="center">
  <a href="https://github.com/caglarergul/modsweep-macos/releases/latest"><b>Descargar la última versión</b></a>
  · <a href="https://caglarergul.github.io/modsweep-macos/?lang=es">Sitio web</a>
  · macOS 14 Sonoma o posterior · Apple Silicon e Intel
</p>

---

## Instalación

**Descarga:** baja `modsweep-<versión>.dmg` de la [última versión](https://github.com/caglarergul/modsweep-macos/releases/latest),
ábrelo y arrastra **modsweep** a **Aplicaciones**. Cada versión está firmada con Developer ID y notarizada por Apple,
así que se abre sin avisos.

**Actualizaciones:** desde la 1.4.0, modsweep se actualiza solo. Lo comprueba una vez al día, descarga la nueva
versión de GitHub Releases, verifica sus firmas y se reemplaza. **modsweep → Buscar actualizaciones…** lo comprueba
al momento; la comprobación diaria y la instalación automática se pueden desactivar en Ajustes.

**Homebrew:**

```bash
brew install --cask caglarergul/tap/modsweep   # instalar
brew upgrade --cask modsweep                   # actualizar
brew uninstall --cask --zap modsweep           # quitar la app y sus datos
```

**Requisitos:** macOS 14 Sonoma o posterior. Para instalar proyectos (Instalar y verificar) hace falta
[pnpm](https://pnpm.io/installation); también se admiten proyectos npm, yarn y bun.

## Qué hace

| | |
|---|---|
| **Analizar carpeta** | Encuentra los proyectos JavaScript de una carpeta y muestra cuánto ocupa cada `node_modules`, el gestor de paquetes, la última actividad y el estado de git, además de las cachés de npm/pnpm/yarn/bun y el disco libre. El total aparece en la barra de menús. |
| **Análisis profundo** | Encuentra problemas de instalación y arranque antes de que te afecten — lockfiles desincronizados o duplicados, versiones de Node distintas, `node-sass`, webpack antiguo con Node nuevo, Next 16 con configuración de webpack, Prisma, falta de `.env`, problemas de tiendas Stencil … — y propone una solución para cada uno. |
| **Limpiar** | Mueve a la **Papelera** las cachés de build (`.next`, `.turbo`, `.angular`, `.expo`, React Native `ios/build`, `ios/Pods`, `android/build` …) o las carpetas `node_modules` que elijas, para que puedas recuperarlas. No toca carpetas con un proceso de Node en marcha ni con archivos versionados en git. |
| **Compartir** | npm y yarn ponen una copia completa de cada paquete en cada proyecto. modsweep muestra qué versiones se repiten entre tus proyectos y mueve los que elijas a **un único almacén pnpm compartido** en este Mac, así cada versión se guarda una vez. Solo se añaden dos archivos locales (listados en `.git/info/exclude`): nada cambia para git ni para tu equipo. Cada proyecto se respalda antes y se revierte ante cualquier error, el `node_modules` antiguo va a la Papelera y puedes volver a npm/yarn cuando quieras. Requiere pnpm 10 o posterior. |
| **Instalar y verificar** | Instala los proyectos seleccionados y comprueba dependencias, comandos, typecheck, build y, si quieres, un servidor de desarrollo — con log en vivo, botón Detener y todo restaurado al final. |

Disponible en **English, Türkçe, Deutsch y Español** (Ajustes → Idioma).

## Seguridad

modsweep está hecho para proyectos reales conectados a sistemas en producción.

- **No se hace push ni deploy.** Los scripts que mencionan deploy, publish, push, migrate, vercel, shopify … nunca se
  ejecutan durante una prueba.
- **Las bases de datos son inalcanzables.** Durante la prueba, las direcciones de base de datos, Redis y Mongo de los
  `.env` no apuntan a nada.
- **Tus archivos se restauran.** `package.json`, los lockfiles y el estado de git se guardan antes de la prueba y se
  reponen después — también al pulsar Detener.
- **No queda ningún proceso.** Los servidores de prueba se detienen por árbol de procesos y por carpeta.
- **A prueba de cierres inesperados.** Si el Mac o la app se detienen en mitad de una prueba, modsweep restaura el
  proyecto en el siguiente arranque, antes de hacer cualquier otra cosa.
- **Limpiar va a la Papelera.** La app no borra nada de forma definitiva.

## Primer arranque

modsweep sugiere tu carpeta personal, pero no analiza nada por su cuenta. Elige la carpeta con tus proyectos (por
ejemplo `~/Developer` o `~/www`) y pulsa Analizar. Puedes cambiarla cuando quieras desde la barra lateral o en
Ajustes.

Si Node, pnpm u otras herramientas vienen de nvm, asdf o mise, añade su carpeta en **Ajustes → Herramientas**.

## Privacidad

modsweep no tiene cuenta, analíticas ni seguimiento. Solo se conecta a internet cuando tú lo pides: al instalar
paquetes en Instalar y verificar y en la comprobación opcional de tiendas Stencil del análisis (se puede desactivar
en Ajustes).

## Desinstalar

`brew uninstall --cask --zap modsweep`, o arrastra modsweep de Aplicaciones a la Papelera y borra
`~/Library/Application Support/modsweep`.

## Exención de responsabilidad

modsweep es gratuito y se ofrece «tal cual», sin garantía. Modifica archivos en tu ordenador (Papelera, instalación
de paquetes, builds); lo usas bajo tu responsabilidad. Haz copias de seguridad y usa control de versiones. Texto
completo: [exención de responsabilidad](DISCLAIMER.es.md).

---

Este repositorio solo aloja los archivos de las versiones; el código fuente no es público.

Copyright © 2026 Caglar Ergul. Todos los derechos reservados.
