# API Kullanım Rehberi

Bu doküman, farklı alanlarda bilgi sağlayan bir API sistemi hakkında bilgi sunar. Aşağıdaki API servisleri, Türkiye'deki son depremlerden döviz kurlarına, lig sıralamalarından sistem çalışma süresine kadar geniş bir yelpazede veri sunmaktadır. API'lerin tüm detaylarına ve kullanım talimatlarına erişmek için [https://api.gokhanozen.top](https://api.gokhanozen.top) adresini ziyaret edebilirsiniz.

## Deprem API
Türkiye'deki en güncel depremler hakkında gerçek zamanlı bilgi sağlar. Depremlerin konumu, büyüklüğü, derinliği ve zamanı gibi detaylara ulaşabilirsiniz.

**API URL**: `https://api.gokhanozen.top/kandiliearthquake`

Örnek kullanım:
```json
{
  "datainfo": {
    "last_earthquake_location": "KARTAL-(KAHRAMANMARAS)",
    "last_earthquake_magnitude": "2.4",
    "last_earthquake_time": "2024.10.08 00:40:27",
    "next_check": "2024-10-08 02:17:38",
    "total_earthquakes": 499
  },
  "earthquakes": [
    {
      "date": "2024.10.08",
      "depth_km": "5.4",
      "gmaps": "https://www.google.com/maps?q=37.5122,37.1610",
      "latitude": "37.5122",
      "location": "KARTAL-(KAHRAMANMARAS)",
      "longitude": "37.1610",
      "magnitude_md": "-.-",
      "magnitude_ml": "2.4",
      "magnitude_mw": "-.-",
      "solution_quality": "İlksel",
      "time": "00:40:27"
    }
  ]
}
```

## Uptime API
Sisteminizin ne kadar süredir aktif olduğunu ve kaç API isteği alındığını gösterir. Sistemlerinize dair çalışma sürelerini takip etmek için kullanabilirsiniz.

**API URL**: `https://api.gokhanozen.top/uptime`

Örnek kullanım:
```json
{
  "application_name": "Uptime API",
  "current_time": "2024-10-08 02:10:59",
  "request_count": 2,
  "start_time": "2024-10-08 02:08:53",
  "uptime": 125.525665521622,
  "uptime_in_human_readable": "0 saat, 2 dakika, 5 saniye"
}
```

## Kur API
Döviz kurlarını sorgulamanıza olanak tanır. Farklı dövizlerin güncel değerlerine erişebilirsiniz.

**API URL**: `https://api.gokhanozen.top/kur`

Örnek kullanım:
```json
{
  "USD": "27.50",
  "EUR": "30.10",
  "GBP": "35.20"
}
```

## Ligler API
Farklı liglerdeki güncel puan durumları hakkında bilgi sağlar. Türkiye Süper Ligi, Avrupa ligleri ve daha fazlası hakkında detaylı puan bilgilerine ulaşabilirsiniz.

### Süper Lig
**API URL**: `https://api.gokhanozen.top/standings/superlig`

Örnek kullanım:
```json
{
  "rank": "1",
  "team": "Galatasaray",
  "matches_played": "8",
  "wins": "7",
  "draws": "1",
  "losses": "0",
  "goals_scored": "21",
  "goals_against": "8",
  "goal_difference": "13",
  "points": "22",
  "logo_url": "https://example.com/logo_galatasaray.png"
}
```

### Diğer Ligler
- **1. Lig**: `https://api.gokhanozen.top/standings/lig1`
- **Şampiyonlar Ligi**: `https://api.gokhanozen.top/standings/sampiyonlar_ligi`
- **Avrupa Ligi**: `https://api.gokhanozen.top/standings/avrupa_ligi`
- **Konferans Ligi**: `https://api.gokhanozen.top/standings/konferans_ligi`
- **Premier Lig**: `https://api.gokhanozen.top/standings/premier_lig`
- **La Liga**: `https://api.gokhanozen.top/standings/la_liga`
- **Serie A**: `https://api.gokhanozen.top/standings/serie_a`

API'yi daha detaylı incelemek ve projelerinizde kullanmak için [https://api.gokhanozen.top](https://api.gokhanozen.top) adresine göz atabilirsiniz.
