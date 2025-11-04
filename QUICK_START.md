# 🚀 RailDevHub - Quick Start Guide

GitHub Pages'e deploy edilmiş RailDevHub websitesi için hızlı başlangıç rehberi.

---

## 📦 5 Dakikada Başlayın

### 1. Repository'yi Klonlayın

```bash
git clone https://github.com/raildevhub/raildevhub.github.io.git
cd raildevhub.github.io
```

### 2. Bağımlılıkları Yükleyin

```bash
npm install
```

### 3. Geliştirme Sunucusunu Başlatın

```bash
npm run dev
```

🎉 Site hazır! Tarayıcınızda açın: **http://localhost:4321**

---

## 🌐 Canlı Site

**URL:** https://raildevhub.github.io

Her `main` branch'e push otomatik olarak deploy edilir (1-3 dakika).

---

## 🛠️ Temel Komutlar

```bash
npm run dev       # Geliştirme sunucusu (http://localhost:4321)
npm run build     # Production build oluştur
npm run preview   # Build'i lokal olarak test et
```

---

## 📝 İlk Değişikliğinizi Yapın

### Örnek: Home Page Title'ı Değiştirme

1. **Dosyayı açın:** `src/pages/index.astro`

2. **Title'ı değiştirin:**
```astro
<h1 class="text-3xl sm:text-4xl md:text-5xl...">
  Yeni Başlığınız Buraya
</h1>
```

3. **Kaydedin** - Değişiklik otomatik yansır (hot reload)

4. **Deploy edin:**
```bash
git add .
git commit -m "feat: update home page title"
git push origin main
```

5. **Bekleyin:** 1-3 dakika içinde https://raildevhub.github.io yayında!

---

## 📱 Mobil Özellikler

- **Bottom Navigation:** Mobil/tablet için alt navigasyon çubuğu
- **Auto-Hide Header:** Scroll'da otomatik gizlenip görünen header
- **Dark Mode:** Sistem tercihi + manuel toggle
- **Touch Optimized:** 44x44px minimum dokunma alanları

Test etmek için:
```bash
npm run dev
```
Chrome DevTools > Toggle Device Toolbar (Ctrl+Shift+M)

---

## 📂 Proje Yapısı

```
src/
├── components/       # Reusable components
│   ├── Header.astro
│   ├── Footer.astro
│   ├── BottomNav.astro
│   └── ThemeToggle.astro
├── layouts/         # Page layouts
│   └── BaseLayout.astro
├── pages/           # Website pages
│   ├── index.astro
│   ├── about.astro
│   ├── expertise.astro
│   ├── projects.astro
│   └── stories.astro
└── styles/          # Global styles
    └── global.css
```

---

## 🎨 Renk Paleti

```css
/* Tailwind config içinde tanımlı */
primary: {
  50: '#f0f9ff',
  600: '#1D4ED8',  /* Ana mavi */
}

railway-steel: '#2C3E50',    /* Koyu mavi-gri */
railway-signal: '#DC2626',   /* Kırmızı */
railway-safety: '#F59E0B',   /* Turuncu */
```

---

## 🔧 Yaygın Görevler

### Yeni Bir Sayfa Eklemek

1. `src/pages/new-page.astro` oluşturun
2. İçeriği ekleyin:
```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
---

<BaseLayout title="New Page">
  <Header />
  <main>
    <section class="py-20">
      <div class="section-container">
        <h1>New Page</h1>
      </div>
    </section>
  </main>
  <Footer />
</BaseLayout>
```
3. Navigation'a ekleyin: `src/components/Header.astro` ve `src/components/BottomNav.astro`

### Component Oluşturmak

1. `src/components/MyComponent.astro` oluşturun
2. Component'i yazın:
```astro
---
interface Props {
  title: string;
}

const { title } = Astro.props;
---

<div class="my-component">
  <h2>{title}</h2>
</div>
```
3. Kullanın:
```astro
---
import MyComponent from '../components/MyComponent.astro';
---

<MyComponent title="Hello!" />
```

### Stil Değişiklikleri

**Global Styles:** `src/styles/global.css`
```css
@layer components {
  .my-custom-class {
    @apply bg-primary-600 text-white p-4 rounded-lg;
  }
}
```

**Inline Tailwind:**
```html
<div class="bg-white dark:bg-gray-900 p-6 rounded-xl">
  Content
</div>
```

---

## 🐛 Sorun mu Yaşıyorsunuz?

### Build Hatası

```bash
rm -rf node_modules/ dist/
npm install
npm run build
```

### Port Zaten Kullanımda

```bash
# 4321 yerine başka port kullan
npm run dev -- --port 3000
```

### Dark Mode Çalışmıyor

- Browser localStorage'ı temizleyin
- Hard refresh: Ctrl+Shift+R (Windows) / Cmd+Shift+R (Mac)

### Deployment Başarısız

1. GitHub Actions'ı kontrol edin: https://github.com/raildevhub/raildevhub.github.io/actions
2. Log'ları inceleyin
3. Lokal build test edin: `npm run build`

---

## 📚 Dokümantasyon

### Başlangıç Seviye
- ✅ Bu dosya (`QUICK_START.md`)
- 📖 `README.md` - Proje genel bakış

### Orta/İleri Seviye
- 📱 `MOBILE_RESPONSIVE_GUIDE.md` - Mobil responsive detayları (10,000+ kelime)
- 🤖 `LLM_PROJECT_GENERATION_GUIDE.md` - AI ile proje geliştirme (12,000+ kelime)
- 🚀 `DEPLOYMENT.md` - Deployment detayları (5,000+ kelime)

---

## 🎯 Sonraki Adımlar

### Yeni Başlayanlar İçin
1. ✅ Projeyi çalıştırdınız
2. 📖 Kod yapısını inceleyin
3. 🎨 Küçük bir değişiklik yapın (örn: renk)
4. 🚀 Deploy edin ve sonucu görün

### İleri Seviye
1. 📱 Mobil responsive guide'ı okuyun
2. 🎨 Yeni bir component oluşturun
3. 📄 Yeni bir sayfa ekleyin
4. 🧪 Farklı cihazlarda test edin

---

## 💡 İpuçları

### 1. Hot Reload
Dev server çalışırken dosyaları değiştirdiğinizde sayfa otomatik yenilenir.

### 2. Tailwind IntelliSense
VS Code kullanıyorsanız "Tailwind CSS IntelliSense" extension'ını yükleyin.

### 3. Dark Mode Test
```javascript
// Browser console'da
localStorage.setItem('theme', 'dark');  // Dark mode
localStorage.setItem('theme', 'light'); // Light mode
location.reload();
```

### 4. Mobile Test
- Chrome DevTools: F12 > Toggle Device Toolbar (Ctrl+Shift+M)
- Gerçek cihazda test: `npm run dev -- --host`
  - Sonra `http://YOUR_IP:4321` adresine gidin

### 5. Performance Check
```bash
npm run build
npm run preview

# Sonra Lighthouse ile test edin (Chrome DevTools)
```

---

## 🤝 Yardım Alın

### Dokümantasyon
- Proje içi: `MOBILE_RESPONSIVE_GUIDE.md`, `DEPLOYMENT.md`
- Astro: https://docs.astro.build/
- Tailwind: https://tailwindcss.com/docs

### Örnekler
Mevcut sayfaları örnek alın:
- `src/pages/index.astro` - Hero section, stats, cards
- `src/pages/about.astro` - Timeline, team info
- `src/components/BottomNav.astro` - Mobile navigation

### Sık Sorulanlar

**Q: Hangi Node.js versiyonu?**
A: Node.js 20 veya üzeri

**Q: Deploy ne kadar sürer?**
A: Genellikle 1-3 dakika

**Q: Mobile test nasıl yapılır?**
A: Chrome DevTools device mode veya gerçek cihaz

**Q: Dark mode nasıl çalışır?**
A: Sistem tercihi otomatik algılanır, manuel toggle da var

---

## 🎉 Başarılar!

Artık RailDevHub projesinde çalışmaya hazırsınız. Küçük adımlarla başlayın, kod yapısını öğrenin, ve yavaş yavaş büyük değişiklikler yapın.

**Mutlu kodlamalar! 🚄✨**

---

**Güncellenme:** 2025-11-04
**Versiyon:** 1.0.0
