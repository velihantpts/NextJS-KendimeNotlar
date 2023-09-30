## Next JS'de routing nasıl yapılır?
### Pages klasörü

* Next JS file-based routing mimarisine sahiptir. Bu da sayfa pathlerinin dosya adlarına göre otomatik oluştuğu anlamında gelmektedir.
  Bu dinamik sistem  Pages klasörü üzerine kurulmuştur. İçindeki dosya adlarına göre uygulamanın URL'i belirlenir. Örneğin `pages/about.js`  dosyasına  `/about` pathi ile erişilebilir.
  Aynı şekilde daha katmanlı bir routing istiyorsak bu alt alt klasörler yapısı ile birlikteNext JS'de mümkün.
  
![image](https://github.com/velihantpts/NextJS-KendimeNotlar/assets/56006189/5fed51e6-a856-41a6-80ce-f15e1c18cf5a)


* Yukarıdaki file-based routing mantığını daha iyi anlatan bir görsel mevcut. Öncellikle index.js dosyalarımınız ana pathi olmaktadır. Daha sonra oluşturulan dosyaların pathleri `/******` şeklinde olmaktadır.
  
* Burada dikkat etmemiz gereken bir nokta da katmanlı yapıda pathler oluşturabilmemizdir. Görselde de olduğu gibi blog klasörünün altında oluşturulan [id].js dosyasına /blog/blog_id pathi ile ulaşabiliriz. Bu kullanım özellikle
  dinamik yapılar için oldukça önemlidir.

### Pages klasörü dışında routing işlemi

* Pages dosyasının Next.JS için özel routing klasörü olduğunu yukarıda söylemiştik. Peki kendi klasörlerimizde routing işlemi yapamaz mıyız? Elbette yapabiliriz ama bu noktada Next js bize klasörlerin için page.js dosyasında işlemi yapmamızı istemekte. Diğer yapılan dosyaları
  otomatik navigate yapamamakta.
 ![image](https://github.com/velihantpts/NextJS-KendimeNotlar/assets/56006189/969fc50f-1382-4367-a6d5-be4b1ab8f891)
* Yukarıdaki görselde pages.js dosyaları navigate edilebilirken diğer dosyalarının edilemediğini söyleyebiliriz.
