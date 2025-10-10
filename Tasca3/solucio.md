# **T03: Seguretat Lògica: recuperant accés a sistemes**

| Breu descripció | Després de la primera feina exitosa, us arriba un encàrrec urgent que obliga a que us hi poseu per donar-li solució. Com a fase prèvia rebreu una formació sobre la seguretat lògica que us permetrà tenir els coneixements necessaris per afrontar la tasca. Han arribat a la consultora un equip provinent d’un client que demana que els hi solucionem el problema. Tenen un portàtil amb Zorin OS (un Linux amb entorn gràfic) que usava habitualment un directiu. El problema és que ha oblidat la contrasenya i és necessari poder recuperar l’accés perquè hi ha documentació molt important que cal recuperar. Per evitar que una acció catastròfica pugui danyar l’equip original, ens han clonat el disc en un disc virtual perquè hi treballeu. ![][image1] Per tant, el primer pas serà crear una màquina virtual al que connectareu aquest disc. A continuació, cal que entreu a la màquina virtual, trobeu el nom de l’usuari existent i assigneu-li una contrasenya nova. Quan el client és informat del senzill que és accedir a l’equip, demana si n’hi ha alguna manera de fortificar el sistema, ja que té por que si algú roba el portàtil hi pugui accedir a la informació que hi conté. Per tant, ara ens demanen que cerquem solucions per tal d’evitar que es pugui reiniciar la contrasenya amb el procediment anterior.  Investigueu el procediment per tal que l’accés al GRUB quedi protegit per contrasenya per evitar canvis de configuració. Procediment individual Vulnereu l’accés al GRUB del Linux. Identifiqueu l’usuari del sistema. Modifiqueu la contrasenya de l’usuari i verifiqueu que ara ja té accés. Investigueu com es pot fortificar l’accés al GRUB. És molt important que indiquis les fonts d’informació que usis. Configura la màquina virtual per tal de fortificar l’accés al GRUB Documenteu el procediment en un document (cal incloure imatges) per posteriorment pujar-lo al vostre repositori. Material de suport Disc virtual. Apunts RA1AA4 Seguretat Lògica Recuperant Password en Linux:[https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/](https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/)  |
| :---- | ----- |

Iniciem Maquina virtual i la añadim.

Al entrar mantenim SHIFT i qualsevol altre tecla  
![][image2]  
Un cop iniciat ens entra al menu de recuperació:  
![][image3]  
![][image4]  
I li donem a root per entrar com admin  
Posem una comanda la cual no dona resposta.  
![][image5]  
I ara amb la comanda (paswd usuari)  
![][image6]

![][image7]  
Ara ya podem entrar al usuari del miquel

![][image8]  
fem un sudo \-i

Entrem a la terminal y possem sudo nano /etc/grub.d/40\_custom i

![][image9]

Afegeix al final del fitxer:

`set superusers="admin"`  
`password_pbkdf2 admin grub.pbkdf2.sha512.10000.[...]`

![][image10]

Hem de editar el fitxer `/etc/default/grub` per afegir o modificar aquestes línies:

`GRUB_TIMEOUT_STYLE=hidden`  
`GRUB_TIMEOUT=5`  
`GRUB_DISABLE_RECOVERY=true`

![][image11]

Reinicia la màquina:

`sudo reboot`  
I apretar shift+d  
Quan vegis el menú del GRUB (on pots triar Zorin o altres opcions):

1. Selecciona la línia que diu:  
    **"Zorin OS"** o **"Advanced options for Zorin"**

2. Prem la tecla **`e`** (edit)

Si la protecció està ben configurada, **veuràs una pantalla que demana**:

`Enter username:`

I ja haurem acabat amb el reforçament de seguretat
