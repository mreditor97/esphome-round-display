# ESPHome Round Display

ESPHome configuration for the LilyGo T-RGB 2.1" round (full circle) display, with an LVGL touch interface.

| Part             | ESPHome component                                                          |
| ---------------- | -------------------------------------------------------------------------- |
| ST7701S panel    | [`mipi_rgb`](https://esphome.io/components/display/mipi_rgb/), `T-RGB-2.1` |
| CST820 touch     | [`cst816`](https://esphome.io/components/touchscreen/cst816/)              |
| XL9535 expander  | [`xl9535`](https://esphome.io/components/xl9535/)                          |
| UI               | [`lvgl`](https://esphome.io/components/lvgl/)                              |

## Usage

1. Copy `secrets.yaml.example` to `secrets.yaml` and fill in your values.
2. Build and flash over USB:

   ```bash
   esphome run lilygo-t-rgb-2-1.yaml
   ```

## Notes

- The panel's SPI init lines, reset, power enable and touch reset are all on the XL9535 expander. The init
  sequence is bit-banged over I2C at boot, so the display takes a moment to come up.
- GPIO46 drives the backlight as a dimmable light. The arc on the screen sets its brightness.
- If touches land in the wrong place, add a `transform` (`mirror_x`, `mirror_y`, `swap_xy`) to the touchscreen.
