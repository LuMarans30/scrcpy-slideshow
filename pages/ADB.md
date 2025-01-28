# ADB: Android Debugging Bridge

ADB è un tool CLI sviluppato da Google che comunica con un dispositivo Android.

Si può dividere in tre componenti principali:
- **Daemon** - adbd, il demone di adb, è un processo che gira sul dispositivo Android
- **Server** - Il server gira sul PC sulla porta 5037, e gestisce la comunicazione tra client e demone
- **Client** - Il client gira anch'esso sul PC. Invia i comandi inseriti dall'utente alle API del server

Alcuni comandi ADB utili:
- `adb devices`
- `adb pair <ip>:<port> <pairing code>`
- `adb tcpip <port>`
- `adb shell`
- `adb push <local file> <remote file>`
- `adb pull <remote file> <local file>`

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #54B052 10%, #3B7B39 20%);
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
level: 2
title: Sequence Diagram
---

# Sequence Diagram di ADB

```mermaid
sequenceDiagram
    box Blue Host (PC)
    participant adbClient as adb client
    participant adbServer as adb server
    end
    box Green Device (Android)
    participant adbDaemon as adb-daemon.cm
    participant adbShell as adb-shell.cm
    participant dashShell as dash shell
    end

    adbClient->>adbServer: comando "adb shell"
    adbServer->>adbDaemon: OPEN("shell")
    adbShell->>adbDaemon: PublishService("shell")
    adbDaemon->>adbShell: ConnectToService()
    Note over adbShell, dashShell: Spawn dash shell and pty device
    adbDaemon-->>adbServer: READY()
    dashShell<<->>adbClient: canale di trasporto ADB
```