# İnternette Gezerken Perde Arkası Nasıldır
<p>
Normalde yazılımla ilgili bilgi sahibi olmayan biri, "İnternette hepsiburada.com'a girdim." ya da "hepsiburada.com'a tıkladım" diye bir ifade kullanır. Ancak biz yazılımcıların dilinin bu şekilde olmaması gerekir. Bu ifadelerin yerine "hepsiburada.com'a istek / request attım ve bu istek sonucunda response geldi" demeliyiz.
</p>

<p>
Yani artık bir web sitesinin açılması için yaptığımız eyleme girdik / tıkladık değil istek gönderdik diyeceğiz.
</p>
<br><br>


## İnternette Kullandığımız Temel Kavramlar
<p>
User => Web'e girmek isteyen kişidir.
</p>
<p>
Client => User'ın web'e girmek için kullandığı teknoloji, uygulamadır. 
Bir istekte bulunmak için kullanılan teknolojiye, araca client denir.
</p>
<p>
Hosting => Bir web sitesinde yayınlanmak istenen sayfaların, resimlerin veya dokümanların userlar tarafından erişebileceği bir bilgisayarda tutulmasıdır.
</p>
<p>
Request => Client üzerinden user'ın yaptığı istektir. Request içerisinde adrese / domain'e / ip'ye istek gönderildiği bilgisi tutulur. 
</p>
<p>
Response => Sunucu tarafından client'a dönülen cevaptır. Bu cevap server tarafından üretilen result'ı barındırabilir. 
</p>
<p>
Ip => Birbirlerinden bağımsız, unique, farklı kimliklerdir. Yani internette her bir bilgisayara verilen kimliktir. Ve bizim hosting'inde bir kimliği var. Hosting'imi ben ilgili ip'ye isteği gönderdiğimde o hosting'in içerisindeki web uygulamam orada işleniyor ve sonucu döndürülüyor. 
</p>
<p>
Domain => Ip'ye yönlendirilmiş anlamlı, metinsel değerlerdir. Alan adı, bir web sitesinin internetteki adı ve adresidir.
</p>
Burada client her şey olabilir. Genellikle web sitelerini ya da kullanıcıları client zannediyoruz ancak client dediğimiz şey istek yapabildiğimiz her şey olabilir. 
</p>
<p>
Örneğin, televizyon izliyoruz ve burda televizyonu izleyen kişi user iken kumandayı kullanarak kanalı değiştirdiğim için, bir istek yaptığım için kumanda burada bir client'dır, istemcidir. Televizyon ise server'dır.
</p>
<p>
İnternette istek yapacağımız sitenin herkes tarafından, 7/24 erişilebilmesi için bu siteyi açabilecek bir bilgisayarın olması gerekiyor. Bu bilgisayara sunucu, hosting veya server denir. 
</p>
<br><hr><br>

<p>
İnternette istek yaptığımızda dünya üzerinde binlerce milyonlarca domain, hosting olabilir. Bunlardan hangisine istek gönderdiğimizi ip eşleşmesinden buluyoruz.
</p>
<p>
Hosting, web uygulamamıza bir tane ip veriyor. Ve biz bu ip'ye istek göndermiş oluyoruz.
</p>
<p>
Ve normalde hosting'e www.hepsiburada.com konseptinde istekler gönderiyoruz. Peki hosting'in vermiş olduğu ip ile bu yapmış olduğumuz istekler nasıl eşleşecek?
</p>
<p>
Şimdi biz user'lara kolaylık olması açısından ip'leri kullanmayız onun yerine domain'leri tercih ederiz. Çünkü ip adreslerini akılda tutmak zordur bunun yerine anlamlı olan domain'leri kullanırız.
</p>
<p>
Yani web uygulamasına istek göndermek için domain'i de, ip'yi de kullanabiliriz. Ancak domainleri akılda tutmak daha kolay olduğu için domain'leri kullanmayı tercih ederiz.
</p>
<p>



