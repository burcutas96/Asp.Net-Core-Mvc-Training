# View Yapılanması

## View Nedir?
<p>
View; controller'da üretilen verinin js, css ve bunun gibi UI teknolojilerinin kullanılarak görselleştirildiği, render edildiği bir katmandır. 
</p>
<p>
C#'ı kullanarak UI tabanlı çalışmamızı sağlayan yani html içerisinde c# kodlarını yazmamızı sağlayan asıl teknoloji razor teknolojisidir. Microsoft tarafından geliştirilmiştir.   
</p>
<p>
View, uzantısı .cshtml olan bir dosyadır. Ve bu dosya her ne kadar web'de çalışıyor olsakta web terminolojisinde evrensel bir yapılanma değildir. 
</p>
<p>
Bunu örnek vererek açıklayacak olursak; html web terminolojisinde evrenseldir. Css evrenseldir. Js evrenseldir. Yani biz bunları  herhangi bir platformda kullanabiliriz. Ancak .cshtml evrensel değildir. Sadece asp .net core'a aittir, asp .net core'da çalışır. 
</p>
<p>
View dosyalarını render ettikten sonra c# kodlarını göremeyiz. Çıktı olarak sadece html verecektir.    
</p>
<br>


## Views Klasörü
<p>
Bir projede view dosyaları genellikle Views klasörü altında bulunurlar.
</p>
<p>
Neden genellikle burada bulunurlar peki? Çünkü asp .net core mimarisinde mvc'de action'lar, karşılıkları olan view dosyalarını belirli bir format üzerinden bulmaktadır. 
</p>
<p>
Yani view klasörünün altında, controller isminde bir klasör vardır. Ve onun altında da action isimlerine karşılık gelen .cshtml uzantılı dosyalar ilgili action'ın view dosyası olarak direkt, default olarak kabul edilirler. Mimari bu şekilde çalışmaktadır.
</p>
<p>
Bu yüzden view'lerimizin Views klasörü altında olması gerekiyor. Ancak bu şart değildir. Views klasörü dışında başka bir isimle klasörümüzü isimlendirip varsayılanın dışına çıkabiliriz ama bu geleneği, standartı yine de bozmamalıyız. 
</p>
<br>

## Controllers - Views Veri Taşıma
<p>
Controller'dan View'e 4 farklı şekilde veri gönderebiliriz. Bu dört farklı şeklin biri model bazlı veri göndermekken diğer üçü veri taşıma kontrolleri ile veri göndermektir. 
</p>
<p>
Model bazlı veri göndermeyle beraber biz ekstradan kullanıcıdan veri alabilirken veri taşıma kontrolleri ile sadece controllerdan view'e veri gönderme operasyonlarını gerçekleştirebiliyoruz.
</p>
<br>

* ### Model Bazlı Veri Gönderimi
<p>
Eğer bir veriyi view'e model bazlı göndereceksek View fonksiyonunun model overload'ını kullanmamız gerekmektedir.
</p>
<img src="img/modelcontroller.png">
<p>
View() fonksiyonuyla model'ı yani verimizi view'e gönderiyoruz.
</p>
<p>
Ve view'de bu gelen veriyi şu şekilde kontrol ediyoruz: 
</p>
<p>
1- İlk öncelikle object türünde gelen verinin türünü <strong>@model</strong> keyword'ü ile belirliyoruz. 
</p>
<p>
2- Gelecek olan data'yı kullanabilmek için de <strong>@Model</strong> keyword'ünü kullanıyoruz. Bu keyword, @model ile bildirilen türe bürünüyor ve o türdeki data'yı yakalıyor.  
</p>
<img src="img/modelview.png">
<p>
>> Resimde altı çizili olarak belirtilen <strong>@</strong> keyword'ünü c# kodlarını yazabilmek için kullanıyoruz!
</p>
<br>


* ### Veri Taşıma Kontrolleri

<h4 style="margin-top:30px">
1- ViewBag 
</h4>
<p>
View'e gönderilecek / taşınacak data'yı dynamic şekilde tanımlanan bir değişkenle göndermemizi sağlayan bir veri taşıma kontrolüdür. 
</p>
<p>
Dynamic türünde olan ViewBag property'si ile data'yı view katmanına göndeririz.
</p>
<p style="margin-bottom:15px">
Ve resimde altı çizili olan ifade bir değişkendir. Bu değişkene products listemizi atadık. 
</p>
<p>
View() fonksiyonu veriyi, ViewBag.products değişkeniyle view'e gönderecektir.
</p>
<img src="img/viewbag.png">
<p style="margin:15px 0">
Controllers'dan gelen ViewBag.products değişkenini yine aynı konseptle view'de karşılıyoruz.
</p>
<img src="img/viewbag-view.png">
<p style="margin-top:15px">
Ancak ViewBag.products değişkeni dynamic türünde olduğu için derleme aşamasında verinin türü bilinmez. 
</p>
<p>
Bu sebepten ötürü de biz derleme aşamasında veri üzerinde işlem yapabilmek / verinin elemanlarına ulaşabilmek için as veya cast operatörü ile verinin türünü bildirmiş oluruz. 
</p>
<p>
Eğer verinin türünü bildirmezsek derleme aşamasında elemanlara ulaşamazken;
</p>
<img src="img/viewbag-view1.png">
<p style="margin:15px 0">
Türü bildirdiğimizde verinin elemanlarına ulaşabiliriz;
</p>
<img src="img/viewbag-view2.png">
<p>
Yani burda tür bildirme işlemi opsiyonel bir şeydir. Eğer elemanlara ulaşmak istiyorsak as veya cast operatörlerinden birini kullanmamız gerekirken elemanlara ulaşmak istemiyorsak bu operatörleri kullanarak tür bildirimi yapmamıza gerek yoktur.
</p><br>


<h4 style="margin-top:30px">
2- ViewData
</h4>
<p>
ViewBag'de olduğu gibi action'daki datayı view'e taşımamızı sağlayan bir kontroldür. 
</p>
<p>
Peki ViewBag ile ViewData arasındaki fark nedir?
</p>
<p>
ViewBag, ilgili data'yı dynamic ile view katmanına taşırken; ViewData, ilgili data'yı boxing ederek view'e  taşır.
</p>
<p>
Dolayısıyla ViewData ile gönderdiğimiz veriyi view'de kullanabilmek için unboxing etmeliyiz. 
</p>
<p>
ViewData'da ViewBag gibi çalışmaktadır. View() fonksiyonuyla veriyi, object türündeki ViewData property'si ile göndeririz.
</p>
<img src="img/viewdata.png">
<p style="margin:15px 0">
Ancak view katmanına gönderilen boxing edilmiş veriyi kullanabilmek için as veya cast operatörleriyle unboxing etmek zorundayız. 
</p>
<img src="img/viewdata-view.png">
<br><br>


<h4 style="margin-top:30px">
3- TempData
</h4>
<p>
TempData'da, ViewData'da olduğu gibi action'daki veriyi boxing'e tabi tutarak view'e göndermemizi sağlar.
</p>
<p>
Dolayısıyla TempData'da da gönderdiğimiz veriyi view'de kullanabilmek için unboxing etmeliyiz.
</p>
<p>
Peki TempData ile ViewData arasındaki fark nedir?
</p>
<p>
Biz, action'ları kendi aralarında yönlendirebiliyoruz. Örneğin; bir action'ın operasyonu bittikten sonra kullanıcıya herhangi bir response göndermeden önce başka bir action'a yönlendirme yapabiliyoruz. O action'daki operasyonların da gerçekleştirilmesini sağlayabiliyoruz. 
</p>
<p>
Böyle bir durumda, farklı bir action'a yönlendirme söz konusu olduğunda ViewBag veya ViewData ile diğer action'a veri taşıyamazken TempData ile veri taşıyabiliriz. 
</p>
<p>
Çünkü TempData arkaplanda bir cookie kullanıyor ve bu cookie sayesinde TempData ilgili veriyi hedef action'a taşıyabiliyor. 
</p>
<p style="margin-bottom:20px">
Bu yüzden yönlendirme yaptığımız zamanlarda bir action'da elde edilen data'yı farklı bir action'a göndermek istiyorsak burada TempData'yı kullanmamız gerekir. Aksi taktirde diğer veri taşıma kontrolleri ile action'lar arasında veri taşıyamayız.
</p>
<img src="img/tempdata.png">
<p style="margin:15px 0">
RedirectToAction() metoduyla hangi action'a yönlendirme yapacağımızı bildirmiş oluyoruz. Eğer bu controller'ın dışında başka bir controller'ın içerisindeki action metoda yönlendirme yapmak istiyorsak yine bu metodun overload'unu kullanabiliriz. 
</p>
<img src="img/tempdata-view.png">
<p style="margin-top:15px">
Get() action'ından gönderilen veriyi Update() action'ında bu şekilde kullanabiliriz.
</p>
<br>
<p>
TempData, cookie değeri üzerinden veriyi taşıyor. Haliyle cookie'ye ilgili verinin dönüştürülmesi yani serilize edilmesi  gerekir. Basit türleri serilize etmede bir sıkıntı yok ancak komplex type'da çalışıyorsak komplex type'ı serilize etmek ekstradan bir maliyet olduğu için uygulama hata verecektir.
</p>
<img src="img/tempdata-view1.png">
<p style="margin-top:15px">
TempData'da bu şekilde kompleks bir data kullanırsak veri serilize edilemediği için çalışma zamanında hata alırız.
</p>
<p>
Bu hatanın önüne geçebilmek için veriyi serilize ederek göndermemiz gerekecektir. Bunun içinde JsonSerializer adındaki kütüphaneyi kullanmalıyız. 
</p>
<img src="img/tempdata-view2.png">
<p style="margin-top:15px">
Serilize ettiğimiz data'yı string türünde elde ediyoruz. Ve bu elde ettiğimiz data'yı TempData ile diğer action'a gönderiyoruz.
</p>
<p>
Daha sonrasında Update() metoduna gelen veriyi kullanabilmek için deserilize etmemiz gerekmektedir. Ancak veri TempData tarafından boxing edilerek gönderildiği için ve deserilize etme işleminde data'yı string formatta kullanmamız gerektiği için öncelikle bu datayı string'e dönüştürüyoruz sonrasında deserilize ediyoruz.
</p>

