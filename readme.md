# Цей репозиторій опиує ДСОМ (Державну Систему Онлайн Моніторингу) з точки зору загального контексту, контейнерів та коду.

Нижче перелік запитань і посилання на розділи з відповідною інформацією:



| питання | відповідь |
|---|---|
| Діаграми рівня C4 (або еквівалент): Context/Container/Component + deployment. | Папки [context](context/readme.md#context-diagram) та [containers](containers/readme.md#main-flow-diagram) мають в файлах readme.md діаграми з деталізацією, близькою до відповідних рівней С4, папка [code](code) описує загальні архітектурни практики системи |
| Середовища (dev/test/stage/prod), де й що крутиться. | В даний момент активне лише dev середовищє з певними обмеженнями. Середовища описані у вигляді Infrastructure as a code, більше інформації в розділі [CI/CD](code/readme.md#cicd) |
| Техстек по кожному сервісу: мови/фреймворки/версії (бек/фронт), БД (тип/версія), кеш (Redis тощо), черги/шина (Kafka/Rabbit), пошук (Elastic/OpenSearch), файлове сховище (S3/MinIO). | Техстек контейнерів за замовченням подано у розділі [commonly used software](containers/readme.md#commonly-used-software). Конфігурації окремих контейнерів (наявність фронту/беку/бази) подані у папках, дочірніх до папки [containers](containers), так само як і можливі девіації від базових |
| Архітектурні патерни: моноліт/мікросервіси, sync/async взаємодія. | Опис [взаємодій](code/readme.md#in-cluster-communications), [опис ахрітектури](containers/readme.md#container-architecture) |
| НФ-вимоги: навантаження, перформанс-цілі, SLO/SLI, масштабування, HA. | Високорівневі цілі [подано тут](context/readme.md#main-implemented-nfrs-and-challenges) |
| ERD/схема БД, міграції. | Кожна з груп сервісів що має базу має відповідну ERD діаграму, наприклад [EventsWarehousing](containers/EventWarehousing/readme.md#components)  |
| Каталог подій/черг (схеми Avro/JSON, контракти). |  Кожна з груп сервісів що слугує РПЦ хостом або слухає події має відповідну ERD діаграму, наприклад [EventsWarehousing](containers/EventWarehousing/readme.md#listen-as)  |
| Перелік зовнішніх інтеграцій: протоколи, точки входу, контракти, SLA/обмеження. | Відсутні |
| API: OpenAPI/Swagger або Postman-колекції, вебхуки. | Дивись поруч з [context](context/readme.md#context-diagram)  |
| AuthN/AuthZ (OIDC/SAML/Keycloak/SSO), ролі/права. | правила доступу до системи описані в секціі [authorization](code/readme.md#authorization)  |
| Secrets management (Vault/KMS), політики доступу. | політика роботи з секретами описана в секціі [secrets-management-and-security](code/readme.md#secrets-management-and-security) |
| Мережева сегментація, ізоляція середовищ. | дивись секцію [networking](code/readme.md#networking) |


