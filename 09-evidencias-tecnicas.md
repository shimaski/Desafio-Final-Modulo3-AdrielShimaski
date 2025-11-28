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
