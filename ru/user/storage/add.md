# Добавление нового хранилища

Для того чтобы добавить новое [хранилище](/ru/user/storage/list.md#storage), необходимо перейти на страницу со
[списком хранилищ](/ru/user/storage/list.md) и выбрав в главном меню *Настройки -> Файловые хранилища*, щелкнуть по
ссылке перехода к форме добавления хранилища.

![Список хранилищ](https://raw.githubusercontent.com/anime-db/anime-db-docs/master/images/ru/storage/menu.jpg)

<a name="type"></a>
Хранилища разделяются на разные типы по своим свойствам:

- **Папка на компьютере (локальная/сетевая)**

    Дирректория с файлами на вашем компьютере или [сетевой диск](http://ru.wikipedia.org/wiki/Сетевой_диск). Также это
    может быть целый [винчестер](http://ru.wikipedia.org/wiki/Жёсткий_диск). Для приложения этот тип означает, что оно
    может читать и писать данные на хранилище в любое время.

- **Внешний накопитель (HDD/Flash/SD)**

    Можете хранить файлы сериалов и фильмов на внешнем диске, чтобы не загружать компьютер. Имея несколько внешних
    жестких дисков, вы можете поочередно подключать их при необходимости. Для приложения этот тип означает, что оно
    может читать и писать данные на хранилище, но оно может быть недоступно в данный момент времени.

- **Внешний накопитель только для чтения (CD/DVD)**

    На CD и DVD носителях можно хранить файлы, а не только закодированое
    [DVD-видео](http://ru.wikipedia.org/wiki/DVD#DVD-.D0.B2.D0.B8.D0.B4.D0.B5.D0.BE). Это более дешевая альтернатива
    внешним носителям. Однако этот метод хранения данных не позволяет редактировать данные после их записи на диск
    ([DVD-RW](http://ru.wikipedia.org/wiki/DVD-RW) не рассматривается). Приложение может считывать данные из хранилища,
    но не может на него ничего писать.

- **Накопитель видеозаписей (DVD/BD/VHS)**

   Любой видео носитель, такой как DVD-видео, [Blu-ray Disc](http://ru.wikipedia.org/wiki/Blu-ray_Disc),
   [VHS](http://ru.wikipedia.org/wiki/VHS) и т.д. Приложение никак не взаимодействует с хранилищами этого типа.

Для папок и внешних накопителей обязательно указывать путь к хранилищу.

> Пример рекомендуемой структуры хранения данных:
>
> ```
> C:\Downloads\Sailor Moon (1992) [TV]\
> ```
>
> где,
>
> - `C:\Downloads\` - путь к хранилищу аниме, содержащее несколько папок;
> - `Sailor Moon (1992) [TV]` - папка, в которой хранятся файлы аниме (видеофайлы, субтитры, обложки, звуковые дорожки
> и т.д.).

Заполните поля формы и нажмите кнопку *Добавить*, после чего будете перенаправлены на страницу со списком хранилищ.

> Для корректной работы программы храните в папках только файлы, связанные с аниме. В случае обнаружения в папке иных
> файлов или программ, возможны сбои в работе приложения.