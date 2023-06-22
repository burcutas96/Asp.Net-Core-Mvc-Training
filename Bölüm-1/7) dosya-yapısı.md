# Asp .NET Core 5.0 Dosya Yapısı
<p>
Asp .net core esasında bir console uygulamasıdır. 
</p>
<p>
Asp .net core kendi dahilinde / fıtratında bir sunucu (Kestrel) barındırır. İşte bu sunucuyu ayağa kaldırdığı nokta Program.cs dosyasıdır.
</p>
<img src = "img/program_cs.png">

<br>
<br>
<p>
Program.cs içerisinde, ayağa kaldırılacak olan host'un kullanacağı konfigürasyonları nereden alacağını bildirir. 
</p>
<p>
Asp .net core 5.0 sürümünde Startup.cs dosyası kullanılıyor ancak .net 6 sürümünden itibaren Startup.cs dosyası, Program.cs dosyasıyla birleştirilmiştir. Bu yüzden .net 6 sürümü ve sonraki sürümlerde Startup.cs dosyası ile karşılaşmıyoruz. 
</p>

<p>
Startup.cs sınıfı, temel konfigürasyon sınıfıdır.
</p>

<img src = "img/startup_cs.png">

<br>
<br>
<p>
ConfigureServices() metodu, uygulamada kullanılacak servislerin eklendiği / konfigüre edildiği metottur.
</p>
<p>
- Servis nedir? 
</p>
<p>
Belirli işlere odaklanmış ve o işin sorumluluğunu üstlenmiş kütüphanler / sınıflardır.
</p>
<p>
Servis, modül, kütüphane bunlar aynı anlamlara gelmektedir.
</p>
<p>
Configure() metoduyla uygulamada kullanılacak olan middleware'ları / ara katmanları / ara yazılımları çağırmaktayız.
</p>

<p>
appsettings.json Dosyası: Uygulamada belirli static değerleri tuttuğumuz bir konfigürasyon dosyasıdır.
</p>

<img src = "img/appsettings.png">
<br>
<br>
<p>
Bazen yazılımlarımızda, uygulamanın her yerinde kullanmak isteyeceğimiz metinsel değerler olabilir. (Örn. veri tabanı bağlantı stringi)
</p>
<p>
Yazılımlarda kullanılması gereken static olan metinsel değerler kodun içerisine yerleştirilmez. Çünkü günün birinde bu değerin değiştirilmesi gerektiğinde kodun yer yerinde düzeltme yapılması gerekecektir. 
</p>

<p>
- Dependencies nedir? 
</p>
<p>
Uygulamada kullandığımız harici ve dahili kütüphanelerdir. 
</p>

<p>
Bir uygulamayı kestrel'de ya da IIS'de ayağa kaldırabiliriz
</p>

<img src = "img/kestrel.png">
<br>
<br>
<p>
Görseldeki açılan seçeneklerde projenin ismiyle aynı olan seçenek kestrel'dir. 
</p>


