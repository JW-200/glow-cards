# ✨ Glow Cards

## Disclaimer
> **AI-generated project:** The cards in this repository were generated using AI.

## Cards

Glow Cards currently includes seven card types:

| Card               | Type                                     | Description                                       |
| ------------------ | ---------------------------------------- | ------------------------------------------------- |
| 💡 Light           | `custom:reference-basic-light-card`      | Compact on/off light or switch card               |
| 🎚️ Dimmable Light | `custom:reference-brightness-light-card` | Light card with brightness slider                 |
| 👤 Person          | `custom:reference-person-picture-card`   | Person presence card with optional battery status |
| 📊 Sensor          | `custom:reference-sensor-state-card`     | Sensor value card with configurable active state  |
| 🌡️ Thermostat     | `custom:reference-thermostat-card`       | Climate card with target-temperature controls     |
| ➡️ Navigation      | `custom:reference-navigation-card`       | Dashboard navigation card                         |

| Vacuum             | `custom:reference-vacuum-card`            | Optional dock and consumable indicators           |

All cards can be configured through YAML and include a Home Assistant visual editor.

### Interaction actions

The light, dimmable-light, and sensor cards support Home Assistant-style
`tap_action`, `double_tap_action`, and `hold_action` overrides. Supported actions
include `toggle`, `more-info`, `navigate`, `url`, `assist`, `perform-action`, and
`none`.

### Additional style for navbar card:

```css
styles: |-
  .image {
    border-radius: 50% !important;
  }

  .navbar-card {
    --navbar-border-radius: 100px;
    overflow: visible !important;
  }

  .routes,
  .route,
  .route .button,
  .button {
    overflow: visible !important;
  }

  .route .button {
    width: 48px !important;
  }

  .button {
    height: 48px !important;
    border-radius: 24px !important;
  }

  /* Counter styled like Glow Cards compact subicon */
  .badge,
  .badge.with-counter {
    width: 20px !important;
    min-width: 20px !important;
    max-width: 20px !important;
    height: 20px !important;

    padding: 0 !important;
    box-sizing: border-box !important;

    display: flex !important;
    align-items: center !important;
    justify-content: center !important;

    border-radius: 50% !important;

    font-size: 11px !important;
    font-weight: 700 !important;
    line-height: 1 !important;

    /* Dark glass face, matching subicon treatment */
    background:
      linear-gradient(
        145deg,
        rgba(40, 30, 32, 0.96),
        rgba(20, 17, 20, 0.98)
      ) !important;

    color: rgb(255, 145, 138) !important;

    border: 1px solid rgba(255, 145, 138, 0.58) !important;

    box-shadow:
      0 0 5px rgba(255, 145, 138, 0.38),
      0 0 10px rgba(255, 145, 138, 0.16),
      inset 0 1px 1px rgba(255, 255, 255, 0.07) !important;

    text-shadow:
      0 0 4px rgba(255, 145, 138, 0.65) !important;

    /* Sit partly over the lower/right edge, like a subicon */
    top: -4px !important;
    right: -6px !important;
  }

  /* Slightly reduce text for 2+ digit counters */
  .badge.with-counter {
    letter-spacing: -0.3px !important;
  }

  /* Selected item blue glow */
  .route.active .button {
    background:
      linear-gradient(
        145deg,
        rgba(144, 191, 255, 0.16),
        rgba(80, 120, 180, 0.08)
      ) !important;

    border: 1px solid rgba(144, 191, 255, 0.40) !important;

    box-shadow:
      0 0 8px rgba(144, 191, 255, 0.60),
      0 0 18px rgba(144, 191, 255, 0.28),
      inset 0 0 10px rgba(144, 191, 255, 0.10),
      inset 0 1px 1px rgba(255, 255, 255, 0.06) !important;
  }

  .route.active ha-icon {
    color: rgb(144, 191, 255) !important;

    filter:
      drop-shadow(0 0 4px rgba(144, 191, 255, 0.90))
      drop-shadow(0 0 8px rgba(144, 191, 255, 0.40));
  }
```

---

## Installation

### HACS

1. Open **HACS** in Home Assistant.
2. Add this repository as a **Custom Repository**.
3. Select **Dashboard / Lovelace** as the repository type.
4. Install **Glow Cards**.
5. Refresh your browser.

If the cards do not appear immediately, reload Home Assistant and clear the browser cache.
