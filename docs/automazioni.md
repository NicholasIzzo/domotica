# Scenari e Automazioni

Esempi pratici di automazioni pronte da copiare in Home Assistant. Ogni scenario include il codice YAML completo e una spiegazione.

---

## Come usare questi esempi

In Home Assistant vai in **Impostazioni → Automazioni → Crea automazione → Modifica come YAML** e incolla il codice. Sostituisci gli `entity_id` con quelli dei tuoi dispositivi reali.

Per trovare l'entity_id di un dispositivo: **Impostazioni → Dispositivi e servizi → clic sul dispositivo → clic sull'entità**.

---

## Scenario 1 — Luci automatiche al tramonto

Le luci del soggiorno si accendono 30 minuti prima del tramonto con una luminosità morbida.

```yaml
alias: "Luci soggiorno al tramonto"
description: "Accende le luci 30 min prima del tramonto"
trigger:
  - platform: sun
    event: sunset
    offset: "-00:30:00"
condition:
  - condition: state
    entity_id: person.nicholas
    state: home
action:
  - service: light.turn_on
    target:
      entity_id: light.soggiorno
    data:
      brightness_pct: 60
      color_temp: 370
mode: single
```

---

## Scenario 2 — Spegni tutto quando esci di casa

Quando l'ultima persona esce di casa, luci e prese si spengono automaticamente.

```yaml
alias: "Casa vuota — spegni tutto"
description: "Spegne luci e prese quando nessuno è in casa"
trigger:
  - platform: state
    entity_id: group.tutti_in_casa
    to: "off"
    for: "00:02:00"
condition: []
action:
  - service: light.turn_off
    target:
      area_id: tutta_la_casa
  - service: switch.turn_off
    target:
      entity_id:
        - switch.presa_tv
        - switch.presa_pc
        - switch.presa_stereo
  - service: notify.mobile_app_telefono_nicholas
    data:
      message: "Casa svuotata — tutto spento"
mode: single
```

---

## Scenario 3 — Luce corridoio di notte

Di notte, se rileva movimento nel corridoio, la luce si accende al 10% per 2 minuti.

```yaml
alias: "Luce corridoio notturna"
description: "Luce fioca al movimento durante la notte"
trigger:
  - platform: state
    entity_id: binary_sensor.sensore_movimento_corridoio
    to: "on"
condition:
  - condition: time
    after: "23:00:00"
    before: "07:00:00"
action:
  - service: light.turn_on
    target:
      entity_id: light.corridoio
    data:
      brightness_pct: 10
      color_temp: 500
  - delay: "00:02:00"
  - service: light.turn_off
    target:
      entity_id: light.corridoio
mode: restart
```

---

## Scenario 4 — Finestra aperta con riscaldamento acceso

Notifica se una finestra rimane aperta per più di 5 minuti con il riscaldamento attivo.

```yaml
alias: "Finestra aperta + riscaldamento"
description: "Avvisa se si spreca energia"
trigger:
  - platform: state
    entity_id: binary_sensor.finestra_camera
    to: "on"
    for: "00:05:00"
condition:
  - condition: state
    entity_id: climate.termostato_camera
    state: heat
action:
  - service: notify.mobile_app_telefono_nicholas
    data:
      title: "Attenzione risparmio energetico"
      message: "Finestra camera aperta da 5 min con riscaldamento attivo!"
mode: single
```

---

## Scenario 5 — Modalità Cinema

Un tap su un pulsante virtuale: TV accesa, luci soffuse, presa soundbar accesa.

```yaml
alias: "Modalità Cinema"
description: "Prepara il soggiorno per guardare un film"
trigger:
  - platform: state
    entity_id: input_boolean.modalita_cinema
    to: "on"
condition: []
action:
  - service: light.turn_on
    target:
      entity_id: light.soggiorno
    data:
      brightness_pct: 15
      color_temp: 500
  - service: switch.turn_on
    target:
      entity_id: switch.presa_soundbar
  - service: media_player.turn_on
    target:
      entity_id: media_player.tv_soggiorno
mode: single
```

Per creare il pulsante virtuale: **Impostazioni → Dispositivi e servizi → Helper → Interruttore di input**.

---

## Scenario 6 — Risparmio energetico standby

Spegne le prese di dispositivi in standby (TV, console, caricabatterie) automaticamente di notte.

```yaml
alias: "Spegni standby a mezzanotte"
description: "Elimina i consumi fantasma di notte"
trigger:
  - platform: time
    at: "00:30:00"
condition:
  - condition: state
    entity_id: person.nicholas
    state: not_home
action:
  - service: switch.turn_off
    target:
      entity_id:
        - switch.presa_tv
        - switch.presa_console
        - switch.presa_caricabatterie
mode: single
```

---

## Scenario 7 — Benvenuto a casa

Quando torni a casa dopo le 18, le luci si accendono e la notifica ti accoglie.

```yaml
alias: "Bentornato a casa"
description: "Accende le luci al rientro serale"
trigger:
  - platform: state
    entity_id: person.nicholas
    to: home
condition:
  - condition: sun
    after: sunset
    after_offset: "-01:00:00"
action:
  - service: light.turn_on
    target:
      area_id: ingresso
    data:
      brightness_pct: 80
  - service: notify.mobile_app_telefono_nicholas
    data:
      message: "Bentornato a casa!"
mode: single
```

---

## Scenario 8 — Monitoraggio consumi anomali

Notifica se una presa supera una soglia di consumo inattesa (es. lavatrice finita).

```yaml
alias: "Lavatrice finita"
description: "Avvisa quando la lavatrice ha terminato il ciclo"
trigger:
  - platform: numeric_state
    entity_id: sensor.presa_lavatrice_power
    below: 5
    for: "00:02:00"
condition:
  - condition: numeric_state
    entity_id: sensor.presa_lavatrice_power
    above: 0
    # evita notifiche false quando è già spenta
action:
  - service: notify.mobile_app_telefono_nicholas
    data:
      title: "Lavatrice"
      message: "Il bucato è pronto!"
mode: single
```

---

## Suggerimenti generali

**Usa `mode: restart`** per automazioni con sensori di movimento — se il sensore scatta di nuovo mentre l'automazione è in corso, riparte il timer.

**Usa `mode: single`** per automazioni che non devono sovrapporsi (es. benvenuto a casa).

**Testa sempre** le automazioni manualmente prima di affidarci cose importanti — clic su **Esegui** nell'editor dell'automazione.

**Usa i log** in **Impostazioni → Sistema → Log** per debuggare automazioni che non funzionano come previsto.
