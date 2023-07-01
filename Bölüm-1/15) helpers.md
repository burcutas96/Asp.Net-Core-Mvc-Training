# Helpers
<p>
Helpers yapılanmaları, yardımcı metotlardır. Üç tane helper fonksiyonu vardır: UrlHelper, HtmlHelper, TagHelper.
</p>
<br><br>

## 1- UrlHelper 
<p>
Asp .Net Core Mvc uygulamalarında url oluşturmak için yardımcı metotlar içeren ve o anki url'e dair bizlere bilgi veren bir sınıftır.
</p>

### UrlHelper Metotları
* <p>Action</p>
* <p>ActionLink</p>
* <p>Content</p>
* <p>RouteUrl</p>

### UrlHelper Property'leri
* <p>ActionContext</p>
<br>


### A- Action Metodu
<p>
Verilen controller ve action'a ait bir url oluşturmayı sağlayan metottur. Yani bir link oluşturacaksak eğer bu linki manuel'de oluşturabiliriz UrlHelper'ı kullanarak da oluşturabiliriz.
</p>
<img src="img/urlhelper.png">
<br><br>


### B- ActionLink Metodu
<p>
Verilen controller ve action'a ait bir url oluşturmayı sağlayan metottur. Action metotla aralarında çok fazla bir değişiklik yoktur. Aralarındaki tek fark; oluşturulan url'de temel host bilgisi, protokolü ve port bilgisini barındırılır.     
</p>
<img src="img/urlhelper1.png">
<br><br>


### C- Content Metodu
<p>
Genellikle css ve javascript gibi dosya dizinlerini programatik olarak tarif etmek için kullanırız. 
</p>
<img src="img/urlhelper2.png">
<p style="margin-top: 15px">
Bu metot çokta önemli değil. Önemli olmamasının sebebi ise; UseStaticFiles middleware ile gelen static dosya yapılanması bu metodun işlevselliğini daha efektif üstlenmektedir. 
</p>
<br>


### D- RouteUrl Metodu
<p>
Mimaride tanımlı olan Route isimlerine uygun bir şekilde url oluşturan bir metottur.
</p>
<img src="img/routeurl.png">
<br><br>


### E- ActionContext Property
<p>
O anki url'e dair tüm bilgilere erişmemizi sağlayan bir property'dir.
</p>
<img src="img/actioncontext.png">
<br><br><br>


## 2- HtmlHelper 
<p>
Html etiketlerini server tabanlı oluşturmamızı sağlayan yardımcı metotları barındırmaktadır.
</p>

<p>
Hedeflenen .cshtml dosyalarını render etmemizi sağlamaktadır.
</p>

<p>
O anki context'e dair bilgi edinmemizi sağlamaktadır. 
</p>

<p>
Veri taşıma kontrollerine erişmemizi sağlamaktadır.
</p>

### HtmlHelper Metotları
* <p>Html.Partial</p>
* <p>Html.RenderPartial</p>
* <p>Html.ActionLink</p>
* <p>Html Form Metotları</p>

### HtmlHelper Property'leri
* <p>ViewContext</p>
* <p>TempData</p>
* <p>ViewData</p>
* <p>ViewBag</p>
<br>


### A- Html.Partial Metodu
<p>
Hedef view'i render etmemizi sağlayan bir fonksiyondur.
</p>
<p>
Yani herhangi bir view'in içerisinde Html.Partial ile başka bir view'i render edebiliyoruz.
</p>
<p>
Örneğin; ProductController'ın içerisindeki GetProducts() action'ının view'inde başka bir view olan ListPartial.cshtml view'ini çağırabiliyoruz.
</p>
<img src="img/htmlpartial.png">
<img src="img/htmlpartial1.png">
<br>
<hr>
<p>
Eğer ki en sondaki view'in (mesela bu örnekte ListPartial.cshtml'in) bir data'ya ihtiyacı varsa, bu data'yı controller ile vermemiz gerekiyor.
</p>
<p>
Data, ilk öncelikle ilgili action'ın view'ine gönderilir daha sonra bu view'in tetiklediği hedef view'e gönderilir.  
</p>
<img src="img/htmlpartial2.png">
<br><br>

#### Kritik
<p>
Eğer ki GetProducts() view'ine User nesnesini model bazlı gönderirsem ListPartial view'inde de bu model'ı kullanabilirim. Bu zaten normal şartlardaki durumdur. Ancak ben ListPartial'da User nesnesini değil de başka bir nesneyi örneğin Product nesnesini kullanmak istiyorsam Html.Partial metodunun overload'unu kullanmalıyım.
</p>
<p>
Yani GetProducts view'inde User nesnesini, ListPartial view'inde ise Product nesnesi gibi farklı nesneleri kullanmak istiyorsam bunun için Html.Partial'da küçük bir değişiklik yapmalıyım.
</p>
<img src="img/htmlpartial3.png">
<br><br>


### B- Html.RenderPartial Metodu
<p>
Hedef view'i render etmemizi sağlayan bir fonksiyondur.
</p>
<p>
Bu metodun Html.Partial'dan farkı; 
</p>
<p>
Html.Partial'da hedef view'i direkt razor operatörüyle bildirirken Html.RenderPartial'da razor operatöründen sonra süslü parantezleri de kullanmalıyız.
</p>
<p>
Html.Partial'da hedef view'i şu şekilde bildirirken:
</p>
<img src="img/htmlpartial4.png">
<br><br>
<p>
Html.RenderPartial'da bu şekilde bildiririz:
</p>
<img src="img/htmlrenderpartial.png">
<br><br>
<p>
Bu şekilde farklı bildirmemizin sebebi; partial geriye string döndürürken RenderPartial void döndürür. Bu yüzden bunu tetikleyebilmemiz için scope içerisinde c# kurallarıyla tetiklememiz gerekiyor.
</p>
<p>
İşlevsel olarak yani sonuç olarak bişey fark etmiyor. İkisinde de aynı sonucu alıyoruz. 
</p>
<p>
Ancak teknik olarak şöyle bir fark vardır;
</p>
<p>
Html.RenderPartial sayfanın TextWriter'ını kullandığı için (yani http response'u server'a yazdığı için) Html.Partial'a nazaran daha hızlı render işlemini yürütür. Dolayısıyla Html.RenderPartial daha performanslıdır.
</p>
<br>


### C- Html.ActionLink Metodu
<p>
Link oluşturur. Url.ActionLink'le birebir aynı amaca hizmet eder. Aralarındaki tek fark Html.ActionLink'de oluşturulan linki a tagında oluşturur. Çünkü bu Html Helper olduğu için bize html çıktısını verir.
</p>
<br>


### D- Html Form Metotları
<p>
Kullanıcıyla etkileşime girmemizi ve form ve input nesneleri oluşturmamızı sağlayan metotlardır. 
</p>

* <p>Html.BeginForm</p> 
* <p>Html.CheckBox</p> 
* <p>Html.TextBox</p> 
* <p>Html.Display</p> 
* <p>Html.Password</p> 
* <p>Html.Textarea</p> 
* <p>Html.ValidationMessage</p> 






