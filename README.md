# Kemer Yat Turu — Web Sitesi

Kemer Marina çıkışlı günlük lüks yat turu için tek sayfalık (one-page) tanıtım
ve rezervasyon yönlendirme sitesi. Saf statik HTML/CSS/JS — sunucu, veritabanı
veya derleme adımı gerektirmez.

**Canlı site:** https://www.kemeryatturu.com/
**Diller:** Türkçe (varsayılan), İngilizce, Rusça — sayfa içi dil değiştirme (JS)

---

## Dosya Yapısı

```
index.html              Tüm sayfa: HTML + özel CSS + JS + 3 dil sözlüğü + JSON-LD şeması
assets/tailwind.min.css Derlenmiş Tailwind CSS (cdn.tailwindcss.com yerine yerel — 23 KB)
images/*.webp           Sayfada kullanılan görseller (toplam 1.13 MB)
images/hero-yacht.jpg   Hero görselinin eski tarayıcı yedeği + og:image (SİLMEYİN)
images/logo.svg         Site logosu ve favicon
robots.txt              Tarama kuralları + AI botlarına (GPTBot, ClaudeBot vb.) izin
sitemap.xml             Site haritası (görsel girdileriyle)
llms.txt                AI arama motorları için işletme özeti (GEO)
BASLAT.bat              Windows'ta çift tıkla → http://localhost:8000 yerel önizleme
```

`images/*.jpg` dosyalarının WebP dışındaki ham kopyaları `.gitignore` ile hariç
tutulur (yalnızca `hero-yacht.jpg` zorunlu olduğu için repoda kalır).

---

## Yerel Önizleme

**Kolay yol (Windows):** `BASLAT.bat` dosyasına çift tıklayın → tarayıcı
`http://localhost:8000` adresinde açılır.

**Diğer:** klasörü herhangi bir statik sunucuyla yayınlayın:

```bash
python -m http.server 8000     # Python
npx serve .                    # Node.js
```

> Not: `index.html`'i doğrudan çift tıklayarak (`file://`) açmak yerine sunucu
> üzerinden açın; `robots.txt`/`sitemap.xml` ve göreli yollar o zaman doğru çalışır.

---

## Yayına Alma

1. `index.html`, `robots.txt`, `sitemap.xml`, `llms.txt`, `assets/` ve `images/`
   klasörlerini barındırma (hosting) kök dizinine yükleyin.
2. Netlify kullanıyorsanız hazır paket: `kemer-yat-turu-web.zip` dosyasını
   Netlify Drop alanına sürükleyin (derleme ayarı gerekmez, publish dizini: kök).
3. Yayın sonrası kontrol listesi:
   - `https://www.kemeryatturu.com/robots.txt` ve `/sitemap.xml` tarayıcıda açılıyor mu?
   - Google Search Console'a `sitemap.xml` gönderildi mi?
   - `index.html` içindeki canonical / og / sitemap adresleri alan adıyla birebir mi?

---

## Yapılan SEO / GEO Çalışmaları

- Görseller WebP'ye çevrildi: **5.12 MB → 1.13 MB (%78 küçülme)**; hero,
  `image-set()` ile WebP sunar, desteklemeyen tarayıcıda JPG'ye düşer.
- Tailwind CDN betiği kaldırıldı → yerel `assets/tailwind.min.css` (JIT derleme yok).
- Başlık 49 karakter, açıklama 147 karakter (TR/EN/RU üç dil için ayrı).
- Tek `<h1>`, başlık seviyesi atlaması yok, tüm görsellerde `alt`, tüm çapalar çalışıyor.
- `robots.txt` (yapay zekâ tarayıcılarına açık), `sitemap.xml`, `llms.txt` eklendi.
- JSON-LD: `LocalBusiness` + `TouristAttraction` + `FAQPage` (görsel URL'leri ve
  fiyat bilgisi sayfayla tutarlı).
- Mobil dokunma hedefleri en az 44 px; 390 px'te yatay taşma yok.

---

## Önemli: Tailwind Sınıfı Eklerken

`assets/tailwind.min.css` **derlenmiş** bir dosyadır. HTML'de **yeni** bir
Tailwind sınıfı kullanırsanız (örnek: `bg-ocean-700`, `mt-13` gibi daha önce
kullanılmamış bir sınıf) o sınıf CSS'te bulunmaz ve etkisiz kalır. Böyle bir
değişiklik yapmadan önce CSS dosyasının yeniden üretilmesi gerekir.
Mevcut sınıfların değerlerini değiştirmek sorun değildir.

---

## İletişim

- Telefon / WhatsApp: +90 532 113 92 44 (`+905321139244`)
- E-posta: info@kemeryatturu.com
- Adres: Kemer Marina, Liman Cad., 07980 Kemer / Antalya
