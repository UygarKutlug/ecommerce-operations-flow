# 🔄 İade, Kalite Kontrol ve Hakediş Mutabakat Süreci

Bu modül; müşterinin pazaryeri üzerinden başlattığı iade talebinin depoya ulaşması, ürünün fiziksel kontrolü, ERP stoklarına kazandırılması veya reddedilmesi ile finansal hakediş mutabakatlarının yapıldığı adımları kapsar.

---

## 📋 İade Kabul ve Fiziksel Akış Şeması

```mermaid
graph TD
    A[Müşteri İade Talebi Oluşturur] --> B{İade Kargo Kodu Alındı mı?}
    B -->|Evet| C[Kargo Depoya Teslim Eder]
    B -->|Hayır| D[Süre Aşımı / İade İptal]
    
    C --> E[Depo Giriş ve Barkod Okutma]
    E --> F[Kalite Kontrol KK İncelemesi]
    
    F --> G{Ürün Durumu Nedir?}
    G -->|Satılabilir Sağlam| H[Nebim V3 Ana Stoka İade Al]
    G -->|Hasarlı / Eksik Parça| I[Kusurlu Ürün / Red Süreci]
    G -->|Yanlış Ürün / Farklı Ürün| J[Tüketici / Operasyon İtiraz Havuzu]
    
    H --> K[E-Fatura / Alacak Dekontu Kesimi]
    K --> L[Pazaryeri Kesinti ve Hakediş Mutabakatı]
