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

### Additional style for navbar card

Paste this into your Navbar Card configuration. It uses the same dark glass,
softly cut corners, and rounded octagonal buttons as Glow Cards. Profile images
fill the octagonal buttons. Submenu popups share the glass finish and active
highlights, including layouts with labels inside their buttons. Counter badges
stay circular and sit above the icon borders.

See the [Navbar Card styling reference](https://joseluis9595.github.io/lovelace-navbar-card/docs/configuration/styles/)
for the supported selectors.

~~~yaml
styles: |-
  :host {
    --glow-nav-active-rgb: 144, 191, 255;
    --glow-nav-badge-rgb: 255, 145, 138;
  }

  .navbar-card {
    --navbar-border-radius: 10px;
    position: relative;
  }

  .navbar-card,
  .navbar-popup {
    isolation: isolate;
    overflow: visible !important;
    border-radius: 10px !important;
    corner-shape: superellipse(.25);
    border: 1px solid rgba(103, 192, 211, .55) !important;
    background:
      linear-gradient(180deg, rgba(223, 246, 255, .1), transparent 52%),
      linear-gradient(125deg, rgba(27, 43, 52, .85), rgba(12, 24, 31, .9)) !important;
    -webkit-backdrop-filter: blur(18px) saturate(135%);
    backdrop-filter: blur(18px) saturate(135%);
    box-shadow:
      inset 0 1px 0 rgba(235, 251, 255, .2),
      inset 0 -1px 0 rgba(0, 0, 0, .28),
      0 4px 12px rgba(0, 0, 0, .28) !important;
  }

  /* Reflections stay below navigation controls and never intercept taps. */
  .navbar-card::before,
  .navbar-popup::before {
    content: '';
    position: absolute;
    inset: 0;
    z-index: 0;
    pointer-events: none;
    border-radius: inherit;
    corner-shape: inherit;
    background: linear-gradient(156deg,
      rgba(235, 251, 255, .09), rgba(235, 251, 255, .025) 28%,
      transparent 29% 68%, rgba(211, 242, 255, .025) 69%, transparent 86%);
  }

  .routes,
  .navbar-popup > .popup-item {
    position: relative;
    z-index: 1;
  }

  .routes,
  .route,
  .route .button,
  .popup-item,
  .popup-item .button {
    overflow: visible !important;
  }

  .route .button,
  .popup-item .button {
    position: relative;
    box-sizing: border-box;
    width: 48px !important;
    height: 48px !important;
    aspect-ratio: 1 / 1;
    border-radius: 14px !important;
    corner-shape: superellipse(.25);
    border: 1px solid rgba(117, 191, 211, .38) !important;
    background: rgba(10, 19, 28, .35) !important;
    color: #9dbfce;
    box-shadow: inset 0 1px 0 rgba(216, 246, 255, .14) !important;
  }

  .route .button:has(.image),
  .popup-item:not(.popuplabelbackground) .button:has(.image) {
    padding: 0 !important;
  }

  .route .image,
  .popup-item:not(.popuplabelbackground) .image {
    position: absolute;
    inset: 0;
    width: 100% !important;
    height: 100% !important;
    max-width: none !important;
    max-height: none !important;
    margin: 0 !important;
    padding: 0 !important;
    display: block;
    aspect-ratio: 1 / 1;
    object-fit: cover;
    object-position: center;
    border-radius: inherit !important;
    corner-shape: inherit;
  }

  .route .icon,
  .popup-item .icon {
    color: #9dbfce !important;
    filter: drop-shadow(0 1px 1px rgba(0, 0, 0, .3));
  }

  /* Current Navbar Card marks the button active; keep route support too. */
  .route .button.active,
  .route.active .button,
  .popup-item.active .button {
    border-color: rgba(var(--glow-nav-active-rgb), .95) !important;
    background:
      linear-gradient(155deg, rgba(231, 251, 255, .07), transparent 48%),
      rgba(var(--glow-nav-active-rgb), .1) !important;
    box-shadow:
      inset 0 1px 0 rgba(231, 255, 255, .2),
      0 0 10px rgba(var(--glow-nav-active-rgb), .38),
      0 0 20px rgba(var(--glow-nav-active-rgb), .14) !important;
  }

  .route .button.active .icon,
  .route.active .icon,
  .popup-item.active .icon {
    color: rgb(var(--glow-nav-active-rgb)) !important;
    filter:
      drop-shadow(0 1px 1px rgba(0, 0, 0, .3))
      drop-shadow(0 0 4px rgba(var(--glow-nav-active-rgb), .5));
  }

  .navbar-popup {
    padding: 12px !important;
    gap: 10px;
  }

  .navbar-popup-backdrop {
    background: rgba(3, 8, 14, .48) !important;
    -webkit-backdrop-filter: blur(3px);
    backdrop-filter: blur(3px);
  }

  .popup-item .label {
    color: #c4c8d0 !important;
    font-size: 13px;
    font-weight: 600;
    text-shadow: 0 1px 2px rgba(0, 0, 0, .4);
  }

  .popup-item.active .label {
    color: rgb(var(--glow-nav-active-rgb)) !important;
  }

  /* Label-background mode needs a wider surface for the icon and text. */
  .popup-item.popuplabelbackground .button {
    width: auto !important;
    min-width: 48px;
    aspect-ratio: auto;
    padding: 0 12px !important;
    gap: 8px;
    border-radius: 10px !important;
  }

  .popup-item.popuplabelbackground .image {
    width: 32px !important;
    height: 32px !important;
    flex-shrink: 0;
    object-fit: cover;
    object-position: center;
    border-radius: 9px !important;
    corner-shape: superellipse(.25);
  }

  /* Circular counters remain above the octagonal border and its glow. */
  .badge,
  .badge.with-counter {
    position: absolute;
    z-index: 3;
    top: -4px !important;
    right: -6px !important;
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
    corner-shape: round;
    font-size: 11px !important;
    font-weight: 700 !important;
    line-height: 1 !important;
    color: rgb(var(--glow-nav-badge-rgb)) !important;
    background: linear-gradient(145deg, #181e27, #070b11) !important;
    border: 1px solid rgba(var(--glow-nav-badge-rgb), .58) !important;
    box-shadow:
      inset 0 1px 1px rgba(255, 255, 255, .09),
      0 0 5px rgba(var(--glow-nav-badge-rgb), .38),
      0 4px 9px rgba(0, 0, 0, .36) !important;
  }

  .badge.with-counter {
    letter-spacing: -.3px !important;
  }
~~~

---

## Installation

### HACS

1. Open **HACS** in Home Assistant.
2. Add this repository as a **Custom Repository**.
3. Select **Dashboard / Lovelace** as the repository type.
4. Install **Glow Cards**.
5. Refresh your browser.

If the cards do not appear immediately, reload Home Assistant and clear the browser cache.
