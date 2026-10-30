# Plataforma Web - Guía de Inicio del Entorno de Desarrollo

Este documento establece los requisitos base y los pasos para configurar el entorno de ejecución local con **Ruby 3.4** y **Ruby on Rails 8.1**.

---

## 📋 1. Requisitos Previos (Herramientas Base)

Antes de instalar Ruby o Rails, asegúrate de contar con las siguientes herramientas en tu sistema operativo:

### A. Control de Versiones: Git

- **Instalación:**
  - **Windows:** Descargar desde [git-scm.com](https://git-scm.com/) e instalar con las opciones por defecto.
  - **Linux (Ubuntu/Debian / WSL):** `sudo apt update && sudo apt install -y git`
  - **Linux (Fedora / WSL):** `sudo dnf install -y git`
- **Verificación:**
  ```bash
  git --version
  ```

### B. Entorno de Ejecución JavaScript: Node.js y Gestor de Paquetes

Requerido para la gestión de dependencias del ecosistema frontend y herramientas auxiliares de compilación.

- **Versión recomendada:** **Node.js LTS (v20.x o v22.x)**.
- **Instalación:**
  - **Windows:** Descargar el instalador LTS desde [nodejs.org](https://nodejs.org/).
  - **Linux / WSL:** Se recomienda instalar mediante NodeSource o gestores como `nvm` o `fnm`:
    ```bash
    # Ejemplo con nvm
    nvm install --lts
    nvm use --lts
    ```
- **Habilitar Corepack (npm / yarn):**
  ```bash
  corepack enable
  ```
- **Verificación:**
  ```bash
  node -v
  npm -v
  ```

### C. Herramientas de Compilación del Sistema

Las gemas de Ruby con código nativo en C/C++ requieren herramientas de compilación en el sistema anfitrión:

- **En Linux (Fedora / WSL):**
  ```bash
  sudo dnf groupinstall -y "Development Tools"
  sudo dnf install -y zlib-devel gcc-c++ patch readline-devel libyaml-devel libffi-devel openssl-devel bzip2 autoconf automake libtool bison
  ```
- **En Linux (Ubuntu / Debian / WSL):**
  ```bash
  sudo apt update
  sudo apt install -y build-essential libssl-dev libyaml-dev libreadline-dev zlib1g-dev libffi-dev libgdbm-dev
  ```
- **En Windows nativo:**
  - Se gestiona automáticamente al descargar el instalador **Ruby+Devkit** (MSYS2) en el paso siguiente.

---

## 💎 2. Instalación de Ruby 3.4.x

### Opción 1: En Linux / WSL (Fedora, Ubuntu) usando un Gestor de Versiones

Para entornos UNIX/WSL es preferible gestionar versiones mediante herramientas como **`mise`** o **`rbenv`** para evitar interferir con el Ruby del sistema:

1. **Instalar Ruby 3.4:**

   ```bash
   # Con mise:
   mise use --global ruby@3.4

   # O con rbenv:
   rbenv install 3.4.1
   rbenv global 3.4.1
   ```

2. **Confirmar la versión activa:**
   ```bash
   ruby -v
   # Salida esperada: ruby 3.4.x...
   ```

### Opción 2: En Windows Nativo (RubyInstaller)

1. Descarga el paquete **`Ruby+Devkit 3.4.x (x64)`** desde [rubyinstaller.org](https://rubyinstaller.org/downloads/).
2. Ejecuta el instalador marcando la casilla **"Add Ruby executables to your PATH"**.
3. Al finalizar, deja seleccionada la opción `ridk install` (opción 3: `MSYS2 and MINGW development toolchain`) para compilar gemas con extensiones nativas.
4. Abre PowerShell y confirma:
   ```powershell
   ruby -v
   ```

---

## 🚀 3. Instalación de Ruby on Rails 8.1

Una vez que Ruby y las herramientas de compilación estén operativas:

1. **Actualizar el gestor de paquetes de Ruby (RubyGems):**

   ```bash
   gem update --system
   ```

2. **Instalar la gema oficial de Rails:**

   ```bash
   gem install rails -v "~> 8.1"
   ```

3. **Verificar la instalación:**
   ```bash
   rails -v
   # Salida esperada: Rails 8.1.x
   ```

---

## 🛠️ 4. Verificación del Entorno Completo

Ejecuta el siguiente chequeo en tu terminal para validar que todas las herramientas esenciales están reconocidas en tu `$PATH`:

```bash
git --version      # Git 2.x+
node -v            # v20.x o v22.x
npm -v             # 10.x+
ruby -v            # ruby 3.4.x
rails -v           # Rails 8.1.x
```
