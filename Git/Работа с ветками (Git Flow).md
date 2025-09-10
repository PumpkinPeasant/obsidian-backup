# Git — работа с ветками (Git Flow)

## 1. Основные ветки
- **main (или master)** → стабильная версия, которая уходит в прод  
- **develop** → основная ветка для разработки, в неё вливаются все фичи  
- **feature/** → ветки для отдельных задач/фич  
- **release/** → подготовка релиза (фикс багов перед продом)  
- **hotfix/** → срочные исправления для production  

---

## 2. Создание feature-ветки
```bash
git checkout develop
git pull origin develop        # обновляем develop
git checkout -b feature/login  # создаём ветку
```

✅ Каждая фича — отдельная ветка.

---

## 3. Завершение feature

```bash
git checkout develop
git merge feature/login
git push origin develop
```

✅ После завершения работа вливается в `develop`.

---

## 4. Release-ветки

Когда проект готов к релизу:

```bash
git checkout develop
git checkout -b release/1.0.0
```

- фикс багов только здесь
- после завершения → merge в `main` и в `develop`

---

## 5. Hotfix-ветки

Исправления для production:

```bash
git checkout main
git checkout -b hotfix/1.0.1
```

- фикс багов
- merge обратно в `main` и в `develop`

---

## 6. Pull Request (Merge Request)

Обычно feature/release/hotfix вливаются в `develop` или `main` через PR (code review).

---

🔑 **Итог:**
- `main` → прод
- `develop` → текущая разработка
- `feature/*` → новые фичи
- `release/*` → подготовка релиза
- `hotfix/*` → срочные фиксы