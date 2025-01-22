# Домашнее задание к занятию «Базы данных, их типы» - Макану Александр


### Задание 1

#### 1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков
Для задачи, связанной с бюджетированием и аналитикой, оптимальным выбором будет реляционная СУБД (например, PostgreSQL, Microsoft SQL Server, Oracle Database). Причины:

Реляционные СУБД обеспечивают строгую структуру данных и целостность благодаря транзакциям (ACID-свойствам).
Они подходят для сложных аналитических запросов и имеют встроенные возможности для работы с финансовыми данными.
Поддержка процедур и триггеров позволяет автоматизировать вычисления и гарантировать корректность данных.

#### 1.2. СУБД для лендингов и CRM
Для лендингов: Рекомендуется использовать NoSQL СУБД типа MongoDB или Firebase Realtime Database. 

Причины:

Легко масштабируются по горизонтали.
Гибкость структуры данных позволяет быстро адаптироваться под изменения в требованиях.
Для CRM: Оптимально использовать реляционную СУБД (например, PostgreSQL или MySQL). CRM нуждаются в чёткой структуре данных, транзакционности и сложных связях между таблицами.

#### 1.3. СУБД для базы по корпоративным нормам и правилам
Для такой задачи лучше всего подойдёт реляционная СУБД (например, SQLite или PostgreSQL). 

Причины:

Простая структура данных.
Возможность легко добавлять и обновлять данные.
Интеграция с другими системами (например, через API или экспорт в различные форматы).

#### 1.4. СУБД для логистики
Для логистики оптимально использовать графовые СУБД (например, Neo4j).

Причины:

Быстрая работа со связями (например, маршруты доставки или распределение курьеров).
Гибкость в моделировании сложных сетевых структур (объекты, маршруты, точки доставки).


---

### Задание 2

#### 2.1. Пользователь пополняет баланс счёта телефона
Для успешного завершения транзакции пополнения баланса телефона необходимо выполнить следующие шаги:

Шаги для завершения транзакции:
Ввод данных пользователя:
Пользователь вводит номер телефона, сумму пополнения и способ оплаты (например, карта или электронный кошелёк).

Проверка корректности данных:
Система проверяет, существует ли указанный номер телефона и валидна ли введённая сумма.

Если данные некорректны, транзакция завершается с ошибкой.
Резервирование средств:
Система инициирует блокировку указанной суммы на платёжной карте пользователя или списывает её с электронного кошелька.

На этом этапе важно убедиться, что у пользователя достаточно средств.
Создание транзакции:
В базе данных создаётся запись о транзакции с её текущим статусом (например, "в обработке").

Пополнение баланса:
Система передаёт запрос в биллинговую платформу оператора связи, которая зачисляет средства на баланс указанного телефона.

Подтверждение и завершение:

Если оператор подтвердил пополнение, статус транзакции обновляется на "успешно завершено", средства окончательно списываются с карты/кошелька, и пользователь получает уведомление.
Если оператор отказал (например, техническая ошибка), средства размораживаются или возвращаются пользователю, а статус транзакции обновляется на "отклонено".


---

### Задание 3

#### 3.1. Пять преимуществ SQL-систем по отношению к NoSQL
Строгая структура данных

SQL-системы используют фиксированные схемы (schema-based), что обеспечивает целостность данных и упрощает их управление.
Это особенно важно для задач, где важны чёткая структура и строгие типы данных, например, в финансовых системах.
Поддержка сложных запросов

SQL предоставляет мощный язык запросов, позволяющий выполнять сложные операции (JOIN, вложенные запросы, агрегатные функции).
Это делает SQL идеальным выбором для аналитики и сложной обработки данных.
Гарантия транзакционной целостности (ACID-свойства)

SQL-системы гарантируют атомарность, согласованность, изолированность и долговечность операций.
Это особенно важно в сценариях, где нельзя допустить потерю данных или некорректные состояния (например, банковские системы).
Поддержка стандартизированных инструментов

SQL поддерживается множеством популярных инструментов для аналитики, отчётности и визуализации (Power BI, Tableau).
Это упрощает интеграцию и делает работу с SQL удобной для специалистов разных уровней.
Развитая экосистема и зрелость

SQL-системы, такие как PostgreSQL, MySQL и Oracle, существуют десятилетиями, обладают обширной документацией, активным сообществом и поддержкой.
Это снижает риски внедрения и эксплуатации.



---


### Задание 4

#### Критерии выбора СУБД
Тип и структура данных:

Если данные имеют строгую структуру и важна транзакционная целостность (ACID), то стоит выбрать NewSQL (например, Google Spanner, CockroachDB).
Если данные неструктурированные или слабо структурированные, лучше использовать NoSQL (например, Apache Cassandra, MongoDB, или HBase).
Объём данных и масштабируемость:

Для обработки петабайтов данных и динамического добавления вычислительных мощностей СУБД должна поддерживать горизонтальное масштабирование.
Тип запросов:

Для аналитических задач подойдут OLAP-ориентированные базы данных, такие как ClickHouse, Apache Druid или Google BigQuery.
Для задач, требующих быстрой обработки записей, подойдут транзакционные базы данных, такие как Cassandra (NoSQL) или CockroachDB (NewSQL).
Обработка в реальном времени или пакетная обработка:

Для обработки потоков данных в реальном времени: Apache Kafka + ksqlDB или Redis Streams.
Для пакетной обработки больших массивов данных: Hadoop HDFS или Snowflake.
Простота интеграции с вычислительными системами:

База данных должна легко интегрироваться с инструментами распределённых вычислений, такими как Apache Spark, Hadoop, или Flink.


#### Модель распределённых вычислений
Для использования 1000 машин в вычислениях подходят следующие модели:

Apache Spark (лучший выбор для большинства задач):

Почему:
Apache Spark отлично масштабируется и работает как с batch (пакетной), так и с stream (поточной) обработкой.
Поддерживает широкую интеграцию с разными типами СУБД (SQL, NoSQL, HDFS).
Использует память (RAM) для ускорения вычислений, что делает его быстрее по сравнению с Hadoop MapReduce.
Имеет встроенные модули для SQL-запросов, обработки графов (GraphX), машинного обучения (MLlib) и потоковой обработки (Spark Streaming).
Сценарии:
Анализ больших данных, моделирование, прогнозирование.
Интеграция с Data Lake для построения сложных аналитических систем.

Hadoop (если важна долговременная обработка данных):

Почему:
Hadoop MapReduce используется для пакетной обработки больших объёмов данных.
HDFS (Hadoop Distributed File System) обеспечивает надёжное хранение данных с репликацией.
Недостатки:
Медленнее, чем Spark, так как основная обработка идёт через диск, а не через память.

Apache Flink (для задач реального времени):

Почему:
Подходит для обработки потоков данных с минимальными задержками.
Гарантирует обработку событий даже при сбоях (exactly-once processing).
Сценарии:
Мониторинг данных в реальном времени, онлайн-рекомендации, обнаружение мошенничества.

Distributed SQL Engine (Presto, Trino):

Почему:
Быстро выполняет SQL-запросы на распределённых системах.
Подходит для анализа больших объёмов данных в распределённой среде.

