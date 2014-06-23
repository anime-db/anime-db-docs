# Сборка на OS Linux из исходников

Описание установки приложения **Anime DB** на Linux-подобных OS на примере
[Ubuntu 12.04 LTS](http://ru.wikipedia.org/wiki/Ubuntu). Процесс установки приложения в других OS семейства Linux будет
мало отличатся от описанных шагов.

<a name="stap-1"></a>

## Шаг 1: Установка PHP

Приложение написано на языке программирования [PHP](http://ru.wikipedia.org/wiki/Php) и для работы ему необходим PHP
[интерпретатор](http://ru.wikipedia.org/wiki/Интерпретатор). В случае OS Windows есть скомпилированная версия не
требующая установки в системе и потому приложение на Windows легко устанавливается. На других OS таких как Ubuntu
необходимо устанавливать интерпретатор в системе.

Для упрощения работы PHP будет установлен из пакетов. В репозиториях Ubuntu сейчас находится PHP версии 5.3, а для
работы приложения требуется 5.4 и выше, в связи с чем, добавляем новый репозиторий со свежей версией:

```bash
sudo add-apt-repository ppa:ondrej/php5
```

Обновить информацию о доступных пакетах и обновить их:

```bash
sudo apt-get update && sudo apt-get upgrade
```

Установить PHP 5.5 и основные расширения:

```bash
sudo apt-get install php5-cli php5-curl php5-gd php5-sqlite php5-tidy
```

После установки приложения необходимо установить параметры для PHP интерпретатора отредактировав файл
`/etc/php/php.ini` и запишите в него следующие параметры:

```ini
display_errors = Off
date.timezone = Europe/Moscow
upload_tmp_dir = "tmp"
extension_dir = "ext"

extension=php_com_dotnet.dll
extension=php_curl.dll
extension=php_gd2.dll
extension=php_intl.dll
extension=php_mbstring.dll
extension=php_openssl.dll
extension=php_pdo_sqlite.dll
extension=php_tidy.dll
extension=php_fileinfo.dll
```

Эти параметры определяют список расширений которые будут подключены и основные параметры. Параметр `date.timezone`
определяет временную зону в которой Вы находитесь. Если ваше временная зона отличается от временной зоны города Москва
в Россие, то Вы можете указать свою временную зону.
[Список поддерживаемых временных зон](http://www.php.net/manual/ru/timezones.php).

<a name="stap-2"></a>

## Шаг 2: Установка приложения

Клонируйте [Git](http://ru.wikipedia.org/wiki/Git) репозиторий с последней версией приложения:

```bash
git clone git://github.com/anime-db/anime-db.git && cd anime-db
```

> Если у Вас не установлен Git Вы можете устанавить его выполнив команду:
> 
> ```bash
> sudo apt-get install git
> ```
> 
> Или Вы можете скачать исходники в виде архива:
> 
> ```bash
> wget https://github.com/anime-db/anime-db/archive/master.zip
> unzip master.zip && mv anime-db-master anime-db && cd anime-db
> ```

<a name="stap-3"></a>

## Шаг 3: Установка компонентов

Скачайте менеджер зависимостей [Composer](https://getcomposer.org/):

```bash
curl -s https://getcomposer.org/installer | php
```

> Если у Вас не установлен [cURL](http://ru.wikipedia.org/wiki/CURL) Вы можете установить его использовав команду:
> 
> ```bash
> sudo apt-get install curl
> ```
> Или Вы можете использовать PHP для скачивания Composer:
> 
> ```bash
> php -r "readfile('https://getcomposer.org/installer');" | php
> ```

Установите зависимости используя Composer:

```bash
php composer.phar install --prefer-dist --no-dev
```

<a name="stap-4"></a>

## Шаг 4: Запуск приложения

Для того что бы запустить приложение вам необходимо в терминале перейти в директорию в которую вы
установили приложение. В корне директории находится скрипт `AnimeDB` отвечающий за управление приложением.
Для запуска приложения выполните команду:

```bash
./AnimeDB start
```

После того как Вы запустите приложение Вы можете открыть свой браузер и перейти по адресу <http://localhost:56780/>. По
этому адресу приложение доступно для пользования.

<a name="change-port"></a>

> Если Ваш компьютер доступен в [локальной сети](http://ru.wikipedia.org/wiki/Локальная_вычислительная_сеть), то Вы
можете подключится к приложению с любого компьютера в сети используя [IP адрес](http://ru.wikipedia.org/wiki/IP-адрес)
вашего компьютера в локальной сети и [порта](http://ru.wikipedia.org/wiki/Порт_%28компьютерные_сети%29)
[56780](/ru/user/port.md). Пример: <http://192.168.0.1:56780/>. Так же Вы можете изменить порт подключения
отредактировав параметр `port` в файле `AnimeDB`. Пример установки порта
*[80](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_ref-11)*:
> 
> ```bash
> port=80
> ```

После того как Вы закончили работу с приложением Вы можете остановить его выполнив скрипт:

```bash
./AnimeDB stop
```

После обновления приложения вам может понадобится перезапустить приложение. Сделать это можно выполнив команду:

```bash
./AnimeDB restart
```

> Вы можете установить приложение как сервис что бы упростить работу с ним или запускать вместе с системой. Для этого
вам необходимо отредактировать параметр `path` в файле `AnimeDB` и указать в нем абсолютный путь к приложению.
> 
> ```bash
> path=/path/to/anime-db
> ```
> 
> Далее вам необходимо создать ссылку на скрипт в сервисах:
> 
> ```bash
> sudo ln -s /path/to/anime-db/AnimeDB /etc/init.d/AnimeDB
> ```
> 
> Теперь Вы можете запускать и останавливать приложение используя стандартный интерфейс сервисов:
> 
> ```bash
> service AnimeDB start
> ```
> 
> Для того что бы приложение запускалось при запуске системы необходимо выполнить команду:
> 
> ```bash
> sudo update-rc.d AnimeDB defaults
> ```

<a name="stap-5"></a>

## Шаг 5: Завершение установки

В приложении есть предустановленные демонстрационные записи. Рекомендуем ознакомится с ними для того что бы иметь
общее представление о приложении. После этого Вы можете удалить все демонстрационные [записи](/ru/user/item/delete.md)
и [хранилище](/ru/user/storage/delete.md).