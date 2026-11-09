# T3 Work sideload build

Run **Sideload iOS (unsigned)** in this fork's Actions tab. The default source is
upstream `main`; `ref` also accepts an upstream tag or commit. Defaults are bundle
ID `com.fermumen.t3code.work` and home screen name `T3 Work`.

Download the `.ipa` from the generated fork Release on your iPhone and open it in
SideStore. SideStore supplies the signing; CI never uses Apple credentials.

The build uses the public production Clerk key, JWT template, and relay URL from
upstream `.env.example`. Clerk production native auth requires the
Bundle ID and Team ID to be registered by T3 in its Clerk dashboard. The public
key alone does not guarantee login for this separate identity. See
https://clerk.com/docs/guides/development/deployment/expo. Native Apple sign-in, push, widgets, and share
extensions are omitted. Expo OTA updates are disabled. Direct QR pairing remains
available.

For a new version, fetch and merge upstream `main` into this fork, preserving
`.github/workflows/sideload-ios.yml`, then push. Keep all inherited workflows
disabled (including any newly added upstream). Run the sideload workflow with the
new upstream ref. Since the workflow fetches upstream itself, syncing is optional
unless its build tooling needs adjustment.
