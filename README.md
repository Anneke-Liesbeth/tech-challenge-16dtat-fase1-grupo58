# Tech Challenge - Fase 1 - Case E-commerce Olist (Projeto Individual)

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

## 6. Panorama Geográfico
Utilizando a mediana estatística para mitigar o efeito de anomalias (*outliers*), o levantamento por estado indica maiores proporções relativas de frete nas regiões Norte e Nordeste.
Observa-se que Pará (PA) e Maranhão (MA) reúnem as maiores taxas de incidência de frete para o cliente final (34,26% e 39,22%, respectivamente) simultaneamente aos maiores volumes de pedidos dessas regiões (1.054 e 800 pedidos).

## 7. A Realidade Logística e o Impacto na Satisfação
O cruzamento da base financeira com a tabela de avaliações (`olist_order_reviews_dataset`) permite quantificar o que gera maior atrito operacional na plataforma:
- **Média Nacional de Avaliação:** 4,08 (em São Paulo atinge 4,18).
- **Médias PA e MA:** Sofrem quedas expressivas, registrando 3,84 e 3,76.

A mineração de textos nas 371 avaliações negativas (notas 1 a 3) registradas nestes dois estados isolou a causa-raiz da insatisfação:
- Apenas **9 queixas** focaram no alto custo do frete.
- **176 menções** relataram exclusivamente atrasos e demora na entrega.

O cálculo exato do tempo de entrega confirma o gargalo logístico: a mediana de entrega em São Paulo é de apenas **7 dias**, enquanto o cliente no Maranhão espera **19 dias** e no Pará **21 dias** (valores muito acima da média nacional de 10 dias). 

*Observação:* Os dados mostram que o que impacta negativamente a nota no Norte/Nordeste não é prioritariamente o valor da entrega. Os consumidores destes locais aceitam pagar o frete mais caro, mas demonstram forte insatisfação com o nível de serviço logístico. 

## 8. Avaliação de Impacto e Conclusão Analítica
O registro de retorno dos clientes para compras futuras (recompra) apresenta a seguinte distribuição:
- **Cenário Nacional e Otimizado:** A taxa de recompra no Brasil é de 3,12%, atingindo 3,24% em São Paulo (praça com logística ágil e frete reduzido).
- **Cenário Norte/Nordeste:** O Maranhão e o Pará registram quedas contundentes, com taxas de recompra de 2,34% e 2,53%, respectivamente.

**Conclusão:**
A maior oportunidade de expansão de receita da Olist encontra-se no destravamento da recompra nos polos de alto volume do Norte e Nordeste (como PA e MA). Os dados demonstram uma correlação direta entre a eficiência logística e a retenção de clientes. Cenários onde o frete tem menor impacto no preço e as entregas são ágeis apresentam as maiores taxas de recompra. Em contrapartida, polos com alto volume de vendas que registram os fretes mais caros e os prazos de entrega mais longos apresentam as menores taxas de retorno da base estudada. A análise indica que a demora na entrega afeta diretamente a percepção de satisfação do consumidor e, consequentemente, destrói o valor do ciclo de vida do cliente (LTV) nessas regiões.