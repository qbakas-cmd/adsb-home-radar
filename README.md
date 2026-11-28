<p align="center">
  <img src="Radar%20ADS-B_%20%C5%9Aledzenie%20lot%C3%B3w%20w%20czasie%20rzeczywistym.png" alt="ADS-B Home Radar: aircraft tracking and flight analytics banner" width="100%">
</p>

# ADS-B Home Radar 📡

**English** | [Polski](#polski)

A browser-based, full-screen ADS-B radar dashboard designed to work alongside [tar1090](https://github.com/wiedehopf/tar1090). It shows tracked aircraft relative to your receiver and keeps daily and historical statistics in the browser.

> **Community preview.** This is an early release. Test it on a local installation before relying on it. It is not an air-traffic-control or safety-critical system.

## Features

- Modern dark radar display with aircraft markers, trails, nearby towns, airports and a home marker.
- Independent radar scale (20 / 50 / 100 / 200 km) and detection/alert radius.
- Daily top-three rankings: highest, lowest, fastest, slowest and nearest aircraft.
- History for the last 7, 30 or 90 days, including daily records, detected flights, airlines, flight routes, flight headings and hourly traffic. Availability of airline and route information depends on external lookup services.
- Optional aircraft detail view, photos, flight routes, notifications and night mode.
- JSON archive export.

## Requirements

- A working ADS-B receiver with tar1090 installed on a local HTTP server.
- The tar1090-compatible aircraft feed at `data/aircraft.json` (or a custom path set in `config.js`).
- A modern desktop/tablet browser with JavaScript and localStorage enabled.
- Internet access for third-party flight route / aircraft-photo lookups; the radar feed itself can remain local.

## Install / Configuration

1. Copy `frame.html` and `config.js` to the same directory served by your tar1090 web server, or host them at a location that can access the aircraft feed on the same origin.
2. Open `config.js` and set your own `homeLat`, `homeLon` and `homeAltM`, plus `dataUrl` if necessary. The provided coordinates are **a public demonstration location in Katowice**, not the maintainer's home.
3. Open `frame.html` via **http(s)** on the server. Avoid opening it as a local `file://` URL.
4. Set the radar scale with the +/- buttons and detection radius from the **WYKRYWANIE** selector.
5. Open **Historia** to browse daily/weekly records or export your archive as JSON.

**Important:** A normal static website such as GitHub Pages does not automatically provide ADS-B data. You still need a feed accessible to the browser. When using a different origin, configure CORS or a same-origin reverse proxy.

## Data and privacy

- The application uses your configured receiver coordinates **in the browser** to calculate aircraft distance and position. Consider using an approximate location when sharing screenshots or the configuration file.
- By default, `config.js` contains public sample coordinates. **Do not commit your personalized config.js to a public repository.**
- Historical observations are stored in this browser's `localStorage`, not on GitHub or in a central database. History requires an open dashboard, and may be cleared with browser data.
- Archive entries are retained for at most 90 distinct recorded days. Older data must be exported manually.
- Aircraft photos and route/airline details may be fetched from third-party services, such as adsbdb.com and planespotters.net. Service response, browser policy and rate limits can affect completeness.
- Detection statistics count unique aircraft ICAO hex identifiers per day, not individual complete flights. Changing the alert radius during the day changes which observations are recorded.

## Known limitations

- The browser must remain open to collect observations.
- Historical route and airline statistics are incomplete when lookup data is unavailable.
- External services may be rate-limited or offline.
- Only static JavaScript syntax was checked before this preview; runtime behavior needs testing against a real tar1090 installation.
- The interface is currently Polish-first. English UI localization is planned.

## Project files

- `frame.html`: radar dashboard.
- `config.js`: **public example** receiver configuration. Change locally for deployment.
- `LICENSE`: MIT license for original contributions in this repository.
- `CHANGELOG.md`: release notes.

## Contributing

Bug reports, improvements, translations and pull requests are welcome. When reporting a problem, please remove private coordinates, receiver IP addresses, access tokens and any identifiable information from logs/screenshots.

---

## Polski

**ADS-B Home Radar** to ekran radaru ADS-B współpracujący z tar1090. Wyświetla samoloty na radarze, miasta i lotniska, oznacza miejsce odbiornika i prowadzi statystyki dzienne oraz historię do 90 dni.

**Instalacja:** skopiuj `frame.html` i `config.js` do katalogu dostępnego z serwera tar1090, ustaw w `config.js` współrzędne odbiornika i ewentualnie ścieżkę `dataUrl`, a następnie otwórz `frame.html` w przeglądarce.

**Ustawienia:** radar można skalować niezależnie od promienia wykrywania. Statystyki obejmują najniższy, najwyższy, najszybszy, najwolniejszy i najbliższy samolot oraz archiwum ze statystykami linii lotniczych i kierunków. Informacje o trasach zależą od baz zewnętrznych.

**Prywatność:** historia jest zapisywana lokalnie w przeglądarce. Nie publikuj własnych współrzędnych domu ani adresu odbiornika. Przykładowe współrzędne w repozytorium wskazują centrum Katowic. Bez otwartego panelu historia nie jest zbierana.

Projekt jest na etapie **community preview** i wymaga prób na rzeczywistym tar1090. Zgłoszenia błędów i propozycje zmian są mile widziane.

## License

MIT, see [LICENSE](LICENSE). Third-party services and related projects keep their own licenses.
