# 💳 EventFinder - Payment Pages

Beautiful, responsive payment success and cancellation pages for Stripe Payment Links integration.

---

## 📁 Files

- **`success.html`** - Shown when payment is successful
- **`cancel.html`** - Shown when payment is cancelled

---

## 🚀 Deployment

### Option 1: GitHub Pages (Recommended)

1. **Create a new repository** named `eventfinder-payment-pages` or use your existing
   `eventfinder-app` repo

2. **Upload these files** to the repository

3. **Enable GitHub Pages**:
    - Go to: Repository → Settings → Pages
    - Source: Deploy from a branch
    - Branch: `main` or `master`
    - Folder: `/` (root)
    - Click Save

4. **Your pages will be available at**:
   ```
   https://paparatsi40.github.io/eventfinder-app/success.html
   https://paparatsi40.github.io/eventfinder-app/cancel.html
   ```

### Option 2: Custom Domain

If you have a custom domain, you can use:

```
https://yourdomain.com/payment/success
https://yourdomain.com/payment/cancel
```

---

## 🔗 Configure Stripe Payment Links

1. **Go to your Payment Links** in Stripe Dashboard:
   https://dashboard.stripe.com/test/payment-links

2. **Edit each Payment Link** (Boost, Featured, Premium)

3. **Configure "After payment"**:
    - **Success URL**:
      `https://paparatsi40.github.io/eventfinder-app/success.html?session_id={CHECKOUT_SESSION_ID}&plan={PLAN_NAME}`
    - **Cancel URL**:
      `https://paparatsi40.github.io/eventfinder-app/cancel.html?session_id={CHECKOUT_SESSION_ID}`

4. **Replace placeholders**:
    - `{CHECKOUT_SESSION_ID}` - Stripe will automatically replace this
    - `{PLAN_NAME}` - Replace with: `boost`, `featured`, or `premium`

### Example URLs

**For BOOST plan**:

```
Success: https://paparatsi40.github.io/eventfinder-app/success.html?session_id={CHECKOUT_SESSION_ID}&plan=boost
Cancel: https://paparatsi40.github.io/eventfinder-app/cancel.html?session_id={CHECKOUT_SESSION_ID}
```

**For FEATURED plan**:

```
Success: https://paparatsi40.github.io/eventfinder-app/success.html?session_id={CHECKOUT_SESSION_ID}&plan=featured
Cancel: https://paparatsi40.github.io/eventfinder-app/cancel.html?session_id={CHECKOUT_SESSION_ID}
```

**For PREMIUM plan**:

```
Success: https://paparatsi40.github.io/eventfinder-app/success.html?session_id={CHECKOUT_SESSION_ID}&plan=premium
Cancel: https://paparatsi40.github.io/eventfinder-app/cancel.html?session_id={CHECKOUT_SESSION_ID}
```

---

## ✨ Features

### Success Page

- ✅ Animated success icon
- ✅ Plan details display
- ✅ Automatic countdown (3 seconds)
- ✅ Auto-redirect to app using deep link
- ✅ Manual "Return to App" button
- ✅ Responsive design

### Cancel Page

- ❌ Clear cancellation message
- 💡 Reasons to promote (persuasion)
- 🔄 "Try Again" button
- 🏠 "Back to App" button
- 📧 Support contact link

---

## 📱 Deep Links

Both pages use deep links to return users to the app:

### Success Deep Link

```
eventfinder://payment/success?session_id={SESSION_ID}&transaction_id={TX_ID}
```

### Cancel Deep Link

```
eventfinder://promote/retry?event_id={EVENT_ID}
```

### Configure Deep Links in Android

Make sure your `AndroidManifest.xml` includes:

```xml
<activity android:name=".MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data
            android:scheme="eventfinder"
            android:host="payment" />
        <data
            android:scheme="eventfinder"
            android:host="promote" />
    </intent-filter>
</activity>
```

---

## 🧪 Testing

### Test Success Page

1. Open in browser: `success.html?session_id=test123&plan=featured`
2. Should show: Featured plan, 7 days duration
3. Countdown should start automatically
4. Button should try to open app

### Test Cancel Page

1. Open in browser: `cancel.html?event_id=test456`
2. Should show reasons to promote
3. Buttons should work

---

## 🎨 Customization

### Colors

The pages use EventFinder's brand colors:

- Primary: `#667eea` → `#764ba2` (gradient)
- Success: `#4CAF50`
- Cancel: `#ff6b6b`

### Timing

Success page redirect timer (line 238):

```javascript
let countdown = 3; // Change this value (seconds)
```

### Content

Edit the HTML directly to change:

- Messages
- Button text
- Support email
- Plan benefits

---

## 📊 Analytics (Optional)

Both pages include console logging. To add proper analytics:

```javascript
// In success.html (line 259)
// Replace with your analytics service
gtag('event', 'payment_success', { plan, sessionId });

// In cancel.html (line 261)
gtag('event', 'payment_cancelled', { sessionId, eventId });
```

---

## 🔐 Security Notes

- ✅ No sensitive data stored
- ✅ Session IDs are safe to pass in URLs
- ✅ All actual validation happens in Firebase Cloud Functions via webhook
- ✅ These pages are for UX only, not payment verification

---

## 📞 Support

If users need help:

- Email: support@eventfinder.com (update in `cancel.html`)
- In-app support chat (implement later)

---

## ✅ Checklist

- [ ] Upload files to GitHub
- [ ] Enable GitHub Pages
- [ ] Configure Payment Links in Stripe (3 plans)
- [ ] Test success page with real payment
- [ ] Test cancel flow
- [ ] Verify deep links work
- [ ] Update support email
- [ ] Add analytics (optional)

---

**Made with ❤️ for EventFinder**
