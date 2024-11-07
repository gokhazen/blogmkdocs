Linux işletim sisteminde deneyimsiz bir kullanıcının karşılaşabileceği en yaygın durumlardan biri, RAM'in dolması sonucunda cihazın yeniden başlatılana kadar kilitlenmesidir. Masaüstü Linux dağıtımlarının çoğunda, "swap" olarak bilinen yedek RAM özelliği otomatik olarak etkin gelir; ancak Ubuntu Server gibi bazı işletim sistemlerinde bu özellik kapalıdır. Swap, cihazın depolama alanının RAM dolduğunda geçici olarak RAM gibi davranmasını sağlayarak, sistemin kilitlenmesini önler. Ancak, bir disk hiçbir zaman RAM kadar hızlı ve verimli çalışamaz ve diskin yazma ömrü, RAM ile kıyaslandığında çok daha kısadır. Dolayısıyla, swap’in sık kullanıldığı sistemlerde, sistem diskinin ömrü kısalabilir. Bununla birlikte, swap, RAM tamamen dolduğunda sisteme uzaktan erişme imkanı sağlar ve kilitlenme olmadan RAM’i dolduran uygulamayı kapatma esnekliği sunar.

### Swap Alanını Kontrol Etme ve Kurulum

1. **Swap Kontrolü**  
   Sistemde hali hazırda bir swap alanı olup olmadığını kontrol etmek için:
   ```
   swapon -s
   ```
   komutunu çalıştırın. Eğer bir sonuç çıkmıyorsa, swap bulunmuyor demektir.

2. **Disk Alanını Kontrol Etme**  
   Swap oluşturabilmek için diskinizde yeterli boş alan olup olmadığını görmek için:
   ```
   df -h
   ```
   komutunu çalıştırarak disk durumunu kontrol edin.

3. **Swap Boyutu Belirleme**  
   Genellikle swap boyutunun, sistemdeki RAM’in yarısı kadar olması önerilir. RAM miktarınızı bilmiyorsanız, görev yöneticisine erişmek için:
   ```
   htop
   ```
   komutunu çalıştırarak RAM miktarınızı kontrol edebilirsiniz.

4. **Swap Dosyası Oluşturma**  
   Örneğin, 2 GB swap alanı oluşturmak için aşağıdaki komutu çalıştırın:
   ```
   dd if=/dev/zero of=/mnt/swapfile bs=1024 count=2048k
   ```
   (İhtiyaca göre “count” değerini ayarlayabilirsiniz: Örneğin, istediğiniz swap boyutu (GB) x 1024)

5. **Swap Bölümünü Biçimlendirme**  
   Swap dosyasını biçimlendirmek için:
   ```
   mkswap /mnt/swapfile
   ```
   Bu komutu çalıştırdığınızda “insecure permissions” uyarısı alırsanız, bu uyarıyı göz ardı edebilirsiniz.

6. **Swap’i Aktifleştirme ve Güvenlik Ayarları**  
   Swap dosyasını etkinleştirmek için:
   ```
   swapon -s
   ```
   komutuyla swap durumunu kontrol edin. Ardından swap’in sistem yeniden başlatıldığında da çalışmasını sağlamak için:
   ```
   echo "/mnt/swapfile none swap defaults 0 0" >> /etc/fstab
   ```
   komutunu kullanın. Swap dosyasının güvenliğini sağlamak için:
   ```
   chown root:root /mnt/swapfile
   chmod 0600 /mnt/swapfile
   ```

### Swappiness Ayarı

Swappiness, swap’in RAM doluluk oranına göre ne zaman devreye gireceğini belirler. Bu değeri görmek için:
```
cat /proc/sys/vm/swappiness
```
Swappiness değerleri:

- `swappiness = 0`: Swap yalnızca RAM tamamen dolduğunda kullanılır.
- `swappiness = 10`: Swap, RAM’in %10'u dolduğunda devreye girer.
- `swappiness = 60`: Swap, RAM’in %60’ı dolduğunda kullanılır.
- `swappiness = 100`: Swap, RAM’e öncelik verir.

Sistem performansı ve disk ömrü açısından, bu değeri düşük tutmanız önerilir. Değeri 10 yapmak için:
```
sysctl vm.swappiness=10
```

Bu ayarın her yeniden başlatmada sabit kalması için, `/etc/sysctl.conf` dosyasının sonuna `vm.swappiness=10` satırını ekleyin. Bu satır dosyada yoksa manuel olarak ekleyin.

### Son Kontrol

Sisteminizi yeniden başlattıktan sonra swap durumunu ve swappiness değerini tekrar kontrol etmek için:
```
swapon -s
cat /proc/sys/vm/swappiness
```
komutlarını kullanarak ayarlarınızın aktif olduğunu doğrulayabilirsiniz.