# Moonin Installer

Native CLI downloads for Linux, macOS and Windows. No container runtime, source
checkout or compilation is required. The source repository remains private.

[English installation](#installation) | [Instalacion en espanol](#instalacion)

## Downloads / Descargas

| System / Sistema | Intel / AMD x86-64 | ARM64 |
| --- | --- | --- |
| Linux | [Download](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_linux_amd64.tar.gz) | [Download](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_linux_arm64.tar.gz) |
| macOS | [Intel](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_darwin_amd64.tar.gz) | [Apple Silicon](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_darwin_arm64.tar.gz) |
| Windows | [Download](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_windows_amd64.zip) | [Download](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/moonin-installer_windows_arm64.zip) |

[SHA256SUMS](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/download/preview/SHA256SUMS)
| [Preview version / Version preview](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases/tag/preview)
| [All versions / Todas las versiones](https://github.com/Moonin-Lab/Moonin-Installer-Releases/releases)

## Installation

1. Download the archive matching your workstation and its `SHA256SUMS` manifest
	into the same folder. `amd64` means Intel/AMD x86-64; `arm64` includes Apple
	Silicon. These are workstation binaries, not Kubernetes images.
2. Verify only your archive against its exact filename entry in the manifest.
	On macOS use `shasum -a 256 ARCHIVE`, on Linux `sha256sum ARCHIVE`, or on
	Windows `Get-FileHash -Algorithm SHA256 ARCHIVE`. Replace `ARCHIVE` with its
	actual filename and compare the complete hash with `SHA256SUMS`. Do not
	extract or run the file if its entry is missing or the hash differs.
3. On Linux/macOS, extract with `tar -xzf ARCHIVE.tar.gz`. Run
	`./moonin-installer version`. To install for your user:

	```bash
	mkdir -p "$HOME/.local/bin"
	install -m 0755 moonin-installer "$HOME/.local/bin/moonin-installer"
	export PATH="$HOME/.local/bin:$PATH"
	moonin-installer version
	```

	Persist that PATH in your shell configuration if required.
4. On Windows, after verifying the hash:

	```powershell
	Expand-Archive -LiteralPath .\moonin-installer_windows_amd64.zip -DestinationPath .\moonin-cli
	.\moonin-cli\moonin-installer.exe version
	.\moonin-cli\moonin-installer.exe --help
	```

	Use the `arm64` filename on ARM64. Move the executable to a permanent folder
	and add that folder to your user's PATH, then open a new terminal.
5. Follow the [Enterprise installation guide](https://docs.moonin.app/enterprise/)
	before running `moonin-installer platform install`. It covers Kubernetes,
	storage, PostgreSQL migrations, ClickHouse, identity, licensing and TLS.
	Installing this CLI alone does not configure those prerequisites.

`preview` is a rolling prerelease channel, including release candidates, not a
stable release. `stable` is updated only by non-prerelease versions and may not
exist until the first stable release. For production, use an approved versioned
release, record `moonin-installer version`, and download both archive and manifest
from that release. Rolling channels may change during downloads. Checksums
verify integrity relative to the manifest, not independent publisher authenticity.
No installer signing, notarization or high-availability certification is implied.

## Instalacion

1. Descargue el archivo correspondiente a su estacion y `SHA256SUMS` en la misma
	carpeta. `amd64` corresponde a Intel/AMD x86-64; `arm64` incluye Apple Silicon.
	Son binarios nativos para la estacion, no imagenes Kubernetes.
2. Verifique solo el archivo elegido contra la entrada de su nombre exacto en el
	manifiesto. En macOS use `shasum -a 256 ARCHIVO`, en Linux `sha256sum ARCHIVO`
	y en Windows `Get-FileHash -Algorithm SHA256 ARCHIVO`. Sustituya `ARCHIVO` por
	su nombre real y compare el hash completo con `SHA256SUMS`. Si falta la
	entrada o no coincide, no extraiga ni ejecute el archivo.
3. En Linux/macOS extraiga con `tar -xzf ARCHIVO.tar.gz` y ejecute
	`./moonin-installer version`. Instale para su usuario con los comandos de
	la seccion inglesa anterior: crean `~/.local/bin`, instalan el ejecutable y
	agregan esa carpeta al PATH de la sesion. Configure el PATH persistente en
	su shell cuando corresponda.
4. En Windows, tras verificar el hash, use los comandos PowerShell anteriores.
	Cambie `amd64` por `arm64` si corresponde. Mueva el ejecutable a una carpeta
	permanente, agreguela al PATH de usuario y abra una terminal nueva.
5. Siga la [guia Enterprise en espanol](https://docs.moonin.app/es/enterprise/)
	antes de ejecutar `moonin-installer platform install`: explica Kubernetes,
	almacenamiento, migraciones PostgreSQL, ClickHouse, identidad, licencia y
	TLS. Instalar la CLI no prepara automaticamente esos prerrequisitos.

`preview` incluye versiones candidatas y no representa una version estable.
`stable` se actualiza solo con versiones no preliminares y puede no existir
hasta la primera version estable. En produccion use una release versionada
aprobada, registre `moonin-installer version` y descargue archivo y manifiesto
de esa misma release. Los canales mutables pueden cambiar durante la descarga.
Los checksums verifican integridad respecto al manifiesto, no autenticidad
independiente. No se presupone firma, notarizacion ni certificacion HA.

The repository contains distribution documentation and release assets only.
No customer credentials, licenses, kubeconfigs or private source code belong here.
