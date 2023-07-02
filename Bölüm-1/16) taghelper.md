# TagHelper

<p>
TagHelpers; daha okunabilir, anlaşılabilir, kolay geliştirilebilir bir view inşa etmemizi sağlayan Asp .Net Core ile birlikte HtmlHelpers'ların yerine gelen yapılardır.  
</p>
<br>

## TagHelper vs HtmlHelper
* <p> TagHelper'lar view'lerdeki kod maliyetini oldukça düşürmektedirler.
</p>
<br>

* <p> TagHelper'lar, HtmlHelper'ların html nesnelerinin generate edilmesi server'a yüklemesinin getirdiği maliyetide ortadan kaldırmaktadır.
</p>
<br>

* <p> HtmlHelpers'lardaki programatik yapılanma, programlama bilmeyen tasarımcıların çalışmasını imkansız hale getirmekteydi. TagHelpers'lar ile buradaki kusur giderildi ve tasarımcılar açısından programlama bilgisine ihtiyaç duyulmaksızın çalışma yapılabilir nitelik kazandırdı.
</p>
<br>

* <p> HtmlHelpers ile oluşturulan html nesnesinin attribute'ları 'htmlAttribute' parametresi üzerinden anonim nesne ile verilmektedir. Bu durum hem bellek optimizasyonu açısından hem de kod maliyeti açısından oldukça zararlıdır. TagHelpers'lar bu maliyeti ortadan kaldırmakta ve html nesnelerine sadece ilgili attribute'ları normal sözdizimiyle vermekle ilgilenmektedir.
</p>
<br>


## TagHelper Entegrasyonu
<p>
TagHelper'lar özlerinde bir sınıf oldukları için belirli bir kütüphanenin içerisinde barındırılmaktadır.
</p>
<p>
TagHelper'ı kullanabilmemiz için öncelikle view'lere @addTagHelper diyerek Microsoft.AspNetCore.Mvc.TagHelpers kütüphanesini eklememiz gerekecektir. 
</p>
<img src="img/taghelper.png">
<br><br>

<p>
Yukarıdaki resimde işaret edilen yıldız sembolüyle TagHelpers kütüphanesindeki bütün sınıflara ulaşmak istediğimizi belirtmiş oluyoruz.
</p>

<p>
TagHelper'ın view'de aktif olup olmadığını anlamak için herhangi bir html etiketi üzerinde "as" yazdığımızda aşağıdaki seçenekler geliyorsa TagHelper sınıfı aktif demektir.
</p>
<img src="img/taghelper1.png">
<br><br><br>


## Html Nesnelerinde TagHelpers

* ### Form TagHelper

<img src="img/taghelper2.png">
<p>
Arkaplanda bir form oluşturmak için kullanmamız gereken parametreler, ifadeler: 1.'si HtmlHelper, 2.'si TagHelper.
</p>
<br>

* ### Input TagHelper
<p>
Input nesnelerinde ve bu nesneler üzerinde belirli model biding işlemlerinde vs. kullandığımız TagHelper'dır.
</p>
<img src="img/inputtaghelper.png">
<br><br>


* ### Cache TagHelper
<p>
Elimizdeki verileri cache işlemine tabi tutabiliyoruz.
</p>
<img src="img/cachetaghelper.png">
<p>
Cache'lenen veri cache'den gelirken, alttaki cache'lenmemiş veri o anki tarih bilgisini ekrana getirir.
</p>
<br>


* ### Environment TagHelper 
<p>
Bulunduğumuz farklı ortamlara göre environment TagHelper'ını kullanabiliriz.  
</p>
<img src="img/environmenttaghelper.png">
<br><br>


* ### Image TagHelper
<p>
Tarayıcılar static dosyaları local cache üzerinde saklamaktadırlar.
</p>
<p>
Cachelenmiş bir dosya tekrar istenildiği taktirde bunun için server'a istek gönderilmez ve local cache üzerinden ilgili dosyanın cache'i gönderilir. Böylece sayfalar ilk açılışlarından sonraki taleplerde daha hızlı yüklenebilmektedir.
</p>
<p>
Lakin bazen dosya adı değişmeden içeriği değişebilmektedir. Böyle bir durumda ilgili dosyanın cache'den değil server'dan yüklenmesi gerekmektedir. Bu duruma biz ETag yöntemiyle müdahale edebilmekteyiz.
</p>
<p>
Asp .Net Core Mvc mimarisinde TagHelper'lar içerisinde static dosyalara ETag yöntemini uygulayabilir ve dosyanın adı değişmesede içeriği değiştiği taktirde ETag üzerinden bu değişikliği fark ederek ilgili dosyanın server'dan talep edileceği bilinebilmektedir.
</p>
<img src="img/imagetaghelper.png">
<br><br>


* ### Partial TagHelper
<img src="img/partialtaghelper.png">
<br><br>


* ### Remove TagHelper
<p>
TagHelper'ları eklediğimiz view'lerden tekrardan kaldırabilmek için kullanılan helper'dır.
</p>
<img src="img/removetaghelper.png">
<p>
Görüldüğü üzere img tag helper pasifleşip normal bir attribute haline gelmiş.
</p>
<br>


* ### Remove ! TagHelper 
<p>
Eğer TagHelper'ları tag seviyesinde pasifleştirmek istiyorsak bunun için remove ! TagHelper'ı kullanırız.
</p>
<img src="img/removetaghelper1.png">
<p>
Görüldüğü üzere üstteki tag helper'da ünlem kullanılmamış. Haliyle tag helper aktif. Ancak alttaki tag helper'da ünlem kullanıldığı için tag helper kullanılamaz hale gelmiştir.
</p>


