# Vinyl Recognizer

Prosty rozpoznawacz muzyki z gramofonu oparty na ESP32-S3.  
Urządzenie nagrywa fragment utworu, wysyła go do AudD API i wyświetla tytuł, artystę oraz album na ekranie e-paper.

## Funkcje

- Rozpoznawanie muzyki przez AudD API
- Wyświetlanie wyniku na 4,2" e-paper
- Automatyczne łączenie z WiFi (WiFiManager)
- Obsługa błędów (brak sieci, błąd mikrofonu, brak rozpoznania)
- Nagranie co 2 minuty (konfigurowalne)

## Wymagane części

| Część | Uwagi |
|-------|-------|
| ESP32-S3 DevKitC-N16R8 | 8 MB PSRAM + 16 MB Flash |
| E-paper 4,2" (GxEPD2_420_GDEY042T81) | Waveshare lub kompatybilny |
| Mikrofon INMP441 (I2S) | |
| Przewody + zasilanie | |

## Podłączenie

### E-paper
| Pin e-paper | GPIO ESP32-S3 |
|-------------|---------------|
| CS          | 10            |
| DC          | 13            |
| RST         | 14            |
| BUSY        | 9             |
| SCK (SCL)   | 12            |
| MOSI (SDA)  | 11            |
| VCC         | 3.3V          |
| GND         | GND           |

### Mikrofon INMP441
| Pin mikrofonu | GPIO ESP32-S3 |
|---------------|---------------|
| WS            | 16            |
| SCK           | 15            |
| SD            | 17            |
| VDD           | 3.3V          |
| GND           | GND           |

## Wymagane biblioteki

W Arduino IDE (Library Manager):

- GxEPD2
- Adafruit GFX
- WiFiManager

## Konfiguracja

1. W pliku `.ino` wstaw swój token AudD:
   ```cpp
   const char* AUDD_TOKEN = "TWOJ_TOKEN";