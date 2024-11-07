UEFI destekli bir sistemde doğrudan BIOS/UEFI ayarlarına erişmek için aşağıdaki komutları kullanabilirsiniz:

1. **Anında BIOS/UEFI Ayarlarına Yeniden Başlatma**
   Aşağıdaki komut, sistemi anında yeniden başlatarak BIOS/UEFI ayarlarına yönlendirecektir:
```
   systemctl reboot --firmware-setup
```

2. **Sonraki Yeniden Başlatmada BIOS/UEFI Ayarlarına Giriş Yapmak**
   Eğer sistemi şu an yeniden başlatmak istemiyorsanız, bir sonraki yeniden başlatmada otomatik olarak BIOS/UEFI ayarlarına yönlendirilmesi için:
```
   bootctl reboot-to-firmware true
```

**Not:** Bu yöntemler yalnızca UEFI destekli sistemlerde çalışmaktadır. Legacy BIOS kullanan sistemlerde, doğrudan komut ile BIOS ayarlarına geçiş yapmak için standart bir yöntem bulunmamaktadır. Bu tür sistemlerde, genellikle bilgisayar açılırken `Del`, `F2`, veya `F12` gibi özel tuşlar yardımıyla BIOS ayarlarına girilebilir.