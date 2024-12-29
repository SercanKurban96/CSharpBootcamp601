#  <img height="50" src="https://user-images.githubusercontent.com/25181517/121405384-444d7300-c95d-11eb-959f-913020d3bf90.png"> EĞİTİM KAMPI
👋 Merhabalar, oluşturmuş olduğum bu repo, Murat Yücedağ hocamızın YouTube üzerinden hazırlamış olduğu C# Eğitim Kampı süresince tamamlamış olduğum projeleri içermektedir. Bu eğitimde 601 modül olan MongoDb konusu anlatılmaktadır.

## 🖥️ C# Eğitim Kampı Ders 24 - C# ile MongoDb Kullanımı 1
### 📆 Tarih: 24 Aralık 2024

## :bangbang: MongoDb ile çalışmalarımızı yapmak için MongoDb Community Server programını yüklemeniz gerekmektedir!

![image](https://github.com/user-attachments/assets/f61ac23a-5ee8-472b-9380-a2771d219a36)

Bu eğitimde MongoDb üzerinden çalışmalarımızı yapacağız. Yeni bir tane form oluşturduk ve ismini CSharpBootcamp601 olarak belirledik. Bu sefer "Müşteriler" adlı tablosundan işlemlerimizi yapacağız. Form tasarımımızı yaptıktan sonra Entities adında bir tane klasör oluşturuyoruz. Daha sonra MongoDb için paket yükleyeceğiz.

![image](https://github.com/user-attachments/assets/9a5dbb25-b277-4502-9ee2-771840d0f96b)

Kuracağımız paketler MongoDB.Bson ve MongoDB.Driver olacaktır.

Paketler kurulduktan sonra Entities klasörüne yeni bir tane class ekliyoruz ve ismini Customer olarak belirliyoruz.

![image](https://github.com/user-attachments/assets/5232a847-7db6-4801-99fe-1e05d3b9808a)

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


## ObjectId Nedir?

ObjectId, MongoDB'de her belgenin benzersiz bir şekilde tanımlanmasını sağlayan 12 baytlık bir kimliktir. MongoDB, belgeler için birincil anahtar (_id) alanında varsayılan olarak ObjectId kullanır. Bu, hem belgenin hızlı bir şekilde tanımlanmasını hem de veritabanında benzersiz olmasını sağlar.

### ObjectId'nin Yapısı
Bir ObjectId, 12 bayttan oluşur ve şu şekilde yapılandırılmıştır:

1. 4 Bayt: Unix zaman damgası (saniye cinsinden). Belgenin oluşturulma zamanını belirtir.

2. 5 Bayt: Makine kimliği. Veritabanının çalıştığı makineyi tanımlayan rastgele bir sayı.

3. 3 Bayt: İşlem kimliği (Process ID). Veritabanını çalıştıran işlemi (process) temsil eder.

4. 3 Bayt: Artan bir sayaç. Aynı makine ve işlem üzerinde oluşturulan ObjectId'lerin benzersiz olmasını sağlar.

### ObjectId'nin Özellikleri

Benzersizlik: Her ObjectId benzersizdir ve MongoDB tarafından otomatik olarak üretilir.

Kronolojik Sıra: İçindeki zaman damgası sayesinde, ObjectId'ler oluşturulma sırasına göre sıralanabilir.

Küçük Boyut: ObjectId yalnızca 12 bayt olduğu için veritabanında az yer kaplar.

Otomatik Üretim: Veritabanına belge eklerken _id alanı belirtilmezse, MongoDB bu alan için otomatik olarak bir ObjectId üretir.

### ObjectId'nin Kullanımı

Bir ObjectId genellikle şu formatta görüntülenir:

![image](https://github.com/user-attachments/assets/190be8b2-b23f-47a9-80eb-df529a3e4b39)

Buradaki dize, 24 karakter uzunluğunda bir hexadecimal (16'lık tabanda) temsilidir.

### Avantajları
1. Dağıtılmış Sistemler için Uygun: Benzersiz kimlikler oluşturmak için merkezi bir sunucuya gerek duyulmaz.

2. Tarih Bilgisi: ObjectId'nin zaman damgası, belgenin ne zaman oluşturulduğunu anlamak için kullanılabilir.

3. Performans: Benzersizliği ve düzenli yapısı sayesinde veritabanı işlemlerinde performansı artırır.

### Dezavantajları

1. İnsanlar tarafından okunabilir bir format olmadığı için debugging sırasında karmaşık görünebilir.

2. Zaman damgası bir gizlilik riski oluşturabilir, çünkü belgenin oluşturulma zamanı analiz edilebilir.

ObjectId, MongoDB'nin hızlı, ölçeklenebilir ve güvenilir bir kimlikleme sistemi sunmasını sağlayan temel bir özelliktir.

![image](https://github.com/user-attachments/assets/6d60a55e-0ab3-49d6-aa69-8956120503af)

Bu kez Services isminde bir tane klasör oluşturuyoruz. Klasörü oluşturduktan sonra MongoDbConnection isminde bir tane class oluşturuyoruz.

MongoDbCompass programını açıyoruz.

![image](https://github.com/user-attachments/assets/090f0efa-5c0e-4308-b28b-c21c5d278694)

MongoDb karşımıza ilk olarak bu şekilde çıkacaktır. Bizde herhangi bir bağlantı olmadığı için kendimiz oluşturacağız. Add new connection butonuna tıklıyoruz.

![image](https://github.com/user-attachments/assets/72eea462-8180-4136-a821-41b6d7b1377d)

Burada bize bir bağlantı adresi verecektir. Bu adresi kopyalıyoruz ve Save & Connect butonuna tıklıyoruz.

![image](https://github.com/user-attachments/assets/e56345fc-6a23-40af-a3cd-3b301f917c9f)

Sol tarafta bize veri tabanlarını gösterecektir. Eğer daha önce herhangi bir veri tabanı oluşturmadıysak sadece buradaki üç tanesi gözükecektir.

![image](https://github.com/user-attachments/assets/ba91687b-e128-4ffe-9694-f5697d1d9388)

Tekrardan MongoDbConnection class'ına dönüyoruz. Burada private metoduyla bir tane IMongoDatabase interface'i oluşturup _database isminde bir field ekliyoruz. Daha sonra ctor ile bir constructor oluşturuyoruz.
Burada var türünde bir client değişkeni oluşturup new MongoClient isminde bir metot ekliyoruz ve daha önce MongoDb'den kopyaladığımız bağlantıyı buraya yapıştırıyoruz. Yeni bir veri tabanı oluşturmak için oluşturduğumuz _database field'ini kullanarak client değişkeninden GetDatabase metodunu kullanıyoruz ve burada istediğimiz veri tabanının ismini belirliyoruz. Burada Db601Customer olarak belirledik.

Daha sonra bir tane daha constructor oluşturup bu kez IMongoCollection oluşturup BSonDocument'i ekliyoruz ve GetCustomersCollection isminde bir metot oluşturuyoruz. Bu işlemden sonra return _database.GetCollection<BsonDocument>("Customers"); komutunu yazmış olduk. Buradaki Customers, Db601Customer veri tabanının içerisinde yer alan tablonun ismi olarak eklenecektir.

Buradaki işlemler tamamlandıktan sonra tekrar Services klasörüne yeni bir tane class ekliyoruz ve ismini CustomerOperations olarak belirliyoruz.

![image](https://github.com/user-attachments/assets/f58c1c27-91fc-4f1e-bf7b-3789be4d18b1)

Burada ilk olarak AddCustomer isminde bir metot oluşturduk. Oluşturduktan sonra connection isminde bir değişken tanımlayıp bağlantı adresimizize bağlanma isteğinde bulunduk. Ardından GetCustomersCollection metodunu kullanarak tabloya bağlandık. Ardından parametreleri gönderdik ve en sonunda ekleme işlemi yaptık.

Formumuza giderek ekleme işlemlerimizi yapıyoruz. Ekle butonuna çift tıkladıktan sonra gerekli kodlarımızı yazmaya başlıyoruz.

![image](https://github.com/user-attachments/assets/aa9a9ba5-c412-4044-b2f3-ea002cf2e00a)

Global alana CustomerOperations customerOperations = new CustomerOperations(); komutunu ekledikten sonra ekle butonuna gelerek ilgili kodlarımızı yazıyoruz. Buradan var türünde bir tane customer değişkeni oluşturup new Customer dedikten sonra süslü parantezlerin içine tek tek hangi değerler varsa ilgili textbox'a atama yapıyoruz. En sonunda global alanda oluşturduğumuz customerOperations üzerinden AddCustomer metodunu çağırarak customer'i ekliyoruz.

![image](https://github.com/user-attachments/assets/ce780359-dcac-40d4-bfac-35aba89b3256)

Ekleme işlemi bu şekildedir.

![image](https://github.com/user-attachments/assets/ce6238a6-c5d6-4c9c-b4f5-823e1a9b45c7)

MongoDb'ye giderek sol tarafta yer alan localhost:27017'nin yanında üç noktaya tıklayıp Refresh databases diyoruz.

![image](https://github.com/user-attachments/assets/6fa1387e-8275-43a2-a1a0-89236e304e97)

![image](https://github.com/user-attachments/assets/f35cab9a-a20b-469e-b2df-8ee25a51ea19)

Veri tabanımız artık hazır. İçerisine geldiğimiz zaman Customers tablosu çıkacaktır. Tabloya bastıktan sonra verimiz bu şekilde gelecektir.

✅ Bu eğitimde MongoDb'nin kurulumunu, veri tabanını bağlamayı ve oluşturmayı, MongoDb ile veri eklemeyi öğrendim ve uyguladım.


## 🖥️ C# Eğitim Kampı Ders 25 - C# ile MongoDb Kullanımı 2
### 📆 Tarih: 28 Aralık 2024

CustomerOperations sınıfından devam ediyoruz.

![image](https://github.com/user-attachments/assets/e262a33e-2880-429a-a5bb-080b1d602f7c)

Burada müşterileri listelemek için GetAllCustomer adında yeni bir metot tanımlıyoruz. İlk olarak connection isminde bir değişken oluşturup MongoDbConnection ile veri tabanına erişim sağlıyoruz. Sonra customersCollection isminde bir değişken oluşturup connection'dan sonra GetCustomersCollection diyerek tabloya erişim sağlıyoruz. Daha sonra customers adında bir değişken oluşturup Find metodunu kullanarak listeleme işlemi yapıyoruz ve bu listeleme işlemini BsonDocument kullanarak yapıyoruz. Listeleme işlemi için List kullanarak entity'e ait olan Customer'ı ekliyoruz ve foreach döngüsünü kullanıyoruz. Döngüyü kullandıktan sonra her bir sütunu tek tek ekliyoruz ve en sonunda return ile işlemimizi tamamlıyoruz.

![image](https://github.com/user-attachments/assets/82a57161-5e9e-4ca2-9e89-535b7c137970)

Formumuza giderek bu kez Listele butonuna tıklıyoruz ve ilgili kodlarımızı yazıyoruz.

![image](https://github.com/user-attachments/assets/57053fea-f29e-4504-abed-4bd8de33ca0b)

Listele butonuna tıkladığımız zaman verileri gösterecektir.

![image](https://github.com/user-attachments/assets/2059e130-9a10-4439-b878-2d26506a5ee2)

Tekrardan CustomerOperations sınıfına gelip bu kez silme işlemi uyguluyoruz. İlk iki satır diğer metotlarda da olduğu gibi verilere bağlanmayı ve tabloya erişimi sağlıyoruz. Daha sonra filter adında bir değişken oluşturup Builders adında bir komut ekleyip BsonDocument'i ekliyoruz, burada Filter ve Eq komutlarını kullanarak veriyi id'ye göre bulma işlemi uyguluyoruz. Silmek için ise MongoDb'ye ait olan DeleteOne komutunu kullanıyoruz.

![image](https://github.com/user-attachments/assets/eab3ce89-73ec-47a2-ae2c-62c1eb918e72)

Burada silme işleminde de olduğu gibi filter değişkenini kullanarak id'yi buluyoruz. İlgili id'yi bulduktan sonra güncellemek için updatedValue isminde bir değişken oluşturup Builders dedikten sonra BsonDocument ile Update komutunu kullanıyoruz. Güncellemek için Set isminde bir komut kullanıp tek tek atamalar yaparak güncelleme işlemini yapıyoruz. En son kısımda ise UpdateOne komutunu kullanarak güncelleme işlemi yapıyoruz.

![image](https://github.com/user-attachments/assets/ed12ba50-7ab4-4937-a931-f2d82278ac2c)

ID'ye göre getirme işlemi için önce bağlantıyı oluşturup sonra koleksiyona bağlanıyoruz. Koleksiyona bağlandıktan sonra ID'ye göre filtreleme yapıyoruz. Sonrasında tek bir veri getireceğimiz için FirstOrDefault komutunu kullanıyoruz. Return işlemi için ise new Customer dedikten sonra tek tek atamalarımızı yapıyoruz.

CRUD işlemleri tamamlandıktan sonra tekrar Form'a geliyoruz ve Sil butonuna tıklıyoruz.

![image](https://github.com/user-attachments/assets/0f1ef32a-fdc9-4680-a398-7dacd7226759)

Silme işlemi için string türünde bir tane customerID değişkeni oluşturup ilgili textbox'a atama yaptık. Ardından customerOperations değişkeni ile DeleteCustomer metodunu buraya çağırıp id'ye göre silme işlemi oluşturduk.

![image](https://github.com/user-attachments/assets/24077ced-d6a6-4eee-91d3-8302b1af3fb8)

Programımızı çalıştırdığımız zaman burada yer alan ID'yi kopyalayıp ilgili textbox'a yapıştırıyoruz ve Sil butonuna tıkladıktan sonra ilgili veri silinecektir.

![image](https://github.com/user-attachments/assets/17504f6f-4b81-46fc-a282-08cbbdfe3cfc)

Güncelleme işlemi için string türünde bir tane id değişkeni oluşturup ilgili textbox'a atama yaptık. Ardından var türünden updateCustomer adında bir değişken oluşturup new Customer dedikten sonra tek tek atamaları yapıyoruz. Ardından customerOperations değişkeni ile UpdateCustomer metodunu buraya çağırıp id'ye göre güncelleme işlemi oluşturduk.

![image](https://github.com/user-attachments/assets/363595f2-f23d-4436-bcef-c96a2a878d2e)

ID'yi ilgili textbox'a ekledikten sonra güncelleyeceğimiz verileri giriyoruz ve Güncelle butonuna bastıktan sonra ilgili veriler güncellenecektir.

![image](https://github.com/user-attachments/assets/ba26fdac-3bf0-4561-8ec4-e5075c2abcf7)

ID'ye Göre Getir adında yeni bir buton daha ekledik.

![image](https://github.com/user-attachments/assets/2f8f16d2-2936-4fd8-a345-a6bcbd610c29)

Buradan string türünde bir id değişkeni oluşturup ilgili textbox'a atadık. Ardından Customer sınıfından bir tane customers oluşturup GetCustomerByID metoduna atadık. Ardından datagridview'de göstermiş olduk.

✅ Bu eğitimde C# ve MongoDb ile CRUD işlemlerinin nasıl yapıldığını öğrendim ve uyguladım.
