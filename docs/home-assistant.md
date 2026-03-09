# Home Assistant — Guida Completa

Home Assistant è il sistema domotico open source più potente e flessibile disponibile. Gira sul tuo hardware, tutto locale, nessun abbonamento.

---

## Perché Home Assistant

- **Oltre 3.000 integrazioni** — quasi qualsiasi dispositivo è supportato
- **Completamente locale** — funziona senza internet
- **Open source e gratuito** — nessun abbonamento obbligatorio
- **Automazioni potenti** — da semplici trigger a logiche complesse
- **Dashboard personalizzabile** — costruisci l'interfaccia che vuoi
- **Community enorme** — forum, Reddit, YouTube pieni di guide

---

## Metodi di installazione

### HAOS (Home Assistant OS) — Raccomandato per iniziare
Sistema operativo dedicato, installazione più semplice, aggiornamenti automatici. Ideale su Raspberry Pi o mini PC dedicato.

### Docker — Per chi ha già un server
Perfetto se hai un NAS o un server Linux. Home Assistant gira come container insieme agli altri servizi.

```yaml
# docker-compose.yml
services:
  homeassistant:
    container_name: homeassistant
    image: ghcr.io/home-assistant/home-assistant:stable
    volumes:
      - /volume1/docker/homeassistant/config:/config
      - /etc/localtime:/etc/localtime:ro
    restart: unless-stopped
    privileged: true
    network_mode: host
```

### Home Assistant Supervised
HA OS su un sistema Linux esistente — hai accesso agli add-on ufficiali mantenendo il controllo del sistema.

---

## Prima configurazione

### 1. Accedere all'interfaccia
Dopo l'installazione, apri il browser su `http://homeassistant.local:8123` oppure `http://IP-DEL-SERVER:8123`.

### 2. Creare l'account admin
Al primo avvio viene richiesto nome, utente e password. Questo è l'account principale — usane uno sicuro.

### 3. Rilevamento automatico dispositivi
Home Assistant scansiona la rete e propone le integrazioni rilevate automaticamente. Accetta quelle che riconosci.

### 4. Struttura della casa
Vai in **Impostazioni → Aree** e crea le stanze della tua casa (Soggiorno, Camera, Cucina...). Assegna i dispositivi alle aree per avere una dashboard organizzata.

---

## Integrazioni essenziali

### Tuya (via LocalTuya)
Per controllare i dispositivi Tuya in locale senza cloud. Vedi la [guida dedicata](tuya-local.md).

### Zigbee2MQTT
Per coordinare i dispositivi Zigbee tramite MQTT. Richiede il dongle Zigbee USB.

```yaml
# In configuration.yaml
mqtt:
  broker: localhost
  port: 1883
```

### HACS (Home Assistant Community Store)
Store non ufficiale con centinaia di integrazioni, temi e card aggiuntive. Indispensabile.

Installazione tramite terminale:
```bash
wget -O - https://get.hacs.xyz | bash -
```

---

## Automazioni

Le automazioni si compongono di tre parti: **trigger** (cosa scatena l'azione), **condizione** (opzionale, vincoli), **azione** (cosa succede).

### Esempio 1 — Luce che si accende al tramonto
```yaml
alias: "Luce soggiorno al tramonto"
trigger:
  - platform: sun
    event: sunset
    offset: "-00:30:00"
condition: []
action:
  - service: light.turn_on
    target:
      entity_id: light.soggiorno
    data:
      brightness_pct: 60
      color_temp: 400
mode: single
```

### Esempio 2 — Spegni tutto quando esci di casa
```yaml
alias: "Spegni tutto — uscita casa"
trigger:
  - platform: state
    entity_id: person.nicholas
    to: not_home
condition: []
action:
  - service: homeassistant.turn_off
    target:
      area_id: tutta_la_casa
mode: single
```

### Esempio 3 — Notifica se finestra aperta e riscaldamento acceso
```yaml
alias: "Finestra aperta con riscaldamento"
trigger:
  - platform: state
    entity_id: binary_sensor.finestra_camera
    to: "on"
    for: "00:05:00"
condition:
  - condition: state
    entity_id: climate.termostato
    state: heat
action:
  - service: notify.mobile_app
    data:
      message: "Finestra camera aperta da 5 minuti con riscaldamento attivo!"
mode: single
```

---

## Add-on utili

Se usi HAOS o Supervised, puoi installare add-on direttamente dall'interfaccia:

| Add-on | Funzione |
|---|---|
| **Zigbee2MQTT** | Gestione dispositivi Zigbee |
| **Mosquitto Broker** | Broker MQTT locale |
| **File Editor** | Modifica file di configurazione dal browser |
| **Terminal & SSH** | Accesso terminale |
| **Node-RED** | Automazioni visuali avanzate |
| **Frigate** | NVR con rilevamento oggetti AI |

---

## Backup

Configura i backup automatici in **Impostazioni → Sistema → Backup**. Imposta un backup giornaliero e scarica periodicamente una copia sul tuo PC.

Per chi usa Docker, è sufficiente fare il backup della cartella `/config`.

---

## Risorse

- Documentazione ufficiale: [home-assistant.io/docs](https://www.home-assistant.io/docs/)
- Community: [community.home-assistant.io](https://community.home-assistant.io)
- YouTube: canale ufficiale Home Assistant, Everything Smart Home, SmartHomeJunkie
