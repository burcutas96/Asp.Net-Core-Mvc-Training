# Web Uygulaması Geliştirme Yaklaşımları
<p>
Web uygulaması geliştirirken, geliştirme yaklaşımımıza göre mimariyi şekillendiririz. Yani belirli yaklaşımlar var ve bu yaklaşımlardan kabul ettiğimizi o mimarimize uygularız. Başka bir deyişle, o yaklaşımla mimarimizi kodlarız. 
</p>

<p>
İnceleyeceğimiz yaklaşımlar; olay tabanlı web geliştirme mimarisi, mvc mimarisi ve api mimarisidir. Bunlardan başka yaklaşımlar olsa da bizim ele alıp inceleyeceğimiz konular bunlardır.
<p>
<br>

## Olay Tabanlı Programlama Yaklaşımı
<p>
Olay güdümlü programlama veya Olay yönlendirmeli programlama da denmektedir.
</p>
<p>
Programın akışını, kullanıcının eylemlerine göre yönlendiren programlama yaklaşımıdır.
</p>
<p>
Örneğin, kapkaranlık bir odaya girdik ve ışığın yanması için düğmeye basmamız gerekiyor. Biz düğmeye bastığımız zaman bu olay gerçekleştiği zaman sonuç olarak ışık yanıyor. İşte burda kullanıcının eylemine göre program yönleniyor. 
</p>
<p>
Bu örnekte şöyle düşünebiliriz: Düğmeye basılması bir olayken bu olay neticesinde bir işin yapılması yani ışığın yanması ise olay tabanlı programlama yaklaşımıdır.
</p>
<p>
Olay tabanlı yaklaşımda kişinin, kullanıcının eylemleri önplandadır.
</p>
<p>
Kullanıcı eylemlerine uygun bir şekilde olaylar tanımlanmıştır. Bu olaylar çalıştırılacak kodu barındırmaktadır.
</p>
<p>
Uygulama hızlı bir şekilde inşa edilebilir ancak bakım ve sonraki gelişim süreci oldukça maliyetli olan bir yaklaşımdır.
</p>
<br>

## Model View Controller (MVC) Yaklaşımı
<p>
Mvc patter'ını kullanan bir yaklaşımdır. Mvc esasında bir design pattern'dır.
</p>
<p>
Üretilen veri ile gösterim arasında bir soyutlama esas alınmıştır.
</p>
<p>
Bu tasarımın çalışma şekli şöyledir: Kullanıcı, ilgili web sitesine bir istek gönderdiği zaman bu istek controller tarafından karşılanır. Eğer ki veri tabanı işlemi varsa controller, model'a gider. İlgili veri tabanı işlemini yapar. Ve elde ettiği yani ürettiği veriyi view'a gönderir. Ve çıkan sonucu user'a gösterir.
</p>
<p>
Mvc pattern'ı Microsoft tarafından üretilmemiştir. Böyle bir yanlış algı vardır.
</p>
<p>
Mvc, Microsoft'un kurulduğu yıllardan beri tasarlanmış bir kalıptır.
</p>
<p>
Microsoft sadece bu tasarım desenine uygun bir mimari geliştirmiştir.
</p>
<br>

## Application Programing Interface (API) Yaklaşımı
<p>
Uygulama Programlama Arayüzü denir. 
</p>
<p>
Web'de çalışabilen ve web uygulamaları, işletim sistemleri, veri tabanları, donanımlar yahut yazılım kütüphaneleri ile iletişim kurabilen bir arayüzdür.
</p>
<p>
Direkt olarak web uygulaması yaklaşımıdır diyemeyiz. Lakin genellikle web tabanlı uygulamalarda client ve server arasındaki iletişimi sağlayan bir sözleşme olarak kullanılmaktadır. Bu forma Web Api ismi verilmektedir. 
</p>
<p>
Web uygulamalarında api'yi bir backend olarak düşünebiliriz. Herhangi bir görsel yanı yoktur.
</p>
<p>
Api sadece web'de kullanılan bir yaklaşım değildir. Api ile biz birçok nesneyi internete bağlayabiliriz.
</p>




