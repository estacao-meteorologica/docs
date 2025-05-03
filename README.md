# Projeto de estação meteorológica

O projeto está organizado em vários repositórios.

## Nuvem

O repositório [nuvem](https://github.com/estacao-meteorologica/nuvem) contém a programação para rodar as aplicações com Docker Compose. Para tal, é preciso criar arquivos sensíveis ao sistema, onde o formato é bastante simples: na primeira linha, informar o valor a ser copiado para o contêiner.

1. `secret-tsdb-username`: nome do operador do TSDB;
1. `secret-tsdb-password`: senha do operador do TSDB; 
1. `secret-tsdb-admin-token`: *token* do administrador do TSDB.

## *Software*

O repositório [*software*](https://github.com/estacao-meteorologica/software) é submódulo do repositório [nuvem](https://github.com/estacao-meteorologica/nuvem). Além dos arquivos anteriores, é preciso também o arquivo `software/.env` com os seguintes valores:

1. `INFLUXDB_URL`: URL da API do TSDB;
1. `INFLUXDB_TOKEN`: *token* do administrador do TSDB, assim como em `secret-tsdb-admin-token`;
1. `INFLUXDB_ORG`: organização do TSDB;
1. `INFLUXDB_BUCKET`: *bucket* do TSDB;
1. `MQTT_BROKER`: endereço do broker MQTT;
1. `MQTT_PORT`: porta do broker MQTT;
1. `MQTT_CLIENT_ID`: identificador do cliente MQTT;
1. `MQTT_TOPIC`: tópico MQTT a ser assinado.

Exemplo:

```ini
INFLUXDB_URL=http://tsdb:8086/
INFLUXDB_TOKEN=my-token
MQTT_BROKER=mqtt-broker
```

## *Hardware*

O repositório [*hardware*](https://github.com/estacao-meteorologica/hardware) tem código projetado para [ESP32 da Expressif](https://www.espressif.com/en/products/socs/esp32) ([código](https://github.com/espressif/arduino-esp32)).

Há duas frentes de trabalho.

### C/C++

Na primeira abordagem, é usado código C/C++ nativo do Arduino, e possui as seguintes dependências:

1. [PubSubClient](https://pubsubclient.knolleary.net/)
1. [DallasTemperature](https://github.com/milesburton/Arduino-Temperature-Control-Library)
1. [OneWire](https://www.pjrc.com/teensy/td_libs_OneWire.html)
1. [TinyDHT sensor library](https://github.com/adafruit/TinyDHT)
1. [Adafruit BMP280 Library](https://github.com/adafruit/Adafruit_BMP280_Library)

### MicroPython

Em paralelo, há estudo de [MicroPython](https://docs.micropython.org/en/latest/esp32/quickref.html#), que requer o arquivo de configuração `.env` conforme o exemplo a seguir:

```ini
WIFI_SSID=em
WIFI_KEY=estacao-meteorologica
MQTT_CLIENT_ID=EMv0
MQTT_BROKER=em.sj.ifsc.edu.br
```

O arquivo `Makefile` contém todos os comandos necessários para instalar as dependências:

```sh
make
```

bem como instalar o código da aplicação:

```sh
make write
```
