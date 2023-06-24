# Action Türleri

## ViewResult
<p>
Response olarak bir view dosyasını (.cshtml) render etmemizi sağlayan action türüdür.
</p>
<img src="img/viewresult.png">
<br><br>


## PartialViewResult
<p>
Yine bir view dosyasını (.cshtml) render etmemizi sağlayan action türüdür.
</p>
<p>
ViewResult'tan temel farkı, client tabanlı yapılan Ajax isteklerinde kullanıma yatkın olmasıdır.   
</p>
<p>
Yani client'tan yapılan istek client tabanlı değilse ViewResult kullanılır. Yok eğer client tabanlıysa, ajax teknolojisiyle bu işlem gerçekleştiriliyorsa PartialViewResult kullanılır.
</p>
<p>
Bunu şu şekilde tahayyül edebiliriz: Web sayfasının genelini bize oluşturan ViewResult'tur. Ancak web sayfasındaki belirli bir noktayı, parçayı oluşturacak olan PartialViewResult'tur.
</p>
<p>
Aralarındaki teknik fark ise ViewResult, _ViewStart.cshtml dosyasını baz alır. Lakin PartialViewResult ilgili dosyayı baz almadan render eder.
</p>
<p>
Yani ViewResult genel sayfayı render ederken PartialViewResult genel sayfayı değil belirli bir alanı render edip onun çıktısını o alanda kullanır. 
</p>
<img src="img/partialview.png">
<br><br>


## JsonResult 
<p>
Üretilen datayı json türüne dönüştürüp döndüren bir action türüdür. Genellikle ajax tabanlı işlemlerde kullanılır.
</p>
<img src="img/jsonresult.png">
<br><br>


## EmptyResult
<p>
Bazen gelen istekler neticesinde herhangi bir şey döndürmek istemeyebiliriz. Böyle bir durumda EmptyResult action türünü kullanabiliriz.
</p>
<p>
Ancak bunu cevapsız gibi düşünmeyelim. Bir response dönderiliyor ancak result'ı yok, adı üzerinde boş result.
</p>
<img src="img/emptyresult.png">
<br><br>


## ContentResult    
<p>
İstek neticesinde cevap olarak metinsel bir değer döndermemizi sağlayan action türüdür. Genellikle ajax tabanlı işlemlerde kullanılır.
</p>
<img src="img/contentresult.png">
<br><br>


## ViewComponentResult
<p>
İsteğe cevap olarak bir ViewComponent render etmemizi sağlayan action türüdür.
</p>
<br>


## ActionResult
<p>
Bütün result türlerinin atasıdır. Tüm action türlerini karşılayan ana türdür.
</p>
<p>
Gelen bir istek neticesinde geriye döndürülecek action türlerinin değişkenlik gösterebildiği durumlarda kullanılan bir action türüdür. 
</p>
<p>
Örneğin istek geldi ve bu istek üzerinde if'lerle switch'lerle kontrol yapıyoruz. Yapmış olduğumuz kontrol neticesinde geriye json döndürmemiz gerekebilir, content döndürmemiz gerekebilir, partial döndürmemiz gerekebilir... İşte bu geri dönüşlerin hepsini tek bir fonksiyonda döndürebilmemiz için bunların ortak bir türe ihtiyacı vardır. O türde ActionResult türü olacaktır.  
</p>
<p>
Yani ActionResult ortak bir tür sağlamış oluyor.
</p>
<img src="img/actionresult.png">
<br><br>


## IActionResult
<p>
IActionResult, ActionResult'ın bir arayüzüdür. IActionResult'ıyla da bütün action'ları karşılayabiliriz.  
</p>