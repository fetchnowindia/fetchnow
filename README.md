# FetchNow – Email + Licence Verification

This version adds a mandatory partner email-verification flow and protected Admin APIs.

## Partner flow
1. Partner submits name, phone, email, vehicle, driving licence number and licence expiry.
2. Email is required and must be verified through a one-time link valid for 30 minutes.
3. After verification, FetchNow emails the Admin address in `ADMIN_EMAIL`.
4. Admin logs into the protected dashboard and approves/rejects the application.
5. Only approved applications become active partners.

## Email setup
This project uses Resend's HTTP API. Set these in the backend `.env` file:
- `RESEND_API_KEY`
- `EMAIL_FROM` (use a verified domain for production)
- `ADMIN_EMAIL=vaidyashantanu75@gmail.com`
- `PUBLIC_URL` = public backend URL, not the GitHub Pages URL
- `ADMIN_PASSWORD` = a strong private password
- `FRONTEND_URL` = exact GitHub Pages origin if frontend is hosted separately

Never put `.env`, API keys or the admin password into GitHub.

## Local run
1. Node.js 18+
2. `npm install`
3. Copy `.env.example` to `.env`
4. Fill in the email/admin settings
5. `npm start`
6. Open `http://localhost:3000`

## GitHub Pages note
GitHub Pages can host the static `public/` frontend, but it cannot run `server.js`. For production, host the Node/Express backend on a Node-capable service and set `public/config.js`:

```js
window.FETCHNOW_API_BASE = 'https://YOUR-BACKEND-DOMAIN';
```

Then set the backend `FRONTEND_URL` to your GitHub Pages origin and `PUBLIC_URL` to the backend URL.

## Licence documents
This version collects licence number + expiry. Do not upload licence photos to a public GitHub Pages folder. If document upload is added later, use private object storage and access-controlled URLs.
