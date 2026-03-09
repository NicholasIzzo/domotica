# Tuya Local — Liberarsi dal Cloud

I dispositivi Tuya sono tra i più economici e diffusi sul mercato. Il problema: di default comunicano con server in Cina e senza internet non funzionano. La soluzione è controllare tutto localmente tramite Home Assistant.

---

## Il problema con Tuya Cloud

```
Situazione default:
Dispositivo Tuya → Internet → Server Cina → Internet → Home Assistant

Problemi:
- Se cade internet → dispositivo non risponde
- I tuoi dati passano per server remoti
- Latenza alta (500ms+)
- Se Tuya chiude il servizio → dispositivi inutili
```

```
Con LocalTuya:
Dispositivo Tuya → Rete locale → Home Assistant

Vantaggi:
- Funziona senza internet
- Latenza <50ms
- Privacy totale
- Nessuna dipendenza da Tuya
```

---

## Prerequisiti

1. **Home Assistant** installato e funzionante
2. **HACS** installato (per LocalTuya)
3. Account Tuya Developer (gratuito) per ottenere le chiavi API locali
4. I dispositivi Tuya devono essere già configurati nell'app Tuya/Smart Life almeno una volta

---

## Metodo 1 — LocalTuya (raccomandato)

### Installazione

1. Apri HACS in Home Assistant
2. Vai in **Integrazioni** → cerca **LocalTuya**
3. Installa e riavvia Home Assistant

### Ottenere le chiavi locali

Hai bisogno di `device_id` e `local_key` per ogni dispositivo. Il modo più semplice:

**Via Tuya IoT Platform:**
1. Registrati su [iot.tuya.com](https://iot.tuya.com)
2. Crea un nuovo progetto Cloud
3. Collega il tuo account Smart Life al progetto
4. Vai in **Devices** — trovi `device_id` e `local_key` per ogni dispositivo

**Via tuyakey (tool automatico):**
```bash
pip install tuyakey
tuyakey --username TUO_EMAIL --password TUA_PASSWORD --country IT
```

### Configurazione in Home Assistant

Vai in **Impostazioni → Dispositivi e servizi → Aggiungi integrazione → LocalTuya**

Per ogni dispositivo inserisci:
- **IP address** — IP fisso del dispositivo (imposta IP statico nel router)
- **Device ID** — ottenuto da Tuya IoT Platform
- **Local Key** — ottenuta da Tuya IoT Platform
- **Protocol version** — solitamente 3.3 o 3.4

### Mappatura dei DP (Data Points)

I DP sono i "canali" del dispositivo. Una presa smart ha DP1 per on/off, DP9 per i consumi, ecc.

```yaml
# Esempio configurazione presa smart con misura consumi
- platform: localtuya
  host: 192.168.1.50
  device_id: abc123def456
  local_key: xyz789
  protocol_version: "3.3"
  entities:
    - platform: switch
      dp: 1
      name: Presa
    - platform: sensor
      dp: 19
      name: Potenza
      unit_of_measurement: W
    - platform: sensor
      dp: 20
      name: Tensione
      unit_of_measurement: V
```

---

## Metodo 2 — Tuya integrazione ufficiale (ibrido)

Home Assistant ha un'integrazione Tuya ufficiale che usa il cloud ma con una modalità locale parziale. Più semplice da configurare ma meno affidabile di LocalTuya.

Va bene per iniziare, ma sul lungo periodo LocalTuya è preferibile.

---

## Metodo 3 — Flash con firmware alternativo

Per i dispositivi basati su chip ESP8266/ESP32 (molti Tuya lo sono), puoi sostituire il firmware con **ESPHome** o **Tasmota** — firmware open source completamente locali.

**Vantaggi:** controllo totale, zero cloud, integrazione nativa con HA
**Svantaggi:** invalida la garanzia, richiede competenze tecniche, non tutti i dispositivi sono flashabili

**Come capire se un dispositivo è flashabile:**
- Cerca il modello su [templates.blakadder.com](https://templates.blakadder.com)
- Se è presente ha un template Tasmota → è flashabile

---

## Risoluzione problemi comuni

**Il dispositivo non risponde:**
- Verifica che abbia IP fisso (configura IP statico nel router per il MAC address del dispositivo)
- Controlla che il firewall non blocchi la porta 6668 (porta Tuya locale)
- Prova a reimpostare il dispositivo e riconfiguralo nell'app Smart Life

**La local_key non funziona:**
- Le chiavi cambiano ogni volta che il dispositivo viene aggiunto/rimosso dall'app
- Dopo ogni reset del dispositivo devi recuperare la nuova local_key

**Dispositivo offline in HA ma funzionante nell'app:**
- Il dispositivo sta ancora usando il cloud — assicurati di usare l'IP corretto
- Alcuni dispositivi più nuovi usano protocollo 3.4 invece di 3.3

---

> Una volta configurato LocalTuya, puoi bloccare l'accesso a internet dei dispositivi Tuya dal router/firewall — così sei sicuro che non comunichino mai con server esterni.
