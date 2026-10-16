# 📲 Pushserver — by Samiul Islam

Firebase Cloud Messaging push-notification backend for Android apps.
Built with Node.js + Express + Firebase Admin SDK + Firestore.

**Live:** https://pushserver-9ghd.onrender.com

---

## 🚀 API

### 1. Register an app (once per APK)

```bash
curl -X POST https://pushserver-9ghd.onrender.com/register-app \
  -H "Content-Type: application/json" \
  -d '{"appId":"com.example.myapp","password":"your-password"}'
```

Password must be at least 6 characters. Save it — you need it for every other call.

### 2. Register a device token (from the APK)

```bash
curl -X POST https://pushserver-9ghd.onrender.com/register-token \
  -H "Content-Type: application/json" \
  -d '{"token":"FCM_TOKEN","appId":"com.example.myapp","password":"your-password"}'
```

### 3. Send to all devices of an app

```bash
curl -X POST https://pushserver-9ghd.onrender.com/send-all \
  -H "Content-Type: application/json" \
  -d '{"appId":"com.example.myapp","password":"your-password","title":"Hello","body":"Update available!"}'
```

### 4. Send to one device

`POST /send-notification` with `{"token":"...","title":"...","body":"..."}`

### 5. List / delete tokens

- `GET /tokens?appId=...&password=...`
- `DELETE /token?appId=...&token=...&password=...`

---

## ⚙️ Deployment

The Firebase service-account key is **never committed**. Production reads it from the
`FIREBASE_SERVICE_ACCOUNT` environment variable (JSON string).
For local development, place `serviceAccountKey.json` next to `index.js` (gitignored).

---

*Made by [Samiul Islam](https://github.com/samiul14)*
