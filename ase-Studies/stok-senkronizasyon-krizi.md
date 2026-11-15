# Kriz Raporu ve Kok Neden Analizi

Vaka Kodu: INC-2026-11-OVERSALE  
Olay: Kampanya Donemi Nebim V3 - Pazaryeri Stok Senkronizasyon Gecikmesi  
Etki Seviyesi: Kritik P1 - Iptal Kaynakli Pazaryeri Ceza Puani ve Musteri Kaybi Riski  

---

## 1. Olay Ozeti
Buyuk kampanya donemi baslangicinda olusan anlik trafik patlamalari nedeniyle, Nebim V3 ERP uzerindeki merkezi stok hareketlerinin pazaryeri API'lerine aktarim kuyrugunda gecikme yasanmistir. Bu gecikme suresince fiziksel olarak tukenen yuksek talep goren urunler icin toplam 83 adet cift satis yasanmistir.

---

## 2. Olay Zaman Cizelgesi
* 21:00: Kampanyanin baslamasi ve siparis akis hizinin normalin ustune cikmasi.
* 21:18: ERP ve pazaryeri stok guncelleme servislerinde asiri istek ve zaman asimi hatalarinin birikmesi.
* 21:35: Depo yonetim ekranlarinda fiziksel olarak tukenen urunlere ait yeni siparislerin dusmeye devam ettiginin fark edilmesi.
* 21:42: Operasyon ekibi tarafindan krizin tespiti ve acil mudahale protokolunun devreye alinmasi.
* 22:15: Kuyruktaki verilerin temizlenmesi ve sistemin normale donmesi.

---

## 3. Kok Neden Analizi
1. Neden cift satis olustu? Pazaryerleri tukenen urunleri satisa kapatmadi.
2. Neden satisa kapatmadi? Nebim V3'ten giden stok bilgisi pazaryerine anlik erismedi.
3. Neden aninda ulasamadi? Entegrasyon katmani her siparis icin tekil istek atarak kuyrugu kilitledi.
4. Neden kuyruk kilitlendi? Kampanya oncesinde kritik kalemler icin tampon stok tanimi yapilmamisti.

---

## 4. Alinan Acil Aksiyonlar
* Manuel Stok Kilidi: Hizli tukenen urunlerin entegrasyon uzerinden otomatik olarak sifir stok statusune cekilmesi.
* Kuyruk Onceliklendirme: Siparis cekme servislerinin durdurularak yalnizca stok guncelleme servisine bant genisligi ayrilmasi.
* Musteri Operasyonu: Acikta kalan siparisler icin hizli magazadan sevk sorgulamasi yapilarak iptallerin onlenmesi.

---

## 5. Kalici Onleyici Tedbirler
* Dinamik Tampon Stok: Kampanya donemlerinde fiziksel stogu kritik seviyede olan urunlerin pazaryerlerine otomatik sifir bildirilmesi kurali eklendi.
* Anlik Tetikleme Mimarisi: Periyodik sorgular yerine stok dustugunde tetiklenen yapiya gecildi.
* Otomatik Alarm: API gecikme suresi siniri astiginda operasyon ekibine bildirim dusmesi saglandi.
