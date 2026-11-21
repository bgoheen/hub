# Real Estate Hub: setup

Contacts, properties, pipeline, deal checklists and postcard farming in one page. It uses the same setup as the appraisal order tracker: a single HTML file on GitHub Pages, data saved to OneDrive, and Google Places address autocomplete.

## 1. Register the redirect URI in Azure (one time)

The hub reuses the order tracker's Microsoft app registration (client ID `89d0320b-597e-4405-8ccd-7beeb8e25566`), so its address has to be added as an allowed redirect.

1. Go to https://portal.azure.com, then **Microsoft Entra ID**, then **App registrations**
2. Open the registration with client ID `89d0320b-597e-4405-8ccd-7beeb8e25566`
3. **Authentication**: under *Single-page application*, click **Add URI**
4. Enter `https://bgoheen.github.io/hub` and **Save**

## 2. Open it

Visit https://bgoheen.github.io/hub and click **Connect OneDrive** at the bottom of the left menu.

## Data

Everything is saved to OneDrive at:

```
/RealEstateHub/hub_data.json
```

The first time you connect, the hub copies every contact from the old postcard tracker (`/RealEstateContacts/contacts_data.json`), including lanes, tiers, postcard months and card text. The old file is only read, never changed.

A copy is also kept in the browser so the page opens instantly. The hub re-reads OneDrive whenever the window comes back into focus, so edits made on another device show up.

OneDrive keeps version history for the file. To roll back: open OneDrive on the web, right-click `hub_data.json`, then **Version history**.

## Settings at the top of the script in index.html

- `APP_REDIRECT_URI`: must match the URL registered in Azure
- `HUB_PATH`: where the data file lives in OneDrive
- `TEMPLATES`: the standard seller and buyer checklists for new deals
- `LANES`, `TIERS`, `PROGRAM_START`: postcard lanes, how often each tier gets a card, and the first postcard month
