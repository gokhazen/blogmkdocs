Docker konteynerlarını yönetmenin pratik bir yolu olan Dockge, kullanıcı dostu bir web arayüzü sunarak Docker kontrolünüze konfor katmaktadır. Basit ve kullanışlı bir arayüze sahip olan Dockge, düşük sistem kaynak kullanımıyla da dikkat çeker. Bu sayede, Docker konteynerlarınızı zahmetsizce izleyip yönetebilirsiniz.

### Dockge Kurulumu

Dockge kurulumu oldukça basittir. Terminale aşağıdaki komutları girerek kurulum işlemini tamamlayabilirsiniz:

```
# Stacks ve Dockge için gerekli dizinleri oluşturun
mkdir -p /opt/stacks /opt/dockge
cd /opt/dockge

# compose.yaml dosyasını indirin
curl https://raw.githubusercontent.com/louislam/dockge/master/compose.yaml --output compose.yaml

# Sunucuyu başlatın
docker compose up -d
```
Eğer Docker Compose V1 veya Podman kullanıyorsanız bununla çalıştırabilirsiniz:
```
# docker-compose up -d
```

Kurulum tamamlandıktan sonra, Dockge paneline tarayıcınız üzerinden sunucunuzun IP adresiyle erişebilirsiniz. Aşağıdaki bağlantıya giderek panelinize ulaşabilirsiniz:

```
https://<sunucu-ip-adresi>:5001
```

Bu arayüz üzerinden Docker konteynerlarınızı kolaylıkla yönetebilir, başlatma, durdurma ve izleme gibi işlemleri hızlıca gerçekleştirebilirsiniz.