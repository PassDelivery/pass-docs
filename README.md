# PassDelivery — Документация

Централизованная документация командного проекта PassDelivery — сервиса доставки еды, разрабатываемого в рамках курса по ООП (МГТУ «СТАНКИН», ИСиТ).

Приложение работает по адресу **[passdelivery.ru](https://passdelivery.ru)**.

## Содержание

| Документ | Описание |
|---|---|
| [`requirements.md`](./requirements.md) | Анализ задачи: цель проекта, роли пользователей, use-case'ы, бизнес-правила |
| [`ERD.md`](./ERD.md) | ERD-диаграмма базы данных и список миграций |
| [`openapi.yaml`](./openapi.yaml) | OpenAPI-контракт REST API (48 операций) |
| [`design.md`](./design.md) | Ссылка на макет в Figma и реализованные экраны |
| [`ROADMAP.md`](./ROADMAP.md) | Roadmap и график работ, фактический ход разработки |

## О проекте

PassDelivery — сервис заказа и доставки еды из ресторанов, по аналогии с Яндекс.Едой. В системе четыре роли:

- customer — заказывает еду
- restaurant_owner — управляет ресторанами и меню, готовит заказы
- courier — доставляет заказы
- admin — модерация и администрирование

Подробный разбор сценариев — в [requirements.md](./requirements.md).

## Архитектура

- **Backend:** Go, трёхслойная архитектура (handler → service → repository), PostgreSQL, миграции golang-migrate, JWT-аутентификация, bcrypt. Фото хранятся на диске сервера, в базе — путь к файлу.
- **Frontend:** HTML, CSS и JavaScript без сборки и фреймворков (ES-модули), сверстан по макету из Figma.
- **Контракт между бекендом и фронтендом:** [OpenAPI-спека](./openapi.yaml), также доступна в SwaggerHub.
- **Инфраструктура:** VPS, Docker Compose (бекенд, PostgreSQL, миграции), nginx отдаёт фронтенд и проксирует `/api/` на бекенд, домен passdelivery.ru.

```
браузер ──► passdelivery.ru (nginx)
              ├─ /         → файлы фронтенда
              └─ /api/v1/  → бекенд на Go (Docker) ──► PostgreSQL (Docker)
```

## Репозитории организации

| Репозиторий | Назначение |
|---|---|
| [`pass-backend`](https://github.com/PassDelivery/pass-backend) | Бекенд — REST API на Go |
| [`pass-frontend`](https://github.com/PassDelivery/pass-frontend) | Фронтенд |
| [`pass-docs`](https://github.com/PassDelivery/pass-docs) | Документация (этот репозиторий) |

## Команда

| Участник | Роль |
|---|---|
| Антон Бурачевский | Тимлид, backend-разработчик, data-base инженер, DevOps |
| Орлов Виктор | Frontend |
| Балаов Георгий | UX/UI дизайнер |
| Точилкин Петр | бизнес аналитик, системный аналитик |
| Волошин Александр | Project менеджер |

## Git-флоу

Разработка ведётся через feature-ветки (`feature/<название>`, исправления — `fix/<название>`) и Pull Request в main. Прямые коммиты в main запрещены (branch protection).
