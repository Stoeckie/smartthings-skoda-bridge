# Škoda cars in SmartThings (official MyŠkoda public API)

Get your **Škoda** into SmartThings through Škoda's **official public API** (free, personal use): battery, charging on/off and power, charging cable, climate, at home and doors. Works for electric and plug-in hybrid Škodas with MyŠkoda connectivity; what is available depends on the car.

The code lives in **[Stoeckie/smartthings-stoeckie-bridge](https://github.com/Stoeckie/smartthings-stoeckie-bridge)**: one small bridge (Windows or Docker) plus the Edge driver **Stoeckie Bridge (local)**. The same bridge also does AEG / Electrolux dryers, Fujitsu FGLair air conditioners and the VELUX ACTIVE departure mode; you only set up what you have.

## What you get

| Part | Capabilities |
|---|---|
| main | `battery` (state of charge), `switch` (charging on/off), `powerMeter` (charging power) |
| Charging cable | `contactSensor`: closed = plugged in |
| Climate | `switch`: air conditioning on/off at the temperature from the settings |
| Car | `presenceSensor` (at the saved charging location), `contactSensor` (doors) |

Routine examples: *cable plugged in and battery below 30 % → start charging*, *weekday 7:15 → Climate on*, *Car not present → notification when a door is open*.

Settings on the car device (also on the bridge setup page): update interval (minutes, default 10) and climate temperature.

## Install

1. Install the bridge and the Edge driver: see [smartthings-stoeckie-bridge](https://github.com/Stoeckie/smartthings-stoeckie-bridge#1-bridge-on-windows).
2. In the MyŠkoda app (version 8.16 or newer): **Settings → Smart Home → API keys**, create a key for your car. It is shown once; keys expire (the app shows the date).
3. Enter the key and the VIN (17 characters, in the app and on the registration papers) in the **Škoda** section of the bridge setup page.
4. SmartThings app: **Add device → Scan nearby**. The car appears under the Stoeckie Bridge.

## Notes

* The API allows **20 requests per hour per car**. The bridge reads the car every 10 minutes and 30 s after a command (once more 60 s later when the change is not visible yet), so there is room for commands.
* The key only lives in `config.json` on the bridge pc.
* API documentation: [public.api.connect.skoda-auto.cz/docs](https://public.api.connect.skoda-auto.cz/docs).

## License

Apache 2.0. Not affiliated with Škoda Auto or Samsung SmartThings.
