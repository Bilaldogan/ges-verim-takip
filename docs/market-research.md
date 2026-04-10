# GES Verim Takip SaaS — Pazar Araştırması

**Tarih:** 2026-04-10
**Durum:** Araştırma tamamlandı, demand validation bekliyor

---

## 1. Türkiye Solar Pazarı

- **Kurulu güç:** ~25.8 GW (Ocak 2026 sonu)
- **GES sayısı:** ~40,000 (39,601 lisanssız + 53 lisanslı)
- **Yıllık büyüme:** ~5 GW / ~5,000 yeni santral
- **2025'te eklenen:** 4.7 GW (rekor yıl)

### Bölgesel Dağılım (Lisanssız GES)
| İl | MW |
|---|---|
| Konya | 1,390 |
| Gaziantep | 1,124 |
| Ankara | 1,079 |
| Şanlıurfa | 377 |

## 2. Problem

- Kirli paneller %3-25 verim kaybı yaratıyor
- 1 MW GES'te %5 kayıp = ~120,000 TL/yıl ekonomik kayıp
- GES sahipleri ne zaman temizlik yapacağını bilmiyor (göz kararı / takvim bazlı)
- "Install and forget" mentalitesi yaygın
- Data-driven karar alan çok az

## 3. İnverter API'leri

| Marka | API | Erişim Kolaylığı | Not |
|---|---|---|---|
| Huawei FusionSolar | REST API | Orta | Rate limit katı, plant sahibi hesap açmalı |
| SMA Sunny Portal | OAuth2 | İyi | API contract gerekli |
| Fronius | Açık REST API | **En kolay** | Partnership yok, doğrudan erişim |
| GoodWe SEMS | API var | Zor | NDA + sales rep gerekli |
| Sungrow iSolarCloud | API var | Orta | NDA + app key |

**Python kütüphanesi:** `fusion-solar-py` (Huawei için PyPI'da mevcut)

**Kritik bulgu:** Tüm büyük markalarda API var ama plant sahibinin izni gerekli. Onboarding friction yaratır ama aşılamaz değil.

## 4. Rakipler

### Türkiye
| Rakip | Durum | Not |
|---|---|---|
| **Solarify (İzmir)** | Tek ciddi yerli rakip | AI-based, kendi datalogger'ı var, fiyat kapalı |
| Solarbita | Temel monitoring | Mobil app, alarm sistemi |
| Entegro Enerji | Danışmanlık | Tozlanma tespit algoritması var |
| SolarRelax | Temel | Uzaktan izleme, arıza bildirimi |

### Global
| Rakip | Ülke | Not |
|---|---|---|
| SmartHelio | İsviçre | Dynamic Cleaning Scheduler, pilot'ta ROI %1,065 |
| SwishOS | Kanada | Mart 2026 launch, $1.5M yatırım, patent bekliyor |
| Solytic | Almanya | €100/yıl + €0.2/kWp — en şeffaf fiyat |
| Meteocontrol | Almanya | Enterprise CMMS |
| AlsoEnergy | ABD | Enterprise DAS + SCADA |

**Temizlik optimizasyonu yapan yerli firma: YOK** — bu boşluk bizim giriş noktamız.

## 5. Ekonomik Model

### GES Sahibi için ROI
- 1 MW GES'te %5 kirlilik kaybı = ~120,000 TL/yıl
- SaaS maliyeti: ~12,000 TL/yıl
- **ROI: 10x**
- SmartHelio referans: tek optimum temizlik = €174,700 kurtarıldı (€15,000 temizlik maliyetiyle)

### Fiyatlandırma (Solytic benchmark bazlı, TR'ye uyarlanmış)
- **Küçük GES (100 kW):** 200-500 TL/ay
- **Orta GES (1 MW):** 500-1,500 TL/ay
- **Enterprise/portfolyo:** Santral bazlı özel fiyat

### Temizlik Maliyetleri (Türkiye)
- 500-2,000 panel: 3-5 TL/panel
- 2,000-5,000 panel: 2-3.5 TL/panel
- Önerilen sıklık: yılda 1-2 (kurak bölgelerde daha sık)

## 6. Gelir Projeksiyonu

| Dönem | Müşteri | Ort. ARPU | MRR (TL) | MRR (USD) |
|---|---|---|---|---|
| 6 ay | 50 | 500 TL | 25,000 | ~$650 |
| 12 ay | 150 | 700 TL | 105,000 | ~$2,700 |
| 18 ay | 300 | 1,000 TL | 300,000 | ~$7,700 |

## 7. Riskler

1. **API erişim friction** — her müşteri için inverter hesabı ayarlanması
2. **Huawei rate limit** — en yaygın marka ama API kısıtlı
3. **Solarify mevcut** — 4+ yıllık yerli rakip
4. **Düşük ARPU** — TR fiyatlarıyla yüksek müşteri sayısı gerekli
5. **GES sahipleri teknik değil** — yazılıma para vermeye dirençli olabilir

## 8. Verdict: CONDITIONAL GO

**Koşul:** 5-10 GES sahibiyle görüşme yap, 3+ tanesi "evet buna para veririm" derse → build.

### Validation Adımları
1. Landing page + verim kaybı calculator
2. 5-10 GES sahibi cold outreach (LinkedIn + telefon)
3. Huawei FusionSolar API pilot (rate limit testi)
4. MVP: sadece Huawei + temizlik optimizasyonu

---

## Kaynaklar
- Ember - Turkey solar capacity
- PV Magazine - Turkey 4.7 GW in 2025
- GENSED - İllere göre lisanssız GES kurulu gücü
- Enerji Ekonomisi - GES sayısı 40 bine yaklaştı
- Huawei FusionSolar Northbound API docs
- SMA Developer Portal
- Fronius Solar API docs
- SmartHelio Dynamic Cleaning Scheduler
- PV Magazine - SwishOS launch
- Solytic PV Monitoring comparison
- Solarify.io
- NREL O&M budgeting
