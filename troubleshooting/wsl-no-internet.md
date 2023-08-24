# WSL no conecta a internet

Si la conexión a internet de WSL empieza a fallar reiniciar el adaptador de Ethernet de WSL, ejecutando en una ventana de `powershell` con privilegios de admin los siguientes comandos como se explica en [este artículo](https://winaero.com/disable-network-adapter-windows-10/).

Liste las interfaces de red disponibles

~~~powershell
netsh interface show interface
~~~

Deshabilite la interface de red de WSL

> Para el caso del ejemplo la interfaz se llama *"vEthernet (WSL)"* en caso que lo vea necesario, reemplace el nombre por el que corresponda segun los resultados del comando anterior

~~~powershell
netsh interface set interface "vEthernet (WSL)" disable
~~~

Habilite nuevamente la interfaz

> Para el caso del ejemplo la interfaz se llama *"vEthernet (WSL)"* en caso que lo vea necesario, reemplace el nombre por el que corresponda segun los resultados del comando anterior

~~~powershell
netsh interface set interface "vEthernet (WSL)" enable
~~~

Pruebe la conexión a internet enviando un `ping` a google.com desde una instancia de la `terminal de linux`

~~~bash
ping google.com
~~~

## Enlaces

- [Instalación y configuración de WSL en Windows](../README.md)
- [Instalar y configurar una máquina Linux](../steps/install-linux.md)
