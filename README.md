# macOS_AMD
Como instalar macOS 15 en VMware Workstation Pro 17

Instalar Python3: https://www.python.org/downloads/

Instalar Qemu:  https://qemu.weilnetz.de/w64/

Instalar VMware workstation Pro:   https://support.broadcom.com/group/ecx/downloads

Descargar OC4VM:  https://github.com/DrDonk/OC4VM/releases

Descargar OpenCorePkg:  https://github.com/acidanthera/OpenCorePkg/releases

# Descomprimir OC4VM y OpenCorePkg

ir a la carpeta OpenCore-1.0.5-RELEASE\Utilities\macrecovery

Para bajar BaseSystem.dmg para Sequoia ejecutar:  

py macrecovery.py -b Mac-937A206F2EE63C01 -m 00000000000000000 download

ir a la carpeta com.apple.recovery.boot

Convertir BaseSystem.dmg a BaseSystem.vmdk:  C

:\"Program Files"\qemu\qemu-img.exe convert -O vmdk -o compat6 BaseSystem.dmg BaseSystem.vmdk

ir a la carpeta \macOS guest\oc4vm-1.1.1\vmware

copiar la carpeta AMD o Intel a la carpeta VM de virtual machines y cambiar el nombre a "macOS"

copiar BaseSystem.vmdk a la carpeta macOS

Iniciar VMWare 17

Presionar FILE, New

Presionar Editar Configuracion de VM

Cambiar la memoria y los procesadores de ser necesario

Agregar un nuevo disco, sata, desde archivo, seleccionar BaseSystem.vmdk, seleccionar Keep 
Existing Format

Iniciar la VM

Seleccionar Idioma

Si se cambio el tamaño del disco, seleccionar DISK UTILITY y formatear

Seleccionar Reinstalar macOS Sequoia

Seleccionar Continuar

Seleccionar Macintosh HD

Iniciará la descarga por internet de los archivos necesarios, luego los descomprimirá, esto puede llevar HORAS.

Chequear la pantalla de bloqueo para que NO se SUSPENDA el equipo!.

cd /Volumes/OPENCORE/OC4VM/iso

ejecutar: darwin.iso

pedirá autorización, seleccionar "Open System Settings", en la lista casi al final seleccionar ALLOW

volver a presionar OK

volver a ejecutar darwin.iso

Install VMware Tools

No Reiniciar

# Para reparar el Apple ID:

Abrir Terminal

cd /Volumes/OPENCORE/OC4VM/Tools

./vmhide -on

REINICIAR

# Para reparar los virtual CPU en AMD, el 4 es el número de cores

Abrir Terminal

cd /Volumes/OPENCORE/OC4VM/Tools

./amdcpu 4


# Para cambiar la resolución de pantalla en el VM:  

Abrir Terminal

sudo /Library/Application\ Support/VMware\ Tools/vmware-resolutionSet 1280 800

# Otros

Lista de versiones de macOS para descargar

https://dortania.github.io/OpenCore-Install-Guide/installer-guide/windows-install.html#downloading-macos
