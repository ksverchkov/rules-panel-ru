![](https://raw.githubusercontent.com/Git-Lofter/rules-panel/master/img/01.png )

![](https://raw.githubusercontent.com/Git-Lofter/rules-panel/master/img/02.png )

![](https://raw.githubusercontent.com/Git-Lofter/rules-panel/master/img/03.png )

#Развертывание на стороне управления：

1. Загрузите исходный код и установите папку public в качестве запущенного каталога (обратите внимание, что файл не содержит главную папку).
2. Псевдостатическая конфигурация Nginx：

```
location /{     
    if (!-e $request_filename) {       
        rewrite ^/(.*)$ /index.php/$1 last;       
        break;     
    }    
}
```

Псевдостатический Apache (.htaccess настроен в папку public)：

``
<IfModule mod_rewrite.c>

RewriteEngine on

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME} !-f

RewriteRule ^(.*)$ index.php/$1 [QSA,PT,L]

</IfModule>
```

3. Устанавливайте запланированные задачи

# Установите curl

'apt-get install curl-y`

# Установите запланированные задачи (выполнять один раз в 5 минут)

"krontab-e`

# Добавьте запланированные задачи, пожалуйста, замените URL-адрес на свой собственный

`*/5 * * * * curl https://твойадрес/cron`

4. Импортируйте базу данных (test.sql). Файл конфигурации базы данных app/config. Имя пользователя и пароль php по умолчанию: admin 123456

# Серверное развертывание -версия Golang (рекомендуется):

Код и логика выполнения переработаны, чтобы значительно снизить загрузку процессора, но это не с открытым исходным кодом и предоставляет только скомпилированные двоичные файлы.

Эта программа переняет правила NAT iptables. Если вы не владеете iptables, пожалуйста, не используйте другие скрипты на основе iptables!！！

# Включить переадресацию (вот скрипт)：

'wget http://ftp.taoluyun.cc/iptables-pf.sh &&chmod+x iptables-pf.sh `

Затем выполните`./iptables-pf.sh ' Выберите вариант 1 для установки iptables

# Очистите локальное правило iptables (если вы мигрируете с сервера nodejs, вы также должны выполнить эту команду)

`iptables -F`

'iptables-t nat-F`

# Сохранить брандмауэр

Выполнение в CENTOS:

`service iptables save`

Выполнение в debian:

'iptables-save>/etc/iptables`

# Загрузите этот файл：

```bash
wget - htttp://ftp.taoluyun.cc/ip_table &&chmod+x ip_table
```

# Установите запланированные задачи：

"krontab-e`

`*/5 * * * * . /etc/profile;/root/ip_table key123 10.0.0.4 https://baidu.com/api`

# Описание параметра:


*key123 - это ключ, назначенный после добавления сервера в главную панель управления

*10.0.0.4 IP на основной сетевой карте, проверьте метод: 'ip addr`.Если ваш IP-адрес является общедоступным IP-адресом и это динамический IP-адрес, вам необходимо изменить его при изменении IP-адреса.

*https://baidu.com/api Для вашего основного URI, пожалуйста, замените его на ваше доменное имя самостоятельно

# Руководство по развертыванию серверной части-версия NodeJS (эта версия не рекомендуется, рекомендуется версия Golang):

Рекомендуется использовать версию клиента Golang. Если вам нужно использовать эту версию, пожалуйста, изучите ее самостоятельно!

Чтобы заменить Golang, вам необходимо отключить сервер nodejs, чтобы избежать путаницы

`pm2 delete 0`

`pm2 save`

Затем удалите файлы, связанные с nodejs


#### Анализ ошибок

1. Ошибка записи файла с запросом: `Каталог веб-сайта chown www-R`
2. После добавления сервера, но не могу его найти: назначьте разрешения пользователю
3. Если ваша сетевая карта NAT, ip-адрес основной сетевой карты должен быть ip-адресом интрасети (обычно 10.начало)
4. Порт не работает: отключите брандмауэр iptables.Если это centos, вам необходимо удалить firwall и включить iptables

###### ошибка сигнала SIGSEGV：

debian:
```shell
apt-get install ca-certificates -y
```
centos:
```shell
yum install ca-certificates -y
```
