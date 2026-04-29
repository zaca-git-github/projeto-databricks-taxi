# projeto-databricks-taxi

🚖 Azure Data Pipeline: NYC Taxi Medallion Architecture
Este projeto demonstra a implementação de um pipeline de dados ponta a ponta utilizando a Arquitetura Medalhão dentro do ecossistema Azure. O objetivo é processar dados brutos de corridas de taxi, transformá-los para garantir qualidade e integridade, e gerar KPIs de faturamento para análise de negócio.

🛠️ Tecnologias e Ferramentas
Azure Databricks: Processamento distribuído com PySpark.

Azure Data Factory (ADF): Orquestração dos notebooks e gerenciamento do fluxo.

Azure Data Lake Storage Gen2: Armazenamento em camadas (Bronze, Silver, Gold).

Delta Lake: Formato de armazenamento para garantir transações ACID e performance.

GitHub Repos: Versionamento de código e integração CI/CD com Databricks.

🏗️ Arquitetura do Pipeline
O pipeline segue o padrão de três camadas para garantir a qualidade do dado:

Bronze (Raw): Ingestão dos dados brutos exatamente como recebidos da origem.

Silver (Trusted): * Limpeza e padronização de esquemas.

Conversão de tipos de dados (Ex: strings para timestamps).

Remoção de duplicados.

Dados salvos em formato Delta.

Gold (Business): * Agregações de negócio.

Cálculo de faturamento diário consolidado.

Dados otimizados para consumo em ferramentas de BI como Power BI.

🚀 Desafios Resolvidos
Orquestração de Dependências: Configuração no ADF para garantir que a camada Gold seja processada apenas após o sucesso da Silver.

Segurança de Dados: Implementação de proteção contra exposição de segredos (GitHub Push Protection) em notebooks.

Versionamento Nativo: Integração do Databricks com GitHub via PAT (Personal Access Token) para controle de versão profissional.

📈 Como Executar
O pipeline é orquestrado pelo Azure Data Factory.

O gatilho inicia o Notebook1 (Processamento Bronze -> Silver).

Após a conclusão com sucesso, o Notebook2 (Processamento Silver -> Gold) é iniciado automaticamente.

Os resultados finais são armazenados no caminho: dados/03-gold/kpi_faturamento_diario.
