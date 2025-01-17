# Redes1-Práctica1_201700886
La practicá una consiste en realizar una red de computadoras pequeña usando diversas interfaces, la 
manera en la que se comprueba que la conexión sea correcta entre los equipos es con el comando **ping** hacia una ip de algú equipo de la 
red, fue implementado en **GNS3** se utilizó la imagen **C3725** como router ademas la computadora virtualizada corre en **vmware** usando **tiny core**. 
### Componentes Utilizados
Se realizó una pequeña red con:
- 1 routers(C3725)
- 2 switch
- 3 vpc
- 1 computadora virtualizada ejecutando tiny core.
### Comandos Utilizados Y Su Funcionalidad.
- ping 
>sirve para comprobar la conexión entre 2 interfaces.
- ena
>utilizado para habilitar la cofiguración del router.
- sh int bri
>utilizado para verificar las interfaces del router.
- int fa **x/n**
>sirve para configurar la interfaz, los valores posibles se encuentran con **sh int bri**.
- full-duplex
>indica que la conexión que se manejará es de tipo full-duplex.
- speed **x**
>para indicar el valor de transferencia de la información.
- ip add **CIDR** **GATEWAY**
>sirve para configurar la dirección ip de la interfaz e indicar el valor de **GATEWAY***.
- no sthudown
>para mantener la interfaz activa
- exit
>para salir del actual menú de configuración.
- write
> para escribir los cambios de configuración en el rputer.
- save
>para guardar la configuración en un **VPC**.
### Topología Utilizada En La Red
Se conectaron 2 Switch a un router principal, cada switch estaba conectado a 2 terminales.
![Contribution guidelines for this project](Practica1/imagenes/Red.PNG)
### Configuración Individual De Cada Componente

- **Configuración De La Interfaz Del Router**
  Para configurar el router en GNS3 necesitamos activarlo y darle doble click y se abrira una consola, en la consola nceesitamos usar los siguientes comandosÑ
  - **ena**
  - **sh ip int bri** se nos mostrara la informacion de las interfaces del router
  
 ![Contribution guidelines for this project](Practica1/imagenes/CR1.PNG)
  
  - **configure terminal**
  - **int fa 0/0** para entrar a la interfaz 0/0
  - **ip add 192.168.16.254 255.255.255.0**  se coloca ip y la mascara de red para la interfaz
  - **no shutdow**
  - **exit**
  - **write** para guardar la configuracion
  
  ![Contribution guidelines for this project](Practica1/imagenes/CR2.PNG)
  
  Esa manera de configurar corresponde a los 2 switch que se conectan al router, los switch se concetan desded su puerto ethernet 0 al puerto fast ehternet del router     correspondiente,   se eligio diferente GATEWAY en cada interfaz del router para no incurrir en problemas de una dirección ip repetida

- **Configuración De Las VPC**
![Contribution guidelines for this project](Practica1/imagenes/VPC1.PNG)
![Contribution guidelines for this project](Practica1/imagenes/VPC2.PNG)

  configurar las VPC en GNS3 es bastante sencillo y rapido solo se necesitan 2 comandos, abrimos la VPC con doble click y escribimos:
  - **ip 192.168.16.30/24 192.168.16.254** con eso indicamos que la VPC tendrá la dirección ip 192.168.16.30 con mascara de subred 255.255.255.0 y que su gateway es de 192.168.16.254
  - **save** para guardar la condiguración
  - **ping 192.168.16.254** para comprobar la conección correcta al Gateway.
 ![Contribution guidelines for this project](Practica1/imagenes/VPC3.PNG)
- **Configuración De La PC Virtualizada**

  iniciamos la pc virtualizada, le damos doble click y empezará a cargar VMWARE workstation, cuando termine de cargar se debe hacer lo siguiente.
  - Click Derecho y abrimos Control Panel que está adentro de System Tools
  ![Contribution guidelines for this project](Practica1/imagenes/PC1.PNG)
  - Se abrira una ventana y se le da click en Network para abrir una nueva ventana
  ![Contribution guidelines for this project](Practica1/imagenes/PC2.PNG)
  - En esta nueva ventana se escribe la dirección ip que la maquina tendrá aplicamos los cambios y abrimos un terminal, en aplications y luego terminal.
  ![Contribution guidelines for this project](Practica1/imagenes/PC3.PNG)
  - En el terminal escribimos **ping 192.168.16.254** para comprobar que la conexión con el gateway está correcta.
  ![Contribution guidelines for this project](Practica1/imagenes/PC4.PNG)
  
### Glosario
  - **GATEWAY**: es un dispositivo que permite interconectar redes con arquitecturas y protocolos diferentes-
  - **IP**: Es la dirección que un terminal o interfaz poseé en la red.
  - **Ping**: Es un comando para identificar si se pueden enviar paquetes o recibir de otro dispositivo.
  - **Tiny Core**: Un sistema operativo linux que su principal caracteristica es su baja demanda de recursos y acceso a funciones basicas. 
  - **Save**: Palabra que se traduce en guardar, es usada como comando por las VPC para almacenar los cambios.
  - **GNS3**: Es un simulador de red.
  - **ROUTER**: tambien llamado enrutador es un dispositivo que permite la conección entre computadoras su principal función es determinar la mejor ruta de los paquetes de información-
  - **SWITCH**: Es un controlador de interconexión entre varios dispositivos.
  - **CIDR**: Es una notación para indicar cual es la dirección ip de un equipo y su mascara.
  - **FULL DUPLEX**: Modo de comunicación donde se puede enviar y recibir al mismo tiempo, los hubs no son capaces de usar este modo.
  - **HALF DUPLEX**: Modo de comunicación donde solo se puede enviar o recibir al mismo tiempo.
