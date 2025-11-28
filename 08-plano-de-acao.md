# 08 - Plano de Ação

---

## 8.1 Fase 1 - 24 a 48 horas (Crítico)

### 1. Correção de SQL Injection
- Implementar Prepared Statements em todas as rotas PHP.
- Aplicar validação de entrada no servidor.
- Remover concatenação direta em queries SQL.
- Reexecutar testes de SQLi para validação.

### 2. Remoção de Arquivos Sensíveis
- Remover diretório `/var/www/html/config/`.
- Restringir acesso web a arquivos `.conf`, `.sql`, `.sh`, `.bak`, `.zip`.

### 3. Desativação do FTP Anônimo
- Editar `/etc/vsftpd.conf`: `anonymous_enable=NO`.
- Criar regras de firewall.
- Rotacionar credenciais FTP.

### 4. Rotação de Credenciais
**Credenciais a substituir:**
- MySQL: `root`, `techcorp_user`, `backup_user`
- SSH: `techcorp`, `ftpadmin`
- Senhas do `passwords.txt`
- Credenciais do `.bash_history`

### 5. Revogação de Tokens
- Revogar credenciais do `.git-credentials`.
- Gerar novos tokens para ambientes.

### 6. Bloqueio Temporário
- Bloquear acesso ao painel administrativo.
- Habilitar firewall para portas `21`, `22`, `80`.
- Auditar acessos registrados.

---

## 8.2 Fase 2 - 1 Semana (Alto)

### 1. Implementar WAF
- Regras OWASP Core Rule Set.
- Bloqueio de SQLi, XSS, LFI.
- Rate limiting para `/admin/` e `/login.php`.

### 2. Configurar Monitoramento
**Logs centralizados via:**
- journald
- syslog
- ELK

**Alertas automáticos para:**
- Tentativas de SQLi.
- Acessos suspeitos.
- Modificação de arquivos.

### 3. Backup Seguro
- Criptografar backups em `/var/backups/techcorp`.
- Restringir permissões.
- Remover informações sensíveis do script.

### 4. Revisão de Permissões
- Remover permissões excessivas (`chmod 777`).
- Reforçar permissões em:
  - `/home/techcorp/`
  - `/var/www/html/`
  - `/opt/`
  - `/tmp/`

### 5. Auditoria de Código
- Revisão completa de scripts PHP.
- Remoção de comentários sensíveis.
- Padronização de segurança.

---

## 8.3 Fase 3 - 1 Mês (Médio)

### 1. Programa de Segurança Interno
- Treinamento em OWASP Top 10.
- Campanha sobre boas práticas.
- Revisão trimestral de segurança.

### 2. Implementação de SIEM
- Ferramenta: Wazuh, Splunk ou Elasticsearch.
- Dashboards para anomalias.
- Retenção de logs por 90 dias.

### 3. Melhoria na Arquitetura
- Variáveis de ambiente para senhas.
- Segregar banco em rede privada.
- SSH somente com chave pública.

### 4. Testes Periódicos
- Frequência: trimestral.
- Relatórios seguindo NIST 800-115.
- Incluir SAST e DAST.

---

## 8.4 Fase 4 - Contínuo

### 1. Manutenção
- Revisão de logs diária.
- Testes semestrais de backup.
- Atualizações de kernel.

### 2. Compliance
- Adequação à LGPD.
- Relatório de impacto.
- Inventário de ativos.

### 3. Métricas
**Indicadores:**
- Tempo médio para resposta (MTTR).
- Incidentes de segurança.
- Patches aplicados no prazo.
- Evolução da superfície de ataque.

---

## 8.5 Resumo do Plano

| Fase     | Prioridade | Entrega                     |
|----------|------------|-----------------------------|
| 24-48h   | Crítica    | Correções indispensáveis    |
| 1 Semana | Alta       | Fortalecimento inicial      |
| 1 Mês    | Média      | Estruturação do programa    |
| Contínuo | Permanente | Monitoramento               |
