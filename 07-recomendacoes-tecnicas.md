# 07 - Recomendações Técnicas


## 7.1 Correções Críticas (Prazo: **24 a 48 horas**)

---

### 7.1.1 Mitigação de SQL Injection

**Ações obrigatórias:**
* Substituir consultas SQL concatenadas por *Prepared Statements*.
* Implementar validação de entrada (Whitelist/Input Sanitization).
* Habilitar logs e alertas para padrões de SQLi.
* Configurar WAF para detectar padrões suspeitos.

**Exemplo de correção (PHP):**
```php
$stmt = $conn->prepare("SELECT * FROM users WHERE username = ?");
$stmt->bind_param("s", $username);
$stmt->execute();

```

**Ações obrigatórias:**
* Remover concatenação direta de variáveis em consultas SQL.
* Implementar validação de entrada com *whitelist*.
* Ativar logs de detecção de padrões de SQLi.

### 7.1.2 Remoção de Arquivos Sensíveis Expostos

**Arquivos afetados:**
* `/config/database.php`
* `/config/database.php.txt`
* Backups no diretório público
* Arquivos `.git-credentials`

**Correção:**

```bash
rm -rf /var/www/html/config/
```

### 7.1.3 Desativar FTP Anônimo

**Configuração:**
``` echo "anonymous_enable=NO" >> /etc/vsftpd.conf
systemctl restart vsftpd
```
### 7.1.4 Rotação de Credenciais Comprometidas

**Credenciais a alterar:**
* MySQL (root e techcorp_user)
* Senhas SSH
* Credenciais de painel administrativo
* Tokens Git e API Keys

---

### 7.2 Melhorias de Alta Prioridade (Prazo: 1 semana)

### 7.2.1 Implementação de WAF

**Exemplo de configuração (Nginx):**
```nginx
location /admin/ {
    limit_req zone=one burst=10 nodelay;
    deny all;
}



