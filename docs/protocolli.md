# Protocolli a Confronto

Scegliere il protocollo giusto è la decisione più importante quando si costruisce un sistema domotico.

---

## Confronto rapido

| Protocollo | Mesh | Batterie | Hub richiesto | Costo dispositivi | Privacy |
|---|---|---|---|---|---|
| **Wi-Fi** | No | No | No | Basso | Cloud |
| **Zigbee** | Sì | Sì (anni) | Dongle ~20€ | Basso | Locale |
| **Z-Wave** | Sì | Sì (anni) | Dongle ~50€ | Medio-Alto | Locale |
| **Matter** | Sì (Thread) | Sì | No | Medio | Locale |

---

## Wi-Fi

La maggior parte dei dispositivi economici usa Wi-Fi — Tuya, Shelly, Sonoff WiFi si connettono direttamente al router.

**Quando ha senso:** stai iniziando, hai pochi dispositivi, vuoi spendere poco.

**Il problema:** i dispositivi Tuya di default parlano con server in Cina. Se cade internet, non funzionano. La soluzione è **LocalTuya** su Home Assistant — vedi la [guida dedicata](tuya-local.md).

**Shelly** è l'alternativa Wi-Fi migliore: MQTT locale nativo, nessun cloud obbligatorio, firmware open source disponibile.

---

## Zigbee — Il gold standard

Il protocollo più usato nella domotica seria. Centinaia di dispositivi compatibili, prezzi bassi, completamente locale.

### Come funziona la mesh

```
Coordinatore (dongle USB collegato a Home Assistant)
        │
    ┌───┴────────┐
  Router       Router        ← dispositivi alimentati (prese, lampadine)
  (presa)     (lampadina)       estendono automaticamente la rete
    │
  End Device                 ← dispositivi a batteria (sensori)
  (sensore porta)               si connettono al router più vicino
```

I dispositivi alimentati fanno da ripetitori automaticamente — più dispositivi hai, più la rete è stabile.

### Dongle consigliati

| Dongle | Prezzo | Note |
|---|---|---|
| **Sonoff Zigbee 3.0 USB Dongle Plus** | ~20€ | Il più consigliato, plug & play con HA |
| **Conbee II** | ~35€ | Ottima compatibilità |
| **HUSBZB-1** | ~40€ | Zigbee + Z-Wave combo |

### Brand affidabili

- **IKEA Tradfri** — economici, ottima compatibilità, reperibili ovunque
- **Aqara** — sensori eccellenti, qualità costruttiva alta
- **Sonoff Zigbee** — prese e sensori economici e affidabili
- **Tuya Zigbee** — economici, compatibili con Zigbee2MQTT

---

## Z-Wave

Usa la frequenza 868MHz in Europa — dedicata, zero interferenze con Wi-Fi. Standard preferito per installazioni professionali.

**Quando scegliere Z-Wave:** vuoi zero compromessi sulla stabilità, hai budget più alto, l'ambiente ha molte interferenze radio.

**Contro:** i dispositivi costano il doppio rispetto a Zigbee equivalente.

---

## Matter — Il futuro

Protocollo unificato creato da Apple, Google, Amazon e Samsung. Un dispositivo Matter funziona con tutti gli ecosistemi.

**Stato attuale:** Home Assistant lo supporta nativamente, ecosistema in crescita ma ancora pochi dispositivi economici. Per ora Zigbee rimane la scelta più matura.

---

## La scelta giusta per te

```
Inizi con budget limitato?
    → Wi-Fi (Tuya/Shelly) + LocalTuya

Vuoi un sistema serio e scalabile?
    → Zigbee (dongle Sonoff + IKEA/Aqara)

Massima stabilità, budget alto?
    → Z-Wave

Pensi al lungo periodo?
    → Matter dove disponibile, Zigbee per il resto
```

> Home Assistant gestisce tutti i protocolli contemporaneamente — puoi avere luci Zigbee, prese Shelly Wi-Fi e sensori Z-Wave nello stesso sistema.
