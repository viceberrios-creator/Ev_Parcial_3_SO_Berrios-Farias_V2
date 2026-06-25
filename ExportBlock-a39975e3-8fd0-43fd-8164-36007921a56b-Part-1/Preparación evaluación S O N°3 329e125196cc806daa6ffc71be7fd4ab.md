# Preparación evaluación S.O N°3

Docente : Jorge Ramirez 

Integrantes:

- Diego Farias
- Vicente Berríos

SISTEMAS OPERATIVOS CORPORATIVOS_001D

# LINUX

•  **Cree un servidor virtual Linux con 2 Vcpu y 4 GB de RAM.** 

Buscamos el tipo de instancia amazon linux y elegimos  “T3.Medium” que es la que cumple con 2Vcpu y 4GB de ram

![image.png](image.png)

- **Configure los security group respectivos, de forma que les permita acceso a los servicios SSH y HTTP, en los comentarios de conexión utilice su nombre y apellido.**

Habilitamos protocolos ssh y http para permitir la conexión remota y dejamos como descripción mi nombre y apellido

![image.png](image%201.png)

- **IP publica de la instancia**

Identificamos la ip pública: 3.94.196.141

![image.png](image%202.png)

- **Nombre de DNS de la instancia**

Identificamos el dns bajo el nombre de http://ec2-3-94-196-141.compute-1.amazonaws.com/

![image.png](image%203.png)

- **Cree la llave de conexión con su apellido.**

Creamos la clave para luego acceder por ssh

![image.png](image%204.png)

**Conéctese al server a través del cliente ssh (Putty u otro).**

Nos conectamos con ssh a linux desde el sistema windows usando powershell

![image.png](image%205.png)

- **Instale el servicio httpd**

Instalamos el servicio httpd (apache) con los siguientes comandos:

sudo dnf install httpd -y 

![image.png](image%206.png)

- **A través de comandos, verifique el estado en el que se encuentra HTTP en el servidor e inícielo.**

Verificamos e iniciamos el servicio con los comandos:

sudo systemctl start httpd // sudo systemctl status httpd

![image.png](image%207.png)

- **A través de comandos, modifique la página de bienvenida del sitio utilizando una página donde aparezca su nombre y el logo de Duoc UC, este archivo debe estar en el servidor, no un enlace a otro sitio con la imagen.**

Modificamos el sitio web html, agregamos nuestros nombres y copiamos la dirección de la imagen del logo de Duoc UC

![image.png](image%208.png)

- **Compruebe el funcionamiento del sitio WEB creado a través de su navegador.**

Luego en nuestro navegador buscamos el sitio web por la ip pública de la instancia o por el nombre que le asignó DNS

![image.png](image%209.png)

- **En el panel de administración de AWS Detenga la instancia Linux Creada.**

Y por último detenemos la instancia

![image.png](image%2010.png)

Y por para finalizar, en esta última foto verificamos que la instancia creada aparece como “detenida”

![image.png](image%2011.png)

# WINDOWS

1- Creacion de windows server 2019 con GUI

![Eleccion de AMI y tipo instancia.png](Eleccion_de_AMI_y_tipo_instancia.png)

- En  la imagen se observa la eleccion de AMI , que en este caso es “Microsoft Windows Server 2019 Base” , ademas del tipo de instancia que es t3.small.

2- Creacion de los security  groups , permitiendo el acceso a los servicios de RDP , HTTP y FTP.

![creacion de sg y rdp.png](creacion_de_sg_y_rdp.png)

- Se observa la creación del grupo de seguridad llamado “SG-Windows-RDP-HTPP” , y con su respectiva descripción como se pide (nombre, apellido). Y en la imagen de abajo se observa los SG correspondientes a HTTP y FTP.

![http y ftp.png](http_y_ftp.png)

3- IP publica de la instancia y DNS

- A continuación en la imagen se observa lo que viene a ser la IP publica de la instancia ademas de tambien el DNS publico.
    
    ![ip publica y dns.png](ip_publica_y_dns.png)
    

4-Creacion de la llave privada

- Se creo la llave privada guardándola como “Berrios.pem”
    
    ![Creacion para de llaves.png](Creacion_para_de_llaves.png)
    
    ![Captura de pantalla 2026-06-25 172628.png](Captura_de_pantalla_2026-06-25_172628.png)
    

5- Conexión por RDP con la instancia de Windows server

- En las imágenes a continuación podremos ver como es la conexión mediante escritorio remoto hacia la instancia de win server , esto mediante el DNS publico, usuario Administrator y la contraseña que se obtuvo al descifrar el archivo Berrios.pem.

![Conexion rdp y password.png](Conexion_rdp_y_password.png)

![conectando rdp.png](conectando_rdp.png)

6- Instalacion de IIS y el rol de HTTP+FTP

- En la imagen se observa la instalacion de IIS.

![instalacion de IIS.png](instalacion_de_IIS.png)

- Y en la imagen de abajo se ve la intalacion del rol de HTTP + FTP , y finalmente cuando se finaliza la correcta instalacion de los servicios.
    
    ![innstalacion de ftp.png](innstalacion_de_ftp.png)
    
    ![instalacion finalizada.png](instalacion_finalizada.png)
    

7- Verificacion de estado de los servicios

- A continuación revisamos con la herramienta de administración , el estado de los Servicios de HTTP y FTP.
    - HTTP
    
    ![ev servicio web.png](ev_servicio_web.png)
    
    - FTP
        
        ![ev servicio ftp.png](ev_servicio_ftp.png)
        

8- Modificación y Comprobacion de la pagina de bienvenida del sitio web.

- Se modifico el archivo index.html  , para que la pagina de bienvenida muestre el nombre de un alumno y agregándole el logo de DuocUC. La conexion se realizo a través de la IP publica de la instancia de Windows Server.
    
    ![ev server web.png](ev_server_web.png)
    

9- Funcionamiento de FTP

- Se intento verificar por navegador , pero no se logro ya que al momento de poner la dirección IP o de nombre de DNS en el navegador me redirigía hacia el navegador Explorer , y al intentar la conexión arrojaba error como se puede ver en la imagen a continuacion.
    
    ![ev ftp no nav.png](ev_ftp_no_nav.png)
    
- Pero si se pudo comprobar el funcionamiento mediante la terminal de comandos y se pudo visualizar el archivo “prueba.txt” creado en la carpeta que aloja al servicio FTP.
    
    ![ev revision ftp.png](ev_revision_ftp.png)
    

10- Finalmente en el panel de administracion de las instancias , se detuvo la instancia de Windows Server.

![instancia detenida.png](instancia_detenida.png)