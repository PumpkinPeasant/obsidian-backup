## 1. Что такое Squash
Squash позволяет объединить несколько коммитов в один.  
👉 Полезно, чтобы очистить историю перед merge (например, убрать "fix typo", "small change").

---

## 2. Интерактивный rebase
```bash
git rebase -i HEAD~3
```

(объединить последние 3 коммита)

Редактор откроется с таким списком:

```
pick a1b2c3 First commit
pick d4e5f6 Second commit
pick g7h8i9 Third commit
```

Меняем `pick` на `squash` или `s` для тех коммитов, которые хотим объединить:

```
pick a1b2c3 First commit
squash d4e5f6 Second commit
squash g7h8i9 Third commit
```

После этого появится редактор для объединения сообщений коммитов.

---

## 3. Squash при merge

Можно сделать squash сразу при слиянии ветки:

```bash
git checkout develop
git merge --squash feature/login
git commit -m "Добавил авторизацию"
```

👉 Все изменения из `feature/login` попадут в один коммит в `develop`.

---

## 4. Когда использовать

- Перед PR, чтобы история была чистой
- Для feature-веток с множеством мелких коммитов
- Чтобы оставить только один "логичный" коммит вместо серии мелких


---

🔑 **Итог:**

- `git rebase -i HEAD~N` → объединить несколько последних коммитов
- `git merge --squash` → объединить всю ветку в один коммит
- Squash делает историю чище и понятнее
