# RailDevHub GitHub Pages Deployment Guide

## 🚀 Genel Bakış

Bu proje GitHub Pages üzerinde `https://raildevhub.github.io` adresinde yayınlanmaktadır. Otomatik deployment için GitHub Actions kullanılmaktadır.

---

## 📋 İçindekiler

1. [Ön Koşullar](#ön-koşullar)
2. [İlk Kurulum](#ilk-kurulum)
3. [Otomatik Deployment](#otomatik-deployment)
4. [Manuel Deployment](#manuel-deployment)
5. [Sorun Giderme](#sorun-giderme)
6. [Deployment Kontrol Listesi](#deployment-kontrol-listesi)

---

## Ön Koşullar

### Gerekli Yazılımlar
- Node.js 20.x veya üzeri
- npm 10.x veya üzeri
- Git

### GitHub Repository Ayarları
Repository: `https://github.com/raildevhub/raildevhub.github.io.git`

---

## İlk Kurulum

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

Tarayıcınızda `http://localhost:4321` adresine gidin.

---

## Otomatik Deployment

### GitHub Actions Workflow

Proje, her `main` branch'e push yapıldığında otomatik olarak deploy edilir.

**Workflow Dosyası**: `.github/workflows/deploy.yml`

### Deployment Süreci

1. **Kod Push Edilir**
   ```bash
   git add .
   git commit -m "feat: new feature added"
   git push origin main
   ```

2. **GitHub Actions Tetiklenir**
   - Bağımlılıklar yüklenir
   - Proje build edilir (`npm run build`)
   - Dist klasörü GitHub Pages'e deploy edilir

3. **Site Yayına Girer**
   - URL: `https://raildevhub.github.io`
   - Genellikle 1-3 dakika içinde aktif olur

### Deployment Durumunu Kontrol Etme

1. GitHub repository sayfasına gidin
2. **Actions** sekmesine tıklayın
3. Son workflow run'ını görüntüleyin
4. Yeşil ✓ = Başarılı, Kırmızı ✗ = Hata

**Actions URL**: `https://github.com/raildevhub/raildevhub.github.io/actions`

---

## GitHub Pages Ayarları

### Repository Settings

1. GitHub'da repository'ye gidin
2. **Settings** > **Pages** sekmesine tıklayın
3. **Source**: `GitHub Actions` seçili olmalı
4. **Custom domain** (opsiyonel): Özel domain ekleyebilirsiniz

### Ayarlar Kontrolü

```yaml
Source: GitHub Actions
Branch: gh-pages (otomatik oluşturulur)
URL: https://raildevhub.github.io
```

---

## Manuel Deployment

Gerekirse manuel deployment de yapabilirsiniz:

### 1. Lokal Build

```bash
# Bağımlılıkları yükleyin
npm install

# Build yapın
npm run build

# Build'i önizleyin
npm run preview
```

### 2. Build Çıktısını Kontrol Edin

```bash
ls -la dist/
```

Dist klasörü şunları içermelidir:
- `index.html`
- `about/index.html`
- `expertise/index.html`
- `projects/index.html`
- `stories/index.html`
- `_astro/` (CSS ve JS dosyaları)
- Diğer asset'ler

### 3. Manuel Push (GitHub Actions Olmadan)

```bash
# Build yapın
npm run build

# Değişiklikleri commit edin
git add dist/
git commit -m "build: manual build for deployment"
git push origin main
```

---

## Sorun Giderme

### Problem 1: Deployment Başarısız

**Hata**: GitHub Actions build hatası

**Çözüm**:
1. Actions log'larını kontrol edin
2. Lokal olarak build deneyin:
   ```bash
   npm run build
   ```
3. Hataları düzeltin ve tekrar push edin

### Problem 2: Sayfa 404 Hatası Veriyor

**Hata**: `https://raildevhub.github.io` açılmıyor

**Çözüm**:
1. GitHub Pages ayarlarını kontrol edin
2. `astro.config.mjs` dosyasında `site` değerini kontrol edin:
   ```javascript
   export default defineConfig({
     site: 'https://raildevhub.github.io',
   });
   ```
3. Repository adının doğru olduğundan emin olun: `raildevhub.github.io`

### Problem 3: CSS/JS Dosyaları Yüklenmiyor

**Hata**: Stil ve JavaScript çalışmıyor

**Çözüm**:
1. Browser console'u kontrol edin (F12)
2. `astro.config.mjs` base path'ini kontrol edin
3. Build'i tekrar yapın:
   ```bash
   rm -rf dist/
   npm run build
   git add .
   git commit -m "fix: rebuild assets"
   git push origin main
   ```

### Problem 4: Dark Mode Çalışmıyor

**Hata**: Theme toggle çalışmıyor

**Çözüm**:
1. Browser localStorage'ı temizleyin
2. Sayfayı hard refresh yapın (Ctrl+Shift+R / Cmd+Shift+R)
3. `src/components/ThemeToggle.astro` script'ini kontrol edin

### Problem 5: Mobile Görünüm Bozuk

**Hata**: Mobil cihazlarda düzen bozuk

**Çözüm**:
1. Responsive breakpoints'leri kontrol edin
2. Chrome DevTools'da mobile preview yapın
3. `MOBILE_RESPONSIVE_GUIDE.md` dokümantasyonunu inceleyin

---

## Deployment Kontrol Listesi

Deployment yapmadan önce bu listeyi kontrol edin:

### Pre-Deployment Checklist

- [ ] **Build Testi**
  ```bash
  npm run build
  npm run preview
  ```

- [ ] **Responsive Test**
  - [ ] Mobile (375px)
  - [ ] Tablet (768px)
  - [ ] Desktop (1280px+)

- [ ] **Browser Test**
  - [ ] Chrome
  - [ ] Firefox
  - [ ] Safari
  - [ ] Edge

- [ ] **Functionality Test**
  - [ ] Tüm sayfalar açılıyor
  - [ ] Navigation çalışıyor
  - [ ] Bottom nav (mobile) çalışıyor
  - [ ] Theme toggle çalışıyor
  - [ ] Linkler doğru yönlendiriyor

- [ ] **Performance Check**
  ```bash
  npm run build
  # dist/ klasörü boyutunu kontrol edin
  du -sh dist/
  ```

- [ ] **SEO & Meta Tags**
  - [ ] Tüm sayfalarda title var
  - [ ] Meta descriptions tanımlı
  - [ ] Open Graph tags var (opsiyonel)

### Post-Deployment Checklist

- [ ] Site açılıyor: `https://raildevhub.github.io`
- [ ] GitHub Actions başarılı: ✓ (yeşil)
- [ ] Tüm sayfalar çalışıyor
- [ ] Mobile görünüm düzgün
- [ ] Dark mode çalışıyor
- [ ] Performance kabul edilebilir (Lighthouse > 90)

---

## Deployment Komutları Özeti

```bash
# Geliştirme sunucusu başlat
npm run dev

# Production build yap
npm run build

# Build'i lokal olarak önizle
npm run preview

# Değişiklikleri commit et ve deploy et
git add .
git commit -m "feat: new changes"
git push origin main

# GitHub Actions durumunu kontrol et
# https://github.com/raildevhub/raildevhub.github.io/actions
```

---

## Konfigürasyon Dosyaları

### astro.config.mjs

```javascript
import { defineConfig } from 'astro/config';
import tailwind from '@astrojs/tailwind';

export default defineConfig({
  site: 'https://raildevhub.github.io',
  integrations: [tailwind()],
  output: 'static',
});
```

**Önemli**: `site` değeri repository URL'iniz ile eşleşmeli!

### .github/workflows/deploy.yml

```yaml
name: Deploy Astro site to GitHub Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write
```

Workflow dosyası şu işlemleri yapar:
1. Kodu checkout eder
2. Node.js kurar
3. Bağımlılıkları yükler (`npm ci`)
4. Build yapar (`npm run build`)
5. GitHub Pages'e deploy eder

---

## Performance Optimizasyonu

### Build Boyutunu Azaltma

```bash
# Build boyutunu kontrol edin
npm run build
du -sh dist/

# Dosya detaylarını görün
du -h dist/* | sort -h
```

### Optimizasyon İpuçları

1. **Image Optimization**
   - Görselleri compress edin
   - WebP formatı kullanın
   - Lazy loading ekleyin

2. **CSS Optimization**
   - Tailwind purge çalışıyor (otomatik)
   - Kullanılmayan CSS'ler temizleniyor

3. **JavaScript Optimization**
   - Minimal JavaScript kullanımı
   - Astro otomatik olarak optimize eder

---

## Monitoring & Analytics

### GitHub Pages Status

Site durumunu kontrol edin:
```
https://www.githubstatus.com/
```

### Google Analytics (Opsiyonel)

Google Analytics eklemek için:

1. `src/layouts/BaseLayout.astro` dosyasına ekleyin:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script is:inline>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Lighthouse Audit

Performance testi yapın:
```bash
# Chrome DevTools > Lighthouse
# veya
npx lighthouse https://raildevhub.github.io --view
```

**Hedef Skorlar**:
- Performance: > 90
- Accessibility: > 90
- Best Practices: > 90
- SEO: > 90

---

## Güvenlik

### Secrets Yönetimi

GitHub Actions için secrets:
1. Repository Settings > Secrets and variables > Actions
2. Gerekirse API keys ekleyin
3. Workflow dosyasında `${{ secrets.SECRET_NAME }}` ile kullanın

### HTTPS

GitHub Pages otomatik HTTPS sağlar:
- ✅ `https://raildevhub.github.io`
- ❌ `http://raildevhub.github.io` (redirect edilir)

---

## Özel Domain (Opsiyonel)

Kendi domain'inizi kullanmak için:

### 1. DNS Ayarları

Domain sağlayıcınızda A record ekleyin:
```
A    @    185.199.108.153
A    @    185.199.109.153
A    @    185.199.110.153
A    @    185.199.111.153
```

veya CNAME record:
```
CNAME    www    raildevhub.github.io
```

### 2. GitHub Settings

1. Repository Settings > Pages
2. Custom domain: `www.raildevhub.com` (örnek)
3. Enforce HTTPS: ✓

### 3. Astro Config

```javascript
export default defineConfig({
  site: 'https://www.raildevhub.com',
});
```

---

## Rollback (Geri Alma)

Hatalı deployment'ı geri almak için:

### Method 1: Git Revert

```bash
# Son commit'i geri al
git revert HEAD

# Push et
git push origin main
```

### Method 2: Önceki Commit'e Dön

```bash
# Commit geçmişini göster
git log --oneline

# İstediğiniz commit'e dön
git reset --hard COMMIT_HASH

# Force push (dikkatli kullanın!)
git push origin main --force
```

### Method 3: GitHub Actions Re-run

1. Actions sekmesine gidin
2. Başarılı olan önceki workflow'u seçin
3. "Re-run jobs" butonuna tıklayın

---

## CI/CD Pipeline

### Current Pipeline

```
Code Push → GitHub Actions → Build → Test → Deploy → Live
```

### Pipeline Steps

1. **Trigger**: Push to main
2. **Build**: `npm ci && npm run build`
3. **Upload**: Artifact upload to GitHub
4. **Deploy**: Deploy to GitHub Pages
5. **Verify**: Check site is live

### Adding Tests (Future)

```yaml
# .github/workflows/deploy.yml içine eklenebilir
- name: Run tests
  run: npm test

- name: Run linter
  run: npm run lint
```

---

## Backup & Version Control

### Git Tags

Önemli release'leri tag'leyin:

```bash
# Tag oluştur
git tag -a v1.0.0 -m "Release version 1.0.0"

# Push tag
git push origin v1.0.0

# Tüm tag'leri göster
git tag -l
```

### Backup

```bash
# Tüm repository'yi backup alın
git clone --mirror https://github.com/raildevhub/raildevhub.github.io.git
```

---

## Destek & Kaynaklar

### Dokümantasyon
- [Astro Docs](https://docs.astro.build/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)

### Proje Dokümantasyonu
- `MOBILE_RESPONSIVE_GUIDE.md` - Mobile responsiveness
- `LLM_PROJECT_GENERATION_GUIDE.md` - LLM kullanım rehberi
- `README.md` - Proje hakkında

### Yardım

Sorun yaşarsanız:
1. Bu dokümantasyonu kontrol edin
2. GitHub Actions log'larını inceleyin
3. Lokal olarak test edin
4. Senior developer'lara danışın

---

## Sık Kullanılan Komutlar

```bash
# Geliştirme
npm run dev                 # Dev server başlat
npm run build              # Production build
npm run preview            # Build'i önizle

# Git
git status                 # Değişiklikleri göster
git add .                  # Tüm değişiklikleri ekle
git commit -m "message"    # Commit oluştur
git push origin main       # Deploy tetikle

# Kontrol
git log --oneline         # Commit geçmişi
git diff                  # Değişiklikleri göster

# Troubleshooting
rm -rf node_modules/      # Node modules'ları sil
npm install               # Tekrar yükle
rm -rf dist/              # Build çıktısını sil
npm run build             # Tekrar build et
```

---

## Changelog Format

Değişikliklerinizi kaydedin:

```markdown
## [1.0.0] - 2025-11-04
### Added
- Mobile bottom navigation
- Auto-hide header on scroll
- Dark mode improvements

### Fixed
- Responsive layout issues
- Touch target sizes

### Changed
- Updated button styles
- Improved mobile performance
```

---

**Son Güncelleme**: 2025-11-04
**Versiyon**: 1.0.0
**Yönetici**: RailDevHub DevOps Team
