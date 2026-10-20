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
- [x] Definição da Pergunta de Negócio: Oportunidades de expansão de receita e impacto do frete.
- [x] Criação do ambiente virtual Python e instalação de bibliotecas (`pandas`, `numpy`, `seaborn`, `matplotlib`, `plotly`).
- [x] Criação do caderno principal (`analise_crescimento_olist.ipynb`) aplicando os conceitos de Storytelling.
- [x] Primeira carga de dados e validação da tabela Fato (`olist_orders_dataset.csv`).