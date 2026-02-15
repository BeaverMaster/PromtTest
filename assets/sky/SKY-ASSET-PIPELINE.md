# Sky Asset Pipeline — Apple Weather Reproduktion

Referenz: 7 Apple-Wetter-Screenshots (AppleBilder/)
Ziel: Realistische volumetrische Himmel-Hintergründe als WebP-Assets.

---

## 0. Referenzbild-Analyse (Pixel-Extraktion)

Exakte Farbwerte aus den 7 Apple-Screenshots, extrahiert per Eyedropper an
definierten Positionen (oben 10%, Mitte 50%, unten 90%).

### clear-day (Sylt)
- Oben: #a8d4f0 mit massivem warmem Bloom (#fffaf0 → #e8f4fc radialer Verlauf)
- Mitte: #56b0e6 brillantes mittleres Blau
- Unten: #bce2f6 aufgehelltes Eisblau durch atmosphärische Streuung
- Besonderheit: Sichtbare Lens Flares, Sun-Glow obere 30%, subtile Cirrus-Wisps
- Lichtrichtung: Oben-mittig, leicht links versetzt
- Farbtemperatur: Warm (6800K+)

### partly-day (Slovenska Bistrica)
- Oben: #89c4e0 pastelliges Blau mit zarten Schleierwolken
- Mitte: #a4d2ec entsättigtes Himmelblau, Wolken durchscheinend
- Unten: #cce6f5 hell, fast weiß-blau
- Besonderheit: Flache Schleierwolken, KEIN Cumulus, sehr zart und transparent
- Wolkentyp: Cirrostratus / hohe Schleierwolken
- Farbtemperatur: Neutral-kühl (6200K)

### partly-day-heavy (Telgte)
- Oben: #3a8cc4 tieferes Blau, teilweise von massiven Wolken verdeckt
- Mitte: #78b8dc mit großen volumetrischen Cumulus-Massen
- Unten: #96cce8 helleres Blau unter den Wolken
- Besonderheit: Massive 3D-Cumulus mit hellen Oberseiten (#e8eef2) und grauen Unterseiten (#a0aab4)
- Wolkentyp: Cumulus congestus, mehrere Schichten
- Farbtemperatur: Neutral (6000K)

### cloudy-day (England)
- Oben: #8a96a4 kühles desaturiertes Grau-Blau
- Mitte: #9eacb8 gleichmäßiges mittleres Grau
- Unten: #b8c4ce minimal heller, kaum Kontrast
- Besonderheit: Stratus-Decke, fast keine Texturvariation, extrem flach
- Wolkentyp: Stratus opacus, geschlossene Decke
- Farbtemperatur: Kalt (5200K)

### rain (München)
- Oben: #283440 sehr dunkles Blau-Grau, schwere Wolkenmasse
- Mitte: #3c5060 dunkles kaltes Grau-Blau
- Unten: #506a7a leicht aufgehellt durch Regen-Diffusion
- Besonderheit: Diagonale Regenstreifen (~105°), dichte Cumulonimbus oben
- Wolkentyp: Cumulonimbus mit Niederschlag
- Niederschlagseffekt: Dünne diagonale Streifen, leichter Dunst unten
- Farbtemperatur: Sehr kalt (4800K)

### snow (München-Variante)
- Oben: #6a809a mittleres Grau-Blau, weicher als Regen
- Mitte: #8ea4ba helles kühles Grau mit bläulichem Unterton
- Unten: #b0c4d4 aufgehellt (Bodenreflexion simuliert)
- Besonderheit: Weichere Wolken als Regen, höhere Grundhelligkeit, subtile Schneepunkte
- Wolkentyp: Nimbostratus, weich, gleichmäßig
- Farbtemperatur: Kalt (5000K)

### clear-night (New York)
- Oben: #080c18 fast schwarz, tiefes Navy
- Mitte: #141a3a dunkles Mitternachtsblau
- Unten: #221e4a warm-violetter Unterton (Mauve)
- Besonderheit: Subtile Wolkentextur als leicht hellere Wisps, kein Mond, keine Sterne
- Farbtemperatur: Kalt-Warm Übergang (Navy → Purple)

### cloudy-night (Hongkong)
- Oben: #0c1020 dunkler als clear-night Mitte
- Mitte: #1a2040 dunkles Navy mit sichtbaren Wolkenmassen
- Unten: #282a48 leicht wärmer, subtiler Ambient-Schein
- Besonderheit: Organische Wolkenformen als dunklere Silhouetten gegen etwas helleren Himmel
- Wolkentyp: Stratocumulus in mehreren Schichten
- Ambient Light: Wolken-Unterseiten leicht aufgehellt von unten
- Farbtemperatur: Kalt-Neutral (5400K)

---

## 1. Midjourney Prompts (v6.1)

Basis-Parameter für alle Varianten:
- Aspect Ratio: `--ar 16:9`
- Stylize: `--s 30` bis `--s 50` (niedrig für Realismus)
- Quality: `--q 2` (maximale Detailauflösung)
- Version: `--v 6.1`

### clear-day
Referenz: Sylt — brillanter blauer Himmel, massiver warmer Bloom oben-mittig

```
photorealistic sky only, looking straight up into clear blue sky, volumetric atmospheric scattering, massive warm sun glow at upper center bleeding outward into brilliant azure, extremely soft overexposed light bloom radiating from top, thin wispy cirrus clouds barely visible at mid-frame, subtle rainbow lens flare streaks radiating from light source, color transition from overexposed warm white through cerulean blue to pale ice blue at bottom edge, soft atmospheric haze throughout, luminous and airy, no horizon line, no ground, no landscape, no sun disc visible, no buildings, no mountains, 8k resolution, shot on Hasselblad H6D --ar 16:9 --s 40 --q 2 --v 6.1
```

### partly-day
Referenz: Slovenska Bistrica — zarte transparente Schleierwolken, pastellblau

```
photorealistic sky only, soft pastel blue sky, delicate thin cirrostratus clouds scattered across frame, clouds are translucent and wispy with no hard edges, gentle atmospheric diffusion throughout, very soft light from above, color palette pale cerulean blue transitioning to lighter powder blue at bottom, clouds appear as barely-there veils of white, no dense cloud masses, no cumulus, extremely gentle and serene atmosphere, slight atmospheric haze softening everything, no horizon line, no ground, no landscape, no buildings, no sun disc, 8k resolution, shot on Phase One IQ4 --ar 16:9 --s 40 --q 2 --v 6.1
```

### partly-day-heavy
Referenz: Telgte — massive volumetrische Cumulus-Wolken mit Tiefe

```
photorealistic sky only, large volumetric cumulus clouds occupying upper forty percent of frame, realistic cloud depth with brilliant white sunlit tops and subtle grey-blue undersides, deep saturated blue sky visible in gaps between cloud masses, multiple cloud layers at different altitudes creating atmospheric depth, distant clouds slightly blue-tinted from atmospheric perspective, foreground clouds have soft three-dimensional volume with light and shadow, bottom portion transitions to clearer lighter blue, no horizon line, no ground, no landscape, no buildings, no sun disc visible, 8k resolution, shot on Phase One IQ4 --ar 16:9 --s 50 --q 2 --v 6.1
```

### cloudy-day
Referenz: England — flache gleichmäßige Stratus-Bewölkung, grau-kühl

```
photorealistic overcast sky only, complete unbroken stratus cloud cover, flat uniform light grey cloud layer with extremely subtle texture variations, cool desaturated blue-grey color palette, perfectly diffused lighting with no visible light source direction, soft and even illumination throughout, very slight brightness increase toward bottom edge from atmospheric scattering, no blue sky visible, no breaks in cloud layer, no horizon, no ground, no landscape, no buildings, muted calm monotone atmosphere, minimal contrast, 8k resolution, shot on Hasselblad H6D --ar 16:9 --s 25 --q 2 --v 6.1
```

### rain
Referenz: München — schwere dunkle Cumulonimbus, sichtbarer Regen

```
photorealistic dramatic rain sky only, heavy dark cumulonimbus cloud mass filling upper half of frame, visible diagonal rain streaks falling at approximately 105 degrees through mid and lower frame, threatening dark grey-blue atmosphere, dense cloud mass with volumetric depth and internal darkness variation, cold desaturated color temperature, rain creating visible haze and reduced visibility in lower portion, atmospheric heavy and oppressive mood, rain streaks are thin semi-transparent white lines, no horizon, no ground, no landscape, no buildings, no lightning bolts, no rainbow, 8k resolution, cinematic --ar 16:9 --s 50 --q 2 --v 6.1
```

### snow
Referenz: München-Variante — kalt, weich, weniger bedrohlich als Regen

```
photorealistic winter snow sky only, thick soft nimbostratus clouds with cold blue-grey undertone, gentle diffused light filtering evenly through cloud layer, noticeably lighter and more luminous than rain clouds, subtle tiny snow particles visible as soft white dots scattered through frame, serene and cold atmosphere, high even cloud base with smooth soft texture, slight warm brightness increase at bottom edge suggesting ground snow reflection, no heavy darkness, no threatening mood, peaceful winter atmosphere, no horizon, no ground, no landscape, no buildings, 8k resolution, shot on Hasselblad H6D --ar 16:9 --s 35 --q 2 --v 6.1
```

### clear-night
Referenz: New York — tiefer Navy-Purple Nachthimmel

```
photorealistic deep night sky only, rich dark navy blue filling upper frame transitioning smoothly to subtle purple and mauve tones at lower edge, extremely faint cloud texture barely visible as slightly lighter blue-grey wisps at mid-frame, no moon visible, no stars visible, smooth continuous color gradients with absolutely no banding, deep peaceful atmospheric darkness, hint of warm purple-mauve undertone increasing toward bottom, very subtle atmospheric depth layering, no horizon, no ground, no landscape, no city lights, no buildings, no light pollution glow, 8k resolution, cinematic --ar 16:9 --s 25 --q 2 --v 6.1
```

### cloudy-night
Referenz: Hongkong — dunkle organische Wolkenmassen gegen Nachthimmel

```
photorealistic cloudy night sky only, dark organic cloud masses clearly visible as volumetric shapes against slightly lighter deep blue-grey sky behind, clouds appear as darker three-dimensional forms with very soft edges, subtle warm-cool undertone throughout, cloud layers at multiple depths creating layered darkness with parallax depth, faint ambient light from below gently illuminating cloud undersides with barely perceptible warmth, no moon, no stars visible through cloud cover, atmospheric and moody, dense but not threatening, no horizon, no ground, no landscape, no city lights, no buildings, 8k resolution, cinematic --ar 16:9 --s 35 --q 2 --v 6.1
```

---

## 2. Stable Diffusion Prompts (SDXL)

Model-Empfehlung: Juggernaut XL v9 oder RealVisXL V5.0
Sampler: DPM++ 2M Karras, 35 Steps, CFG 7
Resolution: 1344x768 (SDXL optimal für 16:9), dann Upscale auf 3072x1728

### clear-day
```
(photorealistic:1.3) sky only, looking up into clear blue sky, (volumetric atmospheric scattering:1.2), massive warm sun glow at upper center, (brilliant azure blue:1.1), extremely soft overexposed light bloom, thin wispy cirrus clouds, subtle lens flare streaks, color transition from overexposed warm white through cerulean to pale ice blue at bottom, luminous airy atmosphere, (no horizon:1.4), no ground, no landscape, no sun disc, atmospheric haze, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### partly-day
```
(photorealistic:1.3) sky only, soft pastel blue sky, (delicate cirrostratus clouds:1.1) scattered translucent, wispy no hard edges, gentle atmospheric diffusion, pale cerulean blue transitioning to lighter powder blue at bottom, clouds as barely-there white veils, no dense cumulus, serene atmosphere, (no horizon:1.4), no ground, no landscape, no buildings, no sun disc, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### partly-day-heavy
```
(photorealistic:1.3) sky only, large (volumetric cumulus clouds:1.2) upper portion, realistic cloud depth, brilliant white sunlit cloud tops, subtle grey-blue undersides, deep saturated blue sky between clouds, multiple cloud layers at different altitudes, atmospheric perspective, three-dimensional cloud volume, lighter blue at bottom, (no horizon:1.4), no ground, no landscape, no buildings, no sun disc, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### cloudy-day
```
(photorealistic:1.3) overcast sky only, complete (stratus cloud cover:1.2), flat uniform light grey, extremely subtle texture variations, cool desaturated blue-grey, perfectly diffused lighting, no visible light source, slight brightness at bottom edge, no blue sky visible, (no horizon:1.4), no ground, no landscape, no buildings, muted calm monotone, minimal contrast, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### rain
```
(photorealistic:1.3) dramatic rain sky only, (heavy dark cumulonimbus clouds:1.2) upper half, visible diagonal rain streaks at 105 degrees, threatening dark grey-blue, dense volumetric cloud mass, cold desaturated color, rain haze in lower portion, thin semi-transparent rain lines, oppressive atmospheric mood, (no horizon:1.4), no ground, no landscape, no buildings, no lightning, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### snow
```
(photorealistic:1.3) winter snow sky only, (thick soft nimbostratus clouds:1.2), cold blue-grey undertone, gentle diffused light, lighter and more luminous than rain, subtle tiny snow particles as soft white dots, serene cold atmosphere, high even cloud base, smooth soft texture, slight warm brightness at bottom, peaceful winter, (no horizon:1.4), no ground, no landscape, no buildings, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### clear-night
```
(photorealistic:1.3) deep night sky only, (rich dark navy blue:1.2) transitioning to subtle purple mauve at bottom, extremely faint cloud texture as lighter wisps, no moon, no stars, smooth color gradients no banding, deep peaceful atmospheric darkness, warm purple undertone at bottom, (no horizon:1.4), no ground, no landscape, no city lights, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

### cloudy-night
```
(photorealistic:1.3) cloudy night sky only, (dark organic cloud masses:1.2) against slightly lighter deep blue-grey sky, clouds as darker volumetric shapes with soft edges, warm-cool undertone, layered cloud depths with parallax, faint ambient light on cloud undersides from below, no moon, no stars, (no horizon:1.4), no ground, no landscape, no buildings, 8k, masterpiece, best quality, RAW photo, ultra detailed
```

---

## 3. Negative Prompts (universal für alle Varianten)

### Midjourney
```
--no horizon, ground, floor, landscape, earth, terrain, mountains, hills, trees, forest, water, ocean, sea, lake, buildings, city, skyline, architecture, roads, people, animals, birds, planes, aircraft, sun disc, moon disc, text, watermark, logo, frame, border, vignette dark corners, fish-eye distortion, lens distortion, chromatic aberration, noise grain, jpeg artifacts, posterization, banding, cartoon, illustration, painting, digital art, 3d render, anime, HDR tonemapping, oversaturated
```

### Stable Diffusion
```
horizon, ground, floor, landscape, earth, terrain, mountains, hills, trees, forest, water, ocean, sea, lake, river, buildings, city, skyline, architecture, roads, people, animals, birds, planes, aircraft, sun disc, moon disc, text, watermark, logo, frame, border, dark vignette, fish-eye, lens distortion, chromatic aberration, heavy noise, jpeg artifacts, posterization, color banding, cartoon, illustration, painting, digital art, 3d render, anime, drawing, sketch, low quality, blurry, deformed, ugly, duplicate, mutated, extra, missing, oversaturated, HDR tonemapping, tilt-shift
```

---

## 4. Post-Processing Workflow (Photoshop / Affinity Photo)

Jedes generierte Bild durchläuft exakt diese Schritte:

### Schritt 1: Crop und Skalierung
- Originalbild (3072x1728 oder größer) auf **2458x1382** croppen (Drift-Variante)
- Zweiter Export: Center-Crop auf **2048x1152** (Standard-Variante)
- Resampling: Bicubic Sharper (Photoshop) / Lanczos 3 (Affinity)

### Schritt 2: Farbkorrektur (allgemein)
- Levels: Input Schwarz auf **5** (verhindert reines Schwarz = Banding auf OLED)
- Levels: Input Weiß auf **250** (verhindert reines Weiß = Clipping)
- Curves: Leichte S-Kurve, Highlights **-3**, Shadows **+5**
- Hue/Saturation: Sättigung **+3** bis **+5** (kompensiert WebP-Chroma-Subsampling)

### Schritt 2b: Farbabgleich pro Variante

Jede Variante wird auf ihr Apple-Referenzbild abgeglichen:

| Variante | Colour Temp | Sättigung | Helligkeit | Schatten-Hue | Spezial |
|---|---|---|---|---|---|
| clear-day | +200K (wärmer) | +5 | 0 | — | Bloom-Bereich: Exposure +0.3 |
| partly-day | 0 (neutral) | 0 | 0 | — | — |
| partly-day-heavy | 0 | +3 | 0 | — | Wolken-Kontrast prüfen |
| cloudy-day | -150K (kühler) | -8 | 0 | — | — |
| rain | -400K (sehr kühl) | -12 | -5 | — | Regen-Streifen-Kontrast prüfen |
| snow | -200K (kühl) | -5 | +5 | — | — |
| clear-night | 0 | 0 | 0 | +15 (Purple) | Untere 30%: Mauve-Shift |
| cloudy-night | 0 | 0 | 0 | +8 (warm Navy) | Wolken-Ambient prüfen |

### Schritt 3: Anti-Banding
KRITISCH für Himmel-Gradienten auf 8-bit Displays und nach WebP-Kompression.

**Photoshop:**
1. Neue Ebene erstellen (Strg+Shift+N)
2. Ebene mit 50% Grau füllen (Edit > Fill > 50% Gray)
3. Filter > Noise > Add Noise: **0.8%**, Gaussian, Monochromatic
4. Ebenen-Modus: **Overlay**, Opacity **100%**
5. Auf Hintergrund reduzieren (Flatten)

**Affinity Photo:**
1. Live-Filter-Ebene: Add Noise, Intensity **0.8%**, Monochrome **On**
2. Flatten

**Warum Overlay statt Normal:**
Bei Normal wird der Noise gleichmäßig sichtbar. Overlay preserviert Lichter und Tiefen,
der Noise wirkt nur in Mitteltönen — exakt dort wo Banding entsteht.

### Schritt 4: Rand-Behandlung (nur Drift-Varianten, 2458x1382)

1. Select All → Select > Modify > Border: **80px**
2. Feather: **60px**
3. Filter > Blur > Gaussian Blur: **40px** auf Auswahl
4. Deselect

Ergebnis: Bildränder verlaufen weich in die Durchschnittsfarbe des Rands.
Bei 120% Skalierung und Drift-Animation ist der äußerste Rand nie im Viewport sichtbar.

### Schritt 5: Referenzvergleich

Für jede Variante:
1. Apple-Screenshot und generiertes Bild nebeneinander öffnen
2. **Farbstimmung**: Gleicher Gesamteindruck? (Warm/Kalt/Neutral)
3. **Helligkeitsverteilung**: Oben dunkler als Mitte? Unten aufgehellt?
4. **Wolkendichte**: Passt der Bedeckungsgrad?
5. **100% Zoom**: Kein sichtbares Banding?
6. **Ränder**: Kein harter Abschluss?
7. **iPhone-Test**: Im iOS Safari Simulator bei 390x844pt prüfen

---

## 5. Export und WebP Optimierung

### Zwischenformat
1. Photoshop: File > Export > Save for Web (Legacy), Format **PNG-24**, kein Interlacing
2. Affinity: File > Export, Format **PNG**, kein Metadata

### WebP Konvertierung (cwebp CLI)

Zwei Dateien pro Variante:

**Standard (2048x1152):**
```bash
cwebp -q 82 -m 6 -sharp_yuv -metadata none -resize 2048 1152 input.png -o clear-night.webp
```

**Drift (2458x1382):**
```bash
cwebp -q 80 -m 6 -sharp_yuv -metadata none -resize 2458 1382 input.png -o clear-day-drift.webp
```

### Parameter-Erklärung
- `-q 82` / `-q 80`: Quality 80–82 = Sweetspot für Himmel (kaum Unterschied zu 95, aber ~40% kleiner)
- `-m 6`: Maximale Kompressionseffizienz (langsamer Encode, kleinere Datei)
- `-sharp_yuv`: Verhindert Farbverschiebung bei Chroma-Subsampling (kritisch bei subtilen Gradienten)
- `-metadata none`: Keine EXIF-Daten (spart 2–5kb)

### Zielgrößen

| Variante | Standard (2048) | Drift (2458) | Bemerkung |
|---|---|---|---|
| clear-day | ~420kb | ~520kb | Bloom erhöht Komplexität |
| partly-day | ~350kb | ~440kb | Wenig Wolkendetail |
| partly-day-heavy | ~480kb | ~580kb | Maximale Wolkentextur |
| cloudy-day | ~320kb | ~420kb | Geringe Texturkomplexität |
| rain | ~380kb | ~480kb | Regenstreifen = Hochfrequenzdetail |
| snow | ~360kb | ~460kb | Schneepunkte = Hochfrequenzdetail |
| clear-night | ~280kb | ~360kb | Geringe Farbvariation |
| cloudy-night | ~340kb | ~430kb | Moderate Wolkentextur |

**Gesamt (nur Drift):** ~3.7 MB für alle 8 Varianten.
**Gesamt (nur Standard):** ~2.9 MB für alle 8 Varianten.

### Banding-Test nach Export
```bash
# ImageMagick: Posterize auf 32 Stufen um Banding sichtbar zu machen
magick clear-night.webp -posterize 32 clear-day-banding-test.png
```
Wenn harte Streifen sichtbar → Noise-Schritt mit **1.2%** statt 0.8% wiederholen.

### Batch-Konvertierung (alle Varianten)
```bash
#!/bin/bash
VARIANTS="clear-day partly-day partly-day-heavy cloudy-day rain snow clear-night cloudy-night"
for v in $VARIANTS; do
    cwebp -q 82 -m 6 -sharp_yuv -metadata none -resize 2048 1152 "src/${v}.png" -o "${v}.webp"
    cwebp -q 80 -m 6 -sharp_yuv -metadata none -resize 2458 1382 "src/${v}.png" -o "${v}-drift.webp"
    echo "OK: ${v}"
done
```

---

## 6. Drift-Animation Strategie

### Warum 120% Skalierung

Das Hintergrundbild wird mit `background-size: 120% 120%` dargestellt.
Das ergibt einen Overscan von 10% auf jeder Seite.

```
+---------- 120% Bildbreite -----------+
|  10%  |---- 100% Viewport ----|  10% |
|  Rand |      sichtbar         | Rand |
+--------------------------------------+
```

Die CSS-Animation verschiebt das Bild um maximal 10% in jede Richtung.
Da der Overscan exakt 10% beträgt, ist der Bildrand NIE sichtbar.

### CSS-Implementation

```css
.sky-bg {
    position: absolute;
    inset: 0;
    background-size: 120% 120%;
    background-position: center center;
    background-repeat: no-repeat;
    opacity: 0;
    transition: opacity 1.4s ease;
    animation: skyDrift 80s ease-in-out infinite alternate;
    will-change: background-position;
}

.sky-bg.sky-bg-loaded {
    opacity: 1;
}

@keyframes skyDrift {
    0%   { background-position: 45% 45%; }
    25%  { background-position: 55% 48%; }
    50%  { background-position: 52% 55%; }
    75%  { background-position: 48% 52%; }
    100% { background-position: 45% 45%; }
}
```

### Warum background-position statt transform

- `transform: translate()` promoted das Element in einen eigenen GPU-Layer
- Der GPU-Layer hat Tile-Grenzen die bei Bewegung sichtbar werden können
- `background-position` animiert innerhalb des bestehenden Paint-Layers
- Kein neuer Compositing-Layer = keine Tile-Nähte
- Tradeoff: background-position triggert Repaint statt nur Composite
- Bei 80s Animationsdauer (~0.0125 Positionsänderungen/Frame) ist der Repaint-Cost vernachlässigbar

### Rand-Behandlung im Bild

Die äußersten 80px jeder Drift-Variante sind per Gaussian Blur verwischt.
Bei 120% Skalierung auf einem 390px breiten iPhone-Display:
- 10% Overscan = 39px sichtbarer Overscan
- 80px Quellbild ÷ (120% Skalierung) = ~47px am Display
- Die verwischte Zone liegt komplett außerhalb des Viewports

### Keine Parallax-Fehler

Die Animation verwendet `ease-in-out` und `alternate`:
- An den Umkehrpunkten verlangsamt die Bewegung
- Kein abrupter Sprung
- Die Richtung wechselt sanft
- 80s Dauer = unmerklich langsame Bewegung (~3% sichtbare Verschiebung)

---

## 7. Preloading und Lade-Strategie

### Initiales Preloading (HTML)

Nur das wahrscheinlichste Bild per `<link>` preloaden:
```html
<link rel="preload" href="assets/sky/clear-day-drift.webp" as="image" type="image/webp">
```

### JavaScript Lazy-Loading

Nach Wetterdaten-Empfang das passende Bild laden, Rest im Hintergrund:

```javascript
// Aktives Bild laden
function loadSkyAsset(variant) {
    return new Promise(function(resolve, reject) {
        var img = new Image();
        img.onload = function() { resolve(variant); };
        img.onerror = function() { reject(variant); };
        img.src = 'assets/sky/' + variant + '-drift.webp';
    });
}

// Alle Varianten im Hintergrund vorladen (nach Initial-Load)
function preloadAllSkyAssets() {
    var variants = ['clear-day','partly-day','partly-day-heavy','cloudy-day','rain','snow','clear-night','cloudy-night'];
    for (var i = 0; i < variants.length; i++) {
        var img = new Image();
        img.src = 'assets/sky/' + variants[i] + '-drift.webp';
    }
}
```

### Lade-Reihenfolge
1. CSS-Gradient wird sofort sichtbar (Fallback)
2. WebP-Bild lädt im Hintergrund
3. Nach Load: `sky-bg` bekommt `sky-bg-loaded` Klasse → opacity: 0 → 1 (1.4s fade)
4. CSS-Gradient bleibt unter dem Bild als permanenter Fallback

### WebP Support Check

WebP wird von allen modernen Browsern unterstützt (iOS 14+, Chrome 32+, Firefox 65+).
Kein Feature-Check nötig. Der CSS-Gradient als Fallback deckt Edge-Cases ab.

---

## 8. Mapping: Weather Code → Sky-Variante

| WMO Code | Zustand | Sky-Variante (Tag) | Sky-Variante (Nacht) |
|---|---|---|---|
| 0 | Klar | clear-day | clear-night |
| 1 | Überwiegend klar | clear-day | clear-night |
| 2 | Teilweise bewölkt | partly-day | cloudy-night |
| 3 | Bewölkt | cloudy-day | cloudy-night |
| 45, 48 | Nebel | cloudy-day | cloudy-night |
| 51–57 | Nieselregen | rain | rain |
| 61–67 | Regen | rain | rain |
| 71–77 | Schnee | snow | snow |
| 80–82 | Regenschauer | rain | rain |
| 85–86 | Schneeschauer | snow | snow |
| 95–99 | Gewitter | rain | rain |

Für `partly-day-heavy`: Wird bei WMO Code 2 verwendet wenn `wind_speed > 15 km/h`
oder `precipitation_probability > 40%` (deutet auf aktive Wetterlage mit entwickelten Wolken hin).

---

## 9. Dateistruktur

```
assets/sky/
├── SKY-ASSET-PIPELINE.md          (dieses Dokument)
├── clear-day-drift.webp            (2458x1382, Drift-Variante)
├── clear-day.webp                  (2048x1152, Standard)
├── partly-day-drift.webp
├── partly-day.webp
├── partly-day-heavy-drift.webp
├── partly-day-heavy.webp
├── cloudy-day-drift.webp
├── cloudy-day.webp
├── rain-drift.webp
├── rain.webp
├── snow-drift.webp
├── snow.webp
├── clear-night-drift.webp
├── clear-night.webp
├── cloudy-night-drift.webp
├── cloudy-night.webp
└── src/                            (Quell-PNGs, nicht im Repo)
    ├── clear-day.png
    ├── partly-day.png
    └── ...
```
