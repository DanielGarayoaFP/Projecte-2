# Solució Tasca 3

Aquest document conté la solució a l'exercici proposat a la tasca 3.

> **Enunciat de l'exercici:**  
> Configura una connexió VPN segura entre dos equips.

## Solució

Per establir la connexió VPN s'han seguit els passos següents:

```bash
sudo apt-get install openvpn
sudo openvpn --config client.ovpn
