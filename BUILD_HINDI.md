# MDTrace — APK कैसे बनाएँ (GitHub se)

यह प्रोजेक्ट अब पूरी तरह बिल्ड-रेडी है। हर बार आने वाली एरर की वजहें ठीक कर दी गई हैं:
- `gradle.properties` जोड़ा गया (AndroidX बिना इसके बिल्ड फेल होता था)
- सही `gradle-wrapper.jar` + `gradlew` / `gradlew.bat` डाले गए (पहले टूटे हुए थे)
- `app/proguard-rules.pro` जोड़ा गया (build.gradle इसे ढूँढ रहा था)
- GitHub Actions workflow जोड़ा गया जो अपने-आप APK बनाता है

## तरीका A — GitHub पर अपने-आप APK बनेगा (सबसे आसान)
1. इस फोल्डर की सारी फाइलें अपनी GitHub repository में push/upload करें
   (यह ज़िप खोलकर पूरा `MDTrace-Android` फोल्डर अपलोड करें — सभी छिपी फाइलें भी,
    जैसे `.github` फोल्डर ज़रूरी है)।
2. GitHub पर repo खोलें → ऊपर **Actions** टैब पर जाएँ।
3. "Build APK" workflow अपने-आप चल जाएगा (या बाईं तरफ़ से चुनकर
   **Run workflow** दबाएँ)।
4. ~3–5 मिनट बाद हरा टिक ✅ आने पर उस run को खोलें।
5. नीचे **Artifacts** में **MDTrace-APK** दिखेगा — उसे डाउनलोड करें।
   अंदर `MDTrace.apk` मिलेगा। फ़ोन में इंस्टॉल कर लें।

> नोट: GitHub Actions का artifact एक ZIP में आता है — उसे खोलकर अंदर से
> `MDTrace.apk` निकालें।

## तरीका B — अपने कंप्यूटर पर बनाएँ
शर्त: JDK 17 और Android SDK (platform 34, build-tools 34.0.0) इंस्टॉल हों।
```
./gradlew assembleDebug
```
APK यहाँ बनेगा: `app/build/outputs/apk/debug/app-debug.apk`

## ज़रूरी
- पहली बार खोलने पर Location permission **"हर समय / Allow all the time"** दें,
  वरना background tracking नहीं चलेगी।
