# Safety 4.0 Bootcamp — Panel Ebatlama Hattı (Lab 1–5)

Otomatik Ahşap Ebatlama (Panel Beam Saw) ve Robotik İstifleme Hattı için hazırlanmış Safety 4.0 Bootcamp laboratuvar föyleri (1–5. hafta). Föyler PaketPro 3000 örnek föylerinin düzeni korunarak bu makineye uyarlanmış ve doldurulmuştur.

> Bu çalışma bir eğitim çıktısıdır; resmî denetim, uygunluk değerlendirmesi veya belgelendirme değildir ve CE/mevzuat uygunluğu garantisi vermez.

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

| Lab | Konu | Çıktı | Evidence Pack |
|---|---|---|---|
| 1 | Safety Architecture | Safety Function Map | EP 03 |
| 2 | IEC 62443 Mini Workshop | Zone / Conduit Diagram | EP 05 |
| 3 | Threat & Risk + Risk Matrix | Risk Register | EP 04 |
| 4 | Secure Remote Access | Secure Architecture | EP 02 + EP 06 |
| 5 | SBOM / CVE / Patch | Vulnerability Decision | EP 09 · 10 · 11 |

## Dosyalar

| Dosya | Açıklama |
|---|---|
| [`laboratuvarlar/Panel_Ebatlama_Hatti_Lab_1-4.pdf`](laboratuvarlar/Panel_Ebatlama_Hatti_Lab_1-4.pdf) | Kapak + Lab 1–4 (5 sayfa) |
| [`laboratuvarlar/Panel_Ebatlama_Hatti_Lab_5.pdf`](laboratuvarlar/Panel_Ebatlama_Hatti_Lab_5.pdf) | Lab 5 (1 sayfa) |

## Özet bulgular

**Lab 1 — Safety Architecture:** Başlıca tehlikeler dönen testereyle kesilme, baskı kirişi ve pusher arasında ezilme, robotun taşıdığı panelin düşmesidir. Emniyet fonksiyonları ışık bariyeri → STO, kapı kilidi + durma izleme, vakum düşmesinde robot durdurma, alan tarayıcı ve acil stoptur.

**Lab 2 — Zone / Conduit:** Varlıklar kurumsal, DMZ, operasyon, hücre ve safety olmak üzere 5 bölgeye ayrıldı. Internete açık uzak bakım router'ı hücre ağında kalamaz, DMZ'ye taşınmalıdır. Uzak erişim kararları: jump server, VPN, MFA, kişisel hesap, tam oturum kaydı, varsayılan kapalı.

**Lab 3 — Risk Register:**

| Senaryo | L | S | E | Skor | Öncelik |
|---|---|---|---|---|---|
| Dış saldırgan → uzak bakım router'ı → Safety PLC parametresi → kapı testere dönerken açılır | 2 | 3 | 3 | 18 | Kritik |
| İmzasız reçete → ağırlık verisi bozulur → panel düşer | 2 | 3 | 2 | 12 | Yüksek |
| USB → robot güvenli alan konfigürasyonu → robot çarpması | 1 | 3 | 1 | 3 | Düşük (S=3 bayraklı) |

Reçetede ölçünün 2 mm kaydırılması insana zarar vermediği için emniyet bulgusu değil, kalite ve iş sürekliliği riski olarak ayrı ele alındı.

**Lab 4 — Secure Remote Access:** Hedef mimaride erişim VPN + MFA ile, kişisel hesapla ve jump server üzerinden yapılır; oturumlar kaydedilir, bağlantı varsayılan kapalıdır. Safety PLC'ye uzaktan ulaşılamaz, parametreleri yalnızca yerinde değiştirilir.

**Lab 5 — SBOM / CVE / Patch:** Component X (CVSS 9.8) bugünkü mimaride üç şartı da sağladığı için etkiler. Üretim durdurulmaz; önce telafi önlemi alınır, yama test ortamında denendikten sonra bakım penceresinde uygulanır. Yama sonrası emniyet fonksiyonlarının testi yapılır.

## Notlar

- Föylerdeki PLr değerleri eğitim amaçlı tahmindir; gerçek değerler makine üreticisinin risk değerlendirmesinden alınmalıdır.
- Lab 1–4 föylerindeki makine bilgileri (varlık listesi, uzak bakım router'ı, reçete akışı) bu eğitim için varsayılmış tipik bir mimariyi yansıtır.

## Hazırlayan

Sabri Baz · 240541164 · 23.10.2026
