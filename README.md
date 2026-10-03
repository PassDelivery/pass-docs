# PassDelivery — Документация

Централизованная документация командного проекта PassDelivery — сервиса доставки еды, разрабатываемого в рамках курса по ООП (МГТУ «СТАНКИН», ИСиТ).


## Содержание

| Документ | Описание |
|---|---|
| [`requirements.md`](./requirements.md) | Анализ задачи: цель проекта, роли пользователей, use-case'ы, бизнес-правила |
| [`erd.md`](./erd.md) | ERD-диаграмма базы данных |
| [`openapi-core.yaml`](./openapi.yaml) | OpenAPI-контракт REST API |
| [Roadmap и график работ](./ROADMAP.md) | План по этапам на все 3 лабораторные |

## О проекте

PassDelivery — сервис заказа и доставки еды из ресторанов, по аналогии с Яндекс.Едой. В системе четыре роли:

- customer — заказывает еду
- restaurant_owner — управляет рестораном и меню
- courier — доставляет заказы
- admin — модерация и администрирование

Подробный разбор сценариев — в [requirements.md](./requirements.md).

## Архитектура

- Backend: Go, трёхслойная архитектура (handler → service → repository), PostgreSQL, Docker Compose, JWT-аутентификация
- Frontend: см. репозиторий pass-frontend
- Контракт между бекендом и фронтендом: [OpenAPI-спека](./openapi.yaml), также доступна в SwaggerHub

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

Разработка ведётся через feature-ветки (`feature/<название>`) и Pull Request в main. Прямые коммиты в main запрещены (branch protection).
