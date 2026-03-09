# Dispositivi Consigliati

Una selezione curata dei migliori dispositivi per categoria — qualità, compatibilità con Home Assistant e rapporto qualità/prezzo.

---

## Illuminazione

### Lampadine smart

**Budget — IKEA Tradfri (~10€)**
Il miglior rapporto qualità/prezzo. Zigbee nativo, compatibile con HA out-of-the-box, reperibile ovunque. Disponibile in E27, E14, GU10. Unico limite: cambio colore solo su modelli specifici.

**Medio — Innr (~15€)**
Qualità costruttiva superiore a IKEA, colori più precisi, ottima compatibilità Zigbee.

**Premium — Philips Hue (~25-40€)**
La migliore qualità colore sul mercato, ecosistema maturo. Funzionano anche senza il bridge Hue tramite HA + Zigbee. Costosi ma durano anni.

**Da evitare:** lampadine Wi-Fi no-brand — incompatibili o difficili da integrare localmente.

---

### Strisce LED

**Gledopto Zigbee (~20-25€)**
Standard de facto per strisce LED Zigbee. Supporta RGBCCT (colore + bianco caldo/freddo), compatibile con qualsiasi striscia LED 12V/24V.

**Shelly RGBW2 (~20€)**
Controller Wi-Fi per strisce LED, supporto MQTT locale nativo, ottima integrazione HA.

---

### Interruttori smart

**Aqara D1 (~20€)** — Zigbee, installazione senza neutro, design elegante
**Shelly 1 (~10€)** — Wi-Fi, MQTT locale, installazione in scatola da muro esistente
**Sonoff ZBMINIL2 (~8€)** — Zigbee, senza neutro, ideale per retrofit

---

## Prese Smart

**Sonoff S26R2ZB (~10€)**
Presa Zigbee con on/off. Economica, affidabile, buona compatibilità.

**NOUS A1Z (~12€)**
Presa Zigbee con misura consumi in tempo reale — potenza, tensione, corrente. Ottima per monitorare elettrodomestici.

**Shelly Plug S (~15€)**
Wi-Fi con MQTT locale, misura consumi, design compatto. Tra le migliori prese smart in assoluto.

---

## Sensori

### Temperatura e umidità

**Aqara WSDCGQ11LM (~8€)**
Il sensore temperatura/umidità Zigbee più usato. Piccolo, preciso, batteria che dura 2+ anni.

**Sonoff SNZB-02 (~7€)**
Alternativa economica con buona precisione.

**Xiaomi LYWSD03MMC (~5€)**
Bluetooth, ma con firmware custom diventa locale e si integra con HA tramite BTHome.

---

### Apertura porte e finestre

**Aqara MCCGQ11LM (~8€)**
Sensore porta/finestra Zigbee più affidabile. Design minimale, magnete separato, ottima build quality.

**Sonoff SNZB-04 (~6€)**
Alternativa economica, stesso principio di funzionamento.

---

### Movimento (PIR)

**Aqara MS-FP1 (~35€)**
Sensore presenza con tecnologia radar mmWave — rileva la presenza anche ferma (non solo il movimento). Il migliore sul mercato per evitare che le luci si spengano mentre sei seduto fermo.

**SONOFF SNZB-03 (~8€)**
PIR classico, economico, buona sensibilità. Per aree di transito (corridoio, ingresso).

**Philips Hue Motion (~30€)**
PIR di qualità, include anche temperatura. Zigbee, funziona direttamente con HA.

---

### Qualità dell'aria

**Aqara TVOC Air Quality Monitor (~35€)**
Zigbee, misura TVOC (composti organici volatili), temperatura e umidità. Ottimo per camere e uffici.

**Ikea Vindstyrka (~15€)**
Sensore qualità aria con display. Wi-Fi, integrazione HA via Matter.

---

## Termostati e Riscaldamento

**Valvole termostatiche Zigbee — SONOFF TRVZB (~25€)**
Controllo temperatura per ogni radiatore. Si monta al posto della valvola manuale. Controllo stanza per stanza.

**Termostato Zigbee — Sonoff NSPanel (~35€)**
Display touch da parete, controlla temperatura e altri dispositivi. Può fungere da interruttore centrale.

**Termostato Zigbee — MOES BRT-100 (~30€)**
Valvola termostatica intelligente con auto-calibrazione.

---

## Sicurezza

### Telecamere

**Reolink E1 Zoom (~35€)**
Wi-Fi, 5MP, supporto RTSP nativo — fondamentale per integrazione con Home Assistant e Frigate. Nessun cloud obbligatorio.

**Reolink RLC-810A (~60€)**
PoE (cablata), 4K, rilevamento AI (persone, veicoli). La migliore per esterno.

**Da evitare:** telecamere che non supportano RTSP o che richiedono obbligatoriamente il cloud.

---

### Serrature smart

**Nuki Smart Lock 4.0 (~130€)**
Si installa sopra la serratura esistente senza sostituirla. Bluetooth + Thread (Matter). Integrazione HA nativa. La più usata in Italia.

**Danalock V3 (~100€)**
Z-Wave, ottima affidabilità, integrazione HA diretta.

---

## Coordinatori e Hub

**Dongle Zigbee — Sonoff Zigbee 3.0 USB Dongle Plus (~20€)**
Il coordinatore Zigbee più consigliato dalla community. Plug & play con Zigbee2MQTT e ZHA su Home Assistant.

**Dongle combo — HUSBZB-1 (~40€)**
Zigbee + Z-Wave in un unico dongle USB. Ideale se vuoi supportare entrambi i protocolli.

---

> Controlla sempre la compatibilità su [zigbee2mqtt.io/supported-devices](https://www.zigbee2mqtt.io/supported-devices/) prima di acquistare qualsiasi dispositivo Zigbee.
