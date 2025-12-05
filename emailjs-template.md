# EmailJS Setup Guide (Foundation + Donor Templates)

Use this file to configure EmailJS for donation notifications, styled to match the site (nav blue, soft gray background, rounded cards, logo on top). Replace placeholder IDs with your actual values from EmailJS.

## 1) Get Your Keys
- Public Key: `YOUR_EMAILJS_PUBLIC_KEY`
- Service ID: `YOUR_EMAILJS_SERVICE_ID`
- Template ID (Foundation notification): `YOUR_FOUNDATION_TEMPLATE_ID`
- Template ID (Donor thank-you): `YOUR_DONOR_TEMPLATE_ID`
- Template ID (Report notification): `YOUR_REPORT_TEMPLATE_FOUNDATION`
- Template ID (Reporter confirmation): `YOUR_REPORT_TEMPLATE_REPORTER`

## 2) Template Variables (keep these exact names)
```
donor_name
donor_email
amount
donation_type
payment_method
anonymous
timestamp
to_email
logo_url
```
> Set `logo_url` to a hosted image. To match the site, you can use the handshake icon: `https://img.icons8.com/fluency/96/handshake.png`.

Report templates use these:
```
reporter_name
reporter_email
phone
location
category
urgency
subject
description
previous_help
consent
timestamp
to_email
logo_url
```

## 3) Foundation Notification Template (HTML)
Set **To** to `{{to_email}}`. Uses the handshake icon via `{{logo_url}}` for the header.
```html
<table width="100%" cellpadding="0" cellspacing="0" style="font-family:'Poppins',Arial,sans-serif; background:#f9fafb; padding:24px; color:#0f172a;">
  <tr><td>
    <table width="640" align="center" cellpadding="0" cellspacing="0" style="background:#ffffff; border-radius:18px; padding:0; box-shadow:0 14px 36px rgba(15,23,42,0.12); overflow:hidden;">
      <tr>
        <td style="background:linear-gradient(135deg,#2563eb 0%,#1d4ed8 100%); padding:18px 24px; text-align:left; color:#ffffff;">
          <table width="100%" cellpadding="0" cellspacing="0">
            <tr>
              <td style="vertical-align:middle;">
                <img src="{{logo_url}}" alt="The Giver Foundation" style="height:52px; width:auto; border-radius:12px; display:block;">
              </td>
              <td style="text-align:right; font-weight:700; font-size:14px; letter-spacing:0.2px; opacity:0.95;">Donation Notification</td>
            </tr>
          </table>
        </td>
      </tr>
      <tr><td style="padding:24px 24px 28px;">
        <h2 style="margin:0 0 6px; color:#0f172a; font-size:22px;">New Donation Received</h2>
        <p style="margin:0 0 16px; color:#475569;">A supporter just submitted a donation.</p>
        <table width="100%" cellpadding="10" cellspacing="0" style="color:#0f172a; border:1px solid #e2e8f0; border-radius:12px;">
          <tr><td width="38%" style="color:#64748b;">Donor</td><td>{{donor_name}}</td></tr>
          <tr><td style="color:#64748b;">Email</td><td>{{donor_email}}</td></tr>
          <tr><td style="color:#64748b;">Amount</td><td>{{amount}}</td></tr>
          <tr><td style="color:#64748b;">Type</td><td>{{donation_type}}</td></tr>
          <tr><td style="color:#64748b;">Payment Method</td><td>{{payment_method}}</td></tr>
          <tr><td style="color:#64748b;">Anonymous</td><td>{{anonymous}}</td></tr>
          <tr><td style="color:#64748b;">Submitted</td><td>{{timestamp}}</td></tr>
        </table>
        <p style="margin:16px 0 0; color:#475569;">If bank transfer, expect a receipt from the donor. If cash, coordinate pickup/drop-off.</p>
      </td></tr>
    </table>
  </td></tr>
</table>
```

## 4) Donor Thank-You Template (HTML)
Set **To** to `{{to_email}}` (the donor email). Uses the handshake icon via `{{logo_url}}` for the header.
```html
<table width="100%" cellpadding="0" cellspacing="0" style="font-family:'Poppins',Arial,sans-serif; background:#f9fafb; padding:24px; color:#0f172a;">
  <tr><td>
    <table width="640" align="center" cellpadding="0" cellspacing="0" style="background:#ffffff; border-radius:18px; padding:0; box-shadow:0 14px 36px rgba(15,23,42,0.12); overflow:hidden;">
      <tr>
        <td style="background:linear-gradient(135deg,#2563eb 0%,#1d4ed8 100%); padding:18px 24px; text-align:left; color:#ffffff;">
          <table width="100%" cellpadding="0" cellspacing="0">
            <tr>
              <td style="vertical-align:middle;">
                <img src="{{logo_url}}" alt="The Giver Foundation" style="height:52px; width:auto; border-radius:12px; display:block;">
              </td>
              <td style="text-align:right; font-weight:700; font-size:14px; letter-spacing:0.2px; opacity:0.95;">Thank You</td>
            </tr>
          </table>
        </td>
      </tr>
      <tr><td style="padding:24px 24px 28px;">
        <h2 style="margin:0 0 6px; color:#0f172a; font-size:22px;">Thank You for Your Donation</h2>
        <p style="margin:0 0 14px; color:#475569;">Hi {{donor_name}}, we’ve received your pledge.</p>
        <table width="100%" cellpadding="10" cellspacing="0" style="color:#0f172a; border:1px solid #e2e8f0; border-radius:12px;">
          <tr><td width="38%" style="color:#64748b;">Amount</td><td>{{amount}}</td></tr>
          <tr><td style="color:#64748b;">Type</td><td>{{donation_type}}</td></tr>
          <tr><td style="color:#64748b;">Payment Method</td><td>{{payment_method}}</td></tr>
          <tr><td style="color:#64748b;">Submitted</td><td>{{timestamp}}</td></tr>
        </table>
        <p style="margin:16px 0 0; color:#475569;">If you chose bank transfer, please email your transfer receipt to giverfoundation2025@gmail.com. For cash in hand, we’ll contact you to arrange pickup/drop-off.</p>
        <p style="margin:16px 0 0; color:#0f172a; font-weight:700;">With gratitude,<br>The Giver Foundation Team</p>
      </td></tr>
    </table>
  </td></tr>
</table>
```

## 5) Report Notification Template (HTML)
Set **To** to `{{to_email}}`. Uses the handshake icon via `{{logo_url}}` for the header.
```html
<table width="100%" cellpadding="0" cellspacing="0" style="font-family:'Poppins',Arial,sans-serif; background:#f9fafb; padding:24px; color:#0f172a;">
  <tr><td>
    <table width="640" align="center" cellpadding="0" cellspacing="0" style="background:#ffffff; border-radius:18px; padding:0; box-shadow:0 14px 36px rgba(15,23,42,0.12); overflow:hidden;">
      <tr>
        <td style="background:linear-gradient(135deg,#2563eb 0%,#1d4ed8 100%); padding:18px 24px; text-align:left; color:#ffffff;">
          <table width="100%" cellpadding="0" cellspacing="0">
            <tr>
              <td style="vertical-align:middle;">
                <img src="{{logo_url}}" alt="The Giver Foundation" style="height:52px; width:auto; border-radius:12px; display:block;">
              </td>
              <td style="text-align:right; font-weight:700; font-size:14px; letter-spacing:0.2px; opacity:0.95;">New Report</td>
            </tr>
          </table>
        </td>
      </tr>
      <tr><td style="padding:24px 24px 28px;">
        <h2 style="margin:0 0 6px; color:#0f172a; font-size:22px;">A New Report Was Submitted</h2>
        <p style="margin:0 0 16px; color:#475569;">Review the details below.</p>
        <table width="100%" cellpadding="10" cellspacing="0" style="color:#0f172a; border:1px solid #e2e8f0; border-radius:12px;">
          <tr><td width="38%" style="color:#64748b;">Name</td><td>{{reporter_name}}</td></tr>
          <tr><td style="color:#64748b;">Email</td><td>{{reporter_email}}</td></tr>
          <tr><td style="color:#64748b;">Phone</td><td>{{phone}}</td></tr>
          <tr><td style="color:#64748b;">Location</td><td>{{location}}</td></tr>
          <tr><td style="color:#64748b;">Category</td><td>{{category}}</td></tr>
          <tr><td style="color:#64748b;">Urgency</td><td>{{urgency}}</td></tr>
          <tr><td style="color:#64748b;">Subject</td><td>{{subject}}</td></tr>
          <tr><td style="color:#64748b;">Description</td><td>{{description}}</td></tr>
          <tr><td style="color:#64748b;">Received Help Before</td><td>{{previous_help}}</td></tr>
          <tr><td style="color:#64748b;">Consent</td><td>{{consent}}</td></tr>
          <tr><td style="color:#64748b;">Submitted</td><td>{{timestamp}}</td></tr>
        </table>
        <p style="margin:16px 0 0; color:#475569;">Please follow up within 24-48 hours. Ensure consent is honored when contacting the reporter.</p>
      </td></tr>
    </table>
  </td></tr>
</table>
```

## 6) Report Confirmation Template (HTML)
Set **To** to `{{to_email}}` (the reporter’s email). Uses the handshake icon via `{{logo_url}}` for the header.
```html
<table width="100%" cellpadding="0" cellspacing="0" style="font-family:'Poppins',Arial,sans-serif; background:#f9fafb; padding:24px; color:#0f172a;">
  <tr><td>
    <table width="640" align="center" cellpadding="0" cellspacing="0" style="background:#ffffff; border-radius:18px; padding:0; box-shadow:0 14px 36px rgba(15,23,42,0.12); overflow:hidden;">
      <tr>
        <td style="background:linear-gradient(135deg,#2563eb 0%,#1d4ed8 100%); padding:18px 24px; text-align:left; color:#ffffff;">
          <table width="100%" cellpadding="0" cellspacing="0">
            <tr>
              <td style="vertical-align:middle;">
                <img src="{{logo_url}}" alt="The Giver Foundation" style="height:52px; width:auto; border-radius:12px; display:block;">
              </td>
              <td style="text-align:right; font-weight:700; font-size:14px; letter-spacing:0.2px; opacity:0.95;">Report Received</td>
            </tr>
          </table>
        </td>
      </tr>
      <tr><td style="padding:24px 24px 28px;">
        <h2 style="margin:0 0 6px; color:#0f172a; font-size:22px;">We Received Your Report</h2>
        <p style="margin:0 0 14px; color:#475569;">Hi {{reporter_name}}, thanks for reaching out. We’re reviewing your report and will contact you within 24-48 hours.</p>
        <table width="100%" cellpadding="10" cellspacing="0" style="color:#0f172a; border:1px solid #e2e8f0; border-radius:12px;">
          <tr><td width="38%" style="color:#64748b;">Subject</td><td>{{subject}}</td></tr>
          <tr><td style="color:#64748b;">Category</td><td>{{category}}</td></tr>
          <tr><td style="color:#64748b;">Urgency</td><td>{{urgency}}</td></tr>
          <tr><td style="color:#64748b;">Submitted</td><td>{{timestamp}}</td></tr>
        </table>
        <p style="margin:16px 0 0; color:#475569;">If anything changes or you need to add details, reply to this email.</p>
        <p style="margin:16px 0 0; color:#0f172a; font-weight:700;">With care,<br>The Giver Foundation Team</p>
      </td></tr>
    </table>
  </td></tr>
</table>
```

## 7) Recommended Subject Lines
- Foundation donation notification: `New Donation – {{donation_type}} via {{payment_method}}`
- Donor thank-you: `Thank You for Your Donation – The Giver Foundation`
- Report notification: `New Report – {{category}} ({{urgency}})`
- Report confirmation: `We Received Your Report – The Giver Foundation`

## 8) Hooking into `donate.js`
Replace placeholders in `js/donate.js`:
```
const EMAILJS_PUBLIC_KEY = 'YOUR_EMAILJS_PUBLIC_KEY';
const EMAILJS_SERVICE_ID = 'YOUR_EMAILJS_SERVICE_ID';
const EMAILJS_TEMPLATE_FOUNDATION = 'YOUR_FOUNDATION_TEMPLATE_ID';
const EMAILJS_TEMPLATE_DONOR = 'YOUR_DONOR_TEMPLATE_ID';
```
Also set a hosted logo URL in your template params:
```
const logoUrl = 'https://img.icons8.com/fluency/96/handshake.png';
// pass logo_url: logoUrl inside template params
```

## 9) Hooking into `report.js`
Replace placeholders in `js/report.js`:
```
const EMAILJS_PUBLIC_KEY = 'YOUR_EMAILJS_PUBLIC_KEY';
const EMAILJS_SERVICE_ID = 'YOUR_EMAILJS_SERVICE_ID';
const EMAILJS_TEMPLATE_REPORT_FOUNDATION = 'YOUR_REPORT_TEMPLATE_FOUNDATION';
const EMAILJS_TEMPLATE_REPORT_REPORTER = 'YOUR_REPORT_TEMPLATE_REPORTER';
const EMAILJS_LOGO_URL = 'https://img.icons8.com/fluency/96/handshake.png';
```
Pass `logo_url: EMAILJS_LOGO_URL` inside template params.

## 10) Required Template Params in EmailJS
Ensure both templates have these parameters defined in EmailJS:
- `donor_name`
- `donor_email`
- `amount`
- `donation_type`
- `payment_method`
- `anonymous`
- `timestamp`
- `to_email`
- `logo_url` (for the header image)

Report templates also need:
- `reporter_name`
- `reporter_email`
- `phone`
- `location`
- `category`
- `urgency`
- `subject`
- `description`
- `previous_help`
- `consent`

## 11) Testing
1) Open Donate page, choose Bank Transfer or Cash, fill the form, submit.
2) Expect two emails: one to foundation, one to donor (both show logo and brand colors).
3) If nothing arrives, check browser console for EmailJS errors and ensure keys/template IDs/logo URL are correct.
4) Open Report page, submit a report. Expect one email to foundation and one confirmation to the reporter.
