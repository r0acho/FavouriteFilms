# Сервис избранных фильмов

Нужно создать веб-сервис, который будет сохранять понравившиеся фильмы с КиноПоиска и давать возможность полнотекстового поиска по сохраненным фильмам. 

## Требования к сервису.

1. Должна быть возможность сохранять понравившиеся фильмы с КиноПоиска указав ссылку на страницу с фильмом. Для этого используем следующие инструменты:

    Используя фреймворк ASP.NET нужно предоставить API для получения от пользователя ссылки на понравившиеся фильмы с КиноПоиска. Не забываем добавить тесты на NUnit для тестирования API.
    После получения ссылки нужно cпарсить информацию о фильме расположенного по этой ссылке. С КиноПоиска забираем следующую информацию:
    - Название фильма.
    - Актёров.
    - Описание.
    - Дата выхода в прокат.
    - Страна производства.
    - Жанр.
    - Режиссёр.

    Парсинг нужно осуществить при помощи сервиса, разработанного на Flask с использованием BS4. Для связи с ASP.NET приложением использовать gRPC.

    После того как спарсили информацию, кладём её в Postgres.
    Информацию о “Название фильма”, “Актёров” и “Описание”, также сохраняем в elasticsearch для дальнейшего поиска среди фильмов.

2. Должна быть возможность полнотекстового поиска по сохраненным фильмам. Для этого к нашему API разработанного на ASP.NET нужно добавить API для поиска фильмов.

3. Сервис должен быть легко развертываемым, следовательно, всё нужно упаковать в docker-контейнеры и описать их запуск в docker-compose. По результату выполнения задания должны быть описаны следующие сервисы в  docker-compose:
    - API на фреймворке ASP.NET;
    - Flask-приложение с парсером;
    - Postgres;
    - opensearch.
