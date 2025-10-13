T03: Seguretat Lògica: recuperant accés a sistemes
Breu descripció
Després de la primera feina exitosa, us arriba un encàrrec urgent que obliga a que us hi poseu per donar-li solució.
Com a fase prèvia rebreu una formació sobre la seguretat lògica que us permetrà tenir els coneixements necessaris per afrontar la tasca.
Han arribat a la consultora un equip provinent d’un client que demana que els hi solucionem el problema.
Tenen un portàtil amb Zorin OS (un Linux amb entorn gràfic) que usava habitualment un directiu. El problema és que ha oblidat la contrasenya i és necessari poder recuperar l’accés perquè hi ha documentació molt important que cal recuperar. Per evitar que una acció catastròfica pugui danyar l’equip original, ens han clonat el disc en un disc virtual perquè hi treballeu.

<img width="170" height="240" alt="imagen2" src="https://github.com/user-attachments/assets/cea2a380-f115-4144-8dab-15e6da57fc90" />

Per tant, el primer pas serà crear una màquina virtual al que connectareu aquest disc. A continuació, cal que entreu a la màquina virtual, trobeu el nom de l’usuari existent i assigneu-li una contrasenya nova.
Quan el client és informat del senzill que és accedir a l’equip, demana si n’hi ha alguna manera de fortificar el sistema, ja que té por que si algú roba el portàtil hi pugui accedir a la informació que hi conté. Per tant, ara ens demanen que cerquem solucions per tal d’evitar que es pugui reiniciar la contrasenya amb el procediment anterior. 
Investigueu el procediment per tal que l’accés al GRUB quedi protegit per contrasenya per evitar canvis de configuració.
Procediment individual
Vulnereu l’accés al GRUB del Linux.
Identifiqueu l’usuari del sistema.
Modifiqueu la contrasenya de l’usuari i verifiqueu que ara ja té accés.
Investigueu com es pot fortificar l’accés al GRUB. És molt important que indiquis les fonts d’informació que usis.
Configura la màquina virtual per tal de fortificar l’accés al GRUB
Documenteu el procediment en un document (cal incloure imatges) per posteriorment pujar-lo al vostre repositori.
Material de suport
Disc virtual.
Apunts RA1AA4 Seguretat Lògica
Recuperant Password en Linux:
https://waytoit.wordpress.com/2013/06/06/recuperando-password-en-ubuntu/


RESPOSTA




🔒 Reforçament de seguretat del GRUB i recuperació d'accés d'usuari**

🖥️ 1. Iniciem la màquina virtual**

Arrenca la màquina virtual.

Mantén premuda la tecla SHIFT (i alguna altra tecla si cal) durant l’inici.

Això et portarà al menú de GRUB 🧰.

-
<img width="411" height="289" alt="2025-10-10 17_36_57-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/44a1e400-b4a5-4777-b95e-8643c3b6a085" />

<img width="292" height="320" alt="2025-10-10 17_37_16-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/db397d2c-c500-497c-a8e9-6522ba0fc311" />

Al entrar mantenim SHIFT i qualsevol altre tecla

<img width="539" height="401" alt="2025-10-10 17_37_30-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/826879d5-cf11-4f3a-a119-897df62f4847" />
-





🔃 2. Entra al mode de recuperació

Un cop dins el GRUB, selecciona la opció de recuperació (recovery mode).

A la següent pantalla, selecciona:
🔹 root - Drop to root shell prompt
Per entrar com a usuari root 🧑‍💻.

-
<img width="422" height="233" alt="2025-10-10 17_37_43-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/186cf21c-afb8-405e-98a1-b38ed1fa2d4c" />

<img width="412" height="131" alt="2025-10-10 17_37_53-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/14a9b1bd-2e06-46f1-8943-da6bd3e3e2e5" />

I li donem a root per entrar com admin
Posem una comanda la cual no dona resposta.

<img width="344" height="17" alt="2025-10-10 17_38_03-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/3f47bc51-3697-4da9-847b-c42de9175c6d" />

I ara amb la comanda (paswd usuari)

<img width="537" height="128" alt="2025-10-10 17_38_14-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/4a97271f-9536-44ff-9734-97fd18d4816d" />
-




🔐 3. Restablir la contrasenya d’un usuari

Ara pots escriure la següent comanda:

passwd miquel


Introdueix la nova contrasenya per l’usuari miquel.

✅ Ara ja pots iniciar sessió amb aquest usuari.
-

<img width="540" height="484" alt="2025-10-10 17_38_27-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/913380e5-62ef-494b-9313-8b79d5412705" />




⚙️ 4. Aconseguir permisos de superusuari

Un cop dins amb el compte miquel, obre una terminal i escriu:

sudo -i


🔓 Això et donarà accés com a root dins la sessió.
-
<img width="540" height="294" alt="2025-10-10 17_38_39-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/87ac093a-dbdc-453b-a50e-c5a8c7bdbd1d" />

Entrem a la terminal y possem sudo nano /etc/grub.d/40_custom i

<img width="538" height="133" alt="2025-10-10 17_38_52-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/ddc6e0f4-0ed1-4503-99fb-59606f125fe3" />





-
📝 5. Configura un usuari i contrasenya per protegir el GRUB

Edita el fitxer de configuració personalitzada del GRUB:

sudo nano /etc/grub.d/40_custom


Afageix al final del fitxer aquesta línia:

set superusers="admin"
password_pbkdf2 admin grub.pbkdf2.sha512.10000.[...]


📌 Substitueix la part del hash per la teva contrasenya generada amb grub-mkpasswd-pbkdf2 si cal.
-
<img width="543" height="148" alt="2025-10-10 17_39_02-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/d31eb0fc-276b-428e-9230-47fe2ffd577b" />





-
🛠️ 6. Edita configuració general del GRUB

Ara edita el fitxer:

sudo nano /etc/default/grub


Assegura’t que conté aquestes línies (o modifica-les):

GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_DISABLE_RECOVERY=true


🔧 Això farà que el GRUB sigui més ràpid i segur.
-
<img width="537" height="310" alt="2025-10-10 17_39_10-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/d1a6bcfc-6787-47b8-a2a6-8f432a5f649e" />






🔄 7. Reinicia la màquina i prova la protecció

Reinicia:

sudo reboot


🔁 Durant l’arrencada:

Prem SHIFT + D per veure el menú del GRUB.

Selecciona: Zorin OS o Advanced options for Zorin.
-
<img width="306" height="234" alt="2025-10-10 17_39_20-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/7418ae1c-30a8-4ae0-b90d-a1e12cd58a4e" />

-
Prem SHIFT + D per veure el menú del GRUB.

Selecciona: Zorin OS o Advanced options for Zorin.

Prem la tecla e per editar.

🔐 Ara, si tot està correcte, apareixerà:

Enter username:

✅ La protecció del GRUB està activada i funcional!




I ja haurem acabat amb el reforçament de seguretat
-
