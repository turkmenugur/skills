# Belge Template'leri

Her belge için skeleton template. Bu template'leri **harfi harfine doldurmak yerine** uygulamaya özel içerik üretmek için başlangıç noktası olarak kullan. Başlıkları değiştirmemeye çalış — kullanıcı birden fazla proje oluşturduğunda tutarlılık önemli.

---

## FEATURES.md Template

```markdown
# [Uygulama Adı] — Feature List

> Son güncelleme: [tarih]
> Versiyon hedefi: v1.0 (MVP)

## Öncelik Sistemi
- **P0** — MVP için zorunlu. Bunlar olmadan uygulama çalışmaz.
- **P1** — v1.0'da olması güçlü tercih. Kullanıcı deneyimini tamamlar.
- **P2** — Sonraki sürümler için. Backlog'da bekleyebilir.

---

## P0 — MVP Core

### [Özellik Adı]
**Kullanıcı hikayesi:** [Kullanıcı rolü] olarak, [hedef], [çünkü gerekçe].
**Kapsam:**
- [ ] [Alt görev 1]
- [ ] [Alt görev 2]
**Bağımlılıklar:** [Başka özellik / servis]
**Notlar:** [Önemli teknik not veya edge case]

### [Özellik Adı 2]
...

---

## P1 — v1.0 Tamamlayıcı

### [Özellik Adı]
...

---

## P2 — Gelecek Sürümler

- [ ] [Özellik] — [kısa açıklama]
- [ ] [Özellik] — [kısa açıklama]

---

## Kapsam Dışı (Açıkça Belirtilenler)
Bu sürümde **kasıtlı olarak** dahil edilmeyecek şeyler:
- [Neden dahil edilmediğiyle birlikte]
```

---

## STACK.md Template

```markdown
# [Uygulama Adı] — Tech Stack

> Bu stack [tarih] itibarıyla seçilmiştir. Temel gerekçeler notlanmıştır.

## Platform & Framework

| Alan | Seçim | Versiyon | Gerekçe |
|---|---|---|---|
| Framework | [React Native / Flutter / Swift / Kotlin] | [vX.X] | [neden] |
| Build Aracı | [Expo EAS / Xcode / Gradle] | — | [neden] |
| Dil | [TypeScript / Dart / Swift / Kotlin] | — | [neden] |
| Min OS | iOS [X]+ / Android [X]+ | — | — |

## State Management

| Alan | Seçim | Gerekçe |
|---|---|---|
| Client state | [Zustand / Riverpod / vb.] | [neden] |
| Server state | [React Query / SWR / vb.] | [neden] |
| Persistence | [MMKV / AsyncStorage / vb.] | [neden] |

## Backend & Servisler

| Alan | Seçim | Gerekçe |
|---|---|---|
| Auth | [Supabase Auth / Firebase Auth / Custom] | [neden] |
| Database | [Supabase Postgres / Firestore / vb.] | [neden] |
| Storage | [Supabase Storage / S3 / vb.] | [neden] |
| Real-time | [Supabase Realtime / Firebase / yok] | [neden] |
| Push notification | [expo-notifications / FCM] | [neden] |

## UI & Animasyon

| Alan | Seçim | Gerekçe |
|---|---|---|
| Komponent sistemi | [NativeWind / Tamagui / vb.] | [neden] |
| İkonlar | [Expo Icons / react-native-vector-icons] | — |
| Animasyon | [Reanimated 3 / vb.] | [neden] |
| Gesture | [Gesture Handler] | — |

## Navigation

[React Navigation v7 — Stack + Tab yapılandırması]

## Testing & Kalite

| Alan | Seçim |
|---|---|
| Unit test | Jest + React Native Testing Library |
| E2E | Detox / Maestro |
| Crash reporting | Sentry |
| Analytics | [PostHog / Mixpanel / vb.] |

## Geliştirme Araçları

| Alan | Seçim |
|---|---|
| Linter | ESLint + Prettier |
| Tip kontrolü | TypeScript strict mode |
| Pre-commit | Husky + lint-staged |
| CI/CD | GitHub Actions + EAS Build |

## Paket Listesi (package.json özeti)

\`\`\`json
{
  "dependencies": {
    // Core
    "expo": "~XX.X.X",
    "react-native": "X.XX.X",
    // [diğer paketler listelenecek]
  }
}
\`\`\`

## Bilinen Riskler & Alternatifler

- **[Seçim]**: [Risk]. Alternatif: [Alternatif seçim, neden tercih edilmedi]
```

---

## ARCHITECTURE.md Template

```markdown
# [Uygulama Adı] — Architecture

## Klasör Yapısı

\`\`\`
src/
├── app/                    # Expo Router ekranları veya navigasyon konfigürasyonu
│   ├── (auth)/             # Auth gerektiren ekranlar (route group)
│   └── (public)/           # Auth gerektirmeyen ekranlar
├── components/
│   ├── ui/                 # Temel UI primitifleri (Button, Input, Card...)
│   └── features/           # Feature-specific componentler
│       ├── [feature-1]/
│       └── [feature-2]/
├── hooks/                  # Custom React hooks
├── services/               # API çağrıları, dış servis entegrasyonları
│   ├── api/                # REST/GraphQL istek fonksiyonları
│   └── [service-name]/     # Supabase, Firebase vb.
├── stores/                 # State yönetimi (Zustand store'ları)
├── utils/                  # Pure utility fonksiyonlar
├── types/                  # TypeScript tip tanımları
├── constants/              # Sabitler (renkler, boyutlar, config)
└── assets/                 # Görseller, fontlar, ses dosyaları
\`\`\`

## Veri Akışı

\`\`\`
[Kullanıcı Etkileşimi]
        ↓
[Component / Screen]
        ↓
[Store Action (Zustand)] ←→ [React Query (server state)]
        ↓                           ↓
[Local State Update]        [API / Supabase]
        ↓                           ↓
[UI Re-render]              [Cache Update]
\`\`\`

## Ekran Listesi & Navigation

\`\`\`
RootNavigator
├── AuthStack
│   ├── LoginScreen
│   ├── RegisterScreen
│   └── ForgotPasswordScreen
└── AppStack (auth required)
    ├── TabNavigator
    │   ├── HomeScreen
    │   ├── [Tab2]Screen
    │   └── ProfileScreen
    └── [diğer ekranlar]
\`\`\`

## State Mimarisi

### Client State (Zustand)
\`\`\`typescript
// stores/[domain]Store.ts yapısı
interface [Domain]State {
  // state alanları
}
interface [Domain]Actions {
  // action tanımları
}
\`\`\`

### Server State (React Query)
- Query keys: `['resource', 'list', filters]` formatı
- Stale time: [X dakika] — [gerekçe]
- Cache time: [Y dakika]

## API Tasarımı

### Endpoint'ler

| Method | Path | Açıklama | Auth |
|---|---|---|---|
| GET | `/api/[resource]` | Liste getir | ✅ |
| POST | `/api/[resource]` | Yeni oluştur | ✅ |
| PUT | `/api/[resource]/:id` | Güncelle | ✅ |
| DELETE | `/api/[resource]/:id` | Sil | ✅ |

### Supabase Schema (varsa)

\`\`\`sql
-- [tablo adı]
create table [table] (
  id uuid primary key default gen_random_uuid(),
  user_id uuid references auth.users(id) on delete cascade,
  created_at timestamptz default now(),
  -- [diğer kolonlar]
);

-- RLS
alter table [table] enable row level security;
create policy "[table] owner access" on [table]
  for all using (auth.uid() = user_id);
\`\`\`

## Güvenlik

- Auth token'ları MMKV secure store'da tutulur
- API key'ler `.env` + Expo Constants üzerinden enjekte edilir, commit'lenmez
- RLS tüm Supabase tablolarında aktif
- Hassas ekranlarda `expo-local-authentication` ile biyometrik kilit (opsiyonel)

## Performance Notları

- [Performans kararı 1 ve gerekçesi]
- [Performans kararı 2 ve gerekçesi]
```

---

## PLAN.md Template

```markdown
# [Uygulama Adı] — Geliştirme Planı

> Geliştirici: Solo / [Takım büyüklüğü]
> Hedef ship tarihi: [Tarih / "TBD"]

## Özet Takvim

| Aşama | Süre | Çıktı |
|---|---|---|
| Aşama 1 — Setup & Altyapı | [X gün/hafta] | Çalışan iskelet uygulama |
| Aşama 2 — Core Features (P0) | [X gün/hafta] | MVP kullanılabilir |
| Aşama 3 — P1 Features | [X gün/hafta] | v1.0 feature complete |
| Aşama 4 — Polish & Launch | [X gün/hafta] | App Store'da |

---

## Aşama 1 — Setup & Altyapı

**Hedef:** Temiz, deploy edilebilir bir başlangıç noktası.

- [ ] Expo projesi oluştur (`npx create-expo-app`)
- [ ] TypeScript strict mode konfigürasyonu
- [ ] ESLint + Prettier kurulumu
- [ ] Klasör yapısını oluştur (src/ altında)
- [ ] Navigation skeleton (React Navigation kurulumu)
- [ ] [Backend] kurulumu ve bağlantı testi
- [ ] `.env` yapısını oluştur, Expo Constants ile bağla
- [ ] Temel UI komponentleri: Button, Input, Screen, Text
- [ ] Renk ve tipografi constants dosyası
- [ ] Sentry entegrasyonu

**Milestone:** Hello World ekran çalışıyor, backend bağlantısı test edildi.

---

## Aşama 2 — Core Features (P0)

**Hedef:** FEATURES.md'deki tüm P0 özellikleri çalışıyor.

### [P0 Özellik Adı 1]
- [ ] [Alt görev]
- [ ] [Alt görev]

### [P0 Özellik Adı 2]
- [ ] [Alt görev]
- [ ] [Alt görev]

**Milestone:** Uygulamanın temel akışı uçtan uca çalışıyor (happy path).

---

## Aşama 3 — P1 Features

**Hedef:** FEATURES.md'deki tüm P1 özellikleri çalışıyor.

### [P1 Özellik Adı 1]
- [ ] [Alt görev]

**Milestone:** Uygulama gerçek kullanıcıya gösterilebilir hale geldi.

---

## Aşama 4 — Polish & Launch

- [ ] UX polish (loading states, error states, empty states)
- [ ] Offline davranışı gözden geçir
- [ ] Performans profiling (Flipper / React Native DevTools)
- [ ] App icon ve splash screen
- [ ] App Store / Play Store metadata (açıklama, ekran görüntüleri)
- [ ] TestFlight / Internal Test dağıtımı
- [ ] Beta test (en az 5 kullanıcı)
- [ ] Crash ve analitik dashboard kontrolü
- [ ] App Store review submit

**Milestone:** 🚀 Uygulama App Store / Play Store'da yayında.

---

## Risk & Varsayımlar

| Risk | Olasılık | Etki | Azaltma |
|---|---|---|---|
| [Risk 1] | Orta | Yüksek | [Plan B] |
| [Risk 2] | Düşük | Orta | [Plan B] |

## Sonraki Sürüm İçin Notlar

Bu plana sığmayan ama unutulmaması gereken şeyler:
- [Not 1]
```

---

## DESIGN.md Template

```markdown
# [Uygulama Adı] — Design System

> Bu dosya hem geliştirme referansı hem de LLM'e prompt bağlamı olarak kullanılır.

## Genel Estetik

**Tone:** [Modern minimalist / Canlı ve enerjik / Güven verici profesyonel / vb.]
**Referans uygulamalar:** [Benzer estetikteki 2-3 uygulama]
**Hedef his:** Kullanıcı uygulamayı açtığında [X] hissetmeli.

---

## Renk Sistemi

\`\`\`typescript
// constants/colors.ts
export const Colors = {
  // Brand
  primary: '[hex]',       // Ana eylem rengi — butonlar, CTA'lar
  primaryDark: '[hex]',   // Hover / pressed state
  secondary: '[hex]',     // Destekleyici vurgu

  // Nötr
  background: '[hex]',    // Sayfa arka planı
  surface: '[hex]',       // Kart, sheet arka planı
  border: '[hex]',        // Ayırıcı çizgiler

  // Tipografi
  textPrimary: '[hex]',   // Ana metin
  textSecondary: '[hex]', // İkincil / açıklama metni
  textDisabled: '[hex]',  // Devre dışı

  // Durum
  success: '[hex]',
  warning: '[hex]',
  error: '[hex]',
  info: '[hex]',

  // Dark mode (varsa)
  dark: {
    background: '[hex]',
    surface: '[hex]',
    // ...
  }
};
\`\`\`

---

## Tipografi

\`\`\`typescript
// constants/typography.ts
export const Typography = {
  // Font ailesi
  fontFamily: {
    regular: '[Font adı]',    // Gövde metni
    medium: '[Font adı]',     // Vurgular
    bold: '[Font adı]',       // Başlıklar
    mono: '[Font adı]',       // Kod / sayısal değerler
  },

  // Boyutlar
  sizes: {
    h1: 32,   // Sayfa başlıkları
    h2: 24,   // Bölüm başlıkları
    h3: 20,   // Kart başlıkları
    body1: 16, // Ana gövde metni
    body2: 14, // İkincil gövde
    caption: 12, // Etiket, metadata
    tiny: 10,    // Yasal, çok küçük
  },

  // Satır yüksekliği çarpanı
  lineHeights: {
    tight: 1.2,
    normal: 1.5,
    relaxed: 1.8,
  }
};
\`\`\`

---

## Spacing & Layout

\`\`\`typescript
// constants/spacing.ts — 4px grid sistemi
export const Spacing = {
  xs: 4,
  sm: 8,
  md: 16,   // Standart padding
  lg: 24,
  xl: 32,
  xxl: 48,
};

export const Layout = {
  screenPadding: 16,      // Ekran kenar boşluğu
  cardBorderRadius: 12,   // Kart köşe yuvarlama
  buttonBorderRadius: 8,  // Buton köşe yuvarlama
  maxContentWidth: 480,   // Tablet'te max içerik genişliği
};
\`\`\`

---

## Komponent Kütüphanesi

### Temel Komponentler

| Komponent | Kullanım | Özel Notlar |
|---|---|---|
| `<PrimaryButton>` | CTA, form submit | Primary renk, 48px yüksek |
| `<SecondaryButton>` | İkincil aksiyon | Border, transparan bg |
| `<TextButton>` | Tertiary / link | Sadece metin |
| `<Input>` | Form alanları | Label + error state dahil |
| `<Card>` | İçerik container | surface bg, shadow |
| `<Screen>` | Sayfa wrapper | Safe area + scroll |
| `<Avatar>` | Kullanıcı resmi | Fallback initial letters |
| `<Badge>` | Sayı / durum etiketi | |
| `<Skeleton>` | Loading placeholder | |

### Feature Komponentler

| Komponent | Kullanım |
|---|---|
| `<[FeatureCard]>` | [Açıklama] |
| `<[FeatureList]>` | [Açıklama] |

---

## Ekran Envanteri

| # | Ekran Adı | Route | Açıklama |
|---|---|---|---|
| 1 | Onboarding | `/onboarding` | İlk açılışta gösterilir |
| 2 | Login | `/auth/login` | |
| 3 | Register | `/auth/register` | |
| 4 | Home | `/(app)/` | Ana tab |
| 5 | [Ekran] | `/(app)/[route]` | |
| 6 | Profile | `/(app)/profile` | |
| 7 | Settings | `/(app)/settings` | |

---

## İkonografi

**Kütüphane:** [@expo/vector-icons — Ionicons]
**Boyut standartları:**
- Navigation tab: 24px
- İçerik içi: 20px
- Küçük/inline: 16px

**Sık kullanılan ikonlar:**

| Kullanım | İkon adı |
|---|---|
| Ana sayfa | `home-outline` / `home` |
| Arama | `search-outline` |
| Profil | `person-outline` / `person` |
| Geri | `arrow-back` |
| Kapat | `close` |
| Daha fazla | `ellipsis-horizontal` |

---

## Animasyon Prensipleri

- **Süre:** Çoğu geçiş 200-300ms; enter animasyonları 300-400ms
- **Easing:** `spring` ilk tercih (doğal his); `easeOut` sayfa geçişleri için
- **Prensip:** Animasyon kullanıcıya bilgi vermelidir (state change, hierarchy)
- **Erişilebilirlik:** `useReducedMotion()` ile animasyonları kapat seçeneği sun

---

## Dark Mode

[Dark mode desteği: Evet / Hayır / Sonraki sürümde]

Evet ise: React Native'in `useColorScheme()` hook'u + Colors.dark objesi
\`\`\`

---

## Notlar

- Template'lerdeki tüm `[köşeli parantez]` ifadeleri uygulamaya özel içerikle doldurulmalı
- Kod blokları doğrudan projeye kopyalanabilecek netlikte yazılmalı
- Her dosya kendi başına okunabilir ve LLM'e prompt bağlamı olarak verilebilir olmalı
