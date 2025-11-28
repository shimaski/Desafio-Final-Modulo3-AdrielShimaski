# 03-metodologia.md

# Metodologia

## Frameworks utilizados

- OWASP Testing Guide v4.2
- PTES (Penetration Testing Execution Standard)
- NIST SP 800-115

## Fases do Pentest

### 1. Reconhecimento
- Inspeção de HTML
- Robots.txt
- Descoberta de arquivos ocultos

### 2. Varredura
- Enumeração de portas
- Recon de serviços (FTP, SSH, MySQL)

### 3. Exploração
- SQL Injection
- XSS Refletido
- Leitura de arquivos sensíveis
- FTP anônimo
- Credenciais expostas

### 4. Pós-exploração
- SSH via credenciais encontradas
- Dump de arquivos internos
- Enumeração de tabelas SQL
- Coleta de flags