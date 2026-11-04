flowchart LR
    RAW["Сырой ответ<br/>опрос / вебхук / скрапинг"] --> DEDUP{"dedupe_key<br/>уже встречался?"}
    DEDUP -->|да| DROP["отбросить"]
    DEDUP -->|нет| NORM["Нормализация<br/>source, observed_at, sequence,<br/>flight_instance_id, status, severity"]
    NORM --> OUTBOX["Транзакционный Outbox"]
    OUTBOX --> STREAM["Долговечный поток событий"]
    STREAM --> OP["Операционный потребитель<br/>состояние поездки"]
    STREAM --> IX["Потребитель индекса<br/>поисковые представления"]
    STREAM --> NOTIF["Маршрутизатор уведомлений"]
    STREAM --> REB["Оркестратор перебронирования"]
