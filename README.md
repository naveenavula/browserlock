# Browser Lock

Locks Chrome or Edge behind an email login, like Dia's sign-in window.

While locked, the only browser window is a small sign-in window: no tabs, bookmarks, history, settings or menus. Any other window (including InPrivate/Incognito) is closed the moment it opens. Your open tabs are saved and reopened after you sign in.

```
browser-lock/
├── worker/worker.js   Backend — already in your Cloudflare Worker (unchanged)
└── extension/         The browser extension
```

## Install (Edge)

1. Unzip into a folder you'll keep (e.g. Documents\browser-lock). The browser runs the extension from there.
2. Go to `edge://extensions` (Chrome: `chrome://extensions`).
3. If the earlier version is there, click **Remove** on it.
4. Turn on **Developer mode**, click **Load unpacked**, and choose the `extension` folder.
5. Click **Details** on Browser Lock and turn on **Allow in InPrivate** (Chrome: **Allow in Incognito**). Without this, InPrivate windows aren't blocked.

The browser locks straight away. Sign in with your email and the 6-digit code.

## How it behaves

- Locked every time the browser starts, and whenever you close all its windows.
- Unlocked for 12 hours, then locks again (tabs are saved and come back after signing in).
- Toolbar icon → **Lock browser now** locks immediately.
- Closing the sign-in window closes the browser.
- No internet = can't unlock (the code has to come from your Worker).

## Limits

An extension can't stop someone who starts the browser with extensions turned off, or who uses a Guest or different profile. For a lock nobody can get around, Edge/Chrome group policy can force-install the extension and turn off guest mode, InPrivate and new profiles.

When the browser starts, it may show your last window for a split second before the lock closes it.
