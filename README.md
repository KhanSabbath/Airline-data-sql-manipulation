# 🛫 Airline Data Analysis

Análise exploratória de dados de companhias aéreas usando **SQL** e **Python**, com foco em padrões de voos, rotas e receitas.

## Sobre o Projeto

Este projeto realiza uma análise completa de dados de voos armazenados em um banco de dados SQLite. A investigação inclui:

- **Hubs aéreos**: Identificação de aeroportos com maior movimento
- **Rotas mais utilizadas**: Análise das combinações de voos mais frequentes
- **Cálculo de distâncias**: Uso da fórmula de Haversine para calcular distâncias entre cidades
- **Análise de receita**: Distribuição de ganhos por classe de passagem (fare conditions)

## Estrutura do Banco de Dados

### Tabelas Principais

| Tabela | Descrição | Campos Relevantes |
|--------|-----------|-------------------|
| `flights` | Registro de todos os voos | `flight_id`, `departure_airport`, `arrival_airport`, `actual_departure`, `actual_arrival`, `aircraft_code`, `status` |
| `airports_data` | Informações sobre aeroportos | `airport_code`, `city`, `coordinates` |
| `aircrafts_data` | Dados de aeronaves | `aircraft_code`, `range` |
| `ticket_flights` | Informações de passagens | `flight_id`, `amount`, `fare_conditions` |

## Principais Análises

### 1. **Aeroportos com Maior/Menor Movimento**
Identifica os 5 aeroportos com mais e menos voos de saída, utilizando `ROW_NUMBER()` para ranking.

### 2. **Rotas Mais Utilizadas**
Agrupa voos pelas cidades de partida e chegada, revelando os trajetos mais relevantes (TOP 10).

### 3. **Distância de Rotas**
Calcula a distância entre cidades usando a **fórmula de Haversine**:
```
distance = 2 * R * ASIN(SQRT(sin²((Δlat)/2) + cos(lat1) * cos(lat2) * sin²((Δlon)/2)))
```
onde R = 6371 km (raio da Terra)

### 4. **Análise de Receita**
Agrupa passagens por classe de serviço, calculando:
- Total de passagens vendidas
- Preço médio por passagem
- Receita total por classe

## Tecnologias Utilizadas

- **Python 3.12+**
- **Pandas**: Processamento e manipulação de dados
- **SQLAlchemy**: ORM e interface SQL
- **ipython-sql**: Extensão para executar SQL direto em notebooks
- **Jupyter/IPykernel**: Ambiente interativo de análise
- **NumPy**: Computações numéricas e álgebra linear
- **Matplotlib**: Visualização de dados
- **SQLite**: Banco de dados embutido

## Instalação

### Pré-requisitos
- Python 3.12+
- pip ou uv (gerenciador de pacotes)

### Instalação das Dependências

```bash
# Ativar o ambiente virtual
source .venv/bin/activate

# Instalar dependências via pip
pip install -r requirements.txt

# Ou inicializar com uv (recomendado)
uv sync
```

## Como Usar

1. **Ativar o ambiente virtual**:
   ```bash
   source .venv/bin/activate
   ```

2. **Abrir o notebook**:
   ```bash
   jupyter notebook main.ipynb
   ```

3. **Executar as análises**:
   - Navegar pelas células do notebook
   - Cada célula contém uma análise específica
   - Os resultados são exibidos em tabelas e visualizações

## Saídas Esperadas

- Tabelas DataFrames com dados agregados
- Ranking de aeroportos e rotas
- Visualizações de distribuições de distância
- Análise de receita por classe de passagem

## Conceitos SQL Utilizados

- **JOIN**: Combinação de múltiplas tabelas
- **GROUP BY + Agregações**: Contagens, somas e médias
- **Window Functions**: `ROW_NUMBER()` para rankings
- **Subqueries**: Cálculos em cascata
- **Temporary Tables**: Tabelas de trabalho temporárias
- **Índices**: Otimização de queries
- **CTEs (Common Table Expressions)**: Organização com WITH

## Notas de Aprendizado

Este projeto foi desenvolvido como estudo de:
- Manipulação avançada de SQL (SQLite)
- Análise exploratória de dados (EDA)
- Integração Python + SQL
- Uso de extensões IPython para SQL interativo
- Aplicação de fórmulas matemáticas em consultas SQL

## Estrutura de Arquivos

```
.
├── main.ipynb              # Notebook principal com análises
├── data/
│   └── travel.sqlite       # Banco de dados SQLite
├── pyproject.toml          # Configuração do projeto
├── README.md               # Este arquivo
└── .venv/                  # Ambiente virtual Python
```

## Referências

- [Fórmula de Haversine - Wikipedia](https://pt.wikipedia.org/wiki/Fórmula_de_haversine)
- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)
- [iPython-SQL GitHub](https://github.com/cathaysia/ipython-sql)
- [Pandas Documentation](https://pandas.pydata.org/)

## Licença

Este projeto é de uso educacional e estudo pessoal.

---

**Última atualização**: Fevereiro de 2026