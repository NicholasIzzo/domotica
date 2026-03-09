# Consigli di Acquisto per Fascia di Prezzo

Tre setup completi e funzionanti, da quello essenziale a quello avanzato. Tutti basati su Home Assistant, tutti completamente locali.

---

## Setup Base — ~50€

Ideale per: chi vuole iniziare, appartamento piccolo, primo approccio alla domotica.

**Hardware:**

| Dispositivo | Prezzo | Note |
|---|---|---|
| Raspberry Pi 4 (2GB) o mini PC usato | ~35-50€ | Per far girare Home Assistant |
| Sonoff Zigbee 3.0 USB Dongle Plus | ~20€ | Coordinatore Zigbee |
| 2x Presa smart Sonoff ZBMINI o Tuya Zigbee | ~8-10€ cad | Prese con misura consumi |
| 1x Sensore temperatura/umidità Aqara o SONOFF | ~8€ | |

**Totale: ~55-70€**

**Cosa ottieni:**
- Home Assistant su hardware dedicato
- 2 prese smart controllabili da app e con automazioni
- Monitoraggio temperatura/umidità
- Base Zigbee espandibile

**Setup consigliato:**
1. Installa Home Assistant OS sul Raspberry Pi
2. Collega il dongle Zigbee via USB
3. Installa l'integrazione Zigbee2MQTT
4. Aggiungi le prese e il sensore
5. Prima automazione: spegni le prese in standby dopo mezzanotte

---

## Setup Intermedio — ~200€

Ideale per: appartamento medio, vuoi coprire le aree principali, automazioni più complete.

**Hardware:**

| Dispositivo | Qtà | Prezzo | Note |
|---|---|---|---|
| Mini PC (HP EliteDesk usato o Beelink mini) | 1 | ~80-100€ | Più potente del Pi, silenzioso |
| Sonoff Zigbee 3.0 USB Dongle Plus | 1 | ~20€ | |
| Lampadine Zigbee IKEA Tradfri E27 | 4-6 | ~10€ cad | Soggiorno e camera |
| Prese smart Zigbee Sonoff | 3-4 | ~10€ cad | TV, PC, elettrodomestici |
| Sensori apertura porta/finestra Aqara | 3-4 | ~8€ cad | Porte principali e finestre |
| Sensore movimento PIR Zigbee | 2 | ~10€ cad | Ingresso e corridoio |
| Sensore temperatura Aqara | 2 | ~8€ cad | Soggiorno e camera |

**Totale: ~180-220€**

**Cosa ottieni:**
- Illuminazione smart nelle stanze principali
- Monitoraggio consumi elettrici
- Rilevamento presenza per automazioni
- Allarme apertura finestre/porte
- Automazioni complete: luci al tramonto, spegnimento automatico, riscaldamento intelligente

**Automazioni incluse:**
- Luci che si accendono al tramonto e si spengono quando esci di casa
- Notifica se finestra rimane aperta con riscaldamento acceso
- Luce corridoio che si accende al movimento di notte (10% luminosità)
- Spegnimento totale con un tap quando vai a dormire

---

## Setup Avanzato — 500€+

Ideale per: casa, vuoi coprire tutto, integrazioni avanzate, sicurezza e risparmio energetico serio.

**Hardware:**

| Dispositivo | Qtà | Prezzo | Note |
|---|---|---|---|
| Mini PC dedicato (Beelink S12 Pro o simile) | 1 | ~150€ | SSD, RAM adeguata |
| Sonoff Zigbee 3.0 USB Dongle Plus | 1 | ~20€ | |
| Lampadine Zigbee (vari ambienti) | 10-15 | ~10€ cad | Tutta la casa |
| Strisce LED Zigbee (TV, cucina) | 2-3 | ~15-25€ cad | |
| Prese smart con misura consumi | 6-8 | ~10€ cad | |
| Sensori apertura (porte + finestre) | 6-8 | ~8€ cad | |
| Sensori movimento | 4-5 | ~10€ cad | |
| Termostato smart Zigbee | 1 | ~40-80€ | Es. Sonoff NSPanel o TRV Aqara |
| Valvole termostatiche Zigbee | 3-4 | ~25€ cad | Per ogni radiatore |
| Telecamera interna (Reolink o Frigate) | 1-2 | ~30-50€ cad | |
| Interruttori smart Zigbee (Aqara) | 4-6 | ~20€ cad | Senza staccare l'impianto |

**Totale: ~500-700€**

**Cosa ottieni:**
- Controllo completo dell'illuminazione in ogni stanza
- Gestione intelligente del riscaldamento stanza per stanza
- Monitoraggio consumi totale della casa
- Videosorveglianza locale (no cloud, con Frigate + rilevamento AI)
- Risparmio energetico stimato: 15-25% su riscaldamento e standby

**Funzionalità avanzate:**
- Riscaldamento che si abbassa automaticamente quando esci
- Modalità "cinema": luci soffuse, TV accesa, tutto controllato da un tap
- Rilevamento presenze per stanza
- Dashboard con consumi in tempo reale
- Integrazione con Google Home o Alexa per controllo vocale

---

## Dove comprare

| Shop | Punti di forza |
|---|---|
| **AliExpress** | Prezzi più bassi, spedizione 2-4 settimane |
| **Amazon** | Spedizione rapida, reso facile, prezzi leggermente più alti |
| **IKEA** | Dispositivi Tradfri reperibili subito, qualità garantita |
| **Domadoo** (FR) | Specializzato domotica, ottima selezione Z-Wave |
| **zigbee2mqtt.io** | Lista compatibilità dispositivi — controlla sempre prima di comprare |

---

> Prima di comprare qualsiasi dispositivo Zigbee, verifica la compatibilità su [zigbee2mqtt.io/supported-devices](https://www.zigbee2mqtt.io/supported-devices/). Ci sono oltre 3.000 dispositivi nella lista.
