# Sözlük

Aklına bir kelime takılıyor ama tam çıkaramıyorsun, ya da "-lık ile biten kaç kelime varmış?" diye merak ediyorsun. Bu site tam bunun için: TDK sözlüğündeki ~65 bin Türkçe kelimeyi **regex** ile arayabiliyorsun.

**🌐 Canlıda:** <https://sozluk-20s.pages.dev>

## Neler yapabilirsin

Arama kutusuna istediğin kalıbı yazıyorsun — `^kit` (kit ile başlayanlar), `lık$` (lık ile bitenler), `k.t.p` (kitap, kâtip, kutup…), `^.{5}$` (tam beş harfli kelimeler) — eşleşenler anında listeleniyor. Sağdaki örnek tablodan birkaç dakika içinde regex'i kavrayabilirsin.

Bir kelimeye tıkladığında ayrı bir sayfada anlamı, kökeni (Arapça, Farsça…), kelime grubu (isim/fiil/sıfat), TDK'daki örnek cümle ve birleşik kelimeleri açılıyor — hepsi sözlük.gov.tr'den canlı geliyor.

Birkaç küçük detay:
- "kabus" yazınca "kâbus"u da buluyor; şapkalı harf takıntısı yok.
- Geri tuşuna basınca aramanı kaybetmiyorsun. URL'de duruyor, paylaşabilirsin.
- Telefon, tablet, masaüstü hepsinde rahat görünüyor.

## Yapılacaklar

- [ ] **Tarama Sözlüğü** entegrasyonu — eski Türkçe / tarihi kelimeler için `sozluk.gov.tr/tarama?ara=` endpoint'i.
- [ ] **Derleme Sözlüğü** — halk ağzı / yöresel kelimeler için `sozluk.gov.tr/derleme?ara=`.
- [ ] **Atasözleri ve deyimler** sözlüğü.
- [ ] Köken bilgisi (etimoloji) sayfasının daha zengin gösterimi.
- [ ] Kelime sayfasında "ilgili sesli okuma" — TDK'nın `ses/<kod>.wav` dosyaları.

## Veriler nereden geliyor

- Kelime listesi: [`sozluk.gov.tr/autocomplete.json`](https://sozluk.gov.tr/autocomplete.json). Boşluklu/öbekli maddeler temizlenip kalan 65.084 tek-kelime `public/autocomplete.json`'da gömülü duruyor.
- Anlamlar: `sozluk.gov.tr/gts?ara=<kelime>` — backend olmadığı için kullanıcı kelimeye tıkladığında doğrudan tarayıcısı çağırıyor.

## Çalıştırmak istersen

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # dist/ klasörüne statik çıktı
```

## Proje yapısı

```
public/autocomplete.json   — 65.084 kelime
src/pages/index.astro      — arama sayfası, regex tutorial sidebar
src/pages/kelime.astro     — /kelime/?w=… tek kelime detay sayfası
```

[Astro](https://astro.build) ile yazıldı; framework yok, build-time DB yok, her şey tarayıcıda. Tasarım **Neo-Brutalism** — krem zemin, kalın siyah kenarlar, elektrik sarısı vurgular.

## Lisans

MIT.
