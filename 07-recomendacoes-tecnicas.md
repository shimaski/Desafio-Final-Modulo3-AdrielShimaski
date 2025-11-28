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

```


### 7.2.2 Auditoria de Permissões

**Diretórios a verificar:**
* /home/techcorp/
* /var/backups/
* /opt/backup_script.sh

**Comandos:**
```bash
chmod 600 sensitive_file
chown root:root sensitive_file

```

### 7.2.3 Limpeza e Proteção de Logs

**Correção:**
```bash
truncate -s 0 ~/.bash_history
export HISTSIZE=0
export HISTFILESIZE=0
```
### 7.2.4 Hardening de SSH

**Recomendações:**
* Desativar login com senha.
* Forçar uso de chave pública.
* Limitar usuários permitidos.
* Configurar Fail2Ban.

---

## 7.3 Melhorias de Médio Prazo (Prazo: 1 mês)

### 7.3.1 Política de Segurança

**Implementar:**
* Política de desenvolvimento seguro.
* Treinamento para desenvolvedores.
* Revisão de código periódica.
* Processo de CI/CD com análise SAST.

---

### 7.3.2 Sistema de Monitoramento

**Recomendações:**
* Centralizar logs (ELK, Splunk ou Graylog).
* Alertas para tentativas de SQL Injection.
* Monitoramento de acessos SSH suspeitos.

---

### 7.3.3 Backup Seguro

**Recomendações:**
* Criptografar backups com GPG.
* Mover backups para ambiente segregado.
* Remover credenciais hardcoded.

---

## 7.4 Melhorias de Longo Prazo (2-3 meses)

### 7.4.1 Implantação de SIEM

**Benefícios:**
* Correlação de eventos.
* Detecção de incidentes.
* Alertas centralizados.

---

### 7.4.2 Testes Periódicos

**Calendário sugerido:**
* Teste trimestral.
* Testes após cada release importante.
* Auditoria anual completa.
