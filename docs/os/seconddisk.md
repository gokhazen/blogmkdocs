Yeni bir sabit diski tanımlayıp otomatik olarak bağlanmasını sağlamak için aşağıdaki adımları takip edebilirsiniz:

1. **Yeni Sabit Diski Tanımlama**
   Yeni sabit diski görmek için bir konsol açın veya ssh ile ilgili bilgisayara bağlanın.
   Konsolu açtıktan sonra aşağıdaki komutu çalıştırın:
```
lsblk
```
   Çıktı olarak benzer bir şey göreceksiniz:
```
   loop0    7:0    0 86.6M  1 loop /snap/core/4486
   sda      8:0    0    5G  0 disk 
   ├─sda1   8:1    0  512M  0 part /boot/efi
   └─sda2   8:2    0  4.5G  0 part /
   sdb      8:16   0   10G  0 disk
   sr0     11:0    1 1024M  0 rom 
```
   Burada, `sdb` yeni sabit disk olarak görünüyor.

2. **Yeni Diski Formatlama**
   Eğer `sdb` yeni bir sabit diskse, onu ext3 veya ext4 olarak biçimlendirin. Bu komut, hedef diskteki tüm verileri siler:
```
   sudo mkfs.ext4 -j -L NewHDD /dev/sdb
```
   **Dikkat:** Eğer diskte veri varsa ve kaybetmek istemiyorsanız, bu adımı atlayabilirsiniz.

3. **UUID’yi Bulma**
   Yeni diskin UUID’sini almak için:
```
   sudo blkid /dev/sdb
```
   Çıktı olarak şöyle bir şey görebilirsiniz:
```
   /dev/sdb: LABEL="NewHDD" UUID="5d6c8f68-dcc8-4a91-a510-9bca2aa71521" TYPE="ext4"
```

4. **Yeni Diski fstab Dosyasına Ekleyerek Otomatik Bağlama**
   Sabit diskin her yeniden başlatıldığında otomatik olarak bağlanması için fstab dosyasına bir satır ekleyin:
```
   sudo nano /etc/fstab
```
   Dosyanın en altına şu satırı ekleyin (UUID ve bağlama yolunu kendi değerlerinizle değiştirin):
```
   /dev/disk/by-uuid/5d6c8f68-dcc8-4a91-a510-9bca2aa71521 /mnt/NewHDD auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=NewHDD 0 0
```
   **Not:** `5d6c8f68-dcc8-4a91-a510-9bca2aa71521` UUID’sini ve `/mnt/NewHDD` bağlama yolunu kendi bilgilerinizle değiştirin. Kaydetmek için `CTRL+X`, ardından `Y` ve `ENTER` tuşlarına basın.

5. **Diski Bağlama**
   Fstab dosyasındaki ayarları uygulamak için:
```
   sudo mount -a
```
   Eğer şu hata mesajını alırsanız:
```
   mount: /mnt/NewHDD: mount point does not exist.
```
   Bağlama noktasını oluşturmanız gerekir:
```
   sudo mkdir /mnt/NewHDD
```
   Ardından tekrar:
```
   sudo mount -a
```

6. **Diskin Sahiplik ve İzinlerini Ayarlama**
   Yeni sabit diskin sahibi ve grubunu değiştirerek izinleri ayarlayın:
```
   sudo chown user:user -R /mnt/NewHDD
```
   Burada `user:user` kısmını kendi kullanıcı ve grubunuza göre değiştirin.

Bu adımları izleyerek yeni diskinizi otomatik olarak bağlayabilir ve kullanıma hazır hale getirebilirsiniz.