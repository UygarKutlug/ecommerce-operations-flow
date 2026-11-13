# Uçtan Uca E-Ticaret Sipariş ve Operasyon Süreç Akışı 

Bu doküman, pazaryerlerinden (Trendyol, Hepsiburada vb.) gelen bir siparişin Nebim ERP sistemine düşmesinden başlayarak depoda hazırlanması, faturalandırılması, kargolanması ve olası iade süreçlerinin yönetilmesine kadar olan standart operasyon akışını tanımlar.

---

## 1. Aşama: Sipariş Alımı ve ERP Entegrasyonu 
* **Sipariş Tetiklenmesi:** Müşteri pazaryeri üzerinden siparişi onaylar ve ödeme onayı tamamlanır.
* **Entegrasyon Aktarımı:** Entegratör yazılım aracılığıyla sipariş verileri (müşteri bilgisi, SKU, varyant, adet, tutar) belirli periyotlarla **Nebim ERP** ekranına aktarılır.
* **Stok Rezervasyonu:** Sipariş Nebim'e düştüğü an ilgili SKU'nun kullanılabilir stoğu sistemde rezerve edilir ve diğer pazaryerlerindeki stok adedi güncellenir (çift satış önleme).
* **İlk Kontrol:** Barkod eşleşmesi hatalı olan veya stok uyuşmazlığı tespit edilen siparişler "Hatalı Siparişler" havuzuna düşer ve operasyon sorumlusu tarafından manuel müdahale ile düzeltilir.

## 2. Aşama: Depo Toplama ve Hazırlık (Picking & Packing)
* **Toplama Listesi :** Nebim üzerinden onaylanan siparişler için raf/lokasyon bazlı toplama listeleri oluşturulur ve depo ekibine iletilir.
* **Ürün Toplama ve Doğrulama:** Depo personeli ürünleri raflardan toplar. El terminali veya barkod okuyucu ile ürün barkodu okutularak renk/beden (varyant) doğruluğu teyit edilir.
* **Paketleme :** Doğrulanan ürünler, ürün tipine uygun koruyucu ambalaj ve kargo poşeti/kolisi ile hasar görmeyecek şekilde paketlenir.

## 3. Aşama: Faturalandırma ve Kargo Etiketleme (Invoicing & Dispatch)
* **E-Arşiv / E-Fatura Kesimi:** Paketlemesi tamamlanan siparişin faturası Nebim üzerinden otomatik veya toplu olarak kesilir ve entegratör aracılığıyla pazaryeri paneline iletilir.
* **Kargo Barkodu Eşleştirme:** Pazaryeri tarafından atanan kargo firmasına ait taşıma barkodu yazdırılır ve doğru paketle eşleştirilerek paketin üzerine yapıştırılır.
* **Kargo Teslimi:** Gün sonunda hazırlanan tüm paketler kargo görevlisine teslim edilir, barkodlar okutularak zimmet/teslim tutanağı alınır ve sipariş statüsü **"Kargoya Verildi"** olarak güncellenir.

## 4. Aşama: Teslimat Sonrası ve İade Yönetimi (Post-Delivery & Returns)
* **Teslimat Takibi:** Kargo entegrasyonu üzerinden müşteriye teslimat bilgisi panele yansır ve hakediş/finansal mutabakat süreci başlar.
* **İade Kabulü :** Müşteriden iade gelen paketler depoda açılır; ürünün kullanılmamış, etiketi kopmamış ve tekrar satılabilir durumda olup olmadığı kontrol edilir.
* **Stok İadesi veya Red:** Onaylanan iadeler Nebim üzerinden iade faturası/girişi yapılarak tekrar satış stoğuna alınır; hasarlı veya şartlara uymayan ürünler görselleriyle belgelenerek pazaryeri üzerinden iade reddi (itiraz) sürecine sokulur.
