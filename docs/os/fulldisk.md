### Ubuntu Server'da Diskin Tamamını Kullanılabilir Hale Getirme

Ubuntu Server kurulumlarında bazen disk alanının tamamı kullanılabilir olarak tanımlanmaz ve bu da diskin bir kısmının boşta kalmasına neden olabilir. Aşağıdaki adımları izleyerek diskinizin tamamını sisteme tanımlayabilirsiniz:

1. Yönetici hesabına geçin:
   `sudo su`

2. Disk hacmini görüntülemek için aşağıdaki komutu çalıştırın:
   ```vgdisplay```

3. Diskin tamamını kullanmak için alanı genişletin:
   ```lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv```

4. Dosya sistemini yeni alana göre yeniden boyutlandırın:
   ```resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv```