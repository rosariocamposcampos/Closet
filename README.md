# Closet

Your wardrobe, photographed and styled, in a terracotta and soft marble design. Upload your clothes, and Closet scans each piece (cuts it out of the background, reads its colors and pattern, and guesses what it is). Then it builds outfits for the occasion, the weather and your taste.

Everything runs in the browser. There is no AI service and nothing to pay for. Turn on the free **sync** (see `SYNC-SETUP.md`) to sign in with your email on any device and see the same closet.

## What it does

- **Closet:** Upload photos and each piece is scanned on your device (cut out, colors, pattern, type). **Sweaters** have their own type: thick and thin sweaters, cardigans and sweater vests can be layered over tops, and turtlenecks make a base for other layers. Mark pieces as **in the laundry** and outfits skip them until you bring them back.
- **Outfits:** **Today** builds outfits for an occasion and the weather. Swipe right to wear, left to pass and say what to change.
- **Finish the look:** After choosing an outfit, add or swap a **jacket**, layer a **sweater**, **change your shoes** and pick **accessories**, all ranked for that outfit and the weather.
- **My week:** Plans seven days at once and spreads your pieces out so you don't repeat a top two days running.
- **A trip:** Plans every day of a trip using the destination's forecast, reuses bottoms, shoes and layers so you pack less, and builds a **packing list** you can tick off.
- **Journal:** Tap **Wore this today** and it is logged. The stylist avoids repeating recent outfits. The Journal also shows **forgotten pieces** you haven't worn in a while and **closet gaps**: pieces that would unlock the most new outfits.
- **Inspiration:** Add Pinterest pins. Together with your **outfit photos** and what you wear most, they build your style profile, which shapes every outfit.
- **Learns your style:** Every like, worn outfit, outfit photo and pass teaches it the colors, pieces, combinations and moods you love and the ones you skip. Tap **Not my style** to steer it away from a look, or write things like "no yellow, more navy". See what it has learned at the bottom of the Inspiration page.
- **Liked:** Save outfits you love, or **add a photo of an outfit you already wore**. The app matches the photo to pieces in your closet, you confirm them, and the stylist learns from it.

Nothing uses AI: the scanner, the photo polish and the stylist are all rules and image analysis that run in your browser.

## What is in this folder

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `manifest.webmanifest` | Lets your phone install it like an app |
| `icon-180.png`, `icon-512.png` | The app icon |
| `README.md` | This guide |
| `CUSTOMIZE.md` | How to change colors, fonts, styles, occasions and how the stylist thinks |
| `SYNC-SETUP.md` | How to turn on sync so your closet follows you across devices |

## Put it online with GitHub Pages (free)

1. Go to **https://github.com/new**. Name the repository `closet`, set it to **Public**, and click **Create repository**.
2. On the new repo page, click **uploading an existing file**.
3. Drag in **all the files** (`index.html`, `manifest.webmanifest`, `icon-180.png`, `icon-512.png`, `README.md`, `CUSTOMIZE.md`, `SYNC-SETUP.md`). They must sit at the top level of the repo, not inside a folder. Click **Commit changes**.
4. Go to **Settings**, then **Pages** in the left sidebar.
5. Under **Build and deployment**, set **Source** to *Deploy from a branch*, **Branch** to `main` and the folder to `/ (root)`. Click **Save**.
6. Wait about a minute, then refresh the Pages screen. Your link appears at the top:

   **https://rosariocamposcampos.github.io/closet/**

### Updating the site later

1. Make your changes to `index.html` on your computer.
2. In the repo, click **Add file**, then **Upload files**, drag in the new `index.html` and click **Commit changes**. It replaces the old one.
3. Wait about a minute, then hard-refresh the site (**Cmd+Shift+R** on Mac, **Ctrl+Shift+R** on Windows) so your browser doesn't show the old cached version.

## Put it on your phone like an app

Open your GitHub link on your phone.

- **iPhone (Safari):** tap the Share button, then **Add to Home Screen**.
- **Android (Chrome):** tap the menu, then **Add to Home screen** or **Install app**.

It opens full screen with its own icon.

## How your data is saved

**With sync turned on (recommended):** follow `SYNC-SETUP.md` once. Then you sign in with your email, and your clothes, photos, outfits, pins, journal and everything the stylist has learned are saved to your private account. Open the site on any phone or computer, sign in, and it's all there. Changes save automatically and work offline too.

**Without sync:** everything is saved only in the browser you use. Your laptop and phone keep separate closets, and clearing the browser's website data erases it. To move it, open **Colors, backup and settings** (or the ⚙ button on a phone), **Download backup**, send the file to the other device and **Restore from backup** there.

Either way, download a backup now and then as a safe copy.

## Weather

On the **Outfits** page, **Use location** fills in today's forecast automatically, using the free Open-Meteo service. **My week** can fill in seven days at once, and **A trip** looks up the forecast for your destination (forecasts reach up to 16 days ahead). Your browser asks for permission the first time. You can always set the weather by hand instead.

## Getting the best scans

- Photograph **one piece per photo**, laid flat or on a hanger. Flat lays give the cleanest cutouts.
- Every cutout is **polished** automatically: colors are corrected when you shoot on a white or light grey surface, edges are smoothed, small tilts are straightened, and every piece is framed the same way. For pieces added before this feature, open **Colors, backup and settings** and tap **Polish photos**.
- Add the **back** of a piece when you upload it (**Add back**) or later from its details (**Add the back**). Hover over a piece in your closet to see its back.
- Use a **plain background**. Light clothes scan best on a darker surface, and dark clothes on a light one.
- Photos of clothes you're wearing (like mirror selfies) work too. The app finds the piece by its color, and you choose the type yourself.
- If a cutout looks wrong, tap **Fix cutout** (when adding) or **Fix the cutout** (on a saved piece). The outline the app found appears as dots: **drag a dot** to move it, **tap the line** to add a dot, **double-tap a dot** to remove it. Or tap **Start over** and **draw around the piece** with your finger or mouse; the outline snaps to where the fabric ends. Draw a second loop for separate parts, like a pair of shoes. **Tap by color** is still there for quick selections.
- Always check the type and style before saving. The style you choose (blazer, sneakers, slip dress and so on) tells the stylist how dressy and how warm the piece is.
