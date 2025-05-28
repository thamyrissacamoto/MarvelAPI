# API Marvel

Projeto em Python para extrair dados da API pública da Marvel (https://developer.marvel.com), com suporte à autenticação segura, paginação automática, cache com ETag e exportação em CSV.

## Funcionalidades

- Autenticação dinâmica com chaves públicas e privadas
- Paginação automática em endpoints com grandes volumes
- Cache inteligente com suporte a ETag
- Extração de relacionamentos
- Exportação de dados para arquivos .csv

## Instalação

### 1. Clonar ou abrir no Google Colab

Você pode copiar o código ou abrir diretamente no Google Colab.

### 2. Armazenar suas chaves da API

Cadastre-se em https://developer.marvel.com e receba:

- public_key
- private_key

### Google Colab
Armazene nas variáveis de ambiente do Colab.

### Visual Studio Code
Instale:
```python
!pip install dotenv
```
Crie um arquivo `.env` e armazene:

```python
public_key=SUA_PUBLIC_KEY
private_key=SUA_PRIVATE_KEY.
```

### Autenticação

A autenticação é realizada da seguinte forma:

- ts: timestamp da requisição
- apikey: sua chave pública
- hash: MD5 do ts + private_key + public_key

### Requisições com ETag

A função `marvel_request()` faz chamadas com controle de ETag. Se o servidor retornar 304, os dados armazenados localmente são reutilizados.

### Extração de dados (endpoint principal)

A função `get_all_data()` percorre todas as páginas de um endpoint com paginação automática (`limit` e `offset`) e salva os dados em CSV.

### Coleta de relacionamentos

A função `get_relationships()` busca os dados relacionados e salva as associações em um CSV.
