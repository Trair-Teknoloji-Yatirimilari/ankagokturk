# Anka Göktürk Breath & Art — Web Sitesi

[ankagokturk.com](https://www.ankagokturk.com) sitesinin Wix'ten bağımsız, temiz HTML/CSS ile yeniden inşa edilmiş hali. Framework yok, build adımı yok — dosyaları herhangi bir sunucuya koyman yeterli.

## Yapı

- 14 statik HTML sayfası (anasayfa, hakkımızda, eğitmenler, transformal nefes sayfaları, kurumsal, kişisel gelişim, sanat, çocuk-ebeveyn, mekan, etkinlikler, iletişim)
- `css/style.css` — tüm sitenin ortak stili
- Rezervasyon/etkinlik kaydı yerine WhatsApp, telefon ve Instagram bağlantıları kullanılıyor

## Yerelde görüntüleme

Herhangi bir `.html` dosyasını tarayıcıda aç, ya da:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## GitHub'a yükleme

```bash
cd anka-gokturk-site
git init
git add .
git commit -m "İlk sürüm: Wix'ten temiz HTML'e geçiş"
git branch -M main
git remote add origin https://github.com/KULLANICI_ADIN/anka-gokturk-site.git
git push -u origin main
```

## GitHub Pages ile ücretsiz yayınlama

1. GitHub'da repo sayfası → **Settings → Pages**
2. Source: **Deploy from a branch**, Branch: **main**, klasör: **/ (root)** → Save
3. Birkaç dakika içinde site `https://KULLANICI_ADIN.github.io/anka-gokturk-site/` adresinde yayında olur
4. Kendi alan adını (ankagokturk.com) bağlamak için: Settings → Pages → Custom domain alanına alan adını yaz ve DNS sağlayıcında `www` için `KULLANICI_ADIN.github.io` hedefli bir CNAME kaydı oluştur

## Önemli not: Görseller

Görseller şu an Wix CDN'inden (`static.wixstatic.com`) yükleniyor. **Wix aboneliği kapatılırsa bu görseller bir süre sonra erişilemez olabilir.** Wix'ten tamamen ayrılmadan önce görselleri indirip repoya ekle:

```bash
mkdir -p assets/img
# HTML dosyalarındaki tüm wixstatic URL'lerini indir:
grep -ohr 'https://static\.wixstatic\.com/[^"]*' *.html | sort -u | while read url; do
  curl -sL "$url" -o "assets/img/$(echo "$url" | md5sum | cut -c1-12).jpg"
done
```

Sonra HTML'lerdeki URL'leri `assets/img/...` yollarıyla değiştir (bunu istediğinde birlikte de yapabiliriz).

## Wix'te olup burada olmayanlar

- Etkinlik kaydı ve online ödeme (Wix Events/Bookings) → WhatsApp/Instagram yönlendirmesiyle çözüldü
- Bülten abonelik formu → istenirse ücretsiz bir form servisi (ör. Formspree, Google Form) eklenebilir
