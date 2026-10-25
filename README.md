# Tech Challenge - Fase 1 - Case E-commerce Olist (Grupo 58 - Projeto Individual)

## 1. Contexto e Pergunta de Negócio
**Pergunta Principal:** Onde estão as maiores oportunidades de expansão de receita da Olist, considerando o ticket médio e o impacto percentual do frete?

**Justificativa Estratégica:**
No e-commerce, o cenário financeiro apresenta alta correlação com a logística. Segundo um levantamento da ABIACOM, o frete representa quase 66% dos custos logísticos de uma loja virtual. O cruzamento dos dados de **Faturamento (Receita)** e **Frete (Custo)** deste projeto tem como objetivo mapear a incidência do custo de envio e expor o cenário regional para possíveis otimizações operacionais.

## 2. Configuração Inicial e Governança de Dados
A organização e reprodutibilidade do projeto seguem a estrutura:
* **Repositório GitHub:** Versionamento de código (`.ipynb`) e documentação oficial.
* **Gestão da Pasta `data/`:** Os arquivos de dados originais (`.csv`) foram isolados localmente e ignorados via `.gitignore` para não sobrecarregar o repositório em nuvem.
* **Ferramentas e Bibliotecas:** `pandas`, `numpy`, `seaborn` e `matplotlib`.

## 3. Preparação e Limpeza de Dados
Para o levantamento da receita, a base foi filtrada para considerar apenas os pedidos com o status "delivered" (entregue).
* **Itens Descartados:** 2.453 itens referentes a pedidos cancelados, não aprovados ou extraviados.
* **Base Consolidada:** 110.197 itens faturados e entregues.

## 4. Indicadores Financeiros Globais
A extração inicial da base limpa apresenta os seguintes valores para a operação geral:
* **Faturamento Total (Receita de Produtos):** R$ 13.221.498,11
* **Custo Total de Frete:** R$ 2.198.275,64
* **Ticket Médio (Preço médio por item):** R$ 119,98
* **Frete Médio por item:** R$ 19,95

## 5. Incidência do Frete (Análise de Quartis)
O frete médio global equivale a 32,08% do valor do produto. Para observar como essa taxa incide sobre diferentes faixas de preço sem viés de categorização prévia, aplicou-se a divisão por **Quartis**:
* **1º Quartil (Até R$ 39,90):** A taxa de frete corresponde a **65,36%** do valor da compra.
* **2º Quartil (R$ 39,90 a R$ 74,90):** A incidência é de **30,09%**.
* **3º Quartil (R$ 74,90 a R$ 134,17):** A incidência reduz para **20,03%**.
* **4º Quartil (Acima de R$ 134,17):** A taxa de frete representa **12,33%** do valor da compra.

## 6. Panorama Geográfico
Utilizando a mediana estatística para mitigar o efeito de anomalias (*outliers*), o levantamento por estado indica maiores proporções relativas de frete nas regiões Norte e Nordeste.
Observa-se que Pará (PA) e Maranhão (MA) reúnem as maiores taxas de incidência de frete para o cliente final (34,26% e 39,22%, respectivamente) simultaneamente aos maiores volumes de pedidos dessas regiões (1.054 e 800 pedidos).

## 7. Avaliação de Satisfação e Prazos de Entrega
O cruzamento da base financeira com a tabela de avaliações (`olist_order_reviews_dataset`) permite observar a resposta do consumidor:
* **Média Nacional de Avaliação:** 4,08 (em São Paulo, 4,18).
* **Médias PA e MA:** 3,84 e 3,76.
A mineração de textos nas 371 avaliações negativas registradas nestes dois estados contabiliza **9 menções** atreladas a custo/frete e **176 menções** atreladas a prazo/atraso. O levantamento das datas de rastreio de logística indica que a mediana de tempo de entrega é de 7 dias em SP, 19 dias no MA e 21 dias no PA.

## 8. Comportamento de Recompra
O registro de retorno dos clientes para compras futuras apresenta a seguinte distribuição estatística:
* **Taxa de recompra nacional:** 3,12% (3,24% em São Paulo).
* **Taxa de recompra no Maranhão e Pará:** 2,34% e 2,53%.
Esses números abrem espaço para um debate de negócios sobre como os indicadores logísticos podem estar influenciando o *Lifetime Value* (LTV) da plataforma em pólos distantes.

## 9. Hipóteses para Discussão (Próximos Passos)
A partir da correlação dos dados apresentados, surgem algumas frentes de otimização que podem ser estudadas pela Olist:
* **Diversificação de Malha (Last Mile):** Avaliação de parcerias com transportadoras regionais no Norte/Nordeste para reduzir a dependência de remessas unificadas despachadas do Sudeste.
* **Aproximação de Estoque (Cross-Docking):** Estudos de viabilidade para a criação de hubs logísticos de transição em capitais estratégicas (como Belém ou São Luís), visando a redução no prazo final de entrega.
