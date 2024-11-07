Jellyfin, açık kaynaklı ve ücretsiz bir medya sunucusudur. Film, dizi, müzik ve diğer medya dosyalarınızı organize etmek ve bu içeriğe her yerden erişebilmek için Jellyfin'i kullanabilirsiniz. Hem ev kullanıcıları hem de küçük işletmeler için mükemmel bir medya yönetim ve akış çözümüdür. Jellyfin, çok sayıda platformda çalışabilir ve medya içeriklerinizi istediğiniz cihazlarda akış olarak izleyebilirsiniz. Jellyfin, medya koleksiyonunuzu yönetmek için güçlü özellikler sunarken, kullanıcı dostu arayüzü sayesinde kolayca erişilebilir ve kurulabilir.

### Jellyfin Kurulumu
Jellyfin’i Docker üzerinde çalıştırmak için aşağıdaki `docker-compose.yml` dosyasını kullanabilirsiniz:

```
version: "3"
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=America/New_York
    volumes:
      - jellyfin-config:/config
      - /mnt/NewHDD/:/NewHDD
    ports:
      - 8096:8096
    restart: unless-stopped
volumes:
  jellyfin-config: null
```

Bu `docker-compose.yml` dosyasında, Jellyfin medya sunucusunu başlatacak gerekli ayarlar yer alır. Burada `PUID` ve `PGID` değişkenleri, Jellyfin’in çalışacağı kullanıcı ve grup kimliklerini belirler. `TZ` ise zaman dilimini ayarlar.

### Port Ayarları
Varsayılan olarak, Jellyfin web arayüzü 8096 numaralı port üzerinden erişilebilir. Bu portu değiştirmek isterseniz, `ports` kısmındaki `8096:8096` değerini değiştirebilirsiniz. Örneğin, Jellyfin'e 8080 portu üzerinden erişmek isterseniz `ports` satırını şu şekilde değiştirebilirsiniz:

```
ports:
  - 8080:8096
```

Bu durumda Jellyfin'e `http://sunucu_ip_adresi:8080` adresinden erişebilirsiniz.

### /mnt Klasöründe Film ve Dizi Klasörlerinin Olması
Jellyfin’in düzgün çalışabilmesi ve medya dosyalarınızı organize edebilmesi için, film ve dizi dosyalarınızın belirli bir klasörde bulunması gerekir. Docker konfigürasyonunda `/mnt/NewHDD/` dizini kullanılmıştır. Burada `/mnt/` klasörü genellikle sunucunuzdaki harici depolama alanını temsil eder ve bu alana film, dizi, müzik gibi medya dosyalarınızı yerleştirmeniz beklenir. Bu klasörler Jellyfin’e doğru bir şekilde bağlanarak, medya içeriğinizin düzenli bir şekilde akışa sunulmasını sağlar.

Örneğin, `/mnt/NewHDD/` altında `Films` ve `Series` gibi klasörler oluşturabilir, bu klasörlere medya dosyalarınızı yükleyebilirsiniz:

```
/mnt/NewHDD/Films/   # Filmler burada
/mnt/NewHDD/Series/  # Diziler burada
```

Jellyfin, bu medya içeriklerine kolayca erişebilir ve kullanıcı dostu arayüzü üzerinden medya koleksiyonlarınızı görüntüleyebilirsiniz.

### Jellyfin’ın Özellikleri
- **Medya Akışı**: Jellyfin, yerel ağınızda veya internet üzerinden medya akışını mümkün kılar.
- **Çoklu Cihaz Desteği**: Jellyfin, akıllı telefonlar, tabletler, bilgisayarlar, akıllı TV’ler ve daha birçok cihazla uyumludur.
- **Kullanıcı Yönetimi**: Farklı kullanıcılar için ayrı profiller oluşturabilir ve erişim haklarını belirleyebilirsiniz.
- **Düşük Sistem Kaynak Kullanımı**: Jellyfin, hafif yapısı sayesinde düşük sistem kaynakları ile çalışabilir.

Jellyfin, medya koleksiyonlarınızı düzenlemek ve her yerden erişim sağlamak için mükemmel bir çözüm sunar. Hem film hem de dizi içeriklerinizi kolayca yönetebilir ve evinizdeki cihazlar arasında kesintisiz bir akış deneyimi yaşayabilirsiniz.