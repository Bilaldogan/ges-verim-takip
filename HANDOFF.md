# GES Verim Takip — Handoff

## Durum: queued
Son guncelleme: 2026-04-10

## Nedir
GES (Güneş Enerji Santrali) sahipleri için panel verim takip + AI temizlik optimizasyonu SaaS'ı. İnverter API'lerinden veri çekip kirlilik kaynaklı verim düşüşünü tespit eder, optimal temizlik zamanını önerir. Uzun vadede tam verim yönetimi platformu.

## Strateji
- **Faz 1 (şimdi):** Demand validation — landing page + robot firma outreach + GES sahibi görüşme
- **Faz 2:** MVP build — Huawei FusionSolar API + temizlik optimizasyonu
- **Faz 3:** Arıza tespiti — string arızası, inverter verimsizliği, gölgeleme analizi
- **Faz 4:** Performans optimizasyonu — clipping, degradasyon, tilt önerisi
- **Faz 5:** RaaS katmanı — hazır robot al, temizlik hizmeti sun
- **Faz 6:** Drone entegrasyonu — termal/RGB ile hot spot, çatlak, ot tespiti

## Yapilan
- Pazar araştırması tamamlandı (docs/market-research.md)
- 40,000 GES, yılda 5,000 yeni, yerli rakip az
- İnverter API'leri araştırıldı (Huawei, SMA, Fronius, GoodWe, Sungrow)
- Gelir projeksiyonu: 150 müşteri × 700 TL/ay = ~$2,700 MRR (12 ay)
- GitHub repo + submodule oluşturuldu
- Verim artırma yol haritası belirlendi (temizlik + arıza + optimizasyon + drone)
- Robot firma ortaklık modelleri tanımlandı (veri ortaklığı, white-label, komisyon)

## Robot Firma Ortaklik Stratejisi
Robot firmalarıyla (SelSun, GES RoboSpace, Robsys, Solenser, Doka) 3 model:

1. **Veri Ortaklığı (ilk adım):** Robot firması temizler, biz öncesi/sonrası verim raporu çıkarırız. Firmanın müşteri listesine erişim sağlar.
2. **White-Label Dashboard (B2B):** Robot firmalarına kendi markaları altında dashboard sat. Firma başı 5-15K TL/ay.
3. **Lead Generation (Faz 3+):** SaaS "şimdi temizlik zamanı" → robot firmasına yönlendir → %10-15 komisyon.

İlk outreach: robot firmalarına "müşterilerinize ücretsiz 1 aylık verim raporu çıkaralım" teklifi.

## Verim Artırma Feature Yol Haritası

### Faz 1 — Temizlik Optimizasyonu (MVP)
- Kirlilik kaybı tespiti (inverter verisinden üretim düşüşü analizi)
- Optimal temizlik zamanı önerisi (AI + meteoroloji)
- Temizlik öncesi/sonrası verim karşılaştırma raporu

### Faz 2 — Arıza Tespiti
- String arızası: string'ler arası üretim farkı → %10-100 kayıp
- Inverter verimsizliği: AC/DC oranı + MPPT performans takibi → %2-5 kayıp
- Gölgeleme analizi: saatlik üretim profili vs beklenen (mevsimsel model) → %5-25 kayıp
- Kablo kaybı: DC voltaj sapması → %1-3 kayıp
- Mismatch: string performans farkı → %2-5 kayıp

### Faz 3 — Performans Optimizasyonu
- Clipping analizi: inverter küçük → "upgrade edin, yılda ₺X kazanın" → %3-10 kayıp
- Degradasyon trendi: yıllık üretim düşüşü → garanti kapsamında değişim uyarısı → %0.5-0.8/yıl
- Mevsimsel tilt önerisi (sabit sistemlerde)

### Faz 4 — Drone Entegrasyonu (donanım gerekli)
- Termal kamera ile hot spot tespiti → %5-20 kayıp + yangın riski
- RGB görüntü + AI ile kuş/ot/fiziksel hasar tespiti
- PID tespiti (karanlık I-V ölçümü)
- Mikro çatlak tespiti (EL testi)
- Otomatik rapor + bakım iş emri

### Fiyatlama Vizyonu
- Temel (temizlik): 500 TL/ay
- Pro (arıza + optimizasyon): 1,500 TL/ay
- Enterprise (drone + tam bakım): 3,000+ TL/ay

## Siradaki
1. **Robot firma outreach** — SelSun, GES RoboSpace, Robsys, Solenser, Doka'ya mail/LinkedIn. "Müşterilerinize ücretsiz 1 aylık verim raporu çıkaralım" teklifi.
2. **Landing page** — "GES'iniz ne kadar para kaybediyor?" calculator'lı tek sayfa
3. **GES sahibi outreach** — LinkedIn + telefon, 5-10 kişi
4. **Validation soruları:** Temizlik ne sıklıkta? Verim kaybını ölçüyor musun? Bu yazılıma aylık 500 TL verir misin?
5. **3+ "evet" gelirse → MVP build**

## Blocker
- Demand validation yapılmadı — GES sahipleri veya robot firmalarıyla konuşulmadan build etme

## Teknik Notlar
- İnverter API erişimi plant sahibinin izni gerektirir (onboarding friction)
- Huawei rate limit katı — çoklu santral izleme stratejisi lazım
- fusion-solar-py Python kütüphanesi mevcut (Huawei için)
- Fronius en kolay API (açık, partnership yok)
- MVP sadece Huawei ile başlasın (pazar lideri)

## Otomasyon Notu
- Landing page oluşturma tamamen Claude'a bırakılabilir
- Robot firma/GES sahibi outreach insan müdahalesi gerektirir
- API entegrasyonu Claude yapabilir ama test için gerçek inverter verisi lazım
