# Come Funziona la Domotica

La domotica è il controllo automatizzato dei dispositivi di casa — luci, prese, termostati, serrature, telecamere — da un unico sistema centrale.

---

## I componenti fondamentali

```
Dispositivi fisici
(lampadine, prese, sensori)
        │
        │ parlano tramite protocollo
        │ (Zigbee, Wi-Fi, Z-Wave...)
        ▼
    Hub / Controller
    (Home Assistant)
        │
        │ espone controllo tramite
        ▼
Dashboard / App / Automazioni
(browser, smartphone, voce)
```

---

## I Dispositivi

Tutto quello che puoi collegare alla tua rete domotica:

| Categoria | Esempi | Uso tipico |
|---|---|---|
| **Illuminazione** | Lampadine smart, strisce LED, interruttori | Accensione automatica, scenari luce |
| **Prese smart** | Prese con misura consumi | Monitoraggio energia, spegnimento automatico |
| **Sensori** | Temperatura, umidità, movimento, apertura porte | Automazioni condizionali |
| **Termostati** | Termostati smart, valvole termostatiche | Riscaldamento intelligente |
| **Sicurezza** | Telecamere, sirene, serrature smart | Monitoraggio e accesso |
| **Multimedia** | TV smart, soundbar, proiettori | Scene home theater |
| **Elettrodomestici** | Lavatrice, lavastoviglie smart | Automazioni energetiche |

---

## I Protocolli

Il protocollo è il "linguaggio" che usano i dispositivi per comunicare. La scelta del protocollo è la decisione più importante nella domotica.

### Wi-Fi
I dispositivi si connettono direttamente alla tua rete Wi-Fi — come uno smartphone.

**Pro:** facile da configurare, non serve hub aggiuntivo
**Contro:** ogni dispositivo occupa un indirizzo IP, la rete si intasa con molti dispositivi, dipende dal cloud del produttore (Tuya, Ezviz, ecc.)

**Ideale per:** chi inizia, chi ha pochi dispositivi

---

### Zigbee
Protocollo radio a bassa potenza, pensato specificamente per la domotica. I dispositivi formano una mesh — si passano i segnali l'uno con l'altro estendendo la copertura.

**Pro:** non usa Wi-Fi, consumi bassissimi (le batterie durano anni), mesh auto-estendente, centinaia di dispositivi supportati, completamente locale
**Contro:** serve un coordinatore (dongle USB ~15€), setup leggermente più tecnico

**Ideale per:** chi vuole scalare con molti dispositivi, chi vuole tutto in locale

---

### Z-Wave
Simile a Zigbee ma su frequenza diversa (868MHz in Europa). Meno interferenze, ma dispositivi più costosi.

**Pro:** frequenza dedicata, zero interferenze con Wi-Fi, ottima stabilità
**Contro:** dispositivi più cari, meno scelta rispetto a Zigbee

**Ideale per:** chi vuole massima affidabilità, budget più alto

---

### Matter / Thread
Il nuovo standard unificato supportato da Apple, Google, Amazon e Samsung. Matter è il protocollo applicativo, Thread è la rete mesh sottostante.

**Pro:** un dispositivo funziona con tutti gli ecosistemi (HA, Google Home, Apple Home)
**Contro:** ecosistema ancora in crescita, non tutti i dispositivi lo supportano

**Ideale per:** chi vuole il futuro, chi usa sia Home Assistant che Google/Apple Home

---

## L'Hub — Home Assistant

Home Assistant è il cervello del sistema. Gira sul tuo hardware (NAS, Raspberry Pi, mini PC) e controlla tutti i dispositivi da un'unica interfaccia.

**Perché Home Assistant:**
- Open source e gratuito
- Supporta oltre 3.000 integrazioni
- Tutto locale — nessun cloud obbligatorio
- Automazioni potentissime
- Dashboard completamente personalizzabile
- Community enorme

**Alternative:**
- Google Home / Apple Home — più semplici ma limitati
- Hubitat — simile a HA ma meno flessibile
- Homey — buona UX ma abbonamento

---

## Cloud vs Locale

Questa è la distinzione più importante da capire:

```
Cloud (Tuya, Alexa, Google)     Locale (Home Assistant)
────────────────────────────    ────────────────────────
Dispositivo → Internet          Dispositivo → Hub locale
    → Server in Cina                → Risposta immediata
    → Risposta (se online)

Rischi:                         Vantaggi:
- Se cade internet → niente     - Funziona senza internet
- Se chiude l'azienda → niente  - Privacy totale
- I tuoi dati su server remoti  - Latenza <100ms
- Costi abbonamento             - Nessun abbonamento
```

**Obiettivo di questa guida:** usare dispositivi anche economici (Tuya) ma controllarli **localmente** tramite Home Assistant, eliminando la dipendenza dal cloud.

---

> Il punto di partenza ideale è Home Assistant + un dongle Zigbee + qualche sensore/lampadina Zigbee economica. Con 50-80€ puoi avere un sistema domotico serio, completamente locale e espandibile.
