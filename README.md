<div align="center">

![GOSTIN LED LAMP — вовк, місяць і дерево](assets/gostin-led-banner.svg)

# GOSTIN LED LAMP

**LIGHT · MUSIC · AUTOMATION**

Розумне освітлення на **ESP8266 + WS2812B** з Android-застосунком, локальним Web UI та світломузикою.

[![ESP8266](https://img.shields.io/badge/ESP8266-v7.5.18-14532d?style=for-the-badge)](https://github.com/Gostin0/Led-Lamp/releases/tag/1.4.7)
[![Android](https://img.shields.io/badge/Android-v1.4.7-166534?style=for-the-badge)](https://github.com/Gostin0/Led-Lamp/releases/tag/1.4.7)
[![WS2812B](https://img.shields.io/badge/LED-WS2812B-15803d?style=for-the-badge)](https://github.com/Gostin0/Led-Lamp)

[**⬇ Завантажити актуальну версію**](https://github.com/Gostin0/Led-Lamp/releases/tag/1.4.7) · [**📝 Історія змін**](CHANGELOG.md) · [**🐞 Повідомити про проблему**](https://github.com/Gostin0/Led-Lamp/issues)

</div>

---

## Про проєкт

**GOSTIN LED LAMP** — система локального керування адресною LED-стрічкою: біле освітлення, декоративні й аудіореактивні ефекти, автоматичне світло та будильники. У звичайному режимі працює локально через Wi-Fi, без хмарного сервера.

### Поточний офіційний реліз

| Компонент | Версія / статус |
|---|---|
| Прошивка ESP8266 | **7.5.18-BOOT-SCAN-RC1** |
| Android | **1.4.7** (`versionCode 1407`) |
| Web UI | Forest Glass із OTA-пакета Android 1.4.7 / ESP 7.5.18 |
| Випуск | [GitHub Release `1.4.7`](https://github.com/Gostin0/Led-Lamp/releases/tag/1.4.7) |

> [!NOTE]
> **Forest Glass** входить до Web-файлів комплекту 1.4.7. Це оновлення інтерфейсу ще потребує повної апаратної перевірки, особливо під навантаженням ESP8266; повне фізичне OTA-тестування опублікованого пакета не заявляється.

## Можливості

| Розділ | Що доступно |
|---|---|
| 💡 Освітлення | ON/OFF без зупинення Wi-Fi, режим **White Light**, яскравість, температура білого |
| 🎨 Ефекти | Декоративні й музичні анімації, швидкість, кольори та індивідуальні профілі |
| 🎵 Аудіо | Мікрофон ESP8266, PHONE MIC, AUDIO CAPTURE, передавання звуку через UDP |
| 🌙 SMART LIGHT | Вечірній/нічний режими, звукова активація, таймер тиші, анімація та реверс |
| ⏰ Будильники | До чотирьох світлових будильників із розкладом і плавним увімкненням |
| 📱 Android | Керування лампою, ефектами, звуком, SMART LIGHT, будильниками та системою |
| 🌐 Web UI | Український вебінтерфейс, параметри, LittleFS і Wi-Fi Setup |
| 🔧 Обслуговування | OTA, Recovery на порту **81**, налаштування мережі |

**Quick Settings Tile (Android 1.4.7):** плитка в шторці перемикає лампу; під час увімкнення вибирає **White Light**. Якщо лампа вже увімкнена, перше натискання її вимикає.

**Wi-Fi BOOT SCAN (ESP 7.5.18):** список до 12 мереж формується **один раз при запуску** ESP та читається Android і Wi-Fi Setup із кешу. Для оновлення списку перезавантаж ESP8266; натискання «Знайти Wi-Fi» не запускає нове радіосканування.

**Вилучені можливості:** SHOW Studio та XM Player не входять до поточного комплекту.

**Android 1.4.7:** виправлено Wi-Fi-вікно (прокрутка, компактні секції, доступне збереження з відкритою клавіатурою) і вбудовано актуальний Forest Web у відновлення LittleFS.

## 🔌 Схема підключення

![GOSTIN LED LAMP — схема підключення ESP8266, MAX4466, WS2812B та DC Jack](assets/gostin-led-wiring.jpg)

[Відкрити схему у повному розмірі](assets/gostin-led-wiring.jpg)

| Вузол | Підключення |
|---|---|
| **MAX4466 OUT** | ESP8266 **A0** |
| **MAX4466 VCC / GND** | ESP8266 **3V (3,3 В)** / **GND** |
| **WS2812B DIN** | ESP8266 **D4 / GPIO2** |
| **WS2812B 5V / GND** | Зовнішнє **+5 В / GND** через DC Jack 5.5 × 2.1 мм |
| **ESP8266 VU / GND** | Лінія **+5 В / GND** на схемі |
| **Спільна земля** | GND блока живлення, LED-стрічки, ESP8266 і MAX4466 об’єднані |

> [!CAUTION]
> **Живлення:** для 259 WS2812B потрібен блок 5 В із запасом струму відповідно до реального ліміту яскравості. Не живи LED-стрічку через GPIO або 3,3-вольтовий вихід ESP. На платах NodeMCU позначення **VU/VIN** і схема живлення від USB можуть відрізнятися: перевір саме свою ревізію плати та захист від зворотного живлення USB перед одночасним підключенням зовнішніх 5 В і комп’ютера. Для довгої стрічки врахуй падіння напруги й необхідність додаткових точок подавання живлення.

## Завантаження

Завантажуй інсталяційні файли **з Releases**, а не з автоматичного архіву вихідного коду GitHub.

| Файл | Призначення |
|---|---|
| [`LED-Lampa.apk`](https://github.com/Gostin0/Led-Lamp/releases/download/1.4.7/LED-Lampa.apk) | Підписаний Android v1.4.7 |
| [`esp-release.zip`](https://github.com/Gostin0/Led-Lamp/releases/download/1.4.7/esp-release.zip) | Firmware, OTA-маніфест і сім файлів Web/Wi-Fi Setup (Forest Web із `forest.jpg`) |
| [`SHA256SUMS.txt`](https://github.com/Gostin0/Led-Lamp/releases/download/1.4.7/SHA256SUMS.txt) | Контрольні SHA-256 |

> [!IMPORTANT]
> Перед оновленням ESP збережи налаштування, перевір доступ до Recovery та не вимикай живлення під час OTA. Для встановлення нового APK **поверх попереднього** потрібен той самий сертифікат підпису і вищий `versionCode`.

### Початок роботи

1. Встанови `LED-Lampa.apk` із поточного релізу.
2. Налаштуй Wi-Fi лампи (за потреби під’єднайся до точки доступу `LED_LAMP`).
3. Відкрий Android або локальний Web UI та налаштуй світло, ефекти й SMART LIGHT.
4. Для оновлення ESP використовуй сумісний OTA-пакет і засоби Recovery.

## Історія релізів

| Реліз | ESP8266 | Головна тема | Опис |
|---|---|---|---|
| [**Android 1.4.7**](https://github.com/Gostin0/Led-Lamp/releases/tag/1.4.7) | **7.5.18** | Wi-Fi-вікно, Forest Web, BOOT SCAN і White Light у шторці | [Деталі](release-notes/1.4.7.md) |
| [Android 1.3.0](https://github.com/Gostin0/Led-Lamp/releases/tag/1.3.0) | 7.5.15 | SMART LIGHT, будильники, анімація | [Деталі](release-notes/1.3.0.md) |
| [Android 1.2.0](https://github.com/Gostin0/Led-Lamp/releases/tag/v1.2.0) | 7.5.0-WEB-DEV1 | Попередня тестова Web/Android інтеграція | [Деталі](release-notes/v1.2.0.md) |

Збірка **Android 1.4.6** була проміжною версією: [історія змін](release-notes/1.4.6.md). Окремого GitHub Release із тегом `1.4.6` зараз немає.

У кожного опублікованого релізу **свій OTA-пакет**; не змішуй APK та `esp-release.zip` з різних версій.

Докладніше — [CHANGELOG.md](CHANGELOG.md). Архівний опис [Android 1.3.0](RELEASE_NOTES_v1.3.0.md).

## Архітектура

```mermaid
flowchart LR
    A[Android] <-->|HTTP / Wi-Fi| E[ESP8266]
    W[Web UI / LittleFS] <-->|HTTP| E
    P[PHONE MIC / AUDIO CAPTURE] -->|UDP| E
    M[ESP MIC / A0] --> E
    E -->|FastLED| L[WS2812B]
    G[GitHub Releases] -->|APK / OTA packages| A
```

---

<div align="center">

**GOSTIN LED LAMP — LIGHT · MUSIC · AUTOMATION**

</div>
