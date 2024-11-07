FreshRSS, haber ve içerik takibinizi kolaylaştıran, açık kaynaklı ve hafif bir RSS okuyucu uygulamasıdır. FreshRSS sayesinde birçok farklı kaynaktan gelen içerikleri tek bir arayüz üzerinden izleyebilir, okuyabilir ve organize edebilirsiniz. Kullanıcı dostu arayüzü ve esnek özellikleri ile haber akışlarınıza erişimi daha pratik ve verimli hale getirir. FreshRSS, kişisel kullanıma olduğu kadar, küçük gruplar için de uygundur.

### FreshRSS Kurulumu
FreshRSS’i Docker üzerinde çalıştırmak için aşağıdaki `compose.yml` dosyasını kullanabilirsiniz:

```
services:
  freshrss:
    image: lscr.io/linuxserver/freshrss:latest
    container_name: freshrss
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
    volumes:
      - /path/to/freshrss/config:/config
    ports:
      - 8034:80
    restart: unless-stopped
```

Bu dosyadaki `TZ` zaman dilimini belirtir.

### Port Ayarları
Varsayılan olarak, FreshRSS web arayüzü 8034 numaralı port üzerinden erişilebilir durumdadır (`http://sunucu_ip_adresi:8034`). Ancak, bu portu değiştirmek isterseniz `ports` kısmındaki sol tarafa dilediğiniz port numarasını girerek özelleştirebilirsiniz. Örneğin, FreshRSS’e 8080 portu üzerinden erişmek isterseniz `ports` satırını şu şekilde düzenleyebilirsiniz:

```
ports:
  - 8080:80
```

Bu değişiklikle, FreshRSS arayüzüne `http://sunucu_ip_adresi:8080` adresi üzerinden erişebilirsiniz. 

FreshRSS, hem pratik hem de kişiselleştirilebilir yapısı ile RSS akışlarını kontrol etmenin etkili bir yolunu sunar.