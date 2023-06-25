# Controller Attribute'ları 

<p>
Controller'ın temel, yegane amacı; sadece request'leri karşılamaktır.
</p>
<p>
Yani controller dediğimiz sınıf kendi içerisinde bir iş mantığı, algoritma yürütmemelidir.  
</p>
<p>
Sadece request'i karşılamalı ve bu request'in gereği olan algoritmaları, servisleri tetiklemelidir. 
</p>
<p>
Controller, işin komutanıdır. İşi yapanı değildir. İş mantığının; başka yerlerde, başka servislerde, başka sınıflarda tanımlanmış olması gerekiyor.
</p>
<p>
Örneğin; hepsiburada.com'a ayın kampanyalı ürünlerini getirmesi için bir istekte bulundunuz. Controller, ilgili isteği karşılar ancak bu istek neticesinde ayın kampanyalı ürünlerini getirme işini controller yapmaz. Bu işi yapacak olan servise yönlendirmede bulunur.  
</p>
<p>
Yani burdaki operasyonel çalışma kesinlikle controller sınıfında olmaması gerekiyor. İdeal tasarım budur. 
</p>
<p>
Controller; kontrol edendir, işi yapan değil.
</p>
<br>

## NonAction Attribute
<p>
Controller içerisinde NonAction attribute'u ile işaretlenen fonksiyonlar dışarıdan request almazlar. 
</p>
<p>
Sadece operatif / algoritma barındıran / iş mantığı yürüten bir metot haline gelmiş olur.
</p>
<img src="img/nonaction.png">
<br><br>

## NonController Attribute
<p>
Controller seviyesinde kullandığımız bir attribute'dur. 
</p>
<p>
Sistemde var olan bütün controller'lar dışarıdan istek alabilmektedir. 
</p>
<p>
Eğer hem controller tanımlayıp hem de dışarıdan istek almasını istemiyorsak ilgili controller'ı NonController ile işaretleyebiliriz. 
</p>
<p>
Artık bu controller, normal bir sınıf işlevi görecektir.
</p>
<img src="img/noncontroller.png">