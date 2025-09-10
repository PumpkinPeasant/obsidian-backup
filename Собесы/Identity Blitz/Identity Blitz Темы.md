## 1. TypeScript
- [ ] [[Типы TypeScript|Базовые типы]] (`string`, `number`, `boolean`, `null`, `undefined`, `void`, `any`, `unknown`, `never`)
- [ ] [[Type и Union|Разница type и interface]]
- [ ] [[Union Types и Intersection Types|Union и intersection типов]]
- [ ] [[Enum и as const|Enum и as const]]
- [ ] [[Utility Types]] (`Partial`, `Pick`, `Omit`, `Required`, `Record`)
- [ ] [[Дженерики|Generics]] (функции и классы)
- [ ] [[Conditional Types (условные типы)|Conditional Types ]](`T extends U ? X : Y`)
- [ ] [[Типизация API (DTO, Fetch)|Типизация API (ответы fetch, DTO)]]
- [ ] [[Типизация Vue компонентов (props, emits, slots)]]
- [ ] [[Для чего нужно использовать TS]]

## 2. Git
- [ ] [[Базовые команды (clone, add, commit, push, pull)]]
- [ ] [[Работа с ветками (Git Flow)]]
- [ ] [[Merge vs Rebase]]
- [ ] [[Squash]] (объединение коммитов)
- [ ] [[Cherry-pick]] (перенос отдельных коммитов)
- [ ] [[Git hooks (pre-commit проверки)]]

## 3. Тестирование
- [ ] [[Какие виды тестирования существуют]]
- [ ] [[Unit-тесты (модульные тесты)]] 
- [ ] [[Vitest]]
- [ ] Snapshot-тесты (для UI)
- [ ] E2E-тесты (Cypress, Playwright)
- [ ] Мокаем `fetch`/`axios`
- [ ] Разница unit vs e2e

## 4. HTTP и браузер
- [ ] [[Жизненный цикл HTTP-запроса|Жизненный цикл запроса (DNS → TCP → TLS → HTTP → backend)]]
- [ ] [[Загрузка ресурсов. DOM, CSSOM, JS, event loop]]
- [ ] [[Кэширование (Cache-Control, ETag, Service Worker)]]
- [ ] [[CORS (Cross-Origin Resource Sharing)|CORS: зачем, preflight-запросы, заголовки]]
- [ ] [[Same-Origin Policy (SOP)]]
- [ ] [[Скрипты async vs defer]]
- [ ] [[Разница 301 и 302]]
- [ ] [[Поддержка IE11]]

## 5. Cookies
- [ ] [[Session vs Persistent]]
- [ ] [[Ограничения (размер, количество на домен)]]
- [ ] [[Использование для сессий и аутентификации]]
- [ ] [[HttpOnly]]
- [ ] [[Secure]]
- [ ] [[SameSite (Strict, Lax, None)]]
- [ ] [[Как защититься от XSS и CSRF]]

## 6. Vite
- [ ] [[Vite|Основные фичи (HMR, ES-модули, скорость)]]
- [ ] [[Конфигурация vite.config.ts]]
- [ ] [[Подключение плагинов]] (`@vitejs/plugin-vue`)
- [ ] [[Vite vs Webpack]]
- [ ] [[Создание собственного плагина]]
- [ ] [[Настройка алиасов]]
- [ ] [[Подключение PostCSS и SCSS]]

## 7. Безопасность
- [ ] [[XSS-атаки (Cross-Site Scripting)|XSS: что это, защита (HttpOnly, CSP, sanitize)]]
- [ ] [[CSRF (Cross-Site Request Forgery)|CSRF: что это, защита (SameSite, CSRF-токены, Origin/Referer)]]

## 7. Аутентификация / IAM / CIAM
- [ ] Разница аутентификации и авторизации
- [ ] Identity Provider (IdP) vs Service Provider (SP)
- [ ] JWT: структура, где хранить (HttpOnly cookies vs localStorage)
- [ ] Access Token vs Refresh Token
- [ ] Что делать при `401 Unauthorized` и `403 Forbidden`
### 7.1 OAuth 2.0
- [ ] Основные потоки (flows):
  - [ ] Authorization Code Flow
  - [ ] Implicit Flow
  - [ ] PKCE (Proof Key for Code Exchange)
- [ ] Как работает `Authorization: Bearer <token>`
- [ ] Когда использовать access и refresh токены
### 7.2 OIDC (OpenID Connect)
- [ ] Отличие от OAuth 2.0
- [ ] Что такое `id_token` и зачем нужен
### 7.3 SSO / SAML / MFA
- [ ] SSO (Single Sign-On): принцип работы
- [ ] SAML: отличие от OIDC (XML vs JSON/JWT)
- [ ] MFA (Multi-Factor Authentication): примеры (SMS, TOTP, push)
- [ ] LDAP: зачем используется в корпоративных системах