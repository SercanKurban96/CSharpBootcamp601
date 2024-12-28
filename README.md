#  <img height="50" src="https://user-images.githubusercontent.com/25181517/121405384-444d7300-c95d-11eb-959f-913020d3bf90.png"> EĞİTİM KAMPI
👋 Merhabalar, oluşturmuş olduğum bu repo, Murat Yücedağ hocamızın YouTube üzerinden hazırlamış olduğu C# Eğitim Kampı süresince tamamlamış olduğum projeleri içermektedir. Bu eğitimde 601 modül olan MongoDb konusu anlatılmaktadır.

## 🖥️ C# Eğitim Kampı Ders 24 - C# ile MongoDb Kullanımı 1
### 📆 Tarih: 24 Aralık 2024

![image](https://github.com/user-attachments/assets/f61ac23a-5ee8-472b-9380-a2771d219a36)

Bu eğitimde MongoDb üzerinden çalışmalarımızı yapacağız. Yeni bir tane form oluşturduk ve ismini CSharpBootcamp601 olarak belirledik. Bu sefer "Müşteriler" adlı tablosundan işlemlerimizi yapacağız. Form tasarımımızı yaptıktan sonra Entities adında bir tane klasör oluşturuyoruz. Daha sonra MongoDb için paket yükleyeceğiz.

![image](https://github.com/user-attachments/assets/9a5dbb25-b277-4502-9ee2-771840d0f96b)

Kuracağımız paketler MongoDB.Bson ve MongoDB.Driver olacaktır.

Paketler kurulduktan sonra Entities klasörüne yeni bir tane class ekliyoruz ve ismini Customer olarak belirliyoruz.

![image](https://github.com/user-attachments/assets/b42763de-b2a4-4ccb-8f88-aa80610587ce)

Customer'a ait entitylerimizi girdikten sonra ID kısmında 2 tane Attribute eklememiz gerekmektedir. Bunlardan ilki BsonId, ikincisi ise BsonRepresentation olacaktır. BsonRepresentation'dan sonra içine BsonType.ObjectId ekliyoruz.

## MongoDb Nedir?

MongoDB, bir NoSQL (SQL olmayan) veritabanı yönetim sistemi (DBMS) türüdür. Geleneksel ilişkisel veritabanlarından farklı olarak, verileri tablolar yerine belgeler (documents) şeklinde saklar. Bu belgeler, JSON-benzeri BSON (Binary JSON) formatında tutulur ve dinamik bir yapıya sahiptir, yani önceden tanımlı bir şema gerektirmez. Bu, MongoDB'yi esnek ve ölçeklenebilir bir çözüm haline getirir.

### MongoDB'nin Özellikleri
1. Şemasız Yapı: Veriler dinamik olarak şekillenebilir, bu da uygulamanızın hızla değişen gereksinimlerine uyum sağlar.

2. Doküman Tabanlı Depolama: JSON formatındaki belgeler, karmaşık veri yapılarını kolayca ifade etmeye olanak tanır.

3. Yüksek Performans: Büyük veri kümeleri ve yoğun okuma/yazma işlemleri için optimize edilmiştir.

4. Yatay Ölçeklenebilirlik: Sharding (parçalama) adı verilen bir yöntemle büyük veritabanları, birden fazla sunucuya bölünebilir.

5. Esnek Sorgulama: MongoDB, güçlü sorgu dilleri ve toplu işlem (aggregation) desteği sunar.

6. ACID Desteği: Son sürümlerde, işlemelere (transactions) ve tutarlılığa daha fazla önem verilmiştir.

### MongoDB Kullanım Alanları

1. Büyük Veri ve Analitik: Hızlı veri analizi ve işlenmesi gereken projelerde.

2. Gerçek Zamanlı Uygulamalar: Chat uygulamaları, canlı veri akışları.

3. IoT Uygulamaları: Büyük hacimli ve yapılandırılmamış verilerin saklanması.

4. E-ticaret: Ürün katalogları ve kullanıcı verileri gibi dinamik içerik yönetimi.

MongoDB, hem geliştiriciler hem de işletmeler için esneklik, hız ve ölçeklenebilirlik sunarak popüler bir veritabanı çözümü haline gelmiştir.


## BSON Nedir?

BSON (Binary JSON), MongoDB'nin verileri depolamak ve taşımak için kullandığı ikili (binary) bir veri formatıdır. JSON (JavaScript Object Notation) formatının bir uzantısıdır ve JSON'un eksikliklerini gidermek için tasarlanmıştır. BSON, özellikle MongoDB'nin performansını ve esnekliğini artırmak için optimize edilmiştir.

### BSON'un Özellikleri

1. İkili Format: JSON verilerini ikili (binary) bir formata dönüştürür, bu da daha hızlı işlem ve veri aktarımı sağlar.

2. Ek Veri Türleri: JSON'un desteklemediği veri türlerini destekler:

*** Tarih/zaman (Date)

*** 64-bit tamsayılar (Int64)

*** Binary veri (Binary Data)

*** Nesne kimlikleri (ObjectId)

3. Hızlı Seri ve Deserilializasyon: Verilerin bellekten okunması ve yazılması daha hızlıdır.

4. Boyut Optimizasyonu: JSON'a göre daha küçük boyutlara sahip olabilir, çünkü veri türlerini belirtmek için meta veriler içerir.

5. Belge Tabanlı Yapı: MongoDB'deki her bir belge bir BSON nesnesi olarak saklanır.

### BSON ve JSON Arasındaki Farklar

![image](https://github.com/user-attachments/assets/131452fd-f032-4b49-8657-1d97a41927c4)

### BSON'un MongoDB'deki Rolü

*** MongoDB, verileri disk üzerinde BSON formatında saklar.

*** Ağ üzerinden veri taşınırken de BSON formatı kullanılır.

*** BSON sayesinde MongoDB, karmaşık ve büyük veri yapılarını etkili bir şekilde yönetebilir.

Kısacası, BSON, MongoDB'nin JSON benzeri kolaylığı ile yüksek performansı bir araya getiren bir veri formatıdır.
