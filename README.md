Сайт [okfilm.com.ua](http://okfilm.com.ua/) для Оксаны
=========================================================
Версия 2018 года. Вторая версия, уже с собственным дизайном.

Сайт написан используя только html/css/js и заточен на работу с Nginx. Конфиг для Apache есть, но он годится только для запуска на локалке.
Для удобства разработки используется технология SSI (Server Side Include) в качестве примитивного шаблонизатора. Чтобы включить поддержку SSI на Apache, необходимо подключить модуль *mod_include* и добавить в инструкцию `DirectoryIndex` поиск файлов `index.shtml`.

## Настройка и запуск
Для работы сайта с конфигом nginx из проекта необходимо скачать проект в директорию `/var/www/okfilm.com.ua/` и подключить конфиг. Подключить конфиг можно или командой `include /var/www/okfilm.com.ua/okfilm_2017/nginx.cfg` в главном конфиге nginx (файл `/etc/nginx/nginx.conf`). Или создав символьную ссылку на конфиг в папке подключённых сайтов nginx следующей командой:

`user@node:/etc/nginx/sites-enabled $ sudo ln -s /var/www/okfilm.com.ua/okfilm_2017/nginx.cfg okfilm.com.ua`

Кроме того, предполагается наличие папки `/var/www/shared-global` у которой открыты права на чтение и запись для всех. Это будет папка для загрузки файлов, которые смогут скачивать клиенты, перейдя по предоставленной им ссылке.

## Подготовка фотографий для портфолио
Чтобы подготовить фотографии для портфолио, создаём экшен в фотошопе, который включает в себя следующие стадии:  
1. Вызов сценария "Большое фото в галерею сайта" ([скачать](utilities/Photoshop/%D0%91%D0%BE%D0%BB%D1%8C%D1%88%D0%BE%D0%B5%20%D1%84%D0%BE%D1%82%D0%BE%20%D0%B2%20%D0%B3%D0%B0%D0%BB%D0%B5%D1%80%D0%B5%D1%8E%20%D1%81%D0%B0%D0%B9%D1%82%D0%B0.jsx));
2. Обрезка фото с соотношением сторон 23x20 (инструмент "Рамка");
3. Вызов сценария "Маленькие превью в галерею сайта" ([скачать](utilities/Photoshop/%D0%9C%D0%B0%D0%BB%D0%B5%D0%BD%D1%8C%D0%BA%D0%B8%D0%B5%20%D0%BF%D1%80%D0%B5%D0%B2%D1%8C%D1%8E%20%D0%B2%20%D0%B3%D0%B0%D0%BB%D0%B5%D1%80%D0%B5%D1%8E%20%D1%81%D0%B0%D0%B9%D1%82%D0%B0.jsx));
4. Закрыть файл без сохранения.

Причём для второго шага (рамка) в экшене включена опция "открытие деалогового окна". Так что, при обработке фоток, обрезка для каждой фотки задаётся вручную. Это позволяет сделать красиво кадрированные миниатюры без отсечения голов.  
