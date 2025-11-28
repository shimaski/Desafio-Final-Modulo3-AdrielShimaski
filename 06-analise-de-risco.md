# Análise de Risco Detalhada

---

##  Metodologias Utilizadas
- **OWASP Risk Rating Methodology**
- **NIST SP 800-30**
- **PTES - Post-Exploitation Risk Model**

---

##  Matriz Quantitativa de Risco

| Vulnerabilidade                      | Probabilidade | Impacto  | Severidade | Status      |
|--------------------------------------|---------------|----------|------------|-------------|
| SQL Injection (Login.php)           | 95%           | 9.5/10   | Crítica    | Ativo       |
| Credenciais de Banco Expostas       | 90%           | 9.0/10   | Crítica    | Ativo       |
| FTP Anônimo                         | 85%           | 8.0/10   | Alta       | Ativo       |
| Config Files Expostos               | 75%           | 7.0/10   | Alta       | Ativo       |
| Bash History Exposto                | 80%           | 7.5/10   | Alta       | Ativo       |
| SSH Home Directory Exposure         | 70%           | 7.5/10   | Alta       | Ativo       |
| Git Credentials Leak                | 85%           | 8.5/10   | Crítica    | Ativo       |
| Script de Backup Sensível           | 75%           | 7.5/10   | Alta       | Persistente |
| Backup.log com Flags                | 70%           | 7.0/10   | Média      | Persistente |
| XSS Refletido                       | 65%           | 6.5/10   | Média      | Ativo       |
| Robots.txt com Infos                | 55%           | 5.3/10   | Média      | Ativo       |
| Basic Source Code Info Leak         | 40%           | 4.0/10   | Baixa      | Ativo       |
| Hidden Database Data                | 75%           | 8.0/10   | Alta       | Ativo       |
| Database View Discovery             | 75%           | 8.0/10   | Alta       | Ativo       |
| Privilege Escalation                | 85%           | 9.0/10   | Crítica    | Ativo       |
| Password File Discovery             | 85%           | 8.5/10   | Alta       | Ativo       |

---

##  Análise de Probabilidade

**Fatores Considerados:**
- Exploitabilidade  
- Existência de PoCs reais  
- Execução bem-sucedida durante pentest  
- Complexidade do ataque  
- Nível de autenticação exigido  

**Exemplos:**
- **SQL Injection:** 95% – execução simples, sem sanitização  
- **FTP Anônimo:** 85% – acesso direto sem autenticação  
- **Git Credential Leak:** 85% – acesso via HTTP direto  

---

##  Análise de Impacto

### Impactos Técnicos:
- Comprometimento total do servidor  
- Acesso às credenciais root do MySQL  
- Vazamento de senhas internas e API keys  
- Exposição de scripts internos de backup  
- Vazamento completo de diretórios sensíveis  

### Impactos de Negócio:

| Área         | Impacto | Detalhes                              |
|--------------|---------|---------------------------------------|
| Financeiro   | Alto    | Multas LGPD (R$ 50.000+)              |
| Reputação    | Alto    | Empresa vista como negligente         |
| Operacional  | Crítico | Paralisação total da infraestrutura   |
| Legal        | Alto    | Exposição de dados sensíveis          |

---

##  Risco Final (Probabilidade × Impacto)

| Categoria | Intervalo | Quantidade de Vulnerabilidades |
|-----------|-----------|--------------------------------|
| Crítico   | 8.5 - 10  | 7                              |
| Alto      | 7.0 - 8.4 | 6                              |
| Moderado  | 5.0 - 6.9 | 2                              |
| Baixo     | 0 - 4.9   | 1                              |

---

##  Conclusão da Análise de Risco

O ambiente apresenta acúmulo de vulnerabilidades **críticas**, com diversas superfícies de ataque simultâneas, levando a um cenário de risco **severo**.

> **Risco Global:  CRÍTICO**

### Consequências Prováveis:
- Comprometimento total do sistema  
- Vazamento de dados sensíveis  
- Multas regulatórias (LGPD, GDPR)  
- Danos irreparáveis à reputação da empresa  

---

