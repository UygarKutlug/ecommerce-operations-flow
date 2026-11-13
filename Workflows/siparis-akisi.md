# Uçtan Uca Sipariş ve Operasyon Akışı

Aşağıdaki şema, pazaryerinden gelen bir siparişin Nebim ERP üzerinden depoya, faturalandırmaya ve kargoya giden uçtan uca yolculuğunu göstermektedir.

```mermaid
graph TD
    A[Müşteri Siparişi - Trendyol/Hepsiburada] -->|Entegratör ile Aktarım| B(Nebim ERP - Stok Rezervasyonu)
    B --> C{Stok / Varyant Kontrolü}
    C -->|Hatalı / Çakışma Var| D[Hatalı Siparişler Havuzu / Manuel Müdahale]
    C -->|Sorunsuz| E[Depo Toplama Listesi - Picking List]
    E --> F[El Terminali ile Barkod Doğrulama]
    F --> G[Paketleme ve Kolileme]
    G --> H[Nebim Üzerinden E-Fatura Kesimi]
    H --> I[Kargo Barkodu Eşleştirme]
    I --> J[Kargo Firmasına Teslim ve Sevk]
    J --> K[Müşteriye Teslimat / Finansal Mutabakat]
    K --> L{İade Durumu Var mı?}
    L -->|Evet| M[İade Kabul ve Satışa Uygunluk Kontrolü]
    L -->|Hayır| N[Süreç Tamamlandı]
