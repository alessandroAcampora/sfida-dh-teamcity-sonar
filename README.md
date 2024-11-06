# Configurazione Completa di WSL2 e Docker su Windows
Questa guida copre l'installazione di WSL2, Docker e Docker Compose su Windows e spiega come avviare un'applicazione con Docker Compose.

## 1. Installazione di WSL2
Prima di tutto, avviare il command prompt come Amministratore (oppure Powershell) e digitare:
```powershell
wsl --install
```
Oppure:
```powershell
wsl --install -d <NomeDellaVersione>
```
## 2. Installazione Docker Engine sotto WSL2
Successivamente, installiamo Docker Engine, che è il componente principale che esegue i container Docker. 
I due blocchi di comandi seguenti aggiungeranno prima il repository apt di Docker e poi installeranno Docker. Puoi eseguirli direttamente nel terminale WSL2.
```powershell
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
Ora che Docker è installato, verifichiamo che funzioni correttamente. Il comando seguente scaricherà ed eseguirà il container hello-world. Se l'installazione è andata a buon fine, dovrebbe apparire un messaggio di conferma e poi il container si chiuderà automaticamente.
```powershell
sudo docker run hello-world
```
Per impostazione predefinita, è necessario utilizzare sudo con i comandi Docker per ottenere permessi elevati. Per eseguire Docker senza sudo, puoi creare un gruppo chiamato docker per gli utenti Docker e aggiungere il tuo utente corrente a quel gruppo.




