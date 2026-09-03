# FetchNow All-in-One MVP

Customer → Request → Fare → Order  
Partner → Email verification → Licence details → Admin review → Approval  
Customer ↔ Partner → Status updates  
Admin → Dashboard + partner applications  

## New partner verification flow
1. Partner enters name, phone, email, vehicle, driving licence number and licence expiry.
2. Email verification is mandatory; a one-time link expires after 30 minutes.
3. After verification, FetchNow emails the Admin (`ADMIN_EMAIL`).
4. Admin reviews the application and licence details.
5. Only an approved application becomes an active partner.

## Email setup
This MVP uses Resend's HTTP API. Create a Resend account/API key, then set:
- `RESEND_API_KEY`
- `EMAIL_FROM` (use a verified domain for production)
- `ADMIN_EMAIL`
- `PUBLIC_URL` to the public URL where this server is hosted.

For local development, if `RESEND_API_KEY` is empty, the server logs that email is not configured rather than sending an email. For real verification, configure Resend.

## Run
1. Install Node.js 18+
2. `npm install`
3. Copy `.env.example` to `.env`
4. Fill in the email settings above
5. `npm start`
6. Open http://localhost:3000

## Production security
The current MVP still needs real Admin authentication/roles before the Admin dashboard is exposed publicly. Licence documents should be added later using private object storage and access-controlled URLs; do not store licence photos in a public GitHub Pages folder.
