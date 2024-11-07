Uptime Kuma, sistemlerinizin ve web sitelerinizin çevrimiçi durumunu izlemenize olanak tanıyan, açık kaynaklı ve kullanıcı dostu bir izleme aracıdır. Modern ve şık bir web arayüzü üzerinden çalışan Uptime Kuma, sunucularınızın, web sitelerinizin veya belirli hizmetlerin uptime (çalışırlık) durumunu sürekli olarak izler. Sorun yaşandığında anında bildirim alabilir ve istatistiklerle dolu geçmiş kayıtlarını inceleyebilirsiniz. Uptime Kuma, basit kurulum süreci ve düşük kaynak kullanımı sayesinde küçük veya büyük çaplı projeler için uygundur.

### Uptime Kuma Kurulumu
Uptime Kuma’yı Docker üzerinde çalıştırmak için aşağıdaki `docker-compose.yml` dosyasını kullanabilirsiniz:

```
version: "3.3"
services:
  uptime-kuma:
    restart: always
    ports:
      - 3001:3001
    volumes:
      - uptime-kuma:/app/data
    container_name: uptime-kuma
    image: louislam/uptime-kuma:1
volumes:
  uptime-kuma: {}
networks: {}
```

### Port Ayarları
Varsayılan olarak Uptime Kuma, 3001 numaralı port üzerinden çalışacak şekilde yapılandırılmıştır. `ports` kısmında sol tarafta belirtilen değer (örneğin `3001:3001`) üzerinden Uptime Kuma web arayüzüne erişim sağlanır. Bu portu değiştirerek başka bir port üzerinden erişim sağlamak için ilk 3001 değerini istediğiniz başka bir port numarasıyla değiştirebilirsiniz.

Örneğin, Uptime Kuma'ya 8080 portu üzerinden erişmek isterseniz `ports` ayarını şu şekilde düzenleyebilirsiniz:

```
ports:
  - 8080:3001
```

Bu değişiklikle birlikte Uptime Kuma arayüzüne `http://sunucu_ip_adresi:8080` adresinden erişebilirsiniz.

### Uptime Kuma’nın Özellikleri
- **Gerçek Zamanlı İzleme**: Sunucularınızın ve hizmetlerinizin çevrimiçi durumunu anında izler.
- **Bildirimler**: E-posta, Telegram, Discord, Slack ve birçok popüler platform aracılığıyla anlık bildirimler sağlar.
- **İstatistik ve Raporlar**: İzleme geçmişine dair detaylı raporlar ve istatistikler sunar.
- **Kolay Kurulum ve Yönetim**: Docker üzerinde hızlı kurulum ve kullanımı kolay bir arayüz sağlar.

Uptime Kuma, sistem yöneticilerinin sunucularını etkili bir şekilde izlemelerine yardımcı olan güçlü ve esnek bir araçtır.