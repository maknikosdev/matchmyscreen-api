# 📱 MatchMyScreen
### Συμβατότητα Προστασίας Οθονών

> Βρες ποια tempered glass ή μεμβράνη hydrogel ταιριάζει στο κινητό σου — ακόμα και από άλλα μοντέλα με ίδιες διαστάσεις οθόνης.

---

## 📌 Τι κάνει η εφαρμογή

Το **MatchMyScreen** αναζητά live τα τεχνικά χαρακτηριστικά των οθονών των κινητών και συγκρίνει:

- 📐 **Φυσικές διαστάσεις οθόνης** (ύψος × πλάτος σε mm)
- 🖥️ **Τύπο οθόνης** (επίπεδη / καμπύλη Edge / 2.5D)
- 📷 **Θέση κάμερας / notch** (punch-hole, Dynamic Island, waterdrop κ.λπ.)

Αποτελέσματα σε 3 κατηγορίες:

| Κατηγορία | Διαφορά | Περιγραφή |
|-----------|:-------:|-----------|
| ✅ Απόλυτη Συμβατότητα | ≤ 0.3mm | Τοποθετείται τέλεια |
| ⚠️ Μερική Συμβατότητα | ≤ 1.2mm | Μικρό κενό στο notch |
| 🔵 Μόνο Hydrogel / TPU | ≤ 2.5mm | Μόνο ελαστικές μεμβράνες |

---

## 📦 Διαθέσιμες εκδόσεις

| Έκδοση | Πλατφόρμα | Τεχνολογία |
|--------|-----------|-----------|
| 📱 Mobile App | Android | React Native / Expo |
| 🖥️ Desktop App | Windows (.exe) | Electron + React |
| 🌐 Backend API | Cloud (Render) | Node.js / Express |

---

## 🏗️ Αρχιτεκτονική

```
┌─────────────────────┐     ┌─────────────────────┐
│   Android App       │     │   Windows App        │
│   (React Native)    │     │   (Electron)         │
└────────┬────────────┘     └──────────┬───────────┘
         │                             │
         └──────────┬──────────────────┘
                    │ HTTPS API
         ┌──────────▼──────────────────┐
         │   Backend (Render.com)      │
         │   Node.js + Express         │
         │   Cache 24h                 │
         └──────────┬──────────────────┘
                    │
         ┌──────────▼──────────────────┐
         │   phones-database.json      │
         │   751+ συσκευές             │
         │   31 brands · 2014-2026     │
         └─────────────────────────────┘
```

---

## 📱 Brands που υποστηρίζονται (751+ μοντέλα)

**Flagship:** Apple · Samsung · Xiaomi · Redmi · POCO

**Mainstream:** Motorola · Realme · OnePlus · Honor · Google · Oppo · Nothing · CMF · Vivo

**Premium / Gaming:** Sony · Asus · ZTE

**VFM / Budget:** TCL · Nokia · Infinix · Tecno · Cubot

**Rugged:** Blackview · Ulefone · Doogee · Caterpillar · FOSSiBOT · HOTWAV · AGM

**Special:** Huawei · Lenovo

---

## 🗂️ Δομή Repository

```
matchmyscreen-api/
├── server.js                 ← Backend API (Express)
├── package.json              ← Dependencies
├── Procfile                  ← Render/Railway start command
├── railway.json              ← Railway config
├── nixpacks.toml             ← Build config
└── phones-database.json      ← Βάση δεδομένων συσκευών
```

---

## 🚀 Backend API — Endpoints

| Endpoint | Περιγραφή |
|----------|-----------|
| `GET /health` | Server status + αριθμός συσκευών |
| `GET /brands` | Λίστα όλων των brands |
| `GET /models?brand=Samsung` | Μοντέλα brand |
| `GET /specs?id=galaxy-s25` | Specs συσκευής |
| `GET /search?q=iphone+16` | Αναζήτηση |
| `GET /reload?key=ADMIN_KEY` | Force ανανέωση cache |

---

## ➕ Πώς να προσθέσεις νέο μοντέλο

Άνοιξε το `phones-database.json`, βρες το brand και πρόσθεσε:

```json
{
  "id": "galaxy-s26-ultra",
  "model": "Galaxy S26 Ultra",
  "brand": "Samsung",
  "year": 2026,
  "screenSize": 6.9,
  "dimensions": { "h": 163.0, "w": 78.0 },
  "screenDimensions": { "h": 155.5, "w": 73.5 },
  "screenType": "flat",
  "notch": "punch-hole",
  "glassType": "gorilla-armour2"
}
```

**Τιμές `screenType`:** `flat` · `curved` · `flat-2.5d`

**Τιμές `notch`:** `none` · `notch` · `punch-hole` · `pill` · `waterdrop` · `bar`

Μετά κάνε commit και κάλεσε:
```
https://matchmyscreen-api.onrender.com/reload?key=YOUR_ADMIN_KEY
```

---

## 🔄 Ροή ενημέρωσης βάσης δεδομένων

```
1. Επεξεργασία phones-database.json
        ↓
2. Commit & Push στο GitHub
        ↓
3. Render κάνει αυτόματο redeploy
        ↓
4. /reload?key=... για άμεση ανανέωση
        ↓
5. Χρήστες βλέπουν τα νέα μοντέλα ✅
```

---

## ⚖️ Αποποίηση Ευθύνης

Τα τεχνικά χαρακτηριστικά των συσκευών αποτελούν δημόσια δεδομένα των κατασκευαστών και χρησιμοποιούνται αποκλειστικά για ενημερωτικούς σκοπούς συμβατότητας.

---

## 📊 Στατιστικά βάσης

- **751+** συσκευές
- **31** brands
- **2014 – 2026** χρονική κάλυψη
- Ενημερώνεται χειροκίνητα με κάθε νέο μοντέλο

---

*© 2026 MatchMyScreen · Συμβατότητα Προστασίας Οθονών*
