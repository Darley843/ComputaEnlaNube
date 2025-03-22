# configuracion subir y descargar archivos en github con vagrant

# README - Configuraci√≥n y Uso de Vagrant en PowerShell

Este documento explica los comandos utilizados para configurar y administrar entornos virtuales con Vagrant en PowerShell.

## Instalaci√≥n y Configuraci√≥n

1. **Instalar VirtualBox**
   - Descarga e instala VirtualBox desde [www.virtualbox.org](https://www.virtualbox.org)

2. **Instalar Vagrant**
   - Descarga e instala la √∫ltima versi√≥n de Vagrant desde [releases.hashicorp.com/vagrant](https://releases.hashicorp.com/vagrant/)

3. **Verificar la versi√≥n de Vagrant**
   ```powershell
   vagrant --version
   ```

4. **Instalar el plugin vbguest para VirtualBox**
   ```powershell
   vagrant plugin install vagrant-vbguest
   ```

## Creaci√≥n del Entorno Virtualizado

5. **Inicializar un directorio para Vagrant**
   ```powershell
   vagrant init
   ```
   Esto crea un archivo `Vagrantfile` en el directorio actual, donde se define la configuraci√≥n de las m√°quinas virtuales.

6. **Modificar el Vagrantfile**
   Ajustar el `Vagrantfile` para definir las m√°quinas "clienteUbuntu" y "servidorUbuntu":
   
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

7. **Levantar las m√°quinas virtuales**
   ```powershell
   vagrant up
   ```
   Esto inicia y provisiona las m√°quinas virtuales seg√∫n la configuraci√≥n definida en `Vagrantfile`.

8. **Verificar el estado de las m√°quinas virtuales**
   ```powershell
   vagrant status
   ```

## Acceso y Configuraci√≥n de las M√°quinas Virtuales

9. **Acceder a la m√°quina "servidorUbuntu"**
   ```powershell
   vagrant ssh servidorUbuntu
   ```

10. **Acceder a la m√°quina "clienteUbuntu"**
    ```powershell
    vagrant ssh clienteUbuntu
    ```

11. **Actualizar paquetes e instalar herramientas en "servidorUbuntu"**
    ```bash
    sudo apt update && sudo apt install net-tools vim git -y
    ```

12. **Confirmar la configuraci√≥n de red y conectividad**
    ```bash
    ifconfig
    ping 192.168.100.2  # Desde servidor a cliente
    ping 192.168.100.3  # Desde cliente a servidor
    ```

## Manejo de M√°quinas Virtuales

13. **Suspender una m√°quina virtual**
    ```powershell
    vagrant suspend
    ```
    Guarda el estado de la m√°quina y la detiene.

14. **Apagar una m√°quina virtual**
    ```powershell
    vagrant halt
    ```
    Apaga la m√°quina virtual de manera segura.

15. **Eliminar una m√°quina virtual**
    ```powershell
    vagrant destroy
    ```
    Elimina la m√°quina virtual del sistema.

## Creaci√≥n y Publicaci√≥n de una Imagen de Vagrant

16. **Empaquetar la m√°quina "servidorUbuntu" en un archivo de imagen Vagrant**
    ```powershell
    vagrant package servidorUbuntu --output mynew.box
    ```

17. **Agregar la nueva imagen de Vagrant**
    ```powershell
    vagrant box add mynewbox mynew.box
    ```

18. **Publicar la imagen en Vagrant Cloud**
    1. Ir a [app.vagrantup.com/boxes/new](https://app.vagrantup.com/boxes/new)
    2. Crear una nueva versi√≥n y subir el archivo `mynew.box`.
    3. Liberar la versi√≥n para que est√© disponible p√∫blicamente.

## Uso de Git en la M√°quina "servidorUbuntu"

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

Este documento proporciona una gu√≠a b√°sica para la gesti√≥n de entornos virtuales con Vagrant en PowerShell. Para m√°s informaci√≥n, consulta la [documentaci√≥n oficial de Vagrant](https://www.vagrantup.com/docs).




ÌæØ **Lista de algunos c√≥digos √∫tiles**:
| Emoji | C√≥digo |
|--------|------------|
| Ì∫Ä | `:rocket:` |
| Ì∏É | `:smiley:` |
| ‚úÖ | `:white_check_mark:` |
| Ì¥• | `:fire:` |
| Ì≥¶ | `:package:` |
| Ì≥å | `:pushpin:` |
| Ì±§ | `:bust_in_silhouette:` |

Ì¥é **Puedes ver la lista completa de emojis de GitHub aqu√≠**:  
Ì±â [https://gist.github.com/rxaviers/7360908](https://gist.github.com/rxaviers/7360908)

---

### Ì¥π **Opci√≥n 2: Copiar y pegar emojis directamente**
Tambi√©n puedes copiar y pegar emojis desde cualquier p√°gina o teclado emoji.

Ì≥å **Ejemplo en `README.md`**:
```md
# Ì∫Ä CompuNube

Ì±ã ¬°Bienvenido a CompuNube! Aqu√≠ trabajamos con **GitHub, Vagrant y computaci√≥n en la nube** ‚òÅÔ∏è.

