# introduction
Merhaba, bu projede nodeMCU(ESP8266) kullanarak sıcaklık ve nem verilerini web server'a gönderdim. 
<br>Yani sensörden aldığım verileri internet aracılığıyla veritabanına kaydettim. Şimdi sizlere bunu nasıl yaptığımı açıklamak istiyorum.

* #### Öncelikle nodeMCU ' ya nem ve sıcaklık sensörünü bağlamamız gerekli. Kablo uçlarını resimdeki çıkışlara bağlayalım

* #### Daha sonra Arduino IDE programını açıp, nodeMCU dosyasını programlamamız lazım.
(Not: Eğer Windows kullanıcısıysanız 'Microsoft Store' ye giriş yaparak Arduino yazısını aratırsanız, Microsoft Store' den programı kurabilirsiniz, bu şekilde kurmak daha pratik.)
![5](https://user-images.githubusercontent.com/50117470/77775186-42033f80-705d-11ea-8c36-3d14e5ffaa0c.PNG)


# Codes
* #### Bu kısımda öncelikle kütüphaneleri include ettik. Daha sonra nodeMCU çıkış pinlerini belirledik, ve nodeMCU' nun kullanacağı internetin wifi ismini ve şifresini girdik. host değişkeninede verileri göndereceğimiz web sitesini yazıyoruz.
![1](https://user-images.githubusercontent.com/50117470/77767932-d4eaac80-7052-11ea-9f59-8be88248d889.PNG)

* #### setup() :coffee:
* #### Bu kısımda nodeMCU, sensör verilerini almaya başlıyor, daha sonrasında WiFi bağlantısını gerçekleştiriyor. WiFi adı ve şifresinde yanlışlık olursa bu kısımda hata verir ve bağlantı gerçekleşmez. Eğer bilgiler doğruysa 'WiFi connected' yazısı Seri Port ekranına gelir.
![2](https://user-images.githubusercontent.com/50117470/77768203-314dcc00-7053-11ea-909c-e3ddbb13f51b.PNG)

* #### Loop() :coffee:
* #### bu kısımda `float h` ve `float t` adında değişken tanımladık. `h` ile nem verilerini `t` ile de sıcaklık verilerini tuttuk. 
``` html
  if (isnan(h) || isnan(t)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }
```
* #### Daha sonra bu kısımda ise okuma denetimi yaptık. Yani sensörden bu kısımda veriler alınıyormu/okunuyormu onu test ettik. Eğer sensör pinlerini farklı bağlarsanız büyük ihtimalle bu kısımda hata ile karşılaşıcaksınız.Sonrasında Host ile bağlantı sağlıyor.
![3](https://user-images.githubusercontent.com/50117470/77768989-4ecf6580-7054-11ea-8acb-4b3ad5858b03.PNG)

* #### Son kısımda ise oluşturduğumuz `insert.php` ' ye parametre gönderiyoruz. float `h` ve `t` değişkeninde tuttuğumuz verileri veritabanına gönderiyoruz. Daha sonra veri yazma işi başarıyla gerçekleştikten sonra bağlantıyı kapatıyoruz.
![4](https://user-images.githubusercontent.com/50117470/77772863-d66ba300-7059-11ea-9d28-064f60e158a7.PNG)


# Link Example
[Video Link](https://streamable.com/q7jjp)




