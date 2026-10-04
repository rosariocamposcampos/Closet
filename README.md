# Closet

Your wardrobe, photographed and styled, in a terracotta and soft marble design. Upload your clothes, and Closet scans each piece (cuts it out of the background, reads its colors and pattern, and guesses what it is). Then it builds outfits for the occasion, the weather and your taste.

Everything runs in the browser. There is no server, no AI service and no account to pay for.

## What it does

- **Closet:** Upload photos and each piece is scanned on your device (cut out, colors, pattern, type). Mark pieces as **in the laundry** and outfits skip them until you bring them back.
- **Outfits:** **Today** builds outfits for an occasion and the weather. Swipe right to wear, left to pass and say what to change. Switch between a **Collage** and a **Mannequin** view, where your pieces are dressed on a drawn figure.
- **My week:** Plans seven days at once and spreads your pieces out so you don't repeat a top two days running.
- **A trip:** Plans every day of a trip using the destination's forecast, reuses bottoms, shoes and layers so you pack less, and builds a **packing list** you can tick off.
- **Journal:** Tap **Wore this today** and it is logged. The stylist avoids repeating recent outfits. The Journal also shows **forgotten pieces** you haven't worn in a while and **closet gaps**: pieces that would unlock the most new outfits.
- **Inspiration:** Add Pinterest pins. Together with your **outfit photos** and what you wear most, they build your style profile, which shapes every outfit.
- **Liked:** Save outfits you love, or **add a photo of an outfit you already wore**. The app matches the photo to pieces in your closet, you confirm them, and the stylist learns from it.

Nothing uses AI: the scanner, the stylist and the mannequin are all rules and image analysis that run in your browser.

## What is in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.webmanifest` | Lets your phone install it like an app |
| `icon-180.png`, `icon-512.png` | The app icon |
| `README.md` | This guide |
| `CUSTOMIZE.md` | How to change colors, fonts, styles, occasions and how the stylist thinks |



## How your data is saved (important)

Closet saves everything **in the browser you use it in**: your account, your clothes, your photos, your pins and your liked outfits. It uses the browser's built-in database (IndexedDB), which has room for photos. Loom used a smaller kind of storage that photos would not fit in.

What that means:

- It is private. Nothing is uploaded anywhere.
- Your laptop and your phone keep **separate** closets.
- Clearing your browser's website data erases it.

**To move your closet between devices, or to keep a safe copy:**

1. On the device that has your closet, open **Backup and settings** (bottom of the sidebar), then click **Download backup**. You get one file with everything, including the photos.
2. Send that file to the other device. AirDrop, email or Google Drive all work.
3. On the other device, sign in (or create the same account), open **Backup and settings**, then **Restore from backup**, and pick the file.

Download a fresh backup every so often, especially after adding a lot of clothes.

## Weather

On the **Outfits** page, **Use location** fills in today's forecast automatically, using the free Open-Meteo service. **My week** can fill in seven days at once, and **A trip** looks up the forecast for your destination (forecasts reach up to 16 days ahead). Your browser asks for permission the first time. You can always set the weather by hand instead.

## Getting the best scans

- Photograph **one piece per photo**, laid flat or on a hanger.
- Use a **plain background**. Light clothes scan best on a darker surface, and dark clothes on a light one.
- If the background cannot be removed, the app uses your whole photo instead. You can still use the piece normally.
- Always check the type and style before saving. The style you choose (blazer, sneakers, slip dress and so on) tells the stylist how dressy and how warm the piece is.
