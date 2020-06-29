# PHP-Lab-2

Берем за основу предыдущую лабу, но в новом репозитории.
Есть массив в котором лежат пользователи, роль поставляем случайным образом:

$users = [
[‘name’=>’Василий’,’surname’=>’Лоханкин’ 'login' => 'Vasisualiy', 'password' => '12345', 'lang' => 'ru',’role’=>’admin’],
[‘name’=>’Афанасий’,’surname’=>’Цукерберг’ 'login' => 'Afanasiy', 'password' => '54321', 'lang' => 'en',’role’=>client],
['login' => 'Petro', ‘name’=>’Петр’,’surname’=>’Инкогнито’ ,'password' => 'EkUC42nzmu', 'lang' => 'ua',’role’=>maneger],
['login' => 'Pedrolus', ‘name’=>’Педро’,’surname’=>’Миланов’, 'password' => 'Cogito_ergo_sum', 'lang' => 'it',’role’=>’client’],
[
'login' =>'Sasha',‘name’=>’Александр’,’surname’=>’Александров’,  'password' => 'Ignorantia_non_excusat ' ],
];

Авторизацию делаем через сессии как я показывал на лекции.

При авторизации в зависимости от того какой пользователь вошел, мы приветствуем его по имени и роли,на всех страницах( делаем 2-3 штуки), на языке( русский, англицкий, украинские или итальянский) в зависимости от того какой у него язык указан в нашем массиве.
Если у пользователя нет языка, даем ему выбор из языков и выводим приветствие на его языке(сами решите как это сделать удобнее для пользователя).
После авторизации пользователь находиться как бы на “закрытой территории”, поэтому все попытки попасть туда неавторизованным пользователем должны натыкаться на переадресацию на страницу авторизации. А попытки авторизованного пользователя зайти на страницу авторизации, должны переадресовывать пользователя в его личный кабинет.

Делаем 3 страницы(файла) которые подразумевают собой личный кабинет:
admin.php
client.php
manager.php

Каждая из страниц доступна пользователю со своей ролью. Админу доступны все страницы. Менеджеру все страницы кроме админской. Клиенту только его страница. При заходе на любую из страниц проверяем права пользователя находиться на ней. 

Если прав нет, то показываем ему ошибку 403. <?php header('HTTP/1.0 403 Forbidden');?>, 
если пользователь не авторизован то переадресовываем пользователя на форму авторизации <?php  header("Location: http://lab2.ua/login.php"); ?>

Итого у вас должно получиться:
вход под разными ролями с авторизацией через сесии
смена языка внутри личного кабинета
ограничение прав доступа в зависимости от роли, для разных страниц
невозможность попасть в личный кабинет неавторизованному пользователю(на следующей лабе будем выводить туда секретную информацию)
