# MVC Proje Altyapısı Oluşturmak ve Temel Konfigürasyonları Sağlamak

<p>
Asp .net uygulamasında, Mvc mimarisini kullanabilmek için uygulamaya mvc'yi servis olarak eklememiz gerekmektedir.
</p>
<img src="img/controllers.png">
<p>
Program.cs dosyasındaki Services property'si üzerinden servisimizi yani mvc mimarimizi uygulamaya ekliyoruz. 
</p>
<p>
Mvc mimarisini ekleyebilmemiz için AddControllers() metodunu ya da AddControllersWithViews() metodunu çağırmamız gerekiyor.
</p>
<p>
Eğer ki mvc'de istekleri alan controller'ı kullanacaksak AddControllers() metodunun ekli olması gerekiyor. 
</p>
<p>
Yok eğer view katmanını da kullanacaksak o zaman AddControllersWithViews() metodunu eklememiz gerekiyor.
</p>
<br><br>


<img src="img/routingandendpoints.png">
<p>
UseRouting() metodu: Gelen isteğin, hangi controller'ın metodunu çağıracağı bu metotla belirliyor. Yani gelen isteğin rotasını bu middleware belirliyor.
</p>

<p>
UseEndpoints() metodu: Yapmış olduğumuz isteğin ta kendisidir. İstek yapılacak adresi temsil eder.
</p>
<p>
Bu uygulamaya gelen isteklerin hangi rotalar / şablonlar eşliğinde gelebileceğini endpoints'den bildireceğiz.
</p><br><br>


<img src="img/controller.png">
<p>
Controller'lar özlerinde bir class'tırlar. Ve bir class'ın request karşılayabilir fıtrata sahip olabilmesi için Controller sınıfından kalıtım alması gerekir. 
</p>
<p>
Action Method: Controller sınıfları içerisinde istekleri karşılayan metotlara action metot denir.
</p>
<p>
Bir controller'ın içerisinde (erişim belirleyicisi fark etmeksizin) herhangi bir metot oluşturduğumuzda bu metotların hepsi birer action metodudur. 
</p>
<p>
Örneğin HomeController sınıfının içerisindeki Index() metodu bir action metodudur. Sebebi ise geri dönüş tipinin IActionResult olması değildir. Bu sınıf Controller sınıfından türetildiği için içerisindeki bütün metotlar action metodu olarak kabul edilecektir.
</p>
<p>
Eğer Controller sınıfından türetilmeseydi o zaman normal bir metot görevi görecekti, action metot olmayacaktı.
</p><br><br>


<img src="img/getproducts.png">
<p>
Bir metodun view'ini oluşturmak için Views klasörünü kullanmalıyız.
</p>
<p>
Bir controller'a ait view'lerin hepsi, ilgili controller isminin altında bulunması gerekiyor. Örneğin ProductController'a ait bütün view'ler, Product klasörünün altında olması gerekiyor.
</p>
<p>
Mesela ProductController içerisindeki GetProducts() action'ının view'i, action ismiyle aynı olmalıdır.
</p>
<p>
View dosyaları .cshtml uzantılı dosyalardır. 
</p>
<p>
c sharp + html = .cshtml ==>  Bu formata Razor teknolojisi denir.
</p>
<p>
Razor teknolojisi, asp .net veya asp .net core mvc mimarisinde view'i kodlayabilmek, view'da hızlı bir şekilde UI tabanlı çalışmalar gerçekleştirebilmek için geliştirilmiş bir teknolojidir. 
</p>
<p>
Html içerisinde c# kodlarını yazmamızı sağlayan bir teknolojidir. 
</p><br><br>


<img src="img/viewfonk.png">
<p>
View fonksiyonu, bu action'a ait view (.cshtml) dosyasını tetikleyecek olan fonksiyondur.
</p><br><br>


<img src="img/anotherview.png">
<p>
Eğer ilgili action ismiyle birebir aynı olan view'i tetiklemek istemiyorsak View() overload'u olan metodu kullanarak belirtilen view ismindeki dosyayı render edebiliriz. 
</p><br><br>


<img src="img/models.png">
<p>
Models klasörünün içinde Context'imiz olur (entity framework'deki), entity'lerimiz olur yani veri tabanı ile ilgili işlemler burada yapılır.
</p>
<p>
Bir veri tabanı sorgusu yazmak istiyorsak ya da bir entity'e ihtiyacımız varsa bu işleme "Models'a gitmek" denir.
</p>
