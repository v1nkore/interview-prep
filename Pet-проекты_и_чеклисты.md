# Пет-проекты и чек-лист подготовки к офферу Senior .NET

Порядок проектов = порядок разделов в [«200 ответов · Senior Backend .NET»](200_ответов_Senior_NET.html).
Логика: изучаешь раздел → разбираешь проект → возвращаешься к вопросам.

Прогресс отмечай прямо здесь: `[ ]` → `[~]` в работе → `[x]` разобрано и можешь объяснить своими словами.

---

## Карта: раздел 200 ответов → проект

| Раздел | Тема | Вопросов | Проект | Чек-лист |
|---|---|---|---|---|
| 1 | C# и .NET runtime | 20 | [TtlCache](dotnet-petprojects/TtlCache/) | п.1 |
| 2 | Async и многопоточность | 16 | [TtlCache](dotnet-petprojects/TtlCache/) | п.1 |
| 3 | ASP.NET Core | 12 | [AspNetLab](dotnet-petprojects/AspNetLab/) | п.5 |
| 4 | EF Core | 12 | [EfCoreLab](dotnet-petprojects/EfCoreLab/) | п.6 |
| 5 | Базы данных и SQL | 14 | [EfCoreLab](dotnet-petprojects/EfCoreLab/) | п.6 |
| 6 | ООП, SOLID, паттерны | 14 | [SolidMap](dotnet-petprojects/SolidMap/) | — |
| 7 | Архитектура: DDD, Clean, CQRS | 12 | [CleanLab](dotnet-petprojects/CleanLab/) | п.14 |
| 8 | Микросервисы и распределённые системы | 16 | [OrderFlow](dotnet-petprojects/OrderFlow/) | п.2 + п.3 |
| 9 | Очереди сообщений: Kafka и RabbitMQ | 12 | [OrderFlow](dotnet-petprojects/OrderFlow/) | п.2 + п.3 |
| 10 | API: REST и gRPC | 12 | [GrpcLab](dotnet-petprojects/GrpcLab/) | п.7 |
| 11 | Кэширование и Redis | 8 | [RedisLab](dotnet-petprojects/RedisLab/) | п.13 |
| 12 | Контейнеры, Kubernetes, CI/CD | 12 | [K8sLab](dotnet-petprojects/K8sLab/) | п.9 |
| 13 | Тестирование | 10 | [TestingLab](dotnet-petprojects/TestingLab/) | п.10 |
| 14 | Производительность и highload | 10 | [PerfLab](dotnet-petprojects/PerfLab/) | п.11–12 |
| 15 | Наблюдаемость и эксплуатация | 6 | [ObservabilityLab](dotnet-petprojects/ObservabilityLab/) | п.8 |
| 16 | System design (открытые задачи) | 6 | [SystemDesign](dotnet-petprojects/SystemDesign/) | п.4 |
| 17 | Поведенческие и лидерские | 8 | [Behavioral](dotnet-petprojects/Behavioral/) | п.15 |

Всего 200 вопросов, 17 разделов, 14 проектов (11 кодовых + 3 письменных).

Вспомогательная карта: [architecture-map.md](dotnet-petprojects/architecture-map.md) — паттерн → проект → конкретный файл/класс.
Обзор всех проектов: [dotnet-petprojects/README.md](dotnet-petprojects/README.md).

---

## Чек-лист по пунктам

Порядок волн — как в README репозитория. Одна волна = 1–2 недели.

### п.1 — TtlCache · потокобезопасный кэш с TTL
- [ ] `dotnet test` в `TtlCache/` — зелёное
- [ ] `dotnet run --project src/TtlCache.Demo -c Release` — увидеть своими глазами
- [ ] Бенчмарки `benchmarks/` — есть цифры, а не ощущения
- [ ] Конспект «что понял» 5–10 строк своими словами
- Закрывает разделы 1–2 (36 вопросов — самый тяжёлый блок)

### п.2 + п.3 — OrderFlow · Kafka, Outbox, Saga, Polly
- [ ] `docker compose up -d` (Postgres + Kafka)
- [ ] Разобрать Outbox: почему нельзя просто писать в БД и слать в Kafka
- [ ] Идемпотентность обработчика — своими словами
- [ ] Saga: компенсации, что при падении на шаге N
- [ ] Polly: какие стратегии и зачем retry с jitter
- Закрывает разделы 8–9 (28 вопросов)

### п.4 — SystemDesign · 5 письменных разборов
- [ ] Проговорить вслух по шаблону из `SystemDesign/README.md`
- [ ] 01-платёжный шлюз
- [ ] 02-URL-shortener
- [ ] 03-нотификации
- [ ] 04-вебхуки
- [ ] 05-feed
- [ ] На каждом: назвать, что упадёт первым при ×10
- Закрывает раздел 16 (6 вопросов)

### п.5 — AspNetLab · pipeline, DI, BackgroundService
- [ ] `dotnet test` и `dotnet run --project src/AspNetLab.Api`
- [ ] Captive dependency в `DiTraps/` — почему это ловушка
- [ ] Порядок middleware, `CorrelationIdMiddleware`, `RequestTimingMiddleware`
- [ ] `ValidateRecipientAttribute` — фильтры vs middleware, когда что
- Закрывает раздел 3 (12 вопросов)

### п.6 — EfCoreLab · EF Core и SQL на реальном Postgres
- [ ] `docker compose up -d` (Postgres)
- [ ] Сценарий N+1: увидеть число запросов через `QueryCountingInterceptor`
- [ ] Change tracking vs `AsNoTracking` — замер
- [ ] Оптимистичная блокировка через `xmin`
- [ ] `EXPLAIN ANALYZE`, индексы составные/покрывающие
- Закрывает разделы 4–5 (26 вопросов)

### п.7 — GrpcLab · gRPC против REST с замером
- [ ] Поднять оба транспорта (5501 gRPC / 5502 REST), снять цифры
- [ ] Deadline и cancellation — что клиент делает при таймауте
- [ ] Interceptor: где логирование и трассинг
- [ ] Streaming — когда вообще нужен
- Закрывает раздел 10 (12 вопросов)

### п.8 — ObservabilityLab · OTel поверх OrderFlow
- [ ] Сквозной трейс через Kafka до Jaeger — открыть и проследить
- [ ] Prometheus + Grafana по `OrderFlow/prometheus.yml`
- [ ] Что добавлять в спаны, а что — только метрики
- Закрывает раздел 15 (6 вопросов)

### п.9 — K8sLab · kind, Helm, CI/CD
- [ ] `kind` кластер, задеплоить AspNetLab
- [ ] Probes: readiness против liveness, почему нельзя одно и то же
- [ ] Limits и requests — из чего исходить
- [ ] `helm` install/upgrade и **откат вживую**
- [ ] `github-actions-ci.yml` — глянуть и понять
- Закрывает раздел 12 (12 вопросов)

### п.10 — TestingLab · Testcontainers, реальный Postgres в тесте
- [ ] `dotnet test` — тесты поднимают настоящий Postgres
- [ ] Отличить unit / integration / e2e на своих примерах
- [ ] Что тестируем в AspNetLab `tests/ApiTests.cs`
- Закрывает раздел 13 (10 вопросов)

### п.11–12 — PerfLab · аллокации и нагрузка
- [ ] BenchmarkDotNet: убрать аллокации с горячего пути (Span)
- [ ] NBomber: thread pool starvation вживую
- [ ] Отчёты в `BenchmarkDotNet.Artifacts/results/` — прочитать свои цифры
- Закрывает раздел 14 (10 вопросов)

### п.13 — RedisLab · cache-aside, stampede, инвалидация
- [ ] `docker compose up -d` (Redis 7)
- [ ] Три защиты от stampede — понимать, чем отличаются
- [ ] Инвалидация: TTL против явной, и почему это источник багов
- Закрывает раздел 11 (8 вопросов)

### п.14 — CleanLab · Clean Architecture + CQRS
- [ ] Направление зависимостей `Api → Infrastructure → Application → Domain`
- [ ] Value Object `Money`, агрегат `Debt`, фабрика `Debt.Open`
- [ ] Доменные события и MediatR
- [ ] «DIP = вся суть Clean Architecture» — проговорить
- Закрывает раздел 7 (12 вопросов)

### п.15 — Behavioral · STAR-истории  ⚠️ требует твоего участия
Каркасы готовы, истории — твои. Одна история = 2–3 минуты речи.
- [ ] Разбор сложной задачи
- [ ] Конфликт / несогласие
- [ ] Ошибка и что исправил
- [ ] Усиление результата (цифры!)
- [ ] Помощь коллегам / менторство
- [ ] Приоритизация при конфликте сроков
- Прогнать вслух с таймером — оценивают гладкость подачи, а не идею
- Закрывает раздел 17 (8 вопросов)

---

## SolidMap — сквозной модуль (к пунктам не привязан)
- [ ] SOLID: каждая буква на живом примере из проектов выше
- [ ] Паттерны (GoF) — с ссылкой на конкретный файл
- Открывает раздел 6 (14 вопросов)

---

## Скрининг рекрутера
- [ ] [recruiter-screening-qa.html](dotnet-petprojects/recruiter-screening-qa.html) — вопросы и заготовки

## Алгоритмы
- [ ] [LeetCode.Practice/](LeetCode.Practice/) — 23 задачи на C#

---

## Рабочий ритм (из README репозитория)

1. Один проект = одна волна в 1–2 недели.
2. После разбора — конспект «что понял» в 5–10 строк своими словами.
3. Параллельно собеседования: поплыл на вопросе → пункт в план следующей недели.

## Требования к машине
Проверено: .NET SDK 10.0.400, `dotnet`, `docker`, `kind`, `helm` — всё на месте.
`docker compose up -d` нужен в трёх проектах: `EfCoreLab/`, `OrderFlow/`, `RedisLab/`.