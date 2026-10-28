---
layout: default
title: Privacy Policy — TallyVally
---

# Privacy Policy — TallyVally

**Effective date:** July 22, 2026
**Last updated:** October 28, 2026

**Applies to:** the TallyVally mobile app for iOS and Android.

**Two iPhone versions.** TallyVally 2.0 for iPhone is a rebuilt app. Where it
handles your data differently from earlier iPhone versions (1.x) and from the
Android app, this policy says **"on iPhone, from 2.0"**. Everything not marked
that way applies to every version.

---

## The short version

- **Your financial data lives on your device.** TallyVally is an offline-first
  expense tracker. Your receipts, line items, store names, dates, amounts, and
  the card last-4 / payment method shown on a receipt are stored **only on your
  phone**, in an on-device database. **On iPhone, from 2.0, the app also keeps a
  copy in your own iCloud** (on by default, and you can turn it off), so your
  receipts come back if you delete the app or move to a new iPhone. We can never
  see that copy.
- **We do not have a server that stores your receipts or your questions,** and
  there are **no user accounts.** We never receive a copy of your ledger. **On
  Android, and on iPhone from 2.2.1**, to count your free scans and chats, our
  server keeps a code for your phone and how many free scans and chats it has
  used — nothing about what you scanned or asked (Sections 3f and 3g).
- **One feature uses the cloud: the AI chat, and AI receipt scanning.** To read a
  receipt photo and to answer your chat questions, data is sent to **Google's
  Gemini AI**, through our backend proxy. **On iPhone, from 2.0, chat questions
  are answered by Apple's AI where your iPhone supports it**, and by Google's only
  when Apple's cannot answer. This is described in detail below.
- **We do not use advertising, behavioral analytics, or third-party tracking
  SDKs.** We do not track you across apps or websites, and we do not sell or
  share your data for advertising.
- **You are in control.** You can delete any receipt, clear your chat history,
  set how long chat history is kept, turn on a stricter "Send only totals to AI"
  chat mode, **export a copy of all your receipts to a file**, or uninstall the
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

TallyVally stores your data in a local database (SQLite) inside the app's
private storage on your device. This includes:

- **Receipts and transactions** — store name, date, time, totals, subtotal, tax,
  savings/coupons, and the **individual line items** (item name, quantity, unit
  price, line total, and a spending category).
- **Card last-4 and payment method** — if your receipt prints them (e.g. "VISA
  ····1234"), they are stored so the receipt detail screen can display them. We
  store only the **last four digits** and a coarse method label (e.g. "Visa",
  "Cash") — never a full card number, PIN, CVV, or bank-account number.
- **A copy of the receipt, if you ask us to keep it** — TallyVally can
  optionally save the photograph or PDF each receipt was scanned from, so you can
  look at it later. Photographs are compressed to save space; PDFs are kept
  exactly as they are. This is **off unless you turn it on** (Settings › Your data
  › Keep a copy of each receipt), it applies only to receipts scanned after you
  turn it on, and the files never come to us. On iPhone they are included in
  your own device backup along with the rest of your app data, and **on iPhone,
  from 2.0**, in the copy in your own iCloud described below, while it is on;
  **on Android they are never backed up to Google Drive, but they move with your
  receipts when you transfer your data to a new phone** (Section 3d). They are stored with the same
  protection as the database above, they
  are deleted when you delete the receipt they belong to, and Settings offers a
  single action that deletes all of them without touching your receipts.
- **Chat history** — the questions you type to the financial assistant and its
  answers.
- **App settings** — your theme, language, home currency, your chat-history
  retention window, and your "Send only totals to AI" preference.

There are **no user accounts**, no sign-in, and no cloud copy of this data under
our control. We cannot see your ledger.

**On iPhone, from 2.0: a copy in your own iCloud.** The app keeps a copy of its
database — your receipts, line items, chat history and settings — and of any
receipt copies you kept, in its private folder in **your own iCloud Drive**, so
that they come back if you delete the app or move to a new iPhone: on a phone
with no receipts, the app offers to bring them back, and does so only if you
say yes. The copy is in your Apple Account; it never comes to us and we can
never see it. It is **on by default**. You can turn it off in **Settings › Your
data › Keep a copy in iCloud**; the app asks first, then deletes the copy in
your iCloud. If iCloud Drive is off on your iPhone, nothing is copied. Android
keeps no such copy.

## 3. What leaves your device, to whom, and why

Only **two features** send what you scanned or asked off your device, and both
send it to the same recipient: **Google's Gemini AI**
(`generativelanguage.googleapis.com`). The
requests are routed through **our backend proxy** — a Supabase-hosted Edge
Function — which forwards them to Google and returns the result. The proxy exists
so that the Google API key is never embedded in the app; it is infrastructure,
not a place where your data is stored.

**On iPhone, from 2.0, three more things can leave your device, none of them to
us:** chat questions may be answered by **Apple's AI** (Section 3b); the copy in
**your own iCloud** (Section 2); and, only if your home currency is the
Kazakhstani tenge, a request for the **National Bank of Kazakhstan's** public
exchange rates (Section 3e).

**On iPhone, from 2.2.1,** each scan or chat also carries the proof that counts
your free scans, and our server asks Apple once about your iPhone (Section 3g).
None of it is about your receipts.

**On Android, a few more things leave your device, none of them about your
receipts:** with each scan or chat, the proof that counts your free scans
(Section 3f); the tenge rates request, as on iPhone (Section 3e); and Google
Play's own billing library, which talks to Google (Section 5).

### 3a. Scanning a receipt (AI receipt OCR)

When you scan or upload a receipt, the app sends the **receipt itself** to Google
Gemini — either the **photo** you took or chose, or a **PDF** you uploaded from
Files. Gemini reads it and returns the structured fields (store, date, totals,
line items, and — if printed on the receipt — the payment method and card last-4).
The extracted result is then saved **on your device**.

A PDF is sent **in full, every page**. If a document holds more than the one
receipt you meant to scan, everything printed in it is part of what is sent.

**Important and honest detail:** because the whole receipt is sent for reading —
the entire photo, or every page of the PDF — anything visible on it is part of the
transmission. If your
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
the three identifies you, and only the date reaches Google. **On Android, and
on iPhone from 2.2.1**, a scan also carries the proof described in Sections 3f
and 3g, which does identify your phone (by a code), so that free scans can be
counted.

Receipt scanning is **user-initiated**: nothing is sent unless you choose to scan
or upload a specific file.

### 3b. Asking the financial assistant (AI chat)

When you ask the in-app assistant a question, the app sends to Google Gemini:

1. **Your typed question** (and the recent back-and-forth of the current
   conversation), and
2. **A summary of your spending** used to ground the answer in your real data.

By default, that summary includes **aggregate figures** (your total spend, number
of transactions, average transaction value, total savings, and spending by
category) and a short list of the **items you buy most often, by name**. When your
question names a particular store, item or time period, the **store names and
shopping dates** needed to answer it are included as well.

**One detail worth being plain about:** the list of your most-purchased item names
is part of **every** cloud chat question, not only the ones that mention an item.
Store names and dates are not — those travel only when your own question or the
recent conversation refers to them. If your receipts record purchases you would
rather not have read by an AI service, turn on **"Send only totals to AI"**
(Section 3c), which sends no item names at all, or use on-device chat where your
iPhone supports it, which sends nothing for an answer. On-device chat is an
iPhone feature; Android has no on-device AI option and always uses the cloud
assistant described above.

The chat path **never sends your card last-4 or payment method.** The grounding
summary is built so that card and payment fields are excluded — they are simply
not part of what the chat feature reads.

**On iPhone, from 2.0: Apple's AI answers first.** With **"Use Apple's most
advanced AI"** on (Settings › Chat & data; on by default) and an iPhone that
supports Apple Intelligence, your question is answered by Apple's AI on
**Apple's Private Cloud Compute** servers. It receives your question, the
recent conversation, a summary of your spending, and the answers to the
questions it asks your receipts to answer you — for example your spending by
month or by category, the stores you shopped at, or when and where you last
bought an item. It never receives your card last-4 or payment method. Apple
says this data is used only to answer you and is not stored. Only when Apple's
AI cannot answer does the question go to Google's Gemini as described above.
Turn the setting off and a simpler Apple AI answers on your iPhone itself, so
**nothing leaves your device** for an answer. On an iPhone without Apple
Intelligence, Google's Gemini answers. Each answer says who wrote it
("Answered by Apple" or "Answered by Google").

### 3c. "Send only totals to AI" (opt-in, for stricter privacy)

In **Settings → Chat & data** you can turn on **"Send only totals to AI"**.
When it is on, the chat feature sends **only totals and category breakdowns** — no item names, no store
names, and no dates leave your device, only the name of the period you asked
about (for example "this month"). **On Android**, the earlier messages of the
conversation are not sent either. **On iPhone, from 2.0**, it limits
Apple's AI in the same way. Answers become less
specific in exchange for sending the minimum possible data. This setting is
**off by default**, so the assistant has the detail it needs unless you choose
otherwise.

### 3d. What we do **not** send anywhere

- We do **not** send your data to any advertiser, data broker, or analytics
  provider.
- We do **not** upload your ledger, receipts, or database **to our servers, or to
  any third-party backup or sync service.** We have no account system and no copy
  of your data. The one exception is yours, not ours: **on iPhone, from 2.0**,
  the copy in your own iCloud (Section 2), which you can turn off.
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
  on your iPhone.
- **On Android, nothing goes to the cloud, but your receipts can move to your
  new phone.** Android's automatic backup to Google Drive is switched **off** for
  this app, so your receipts are never copied to Google Drive and never come to
  us. When you set up a new Android phone and **transfer your data from your old
  one** (phone to phone, by cable or wirelessly), your receipts, and any receipt
  copies you kept, **move with it**, so changing phones does not cost you your
  records. If you **lose or wipe** the phone without such a transfer, they are
  gone: for a copy of your own, use **Settings › Your data › Export your
  receipts** (Section 11).
- **On iPhone, from 2.0, the app contains no crash-reporting SDK and sends no
  crash reports of its own.** If you allow it (iPhone Settings › Privacy &
  Security › Analytics & Improvements › Share With App Developers), **Apple**
  sends us crash reports and diagnostics, with no identity attached. The rest of
  next item covers Android, and the one after it iPhone versions before 2.0.
- **On Android, the app contains no crash-reporting SDK and sends no crash
  reports.** When something fails, it writes a short technical note in its own
  storage on your phone (the newest 50 are kept). A note never contains your
  receipts, items, store names, amounts or chat; long digit runs and access
  tokens are removed from it; and it is **never sent anywhere** — it stays on
  your phone, where only a developer with your phone connected to a computer
  could read it.
- **On iPhone before 2.0, we do send crash reports, and only
  crash reports, to Firebase Crashlytics (a Google service).** When the app crashes or hits an unexpected error, we
  receive the technical details needed to fix it: the type of error, the line of
  code it came from, your device model, and your iOS version. This is
  how a bug
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

### 3e. Exchange rates for the Kazakhstani tenge (iPhone, from 2.0, and Android)

If your home currency is the **Kazakhstani tenge**, the app downloads the
**National Bank of Kazakhstan's** public exchange rates, to convert receipts in
other currencies at the official rate for their own day. Only a **date** is
sent; nothing about you or your receipts. With any other home currency, the app
never makes this request.

### 3f. Counting free scans and chats (Android)

Free scans and chats on Android are counted by **our server**, so that deleting
and reinstalling the app does not reset them. To do this, each scan and each
chat question carries:

- **A scrambled code for your phone.** The app takes the identifier Android
  gives this app on your phone and turns it into a code that cannot be turned
  back (a SHA-256 hash). The identifier itself never leaves your phone. The code
  stays the same if you reinstall the app, and changes if you factory-reset the
  phone.
- **A proof from Google Play that the request comes from the real TallyVally
  app on a real phone** (Google Play Integrity). Our server sends this proof to
  Google to check it.
- **If you subscribe**, your Google Play **purchase token**, which our server
  sends to Google Play to confirm the subscription is active.

**What our server keeps:** your phone's code, with how many free scans and
free chats it has used (the welcome pack, and this month's), and when. This is
kept **for good**, so the welcome pack is not given twice. For a subscription,
it keeps a scrambled form of the purchase token (never the token itself), when
the subscription ends, and which phone codes used it each month. To stop
abuse, it also counts requests per **internet (IP) address** in short time
windows; these counters are not linked to your phone code. **None of this
contains anything you scanned or asked.** Google handles the Play Integrity
and Google Play checks under its own privacy policy.

**On iPhone before 2.2.1, free scans and chats are counted on the phone
itself**, and none of this applies there. From 2.2.1, see Section 3g.

### 3g. Counting free scans and chats (iPhone, from 2.2.1)

From version 2.2.1, free scans and chats on iPhone are counted by **our server**
too, so that deleting and reinstalling the app does not reset them. To do this,
each scan and each chat question carries:

- **A random code for your phone.** The app makes it once and keeps it in your
  iPhone's keychain, so it stays the same if you reinstall the app. It is not
  your phone's serial number or any identifier Apple assigns to your phone.
- **A proof that the request comes from the real TallyVally app on a real
  iPhone** (Apple's App Attest). A key made inside your iPhone for this
  installation signs each request, and our server checks the signature.
- **If you subscribe**, Apple's signed record of your purchase, which our
  server checks with Apple to confirm the subscription is active.

The first time, our server also asks Apple (Apple's **DeviceCheck**) whether
this iPhone has used TallyVally's welcome pack before, and tells Apple that it
now has. Apple keeps this as two yes-or-no answers, and the month they last
changed, for this iPhone and our app only; they contain nothing about you.

**What our server keeps:** your phone's code, with how many free scans and
free chats it has used (the welcome pack, and this month's), and when; and, for
each installation, its key's public half, a counter that stops a request from
being sent twice, and Apple's receipt for the key. This is kept **for good**, so
the welcome pack is not given twice. For a subscription, it keeps a scrambled
form of the purchase's ID (never the record itself), when the subscription
ends, and which phone codes used it each month. As on Android, it also counts
requests per **internet (IP) address** in short time windows; these counters
are not linked to your phone code. **None of this contains anything you scanned
or asked.** Apple handles App Attest, DeviceCheck and the App Store under its
own privacy policy.

## 4. How Google handles the data we send it

The receipt images and chat content described in Section 3 are processed by
**Google's Gemini API**. Google's handling of that data is governed by Google's
own API terms and privacy commitments for the API tier in use, not by us.

We are honest about the limit of our knowledge here: confirming and contracting a
specific **no-retention / no-training Gemini tier** is an operational step the
developer must complete, and **until that is confirmed we do not claim that
Google does not retain or use this data.** We send Google the minimum needed for
the feature to work, we never attach an account or identity to it (there are no
accounts), and "Send only totals to AI" (Section 3c) lets you reduce what is sent
to totals only. For details of Google's practices, see Google's API terms and
privacy documentation.

## 5. No tracking, no ads, no third-party analytics

TallyVally contains **no advertising SDKs, no behavioral-analytics SDKs, and no
cross-app/cross-site tracking.** We do not build advertising profiles, and we do
not use the Apple "tracking" mechanisms (App Tracking Transparency is not invoked
because we do not track). The iOS privacy manifest declares
`NSPrivacyTracking = false` and an empty tracking-domains list, consistent with
this statement. On Android the app requests **no advertising identifier** and
contains no advertising or analytics library.

**On iPhone, from 2.2.1,** the app uses Apple's **App Attest** and
**DeviceCheck** (Section 3g). They are part of iOS, not third-party code, and
are used only to count free scans and chats, never for advertising or
tracking.

**On Android, the app's only third-party code is Google's own Play
libraries:** **Google Play Billing**, which every app that sells subscriptions
through Google Play uses, and **Google Play Integrity** (Section 3f). Google
Play Billing includes Google's own diagnostics component, which sends Google
technical information about how the billing library itself is working (to
`firebaselogging.googleapis.com`). We do not receive that information, and
Google handles it under its own privacy policy. There is no Firebase
Crashlytics and no Google Analytics in the Android app.

**On iPhone, from 2.0, the app contains no third-party SDK at all.** On iPhone
before 2.0, **the one third-party SDK in the app is Firebase
Crashlytics, and it is here to report crashes, not to watch you.** We are naming it rather than hiding it behind
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
  server-side copy of your receipts or questions ourselves.
- **On Android, and on iPhone from 2.2.1, the counts of your free scans and
  chats** are kept on our server with your phone's code, for good (Sections 3f
  and 3g).
- **Kept receipt copies** (if you turned that setting on) stay until you
  delete the receipt they belong to — which deletes the file with it — or until
  you use **Settings › Your data › Delete saved copies**, which removes every
  one of them and leaves your receipts and their amounts untouched. Turning the
  setting **off** stops new ones being saved and deletes nothing.
- **Uninstalling the app** deletes all TallyVally data on the device itself.
- **The copy in your iCloud (iPhone, from 2.0)** stays in your iCloud until you
  turn it off in **Settings › Your data › Keep a copy in iCloud** — which deletes
  it — or delete TallyVally's data from your iCloud storage in iPhone Settings.
  **Deleting the app does not delete it**: that is what lets your receipts come
  back. It is in your Apple Account, never ours.
- **One thing to know about backups, on iPhone.** Because your receipts are
  included in your iPhone's backup (Section 3d), a copy can still exist inside a
  backup you made
  earlier, even after you delete the app. That copy is in **your** Apple account or
  on **your** computer, never ours, and we cannot see it or reach it. It goes when
  the backup goes: delete the backup in **Settings › [your name] › iCloud › Manage
  Account Storage › Backups**, or delete the backup file on your computer. If you
  would rather no backup ever contains your receipts, turn TallyVally off in the same
  iCloud settings screen before backing up. **On Android there is no cloud
  copy:** uninstalling the app, or losing the phone, removes your receipts for
  good unless you exported them first or moved them to a new phone (Section 3d).

## 7. Security

- **At rest, on iPhone:** the on-device database lives in the app's private
  sandbox, which iOS encrypts at rest by default (iOS Data Protection). We
  additionally apply the strongest protection class, so the database is
  unreadable while your phone is locked — **and any receipt copies you asked us
  to keep carry the same protection**, because they are a second copy of the same
  information.
- **The copy in your iCloud (iPhone, from 2.0)** is stored and encrypted by Apple
  in your iCloud Drive; with Apple's **Advanced Data Protection** turned on it is
  end-to-end encrypted, so not even Apple can read it.
- **At rest, on Android:** the same files live in the app's private storage,
  which the system encrypts at rest and which no other app can read. Android
  offers no equivalent of the extra protection class described above, so **we do
  not claim one** — your data is protected by your device's own encryption and
  screen lock.
- **In transit:** production builds require **HTTPS** for all network requests
  (iOS App Transport Security is enforced for public domains; on Android the
  shipped build blocks unencrypted traffic outright). Cleartext is permitted only
  for local development against a developer's own machine, never in a shipped
  build.
- **Keys:** the Google API key is never placed in the app; it lives only on the
  backend proxy.

No method of electronic storage or transmission is perfectly secure, but we
minimize what leaves the device and protect what remains on it.

## 8. Device permissions we request

- **Camera** — to photograph a physical receipt for scanning.
- **Photos / Photo Library** — to let you pick an existing receipt screenshot or
  photo to scan.
- **Files** — to let you choose a PDF receipt to upload. The system document
  picker hands the app only the single file you pick; the app cannot browse your
  documents.

These permissions are used **only** for the receipt-scanning feature you
initiate, and only on the specific image you choose. We do not access your camera
or photo library in the background.

**On Android the app declares no camera, photo, or storage permission at all.**
It asks for internet access, billing through Google Play, and network status
(whether you are online); for **notifications**, only when you choose a reminder
before a subscription or bill is charged; and to **start after the phone
restarts**, only so those reminders are set again.
Photographing a receipt hands the job to your phone's own camera app, and
choosing a photo or a PDF goes through Android's own picker, which passes back
only the one file you chose.

## 9. Children

TallyVally is a general-audience financial tool and is **not directed to
children.** We do not knowingly collect personal information from children.

## 10. International users and data transfer

If you use the app outside the regions where Google processes Gemini API
requests, the receipt/chat data described in Section 3 may be processed in
another country (for example, the United States). By using the AI scanning and
chat features, you understand that this processing occurs as described here.

## 11. Your choices and controls

- **Every scan is your choice.** Scanning a receipt — by camera, by picking an
  image, or by uploading a PDF — is currently the only way to add a transaction to
  the app, and nothing is ever sent unless you initiate a scan on a specific
  file. Browsing, searching,
  and analysing what you have already saved happens entirely on your device.
- **On a supported iPhone, you can make chat fully private.** **From 2.0:** turn
  off **"Use Apple's most advanced AI"** in **Settings → Chat & data**, and a
  simpler Apple AI answers on your phone itself, so your questions and spending
  summary **never leave the device at all** (it requires Apple Intelligence).
  **Before 2.0:** "Use on-device AI for chat" in the same place does this; it is
  off by default, and when it is unavailable the app uses the cloud assistant
  described in Section 3b. **This is an iPhone feature.** Android has no
  on-device AI option, so chat on Android always uses the cloud assistant.
- Turn on **"Send only totals to AI"** to send only totals to the assistant.
- **On iPhone, from 2.0**, turn off **Settings → Your data → Keep a copy in
  iCloud** to keep your receipts only on your phone (Section 2).
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
