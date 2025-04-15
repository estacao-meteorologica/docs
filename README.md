# Projeto de estação meteorológica

O repositório [nuvem](https://github.com/estacao-meteorologica/nuvem) contém a programação para rodar as aplicações em nuvem. Para tal, é preciso criar arquivos sensíveis ao sistema, onde o formato é bastante simples: na primeira linha, informar o valor a ser copiado para o contêiner.

1. `secret-tsdb-username`: nome do operador do TSDB.;
1. `secret-tsdb-password`: senha do operador do TSDB; 
1. `secret-tsdb-admin-token`: *token* do administrador do TSDB.
