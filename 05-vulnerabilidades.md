# 05-vulnerabilidades.md


## Vulnerabilidades Críticas Identificadas

### 1. SQL Injection (Login.php)
**Severidade:** Crítica  
**Flag:** FLAG{sql_1nj3ct10n_m4st3r}  
**Descrição:** Vulnerabilidade de injeção SQL no endpoint de autenticação  
**Impacto:** Acesso completo ao banco de dados  
**Evidência:** Payload: ' OR 1=1 --

### 2. Credenciais de Banco Expostas
**Severidade:** Crítica  
**Flag:** FLAG{d4t4b4s3_cr3d3nt14ls_3xp0s3d}  
**Descrição:** Arquivo database.php.txt acessível publicamente  
**Impacto:** Exposição de credenciais de banco de dados  
**Evidência:** 
```php
$db_user = 'techcorp_user';
$db_pass = 'T3chC0rp_S3cr3t_2024!';
```

### 3. FTP Anônimo Ativo
**Severidade:** Alta  
**Flag:** FLAG{ftp_4n0nym0us_4cc3ss}`  
**Descrição:** Serviço FTP permite acesso anônimo  
**Impacto:** Exposição de diretórios e arquivos sensíveis  
**Evidência:** Acesso via: ftp 98.95.207.28

---

### 4. Arquivos de Configuração Expostos
**Severidade:** Alta  
**Flag:** `FLAG{c0nf1g_f1l3_r34d}`  
**Descrição:** Diretório `/config/` acessível via web  
**Impacto:** Exposição de configurações sensíveis  
**Evidência:** Arquivo `/config/database.php.txt`

---

### 5. Arquivo de Senhas Exposto
**Severidade:** Alta  
**Flag:** `FLAG{p4ssw0rd_f1l3_d1sc0v3ry}`  
**Descrição:** Arquivo `passwords.txt` acessível via FTP  
**Impacto:** Vazamento completo de credenciais corporativas  
**Evidência:**
# Relatório de Vulnerabilidades de Segurança

## 3. FTP Anônimo Ativo
**Severidade:** Alta  
**Flag:** `FLAG{ftp_4n0nym0us_4cc3ss}`  
**Descrição:** Serviço FTP permite acesso anônimo  
**Impacto:** Exposição de diretórios e arquivos sensíveis  
**Evidência:** Acesso via: `ftp 98.95.207.28`

---

## 4. Arquivos de Configuração Expostos
**Severidade:** Alta  
**Flag:** `FLAG{c0nf1g_f1l3_r34d}`  
**Descrição:** Diretório `/config/` acessível via web  
**Impacto:** Exposição de configurações sensíveis  
**Evidência:** Arquivo `/config/database.php.txt`

---

## 5. Arquivo de Senhas Exposto
**Severidade:** Alta  
**Flag:** `FLAG{p4ssw0rd_f1l3_d1sc0v3ry}`  
**Descrição:** Arquivo `passwords.txt` acessível via FTP  
**Impacto:** Vazamento completo de credenciais corporativas  
**Evidência:**
    User: techcorp
    Password: TechCorp2024!

## 6. Histórico Bash Exposto
**Severidade:** Alta  
**Flag:** `FLAG{b4sh_h1st0ry_l34k}`  
**Descrição:** Arquivo `.bash_history` acessível  
**Impacto:** Exposição de comandos e credenciais  
**Evidência:**
```bash
mysql -u root -p # senha r00t_P4ssw0rd_2024

```

### 7. Diretório Home SSH Comprometido
**Severidade:** Alta  
**Flag:** `FLAG{ssh_h0m3_d1r3ct0ry_3xpl0r4t10n}`  
**Descrição:** Arquivos sensíveis no diretório home  
**Impacto:** Acesso a credenciais internas  
**Evidência:** Arquivo `/home/techcorp/secret.txt`

---

### 8. Vazamento de Credenciais Git
**Severidade:** Crítica  
**Flag:** `FLAG{g1t_cr3d3nt14ls_l34k}`  
**Descrição:** Arquivo `.git-credentials` exposto  
**Impacto:** Acesso ao repositório Git privado  
**Evidência:** https://admin:gh_p4t_S3cr3tT0k3n_2024_TechCorp@github.com


---

### 9. Script de Backup Sensível
**Severidade:** Alta  
**Flag:** `FLAG{scr1pt_4n4lys1s_sk1ll}`  
**Descrição:** Script com credenciais hardcoded  
**Impacto:** Exposição de credenciais root  
**Evidência:** `/opt/backup_script.sh`

---

### 10. Log de Backup com Flags
**Severidade:** Média  
**Flag:** `FLAG{b4ckup_scr1pt_f0und}`  
**Descrição:** Logs expostos contendo informações sensíveis  
**Impacto:** Vazamento de informações internas  
**Evidência:** `/tmp/backup.log`

---

### 11. XSS Refletido
**Severidade:** Média  
**Flag:** `FLAG{xss_r3fl3ct3d_vuln3r4b1l1ty}`  
**Descrição:** Vulnerabilidade XSS no parâmetro `search`  
**Impacto:** Execução de scripts arbitrários  
**Evidência:** 
http://98.95.207.28/dashboard.php?search=<script>alert(document.cookie)</script>

### 12. Robots.txt com Informações
**Severidade:** Média  
**Flag:** `FLAG{r0b0ts_txt_l34k4g3}`  
**Descrição:** Arquivo `robots.txt` revela diretórios sensíveis  
**Impacto:** Enumeração de estrutura interna  
**Evidência:**
Disallow: /admin/
Disallow: /backup/
Disallow: /config/


### 13. Vazamento de Código Fonte
**Severidade:** Baixa  
**Flag:** `FLAG{b4s1c_s0urc3_c0d3_1nsp3ct10n}`  
**Descrição:** Comentários em HTML revelam informações  
**Impacto:** Exposição de detalhes de implementação  
**Evidência:**
```html
<!-- FLAG{b4s1c_s0urc3_c0d3_1nsp3ct10n} -->

```

### 14. Dados Ocultos no Banco
**Severidade:** Alta  
**Flag:** `FLAG{h1dd3n_d4t4_t4bl3_f0und}`  
**Descrição:** Tabelas ocultas descobertas via SQLi  
**Impacto:** Acesso a dados sensíveis  
**Evidência:**
```sql
UNION SELECT secret_data,1,1 FROM secret_data;

```

### 15. Views do Banco Descobertas
**Severidade:** Alta  
**Flag:** `FLAG{v13w_d1sc0v3ry_4dv4nc3d}`  
**Descrição:** Enumeração de views do banco via SQLi  
**Impacto:** Mapeamento completo da estrutura de dados  
**Evidência:**
```sql
UNION SELECT table_name,1,1 FROM information_schema.views;

```

### 16. Escalação de Privilégio
**Severidade:** Crítica  
**Flag:** `FLAG{pr1v1l3g3_3sc4l4t10n_succ3ss}`  
**Descrição:** Acesso root via credenciais comprometidas  
**Impacto:** Controle total do sistema  
**Evidência:** Acesso SSH com credenciais de administrador

---
