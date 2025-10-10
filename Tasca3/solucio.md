Iniciem Maquina virtual i la añadim.

<img width="411" height="289" alt="2025-10-10 17_36_57-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/44a1e400-b4a5-4777-b95e-8643c3b6a085" />

<img width="292" height="320" alt="2025-10-10 17_37_16-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/db397d2c-c500-497c-a8e9-6522ba0fc311" />

Al entrar mantenim SHIFT i qualsevol altre tecla

<img width="539" height="401" alt="2025-10-10 17_37_30-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/826879d5-cf11-4f3a-a119-897df62f4847" />


Un cop iniciat ens entra al menu de recuperació:
<img width="422" height="233" alt="2025-10-10 17_37_43-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/186cf21c-afb8-405e-98a1-b38ed1fa2d4c" />
<img width="412" height="131" alt="2025-10-10 17_37_53-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/14a9b1bd-2e06-46f1-8943-da6bd3e3e2e5" />
I li donem a root per entrar com admin
Posem una comanda la cual no dona resposta.
<img width="344" height="17" alt="2025-10-10 17_38_03-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/3f47bc51-3697-4da9-847b-c42de9175c6d" />
I ara amb la comanda (paswd usuari)

<img width="537" height="128" alt="2025-10-10 17_38_14-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/4a97271f-9536-44ff-9734-97fd18d4816d" />


Ara ya podem entrar al usuari del miquel

<img width="540" height="484" alt="2025-10-10 17_38_27-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/913380e5-62ef-494b-9313-8b79d5412705" />

fem un sudo -i
<img width="540" height="294" alt="2025-10-10 17_38_39-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/87ac093a-dbdc-453b-a50e-c5a8c7bdbd1d" />

Entrem a la terminal y possem sudo nano /etc/grub.d/40_custom i
<img width="538" height="133" alt="2025-10-10 17_38_52-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/ddc6e0f4-0ed1-4503-99fb-59606f125fe3" />

Afegeix al final del fitxer:
set superusers="admin"
password_pbkdf2 admin grub.pbkdf2.sha512.10000.[...]
<img width="543" height="148" alt="2025-10-10 17_39_02-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/d31eb0fc-276b-428e-9230-47fe2ffd577b" />

Hem de editar el fitxer /etc/default/grub per afegir o modificar aquestes línies:
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=5
GRUB_DISABLE_RECOVERY=true

<img width="537" height="310" alt="2025-10-10 17_39_10-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/d1a6bcfc-6787-47b8-a2a6-8f432a5f649e" />


Reinicia la màquina:
sudo reboot
I apretar shift+d
Quan vegis el menú del GRUB (on pots triar Zorin o altres opcions):
Selecciona la línia que diu:
 "Zorin OS" o "Advanced options for Zorin"

<img width="306" height="234" alt="2025-10-10 17_39_20-Desktop - Explorador de fitxers" src="https://github.com/user-attachments/assets/7418ae1c-30a8-4ae0-b90d-a1e12cd58a4e" />


Prem la tecla e (edit)
Si la protecció està ben configurada, veuràs una pantalla que demana:
Enter username:







I ja haurem acabat amb el reforçament de seguretat

