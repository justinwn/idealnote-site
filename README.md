# ideal note — website

Marketing page, FAQ, Privacy Policy and Terms of Use for the **ideal note**
iOS app. Served at <https://idealnote.justinewin.com>.

Kept separate from the app so the app's source can stay private, and so copy
changes don't clutter the app's history.

## The legal pages are generated — don't hand-edit them

`privacy.html` and `terms.html` are built from `LegalScreen.swift` in the app
repo, which is what the app itself displays. Two copies of a legal document
drift, and a reviewer comparing the hosted policy against the in-app one is
exactly the inconsistency that draws a rejection.

To change the legal text: edit it in the app, then regenerate here.

```bash
cd ../idealnote && python3 tools/genlegal.py ../idealnote-site
```

Remember to move `lastUpdated` in `LegalScreen.swift` at the same time.

## Everything else

`index.html` is the marketing page and `support.html` is the FAQ. Both are
hand-written — nothing generates them.

Favicons are generated from Cal Sans by `tools/favicon.swift` in the app repo.
The tab icon is a single "i" rather than the wordmark, because two stacked
words are unreadable at 16px. `apple-touch-icon.png` is the real app icon, so
a site saved to a Home Screen matches the App Store listing.

`assets/` holds screenshots exported from the iPhone 18 Pro Max simulator at
1320x2868 and resized to 600px wide. To refresh them, seed the simulator
(`-seedSampleData`), capture, then `sips --resampleWidth 600`. Resize by
*width*, not `-Z`, which scales by the longest side and leaves them too soft
for a retina screen.

The hero shows a "Coming soon to the App Store" marker rather than a download
button. At launch, replace it with Apple's own badge artwork from
<https://developer.apple.com/app-store/marketing/guidelines/> — they require
their image, not a lookalike — linked to the real listing.
The App Store button is the only placeholder left.

## Apple's requirements

App Store Connect needs two publicly reachable URLs, neither behind a login:

| Field | URL |
| --- | --- |
| Privacy Policy URL | `https://idealnote.justinewin.com/privacy.html` |
| Support URL | `https://idealnote.justinewin.com/support.html` |

The subscription also needs Terms of Use reachable from the app binary, which
`LegalScreen` already handles, and from the metadata, which is
`/terms.html`.
