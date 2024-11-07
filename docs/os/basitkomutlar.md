Bu rehber Ubuntu Server'da sık kullanılan bazı temel komutlar ve nasıl kullanıldıklarını anlatıyor . Bu komutlar, dosya ve dizin yönetimi için temel araçlardır ve yeni başlayanlar için çok faydalıdır. İşte en yaygın komutlardan bazıları:

### 1. `ls` - Listeleme Komutu
`ls` komutu, mevcut dizindeki dosya ve dizinleri listelemek için kullanılır.

#### Kullanım:
```
ls
```

#### Örnekler:
- **Sadece dosya adlarını listelemek için**:
  ```
  ls
  ```
- **Detaylı listeleme için**:
  ```
  ls -l
  ```
- **Gizli dosyaları da listelemek için**:
  ```
  ls -a
  ```
  
### 2. `cd` - Dizin Değiştirme Komutu
`cd` komutu, farklı dizinlere geçiş yapmanıza olanak tanır.

#### Kullanım:
```
cd <dizin_adı>
```

#### Örnekler:
- **Ana dizine geçmek için**:
  ```
  cd ~
  ```
- **Bir üst dizine geçmek için**:
  ```
  cd ..
  ```
- **Belirli bir dizine geçmek için**:
  ```
  cd /var/log
  ```

### 3. `mkdir` - Dizin Oluşturma Komutu
`mkdir` komutu, yeni bir dizin oluşturmak için kullanılır.

#### Kullanım:
```
mkdir <dizin_adı>
```

#### Örnek:
- **Yeni bir dizin oluşturmak için**:
  ```
  mkdir projeler
  ```
- **İç içe dizinler oluşturmak için**:
  ```
  mkdir -p projeler/2023/yeni
  ```

### 4. `rm` - Dosya veya Dizin Silme Komutu
`rm` komutu, dosya veya dizinleri silmek için kullanılır.

#### Kullanım:
```
rm <dosya_adı>
```

#### Örnekler:
- **Tek bir dosyayı silmek için**:
  ```
  rm dosya.txt
  ```
- **Boş olmayan bir dizini silmek için (dikkatli olun!)**:
  ```
  rm -r dizin_adı
  ```
- **Onay sormadan tüm dosya ve dizinleri silmek için**:
  ```
  rm -rf dizin_adı
  ```

### 5. `cp` - Kopyalama Komutu
`cp` komutu, dosya veya dizinleri kopyalamak için kullanılır.

#### Kullanım:
```
cp <kaynak> <hedef>
```

#### Örnekler:
- **Bir dosyayı kopyalamak için**:
  ```
  cp dosya1.txt dosya2.txt
  ```
- **Bir dizini ve içindekileri kopyalamak için**:
  ```bsh
  cp -r eski_dizin yeni_dizin
  ```

### 6. `mv` - Taşıma veya Yeniden Adlandırma Komutu
`mv` komutu, dosya veya dizinleri taşımak veya yeniden adlandırmak için kullanılır.

#### Kullanım:
```
mv <kaynak> <hedef>
```

#### Örnekler:
- **Bir dosyayı yeni bir konuma taşımak için**:
  ```
  mv dosya.txt /home/kullanici
  ```
- **Bir dosyayı yeniden adlandırmak için**:
  ```
  mv eski_ad.txt yeni_ad.txt
  ```

### 7. `touch` - Boş Dosya Oluşturma Komutu
`touch` komutu, yeni ve boş bir dosya oluşturmak için kullanılır.

#### Kullanım:
```
touch <dosya_adı>
```

#### Örnek:
- **Yeni bir boş dosya oluşturmak için**:
  ```
  touch yeni_dosya.txt
  ```

### 8. `cat` - Dosya İçeriğini Görüntüleme Komutu
`cat` komutu, bir dosyanın içeriğini terminalde görüntülemek için kullanılır.

#### Kullanım:
```
cat <dosya_adı>
```

#### Örnek:
- **Bir dosyanın içeriğini görüntülemek için**:
  ```
  cat dosya.txt
  ```

### 9. `nano` veya `vi` - Dosya Düzenleyiciler
`nano` ve `vi` komutları, terminal üzerinden dosya düzenlemek için kullanılan basit editörlerdir.

#### Kullanım:
```
nano <dosya_adı>
vi <dosya_adı>
```

#### Örnekler:
- **Bir dosyayı düzenlemek için**:
  ```
  nano dosya.txt
  ```
- **Vi ile bir dosyayı açmak için**:
  ```
  vi dosya.txt
  ```

### 10. `chmod` - İzin Değiştirme Komutu
`chmod` komutu, dosya veya dizin izinlerini değiştirmek için kullanılır.

#### Kullanım:
```
chmod <izinler> <dosya_adı>
```

#### Örnekler:
- **Bir dosyayı çalıştırılabilir yapmak için**:
  ```
  chmod +x script.sh
  ```
- **İzinleri tam olarak belirlemek için**:
  ```
  chmod 755 dosya.txt
  ```


Tabii ki, Ubuntu Server’da sıklıkla kullanılan başka önemli komutlar da var. Bu komutlar, sistem bilgilerini görmek, ağ bağlantılarını yönetmek, süreçleri kontrol etmek ve kullanıcı izinlerini ayarlamak gibi işlemler için kullanılır. İşte daha fazla komut ve açıklamaları:

### 11. `pwd` - Geçerli Dizini Görüntüleme Komutu
`pwd` komutu, şu an içinde bulunduğunuz dizini gösterir.

#### Kullanım:
```
pwd
```

#### Örnek:
```
pwd
```
Bu, örneğin `/home/kullanici` gibi geçerli dizinin tam yolunu gösterecektir.

### 12. `echo` - Metin veya Değişken Yazdırma Komutu
`echo` komutu, bir metni veya değişken değerini terminale yazdırır.

#### Kullanım:
```
echo <mesaj>
```

#### Örnek:
- **Bir mesaj yazdırmak için**:
  ```
  echo "Merhaba, dünya!"
  ```
- **Bir ortam değişkenini yazdırmak için**:
  ```
  echo $HOME
  ```

### 13. `man` - Komutlar İçin Yardım Kılavuzu
`man` komutu, herhangi bir komut hakkında ayrıntılı bilgi sağlar.

#### Kullanım:
```
man <komut_adı>
```

#### Örnek:
- **`ls` komutu hakkında bilgi almak için**:
  ```
  man ls
  ```

### 14. `ps` - Çalışan Süreçleri Listeleme Komutu
`ps` komutu, sistemde çalışan işlemleri listelemek için kullanılır.

#### Kullanım:
```
ps
```

#### Örnek:
- **Sistemde çalışan işlemleri detaylı olarak görmek için**:
  ```
  ps aux
  ```

### 15. `kill` - İşlemi Sonlandırma Komutu
`kill` komutu, belirli bir işlem kimliğine (PID) sahip süreci sonlandırmak için kullanılır.

#### Kullanım:
```
kill <PID>
```

#### Örnek:
- **PID'si 1234 olan işlemi sonlandırmak için**:
  ```
  kill 1234
  ```

### 16. `top` - Sistem Kaynaklarını Canlı İzleme
`top` komutu, CPU ve bellek kullanımı gibi sistem kaynaklarını gerçek zamanlı olarak izlemek için kullanılır.

#### Kullanım:
```
top
```

#### Örnek:
- **Sistem kaynak kullanımını izlemek için**:
  ```
  top
  ```

### 17. `df` - Disk Kullanımını Görüntüleme
`df` komutu, sistemdeki disklerin kullanım oranını gösterir.

#### Kullanım:
```
df
```

#### Örnek:
- **Disk kullanımını insan tarafından okunabilir formatta görmek için**:
  ```
  df -h
  ```

### 18. `du` - Dosya ve Dizin Boyutlarını Görüntüleme
`du` komutu, belirli bir dizin veya dosyanın disk üzerindeki boyutunu gösterir.

#### Kullanım:
```
du <dizin_adı>
```

#### Örnek:
- **Bir dizinin boyutunu görmek için**:
  ```
  du -sh /var/log
  ```

### 19. `ifconfig` veya `ip` - Ağ Arayüzü Bilgileri
`ifconfig` ve `ip` komutları, ağ yapılandırması hakkında bilgi verir.

#### Kullanım:
```
ifconfig
```
veya
```
ip addr
```

#### Örnek:
- **IP adresini görmek için**:
  ```
  ifconfig
  ```
  veya
  ```
  ip addr show
  ```

### 20. `ping` - Ağ Bağlantısını Test Etme
`ping` komutu, bir ağdaki başka bir cihazla bağlantıyı test etmek için kullanılır.

#### Kullanım:
```
ping <hedef_ip_adresi>
```

#### Örnek:
- **Bir sunucuya ping atmak için**:
  ```
  ping google.com
  ```

### 21. `wget` - Dosya İndirme Komutu
`wget` komutu, internetten dosya indirmek için kullanılır.

#### Kullanım:
```
wget <URL>
```

#### Örnek:
- **Bir dosya indirmek için**:
  ```
  wget http://example.com/dosya.zip
  ```

### 22. `apt` - Paket Yöneticisi
`apt` komutu, yazılım paketlerini kurmak, güncellemek veya kaldırmak için kullanılır.

#### Kullanım:
```
sudo apt install <paket_adı>
sudo apt update
sudo apt upgrade
```

#### Örnekler:
- **Yeni bir paket kurmak için**:
  ```
  sudo apt install nginx
  ```
- **Tüm paketleri güncellemek için**:
  ```
  sudo apt update && sudo apt upgrade
  ```


### 23. `chown` - Dosya Sahipliğini Değiştirme
`chown` komutu, dosya veya dizin sahipliğini değiştirmek için kullanılır.

#### Kullanım:
```
sudo chown <yeni_sahip> <dosya_adı>
```

#### Örnek:
- **Bir dosyanın sahibini değiştirmek için**:
  ```
  sudo chown yeni_kullanici dosya.txt
  ```

### 25. `tar` - Arşiv Dosyalarını Yönetme
`tar` komutu, dosyaları sıkıştırmak veya sıkıştırılmış dosyaları açmak için kullanılır.

#### Kullanım:
```
tar -cvf <arşiv_adı.tar> <dizin_adı>
tar -xvf <arşiv_adı.tar>
```

#### Örnekler:
- **Bir dizini sıkıştırmak için**:
  ```
  tar -cvf yedek.tar /home/kullanici
  ```
- **Bir arşivi açmak için**:
  ```
  tar -xvf yedek.tar
  ```

---

### Özet

Bu komutlar, Ubuntu Server'da günlük işlerinizi ve sistem yönetimini oldukça kolaylaştıracaktır. Bu liste, sistem yöneticileri için olmazsa olmaz temel araçları içerir, komutların manuel sayfalarına `man <komut>` yazarak daha ayrıntılı bilgi alabilirsiniz.