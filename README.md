# LocoNet-Pico Servoboard

LocoNet-Modul mit Raspberry Pi Pico für 16 Servos (J12–J27).
KiCad-Projekt, Schaltplan als PDF und Fertigungsdaten liegen in [`loconet-pico/`](loconet-pico/).

## LocoNet-Anbindung

- **Empfang:** Transistor-Eingangsstufe statt Spannungsteiler.
  R3 47k / R7 10k an Q3 (BC337) ergeben eine Schaltschwelle von ca. 3,4–4 V
  (logisch „1“ ab 4 V wird sicher erkannt),
  Q4 invertiert zurück (Leitung High = RX High), keine Invertierung in der Firmware nötig.
  Last am Bus ≥ 47 kΩ.
- **Senden:** Q1 (BC557) / Q2 (BC337) ziehen die Leitung über D1 (1N5818) auf Masse.
- **Schutz:** TVS-Diode D3 (P6KE18CA) am LocoNet, nah an J9/J10.

## Stromversorgung

Die Servos brauchen externe 5 V über J11. USB reicht nur zum Testen mit 1–2 Servos.
GND von Pico und externer Quelle verbinden.
