[English](README.md) · **Türkçe** · [Deutsch](README.de.md) · [Español](README.es.md)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.png">
    <img src="assets/logo-light.png" alt="modsweep" width="460">
  </picture>
</p>

<p align="center"><b>Projeleri temizle. Üretmeye devam et.</b><br>
JavaScript projelerindeki <code>node_modules</code> klasörlerini bul, analiz et ve güvenle temizle — yerel bir macOS uygulaması.</p>

<p align="center">
  <a href="https://github.com/caglarergul/modsweep-macos/releases/latest"><b>Son sürümü indir</b></a>
  · macOS 14 Sonoma ve sonrası · Apple Silicon ve Intel
</p>

---

## Kurulum

**İndir:** [son sürümden](https://github.com/caglarergul/modsweep-macos/releases/latest) `modsweep-<sürüm>.dmg`
dosyasını indir, aç ve **modsweep**'i **Uygulamalar** klasörüne sürükle. Her sürüm Developer ID ile imzalı ve Apple
tarafından notarize edilmiştir; uyarısız açılır.

**Homebrew:**

```bash
brew install --cask caglarergul/tap/modsweep   # kur
brew upgrade --cask modsweep                   # güncelle
brew uninstall --cask --zap modsweep           # uygulamayı ve verilerini kaldır
```

**Gereksinimler:** macOS 14 Sonoma veya sonrası. Projeleri kurmak (Kur ve doğrula) için
[pnpm](https://pnpm.io/installation) gerekir; npm, yarn ve bun projeleri de desteklenir.

## Ne yapar

| | |
|---|---|
| **Tara** | Bir klasördeki JavaScript projelerini bulur; her `node_modules` klasörünün ne kadar yer kapladığını, paket yöneticisini, son etkinliği ve git durumunu, ayrıca npm/pnpm/yarn/bun önbelleklerini ve boş diski gösterir. Toplam boyut menü çubuğunda durur. |
| **Analiz et** | Kurulum ve çalıştırma sorunlarını başına gelmeden bulur — güncel olmayan veya iki ayrı kilit dosyası, Node sürüm uyuşmazlığı, `node-sass`, yeni Node'da eski webpack, webpack ayarlı Next 16, Prisma, eksik `.env`, Stencil mağaza sorunları … — ve her biri için bir çözüm önerir. |
| **Temizle** | Seçtiğin `node_modules` klasörlerini **Çöp Kutusu**'na taşır; istersen geri alabilirsin. İçinde node süreci çalışan ya da git'in takip ettiği dosyaları olan klasörlere dokunmaz. |
| **Paylaş** | npm ve yarn her projeye her paketin tam bir kopyasını koyar. modsweep hangi sürümlerin projelerinde tekrarlandığını gösterir ve seçtiklerini bu Mac'teki **tek bir ortak pnpm deposuna** taşır; her sürüm bir kez tutulur. Yalnızca iki yerel dosya eklenir (`.git/info/exclude`'a yazılır): git ve ekibin için hiçbir şey değişmez. Her proje önce yedeklenir, herhangi bir hatada geri alınır; eski `node_modules` Çöp Kutusu'na gider ve istediğin zaman npm/yarn'a geri dönebilirsin. pnpm 10 veya üstü gerekir. |
| **Kur ve doğrula** | Seçili projeleri kurar; bağımlılıkları, komutları, typecheck'i, build'i ve istersen bir dev server'ı kontrol eder. Canlı log, Durdur butonu var; sonunda her şey geri konur. |

**English, Türkçe, Deutsch ve Español** dillerinde kullanılabilir (Ayarlar → Dil).

## Güvenlik

modsweep, canlı sistemlere bağlı gerçek projeler için tasarlandı.

- **Hiçbir şey push'lanmaz ya da deploy edilmez.** deploy, publish, push, migrate, vercel, shopify … içeren script'ler
  test sırasında asla çalışmaz.
- **Veritabanlarına ulaşılamaz.** Test sırasında `.env` dosyalarındaki veritabanı, Redis ve Mongo adresleri boşa
  yönlendirilir.
- **Dosyaların geri yüklenir.** `package.json`, kilit dosyaları ve git durumu testten önce yedeklenir ve sonra geri
  konur — Durdur'a bastığında da.
- **Arkada süreç kalmaz.** Test sunucuları süreç ağacı ve klasöre göre durdurulur.
- **Çökmeye dayanıklı.** Test ortasında Mac ya da uygulama kapanırsa modsweep bir sonraki açılışta, başka hiçbir şey
  yapmadan önce projeyi geri yükler.
- **Temizlik Çöp Kutusu'na gider.** Uygulama hiçbir şeyi kalıcı olarak silmez.

## İlk açılış

modsweep ev klasörünü önerir ama kendiliğinden hiçbir şeyi taramaz. Projelerinin bulunduğu klasörü seç (ör.
`~/Developer` ya da `~/www`) ve Tara'ya bas. Klasörü istediğin zaman kenar çubuğundan ya da Ayarlar'dan
değiştirebilirsin.

Node, pnpm gibi araçların nvm, asdf veya mise ile kuruluysa klasörlerini **Ayarlar → Araçlar**'dan ekle.

## Gizlilik

modsweep'te hesap, analitik ya da izleme yoktur. Sadece sen istediğinde internete çıkar: Kur ve doğrula sırasında
paket kurarken ve analizdeki isteğe bağlı Stencil mağaza kontrolünde (Ayarlar'dan kapatılabilir).

## Kaldırma

`brew uninstall --cask --zap modsweep` ya da modsweep'i Uygulamalar'dan Çöp Kutusu'na sürükle ve
`~/Library/Application Support/modsweep` klasörünü sil.

## Sorumluluk reddi

modsweep ücretsizdir ve "olduğu gibi", garantisiz sunulur. Bilgisayarındaki dosyaları değiştirir (Çöp Kutusu,
paket kurulumu, build); kullanmanın riski sana aittir. Yedek al ve sürüm kontrolü kullan. Tam metin:
[sorumluluk reddi](DISCLAIMER.tr.md).

---

Bu depo yalnızca sürüm dosyalarını barındırır; kaynak kod herkese açık değildir.

Telif hakkı © 2026 Caglar Ergul. Tüm hakları saklıdır.
