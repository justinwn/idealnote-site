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

`index.html` is a placeholder so the domain isn't a 404. Replace it with the
real marketing page; nothing generates it.

## Apple's requirements

App Store Connect needs two publicly reachable URLs, neither behind a login:

| Field | URL |
| --- | --- |
| Privacy Policy URL | `https://idealnote.justinewin.com/privacy.html` |
| Support URL | wherever people can actually reach you |

The subscription also needs Terms of Use reachable from the app binary, which
`LegalScreen` already handles, and from the metadata, which is
`/terms.html`.
