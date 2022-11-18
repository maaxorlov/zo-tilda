# zo-tilda

## Описание.

На этой странице представлено описание функционала HTML-кодов для сайта [Здоровое образование](https://zdorovoeobrazovanie.ru/) и ссылки на страницы с кодом.

Для поиска существующего функционала воспользуйтесь [оглавлением](#Оглавление) ниже.

## Оглавление.

1. [Подключение функционала](#Подключение-функционала)
2. [Кнопка входа, регистрации и возврата в личный кабинет.](#Кнопка-входа-регистрации-и-возврата-в-личный-кабинет)
3. [Проброс UTM-меток при переходе по ссылкам на сайте.](#Проброс-utm-меток-при-переходе-по-ссылкам-на-сайте)
4. [Личный кабинет.](#Личный-кабинет)
5. [Заполнение скрытых полей при регистрации на мероприятие.](#Заполнение-скрытых-полей-при-регистрации-на-мероприятие)
6. [Страница трансляции.](#Страница-трансляции)
___

## Подключение функционала.

Для подключения необходимого функционала нужно обладать доступом к [конструктору сайта на Тильде](https://tilda.cc/projects/). Его можно запросить у руководителя IT-отдела.

***!!! ATTENTION !!!***

Почти все скрипты основаны на получении элементов HTML-разметки Тильды. В Тильде есть возможность присваивать блокам кастомный className, что позволяет в упрощенном формате получить доступ в редактированию этих элементов. Присваивание кастомного названия класса - внутренняя настройка блока в Тильде. Из этого следует, что иногда мало просто вставить скрипт в нужное место. Порой необходимо добавить нужному блоку в Тильде используемые в скрипте названия классов (иногда даже создать элемент с конкретными размерами и т.д.). Также скрипт может использовать переменные и константы, заданные в других блоках. Они не были добавлены в общий скрипт (который хранится отдельно в alias-блоках), т.к. хранились в блоках, которые менялись часто, например, константа с кодом конкретного мероприятия). Более того, иногда Тильда выкатывает обновления, меняя HTML-разметку. Логика работы скрипта позволяет сохранять заданный функционал, но важно при добавлении всегда следить за тем, чтобы скрипт корректно получал доступ к необходимым элементам HTML-разметки. Если что-то не работает, первым делом необходимо отследить элементы, которые использует скрипт (т.е. посмотреть код скрипта, вникнуть в суть), убедиться в корректности их получения. Это касается всех блоков и в дальнейшем нигде в описании не упоминается, что для конкретного блока нужно настроить конкретный вид.

***!!! ATTENTION !!!***

Перейдите на страницу, на которую хотите добавить функционал. Нажмите "Все блоки" внизу страницы.

![](https://static.tildacdn.com/tild3130-6162-4263-b664-383064353962/1.jpg)

Открывшееся слева меню прокрутите в самый низ до блока "Другое". Нажмите. В открывшемся правее меню выберите блок "HTML-код". Нажмите.

![](https://static.tildacdn.com/tild3662-3161-4961-b739-336136303135/2.jpg)

Появится пустой блок для вставки кода. Нажмите "Контент". Вставьте скопированный код в поле с левой стороны открывшегося блока. Не забудьте сохранить изменения при выходе из редактирования блока. Нажмите "Сохранить и закрыть".

![](https://static.tildacdn.com/tild3936-3832-4236-b733-626638313263/3.jpg)

![](https://static.tildacdn.com/tild3864-3132-4438-b639-303938356232/4.jpg)

Не забудьте опубликовать изменения при выходе из редактирования страницы. Нажмите "Опубликовать".

![](https://static.tildacdn.com/tild3837-3133-4439-a664-623139383431/5.jpg)
[⬆ к оглавлению](#Оглавление)
___

## Кнопка входа, регистрации и возврата в личный кабинет.

По сути, Тильда реализована так, что при переходе со страницы личного кабинета (ЛК) на главную страницу отображаются кнопки:

![](https://static.tildacdn.com/tild3230-3434-4236-b932-623235376361/1.jpg)

Кнопка "Войти" ведет на страницу с формой ввода данных для входа в ЛК, а кнопка "Зарегистрироваться" - на страницу с формой регистрации. Если пользователь уже авторизован, то Тильда автоматически перебрасывает его с указанных страниц в ЛК. С точки зрения уже авторизованных пользователей, некорректно видеть кнопку регистрации. Поэтому скриптом скрываем кнопку для уже авторизованных пользователей. Признаком авторизации является куки "logCookieZO", который записывается при входе пользователя в ЛК, а удаляется при нажатии на кнопку выхода из учетной записи. Скрипт можно найти в файле [from-main-page-to-lk-buttons.html](https://github.com/maaxorlov/zo-tilda/blob/master/from-main-page-to-lk-buttons.html). Так выглядят кнопки для авторизованных пользователей при использровании скрипта:

![](https://static.tildacdn.com/tild3732-3461-4536-b434-366466356464/2.jpg)
[⬆ к оглавлению](#Оглавление)
___

## Проброс UTM-меток при переходе по ссылкам на сайте.
В рассылках пользователю могут отправляться ссылки с UTM-метками. Для сохранения возможности идентификации конкретного пользователя и его действий на сайте при переходе по различным ссылкам необходимо реализовать добавление UTM-меток к ссылкам на сайте. Скрипт можно найти в файле [adding-utm-tags-to-links.html](https://github.com/maaxorlov/zo-tilda/blob/master/adding-utm-tags-to-links.html).

[⬆ к оглавлению](#Оглавление)
___

## Личный кабинет.

В этом разделе представлены несколько скриптов, каждый со своим функционалом. Идейно их объединяет одно - подтягиваются различные данные о конкретном пользователе из книги Даши-Мейл, хранящей информацию обо всех зарегистрированных пользователях (наша "замена" базе данных). Текстовое описание получилось бы достаточно объемным, поэтому для использования рекомендуется просмотреть [видео](https://www.youtube.com/watch?v=pVttncinWAs). Скрипт можно найти в файле [lk.html](https://github.com/maaxorlov/zo-tilda/blob/master/lk.html). Изображения ниже поясняют работу КЛАДРа:

![](https://static.tildacdn.com/tild3633-3331-4663-b536-613635636266/3.jpg)

![](https://static.tildacdn.com/tild3966-6633-4564-a665-376363663939/4.jpg)

![](https://static.tildacdn.com/tild6237-3563-4466-b231-626231376631/5.jpg)
[⬆ к оглавлению](#Оглавление)
___

## Заполнение скрытых полей при регистрации на мероприятие.

При подаче заявки на участие в мероприятии изначально контент страницы скрыт прелоадером (значком загрузки страницы). За кадром идет проверка пользователя в общей базе на предмет заполнения всех необходимых для участия в мероприятии данных. Если данных нет, то появляется сообщение с необходимостью перейти в ЛК и заполнить обязательные для участия данные. При наличии всех необходимых данных прелоадер исчезает, открывая содержимое страницы. Полученными данными заполняются скрытые поля "phone", "основная_специализация", "федеральный_округ", "город", "name" в форме регистрации пользователя для участия в мероприятии. Скрипт можно найти в файле [creating-and-filling-in-hidden-fields-for-registration-for-an-event.html](https://github.com/maaxorlov/zo-tilda/blob/master/creating-and-filling-in-hidden-fields-for-registration-for-an-event.html).

[⬆ к оглавлению](#Оглавление)
___

## Страница трансляции.

По сути, это даже больше отдельный мини-проект, чем просто скрипт. Однажды возникла необходимость найти или реализовать чат с технологией Single Sign-On. Выбор пал на [ChatBro](https://www.chatbro.com/ru/) из-за достаточно обильного функционала в рамках бесплатной версии, а главное - с технологией SSO. Впоследствии был расширен функционал в основном для нужд модераторов. Текстовое описание получилось бы достаточно объемным, поэтому для использования рекомендуется просмотреть [видео](https://www.youtube.com/watch?v=GIxEGxM5t6I). Скрипт можно найти в файле [broadcast-page.html](https://github.com/maaxorlov/zo-tilda/blob/master/broadcast-page.html).

[⬆ к оглавлению](#Оглавление)
___
