Сайт [okfilm.com.ua](http://okfilm.com.ua/) для Оксаны
=========================================================
Версия 2018 года. Вторая версия, уже с собственным дизайном.

Сайт написан используя только html/css/js и заточен на работу с Nginx. Конфиг для Apache есть, но он годится только для запуска на локалке.
Для удобства разработки используется технология SSI (Server Side Include) в качестве примитивного шаблонизатора. Чтобы включить поддержку SSI на Apache, необходимо подключить модуль *mod_include* и добавить в инструкцию `DirectoryIndex` поиск файлов `index.shtml`.

Настройка и запуск
------------------
Для работы сайта с конфигом nginx из проекта необходимо скачать проект в директорию `/var/www/okfilm.com.ua/` и подключить конфиг. Подключить конфиг можно или командой `include /var/www/okfilm.com.ua/okfilm_2017/nginx.cfg` в главном конфиге nginx (файл `/etc/nginx/nginx.conf`). Или создав символьную ссылку на конфиг в папке подключённых сайтов nginx следующей командой:

`user@node:/etc/nginx/sites-enabled $ sudo ln -s /var/www/okfilm.com.ua/okfilm_2017/nginx.cfg okfilm.com.ua`

Кроме того, предполагается наличие папки `/var/www/shared-global` у которой открыты права на чтение и запись для всех. Это будет папка для загрузки файлов, которые смогут скачивать клиенты, перейдя по предоставленной им ссылке.

