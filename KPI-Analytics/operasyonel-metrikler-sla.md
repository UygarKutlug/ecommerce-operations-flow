# 📊 Operasyonel KPI, SLA ve Performans Metrikleri

Bu modül; depo verimliliğini, sevkiyat hızını, stok doğruluğunu ve iade operasyonlarının başarısını ölçmek için kullanılan temel performans göstergelerini KPI ve hizmet seviyesi anlaşmalarını SLA kapsar.

---

## 🎯 Temel Operasyonel Metrikler (KPI Tablosu)

| Metrik Adı | Hedef Eşik (Target) | Formül / Hesaplama Yöntemi | İş Etkisi ve Aksiyon |
| :--- | :--- | :--- | :--- |
| **Sipariş Karşılama Süresi (SLA)** | < 24 Saat | `Kargo Veriliş Zamanı - Sipariş Düşüş Zamanı` | Müşteri memnuniyeti ve pazaryeri ceza puanı önleme. |
| **Stok Doğruluk Oranı** | %99.2+ | `(Fiziksel Sayım / ERP Kaydı) * 100` | Çift satış (overselling) ve iptal oranlarını minimize etme. |
| **İade İşleme Süresi** | < 48 Saat | `Depo Kabul Zamanı - Raf/Stok Yeniden Giriş` | Müşteri memnuniyetsizliğini ve destek taleplerini azaltma. |
| **Hatalı Ürün / Yanlış Gönderim** | < %0.3 | `(Hatalı Sipariş Adedi / Toplam Sipariş) * 100` | Depo toplama (picking) paketleme hatalarının tespiti. |

---

## 📈 Raporlama ve Takip Mekanizmaları

* **Günlük Sabah Operasyon Özeti:** Önceki günün toplam sipariş hacmi, kargoya verilemeyen (geciken) siparişler ve stok uyumsuzluklarının yönetime raporlanması.
* **Hylton / Aylık Mutabakat:** Pazaryeri komisyon kesintileri, kargo faturaları ve iade kesintilerinin finansal kontrolü.
