# twitch-adblock-updated

This repo maintains an updated version of the Twitch ad-blocking script originally created by [pixeltris](https://github.com/pixeltris/TwitchAdSolutions). The script works by intercepting Twitch's video worker and substituting an ad-free stream whenever ads are detected.

> **Recommended browser: Firefox.** uBlock Origin on Firefox uses Manifest V2, which supports full scriptlet injection. Chrome's Manifest V3 imposes restrictions that make this significantly harder to get working reliably.

---

## Installation (Firefox + Violentmonkey)

This is the recommended method. Violentmonkey runs the script with `document-start` timing, which ensures the worker hook is in place before Twitch creates its video workers.

### Steps

**1. Install Violentmonkey**

Install [Violentmonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/violentmonkey/).

**2. Open the script file**

Open `twitch-adblock.user.js` from this repo in any text editor. Press `Ctrl+A` then `Ctrl+C` to copy everything.

**3. Create a new userscript**

Click the Violentmonkey icon in your Firefox toolbar → click the **+** (New Script) button.

**4. Replace the contents**

Select all the placeholder text in the editor (`Ctrl+A`) and paste your copied script (`Ctrl+V`).

**5. Save**

Press `Ctrl+S` or click the save button. Violentmonkey will confirm the script is installed.

**6. Reload Twitch**

Go to twitch.tv and do a hard refresh (`Ctrl+Shift+R`). Ads should now be blocked.

---

## Verifying it works

Open Firefox on any Twitch stream, press **F12**, go to the **Console** tab, and run:

```javascript
window.twitchAdSolutionsVersion
```

- Returns `24` → script is active and working
- Returns `undefined` → script is not running, re-check the install steps above

---

## Updating the script

When a new version of `twitch-adblock.user.js` is available in this repo:

1. Open `twitch-adblock.user.js` and copy the full contents
2. Click the Violentmonkey icon → find the **Twitch AdBlock (vaft)** script → click **Edit**
3. Select all (`Ctrl+A`), paste the new version (`Ctrl+V`), save (`Ctrl+S`)

---

## Alternative: uBlock Origin

1. uBlock Origin dashboard → **Settings** → check **"I am an advanced user"** → click the gear icon
2. Set `userResourceLocation` to:
   ```
   https://raw.githubusercontent.com/Keian-A/twitch-adblock-updated/refs/heads/main/peronal-adsolutions.js
   ```
3. Go to **My filters** and add:
   ```
   twitch.tv##+js(twitch-videoad)
   ```
4. Click **Apply changes** and hard refresh twitch.tv

---

## Credits

Original script by [pixeltris](https://github.com/pixeltris/TwitchAdSolutions).
