# HelvetiDrone: Swiss Drone Pre-flight Dashboard

**Vibecoded by Eddie**

HelvetiDrone is a lightweight, single-file Progressive Web App (PWA) designed to give Swiss drone pilots a fast "Go/No-Go" status based on official data silos.

## The HelvetiDrone Philosophy: Safety by Design

This isn’t a "set it and forget it" tool. HelvetiDrone is built on the idea that the pilot—not the app—is the final authority. I’ve intentionally left out certain automations to keep the pilot in the loop and minimize the "false sense of security" that can lead to accidents or legal headaches.

### 1. No Auto-DABS Parsing (Check the Source)
I’ve intentionally kept Today’s and Tomorrow’s DABS as external links to Skybriefing. 
* **The Logic:** Scrapers can fail and APIs can lag. By forcing you to click through to the official PDF/map, I’m ensuring you’re seeing the absolute latest data directly from the source.
* **The Responsibility:** If I parsed it for you and missed a single NOTAM because of a script error, that’s on me. This way, the legal verification stays where it belongs: with the person holding the remote.

### 2. Surface-Level Weather Only
The wind and gust data is locked to 10m ground-level observations.
* **The Logic:** Providing high-altitude wind data (like 120m AGL) can give the dangerous impression that the "coast is clear" for high-altitude flights.
* **The Responsibility:** Mountain weather is unpredictable. If you’re flying at the ceiling, you need to be doing the math on Alpine gusts yourself. This app gives you the baseline; you provide the pilot's intuition.

### 3. Serverless & Privacy-First
The app is built to be "Serverless."
* **The Logic:** Your GPS coordinates and flight data never hit a private server of mine. The app communicates directly from your browser to official endpoints like `geo.admin.ch` and `open-meteo.com`.
* **The Benefit:** It’s lightning-fast, respects your privacy, and has no backend "middleman" that could go down or compromise your data.

### 4. Conservative "Go/No-Go" Logic
The status engine is built to be "grumpy."
* If wind hits **40 km/h** or gusts hit **50 km/h**, it turns Red.
* If there is even one airspace restriction within your radius, it turns Red.
* **The Logic:** It’s better to stay grounded because an app was too cautious than to crash because it was too optimistic.

### 5. Data Transparency
* **Airspace:** Pulled live from `geo.admin.ch` (BAZL).
* **Meteo:** ICON model data via Open-Meteo.
* **Status:** Every check is timestamped so you know exactly how old the info is.

**Bottom line:** Use this to get your bearings, but always verify with official Swiss sources before you take off.

---

**Dev Note:** This is a single-file PWA. To use it in the field, host it via GitHub Pages, open the URL on your phone, and "Add to Home Screen."

