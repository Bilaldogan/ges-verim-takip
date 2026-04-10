@/Users/bilaldogan/Desktop/ideas/CLAUDE.md

# GES Verim Takip SaaS

## Nedir
GES sahipleri için AI-powered panel verim takip + temizlik optimizasyonu platformu.

## Tech Stack
- **Frontend:** Next.js 15 + Tailwind + shadcn/ui
- **Backend:** Next.js API routes (başlangıçta ayrı backend yok)
- **DB:** Supabase (PostgreSQL + Auth + Realtime)
- **Inverter API:** Huawei FusionSolar (MVP), sonra SMA, Fronius, GoodWe, Sungrow
- **AI:** Claude API (anomali tespiti, temizlik zamanı optimizasyonu)
- **Payments:** Stripe
- **Deploy:** Vercel
- **Boilerplate:** ixartz/SaaS-Boilerplate

## MVP Kapsami
- Sadece Huawei FusionSolar inverter
- Tek feature: verim düşüşü tespiti + temizlik zamanı önerisi
- Dashboard: verim grafiği + kirlilik tahmini + maliyet kaybı hesabı
- Türkçe UI (İngilizce sonra)

## Gelistirme Kurallari
- Demand validation OLMADAN feature build etme
- Landing page + outreach öncelikli
- İnverter API erişimi için gerçek GES sahibi lazım — mock data ile başla, gerçek veriyle doğrula
- Her feature'da "GES sahibi bunu anlar mı?" filtresi uygula — teknik olmayan kullanıcı hedef
