# YMGK-Proje-Otomatik-Ah-ap-Ebatalama-Panel-Beam-Saw-ve-Robotik-stifleme-Hatt-
# Safety 4.0 Bootcamp — Panel Ebatlama Hattı (Lab 1–4)

Otomatik Ahşap Ebatlama (Panel Beam Saw) ve Robotik İstifleme Hattı için hazırlanmış Safety 4.0 Bootcamp laboratuvar föyleri (1–4. hafta).

> Bu çalışma bir eğitim çıktısıdır; resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir.

## Makine

AİMSAD üye makine portföyünden seçilen panel ebatlama hattı:

- 4000+ d/dk dönen dairesel testereler
- Baskı kirişi ve itme kolu (pusher)
- 50–100 kg panel taşıyan vakumlu robot
- Işık bariyeri, kapı kilidi, vakum izleme → Safety PLC (PROFIsafe) → STO
- MES/ERP ve CAD/CAM yazılımından sürekli reçete (XML/G-kodu) akışı

### Seçim gerekçesi

1. **Yüksek fiziksel risk:** Testere, baskı kirişi ve havada panel taşıyan robot, zengin bir Safety PLC donanımı gerektirir.
2. **Geniş siber saldırı yüzeyi:** Fabrika ağından sürekli reçete alındığı için Purdue modeli, endüstriyel firewall, DPI ve dijital imza kontrolü işlenebilir.
3. **Çift yönlü risk analizi:** Hem insana yönelik sabotaj (testere dönerken kapının açılması) hem de sessiz üretim sabotajı (kesim ölçüsünün 2 mm kaydırılması) aynı raporda ele alınır.

## İçerik

| Lab | Konu | Çıktı |
|---|---|---|
| 1 | Safety Architecture | Safety Function Map |
| 2 | IEC 62443 Mini Workshop | Zone / Conduit Diagram |
| 3 | Threat & Risk + Risk Matrix | Risk Register |
| 4 | Secure Remote Access | Secure Architecture |

## Dosyalar

- `Panel_Ebatlama_Hatti_Lab_1-4.pdf` — Doldurulmuş föyler (kapak + 4 laboratuvar, 5 sayfa)

## Özet bulgular

- **En yüksek riskli senaryo:** İnternete açık uzak bakım router'ı üzerinden Safety PLC parametrelerinin değiştirilmesi sonucu testere dönerken kapının açılması (skor 18, Kritik).
- **Temel öneri:** Uzak erişim VPN + MFA + jump server ile yapılmalı, varsayılan olarak kapalı olmalı ve Safety PLC'ye ağdan yazma erişimi olmamalıdır.
- **Reçete güvenliği:** Reçete dosyalarına dijital imza ve hash doğrulaması uygulanmalıdır. Bu önlem hem ölçü sabotajını hem de ağırlık verisi değişikliğiyle oluşabilecek panel düşmesini önler.

## Hazırlayan

Ad Soyad · Grup · Tarih
