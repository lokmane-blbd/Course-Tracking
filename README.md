# Ders Takip Sistemi
Ders Takip Sistemi, Bilgisayar Mühendisliği Fakültesi yüksek lisans ve doktora öğrencilerinin ders kayıtlarını takip etmek amacıyla tasarlanmış bir yazılım projesidir.

<h2>Kullanıcı Arayüz Tasarımı </h2>

<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/90517d9f-84b2-451b-9b03-83f36189c0c9" align="right" width="300px"/>

**Loading Ekranı ve Ana Sayfa:** Ana sayfa, Ders Takip Sistemi'nin kullanıcıların karşılaştığı ilk sayfadır. </br>
Loading Ekranı:</br>
Loading ekranı, kullanıcının beklemesini engelleyerek sistemin yüklenme sürecini gösteren bir ekran tasarımıdır.
<br clear="left"/>

Ana Sayfa:</br>
Ana sayfa üzerinde bir navigasyon çubuğu (navbar) bulunmalıdır.
Navbar, kullanıcılara ana sayfa, duyurular, etkinlikler, hakkında gibi sekmeleri seçme imkanı sunar.
Giriş yapma işlemi  için "Giriş" butonu vardır.</br>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/ff21ad9d-31c5-4778-9621-acc85ef994d4" width="500px" />

**Giriş Sayfasi:** Giriş sayfasında kullanıcılar, numara ve şifrelerini girerek sisteme giriş yapabilirler. Ayrıca, iki seçenek bulunmalıdır: "Öğrenci" ve "Öğretmen". Kullanıcılar, kendi rol ve yetkilerine göre ilgili seçeneği seçerek giriş yapabilirler. Giriş işlemini tamamlamak için "Giriş" butonu bulunmalıdır. Bu sayede kullanıcılar doğru kimlik bilgilerini girerek ilgili kullanıcı hesabına erişebilirler.</br>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/afd28093-41c1-4e9c-9d96-1e8e9ccda4c8" width="500px"/>

**Öğrenci Arayuzu:** Öğrenci arayüzünde, öğrencinin kişisel bilgileri yer alır. Bu bölümde, öğrencinin adı, numarası, bölümü ve diğer önemli bilgileri görüntülenir. 
Ders seçme bölümü, öğrencinin derslerini seçmesini sağlar. Bu bölümde, öğrenciye sunulan ders listesi gösterilir ve öğrenci istediği dersleri seçerek kaydolabilir.</br>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/86619f77-a923-4e96-976b-35db34c837f6" height="300px" width="500px"/>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/7888580b-6620-4e11-ad45-1c09c3460af8" height="300px" width="500px"/>

**Öğretmen Arayuzu:** Öğretmen arayüzünde, öğretmenin kişisel bilgileri bulunur. Bu bölümde, öğretmenin adı, numarası, bölümü ve diğer önemli bilgileri görüntülenir. Ayrıca, öğretmenin verdiği derslerin bir listesi sunulur.
Verdiği dersler listesi bölümü, öğretmenin hangi dersleri verdiğini gösterir. Bu bölümde, öğretmenin dersleri ve ilgili bilgileri, ders adı, kodu, saatleri vb.
Ders aldığı öğrenciler listesi bölümü, öğretmenin hangi öğrencilerin dersine kayıtlı olduğunu gösterir.</br>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/bb221367-22bb-49f6-a012-b00c6b6e7127" height="300px" width="500px"/>
<img src="https://github.com/ChaimaaNairi/Course_Tracking_System/assets/83820363/475e53c9-e7e8-4283-af45-ab322425b4b4" height="300px" width="500px" />

<h2>Veri Tabanı Tasarımı</h2>

+ Veritabanı, PostgreSQL veritabanı yönetim sistemi ve pgAdmin4 grafik kullanıcı arayüzü kullanılarak tasarlandı.

+ **Öğrenci giriş tablosu:** öğrenci id, kullanıcı adı ve şifre alanlarını içerir. 

+ **Öğrenci bilgileri tablosu :** Ad soyad , cinsiyet, bölüm, öğrenci id, dönem alanlarını içerir. 

+ **Dönem dersleri tablosu:** Dönem, ders id , ders adı, gün id, saat, öğretmen bilgilerini içerir. 

+ **Öğretim görevlisi giriş tablosu:** Kullanıcı adı, öğretim üyesi id, şifre bilgilerini içerir. 

+ **Öğretim görevlisi bilgileri tablosu:** ad soyad, cinsiyet, öğretmen bilgilerini içerir. 

+ **Dersi alan öğrenciler tablosu:** Kullanıcı adı, ders id, dönem bilgilerini içerir. 

+ **Ders tablosu:** Öğretim üyesi id, dersin adı, dersin kredisi, ders id, saat id, dönem id, gün id, ders türü bilgilerini içerir.



<h2>Backend Tasarımı</h2>
Kodun çalışma algoritması, Ders Takip Sistemi'nin en önemli parçasıdır. Bu kısım, veri tabanından alınan verileri Backend’de işleyip arayüze sunmayı içerir. Backend SQL,  C# ve .NET programlama dilleri kullanılarak geliştirilmiştir.</br>
Backend kısmında, dört farklı veri yapısı kullanılmıştır. Bunlar; </br>
1 - Öğrenci ve öğretim görevlisi verilerinin tutulduğu AVL ağacıdır. Bu ağaç, veri tabanındaki “ogrenciBilgi” ve “ogrenciGiris” tablolarındaki verileri tutan”ogrenciAVL” ile “ogretimGorevlisiBilgi” ve “ogretimGorevlisiGiris” tablolarındaki verileri tutan “ogretimGorevlisiAVL” den oluşur.</br>
2 - Seçilen derslerin tutulduğu “IkiliBagliListe” dir. “IkiliBagliListe”, öğrencinin seçtiği dersleri tutan “donemDersleri” tablosunu ve kayıt sırasında veri tabanına kaydedilene kadar elde tutulan dersleri içerir. </br>
3 - Tüm derslerin tutulduğu “HashTablosu” dur. “HashTablosu”, derslerin içinde bulunan “donem_id” anahtarını kullanarak verileri ilgili listede tutar.</br>
4 - “HashTablosu” nun içinde “donem_id” sine göre dersleri tutan “dersListe” dir. Bu yapı, aynı “donem_id” sine sahip dersleri “HashTablosu” nda sıralı bir şekilde tutar. </br>










