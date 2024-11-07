Eğer sunucunuzda bir sanal Linux masaüstü çalıştırmak istiyorsanız, Webtop tam size göre bir araç olabilir. Webtop, çok sayıda Linux dağıtımı ve masaüstü ortamı seçeneği sunarak, hızlı ve kolayca sanal masaüstünüze bağlanmanızı sağlar. Ayrıca, web tabanlı bir VNC arayüzü üzerinden rahatlıkla kullanabileceğiniz bir bağlantı imkanı sunar.

### Webtop Kurulum Aşamaları

Webtop'u kurmak için `compose.yml` dosyasını aşağıdaki gibi yapılandırın ve terminalde çalıştırın:

```
services:
  webtop:
    image: lscr.io/linuxserver/webtop:latest
    container_name: webtop
    security_opt:
      - seccomp:unconfined #opsiyonel
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Etc/UTC
      - SUBFOLDER=/ #opsiyonel
      - TITLE=Webtop #opsiyonel
    volumes:
      - /path/to/data:/config
      - /var/run/docker.sock:/var/run/docker.sock #opsiyonel
    ports:
      - 3000:3000
      - 3001:3001
    devices:
      - /dev/dri:/dev/dri #opsiyonel
    shm_size: "1gb" #opsiyonel
    restart: unless-stopped
```

### Port Ayarları
Webtop’un arayüzüne erişmek için kullanılan varsayılan portlar 3000 (HTTP) ve 3001 (HTTPS) olarak ayarlanmıştır. Bu port numaralarını ihtiyaçlarınıza göre sol kısımdaki değerleri değiştirerek özelleştirebilirsiniz.

### Desteklenen Sürümler ve Masaüstü Ortamları
Webtop, çeşitli Linux dağıtımları ve masaüstü ortamları için farklı sürümler sunmaktadır. İşte desteklenen masaüstü ortamları:

| Tag          | Dağıtım ve Masaüstü Ortamı           |
|--------------|--------------------------------------|
| latest       | XFCE Alpine                          |
| ubuntu-xfce  | XFCE Ubuntu                          |
| fedora-xfce  | XFCE Fedora                          |
| arch-xfce    | XFCE Arch                            |
| debian-xfce  | XFCE Debian                          |
| alpine-kde   | KDE Alpine                           |
| ubuntu-kde   | KDE Ubuntu                           |
| ...          | ...                                  |

Her bir sürüm için `compose.yml` dosyasında `image` satırında ilgili sürüm etiketiyle seçiminizi yapabilirsiniz. Örneğin, Ubuntu ve KDE masaüstünü tercih ediyorsanız `lscr.io/linuxserver/webtop:ubuntu-kde` etiketini kullanabilirsiniz.

Daha fazla bilgi ve ayrıntılı kurulum rehberi için [Webtop dökümantasyonunu](https://docs.linuxserver.io/images/docker-webtop/#supported-architectures) ziyaret edebilirsiniz.