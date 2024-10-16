# Boas vindas ao repositório do projeto Job Insights!

Projeto desenvolvido como requisito parcial para a conclusão do módulo de Ciência da Computação do curso de Desenvolvimento Web da Trybe. Neste projeto, são implementadas análises a partir de um conjunto de dados sobre empregos utilizando **Python**. As implementações são incorporadas a um aplicativo Web desenvolvido com **Flask**. Também são escritos testes para a implementação de uma análise de dados.

Os dados foram extraídos do site [Glassdoor](https://www.glassdoor.com.br/) e obtidos através do [Kaggle](https://www.kaggle.com/atharvap329/glassdoor-data-science-job-data), plataforma que disponibliza datasets para cientistas de dados.

---

## Sumário

- [Sumário](#sumário)
- [Habilidades](#habilidades)
- [Estrutura](#estrutura)
- [Data de Entrega](#data-de-entrega)
- [Testes](#testes)
- [Requisitos](#requisitos)
  - [Requisitos obrigatórios](#requisitos-obrigatórios)
      - [1 - Implemente a função `read`](#1---implemente-a-função-read)
      - [2 - Implemente a função `get_unique_job_types`](#2---implemente-a-função-get_unique_job_types)
      - [3 - Implemente a função `get_unique_industries`](#3---implemente-a-função-get_unique_industries)
      - [4 - Implemente a função `get_max_salary`](#4---implemente-a-função-get_max_salary)
      - [5 - Implemente a função `get_min_salary`](#5---implemente-a-função-get_min_salary)
      - [6 - Implemente a função `filter_by_job_type`](#6---implemente-a-função-filter_by_job_type)
      - [7 - Implemente a função `filter_by_industry`](#7---implemente-a-função-filter_by_industry)
      - [8 - Implemente a função `matches_salary_range`](#8---implemente-a-função-matches_salary_range)
      - [9 - Implemente a função `filter_by_salary_range`](#9---implemente-a-função-filter_by_salary_range)
      - [10 - Implemente um teste para a função `sort_by`](#10---implemente-um-teste-para-a-função-sort_by)
  - [Requisitos bônus](#requisitos-bônus)
      - [11 - Implemente a página de um job](#11---implemente-a-página-de-um-job)

---

## Habilidades

- Utilização do terminal interativo do Python.
- Utilização de estruturas condicionais e de repetição.
- Utilização de funções built-in do Python.
- Utilização de tratamento de exceções.
- Manipulação de arquivos.
- Escrita de funções.
- Escrita de testes com Pytest.
- Escrita de módulos próprios e importação destes módulos em outros códigos.

---

### Estrutura

Este repositório já contém um _template_ com a estrutura de diretórios e arquivos:

```
.
├── README.md
├── dev-requirements.txt
├── feedback.jsonc
├── requirements.txt
├── src
│   ├── app.py
│   ├── insights.py
│   ├── jobs.csv
│   ├── jobs.py
│   ├── more_insights.py
│   ├── routes_and_views.py
│   ├── sorting.py
│   └── templates
│       ├── base.jinja2
│       ├── includes
│       │   └── nav.jinja2
│       ├── index.jinja2
│       ├── job.jinja2
│       └── list_jobs.jinja2
├── tests
│   ├── __init__.py
│   ├── mocks
│   │   ├── job_1.html
│   │   ├── jobs.csv
│   │   ├── jobs_with_industries.csv
│   │   ├── jobs_with_salaries.csv
│   │   └── jobs_with_types.csv
│   ├── sorting
│   │   ├── conftest.py
│   │   ├── mocks.py
│   │   └── test_sorting.py
│   ├── test_feedback.py
│   ├── test_flask_app.py
│   ├── test_insights.py
│   ├── test_jobs.py
│   ├── test_more_insights.py
│   └── test_routes_and_views.py
```

Na estrutura deste _template_, foram implementadas as funções necessárias, conforme requisitos descritos a seguir.


### Data de Entrega

- Foram `2` dias de projeto.
- Data de entrega para avaliação final do projeto: `10/12/2021 - 14:00h`.

---

#### Testes

Para executar os testes certifique-se de que os seguintes passos foram realizados;

1. **criar o ambiente virtual**

```bash
$ python3 -m venv .venv
```

2. **ativar o ambiente virtual**

```bash
$ source .venv/bin/activate
```

3. **instalar as dependências no ambiente virtual**

```bash
$ python3 -m pip install -r dev-requirements.txt
```

Com o seu ambiente virtual ativo, as dependências serão instaladas neste ambiente.
Quando precisar desativar o ambiente virtual, execute o comando "deactivate". Lembre-se de ativar novamente quando voltar a trabalhar no projeto.

O arquivo `dev-requirements.txt` contém todas as dependências que serão utilizadas no projeto, ele está agindo como se fosse um `package.json` de um projeto `Node.js`.

Com esta preparação feita, podemos executar os testes:

**Executar os testes**

```bash
$ python3 -m pytest
```

O arquivo `pyproject.toml` já configura corretamente o pytest. Entretanto, caso você tenha problemas com isso queira explicitamente uma saída completa, o comando é:

```bash
python3 -m pytest -s -vv
```

Caso precise executar apenas um arquivo de testes basta executar o comando:

```bash
python3 -m pytest tests/nomedoarquivo.py
```

Caso precise executar apenas uma função de testes basta executar o comando:

```bash
python3 -m pytest -k nome_da_func_de_tests
```

Se quiser saber mais sobre a instalação de dependências com `pip`, veja esse [artigo](https://medium.com/python-pandemonium/better-python-dependency-and-package-management-b5d8ea29dff1).

Além dos testes com o Pytest, você pode (e vai ser bem bacana) rodar a aplicação flask para visualizar no navegador o resultado do desenvolvimento das funções.
Para isso, digite o comando `flask run`, e acesse o site gerado pelo Flask em `http://localhost:5000`. No começo do desenvolvimento, você verá que muitas coisas não funcionam, mas conforme você for implementando os requisitos, perceberá que a aplicação web começa a utilizar suas implementações e passa a ganhar vida.

---

### Requisitos

#### Requisitos obrigatórios

##### 1 - Implemente a função `read`
local: `src/jobs.py`

Para começarmos a processar os dados, devemos antes carregá-los em nossa aplicação. Esta função será responsável por abrir o arquivo CSV e retornar os dados no formato de uma lista de dicionários.

- A função deve receber um _path_ (uma string com o caminho para um arquivo).
- A função deve abrir o arquivo e ler seus conteúdos.
- A função deve tratar o arquivo como CSV.
- A função deve retornar uma lista de dicionários, onde as chaves são os cabeçalhos de cada coluna e os valores correspondem a cada linha.

✍️ Teste manual: abra um terminal Python importando estas funções através do comando `python3 -i src/jobs.py` e invoque a função utilizando diferentes _paths_.

**🤖 O que será verificado pelo avaliador:**

- A função abre o arquivo passado como parâmetro
- A função retorna uma lista de dicionários
- A função retorna a quantidade correta de itens na lista
- Nos dicionários retornados pela função, as chaves correspondem aos cabeçalhos do arquivo

##### 2 - Implemente a função `get_unique_job_types`
local: `src/insights.py`

Agora que temos como carregar os dados, podemos começar a extrair informação deles. Primeiro, vamos identificar quais tipos de empregos existem.

- A função deve receber o _path_ do arquivo csv com os dados.
- A função deve invocar a função `jobs.read` com o _path_ recebido para obter os dados.
- A função deve retornar uma lista de valores únicos presentes na coluna `job_type`.

**🤖 O que será verificado pelo avaliador:**

- A função carrega os dados do arquivo recebido como parâmetro
- A função retorna a quantidade correta de valores
- A função retorna os valores corretos
- A função desconsidera valores vazios

##### 3 - Implemente a função `get_unique_industries`
local: `src/insights.py`

Da mesma forma, agora iremos identificar quais indústrias estão representadas nesse conjunto de dados.

- A função deve obter os dados da mesma forma que o requisito 2.
- A função deve retornar uma lista de valores únicos presentes na coluna `industry`.
- A função desconsidera valores vazios

**🤖 O que será verificado pelo avaliador:**

- A função carrega os dados do arquivo recebido como parâmetro
- A função retorna a quantidade correta de valores
- A função retorna os valores corretos

##### 4 - Implemente a função `get_max_salary`
local: `src/insights.py`

Os dados apresentam faixas salariais para cada emprego exibido. Vamos agora encontrar o maior valor de todas as faixas.

- A função deve obter os dados da mesma forma que o requisito 2.
- A função deve ignorar os valores ausentes.
- A função deve retornar *um valor inteiro* com o maior salário presente na coluna `max_salary`.

**🤖 O que será verificado pelo avaliador:**

- A função carrega os dados do arquivo recebido como parâmetro
- A função retorna o valor correto

##### 5 - Implemente a função `get_min_salary`
local: `src/insights.py`

Os dados apresentam faixas salariais para cada emprego exibido. Vamos agora encontrar o menor valor de todas as faixas.

- A função deve obter os dados da mesma forma que o requisito 2.
- A função deve ignorar os valores ausentes.
- A função deve retornar *um valor inteiro* com o menor salário presente na coluna `min_salary`.

**🤖 O que será verificado pelo avaliador:**

- A função carrega os dados do arquivo recebido como parâmetro
- A função retorna o valor correto

##### 6 - Implemente a função `filter_by_job_type`
local: `src/insights.py`

Os empregos estão listados em um aplicativo web. Para permitir que a pessoa usuária possa filtrar os empregos por tipo de emprego, vamos precisar implementar esse filtro.

- A função deve receber uma lista de dicionários `jobs` como primeiro parâmetro.
- A função deve receber uma string `job_type` como segundo parâmetro.
- A função deve retornar uma lista com todos os empregos onde a coluna `job_type` corresponde ao parâmetro `job_type`.

**🤖 O que será verificado pelo avaliador:**

- A função retorna a quantidade correta de valores
- A função retorna os valores corretos
- A função retorna os valores na ordem correta
- A função retorna uma lista vazia para `job_types` ausentes nos `jobs` recebidos

##### 7 - Implemente a função `filter_by_industry`
local: `src/insights.py`

Do mesmo modo, o aplicativo precisa permitir uma filtragem por indústria. Vamos precisar implementar esse filtro também.

- A função deve receber uma lista de dicionários `jobs` como primeiro parâmetro.
- A função deve receber uma string `industry` como segundo parâmetro.
- A função deve retornar uma lista de dicionários com todos os empregos onde a coluna `industry` corresponde ao parâmetro `industry`.

**🤖 O que será verificado pelo avaliador:**

- A função retorna a quantidade correta de valores
- A função retorna os valores corretos
- A função retorna os valores na ordem correta
- A função retorna uma lista vazia para `job_types` ausentes nos `jobs` recebidos

##### 8 - Implemente a função `matches_salary_range`
local: `src/insights.py`

O aplicativo vai precisar filtrar os empregos por salário também. Como uma função auxiliar, implemente `matches_salary_range` para conferir que o salário procurado está dentro da faixa salarial daquele emprego. Vamos aproveitar também para conferir se a faixa salarial faz sentido -- isto é, se o valor mínimo é menor que o valor máximo.

- A função deve receber um dicionário `job` como primeiro parâmetro, com as chaves `min_salary` e `max_salary`.
- A função deve receber um inteiro `salary` como segundo parâmetro.
- A função deve lançar um erro `ValueError` nos seguintes casos:
  - alguma das chaves `min_salary` ou `max_salary` estão *ausentes* no dicionário;
  - alguma das chaves `min_salary` ou `max_salary` tem valores não-numéricos;
  - o valor de `min_salary` é maior que o valor de `max_salary`;
  - o parâmetro `salary` tem valores não-numéricos;
- A função deve retornar `True` se o salário procurado estiver dentro da faixa salarial ou `False` se não estiver.

**🤖 O que será verificado pelo avaliador:**

- A função retorna o booleano correto
- A função lança um `ValueError` se o valor de `min_salary` for maior que o valor de `max_salary`
- A função lança um `ValueError` se as chaves `min_salary` ou `max_salary` tiverem valores não numéricos
- A função lança um `ValueError` se o parâmetro `salary` tiver valor não numérico
- A função lança um `ValueError` se as chaves `min_salary` ou `max_salary` estiverem ausentes no dicionário

##### 9 - Implemente a função `filter_by_salary_range`
local: `src/insights.py`

Agora vamos implementar o filtro propriamente dito. Para esta filtragem, podemos usar a função auxiliar implementada no requisito anterior -- tomando o cuidado de descartar os empregos que apresentarem faixas salariais inválidas.

- A função deve receber uma lista de dicionários `jobs` como primeiro parâmetro.
- A função deve receber um inteiro `salary` como segundo parâmetro.
- A função deve ignorar os empregos com valores inválidos para `min_salary` ou `max_salary`.
- A função deve retornar uma lista com todos os empregos onde o salário `salary` estiver entre os valores da coluna `min_salary` e `max_salary`.

**🤖 O que será verificado pelo avaliador:**

- A função retorna a quantidade correta de valores
- A função retorna os valores corretos
- A função retorna os valores na ordem correta
- Empregos onde as chaves `min_salary` ou `max_salary` tiverem valores não numéricos devem ser ignorados
- Empregos onde o valor de `min_salary` for maior que o valor de `max_salary` devem ser ignorados

##### 10 - Implemente um teste para a função `sort_by`
local: `tests/sorting/test_sorting.py`

Por fim, espera-se que a pessoa usuária possa escolher um critério de ordenação para exibir os empregos. Já temos uma implementação para essa ordenação em `src/sorting.py`, mas queremos ter certeza de que ela funciona e, principalmente, que não deixará de funcionar conforme vamos implementando novos recursos. Precisamos então escrever um *teste*!

Esse teste deve se chamar `test_sort_by_criteria` e garantir que a função funciona segundo esta especificação:

- A função `sort_by` recebe dois parâmetros:
  - `jobs` uma lista de dicionários com os detalhes de cada emprego;
  - `criteria` uma string com uma chave para ser usada como critério de ordenação.
- O parâmetro `criteria` deve ter um destes valores: `min_salary`, `max_salary`, `date_posted`
- A ordenação para `min_salary` deve ser crescente, mas para `max_salary` ou `date_posted` devem ser decrescentes.
- Os empregos que não apresentarem um valor válido no campo escolhido para ordenação devem aparecer no final da lista.

> 📌 O **teste da Trybe** espera que o **seu teste** falhe em alguns casos. Nesse caso, o teste terá a saída `XFAIL` (ao invés de `PASS` ou `FAIL`), e isso significa que o requisito foi atendido ✔️

**🤖 O que será verificado pelo avaliador:**

- O teste rejeita implementações que aceitam critérios não especificados.
- O teste rejeita implementações que não ordenam corretamente.
- O teste rejeita implementações que não ordenam em ordem crescente quando o critério é `min_salary`.
- O teste aprova implementações corretas.


---

#### Requisitos bônus

##### 11 - Implemente a página de um job
local: `src/routes_and_views.py`

Para fechar com chave de ouro, que tal testar o quanto você aprendeu de Flask apenas vendo como fizemos as páginas de `index` e de `jobs`, e tentar criar uma página que irá exibir todas as informações de um job em específico?

- A função deve ser decorada com a rota `/job/<index>`.
- A função deve receber um parâmetro `index`.
- A função deve chamar a `read` para ter uma lista com todos os jobs.
- A função deve chamar a `get_job`, declarada no arquivo `src/more_insights.py`, para selecionar um job específico pelo `index`.
- A função deve renderizar o template `job.jinja2`, passando um parâmetro `job` contendo o job retornado pela `get_job`.

✍️ Teste manual: após criar a view, cheque se, na página que lista os jobs, aparecem links para jobs específicos nos números que identificam cada job. Ao clicar em um destes links, você deve ser levado a uma página que lista todas as informações do job.

**🤖 O que será verificado pelo avaliador:**

- A rota `/job/<index>` existe.
- A view `job` existe no arquivo `src/routes_and_views.py`, e recebe o parâmetro `index` (e somente ele).
- A página de cada um dos jobs deve retornar o status code 200.
- A página de um job específico (escolhido previamente) deve retornar o HTML exato esperado.

---
