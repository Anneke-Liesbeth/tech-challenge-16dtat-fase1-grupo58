# Tech Challenge - Fase 1 - Case E-commerce Olist (Grupo 58)
Análise de dados para o Tech Challenge.

## 1. Configuração Inicial e Governança de Dados
Para garantir a organização, reprodutibilidade e a governança dos dados em diferentes ambientes de trabalho, adotei a seguinte estrutura:

* **Repositório GitHub**: Criado o repositório oficial `Anneke-Liesbeth/tech-challenge-16dtat-fase1-grupo58` para versionamento do código, documentação e entregáveis.

* **Pré-requisitos**: Instalação e configuração do Git para execução dos comandos de versionamento via terminal (CMD).

* **Clonagem do Repositório**: O código-fonte (notebooks, documentação e arquivos de configuração) é sincronizado via GitHub. Para trabalhar em novas máquinas, utiliza-se o comando `git clone`.

* **Gestão da Pasta `data/`**: Os arquivos `.csv` originais da Olist são baixados do Kaggle e armazenados localmente na pasta `data/` na raiz do projeto.

* **Arquivo `.gitignore`**: Configurado para ignorar a pasta `data/` e arquivos temporários do Python, evitando o envio acidental de dados pesados para o GitHub.