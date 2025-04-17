# Projeto de estação meteorológica

O repositório [nuvem](https://github.com/estacao-meteorologica/nuvem) contém a programação para rodar as aplicações com Docker Compose. Para tal, é preciso criar arquivos sensíveis ao sistema, onde o formato é bastante simples: na primeira linha, informar o valor a ser copiado para o contêiner.

1. `secret-tsdb-username`: nome do operador do TSDB;
1. `secret-tsdb-password`: senha do operador do TSDB; 
1. `secret-tsdb-admin-token`: *token* do administrador do TSDB.

O repositório [software](https://github.com/estacao-meteorologica/software) é submódulo do repositório [nuvem](https://github.com/estacao-meteorologica/nuvem). Além dos arquivos anteriores, é preciso também o arquivo `software/.env` com os seguintes valores:

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
