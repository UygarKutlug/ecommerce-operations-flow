# 🚨 Kriz Raporu ve Kök Neden Analizi
**Vaka Kodu:** INC-2026-11-OVERSALE  
**Olay:** Kampanya Dönemi Nebim V3 - Pazaryeri Stok Senkronizasyon Gecikmesi  
**Etki Seviyesi:** Kritik P1 — İptal Kaynaklı Pazaryeri Ceza Puanı ve Müşteri Kaybı Riski  

---

## 📌 1. Olay Özeti
Büyük kampanya dönemi Efsane Cuma / Mega İndirim başlangıcında oluşan anlık trafik patlaması nedeniyle, Nebim V3 ERP üzerindeki merkezi stok hareketlerinin pazaryeri API'lerine aktarım kuyruğunda 42 dakikalık senkronizasyon gecikmesi yaşanmıştır. Bu gecikme süresince fiziksel stoğu tükenen yüksek talep gören 14 farklı kalem için toplam 83 adet çift satış gerçekleşmiştir.

---

## ⏱️ 2. Olay Zaman Çizelgesi (Timeline)
* **21:00:** Kampanya başlangıcı ve sipariş akış hızının normal ortalamanın 12 katına çıkması.
* **21:18:** ERP - Entegratör - Pazaryeri stok güncelleme servislerinde aşırı istek ve zaman aşımı hatalarının birikmeye başlaması.
* **21:35:** Depo yönetim ekranlarında fiziksel stoğu tükenen ürünlere ait yeni siparişlerin düşmeye devam ettiğinin fark edilmesi.
* **21:42:** Operasyon ekibi tarafından kriz tespiti ve acil müdahale protokolünün devreye alınması.
* **22:15:** Kuyruktaki verilerin temizlenmesi, kritik stok kilidinin aktif edilmesi ve sistemin normale dönmesi.

---

## 🔍 3. Kök Neden Analizi 
1. Neden çift satış oluştu? Pazaryerleri tükenen ürünleri satışa kapatmadı.
2. Neden satışa kapatmadı? Nebim V3'ten giden stok düşüm bilgisi pazaryerine anlık ulaşmadı.
3. Neden anlık ulaşmadı? Entegrasyon katmanı her sipariş için tekil istek atarak kuyruğu kilitledi.
4. Neden kuyruk kilitlendi? Kampanya öncesi kritik kalemler için tampon stok tanımlanmamıştı ve toplu işleme limiti aktif değildi.

---

## 🛠️ 4. Alınan Acil Aksiyonlar 
* **Manuel Stok Kilidi:** Son 3 adet stoğa düşen hızlı tükenen ürünlerin entegrasyon üzerinden otomatik olarak sıfır stok statüsüne çekilmesi.
* **Kuyruk Önceliklendirme:** Sipariş çekme servislerinin durdurularak 15 dakika boyunca yalnızca stok güncelleme servisine bant genişliği ayrılması.
* **Müşteri ve Tedarik Operasyonu:** Açıkta kalan 83 sipariş için hızlı mağazadan sevk sorgulaması yapılarak 68 siparişin iptal edilmeden kurtarılması; kalan 15 sipariş için proaktif müşteri iletişimi ve telafi kuponu tanımlanması.

---

## 🛡️ 5. Kalıcı Önleyici Tedbirler 
* **Dinamik Tampon Stok:** Kampanya dönemlerinde fiziksel stoğu 5 adedin altında olan ürünlerin pazaryeri API'lerine otomatik olarak sıfır bildirilmesi kuralı eklendi.
* **Anlık Tetikleme Mimarisi:** Dakikalık periyodik sorgular yerine, stok kritik eşiğin altına düştüğünde anlık tetiklenen web kancası yapısına geçildi.
* **Otomatik Alarm Mekanizması:** API gecikme süresi 3 dakikayı aştığında operasyon ekibine anlık bildirim düşen izleme kuralı tanımlandı.
