# Demo script (5 minutes)

## Before the judges arrive

```bash
# Terminal 1 — API
cd kura-alert && make api

# Terminal 2 — dashboard
cd kura-alert && make web

# Terminal 3 — a ground reading (optional)
python3 hardware/scripts/simulate_node.py --count 1
```

Check:

- http://127.0.0.1:8000/health returns `ok: true`.
- http://127.0.0.1:3000 loads and the header says **Live data**.
- The ground-node card says **Simulated** (or **Live** for real hardware).
- Browser zoom is 100 %, one tab only, notifications off.
- If the venue Wi-Fi is dead, the page still loads from the bundled snapshot
  and the badge says **Offline snapshot**. Say that out loud; it is a feature.

## 0:00 — Open on the hero

"This is Gombe today. One number, one level, one action — in English or Hausa."

- Point at **21/100 — Low**.
- Read the headline: *Dust is low today in Gombe.*

## 0:30 — Switch to Hausa

- Click **HA** in the header.
- Read the headline and one advice card aloud.
- Say: "The Hausa copy is pending native-speaker review; it is flagged in the
  repo."

## 1:00 — Show the share message

- Point at the WhatsApp card.
- Toggle **Hausa / English** and **WhatsApp / SMS**.
- Click **Copy message**, then paste into a notes app (or just show the char
  count). Do **not** send a message during the demo.
- Say: "This is the whole product for a trader: a message they can forward."

## 1:30 — Move to tomorrow

- Click **Tomorrow** in the day strip.
- Point at the change in score and advice.
- Say: "Three days, so you can plan laundry, stock or a school run."

## 2:00 — Flood early warning

- Scroll to **Dust and flood, in one window**.
- Point at the rainfall bars and the 15/30/50 mm legend.
- Say: "Today is dry, so flood is Low. But the rule has hard floors: 15 mm is a
  watch, 30 is high, 50 is severe. One heavy day cannot hide as low."
- Point at the ground-node card: dust, rain, water level, temperature,
  humidity, device id and last-reading time.

## 2:45 — Evidence

- Click the **NASA** tab.
- Point at the lag badge: **2026-08-30 · 77 days**.
- Say: "We do not pretend MERRA-2 is today. It gives the seasonal baseline;
  CAMS gives the live field."
- Point at the validation tiles: **r 0.87, n 30, bias 0.16** and the caveat.
- Click **Satellite**, show the true-colour/AOD layers, then back to **Live**.

## 3:30 — "Show me why"

- Scroll to **A formula you can audit**.
- Read the formula line and the four weights.
- Point at the level cuts and the flood thresholds.
- Say: "No hidden model. A judge can recompute this."

## 4:00 — Hardware

- Open `hardware/README.md` on screen (or the wiring SVG).
- Point at the pin table: `D0` PMS TX, `D2` rain, `D3/D4` ultrasonic,
  `D5` DHT22, `D6` buzzer, `D7` backlight button, `SDA/SCL` LCD.
- Say: "An Arduino UNO R4 WiFi, a dust sensor, a rain gauge, a water-level
  sensor and a backlit LCD. It posts to the same API and warns locally without
  internet."

## 4:30 — Close

- Back to the top, Hausa message visible.
- "Open data, open code, a message a trader can use. Next: native-speaker
  review and a 50-person market pilot."

## If something breaks

| Problem | Recovery |
| --- | --- |
| API is down | Reload. The page uses the bundled snapshot; point at the **Offline snapshot** badge. |
| Wi-Fi is down | Same. The forecast snapshot and all UI still work; satellite may not load. |
| Satellite image is blank | Click another layer or say "GIBS is delayed; here is the Worldview link" and move on. |
| No sensor reading | Run `make simulate`; the card appears with a **Simulated** badge. |
| Chart is empty | It is the dry season; that is the correct state. Point at the "No rain recorded" note and the watch line. |
| A judge asks for High/Severe | Open `docs/methodology.md` and show the score bands and flood floors. There is no live storm today; do not fake it. |

## Do not

- Do not send a WhatsApp/SMS message from the demo phone.
- Do not claim official warning status.
- Do not give medical advice; read the disclaimer.
- Do not say the Hausa is perfect.
