# 🌬️ Breeze – ESPHome Indoor Air Quality Sensor

> Hobby project: DIY indoor air quality sensor based on ESP8266 + ESPHome

Breeze is a simple, modular DIY indoor air quality sensor designed for learning, experimentation, and seamless integration with Home Assistant. This is a **100% hobby project**, not a commercial product.

---

## ✨ Features

* Temperature, humidity and pressure measurement (BME280)
* Particulate matter measurement PM1.0 / PM2.5 / PM10 (PMS5003)
* Native Home Assistant integration via ESPHome API
* Over-the-air firmware updates (OTA)
* Ability to control PMS sensor (sleep/reset)
* Hardware design prepared for custom PCB

---

## 🧱 Hardware

| Component            | Model                                 |
| -------------------- | ------------------------------------- |
| MCU                  | Wemos D1 mini / D1 mini Pro (ESP8266) |
| Environmental sensor | BME280 (I²C)                          |
| Particulate sensor   | PMS5003 (UART)                        |
| Power supply         | USB 5V                                |

### Connections (target pinout for custom PCB)

#### BME280 (I²C)

| BME280 | D1 mini | GPIO             |
| ------ | ------- | ---------------- |
| VCC    | 3V3     | –                |
| GND    | GND     | –                |
| SCL    | D1      | GPIO5            |
| SDA    | D2      | GPIO4            |
| CSB    | 3V3     | –                |
| SDO    | GND     | – (address 0x76) |

#### PMS5003 (UART + control)

| PMS5003 | D1 mini              | GPIO   |
| ------- | -------------------- | ------ |
| VCC     | 5V                   | –      |
| GND     | GND                  | –      |
| TX      | D6                   | GPIO12 |
| RX      | D7                   | GPIO13 |
| SET     | D5                   | GPIO14 |
| RESET   | D0                   | GPIO16 |
| MOD     | 3V3 via 10k resistor | –      |
| PWM     | NC                   | –      |

---

## 🔌 Power Supply

* D1 mini powered via USB
* PMS5003 powered from 5V pin
* BME280 powered from 3.3V pin

Recommended:

* 470–1000 µF capacitor near PMS5003 power input
* 100 nF decoupling capacitors near BME280

---

## 🧠 Software

The project is based on **ESPHome**.

An example configuration can be found in:

```
firmware/breeze.yaml
```

You can compile and upload using:

* ESPHome add-on in Home Assistant
* or standalone ESPHome CLI

---

## 📂 Repository structure

```
breeze/
├── firmware/
│   └── breeze.yaml          # ESPHome configuration
├── hardware/
│   ├── schematics/          # KiCad schematics
│   └── pcb/                 # PCB files
├── docs/
│   ├── wiring.png           # Wiring diagram
│   └── photos/              # Prototype photos
└── README.md
```

---

## 🔐 Security

The project assumes usage of:

* ESPHome API encryption
* OTA password
* secrets stored in `secrets.yaml`

Passwords and encryption keys should **never be committed to the repository**.

---

## 📦 Project status

Project currently under active development:

* [x] Breadboard prototype
* [x] Pinout finalized for PCB
* [x] ESPHome integration
* [ ] First PCB revision
* [ ] Enclosure design
* [ ] Assembly documentation

---

## 📜 License

Hobby project for personal use, learning and experimentation.

You are free to copy, modify and build your own version — crediting the original project is always appreciated 🙂

---

## 🙌 Author

Created as a personal DIY / hobby project.

If you build your own version of Breeze — feel free to share, I’d love to see it! 🌬️
