**Conventional Commits** — это **стандарт для написания сообщений коммитов в Git**, который задаёт единый формат.

Официальная спецификация:  
🔗 https://www.conventionalcommits.org

#### Шаблон
``` html
<type>(<scope>): <short description>
```

| Тип        | Когда использовать                  | Пример                                        |
| ---------- | ----------------------------------- | --------------------------------------------- |
| `feat`     | новая функциональность              | feat(auth): add password reset flow           |
| `fix`      | исправление бага                    | fix(profile): prevent avatar flickering<br>   |
| `docs`     | документация                        | docs(readme): add local development steps<br> |
| `style`    | форматирование без изменения логики | style(button): format component styles        |
| `refactor` | рефакторинг без изменения поведения | refactor(utils): extract date formatter       |
| `perf`     | улучшение производительности        | perf(table): memoize row rendering<br>        |
| `test`     | тесты                               | test(login): add validation tests<br>         |
| `build`    | сборка, зависимости                 | build(deps): update eslint to v9<br>          |
| `ci`       | CI/CD                               | ci: run lint before tests                     |
| `chore`    | служебные изменения                 | chore: remove unused assets                   |

# Подробно
## Базовый шаблон

```text
<type>(<scope>)!: <description>

[optional body]

[optional footer(s)]
```
### Примеры

```text
feat(auth): add login via Google
fix(cart): correct total price calculation
docs(readme): update installation guide
refactor(api): simplify user mapper
feat!: remove legacy config format
fix(ui)!: drop support for IE11
```

---

## Структура

### 1. `type`
Тип изменения.
### 2. `(scope)` — необязательно
Область, модуль или часть проекта.

### 3. `!` — необязательно
Ставится, если это **breaking change**.

### 4. `description`
Краткое описание изменения в повелительной форме.

- Пиши коротко и по делу
- Используй **английский**
- Пиши описание в **present tense / imperative mood**
- Не начинай с заглавной буквы, если это правило команды
- Не ставь точку в конце short description
- Один коммит = одна логическая единица изменений

Хорошо:
- `add user avatar upload`
- `fix modal closing logic`
- `update dependency versions`

Плохо:
- `added avatar upload`
- `fixed bug`
- `changes`

---

## Основные типы

### `feat`

Новая функциональность.

```text
feat(profile): add avatar cropping
```

### `fix`

Исправление бага.

```text
fix(payment): handle empty cardholder name
```

### `docs`

Изменения только в документации.

```text
docs: update setup instructions
```

### `style`

Изменения, не влияющие на логику:

- форматирование
- пробелы
- точки с запятой
- линтинг без изменения поведения

```text
style: format code with prettier
```

### `refactor`

Рефакторинг без изменения внешнего поведения.

```text
refactor(store): split auth module into smaller files
```

### `perf`

Оптимизация производительности.

```text
perf(list): reduce rerenders in product grid
```

### `test`

Тесты: добавление или изменение тестов.

```text
test(api): add unit tests for token refresh
```

### `build`

Изменения сборки или зависимостей.

```text
build: update vite to latest version
```

### `ci`

Изменения CI/CD.

```text
ci(github-actions): add deploy workflow
```

### `chore`

Прочие служебные изменения, не относящиеся к фичам/фиксам.

```text
chore: update editorconfig
```

---

## Часто используемые дополнительные типы

> Используются не везде, зависят от команды.

- `revert` — откат коммита
- `init` — инициализация проекта
- `merge` — merge-коммит
- `wip` — work in progress (лучше избегать в main ветках)

Пример:

```text
revert: remove experimental payment flow
```

---

## Breaking Changes

### Вариант 1: через `!`

```text
feat(api)!: change response format for /users
```

### Вариант 2: через footer

```text
feat(api): change response format for /users

BREAKING CHANGE: user list endpoint now returns paginated data
```

### Вариант 3: вместе

```text
feat(api)!: change response format for /users

BREAKING CHANGE: user list endpoint now returns paginated data
```

---
## Footer

Часто используют для:

- breaking changes
- ссылок на задачи
- закрытия issue

Примеры:

```text
Refs: #123
Closes: #45
BREAKING CHANGE: config format has changed
```

Полный пример:

```text
feat(payments): add support for Apple Pay

Add Apple Pay button to checkout page and payment service.

Closes: #142
Refs: #118
```

---

## Как это связано с SemVer

Conventional Commits часто используют для автоматического версионирования:

- `fix` → `PATCH` (`1.0.0` → `1.0.1`)
- `feat` → `MINOR` (`1.0.0` → `1.1.0`)
- `BREAKING CHANGE` или `!` → `MAJOR` (`1.0.0` → `2.0.0`)
