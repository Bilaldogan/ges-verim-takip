# GES Verim Takip — Handoff

## Durum: queued
Son guncelleme: 2026-04-10

## Nedir
GES (Güneş Enerji Santrali) sahipleri için panel verim takip + AI temizlik optimizasyonu SaaS'ı. İnverter API'lerinden veri çekip kirlilik kaynaklı verim düşüşünü tespit eder, optimal temizlik zamanını önerir.

## Strateji
- **Faz 1 (şimdi):** Demand validation — landing page + 5-10 GES sahibi görüşme
- **Faz 2:** MVP build — Huawei FusionSolar API + temizlik optimizasyonu
- **Faz 3:** RaaS katmanı — hazır robot al, temizlik hizmeti sun (sermaye gelince)

## Yapilan
- Pazar araştırması tamamlandı (docs/market-research.md)
- 40,000 GES, yılda 5,000 yeni, yerli rakip az
- İnverter API'leri araştırıldı (Huawei, SMA, Fronius, GoodWe, Sungrow)
- Gelir projeksiyonu: 150 müşteri × 700 TL/ay = ~$2,700 MRR (12 ay)
- GitHub repo + submodule oluşturuldu

## Siradaki
1. **Landing page** — "GES'iniz ne kadar para kaybediyor?" calculator'lı tek sayfa
2. **GES sahibi outreach** — LinkedIn + telefon, 5-10 kişi, "ücretsiz 1 aylık verim analizi" teklifi
3. **Validation soruları:** Temizlik ne sıklıkta? Verim kaybını ölçüyor musun? Bu yazılıma aylık 500 TL verir misin?
4. **3+ "evet" gelirse → MVP build:**
   - Huawei FusionSolar API entegrasyonu (tek marka ile başla)
   - Dashboard: verim grafiği + kirlilik tahmini + temizlik önerisi
   - Tech: Next.js + Supabase + inverter API
5. **Fiyat testi:** Landing page'de 3 tier (200 / 700 / 1,500 TL/ay)

## Blocker
- Demand validation yapılmadı — GES sahipleriyle konuşulmadan build etme

## Teknik Notlar
- İnverter API erişimi plant sahibinin izni gerektirir (onboarding friction)
- Huawei rate limit katı — çoklu santral izleme stratejisi lazım
- fusion-solar-py Python kütüphanesi mevcut (Huawei için)
- Fronius en kolay API (açık, partnership yok)
- MVP sadece Huawei ile başlasın (pazar lideri)

## Otomasyon Notu
- Landing page oluşturma tamamen Claude'a bırakılabilir
- GES sahibi bulma/outreach insan müdahalesi gerektirir
- API entegrasyonu Claude yapabilir ama test için gerçek inverter verisi lazım
