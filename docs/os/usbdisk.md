### Sürücüm Nerede?

İlk olarak yapmanız gereken, sürücünüzün nerede olduğunu yani hangi `/dev/` konumuna atandığını bulmaktır.

- **`df-h` komutunu çalıştırmayı deneyin**, bu komut disk alanı ve kullanımını raporlar. Buradan sürücünüzü fark edebilirsiniz, örneğin benim durumumda bu `/dev/sda1`'dir ve sürücünün boyutuna bakarak kolayca anlayabilirsiniz.
- Eğer bu kesin değilse, **`sudo fdisk -l`** komutunu çalıştırın, bu komut disklerinizi bulmanıza yardımcı olabilir.

### Sürücüyü Bağlamak

Diyelim ki cihazımızı bulduk ve bu örnekte `/dev/sda1`'de bulunuyor, peki nasıl bağlarız?

1. Öncelikle bağlayacağımız sürücü için bir klasör oluşturun, örneğin:
   ```bash
   mkdir /media/external
   ```
   veya istediğiniz herhangi bir ismi verebilirsiniz.

2. Şimdi sürücüyü bağlamak için şu komutu kullanın:
   ```bash
   sudo mount -t ntfs-3g /dev/sda1 /media/external
   ```
   Burada bağladığım sürücünün NTFS formatında olduğunu varsayıyorum. Eğer farklı bir dosya sistemi kullanıyorsanız, örneğin `vfat` veya başka bir şey, bunu kontrol etmelisiniz. Sonrasında sadece kaynak (`/dev/sda1`) ve oluşturduğumuz hedef (`/media/external`) klasörüne bağlama yapıyoruz.

   **Not**: Bağlantı işlemi gerçekleşmeden önce, hedef klasörü `ls` komutuyla kontrol ederseniz, eğer sürücünüzde dosyalar varsa bile hiçbir dosya görmezsiniz. Ancak sürücüyü bağladıktan sonra, aynı komutla hedefi tekrar kontrol ettiğinizde USB sürücüsündeki dosyaları görebilirsiniz.

### Sürücüyü Otomatik Bağlama

Eğer sürücüyü her seferinde manuel olarak bağlamak istemiyorsanız ve işletim sisteminin sürücüyü otomatik olarak bağlamasını istiyorsanız, yapmanız gereken birkaç işlem var.

1. **Sürücünün UUID’sini bulmak için** `sudo blkid` komutunu çalıştırın. `/dev/sda1` cihazının yanında bir UUID olacak, bu UUID’yi kopyalayın veya not edin.
2. **fstab dosyasını açın**:
```
   sudo nano /etc/fstab
```
3. Dosyanın altına şu satırı ekleyin:
```
   UUID=ABCDEFGHIJK /media/external auto nosuid,nodev,nofail 0 0
```
   Burada `ABCDEFGHIJK` UUID’niz ile değiştirilmelidir. Ardından dosyayı kaydedin.

4. **sudo mount -a** komutunu çalıştırarak hataların olup olmadığını kontrol edin.

Artık bilgisayarınızı yeniden başlattığınızda USB sürücünüz otomatik olarak bağlanacaktır.