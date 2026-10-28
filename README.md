# Tech Challenge - Fase 1 - Case E-commerce Olist (Grupo 58)
Análise de dados para o Tech Challenge.

## 1. Configuração Inicial e Governança de Dados
Para garantir a organização, reprodutibilidade e a governança dos dados em diferentes ambientes de trabalho, adotei a seguinte estrutura:

* **Repositório GitHub**: Criado o repositório oficial `Anneke-Liesbeth/tech-challenge-16dtat-fase1-grupo58` para versionamento do código, documentação e entregáveis.

* **Pré-requisitos**: Instalação e configuração do Git para execução dos comandos de versionamento via terminal (CMD).

* **Clonagem do Repositório**: O código-fonte (notebooks, documentação e arquivos de configuração) é sincronizado via GitHub. Para trabalhar em novas máquinas, utiliza-se o comando `git clone`.

* **Gestão da Pasta `data/`**: Os arquivos `.csv` originais da Olist são baixados do Kaggle e armazenados localmente na pasta `data/` na raiz do projeto.

* **Arquivo `.gitignore`**: Configurado para ignorar a pasta `data/` e arquivos temporários do Python, evitando o envio acidental de dados pesados para o GitHub.

## 1. Contexto e Pergunta de Negócio
**Pergunta Principal:** Onde estão as maiores oportunidades de expansão de receita da Olist, considerando o ticket médio e o impacto percentual do frete?

**Justificativa Estratégica:**
No e-commerce, o cenário financeiro apresenta alta correlação com a logística. Segundo um levantamento da ABIACOM, o frete representa quase 66% dos custos logísticos de uma loja virtual. O cruzamento dos dados de **Faturamento (Receita)** e **Frete (Custo)** deste projeto tem como objetivo mapear a incidência do custo de envio e expor o cenário regional para possíveis otimizações operacionais.

## 2. Configuração Inicial e Governança de Dados
A organização e reprodutibilidade do projeto seguem a estrutura:
- **Repositório GitHub:** Versionamento de código (`.ipynb`) e documentação oficial.
- **Gestão da Pasta `data/`:** Os arquivos de dados originais (`.csv`) foram isolados localmente e ignorados via `.gitignore` para não sobrecarregar o repositório em nuvem.
- **Ferramentas e Bibliotecas:** `pandas`, `numpy`, `seaborn` e `matplotlib`.

## 3. Preparação e Limpeza de Dados
Para o levantamento da receita, a base foi filtrada para considerar apenas os pedidos com o status "delivered" (entregue).
- **Itens Descartados:** 2.453 itens referentes a pedidos cancelados, não aprovados ou extraviados.
- **Base Consolidada:** 110.197 itens faturados e entregues.

## 4. Indicadores Financeiros Globais
A extração inicial da base limpa apresenta os seguintes valores para a operação geral:
- **Faturamento Total (Receita de Produtos):** R$ 13.221.498,11
- **Custo Total de Frete:** R$ 2.198.275,64
- **Ticket Médio (Preço médio por item):** R$ 119,98
- **Frete Médio por item:** R$ 19,95

## 5. Incidência do Frete (Análise de Quartis)
O frete médio global equivale a 32,08% do valor do produto. Para observar como essa taxa incide sobre diferentes faixas de preço sem viés de categorização prévia, aplicou-se a divisão por **Quartis**:
- **1º Quartil (Até R$ 39,90):** A taxa de frete corresponde a **65,36%** do valor da compra.
- **2º Quartil (R$ 39,90 a R$ 74,90):** A incidência é de **30,09%**.
- **3º Quartil (R$ 74,90 a R$ 134,17):** A incidência reduz para **20,03%**.
- **4º Quartil (Acima de R$ 134,17):** A taxa de frete representa **12,33%** do valor da compra.

**Conclusão:** Como o frete possui um custo mínimo "piso" na maioria das transportadoras, ele afeta desproporcionalmente os itens de baixo valor. A maior oportunidade de expansão de receita (e redução de abandono de carrinho) da Olist está em criar soluções logísticas específicas e parcerias de otimização de rotas focadas no portfólio de ticket baixo.