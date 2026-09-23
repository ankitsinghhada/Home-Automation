# Raspberry Pi Home Automation

A Raspberry Pi GPIO control project that connects physical household devices to Adafruit IO. The Python program polls four Adafruit IO feeds and switches a motor, bulb, light, and socket through relay-connected GPIO pins.

## Features

- Remote control of four relay channels through Adafruit IO
- Independent on/off handling for a motor, bulb, light, and socket
- Raspberry Pi GPIO output control using BCM pin numbering
- One-second polling interval for near real-time state updates
- Simple function-based device controls that are easy to extend

## Hardware Mapping

| Device | GPIO pin | Feed |
| --- | ---: | --- |
| Motor | 18 | `relay-1` |
| Bulb | 23 | `relay-2` |
| Light | 24 | `relay-3` |
| Socket | 20 | `relay-4` |

The relay commands currently used by the script are `1`/`0` for the motor, `ON`/`OFF` for the bulb, `Lon`/`Lof` for the light, and `Son`/`Sof` for the socket.

## How It Works

1. The application configures the Raspberry Pi GPIO pins as outputs.
2. It authenticates with Adafruit IO.
3. It reads each relay feed once per loop.
4. It maps feed values to relay output states.
5. It waits one second and repeats.

## Requirements

- Raspberry Pi with compatible relay hardware
- Python 3
- Adafruit IO account and feed configuration
- `RPi.GPIO` and `Adafruit_IO` Python packages
- Network access from the Raspberry Pi

Install the Python dependencies with:

```bash
pip install RPi.GPIO adafruit-io
```

Run the controller with:

```bash
python3 main.py
```

## Security and Safety

The original script contains an Adafruit IO credential. Rotate that credential immediately and move the replacement to environment variables or a local, ignored configuration file before running or sharing this project. Never commit service keys to GitHub.

Because this project controls physical devices, test with disconnected loads first, use correctly rated relays, and add fault handling before unattended deployment.

## Project Materials

- `main.py`: GPIO and Adafruit IO control loop
- `SMART HOME.pdf`: project documentation
- `ENGINEERING CLINICS.pdf`: supporting project material