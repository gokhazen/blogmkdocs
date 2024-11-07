Vaultwarden, eski adıyla Bitwarden_RS, Bitwarden'in hafif ve açık kaynaklı bir alternatifidir. Şifre yönetimi ve güvenli depolama işlemleri için kullanılan bu araç, kişisel ve küçük işletmeler için ideal bir çözüm sunar. Vaultwarden, kendi şifre yöneticinizi barındırmanıza olanak tanır ve Docker üzerinde kolayca kurulabilir. Kullanıcılar, şifrelerini güvenli bir şekilde saklayabilir, yönetebilir ve senkronize edebilir.

### Vaultwarden Kurulumu
Vaultwarden'ı Docker üzerinde çalıştırmak için aşağıdaki `docker-compose.yml` dosyasını kullanabilirsiniz:

```
version: "3.3"
services:
  server:
    container_name: vaultwarden
    volumes:
      - /vw-data/:/data/
    restart: unless-stopped
    ports:
      - 8054:80
    image: vaultwarden/server:latest
networks: {}
```

Bu dosya, Vaultwarden'ı Docker üzerinden çalıştırmak için gerekli ayarları içerir. `volumes` kısmında belirtilen `/vw-data/` dizini, Vaultwarden'ın veritabanı ve yapılandırma dosyalarını sakladığı yerdir. Bu dizini değiştirmek isterseniz, kendi dizininizi belirtmeniz yeterlidir.

### Port Ayarları
Varsayılan olarak Vaultwarden, 8054 numaralı port üzerinden erişilebilir durumdadır (`http://sunucu_ip_adresi:8054`). Bu portu değiştirmek isterseniz, `ports` kısmındaki sol tarafa yeni port numarasını yazmanız yeterli olacaktır.

Örneğin, Vaultwarden’a 8080 portu üzerinden erişmek isterseniz `docker-compose.yml` dosyasındaki `ports` satırını şu şekilde düzenleyebilirsiniz:

```
ports:
  - 8080:80
```

Bu değişiklikle Vaultwarden'a `http://sunucu_ip_adresi:8080` adresinden erişebilirsiniz.

### Vaultwarden'ın Özellikleri
- **Güvenli Şifre Yönetimi**: Şifrelerinizi ve diğer hassas bilgilerinizi güvenli bir şekilde saklamanızı sağlar.
- **Mobil ve Web Desteği**: Vaultwarden, mobil cihazlarla uyumlu çalışır ve tüm cihazlar arasında senkronizasyon sağlar.
- **Self-hosted Çözüm**: Kendi sunucunuzda barındırabileceğiniz, açık kaynaklı bir şifre yöneticisi çözümü sunar.
- **Kolay Entegrasyon**: Web tarayıcıları ve uygulamalarla entegre olabilen bir sistemdir.

Vaultwarden, kendi şifre yöneticinizi kurmanızı sağlayarak güvenliğinizi artırır ve verilerinize her yerden erişebilmenizi sağlar.