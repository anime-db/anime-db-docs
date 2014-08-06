# Сборка на OS Windows из исходников

Описание установки приложения **Anime DB** на OS Windows на примере Windows 7.
Процесс установки приложения в других версиях OS Windows будет мало отличатся от описанных шагов.

<a name="stap-1"></a>

## Шаг 1: Установка PHP

Приложение написано на языке программирования [PHP](http://ru.wikipedia.org/wiki/Php) и для работы ему необходим PHP
[интерпретатор](http://ru.wikipedia.org/wiki/Интерпретатор). В случае OS Windows есть скомпилированная версия не
требующая установки в системе и потому приложение на Windows легко устанавливается.

Зайдите на страницу загрузки [PHP для OS Windows](http://windows.php.net/download/). Если вы пользуетесь OS Windows XP,
то вы можете пользоваться только PHP версии 5.4. Более ранняя версия недопустима для работы приложения, а в более новой
версии разработчики PHP отказались от поддержки OS Windows XP. Таким образом вам необходимо выбрать версию PHP
интерпретатора и скачать ее:

- [**PHP 5.5** VC11 x86 Non Thread Safe](http://windows.php.net/download/#php-5.5-nts-VC11-x86) *(для Vista и старше) [x86](http://ru.wikipedia.org/wiki/X86)*
- [**PHP 5.5** VC11 x64 Non Thread Safe](http://windows.php.net/download/#php-5.5-nts-VC11-x64) *(для Vista и старше) [x64](http://ru.wikipedia.org/wiki/X86-64)*
- [**PHP 5.4** VC9 x86 Non Thread Safe](http://windows.php.net/download/#php-5.4-nts-VC9-x86) *(для XP и старше) [x86](http://ru.wikipedia.org/wiki/X86)*

Загрузив архив распакуйте его и зайдите в созданную директорию. Создайте в директории текстовый файл с именем
`php.ini` и запишите в него следующие параметры запуска интерпретатора:

```ini
display_errors = Off
date.timezone = Europe/Moscow
upload_tmp_dir = "tmp"
extension_dir = "ext"

extension = php_com_dotnet.dll
extension = php_curl.dll
extension = php_gd2.dll
extension = php_intl.dll
extension = php_mbstring.dll
extension = php_openssl.dll
extension = php_pdo_sqlite.dll
extension = php_tidy.dll
extension = php_fileinfo.dll
```

Эти параметры определяют список расширений которые будут подключены и основные параметры. Параметр `date.timezone`
определяет временную зону в которой вы находитесь. Если ваше временная зона отличается от временной зоны города Москва
в Россие, то вы можете указать свою временную зону.
[Список поддерживаемых временных зон](http://www.php.net/manual/ru/timezones.php).

<a name="stap-2"></a>

## Шаг 2: Установка приложения

Загрузите [архив](https://github.com/anime-db/anime-db/archive/master.zip) с приложением со страницы разработки
приложения на [GitHub](https://github.com/anime-db/anime-db).

Приложение работает портативно и не требует установки в системе, вы можете установить приложение в любую директорию на
своем компьютере, в том числе на USB-носитель.

> Приложение запущенное с USB-носитель может тормозить из-за недостаточной скорости обмена данными. Рекомендуется
использовать USB-носител с поддержкой [USB 3.0](http://ru.wikipedia.org/wiki/USB#USB_3.0) и скоростью обмена данными
от 100 Мб/с.

К сожалению указать можно не любой директорию. Приложение некорректно работает с путями в составе которых
присутствуют символы не входящие в таблицу [ASCII](http://www.asciitable.com/ "Таблица ASCII символов"). То есть
необходимо что бы путь к приложению содержал буквы латинского алфавита и спецсимволы.
Пример допустимых путей:

- `C:\Program Files\`
- `C:\Users\Public\Desktop\`
- `E:\`

Пример НЕ допустимых путей:

- `C:\Documents and Settings\Администратор\Рабочий стол\`
- `C:\Documents and Settings\Администратор\Мои документы\`

<a name="stap-3"></a>

## Шаг 3: Установка компонентов

Скачайте менеджер зависимостей [Composer](https://getcomposer.org/):

```bash
php -r "readfile('https://getcomposer.org/installer');" | php
```

Установите зависимости используя Composer:

```bash
php composer.phar install --prefer-dist --no-dev
```

<a name="stap-4"></a>

## Шаг 4: Установка монитора

Скачайте последнюю версию монитора с [официального сайта](http://anime-db.org/ru/releases/) и распакуйте архив с
монитором в корневую папку приложения или соберите его из [исходников](https://github.com/anime-db/monitor).

![Скачать монитор](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/install/download_monitor.jpg)

> Монитор ожидает что PHP установлен в директорию `bin\php\`. Если вы установили и
[зарегистрировали](http://www.php.net/manual/en/faq.installation.php#faq.installation.addtopath) PHP в системе, то вам
необходимо отредактировать файл `config.ini`, расположенный в корневой директории приложения:
>
> ```ini
> php=php
> ```

<a name="stap-5"></a>

## Шаг 5: Запуск приложения

После того как вы распаковали архив с приложением, откройте директорию с приложением. В корне паки будет находится
монитор запуска приложения `AnimeDB.exe`. После запуска монитора, в трее(рядом с часами), появится значок приложения и
откроется браузер на адресе <http://localhost:56780/>.

![Трай](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/en/install/tray.jpg)

<a name="change-port"></a>

> Если Ваш компьютер доступен в [локальной сети](http://ru.wikipedia.org/wiki/Локальная_вычислительная_сеть), то вы
можете подключится к приложению с любого компьютера в сети используя [IP адрес](http://ru.wikipedia.org/wiki/IP-адрес)
вашего компьютера в локальной сети и [порта](http://ru.wikipedia.org/wiki/Порт_%28компьютерные_сети%29)
[56780](/ru/user/port.md). Пример: <http://192.168.0.1:56780/>. Так же вы можете изменить порт подключения
отредактировав параметр `port` в файле `config.ini`. Пример установки порта
*[80](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#cite_ref-11)*:
> 
> ```ini
> port=80
> ```

Вам может понадобится остановить работу приложения или перезапустить его, например после его обновления. Для этого
щелкните правой кнопкой мыши по значку приложения в трее и выберете нужный пункт в меню.

![Перезапуск приложения](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/install/tray_restart.jpg)

Для того что бы выключить приложение, недостаточно закрыть вкладку в браузере. Если вы хотите полностью остановить
приложение, то вам необходимо щелкнуть правой кнопкой мыши по значку в трее и выбрать соответствующий пункт меню.

![Выключение приложения](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/install/tray_exit.jpg)

<a name="stap-6"></a>

## Шаг 6: Завершение установки

В приложении есть предустановленные демонстрационные записи. Рекомендуем ознакомится с ними для того что бы иметь
общее представление о приложении. После этого вы можете удалить все демонстрационные [записи](/ru/user/item/delete.md)
и [хранилище](/ru/user/storage/delete.md).