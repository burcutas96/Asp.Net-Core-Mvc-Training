# Custom TagHelper

## Neden özel bir tag helper oluşturmamız gerekebilir?
<p>
Özel tag helper oluşturma ihtiyacı normal bir projenin doğal seyrinde olan bir ihtiyaçtır. Gelişim sürecinde olan projelerde bazı yapıları tekrar tekrar oluşturmaktansa bunu tek seferlik oluşturmak ve her kullanmamız gereken noktada onu çağırıp kullanmak işin pratik çözümüdür.
</p>
<p>
Tag helper'da da bu ihtiyacı bu şekilde değerlendirmemiz gerekecektir. Örneğin; büyük bir uygulamada belirli noktalarda belirli view çalışmaları sürekli tekrar ediyor. 
</p>
<p>
Şimdi bu tekrarları her noktada ayrı ayrı özel bir ilgiyle geliştirmektense bunun adına tag helper geliştirip tek seferde bir component mantığıyla çözmek daha kolay, daha mantıklı olacaktır.
</p>
<br>

## Custom tag helper nasıl oluşturulur?
<p>
Custom tag helper oluştururken kullanacağımız senaryo şu şekilde olacak: 
</p>
<p>
Aşağıdaki resimde de görüldüğü üzere mail linkinin birçok view'de kullanılacağını varsayalım. Bu linki her lazım olan noktada tekrar tekrar yazmaktansa bunu bana direkt getirecek özel bir tag helper oluşturacağız.
</p>
<img src="img/customtaghelper.png">
<br><br>

<p>
Özel bir tag helper, html helper'larda olduğu gibi extension olarak oluşturulmazlar.
</p>
<p>
Tag helper'lar yapısal olarak bir sınıftırlar. Dolayısıyla custom bir tag helper oluşturabilmemiz için öncelikle normal bir sınıf oluşturmamız gerekecektir.
</p>
<img src="img/customtaghelper1.png">
<br><br>

<p>
Oluşturduğumuz TagHelpers klasörünün altında EmailTagHelper adında bir class oluşturuyoruz. (Custom TagHelper isimlerinin sonuna "TagHelper" kelimesinin getirilmesi bir isimlendirme standartıdır.)
</p>

<p>
Bir sınıfın, tag helper sınıfı olabilmesi için class isminin sonunda "TagHelper" ifadesinin olması yeterli değildir. Bu sınıfın ayrıca TagHelper class'ından türetiliyor olması lazım.
</p>
<img src="img/customtaghelper2.png">
<br><br>

<p>
Şimdi oluşturduğumuz bu tag helper'ı viewde kullanabilmemiz için öncelikle tag helper'ın kütüphanesini vermeliyiz. 
</p>
<p>
Alttaki resimde @addTagHelper diye eklediğimiz kütüphane sistem tarafından dahili olarak gelen hazır tag helper'ların bulunduğu bir kütüphanedir. 
</p>
<img src="img/customtaghelper3.png">
<br><br>
<p>
Bizim oluşturduğumuz tag helper'ı kullanabilmemiz için yine @addTagHelper komutuyla bizim namespace'imizin ismini eklememiz gerekecektir. 
</p>
<img src="img/customtaghelper4.png">
<p>
Görüldüğü üzere email tag'ı aktif hale geldi.
</p>
<br>

<p>
Bir tag helper, bizden aldığı değerlerle arkaplanda  oluşturacağı yapılanma neyse ona gerekli set işlemlerini yapacaktır.
</p>
<p>
Örneğin biz bu oluşturduğumuz tag helper'a "abc" değerindeki x attribute'unu verdik.
</p>
<p>
Ve dikkat ederseniz bu x attribute'u sadece bir attribute'dan ibaret. Yani bir tag helper'ın parçası olmadığı için herhangi bir vurguluk yok. 
</p>
<img src="img/customtaghelper5.png">
<br><br>

<p>
Bu attribute'u helper üzerinde aktifleştirebilmek / işlevsel hale getirebilmek için EmailTagHelper class'ında override etmemiz gereken bir metot olacaktır. O metot da Process() isminde bir metodudur.
</p>
<img src="img/customtaghelper6.png">
<br><br>
<p>
Uygulamayı çalıştırdığımızda ilgili tag helper tetiklendiğinde bu Process() metodu da tetiklenecektir. Bu fonksiyon, ilgili tag helper'ın işleminin yapıldığı fonksiyondur.
</p>
<p>
Process metodunun iki tane parametresi bulunmaktadır; context ve output parametreleri. Context parametresi, ilgili tag helper'a vermiş olduğumuz bütün değerleri bizlere getirirken Output parametresi bu tag helper'ın yapacağı işlemleri bize sunacaktır.
</p>
<img src="img/customtaghelper7.png">
<p>
Görüldüğü üzere context'in 'attribute' parametresi üzerinden x attribute'umuza ulaşabiliyoruz.
</p>
<p>
Tag helper'daki attribute'lara sadece context'den erişmek gibi bir kısıtlama yoktur. Alternatif olarak property'ler üzerinden de bu attribute'lara erişebiliriz.
</p>
<img src="img/customtaghelper8.png">
<p>
Aynı isimde olan property ve attribute'lar arkaplanda otomatik eşleştirilecektir. x değişkeninin tag helper class'ında bir property'si olmadığı için o attribute'a sadece context parametresinden ulaşabiliriz.
</p>
<br>

<h3>
Peki biz en baştaki a tag'ı gibi bir çıktıyı output parametresiyle nasıl oluşturabiliriz?
</h3> 
<p>
Öncelikle oluşturmak istediğimiz etiketi 'TagName' property'si ile bildiriyoruz. Bu etiketin attribute'ları olacaksa, onları 'Attributes' property'si ile belirtiyoruz. Ardından bu etiketin bir display'i olması lazım yani a etiketini görüntüleyebilmek için bir metninin olması gerekiyor. Bunun içinde 'Content' property'sini kullanıyoruz. 
</p>
<img src="img/customtaghelper9.png">
<br><br>
<p>
Ve uygulamayı çalıştırdığımızda aşağıdaki şekilde bir sonuç alacağız.
</p>
<img src="img/customtaghelper10.png">
<br><br>


### Kritik
<p>
Oluşturulan tag helper'lar isimlerini, otomatik olarak kendi sınıflarından almaktadır. Ancak sınıfın ismi dışında başka bir isimle bu helper'ı kullanmak istiyorsak bu ismi [HtmlTargetElement] attribute'u üzerinden verebiliriz.
</p>
<img src="img/customtaghelper11.png">
<p>
Görüldüğü üzere email tag helper'ı pasifleşirken custom tag helper aktif hale gelmiştir.
</p>




