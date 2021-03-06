# Сканирование хранилища

Для упрощения заполнения каталога был разработан механизм сканирования хранилищ. Сканирование позваляет автоматически
добавлять все записи найденные в хранилище.

> Сканирование хранилищ выполняется только для хранилищ имеющих тип:
> 
> - Папка на компьютере (локальная/сетевая);
> - Внешний накопитель (HDD/Flash/SD).

Сканирование заключается в том что приложение просматривает директории хранилищ, каждую в отдельности, и смотрит на
список файлов и папок в директории хранилища. При обнаружении папки или файла которые не привязаны к конкретной записи
в каталоге, приложение берет название папки/файла и выполняет поиск по нему в [списке
плагинов](/ru/user/general/plugins.md). Если в результате поиска найдено только одна запись, то считается что запись в
хранилище полностью соответствует найденной записи. После этого формируется новая запись в каталоге и ее поля
заполняются из найденной записи. А в [список уведомлений](/ru/user/general/notice_list.md) добавляется сообщение о том
что добавлена новая запись.

Если совпадений не найдено или их найдено больше одного, то нет возможности заполнить запись автоматически и в
уведомления добавляется сообщение о том что найдены файлы для новой записи в хранилище.

Такой механизм позволяет максимально ускорить и упростить заполнение каталога. Вы добавляете новое хранилище,
выполняете его сканирование и далее добавляете записи которые не были добавлены в результате сканирования.

Чтобы выполнить сканирование необходимо перейти на страницу списка хранилищ выбрав в главном меню: *Настройки
-> Файловые хранилища*.

![Список хранилищ](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/storage/menu.jpg)

Щелкните по кнопке в виде лупы рядом с хранилищем для которого хотите запустить сканирование:

![Сканировать хранилище](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/storage/controls.jpg)

Вы будете перенаправлены на новую страницу на которой будет выводится статус выполнения сканирование.

![Список хранилищ](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/storage/scan.jpg)

После завершения сканирования вы будете перенаправлены на страницу со списком уведомлений сгенерированных в результате
сканирования хранилища. Можете перейти на добавленные записи щелкнув на них в соответсвующий уведомлениях. Чтобы
добавить найденную запись необходимо щелкнуть по названию папки/файла в уведомлении и перейти на страницу
[поиска записи по названию](/ru/user/item/add/search_in_all.md "Поиск во всех плагинах").
