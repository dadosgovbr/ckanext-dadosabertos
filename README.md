# CKANext DadosAbertos
Plugin / Tema do Portal de Dados Abertos do Governo Federal - Brasil

## Requisitos

- CKAN 2.5.x / 2.6.x
- Um grupo criado com o "name" igual "dados-em-destaque"
- Plugin: ckanext-scheming


## Instalação ckanext-dadosgovbr

Ative o virtualenv:
```
# Entre no usuário onde o CKAN foi instalado
su ckan

# Ative o virtualenv
. /usr/lib/ckan/default/bin/activate 

# Acesse o diretório de plugins
cd /usr/lib/ckan/default/src
```

Instale o ckanext-dadosgovbr e as dependências:
```
# Instale o ckanext-dadosgovbr
pip install -e git+https://github.com/dadosgovbr/ckanext-dadosabertos.git#egg=ckanext-dadosabertos

# Instale as dependências
pip install -r /usr/lib/ckan/default/src/ckanext-dadosabertos/pip-requirements.txt

# Configure o plugin
cd /usr/lib/ckan/default/src/ckanext-dadosabertos && python setup.py develop
```


## Configuração adicional

### Wordpress
- O Wordpress precisa estar na versão 4.7 ou superior.
- O plugin [WP-API/rest-filter](https://github.com/WP-API/rest-filter) precisa estar instalado e ativado no Wordpress.
- Adicione a URL do seu Wordpress em "get_domain()" no arquivo `/usr/lib/ckan/default/src/ckanext-dadosabertos/ckanext/dadosabertos/helpers/wordpress.py`

### Scheming
Adicione no arquivo `/etc/ckan/default/development.ini` as seguintes linhas, abaixo da definição dos plugins:
```
scheming.dataset_schemas = ckanext.dadosabertos:schema_aplicativo.json
			   ckanext.dadosabertos:schema_inventario.json
			   ckanext.dadosabertos:schema_concurso.json
```
