# Money Split

Split bills with friends and see who should pay whom, then open your UPI app to pay.

A small web app in a single HTML file. No server, no sign-up, no build step. Your data stays in your own browser.

## Features

- Add the people in your group, with an optional UPI ID for each
- Add a bill: what it was for, the amount, who paid and who shared it
- Split equally, or by exact amounts for each person
- See who gets money back and who needs to pay, with the total spent and what each person paid
- Get the fewest payments needed to settle up
- Pay with one tap: opens Google Pay, PhonePe, Paytm, CRED, or any other UPI app (slice, super.money and more) with the receiver and amount filled in
- Copy a UPI ID, copy the summary, or share it on WhatsApp
- Mark a payment as done, and delete any bill or payment from the history

## Live demo

https://moneysplit-app.netlify.app/

## Try it locally

Open `index.html` in a browser. That is all.

For the payment buttons, open the live site on a phone that has a UPI app installed.

## Deploy

**Netlify:** drag this folder onto https://app.netlify.com/drop, or connect the GitHub repo (no build command, publish directory `.`).

**GitHub Pages:** go to Settings, then Pages, choose the `main` branch and the `/ (root)` folder.

## How it works

- Each bill is stored as whole paise, so there are no rounding errors. Any leftover paise in an equal split go to the first people in the list.
- Settle-up uses a greedy match: the person who owes the most pays the person who is owed the most, until everyone is even.
- Payment buttons use UPI links of the form `upi://pay?pa=<upi-id>&pn=<name>&am=<amount>&cu=INR`. Google Pay, PhonePe, Paytm and CRED also get their own app links. slice and super.money are reached through the standard `upi://` link, which lists installed UPI apps on Android.
- Data is saved with `localStorage` under the key `chalo-split-v1`.

## Limits

- Data lives only in one browser on one device. Clearing site data erases it.
- Rupees (INR) only.
- App buttons depend on the phone and the installed apps. They do nothing on a laptop.
- The app does not move money. It only opens your payment app.

## Project files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app (HTML, CSS and JavaScript) |
| `netlify.toml` | Netlify settings and basic security headers |
| `LICENSE` | MIT license |
| `.gitignore` | Files Git should skip |

## Ideas for later

- Edit a bill after saving it
- Several groups, such as "Goa trip" and "Flatmates"
- Split by percentage or shares
- QR code for each payment
- Installable app with offline support

## License

MIT. See `LICENSE`.
