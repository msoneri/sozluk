# Sözlük — Regex ile Türkçe kelime arama

> Türkçe sözlüğünde **regex** ile kelime arayan, statik tek-sayfalık bir web sitesi. Kelimeye tıklayınca TDK'nın anlamını canlı olarak getirir.

**🌐 Canlı:** <https://sozluk-20s.pages.dev>

## Ne yapar?

- Arama kutusuna **regex** yazarsın (`^kit`, `lık$`, `k.t.p`, `^.{5}$` gibi).
- 65.084 Türkçe kelimeden anlık eşleşenleri listeler.
- Sonuç kelimeye tıklarsın → ayrı sayfada açıklaması, kökeni, kelime grubu, örnek cümleler ve birleşik kelimeler gelir.
- **Şapkalı harf umurunda değil:** "kabus" yazınca "kâbus"u da bulur.
- Tarayıcı geri tuşu + sayfanın "Aramaya dön" butonu aramanı korur.

## Veri kaynağı

- Kelime listesi: [`sozluk.gov.tr/autocomplete.json`](https://sozluk.gov.tr/autocomplete.json) — boşluklu maddeler filtrelendi, kalan 65.084 tek kelime `public/autocomplete.json`'da gömülü.
- Anlamlar: `https://sozluk.gov.tr/gts?ara=<kelime>` — kullanıcı sayfaya gelince **client-side** çağrılır (backend yok).

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
  kelime.astro        # /kelime/?w=<kelime> → tek kelime detay sayfası
```

## Teknoloji

- [Astro](https://astro.build) — statik site
- Sıfır framework, sıfır build-time DB. Tüm arama tarayıcıda çalışır.
- Tasarım: **Neo-Brutalism** (krem kâğıt zemin, sert siyah kenarlar, elektrik sarısı aksan).

## Lisans

MIT.
