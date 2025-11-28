# 04-swot.md

# Análise SWOT - Segurança TechCorp Solutions

## Forças
- Backups funcionais
- SSL configurado
- Serviços essenciais respondendo

## Fraquezas
- FTP anônimo
- SQL Injection crítico
- Credenciais hardcoded
- .bash_history exposto
- Arquivos sensíveis acessíveis via web


quadrantChart
    title Análise SWOT - Segurança TechCorp Solutions
    x-axis "Interno" --> "Externo"
    y-axis "Favorável" --> "Desfavorável"
    "Backups funcionais": [0.3, 0.7]
    "SSL Configurado": [0.25, 0.75]
    "FTP Anônimo": [0.7, 0.8]
    "SQL Injection": [0.8, 0.85]
    "Credenciais Hardcoded": [0.75, 0.7]
    "Bash History Exposto": [0.8, 0.6]
    "Concorrência": [0.9, 0.2]
    "Vazamento dados": [0.85, 0.3]
    "Regulamentação": [0.9, 0.4]