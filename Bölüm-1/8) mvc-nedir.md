# MVC (Model View Controller) Nedir?
<p>
MVC, birbirinden bağımsız üç katmanı esas alan mimarisel bir desen (Architectural Pattern)'dir. Kimi kaynaklarda tasarım desenidir diye de geçmektedir. Ancak aslında bir tasarım deseninden daha fazlasıdır.
</p>
<p>
Çünkü design dediğimiz tasarım desenleri belirli senaryolara uygun yerleştirilip kullanılırken mimarisel desenler ise genel yaklaşımımızı belirlerler.
</p>
<p>
Örneğin, bağımsızlık senaryolarında dependency injection desenini kullanırız. Bu bir mimari değildir, bunun üzerine bir mimari geliştirmeyiz. Bu tasarım deseni ilgili senaryo ihtiyacında kullanılır.
</p>
<p>
Ancak mimarisel desen, tasarım deseninden daha geniş kapsamlı olduğu için içinde bir veya birden fazla tasarım deseni barındırabilen desenlerdir.
</p>
<br>
<p>
Mvc; özünde observer, decorator gibi design pattern'ları kullanan mimarisel bir desendir.  
</p>
<p>
Microsoft, bu desen üzerine oturtulmuş Asp .Net Core Mvc mimarisini geliştirmiştir.
</p>
<br>

<h2>Model katmanı</h2>
<p>
Model katmanı, işlenecek olan veriyi temsil eden katmandır. Genellikle veri tabanı işlemlerinin yapıldığı katmandır. (Örn. Entity Framework Core, Entity Modals, Ado .Net, Repository, veri tabanı işlemleri...)
</p>
<p>
Yani veri, mvc'de ayrı bir katmanda işlenen, ayrı bir katman olarak nitelendirilen bir değer, bir olgudur. 
</p>
<br>

<h2>View katmanı</h2>
<p>
İstek neticesinde elde edilen verileri görselleştirecek, görsel çıktısını verecek katmandır. (Örn. html, css, javascript, razor, resim, müzik, video)
</p>
<br>

<h2>Controller katmanı</h2>
<p>
Gelen request'leri karşılayacak olan ve request'in içeriğine göre gerekli model işlemlerini üstlenecek olan katmandır. 
</p>
<p>
Algoritmaları, servisleri, veri tabanını vs. çağırarak / çalıştırarak/ sorgulayarak istenilen veriyi üretmekten ve ihtiyaç dahilinde üretilen bu veriyi view ile görselleştirmekten sorumludur. 
</p>
<p>
İstek neticesinde elde edilen ve işlenen veriyi tekrar client'a response olarak döndürülür.
</p>
<p>
Controller, veriyi üretmekten sorumludur.
</p>
<br><br>

<h2>MVC Çalışma Mantığı</h2>
<p>
User, client üzerinden bir istekte bulunuyor ve isteği karşılayan controller isteğin mahiyetine bakıyor. 
</p>
<p>
Bu istekte, bir veri tabanı ihtiyacı varsa ya da veriler dış kaynaktan alınacaksa ya da bir model kullanılacaksa istek model'a yönlendiriliyor. Yani model'dan bu istenilen verinin üretilmesi isteniyor ve model'da bu verileri üreterek controller'a gönderiyor. 
</p>
<p>
Şimdi veriler controller'da. Eğer bu veriler üzerinde belirli bir görsellik işlemi yapılacaksa veri, view katmanına gönderiliyor. Ve tekrardan bu işlenilen / render edilen veriler controller'a gönderiliyor. En sonunda da elde edilen bu sonuçlar controller'dan client'a gönderiliyor.
</p>
<br><br>

<h2>Peki Asp .Net Core MVC'de bir request nasıl işleniyor?</h2>
<br>
<img src="img/pipeline.png">
<br><br>

<p>
Gönderdiğimiz isteği kestrel sunucumuz karşılayacak ve middleware yapıları devreye girecek. Daha sonra routing katmanına gelinecek.  
</p>
<p>
Routing aşamasında, request'in hangi endpoint'i yani hangi isteği yaptığını yüzlerce controller'ın / istek alanının arasından bulacak ve o endpoint'e yönlendirecek.
</p>
<p>
Bundan sonra ilgili controller ayağa kaldırılıp bu controller'ın içerisindeki action method'lardan, isteği karşılayabilecek olan method çalıştırılacak. 
</p>
<p>
Ardından bu üretilen sonuç ya direkt client'a gönderilecek ya da view'e gönderilip render edildikten sonra elde edilen sonuç client'a gönderilecek. 
</p>


