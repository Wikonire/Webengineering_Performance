# Webengineering_Performance

## Möglichkeiten zur Messung

| Kategorie        | Messziel / Regel                                                                                          | Testmöglichkeit                                                                                   | Typische Optimierungen                                                                 |
|------------------|-----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| **Load Goal**    | • Erste Reaktion ≤ 1s sichtbar (Titel, Hintergrund)<br>• Initial Load: ≤ 5s auf 3G, ≤ 1.5s auf schnellem Netz<br>• Subsequent Loads noch schneller | • Lighthouse (LCP, TTFB, FCP)<br>• WebPageTest (3G-Simulation)<br>• CI mit lighthouserc.json und Budgets | • Bilder optimieren (WebP/AVIF, Responsive Images)<br>• Caching & Service Worker<br>• Code-Splitting, Lazy Loading<br>• CDN für Assets |
| **Idling Goal**  | • JS-Tasks ≤ 50 ms<br>• Main Thread nicht blockieren                                                       | • Chrome DevTools → Performance Tab, Long Tasks<br>• Web Vitals → TBT                            | • Lange Tasks splitten<br>• requestIdleCallback oder Web Worker nutzen<br>• Code aufteilen, ungenutztes JS entfernen |
| **Animation Goal** | • 60fps → Frame ≤ 16.7 ms<br>• davon ca. 6 ms Render, max. 10 ms JS/Layout                               | • Chrome DevTools → Rendering FPS Monitor<br>• Lighthouse → „Avoid long main-thread tasks“        | • CSS-Animationen statt JS<br>• transform & opacity statt top/left ändern<br>• GPU-Beschleunigung nutzen |
| **Responsiveness** | • Feedback ≤ 50 ms (ideal)<br>• Bestätigung ≤ 100 ms<br>• Übergänge 100–200 ms<br>• Feedback bei >100 ms nötig | • Lighthouse (INP / FID)<br>• Web Vitals Extension (INP live)<br>• Playwright/Puppeteer Interaktions-Test | • Optimierte Event-Handler<br>• Debouncing/Throttling für Eingaben<br>• Visuelles Feedback (Spinner, Skeletons) |


* Bilder, Thumbnails optimieren
* Caching client oder Serverseitig
  * Client: wenig veränderliche Daten z.B. Logo
* Caching über header
* Obfuscation (Code "verkleinern/bundlen")
* Auswirkungen: Schon -400 ms verlierst du 10% 
* 
