# "FitSchedule" — Платформа для фитнес-клуба

## Задачи

Разработать бэкэнд, сделать Bruno коллекцию по этому бэку

### Как стартовать

#### Инициализировать Strapi проект

```bash
npx create-strapi-app@latest
```

#### Отключить авторелоад

В файле `package.json` изменить `dev` скрипт на `strapi develop --no-watch-admin`

_Если разворачивать локально, то это не потребуется_

#### Отредактируйте `.gitignore` файл

Удалите следующий список файлов, которые будут игнорироваться гитом

- .env
- *.sql
- *.sqlite
- *.sqlite3

После того как инициализировали проект, собрали админку - сделайте коммит и ТОЛЬКО тогда переключитесь на ветку wip

### Коллекции (Content Types)

**`Member`**
- `firstName`, `lastName` (Text)
- `phone` (Text)
- `birthDate` (Date)
- `photo` (Media)
- `membershipType` (Enumeration: basic / premium / vip)
- relation → `Subscriptions` (one-to-many)
- relation → `Bookings` (one-to-many)

**`Trainer`**
- `firstName`, `lastName` (Text)
- `bio` (Rich Text)
- `photo` (Media)
- `specializations` (JSON)
- relation → `Classes` (one-to-many)
- relation → `Certifications` (one-to-many)

**`Certification`**
- `title` (Text)
- `issuedBy` (Text)
- `issuedAt` (Date)
- `document` (Media)
- relation → `Trainer` (many-to-one)

**`FitnessClass`**
- `title` (Text)
- `description` (Rich Text)
- `scheduledAt` (DateTime)
- `duration` (Integer, в минутах)
- `maxCapacity` (Integer)
- `difficulty` (Enumeration: easy / moderate / hard)
- `type` (Enumeration: yoga / cardio / strength / pilates / hiit)
- `room` (Text)
- relation → `Trainer` (many-to-one)
- relation → `Bookings` (one-to-many)
- relation → `Tags` (many-to-many)

**`Booking`**
- `bookedAt` (DateTime)
- `status` (Enumeration: confirmed / cancelled / attended)
- relation → `Member` (many-to-one)
- relation → `FitnessClass` (many-to-one)

**`Subscription`**
- `startDate`, `endDate` (Date)
- `isActive` (Boolean)
- `plan` (Enumeration: monthly / quarterly / annual)
- `price` (Decimal)
- relation → `Member` (many-to-one)

**`Tag`**
- `name` (Text, unique)
- `color` (Text)

## Перед сдачей наполните 2-3 записями в каждом типе контента

# Как сдавать

- Создайте форк репозитория в вашей организации с названием-этого-репозитория-вашафамилия
- Используя ветку wip сделайте задание
- Зафиксируйте изменения в вашем репозитории
- Когда документ будет готов - создайте пул реквест из ветки wip (вашей) на ветку main (тоже вашу) и укажите меня (ktkv419) как reviewer

Не мержите сами коммит, это сделаю я после проверки задания
