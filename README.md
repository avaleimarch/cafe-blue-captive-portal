# Cafe Blue — Guest WiFi Captive Portal

A branded captive portal is proposed for Cafe Blue’s guest Wi-Fi network that would restrict internet access to business hours and require customers to enter a receipt number as proof of purchase. This solution would authenticate guests using their receipt number, eliminating the need for staff to print, manage, and distribute daily Wi-Fi codes.

## Features

- **Time-gated access** — Form is only available between 7:00 AM and 7:30 PM. Outside these hours, guests see a closed notice.
- **Live status indicator** — Active/Closed pill updates automatically every minute based on the device clock.
- **Proof of purchase** — Guests must enter a same-day receipt number to proceed.
- **Guest details collection** — Captures first name, last name, and email address.
- **Client-side validation** — All fields are validated before submission with inline error messages.
- **Success screen** — Confirms the guest's name and session expiry time upon successful sign-in.


## Files

| File | Description |
|------|-------------|
| `cafe-blue-portal.html` | The complete single-file captive portal (HTML, CSS, JS) |
| `README.md` | This file |


## How It Works

1. Guest connects to the Cafe Blue WiFi network and is redirected to the portal.
2. The portal checks the local device time against the allowed window (7:00 AM – 7:30 PM).
3. If within hours, the sign-in form is displayed.
4. Guest enters their receipt number, name, and email, then submits.
5. On success, a confirmation screen is shown and the guest is granted network access.


## Deployment Notes

### Integration Requirements
This portal is a front-end only file. For production use, the following backend integrations are needed:

- **Receipt validation** — Submit the receipt number to your POS or backend API to verify it was issued on the current date.
- **Network grant** — Wire the form submission to your router or hotspot controller to grant internet access upon successful validation. Compatible with solutions such as pfSense, Ubiquiti UniFi, MikroTik, or any captive portal-capable access point.
- **Data storage** — POST guest details (name, email, receipt number, timestamp) to your preferred backend or CRM for record-keeping.

### Hosting
- Serve this file from your router's built-in captive portal hosting, or from a local web server on the same network.
- No external dependencies are required at runtime except for the Google Fonts stylesheet (loaded via CDN). For fully offline use, embed the fonts locally.


## Customisation

| What | Where in the file |
|------|-------------------|
| Open/close times | `OPEN_HOUR`, `OPEN_MIN`, `CLOSE_HOUR`, `CLOSE_MIN` constants in the `<script>` block |
| Brand name & colours | CSS variables at the top of the `<style>` block |
| Receipt hint text | `field-hint` paragraph beneath the receipt input |
| Success redirect URL | Replace the `setTimeout` block in the submit handler with a `window.location` redirect |


## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). No build step or dependencies required — single `.html` file, ready to deploy.




<img width="569" height="732" alt="Screenshot 2026-03-30 at 5 06 35 PM" src="https://github.com/user-attachments/assets/1d66aacf-6aa4-459d-a7b3-f54d6072efcf" />
