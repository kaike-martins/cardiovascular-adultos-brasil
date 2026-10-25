# ❤️ Mortalidade Cardiovascular em Adultos de 15 a 64 Anos no Brasil (2010–2023)

Análise epidemiológica completa sobre a mortalidade por doenças do aparelho circulatório em adultos de 15 a 64 anos no Brasil, cobrindo o período de 2010 a 2023. O projeto foi desenvolvido como atividade acadêmica no curso de Ciência de Dados da FMU São Paulo, sob orientação da Profa. Luciana Lugli, e resultou em convite para co-autoria em artigo científico.

![Excel](https://img.shields.io/badge/Excel-217346?style=flat-square&logo=microsoftexcel&logoColor=white)
![Power Query](https://img.shields.io/badge/Power_Query-217346?style=flat-square&logo=microsoftexcel&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![PowerPoint](https://img.shields.io/badge/PowerPoint-B7472A?style=flat-square&logo=microsoftpowerpoint&logoColor=white)
![Fonte](https://img.shields.io/badge/Fonte-SIM%2FDATASUS-4B1D72?style=flat-square)

---

## 📋 Contexto

As doenças cardiovasculares são a principal causa de morte no Brasil há décadas, respondendo por aproximadamente 27% de todos os óbitos adultos. Este projeto foca na faixa etária de 15 a 64 anos — a população economicamente ativa — onde cada morte representa anos de vida perdidos prematuramente.

O período de 14 anos analisado (2010–2023) permite identificar tendências de longo prazo, avaliar o impacto da pandemia de COVID-19 sobre a mortalidade cardiovascular e mapear desigualdades regionais, etárias e de gênero com rigor epidemiológico.

> **Nota sobre os dados:** todos os dados utilizados neste projeto são integralmente públicos, provenientes do SIM/DATASUS e do IBGE. Não há qualquer informação confidencial ou identificação individual em nenhum dos arquivos.

---

## 🎯 Perguntas respondidas

- Qual foi a evolução do número de óbitos cardiovasculares entre 2010 e 2023?
- Quais causas (CID-10) concentram a maior parte das mortes?
- Existe desigualdade expressiva entre sexos, faixas etárias e raças?
- Quais regiões apresentam maior taxa de mortalidade por 100.000 habitantes?
- Como a pandemia de COVID-19 afetou a mortalidade cardiovascular em 2020 e 2022?
- Onde as pessoas morrem — dentro ou fora do hospital?

---

## 📊 Principais achados

- **1.436.691 óbitos** registrados no período total — média de mais de **281 mortes por dia**
- **I21 — Infarto Agudo do Miocárdio** é a causa dominante: **31,7%** de todos os óbitos cardiovasculares na faixa 15–64 anos
- A faixa **60–64 anos** concentra **30,6%** das mortes; o risco cresce de forma exponencial a partir dos 40 anos — **90,1% dos óbitos ocorrem em maiores de 40 anos**
- **Homens morrem 1,63x mais** do que mulheres em todas as faixas etárias e em todos os 14 anos do estudo
- A **Região Sudeste** lidera em taxa ajustada por 100k habitantes (82,0); comparação regional sem ajuste é metodologicamente inadequada
- **~24,8% dos óbitos** ocorrem fora do hospital (domicílio + via pública), indicando eventos súbitos sem acesso a socorro a tempo
- **2020** apresenta queda brusca nos registros cardiovasculares — atribuída ao deslocamento de causa básica para COVID-19, não a redução real da doença
- **2022** apresenta pico acima da tendência histórica — excesso de mortalidade associado a efeitos sistêmicos pós-pandemia
- Crescimento de **+29,6%** nos óbitos de raça/cor Preta e Parda entre 2010 e 2023 — sinal de desigualdade estrutural crescente

---

## 🗂️ Estrutura do projeto

```
cardiovascular-adultos-brasil/
│
├── README.md
├── dados/
│   ├── cv_total_15a64.csv               # Total de óbitos por ano
│   ├── cv_cid_15a64.csv                 # Óbitos por categoria CID-10
│   ├── cv_faixaetaria_ano_15a64.csv     # Óbitos por faixa etária e ano
│   ├── cv_faixaetaria_sexo_15a64.csv    # Óbitos por faixa etária e sexo (acumulado)
│   ├── cv_local_15a64.csv               # Óbitos por local de ocorrência
│   ├── cv_raca_15a64.csv                # Óbitos por raça/cor
│   ├── cv_regiao_15a64.csv              # Óbitos por região
│   ├── cv_sexo_15a64.csv                # Óbitos por sexo
│   └── pop_regiao_taxa_15a64.csv        # População IBGE e taxa por 100k hab.
│
├── analise/
│   └── Cardiovascular_adultos_15a64_anos_ANALISE.xlsx   # Análise completa com gráficos
│
├── dashboard/
│   └── cardiovascular_15a64_dashboard.pbix              # Dashboard interativo Power BI
│
└── apresentacao/
    └── cardiovascular_15a64_anos.pptx                   # Apresentação (14 slides)
```

---

## 🛠️ Ferramentas e metodologia

**Coleta de dados**
Os dados de óbitos foram extraídos do SIM — Sistema de Informações sobre Mortalidade (MS/SVSA/CGIAE) via DATASUS/TabNet, utilizando o CID-10 Capítulo IX (Doenças do Aparelho Circulatório), com filtro de faixa etária de 15 a 64 anos. Os dados populacionais foram obtidos do IBGE (Tabela 7358 — Projeção da População por sexo e idade). Data de atualização dos dados: 02/12/2025.

**CIDs excluídos**
Doenças cerebrovasculares (I60–I69) e aneurisma da aorta (I71) foram excluídos do escopo analítico e registrados como nota metodológica. O impacto quantitativo dessa exclusão constitui uma limitação a ser considerada na interpretação dos totais.

**Tratamento no Excel**
Importação dos arquivos CSV via Power Query, transformação para formato longo (unpivot), tratamento de encoding, remoção de registros inconsistentes, cálculo de taxa de mortalidade por 100.000 habitantes com denominador IBGE T7358.

**Análise no Excel**
Construção de 8 gráficos analíticos cobrindo evolução temporal, distribuição por CID-10, perfil etário, comparativo por sexo, distribuição regional por taxa ajustada, local de ocorrência, raça/cor e impacto pandêmico.

**Dashboard no Power BI**
Carregamento de 9 tabelas em formato longo, modelagem de relacionamentos em esquema estrela (todos muitos-para-um conectados à tabela de total por ano), criação de medidas DAX para KPIs dinâmicos, e construção de dashboard de 4 páginas com segmentador de ano interativo sincronizado entre páginas.

**Apresentação**
14 slides com identidade visual profissional, cobrindo contextualização, metodologia, panorama geral, perfil etário, perfil por sexo, distribuição regional, principais causas, local de ocorrência, impacto da pandemia, implicações para enfermagem, limitações metodológicas, síntese dos achados e referências.

---

## 📄 Páginas do dashboard

| Página | Conteúdo |
|---|---|
| **Visão Geral** | KPIs totais, evolução 2010–2023, taxa regional por 100k, distribuição por sexo |
| **Perfil das Vítimas** | Distribuição etária, comparativo M/F por faixa, evolução por faixa etária |
| **Causas e Local** | Top 10 CIDs, local de ocorrência, evolução das principais causas |
| **Raça e Contexto** | Evolução por raça/cor, impacto pandêmico, distribuição acumulada |

---

## ⚠️ Limitações dos dados

1. CIDs excluídos (I60–I69 e I71) — impacto quantitativo não calculado nesta versão
2. Classificação de raça/cor em óbitos súbitos é preenchida por terceiros — possível viés classificatório entre Parda e Preta
3. O SIM registra onde o óbito foi **constatado**, não onde o evento se iniciou — mortes pré-hospitalares podem estar subestimadas
4. Dados populacionais do IBGE são projeções intercensitárias para anos não censitários (exceto 2010 e 2022)
5. O período pandêmico (2020–2022) apresenta interferência no registro de causas básicas — variações nesses anos devem ser interpretadas com cautela adicional
6. Análise baseada integralmente em dados secundários do SIM/DATASUS — qualidade final depende da completude das Declarações de Óbito

---

## 📚 Fontes

- **SIM/DATASUS** — Sistema de Informações sobre Mortalidade (MS/SVSA/CGIAE): [datasus.saude.gov.br](https://datasus.saude.gov.br)
- **IBGE Tabela 7358** — Projeção da População por sexo e idade: [sidra.ibge.gov.br](https://sidra.ibge.gov.br)
- **CID-10 Capítulo IX** — Doenças do Aparelho Circulatório: Organização Mundial da Saúde, 1992
- **Manual de Instruções para o Preenchimento da Declaração de Óbito** — Ministério da Saúde, 4ª ed., 2011
- RIBEIRO, A. L. P. et al. Cardiovascular health in Brazil: Trends and Perspectives. *Circulation*, v. 133, n. 4, p. 422–433, 2016.
- SCHMIDT, M. I. et al. Chronic non-communicable diseases in Brazil: burden and current challenges. *The Lancet*, v. 377, n. 9781, p. 1949–1961, 2011.

---

## 👤 Autor

**Kaike Martins**
Estudante de Ciência de Dados — FMU São Paulo
Orientação: Profa. Luciana Lugli

[LinkedIn](https://linkedin.com/in/kaikemarttins) · [GitHub](https://github.com/kaike-martins)
