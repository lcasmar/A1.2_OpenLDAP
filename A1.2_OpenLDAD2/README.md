# LDAP Account Manager e phpLDAPAdmin

#### Índice
- OpenLDAPManager
- phpLDAPAdmin 

## OpenLDAPManager
### Instalación de paquetes
Instalamos los siguientes paquetes:
- apache2
- php
- php-cgi
- libapache2-mod-php
- php-mbstring
- php-common
- php-pear

![](img/Inst_1.png)

Activamos cgi tras comprobar la version de php y arrancamos apache2  
![](img/inst_2.png)

Instalamos ldap_accountmanager  
![](img/inst_3.png)

### Configuración ldapAccountManager
Desde el archivo /etc/apache2/ldap-account-manager.conf vamos a indicar al servidor quien puede conectarse a LDAPmanager, en este caso vamos a darle permiso a cualquier equipo que se encuentre en la red 192.168.11.0/24  
![](img/inst_4.png)  
Reiniciamos el servicio apache    
![](img/inst_5.png)  

Comprobamos que podemos acceder al servidor desde el cliente  
![](img/inst_6.png)

Ahora vamos a configurar para poder conectarnos al server desde el host.  
Comprobamos la ip de host con ipconfig 
![](img/inst_7.png)

Reconfiguramos el archivo /etc/apache2/ldap-account-manager.conf  
![](img/inst_8.png)  

Reiniciamos el servicio apache    
![](img/inst_5.png)  

Comprobamos la ip con la que el servidor sale a la red externa  
![](img/inst_9.png)  

Accedemos al servidor desde el host  
![](img/inst_10.png)

Vamos a editar las configuraciones generales, para ello seguimos la ruta LAM configuration> Edit General Settings y añadimos contraseña maestra por defecto que es *lam*  
![](img/inst_11s.png)

Cambiamos la contraseña por defecto  
![](img/inst_12.png)

Antes de entrar vamos a continuar configurando el servidor, seguimos la ruta seguimos la ruta LAM configuration> Edit General Server Profiles , configuramos el idioma por defecto y añadimos nuestro dominio  
![](img/inst_15.png)  
![](img/inst_14.png)  

Cambiamos también la contraseña  
![](img/inst_16.png)  

Accedemos a la pestaña *Tipos de cuentas* y modificamos  
![](img/inst_17.png)

Accedemos a nuestro servidor ldap  
![](img/inst_13.png)

Comprobamos como se muestran todos los usuarios y grupos generados en la anterior práctica  
![](img/inst_18.png)
![](img/inst_19.png)  

### Eliminación de infraestructura anterior

Eliminamos todos los usuarios y grupos eliminando la unidad organizativa raíz, en nuestro caso ou=AntonLosadaDieguez  
![](img/del_3.png)  

### Creación de una nueva infraestructura
Creamos las nuevas unidades organizativas desde el entorno gráfico 
La unidad organizativa padre *AntonLosadaDieguez*
![](img/crea_1.png)  
Las unidades organizativas *Alumnos*,*Profesores*,*Otros* y *LDAPAdmin*  
![](img/crea_2.png)![](img/crea_3.png)![](img/crea_4.png)![](img/crea_5.png)  

Creamos los grupos correspondientes a cada unidad organizativa, el objetivo de los grupos es facilitar la gestión de permisos  
![](img/crea_g1.png)  
![](img/crea_g2.png)

Creamos los usuarios para cada grupo  
![](img/crea_u1.png)  
![](img/crea_u2.png)


## phpLDAPAdmin
Instalamos el aplicativo en el servidor *lcmUbuntuServer*  
![](img/2inst_1.png)   
Configuramos el archivo config de phpldapadmin  
![](img/2inst_1.5.png)  
Comprobamos como desde un navegador en el cliente podemos acceder al servidor a través de la dirección *http://192.168.11.1/phpldapadmin/*
![](img/2inst_2.png)  
Eliminamos la estructura creada en el ejercicio anterior eliminado la uo principal *AntonLosadaDieguez*, al estar el resto de elementos colgando de la UO principal ya se eliminan por defecto  
![](img/2del_1.png)  
![](img/2del_2.png)

Creamos una nuevo infraestructura empezando por las UO  
![](img/2crea_uo3.png)  
Una vez creada la UO padre procedemos a crear las hijas  
![](img/2crea_ou4.png)  
![](img/2crea_uo1.png) 

Ahora creamos los grupos dentro de cada uo, empezando por el grupo alumnos dentro de la uo Alumnos  
![](img/2crea_g1.png)  
![](img/2crea_g2.png)  
![](img/2crea_g3.png)  

Creamos un grupo para cada UO  
![](img/2crea_g4.png)  

Para poder añadir usuarios a los grupos debemos añadir un atributo a los grupos *memberUID* a través del cual conectaremos grupos y usuarios  
![](img/2une_gu1.png)  
Ahora procedemos a crear los usuarios  
![](img/2crea_usu1.png)  
![](img/2crea_usu2.png)  
![](img/2crea_usu3.png) 

Una vez tenemos toda la infraestructura creada queda tal que así  
![](img/2crea_usu4.png)  


