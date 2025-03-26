PRACTICA 1. CONFIGURACION ENTORNO MAQUINA VIRTUAL.
ESTUDIANTES.
Juan David Oviedo Rodriguez Código estudiante: 2249689
Paola Isabel Tangarife Mazo código 2249416
Mayerly Moya codigo Salinas código 2249765
Darley Idarraga Londoño código 2249688



# configuracion subir y descargar archivos en github con vagrant

# README - Configuración y Uso de Vagrant en PowerShell

Este documento explica los comandos utilizados para configurar y administrar entornos virtuales con Vagrant en PowerShell.

## Instalación y Configuración

1. **Instalar VirtualBox**
   - Descarga e instala VirtualBox desde [www.virtualbox.org](https://www.virtualbox.org)

2. **Instalar Vagrant**
   - Descarga e instala la última versión de Vagrant desde [releases.hashicorp.com/vagrant](https://releases.hashicorp.com/vagrant/)

3. **Verificar la versión de Vagrant**
   ```powershell
   vagrant --version
   ```

4. **Instalar el plugin vbguest para VirtualBox**
   ```powershell
   vagrant plugin install vagrant-vbguest
   ```

## Creación del Entorno Virtualizado

5. **Inicializar un directorio para Vagrant**
   ```powershell
   vagrant init
   ```
   Esto crea un archivo `Vagrantfile` en el directorio actual, donde se define la configuración de las máquinas virtuales.

6. **Modificar el Vagrantfile**
   Ajustar el `Vagrantfile` para definir las máquinas "clienteUbuntu" y "servidorUbuntu":
   
   ```ruby
   Vagrant.configure("2") do |config|
     if Vagrant.has_plugin? "vagrant-vbguest"
       config.vbguest.no_install  = true
       config.vbguest.auto_update = false
       config.vbguest.no_remote   = true
     end
     config.vm.define :clienteUbuntu do |clienteUbuntu|
       clienteUbuntu.vm.box = "bento/ubuntu-20.04"
       clienteUbuntu.vm.network :private_network, ip: "192.168.100.2"
       clienteUbuntu.vm.hostname = "clienteUbuntu"
     end
     config.vm.define :servidorUbuntu do |servidorUbuntu|
       servidorUbuntu.vm.box = "bento/ubuntu-20.04"
       servidorUbuntu.vm.network :private_network, ip: "192.168.100.3"
       servidorUbuntu.vm.hostname = "servidorUbuntu"
     end
   end
   ```

7. **Levantar las máquinas virtuales**
   ```powershell
   vagrant up
   ```
   Esto inicia y provisiona las máquinas virtuales según la configuración definida en `Vagrantfile`.

8. **Verificar el estado de las máquinas virtuales**
   ```powershell
   vagrant status
   ```

## Acceso y Configuración de las Máquinas Virtuales

9. **Acceder a la máquina "servidorUbuntu"**
   ```powershell
   vagrant ssh servidorUbuntu
   ```

10. **Acceder a la máquina "clienteUbuntu"**
    ```powershell
    vagrant ssh clienteUbuntu
    ```

11. **Actualizar paquetes e instalar herramientas en "servidorUbuntu"**
    ```bash
    sudo apt update && sudo apt install net-tools vim git -y
    ```

12. **Confirmar la configuración de red y conectividad**
    ```bash
    ifconfig
    ping 192.168.100.2  # Desde servidor a cliente
    ping 192.168.100.3  # Desde cliente a servidor
    ```

## Manejo de Máquinas Virtuales

13. **Suspender una máquina virtual**
    ```powershell
    vagrant suspend
    ```
    Guarda el estado de la máquina y la detiene.

14. **Apagar una máquina virtual**
    ```powershell
    vagrant halt
    ```
    Apaga la máquina virtual de manera segura.

15. **Eliminar una máquina virtual**
    ```powershell
    vagrant destroy
    ```
    Elimina la máquina virtual del sistema.

## Creación y Publicación de una Imagen de Vagrant

16. **Empaquetar la máquina "servidorUbuntu" en un archivo de imagen Vagrant**
    ```powershell
    vagrant package servidorUbuntu --output mynew.box
    ```

17. **Agregar la nueva imagen de Vagrant**
    ```powershell
    vagrant box add mynewbox mynew.box
    ```

18. **Publicar la imagen en Vagrant Cloud**
    1. Ir a [app.vagrantup.com/boxes/new](https://app.vagrantup.com/boxes/new)
    2. Crear una nueva versión y subir el archivo `mynew.box`.
    3. Liberar la versión para que esté disponible públicamente.

## Uso de Git en la Máquina "servidorUbuntu"

19. **Configurar Git**
    ```bash
    git config --global user.name "Tu Nombre"
    git config --global user.email "tuemail@example.com"
    ```

20. **Clonar un repositorio desde GitHub**
    ```bash
    git clone https://github.com/usuario/repositorio.git
    ```

21. **Subir cambios a GitHub**
    ```bash
    git add .
    git commit -m "Primer commit"
    git push origin main
    ```

---

Este documento proporciona una guía básica para la gestión de entornos virtuales con Vagrant en PowerShell. Para más información, consulta la [documentación oficial de Vagrant](https://www.vagrantup.com/docs).




��� **Lista de algunos códigos útiles**:
| Emoji | Código |
|--------|------------|
| ��� | `:rocket:` |
| ��� | `:smiley:` |
| ✅ | `:white_check_mark:` |
| ��� | `:fire:` |
| ��� | `:package:` |
| ��� | `:pushpin:` |
| ��� | `:bust_in_silhouette:` |

��� **Puedes ver la lista completa de emojis de GitHub aquí**:  
��� [https://gist.github.com/rxaviers/7360908](https://gist.github.com/rxaviers/7360908)

---

### ��� **Opción 2: Copiar y pegar emojis directamente**
También puedes copiar y pegar emojis desde cualquier página o teclado emoji.

��� **Ejemplo en `README.md`**:
```md
# ��� CompuNube

��� ¡Bienvenido a CompuNube! Aquí trabajamos con **GitHub, Vagrant y computación en la nube** ☁️.

