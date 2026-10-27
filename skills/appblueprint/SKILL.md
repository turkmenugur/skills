---
name: appblueprint
description: >
  Transforms a raw mobile app idea into a full set of structured planning documents: STACK.md (tech stack with reasoning), PLAN.md (phased development roadmap), DESIGN.md (UI/UX system and screen list), FEATURES.md (prioritized feature breakdown with user stories), and ARCHITECTURE.md (folder structure, data flow, state management). Activate this skill whenever the user describes a mobile app idea, says "I want to build an app", "yeni bir uygulama fikrim var", "bir app geliştirmek istiyorum", mentions vibecoding, or asks for an app blueprint, tech stack, or dev plan. Also trigger when the user pastes a raw idea and wants structure, even if they don't mention specific documents. This is the go-to skill for turning rough ideas into actionable, vibecoding-ready plans.
---

# AppBlueprint — Fikri Plana Dönüştür

Bir mobil uygulama fikrini alır; geliştiricinin hemen kodlamaya başlayabileceği 5 yapılandırılmış belge üretir.

## Üretilen Dosyalar

| Dosya | İçerik |
|---|---|
| `STACK.md` | Framework, kütüphane ve servis seçimleri + gerekçeleri |
| `PLAN.md` | Aşamalı geliştirme yol haritası, milestone'lar, görevler |
| `DESIGN.md` | Renk sistemi, tipografi, komponent listesi, ekran envanteri |
| `FEATURES.md` | Önceliklendirilmiş özellikler (P0/P1/P2), kullanıcı hikayeleri |
| `ARCHITECTURE.md` | Klasör yapısı, veri akışı, state yönetimi, API tasarımı |

---

## Workflow

### Adım 1 — Fikri Anla

Kullanıcının mesajından şu bilgileri çıkarmaya çalış. Eksik olanları **tek seferde**, sohbet akışını bozmayan kısa sorularla sor:

**Zorunlu:**
- Uygulama ne yapıyor? (core problem)
- Hedef platform: iOS / Android / İkisi (cross-platform)
- Hedef kullanıcı kitlesi

**Önemli ama tahmin edilebilir:**
- Teknik tercih var mı? (React Native, Flutter, Swift, Kotlin — yoksa sen öner)
- Backend gerekli mi? (auth, database, real-time, vb.)
- Monetization modeli var mı? (freemium, subscription, one-time, ads)

Eğer kullanıcı yeterli bağlam verdiyse, soru sormadan direkt devam et. Tahmin ettiğin şeyleri STACK.md içinde açıkça belirt.

### Adım 2 — Stack Seçimi

`references/stack-guide.md` dosyasını oku. Uygulama tipine göre en uygun stack'i seç ve STACK.md'ye gerekçeyle yaz.

Stack seçerken şu sinyallere dikkat et:
- Solo geliştirici + hızlı ship → React Native veya Flutter
- Animasyon ağırlıklı / yüksek UI karmaşıklığı → Flutter
- Native özellik bağımlılığı (ARKit, HealthKit vb.) → Swift/Kotlin + bridge
- Mevcut web/RN ekibi varsa → React Native
- Oyun / 3D → Unity veya özel değerlendirme

### Adım 3 — Belgeleri Üret

Her dosyayı sırayla üret. Template'ler için `references/templates.md` dosyasını kullan, ancak template'leri körü körüne doldurmak yerine uygulamaya özel içerik üret.

**Üretim sırası:** FEATURES.md → STACK.md → ARCHITECTURE.md → PLAN.md → DESIGN.md

Bu sıra önemlidir: özellikler belirlenince stack, stack belli olunca architecture, ikisi belli olunca plan, hepsi belli olunca design daha tutarlı çıkar.

### Adım 4 — Dosyaları Kaydet ve Sun

Tüm dosyaları `[app-slug]/` klasörüne kaydet: Claude Code'da mevcut çalışma dizininin altına, claude.ai'da `/mnt/user-data/outputs/[app-slug]/` altına. App slug, uygulama adından türetilmiş küçük harfli-tire-ayrılmış bir isimdir (örn. `todo-tracker`, `fitbuddy`).

Ortamda dosya sunma aracı varsa (örn. `present_files`) tüm dosyaları kullanıcıya onunla sun; yoksa oluşturulan dosyaların yollarını listele.

---

## Belge Yazma Prensipleri

### Vibe Coding'e Uygunluk
Dosyalar, kullanıcının doğrudan bir LLM'e prompt olarak girebileceği ya da geliştirme ortamına bırakabileceği netlikte olmalı. Belirsiz ifadelerden kaçın. "Bir auth sistemi ekle" yerine "Supabase Auth ile email/password + Google OAuth entegrasyonu" yaz.

### Gerekçe Her Zaman
Her büyük kararın yanında kısa bir "neden" açıklaması olmalı. Stack seçimi, mimari karar, özellik önceliği — hepsinin bir sebebi var. Kullanıcı bunu sonradan LLM'e sorarsa, LLM de bu bağlamı kullanır.

### Somut ve Actionable
- ❌ "Authentication eklenecek"
- ✅ "Supabase Auth — email/password + Google OAuth. Session yönetimi AsyncStorage'da. Ekran: LoginScreen, RegisterScreen, ForgotPasswordScreen."

### Türkçe / İngilizce
- Teknik terimler (state, component, endpoint vb.) İngilizce kalabilir
- Açıklamalar ve gerekçeler kullanıcının tercih ettiği dilde olmalı
- Kodla ilgili içerikler (klasör isimleri, komponent isimleri, API endpoint'leri) her zaman İngilizce

---

## Kapsam Dışı

Bu skill **kod yazmaz**. Dokümantasyon üretir. Kullanıcı "şimdi kodu yaz" derse, üretilen ARCHITECTURE.md ve STACK.md'yi referans göstererek yardım et ama bu skill'in görevi değil.

---

## Referans Dosyalar

- `references/stack-guide.md` — Platform ve framework seçim rehberi, kütüphane tavsiyeleri
- `references/templates.md` — 5 belge için detaylı template'ler

Her iki dosyayı da belge üretmeden önce oku.
