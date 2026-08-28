---
layout: default
title: Privacy Policy — TallyVally
---

# Privacy Policy — TallyVally

**Effective date:** July 22, 2026
**Last updated:** August 26, 2026

**Applies to:** the TallyVally mobile app for iOS and Android.

---

## The short version

- **Your financial data lives on your device.** TallyVally is an offline-first
  expense tracker. Your receipts, line items, store names, dates, amounts, and
  the card last-4 / payment method shown on a receipt are stored **only on your
  phone**, in an on-device database.
- **We do not have a server that stores your data,** and there are **no user
  accounts.** We never receive a copy of your ledger.
- **One feature uses the cloud: the AI chat, and AI receipt scanning.** To read a
  receipt photo and to answer your chat questions, data is sent to **Google's
  Gemini AI**, through our backend proxy. This is described in detail below.
- **We do not use advertising, behavioral analytics, or third-party tracking
  SDKs.** We do not track you across apps or websites, and we do not sell or
  share your data for advertising.
- **You are in control.** You can delete any receipt, clear your chat history,
  set how long chat history is kept, turn on a stricter "aggregate-only" chat
  privacy mode, **export a copy of all your receipts to a file**, or uninstall the
  app to remove all on-device data.

---

## 1. Who this policy is for and who we are

This policy explains how the TallyVally app ("the app", "TallyVally") handles
your information. The app is published by Alisher Serikbayev ("we", "us",
"the developer"). You can reach us about privacy at alishersv.dev@outlook.com.

TallyVally is a personal expense and asset tracker. Its design principle is
**data sovereignty**: your financial history stays on your device by default, and
anything that leaves the device is disclosed here.

## 2. Where your data lives

TallyVally stores your data in a local database (SQLite, via Drift) inside the
app's private storage on your device. This includes:

- **Receipts and transactions** — store name, date, time, totals, subtotal, tax,
  savings/coupons, and the **individual line items** (item name, quantity, unit
  price, line total, and a spending category).
- **Card last-4 and payment method** — if your receipt prints them (e.g. "VISA
  ····1234"), they are stored so the receipt detail screen can display them. We
  store only the **last four digits** and a coarse method label (e.g. "Visa",
  "Cash") — never a full card number, PIN, CVV, or bank-account number.
- **Chat history** — the questions you type to the financial assistant and its
  answers.
- **App settings** — your theme, your chat-history retention window, and your
  aggregate-only chat preference.

There are **no user accounts**, no sign-in, and no cloud copy of this data under
our control. We cannot see your ledger.

## 3. What leaves your device, to whom, and why

Only **two features** send data off your device, and both send it to the same
recipient: **Google's Gemini AI** (`generativelanguage.googleapis.com`). The
requests are routed through **our backend proxy** — a Supabase-hosted Edge
Function — which forwards them to Google and returns the result. The proxy exists
so that the Google API key is never embedded in the app; it is infrastructure,
not a place where your data is stored.

### 3a. Scanning a receipt (AI receipt OCR)

When you scan or upload a receipt, the app sends the **receipt image** to Google
Gemini, which reads the text and returns the structured fields (store, date,
totals, line items, and — if printed on the receipt — the payment method and card
last-4). The extracted result is then saved **on your device**.

**Important and honest detail:** because the whole receipt **image** is sent for
reading, anything visible on that receipt is part of the transmission. If your
receipt prints the **last four digits of your card and the payment method**,
those are present in the image and are extracted by Gemini. This is why we
disclose **Payment Info** as data that can leave the device. We never send a full
card number, PIN, CVV, expiry, or bank-account number — those are not stored on
the receipt and are not handled by the app.

**Three small technical values travel with a scan, and none of them is a receipt
field.** Your phone's **calendar date** is sent to Google along with the image, so
that a receipt printing no date of its own is filed on *your* day rather than the
server's. Your **home-currency setting** (for example `USD`) and a
**free-or-premium flag** go only as far as our own proxy — the first so it can look
up that day's exchange rate, the second so it can manage its own AI budget. None of
the three identifies you, and only the date reaches Google.

Receipt scanning is **user-initiated**: nothing is sent unless you choose to scan
or upload a specific image.

### 3b. Asking the financial assistant (AI chat)

When you ask the in-app assistant a question, the app sends to Google Gemini:

1. **Your typed question** (and the recent back-and-forth of the current
   conversation), and
2. **A summary of your spending** used to ground the answer in your real data.

By default, that summary includes **aggregate figures** (your total spend, number
of transactions, average transaction value, total savings, and spending by
category) **plus**, for the specific store, item, or time period your question
mentions, the **relevant store names, item names, and shopping dates** needed to
answer it.

The chat path **never sends your card last-4 or payment method.** The grounding
summary is built so that card and payment fields are excluded — they are simply
not part of what the chat feature reads.

### 3c. Aggregate-only chat mode (opt-in, for stricter privacy)

In **Settings → Chat & Data** you can turn on **"Aggregate-only AI mode."** When
it is on, the chat feature sends **only totals and category breakdowns** — no item
names, no store names, and no dates leave your device. Answers become less
specific in exchange for sending the minimum possible data. This setting is
**off by default**, so the assistant has the detail it needs unless you choose
otherwise.

### 3d. What we do **not** send anywhere

- We do **not** send your data to any advertiser, data broker, or analytics
  provider.
- We do **not** upload your ledger, receipts, or database **to our servers, or to
  any third-party backup or sync service.** We have no account system and no copy
  of your data. (Cross-device sync, if it is ever built, will be an explicit,
  consented, opt-in feature governed by an updated version of this policy.)
- **Your iPhone's own backup does include your receipts, and that is deliberate.**
  Your receipts are stored in the app's own storage on your iPhone. If you use
  iCloud Backup or back your phone up to a computer, they are included in that
  backup along with your other app data, so that **replacing or losing your phone
  does not destroy your records.** That backup is your own: it goes to your Apple
  account, not to us, and we can never see it. Apple encrypts it, and if you turn
  on Apple's **Advanced Data Protection** it is encrypted end-to-end so not even
  Apple can read it; a computer backup with "Encrypt local backup" ticked never
  involves Apple at all. If you would rather your receipts were not in any backup,
  you can turn off iCloud Backup for TallyVally in **Settings › [your name] › iCloud**
  on your iPhone. _(Android auto-backup to Google Drive remains **disabled** —
  unlike Apple's, it offered no comparable user control at the time of writing.)_
- **We do send crash reports, and only crash reports, to Firebase Crashlytics
  (a Google service).** When the app crashes or hits an unexpected error, we
  receive the technical details needed to fix it: the type of error, the line of
  code it came from, your device model, and your iOS version. This is how a bug
  that would otherwise silently lose your data gets found and fixed.
  - **What a crash report never contains:** your receipts, your line items, your
    store names, your totals, your card's last four digits, or your chat history.
    Before any report leaves the app it passes through a filter that removes
    long digit sequences (the shape of a card number) and access tokens.
  - **There is no account attached**, because the app has none. Crashlytics
    identifies the report only by a random per-install identifier, which tells us
    that two crashes came from the same installation and nothing about who you
    are. Deleting and reinstalling the app generates a new one.
  - **It is not advertising or analytics.** We do not receive, and have not
    enabled, any record of which screens you visit, what you tap, or how often you
    use the app. Google Analytics for Firebase is **not** in this app.
  - This replaces the previous statement that we transmit no diagnostics at all.
    That statement was true, and it was true at a cost we judged too high: without
    it we could not see a crash that happened on your phone, which meant shipping
    an app that handles money while being unable to tell whether it was breaking.

## 4. How Google handles the data we send it

The receipt images and chat content described in Section 3 are processed by
**Google's Gemini API**. Google's handling of that data is governed by Google's
own API terms and privacy commitments for the API tier in use, not by us.

We are honest about the limit of our knowledge here: confirming and contracting a
specific **no-retention / no-training Gemini tier** is an operational step the
developer must complete, and **until that is confirmed we do not claim that
Google does not retain or use this data.** We send Google the minimum needed for
the feature to work, we never attach an account or identity to it (there are no
accounts), and the aggregate-only mode (Section 3c) lets you reduce what is sent
to totals only. For details of Google's practices, see Google's API terms and
privacy documentation.

## 5. No tracking, no ads, no third-party analytics

TallyVally contains **no advertising SDKs, no behavioral-analytics SDKs, and no
cross-app/cross-site tracking.** We do not build advertising profiles, and we do
not use the Apple "tracking" mechanisms (App Tracking Transparency is not invoked
because we do not track). The iOS privacy manifest declares
`NSPrivacyTracking = false` and an empty tracking-domains list, consistent with
this statement.

**The one third-party SDK in the app is Firebase Crashlytics, and it is here to
report crashes, not to watch you.** We are naming it rather than hiding it behind
the word "analytics", because it is a Google SDK and you are entitled to know it
is there. What it is *not*: it records no screen views, no taps, no sessions, and
no usage patterns, and it builds no profile. Firebase's own privacy manifest
declares that it collects "Crash Data" and "Other Diagnostic Data", both **not
linked to your identity** and both **not used for tracking** — which matches what
we have enabled. Section 3d describes exactly what a report contains.

## 6. Data retention and deletion

- **Your ledger and receipts** stay on your device until **you delete them**
  (per receipt) or **uninstall the app** (which removes the on-device database).
  We do not auto-expire your financial history.
- **Your chat history** is kept on your device for a **retention window you
  control** in Settings (default: **30 days**; you can also choose **7 days** or
  **"Never"**, which keeps it until you clear it). When a window is set, older
  messages are automatically pruned on your device. You can also **clear all chat
  history** at any time.
- **Data sent to Google** for scanning/chat is retained or not retained according
  to Google's API terms for the tier in use (see Section 4). We keep no
  server-side copy ourselves.
- **Uninstalling the app** deletes all TallyVally data on the device itself.
- **One thing to know about backups.** Because your receipts are included in your
  iPhone's backup (Section 3d), a copy can still exist inside a backup you made
  earlier, even after you delete the app. That copy is in **your** Apple account or
  on **your** computer, never ours, and we cannot see it or reach it. It goes when
  the backup goes: delete the backup in **Settings › [your name] › iCloud › Manage
  Account Storage › Backups**, or delete the backup file on your computer. If you
  would rather no backup ever contains your receipts, turn TallyVally off in the same
  iCloud settings screen before backing up.

## 7. Security

- **At rest:** the on-device database lives in the app's private sandbox, which
  both platforms encrypt at rest by default (iOS Data Protection; Android
  file-based encryption).
- **In transit:** production builds require **HTTPS** for all network requests
  (Android blocks cleartext by default in release builds; iOS App Transport
  Security is enforced for public domains). Cleartext is permitted only for
  local development against a developer's own machine, never in a shipped build.
- **Keys:** the Google API key is never placed in the app; it lives only on the
  backend proxy.

No method of electronic storage or transmission is perfectly secure, but we
minimize what leaves the device and protect what remains on it.

## 8. Device permissions we request

- **Camera** — to photograph a physical receipt for scanning.
- **Photos / Photo Library** — to let you pick an existing receipt screenshot or
  photo to scan.

These permissions are used **only** for the receipt-scanning feature you
initiate, and only on the specific image you choose. We do not access your camera
or photo library in the background.

## 9. Children

TallyVally is a general-audience financial tool and is **not directed to
children.** We do not knowingly collect personal information from children.

## 10. International users and data transfer

If you use the app outside the regions where Google processes Gemini API
requests, the receipt/chat data described in Section 3 may be processed in
another country (for example, the United States). By using the AI scanning and
chat features, you understand that this processing occurs as described here.

## 11. Your choices and controls

- **Every scan is your choice.** Scanning a receipt (by camera or by picking an
  image) is currently the only way to add a transaction to the app, and nothing is
  ever sent unless you initiate a scan on a specific image. Browsing, searching,
  and analysing what you have already saved happens entirely on your device.
- **On a supported iPhone, you can make chat fully private.** In
  **Settings → Chat & Data**, "Use on-device AI for chat" runs the assistant
  directly on your phone, so your questions and spending summary **never leave the
  device at all**. It is off by default and requires a device with Apple
  Intelligence; when it is unavailable the app uses the cloud assistant described
  in Section 3b.
- Turn on **Aggregate-only AI mode** to send only totals to the assistant.
- **Take your records with you.** **Settings → Your data → Export your receipts**
  writes every receipt and line item to a spreadsheet file (CSV) and hands it to
  your phone's share sheet, so you can save it, mail it to yourself, or move it to
  another phone, including a non-Apple one. The file is created on your device and
  goes only where **you** send it; it never comes to us. **It contains the same
  details the app shows you, including the card last-4 and payment method when a
  receipt printed them**, so treat the exported file as you would a bank statement.
  Once you have shared it, the copy you sent is governed by whatever app or service
  you sent it to, not by this policy.
- **Delete** individual receipts, **clear** chat history, or set chat history to
  **"Never"** / a short window.
- **Uninstall** to remove all on-device data.

## 12. Changes to this policy

If we change how the app handles data, we will update this policy (and the
"Last updated" date) and, where the change is material, surface it appropriately.
The version published at <https://indxneo.github.io/tallyvally-legal/> is the
authoritative version.

## 13. Contact

Questions about this policy or your data: alishersv.dev@outlook.com.

This policy is governed by the laws of the State of Illinois, United States.
