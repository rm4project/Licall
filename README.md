# 📡 אינטרקום חי - PWA WebRTC

## מה זה?
מערכת אינטרקום בשידור חי המאפשרת שיחת וידאו/קול ישירה בין מכשירים כמו:
- מחשב במשרד ↔ טלפון אנדרואיד
- מחשב ↔ אייפון
- כל שני מכשירים עם דפדפן מודרני

## טכנולוגיה
- **WebRTC** - חיבור P2P ישיר (ללא שרת לאחר ה-handshake)
- **STUN/TURN** - שרתי Google + OpenRelay לחציית NAT
- **PWA** - ניתן להתקנה כאפליקציה נייטיבית
- **Signaling** - localStorage + StorageEvent לאותו מכשיר/תב

## התקנה מהירה

### אפשרות 1: שרת מקומי (מומלץ לבדיקה)
```bash
# Python
python3 -m http.server 8080

# Node.js
npx serve .

# אז פתח: http://localhost:8080
```

### אפשרות 2: Netlify Drop
1. גרור את תיקיית `intercom-pwa` ל-app.netlify.com/drop
2. תקבל URL מאובטח (HTTPS) מיד

### אפשרות 3: GitHub Pages
1. העלה לריפוזיטורי GitHub
2. הפעל GitHub Pages מה-Settings
3. גש ל-`https://username.github.io/intercom-pwa`

## שימוש

### מחשב (יוצר חדר):
1. פתח את ה-URL
2. לחץ "מצלמה + מיק" לאישור הרשאות
3. לחץ "צור חדר חדש"
4. קבל קוד 4 ספרות
5. שלח את הקוד לצד השני

### מכשיר נייד (מצטרף):
1. פתח את אותו URL
2. אשר הרשאות מדיה
3. לחץ "הצטרף לחדר"
4. הזן את הקוד

> **חשוב:** שני המכשירים חייבים לגשת לאותו URL!
> לחיבור בין מכשירים שונים (לא אותה LAN) - הפרוס ב-HTTPS ציבורי.

## הגבלות localStorage
- Signaling דרך localStorage עובד רק כשאותו URL נגיש בשניהם
- לחיבור cross-device: הפרוס ב-Netlify/Vercel עם HTTPS

## דרישות
- Chrome 80+ / Safari 14+ / Firefox 78+
- HTTPS (חובה למצלמה/מיקרופון בדפדפן)
- חיבור אינטרנט (לשלב ה-signaling)
