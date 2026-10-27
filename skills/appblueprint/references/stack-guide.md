# Stack Seçim Rehberi

Bu dosya, uygulama tipine göre en uygun stack'i seçmek için kullanılır. Her bölüm bir karar ağacı veya seçim tablosu içerir.

---

## 1. Framework Seçimi

### Karar Ağacı

```
Yalnızca iOS mu?
  └─ Evet → Swift + SwiftUI
  └─ Hayır ↓

Yalnızca Android mı?
  └─ Evet → Kotlin + Jetpack Compose
  └─ Hayır ↓

Cross-platform →
  ├─ Animasyon yoğun / yüksek UI karmaşıklığı? → Flutter (Dart)
  ├─ Web deneyimi varsa / JS ekibi? → React Native + Expo
  ├─ Oyun / 3D / AR ağırlıklı? → Unity veya özel değerlendirme
  └─ Genel amaç, solo dev, hızlı ship → React Native + Expo (önerilen)
```

### Karşılaştırma Tablosu

| Kriter | React Native + Expo | Flutter | Swift | Kotlin |
|---|---|---|---|---|
| Başlangıç hızı | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| UI esnekliği | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Native özellikler | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Performans | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Ekosistem / paket | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Vibecoding kolaylığı | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |

---

## 2. Backend Seçimi

### Backend Gerekli mi?

| Senaryo | Öneri |
|---|---|
| Tamamen lokal uygulama (notes, tracker) | Backend yok, SQLite / MMKV |
| Auth + basit DB yeterli | Supabase (hızlı, ücretsiz tier iyi) |
| Real-time (chat, collab) | Supabase Realtime veya Firebase |
| Karmaşık iş mantığı / custom API | Node.js + Express / Fastify veya Go |
| Serverless tercih | Supabase Edge Functions veya Vercel Functions |
| Mevcut bir backend var | Mevcut API'yi kullan, adaptör yaz |

### BaaS Karşılaştırması

| | Supabase | Firebase | Pocketbase | Appwrite |
|---|---|---|---|---|
| Open source | ✅ | ❌ | ✅ | ✅ |
| SQL | ✅ (Postgres) | ❌ | ✅ (SQLite) | ✅ |
| Self-host | ✅ | ❌ | ✅ (tek binary) | ✅ |
| Real-time | ✅ | ✅ | ✅ | ✅ |
| Free tier | Cömert | Sınırlı | Self-host | Self-host |
| **Öneri** | **Çoğu proje için** | Legacy projelerde | Side project / solo | Side project |

---

## 3. State Management (React Native)

| Uygulama karmaşıklığı | Öneri |
|---|---|
| Küçük / az ekran | useState + useContext |
| Orta (5-15 ekran) | Zustand (minimal boilerplate) |
| Büyük / ekip projesi | Zustand + React Query (server state ayrımı) |
| Redux alışkanlığı varsa | Redux Toolkit (RTK Query ile) |

**Genel kural:** Zustand + React Query kombinasyonu çoğu proje için altın standarttır. Zustand client state için, React Query server state için.

---

## 4. Navigation (React Native)

- **React Navigation v7** — standart, expo uyumlu, her proje için
  - Stack Navigator: ekran geçişleri
  - Tab Navigator: ana navigasyon
  - Drawer Navigator: yan menü
- **Expo Router** — file-based routing, web de hedefliyorsan ideal

---

## 5. Lokal Storage

| Veri tipi | Öneri |
|---|---|
| Key-value (settings, session) | MMKV (AsyncStorage'dan 10x hızlı) |
| Relational / karmaşık | WatermelonDB veya SQLite (expo-sqlite) |
| Offline-first sync | WatermelonDB + Supabase sync |
| Basit JSON persist | Zustand + MMKV persist middleware |

---

## 6. UI Component Library (React Native)

| Kütüphane | Ne zaman? |
|---|---|
| **NativeWind (Tailwind)** | Tailwind bilen solo dev, hızlı prototip |
| **Tamagui** | Performans kritik, cross-platform (web+mobile) |
| **UI Kitten** | Enterprise, tema sistemi önemli |
| **Gluestack UI v2** | RSC uyumlu, modern stack |
| **Sıfırdan (StyleSheet)** | Full kontrol istiyorsan, küçük UI surface |

---

## 7. Animasyon

| İhtiyaç | Kütüphane |
|---|---|
| Basit geçişler, spring | React Native Reanimated 3 |
| Gesture + animasyon | Reanimated + React Native Gesture Handler |
| Lottie dosyası (JSON anim) | lottie-react-native |
| Kompleks sekanslar | Reanimated + Skia |

---

## 8. Bildirimler

| Senaryo | Öneri |
|---|---|
| Push notification (Expo) | expo-notifications + Expo Push Service |
| Push notification (bare) | Firebase Cloud Messaging (FCM) |
| Lokal bildirim | expo-notifications |
| Scheduled | expo-notifications ile scheduling |

---

## 9. Analytics & Crash Reporting

| Araç | Açıklama |
|---|---|
| **Sentry** | Crash reporting, performans izleme — standart seçim |
| **PostHog** | Open source, event analytics, free self-host |
| **Mixpanel** | Funnel analizi, retention — freemium |
| **Firebase Analytics** | Firebase kullanıyorsan dahil gelir |

---

## 10. Monetization Stack

| Model | Araçlar |
|---|---|
| In-app purchase / subscription | `react-native-purchases` (RevenueCat) — en kolay |
| One-time purchase | App Store / Play Store native IAP |
| Ads | Google AdMob (`expo-ads-admob` veya `react-native-google-mobile-ads`) |
| Web ödeme + mobile | Stripe + kendi backend |

---

## 11. Flutter'a Özel Notlar

- State: Riverpod (en modern) > Bloc (enterprise) > Provider (legacy)
- Routing: GoRouter (standart)
- Network: Dio + Retrofit
- Local DB: Hive (NoSQL) veya Drift (SQL)
- DI: get_it + injectable
- UI: Material 3 + custom, ya da shadcn benzeri için FlexColorScheme

---

## 12. Expo vs Bare React Native

| | Expo (Managed) | Bare RN |
|---|---|---|
| Setup | ⚡ Anında | Zaman alır |
| Native module | Sınırlı ama genellikle yeterli | Her şey mümkün |
| OTA update | ✅ (EAS Update) | ❌ |
| Build | EAS Build (cloud) | Local + CI/CD |
| **Öneri** | **Yeni projelerin %90'ı** | Özel native gereksinim varsa |

> **Default öneri:** Expo ile başla, ihtiyaç olursa `expo eject` ile bare'e geç. Bunu STACK.md'de açıkça belirt.
