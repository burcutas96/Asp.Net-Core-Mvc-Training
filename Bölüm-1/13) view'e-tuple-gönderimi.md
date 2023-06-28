# View'e Tuple Nesne Gönderimi ve Kullanımı
## Tuple Nedir?
<p>
Tuple, içerisinde birden fazla değeri / nesneyi referans edebilen nesnelerdir.
</p>
<br>
<p>
Birden fazla veriyi ya da nesneyi bir bütün olarak kullanabilmek için ViewModel dediğimiz model'ları da kullanabiliriz. Örneğin, product ve user varlıklarımız olsun. Product nesnesiyle user nesnesi için bir tane ViewModel oluşturuyoruz. Ve içerisine product referansıyla user referansını koyuyoruz. Ve ilgili nesneleri bu referanslar üzerinden referans ediyoruz.
</p>
<p>
Dolayısıyla birden fazla değeri tek bir nesne üzerinden referans etmek istiyorsak ViewModel'ı da kullanabiliriz tuple yapısını da. 
</p>
<br>

## View Model ile nesnelerimi View'e Nasıl Taşıyabilirim?
<p>
Öncelikle Models klasörünün altında ViewModels adında bir klasör oluşturuyoruz.
</p>
<p>
Ve View'e göndermek istediğimiz birden fazla nesnenin isminde bir class oluşturuyoruz.
</p>
<img src="img/viewmodel.png">
<p style="margin:20px 0">
Daha sonrasında bu class'a, ViewModel'ın referans edeceği nesneleri property ile ekliyoruz.
</p>
<img src="img/viewmodel1.png">
<p style="margin:20px 0">
Artık oluşturduğumuz ViewModel class'ı ile nesnelerimizi view katmanına gönderebiliriz. 
</p>
<img src="img/viewmodel2.png">
<br><br>

<p>
Model olarak gönderdiğimiz userProduct'ı view katmanında da model bazlı veri gönderimine uygun bir şekilde karşılamalıyız.
</p>
<img src="img/viewmodel3.png">
<br><br>

## Tuple ile nesnelerimi View'e Nasıl Taşıyabilirim?
<p>
View'e taşımak istediğimiz nesneleri aşağıda da görüldüğü üzere virgüllerle ayırarak bildiriyoruz.
</p>
<img src="img/viewtuple.png">
<p style="margin: 20px 0">
Daha sonrasında ViewModel'da da olduğu gibi Model olarak gönderdiğimiz tupleUserProduct nesnemizi view katmanında model bazlı veri gönderimine uygun bir şekilde karşılıyoruz.
</p>
<img src="img/viewtuple1.png">
<p style="margin-top: 20px">
View katmanında tuple nesnemizi karşılarken tuple'ın içerisindeki nesnelerin türlerini parantez içerisinde bildirmeliyiz. 
</p>
<p>
Ve bu nesnelere @Model ile ulaşmak istediğimizde her bir nesneye otomatik olarak Item1, Item2, Item3... şeklinde isimlendirme yapılacak.
</p>
<p>
Eğer bu isimlendirme yerine anlamlı bir isim vermek istiyorsak resimde altı çizili şekilde gösterildiği gibi kendi isimlendirmemizi yapabiliriz.
</p>



