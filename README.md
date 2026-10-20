# Tech Challenge - Fase 1 - Case E-commerce Olist (Grupo 58)
Análise de dados para o Tech Challenge.

## 1. Configuração Inicial e Governança de Dados
Para garantir a organização, reprodutibilidade e a governança dos dados em diferentes ambientes de trabalho, adotei a seguinte estrutura:

* **Repositório GitHub**: Criado o repositório oficial `Anneke-Liesbeth/tech-challenge-16dtat-fase1-grupo58` para versionamento do código, documentação e entregáveis.

* **Pré-requisitos**: Instalação e configuração do Git para execução dos comandos de versionamento via terminal (CMD).

* **Clonagem do Repositório**: O código-fonte (notebooks, documentação e arquivos de configuração) é sincronizado via GitHub. Para trabalhar em novas máquinas, utiliza-se o comando `git clone`.

* **Gestão da Pasta `data/`**: Os arquivos `.csv` originais da Olist são baixados do Kaggle e armazenados localmente na pasta `data/` na raiz do projeto.

* **Arquivo `.gitignore`**: Configurado para ignorar a pasta `data/` e arquivos temporários do Python, evitando o envio acidental de dados pesados para o GitHub.

## 2. Contexto e Pergunta de Negócio

**Pergunta Principal:** Onde estão as maiores oportunidades de expansão de receita da Olist, considerando o ticket médio e o impacto do frete?

**Justificativa Estratégica:**
No cenário do e-commerce brasileiro, o crescimento financeiro está diretamente atrelado à eficiência logística. Segundo um [levantamento publicado pela ABIACOM](https://abiacom.org/noticias/plataforma-de-intermediacao-de-fretes-e-ferramenta-importante-nas-vendas-online/), o frete é responsável por quase 66% dos custos logísticos de uma loja virtual, e o alto valor da entrega leva a 80% dos abandonos de carrinho. 

Como o modelo de negócios da Olist atua diretamente na intermediação e otimização desses contratos logísticos, através de soluções como o [Envios da Olist, que conecta pequenos e médios lojistas a transportadoras parceiras para otimizar custos](https://ajuda.olist.com/integracoes-e-automacao/envios-da-olist-%E2%80%94-guia-completo-de-integracao-e-uso), cruzar os dados de **Faturamento (Receita)** e **Frete (Custo)** me permite analisar onde estão as melhores oportunidades de expansão de mercado e onde o custo de envio está atrapalhando as vendas.

## Status Atual do Projeto
- Definição da Pergunta de Negócio: Oportunidades de expansão de receita e impacto do frete.
- Criação do ambiente virtual Python e instalação de bibliotecas (`pandas`, `numpy`, `seaborn`, `matplotlib`, `plotly`).
- Criação do caderno principal (`analise_crescimento_olist.ipynb`) aplicando os conceitos de Storytelling.
- Primeira carga de dados e validação da tabela Fato (`olist_orders_dataset.csv`).

## 2. Preparação e Limpeza de Dados (Data Cleaning)

Para realizar a análise financeira, decidi contabilizar apenas o dinheiro que efetivamente entrou no caixa da Olist, ou seja, pedidos que foram efetivamente entregues. 

Por isso, cruzei a tabela de Itens com a tabela de Pedidos (usando o `order_id` como chave) e filtrei a base mantendo apenas o status "delivered" (entregue):
- **Itens Descartados:** 2.453 itens atrelados a pedidos cancelados, não aprovados ou extraviados.
- **Base Consolidada:** 110.197 itens vendidos e entregues de fato.

## 3. Primeiros Indicadores Financeiros

Com a base limpa, calculei os indicadores globais da operação:
- **Faturamento Total (Receita de Produtos):** R$ 13.221.498,11
- **Custo Total de Frete:** R$ 2.198.275,64
- **Ticket Médio (Preço médio por item):** R$ 119,98
- **Frete Médio por item:** R$ 19,95

## 4. O Impacto do Frete e a Dor do Ticket Baixo

Com os indicadores globais mapeados (onde o frete médio representa 32,08% do valor da compra), decidi investigar como esse peso logístico se distribui entre os produtos. 

Utilizando o método estatístico de **Quartis**, dividi todo o portfólio de vendas da Olist em 4 faixas de preço de volumes iguais, para evitar deduzir o que é "barato" ou "caro". O resultado foi:

- **1º Quartil (Até R$ 39,90):** O frete corresponde a **65,36%** do valor da compra.
- **2º Quartil (R$ 39,90 a R$ 74,90):** O impacto cai para **30,09%**.
- **3º Quartil (R$ 74,90 a R$ 134,17):** O impacto reduz para **20,03%**.
- **4º Quartil (Acima de R$ 134,17):** O frete corresponte apenas a **12,33%** do valor da compra.

**Conclusão:** Como o frete possui um custo mínimo "piso" na maioria das transportadoras, ele afeta desproporcionalmente os itens de baixo valor. A maior oportunidade de expansão de receita (e redução de abandono de carrinho) da Olist está em criar soluções logísticas específicas e parcerias de otimização de rotas focadas no portfólio de ticket baixo.