# Sözlük — Regex ile Türkçe kelime arama

Türkçe sözlüğünde **regex** ile kelime arayan statik tek sayfalık bir web sitesi. Kelimeye tıklayınca TDK'nın anlamını canlı olarak getirir.

**Canlı:** <https://sozluk-20s.pages.dev>

## Özellikler

- Arama kutusuna regex yaz, 65.084 Türkçe kelimeden eşleşenleri anında listele (`^kit`, `lık$`, `k.t.p`, `^.{5}$` gibi).
- Kelimeye tıklayınca ayrı sayfada anlamı, kökeni, kelime grubu, örnek cümle ve birleşik kelimeler gelir.
- Şapkasız yazınca şapkalı kelimeyi de bulur ("kabus" → "kâbus").
- Arama sorgusu URL'de tutulur, geri tuşu ve "Aramaya dön" linki state'i korur.
- Responsive: mobil, tablet, masaüstü.

## Yol Haritası

- [ ] **Tarama Sözlüğü** entegrasyonu (eski Türkçe / tarihi kelimeler) — `sozluk.gov.tr/tarama?ara=`
- [ ] **Derleme Sözlüğü** (halk ağzı / yöresel) — `sozluk.gov.tr/derleme?ara=`
- [ ] Atasözleri ve deyimler sözlüğü
- [ ] Etimoloji sayfasının zengin gösterimi
- [ ] TDK'nın ses dosyaları ile telaffuz

## Veri kaynağı

- Kelime listesi: [`sozluk.gov.tr/autocomplete.json`](https://sozluk.gov.tr/autocomplete.json) — boşluklu maddeler filtrelendi, kalan 65.084 kelime `public/autocomplete.json`'da gömülü.
- Anlamlar: `https://sozluk.gov.tr/gts?ara=<kelime>` — backend olmadığı için kullanıcı sayfaya gelince doğrudan tarayıcıdan çağrılır.

## Geliştirme

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # dist/ klasörüne statik çıktı
npm run preview  # build'i lokal olarak servis et
```

## Proje yapısı

```
public/
  autocomplete.json   # 65.084 kelime
src/pages/
  index.astro         # arama sayfası + regex tutorial sidebar
  kelime.astro        # /kelime/?w=<kelime> tek kelime detay sayfası
```

## Teknoloji

- [Astro](https://astro.build) — statik site, framework yok, build-time DB yok. Arama tamamen tarayıcıda.
- Tasarım: Neo-Brutalism (krem zemin, kalın siyah kenarlar, elektrik sarısı vurgular).

## Lisans

MIT.
