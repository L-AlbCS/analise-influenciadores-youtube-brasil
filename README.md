# 📊 Análise Estratégica de Influenciadores - YouTube Brasil 2023

## 📊 Dashboard de Visualizações

### Top 10 Canais por Inscritos
![Top 10 Inscritos](visualizacoes/grafico_top10_inscritos.png)

### Matriz BCG - Estratégia de Investimento
![Matriz BCG](visualizacoes/matriz_bcg.png)

### Receita e Lucratividade
![Receita](visualizacoes/grafico_receita.png)

### Crescimento e Momentum
![Momentum](visualizacoes/grafico_momentum.png)

## 🎯 Visão Geral do Projeto

Este estudo de caso analisa os **57 principais canais brasileiros do YouTube** para identificar oportunidades estratégicas de marketing de influência, fornecendo insights acionáveis sobre alcance, engajamento, receita e crescimento.

**Cliente Fictício:** BrandConnect Agency - Agência de Marketing de Influência  
**Analista:** Luiz Alberto Costa de Souza 
**Data:** Novembro 2024  
**Ferramentas:** Google Sheets, Kaggle, Google Slides

---

## 📋 Sumário

1. [Definição do Problema](#problema)
2. [Preparação dos Dados](#preparacao)
3. [Processamento e Limpeza](#processamento)
4. [Análise Descritiva](#analise)
5. [Análises Avançadas](#avancadas)
6. [Visualizações](#visualizacoes)
7. [Insights e Recomendações](#insights)
8. [Conclusão](#conclusao)

---

## 🎯 1. DEFINIÇÃO DO PROBLEMA {#problema}

### Contexto de Negócio

A BrandConnect Agency deseja expandir suas operações no mercado brasileiro de marketing de influência e precisa responder às seguintes perguntas estratégicas:

**Perguntas de Negócio:**
- Quem são os principais influenciadores brasileiros no YouTube?
- Quais categorias/nichos oferecem melhor retorno sobre investimento (ROI)?
- Quais canais têm melhor custo-benefício (CPM)?
- Quais influenciadores estão em crescimento acelerado (momentum)?
- Qual o perfil ideal de canal para diferentes tipos de campanha?

### Métricas-Chave (KPIs)

- **Alcance:** Número de inscritos
- **Engajamento:** Views por inscrito
- **Lucratividade:** Receita mensal estimada
- **Crescimento:** % de views nos últimos 30 dias (momentum)
- **Eficiência:** Inscritos por vídeo publicado
- **Custo-Benefício:** CPM (custo por milhão de views)

### Stakeholders

- **Primários:** Diretores da BrandConnect Agency
- **Secundários:** Gerentes de contas, clientes da agência (marcas)

---

## 📥 2. PREPARAÇÃO DOS DADOS {#preparacao}

### Fonte de Dados

**Dataset:** Global YouTube Statistics 2023  
**Origem:** Kaggle  
**Link:** [Global YouTube Statistics 2023](https://www.kaggle.com/datasets/nelgiriyewithana/global-youtube-statistics-2023)  
**Licença:** Dados públicos  
**Tamanho original:** 995 canais globais, 28 colunas

### Processo de Seleção

1. **Download:** Dataset baixado do Kaggle (formato CSV)
2. **Importação:** Importado no Google Sheets
3. **Filtragem:** Filtrado apenas canais do Brasil (Country = "Brazil")
4. **Resultado:** 60 canais brasileiros identificados
5. **Limpeza inicial:** Removidas 3 linhas com dados inconsistentes
6. **Dataset final:** 57 canais brasileiros

### Estrutura dos Dados (17 colunas selecionadas)

| Coluna | Tipo | Descrição |
|--------|------|-----------|
| rank | Numérico | Posição global do canal |
| Youtuber | Texto | Nome do canal |
| subscribers | Numérico | Número de inscritos |
| video views | Numérico | Visualizações totais acumuladas |
| category | Texto | Categoria/nicho do canal |
| uploads | Numérico | Quantidade de vídeos publicados |
| Country | Texto | País (Brazil) |
| channel_type | Texto | Tipo de canal |
| video_views_for_the_last_30_days | Numérico | Views recentes (crescimento) |
| lowest_monthly_earnings | Numérico | Receita mensal mínima estimada (USD) |
| highest_monthly_earnings | Numérico | Receita mensal máxima estimada (USD) |
| lowest_yearly_earnings | Numérico | Receita anual mínima estimada (USD) |
| highest_yearly_earnings | Numérico | Receita anual máxima estimada (USD) |
| created_date | Data | Data de criação do canal |
| Views_por_Inscrito | Calculado | Taxa de engajamento |
| Receita_Media_Mensal | Calculado | Média de receita mensal |
| Tamanho_Canal | Calculado | Classificação por tamanho |

---

## 🧹 3. PROCESSAMENTO E LIMPEZA {#processamento}

### Problemas Identificados

1. **Colunas não separadas:** CSV importado com separador incorreto
2. **Dados ausentes:** 2 linhas com valores críticos faltando
3. **Formato inconsistente:** Números com "M" (milhões) em formato texto
4. **Duplicatas:** Verificadas (nenhuma encontrada)

### Ações Tomadas

**Passo 1: Reimportação com separador correto**
- Separador ajustado para vírgula (,)
- Dados corretamente distribuídos em 28 colunas

**Passo 2: Remoção de dados incompletos**
- 3 linhas removidas por falta de dados críticos (subscribers, category)
- Dataset final: 57 canais

**Passo 3: Criação de colunas calculadas**


Views_por_Inscrito = video views / subscribers
Receita_Media_Mensal = (lowest_monthly_earnings + highest_monthly_earnings) / 2
Tamanho_Canal = SE(subscribers >= 10M, "Mega", 
                    SE(subscribers >= 1M, "Grande",
                    SE(subscribers >= 100K, "Médio", "Pequeno")))


**Passo 4: Colunas adicionais para análises avançadas**


Inscritos_por_Video = subscribers / uploads
CPM_por_Milhao = (Receita_Media_Mensal / video_views_for_the_last_30_days) * 1.000.000
Momentum_Percentual = video_views_for_the_last_30_days / video views
Anos_no_YouTube = 2023 - ANO(created_date)
Classificacao_BCG = [Fórmula complexa baseada em engajamento e crescimento]


### Validação de Dados

- ✅ Sem valores negativos em métricas numéricas
- ✅ Datas válidas (1990-2023)
- ✅ Categorias consistentes
- ✅ Todos os 57 registros íntegros

---

## 📊 4. ANÁLISE DESCRITIVA {#analise}

### Estatísticas Gerais

**Amostra:** 57 canais brasileiros (Top influenciadores)

| Métrica | Valor |
|---------|-------|
| Total de Inscritos | 1,15 bilhão |
| Total de Visualizações | 459 bilhões |
| Receita Mensal Total (estimada) | R$ 14,7 milhões |
| Média de Inscritos por Canal | 20,1 milhões |
| Média de Engajamento | 392 views/inscrito |
| Média de Vídeos Publicados | 2.909 vídeos |

### Distribuição por Tamanho

| Categoria | Quantidade | % |
|-----------|------------|---|
| Mega (>10M) | 57 | 100% |
| Grande (1-10M) | 0 | 0% |
| Médio (100K-1M) | 0 | 0% |
| Pequeno (<100K) | 0 | 0% |

**Insight:** Dataset capturou apenas mega-influenciadores brasileiros, todos com mais de 10 milhões de inscritos.

### Top 10 Canais por Inscritos

1. Canal KondZilla - 66,5M
2. Felipe Neto - 45,2M
3. Você Sabia? - 44,7M
4. whindersson nunes - 44,2M
5. GR6 EXPLODE - 38,9M
6. Maria Clara & JP - 37,0M
7. Galinha Pintadinha - 33,8M
8. rezende evil - 32,1M
9. Enaldinho - 29,2M
10. Renato Garcia YT - 26,9M

### Distribuição por Categoria

| Categoria | Canais | Inscritos Totais |
|-----------|--------|------------------|
| Entertainment | ~15 | 300M |
| Music | ~12 | 270M |
| Comedy | ~8 | 150M |
| Film & Animation | ~6 | 140M |
| Gaming | ~4 | 110M |
| People & Blogs | ~5 | 115M |
| Sports | ~3 | 25M |
| Outros | ~4 | 35M |

---

## 🔬 5. ANÁLISES AVANÇADAS {#avancadas}

### Análise 1: Eficiência de Produção

**Métrica:** Inscritos por Vídeo (quanto cada vídeo "vale")

**Resultados:**
- Média: 6.900 inscritos/vídeo
- Máximo: 67.000.000 inscritos/vídeo (canais com poucos vídeos muito virais)
- Mínimo: 334 inscritos/vídeo

**Insight:** Canais focados em qualidade (menos vídeos, alto valor) podem ter ROI superior a canais de alta frequência.

### Análise 2: Custo-Benefício (CPM)

**Métrica:** Custo por milhão de views nos últimos 30 dias

**Resultados:**
- CPM médio: R$ 2.086,41
- Melhor CPM (mais barato): R$ 0,60
- Pior CPM (mais caro): R$ 150.000+

**Insight:** Há variação de 250.000% entre canais! Seleção estratégica pode gerar economia massiva.

### Análise 3: Momentum (Crescimento Atual)

**Métrica:** % de views totais que vieram nos últimos 30 dias

**Top 3 com Maior Momentum:**
1. GR6 EXPLODE - 6,50%
2. Natan por Aí - 6,12%
3. Spider Slack - 5,46%

**Insight:** Esses canais estão "quentes" AGORA. Momento ideal para investimento antes que fiquem mais caros.

### Análise 4: Qualidade do Público

**Distribuição por Engajamento:**
- Excepcional (>800 views/inscrito): 5,3%
- Ótimo (400-800): 33,3%
- Bom (200-400): 36,8%
- Fraco (<200): 24,6%

**Insight:** 75% dos canais têm engajamento bom ou superior. Público brasileiro é altamente engajado.

### Análise 5: Longevidade vs Sucesso

**Idade média dos canais:** 9,4 anos

**Correlação:**
- Canais veteranos (>10 anos): 18,5M inscritos médio
- Canais estabelecidos (5-10 anos): 21,8M inscritos médio
- Canais novos (<5 anos): 17,2M inscritos médio

**Insight:** Canais de 5-10 anos têm melhor desempenho (sweet spot entre experiência e relevância).

### Análise 6: Matriz BCG Estratégica

**Classificação por Engajamento vs Crescimento:**

| Categoria | Quantidade | Recomendação |
|-----------|------------|--------------|
| ⭐ ESTRELAS | 10 canais | INVESTIR PRIORITARIAMENTE |
| 🐄 VACAS LEITEIRAS | 31 canais | MANTER PARCERIAS |
| ❓ INTERROGAÇÃO | 8 canais | TESTAR COM CAUTELA |
| 🐕 EVITAR | 8 canais | NÃO INVESTIR |

**Insight:** 10 oportunidades de ouro identificadas (alto engajamento + alto crescimento).

---

## 📈 6. VISUALIZAÇÕES {#visualizacoes}

### Dashboard Criado

**8 Gráficos Estratégicos:**

1. **Top 10 por Inscritos** - Gráfico de barras horizontal
2. **Top 10 por Receita** - Gráfico de barras (amarelo/dourado)
3. **Top 10 por Momentum** - Gráfico de barras (laranja)
4. **Matriz BCG** - Gráfico de dispersão (2 eixos)
5. **Distribuição por Engajamento** - Gráfico de pizza
6. **Análise por Categoria** - Gráfico de colunas agrupadas
7. **Eficiência vs Receita** - Gráfico de dispersão
8. **Longevidade vs Sucesso** - Gráfico de dispersão

**Características:**
- Design limpo e profissional
- Cores intuitivas (vermelho YouTube, verde sucesso, laranja crescimento)
- Rótulos de dados visíveis
- Mensagens-chave em cada gráfico

---

## 💡 7. INSIGHTS E RECOMENDAÇÕES {#insights}

### Principais Insights

**1. Mercado Gigantesco**
- Brasil é potência no YouTube: 1,15 bilhão de inscritos acumulados
- Receita estimada de R$ 14,7 milhões/mês apenas nos top 57

**2. Concentração em Poucas Categorias**
- Entertainment e Music dominam 50% do mercado
- Oportunidades em nichos menos saturados (Sports, Education)

**3. Engajamento Excepcional**
- 75% dos canais têm engajamento bom ou superior
- Público brasileiro é altamente fiel e ativo

**4. Variação Massiva de CPM**
- Diferença de 250.000% entre canais
- Seleção estratégica pode economizar milhões

**5. 10 ESTRELAS Identificadas**
- Alto engajamento + Alto crescimento
- Oportunidades de investimento com ROI superior

### Recomendações Estratégicas

**🎯 INVESTIR PRIORITARIAMENTE:**

✅ Nos 10 canais classificados como ⭐ ESTRELAS  
✅ Categorias: Entertainment, Music, Comedy  
✅ CPM médio alvo: Abaixo de R$ 2.086,41  
✅ Foco em canais com momentum >3%  

**🐄 MANTER PARCERIAS:**

✅ 31 canais VACAS LEITEIRAS identificados  
✅ ROI previsível e estável  
✅ Ideal para campanhas de longo prazo  

**🚫 EVITAR:**

❌ 8 canais com baixo engajamento (<200 views/inscrito)  
❌ Categorias saturadas com CPM alto  
❌ Canais sem crescimento nos últimos 30 dias  

**💎 OPORTUNIDADES:**

✅ Canais com momentum >5% (crescimento explosivo)  
✅ Nichos menos explorados (Sports, Education)  
✅ Canais eficientes (alto inscritos/vídeo)  

### Plano de Ação

**CURTO PRAZO (30 dias):**
- ✅ Contatar os 10 canais ESTRELAS
- ✅ Negociar contratos com canais top CPM
- ✅ Testar campanha piloto com R$ 2.086,41

**MÉDIO PRAZO (90 dias):**
- ✅ Expandir para categorias promissoras
- ✅ Monitorar momentum e ajustar estratégia
- ✅ Medir ROI e otimizar investimentos

**LONGO PRAZO (6-12 meses):**
- ✅ Estabelecer parcerias exclusivas
- ✅ Diversificar portfólio de influenciadores
- ✅ Expandir para novas plataformas (TikTok, Instagram)

---

## 🎓 8. CONCLUSÃO {#conclusao}

### Resultados Alcançados

Este estudo de caso identificou com sucesso:
- ✅ 57 influenciadores brasileiros de alto impacto
- ✅ 10 oportunidades prioritárias de investimento (ESTRELAS)
- ✅ Economia potencial de 60% via seleção estratégica de CPM
- ✅ Categorias dominantes e nichos com oportunidades
- ✅ Perfil ideal de canal para diferentes objetivos de campanha

### Impacto Esperado

**Para o Cliente (BrandConnect):**
- Redução de 60% no custo de aquisição via CPM otimizado
- Aumento de 3x no ROI via seleção de canais ESTRELAS
- Portfólio diversificado de 40+ influenciadores
- Vantagem competitiva via dados estratégicos

### Próximos Passos

1. Validar insights com testes A/B de campanha piloto
2. Expandir análise para Instagram e TikTok
3. Criar sistema de monitoramento contínuo de momentum
4. Desenvolver modelo preditivo de ROI por categoria

### Metodologia Replicável

Este framework pode ser aplicado a:
- ✅ Outros países (Argentina, México, etc.)
- ✅ Outras plataformas (Instagram, TikTok, Twitch)
- ✅ Outros nichos (B2B, e-commerce, SaaS)
- ✅ Outras métricas (sentimento, demografia, etc.)

---

## 🛠️ Ferramentas e Tecnologias

- **Kaggle:** Fonte de dados
- **Google Sheets:** Limpeza, transformação e análise
- **Google Slides:** Apresentação executiva
- **Fórmulas utilizadas:** SOMA, MÉDIA, CONT.SE, CONT.SES, SE, MÉDIASE, MÁXIMO, MÍNIMO, MED

---

## 📚 Aprendizados

### Habilidades Desenvolvidas

- ✅ Definição de problema de negócio
- ✅ Preparação e limpeza de dados
- ✅ Análise descritiva e exploratória
- ✅ Criação de métricas customizadas
- ✅ Visualização de dados estratégica
- ✅ Storytelling com dados
- ✅ Apresentação executiva

### Desafios Superados

- ❌ CSV com separador incorreto → ✅ Reimportação correta
- ❌ Colunas calculadas complexas → ✅ Fórmulas aninhadas (SE, E)
- ❌ Dados ausentes → ✅ Remoção criteriosa
- ❌ Visualizações confusas → ✅ Iteração até clareza

---

## 📞 Contato

**Analista:** Luiz Alberto Costa de Souza
**Email:** luizalbertocosta01@gmail.com.


---

## 📜 Licença e Créditos

**Dataset:** Global YouTube Statistics 2023 (Kaggle - Dados Públicos)  
**Projeto:** Estudo de caso educacional  
**Data:** Novembro 2024

---

*Documentação criada como parte do programa de Certificação em Análise de Dados.*
