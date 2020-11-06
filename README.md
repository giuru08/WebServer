# Spiegazione Server web
## Rucco Giulio

### Spiegazione 
Si accede alla macchina virtuale e si scarica openss-server facendo il comando sudo apt install openssh-server, dopo questo si accede alla cartella /etc/netplan e si configura la rete attraverso la scrittura dei vari ip e gateway sul file 00-yaml. Configurato il nostro ip lo attiviamo con netplan try e poi lo salviamo con netplan apply. Fatto questo mettiamo l'hardware della nostra macchina virtuale la spostiamo in bridge in modo da potersi collegare al nostro pc e fare un ponte di connessione, fatto ciò scarichiamo apache2. Installato apache2 accediamo alle sue directory e creiamo due nuovi file in server-available folder, dopo averli creati e cambiati in modo da renderli idonei al uso. Quindi li attiviamo con il comando a2ensite <nome file> e inviando ci verrrà richiesto di riavviare con un comando apache2, seguite le istruzioni riportate e riavviate apache2.sito
