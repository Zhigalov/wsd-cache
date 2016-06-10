# Материалы доклада про кеширование

### Название
"Осторожно, закешированно!"

### Описание
В суматохе дней очень важно иногда остановиться, отдышаться, оглянуться назад... и заняться оптимизацией производительности! В своем рассказе я дам несколько простых рецептов с чего начать, как и где можно использовать кеширование. Расскажу об инструментах, которые помогут внедрить кеширование на вашем проекте. Дам несколько советов, которые помогут ~~не выстрелить в ногу~~ использовать кеш максимально эффективно.


### Содержание
* Мы не будем рассказывать о кешировании в привычном смысле (кешировани HTTP запросов)
* Фронтендер - пишет код не только в браузере, поэтому в докладе будет про кеширование на ноде
* Показать проблему без кеша
  * Высокая нагрузка
    * Длинные / долгие запросы
    * Кеширование результатов вычисления: перегруппировки (пример с расписанием, искусственный пример с кофе, кеширование оффсетов элементов чтобы вычислять показывать ли элемент при скролле. Инвалидировать при ресайзе окна)
* Решение проблем:
  * Батчинг запросов (кеширвоание промиса, минусы - фейл группы запросов. Лечится ретраями)
  * Собственно кеширование
    * Концепция кеширования
    * Реализации
      * Переменных
      * lru-cache (lru - один из алгоритмов кеширования. Про остальные - читайте сами)
      * redis
* Эффективность кеша (На примере кеширования персональных данных)
* Разогрев кеша
  * SPA prefetch (возвращать html вместе с данными чтобы не делать запросы на старте)
* Антипример (про то как можно использовать кеш в неподходящих задачах. Пример: исполь
  * Прием
    * Абстрактная кеширующая модель
    * Оно должно быль дополнительной компонентой которую легко выключить
    * Закладывать в архитектуру возможность смены движка кеширования
  * Кеш это решение проблем, но в идеальном мире проблем быть не должно. Бекенд должен работать быстро (мб кешировать на своей стороне)
