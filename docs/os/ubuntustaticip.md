## Ubuntu Server'da Statik IP Belirleme

Ubuntu serverda statik IP belirlemek için iki farklı senaryomuz var. Bunlardan birisi kurulum sırasında IP adresini belirlemek, diğeri ise kurulumdan sonra halihazırda çalışan bir makineye IP atamaktır.

### 1. Kurulum Sırasında Statik IP Atama

Kurulum sırasında ağ ile ilgili ayar bölümüne geldiğinizde, IPv4 ayarlarında "Method" kısmını "Manual" olarak değiştirin ve ayarları aşağıdaki gibi yapın:
```
- Subnet: 192.168.1.0/24
- Address: 192.168.1.225
- Gateway: 192.168.1.1
- Name Servers: 8.8.8.8, 8.8.4.4
```
#### Açıklamalar:
- **Subnet**: Bu kısım, modem arayüzüne erişirken kullanılan IP adresinin son hanesinin, cihazlara özel olarak 0 olması gerektiğini belirtir. Örneğin, eğer modem arayüzüne `192.168.0.1` ile giriliyorsa, bu adresin son hanesini 0 ile değiştirip `/24` eklemelisiniz.
- **Address**: Kullanmak istediğiniz IP adresini buraya girin. Eğer bu adres başka bir cihaz tarafından kullanılıyorsa, cihaz internete bağlanamayabilir. Genelde 200 ve üzerindeki adresler ev modemlerinde otomatik atanmaz, bu yüzden `200 - 256` aralığında dilediğiniz sayıyı girebilirsiniz.
- **Gateway**: Modem arayüzüne giriş IP adresinizi buraya yazın. Bu genellikle `192.168.1.1` veya `192.168.0.1` olmaktadır. Bu adreslere tarayıcınızdan girmeyi deneyerek test edebilirsiniz.
- **Name Servers**: Cihazınıza bir DNS sunucusu atamanızı sağlar. Örneğin, Google DNS adreslerini `8.8.8.8, 8.8.4.4` veya en hızlı DNS sunuculardan biri olan Cloudflare DNS adreslerini `1.1.1.1, 1.0.0.1` olarak yazabilirsiniz.

Ayarları yaptıktan sonra "Search domains" kısmını boş bırakın, "Save" tuşuna basarak işlemi tamamlayın. Cihazınız, yeni IP adresine bağlanacaktır.



### 2. Kurulum Sonrasında Statik IP Atama

Kurulum sonrasında statik IP ayarlarını değiştirmek için aşağıdaki adımları izleyin:

1. Öncelikle makinenizde paketleri güncelleyin:
   ```
   sudo apt update
   ```
   ve ardından
   ```
   sudo apt upgrade
   ```
2. Yönetici hesabına geçin:
   ```
   sudo su
   ```
3. `/etc/netplan` dizinindeki `.yaml` dosyalarını görmek için aşağıdaki komutu çalıştırın:
   ```
   ls /etc/netplan/
   ```
   Bu dizinde genellikle `50-cloud-init.yaml` veya `01-network-manager-all.yaml` adında bir dosya bulunur. **Ubuntu Server 20.04** ve üzeri bir sürüm kullanıyorsanız muhtemelen `50-cloud-init.yaml` adlı dosyayı göreceksiniz.

4. Dosyayı düzenlemek için nano editöründe açın:
   ```
   nano /etc/netplan/50-cloud-init.yaml
   ```
5. Dosyada `ethernets:` kısmının altında internet ağ adaptörünüzün adını bulun. Bu isim genellikle `eth0` veya `enp0s3` olarak geçer. Bu ismi not alın ve dosyanın içindeki tüm metni silin.

6. Aşağıdaki örnek yapılandırma metnini dosyaya yapıştırın, ardından istediğiniz IP adresini ve DNS sunucularını girin:

```
network:
    ethernets:
        eth0: # Burada ağ adaptörü adını kendinize göre değiştirin
            addresses:
            - 192.168.1.169/24 # İstediğiniz IP adresini buraya yazın
            nameservers:
                addresses:
                - 8.8.8.8
                - 8.8.4.4 # Veya Cloudflare DNS: 1.1.1.1, 1.0.0.1
                search: []
            routes:
            -   to: default
                via: 192.168.1.1 # Modem arayüzüne giriş IP adresini buraya yazın
    version: 2
```

7. Ayarları yaparken dikkat edin; metinde bir hata yaparsanız ve makineye internet üzerinden bağlıysanız bağlantınızı kaybedebilirsiniz.

8. Dosyayı kaydedin ve nano editöründen çıkın:
   - **Kaydet**: `CTRL + S`
   - **Çıkış**: `CTRL + X`

9. Ayarların etkin olması için makineyi yeniden başlatın:
   ```
   reboot
   ```

Makineniz yeniden başladıktan sonra yeni IP adresiyle bağlantı kurabilirsiniz.