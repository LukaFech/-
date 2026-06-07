Luka@DESKTOP-712IRIB MINGW64 ~
$
$ #!/bin/bash

# ============================================================
#  GIT TASKS 1–12 — повний скрипт
#  Запуск: bash git_tasks.sh
# ============================================================

set -e  # зупинити при помилці

echo ""
echo "=== ЗАВДАННЯ 1: Налаштування Git ==="
git config --global user.name  "Your Name"
git config --global user.email "your@email.com"
git config --list | grep user
echo "Git налаштовано."

echo ""
echo "=== ЗАВДАННЯ 2: Створення папок і файлів ==="
mkdir -p myproject/folder1 myproject/folder2
echo "File A content" > myproject/folder1/a.txt
echo "File B content" > myproject/folder1/b.txt
echo "File C content" > myproject/folder2/c.txt
echo "File D content" > myproject/folder2/d.txt
echo "Структуру створено."

echo ""
echo "=== ЗАВДАННЯ 3: Ініціалізація репозиторію ==="
cd myproject
git init
echo "Репозиторій ініціалізовано."

echo ""
echo "=== ЗАВДАННЯ 4: Додавання в індекс ==="
git add folder1/ folder2/
git status
echo "Файли додано в індекс."

echo ""
echo "=== ЗАВДАННЯ 5: Перший коміт ==="
git commit -m "Add folder1 and folder2 with initial files"
git log --oneline
echo "Перший коміт створено."

echo ""
echo "=== ЗАВДАННЯ 6: Зміна файлу та новий коміт ==="
echo "Updated content line" >> folder1/a.txt
git add folder1/a.txt
git commit -m "Update a.txt in folder1"
git log --oneline
echo "Другий коміт створено."

echo ""
echo "=== ЗАВДАННЯ 7: Нова підпапка та коміт ==="
mkdir -p folder3
echo "New file E content" > folder3/e.txt
echo "New file F content" > folder3/f.txt
git add folder3/
git commit -m "Add folder3 with e.txt and f.txt"
git log --oneline
echo "Третій коміт створено."

echo ""
echo "=== ЗАВДАННЯ 8: git checkout — скасування змін у файлі ==="
echo "Unwanted change" >> folder3/e.txt
echo "  До скасування:"
cat folder3/e.txt
git checkout -- folder3/e.txt
echo "  Після скасування:"
cat folder3/e.txt
echo "Зміни у файлі скасовано."

echo ""
echo "=== ЗАВДАННЯ 9: git reset — прибрати файл з індексу ==="
echo "Staged change" >> folder3/e.txt
git add folder3/e.txt
echo "  Статус після git add:"
git status
git reset HEAD folder3/e.txt
echo "  Статус після git reset:"
git status
echo "Файл прибрано з індексу."

echo ""
echo "=== ЗАВДАННЯ 10: git revert — скасувати коміт ==="
# Спочатку зберігаємо файл у чистий стан
git checkout -- folder3/e.txt
echo "Change to revert" >> folder3/e.txt
git add folder3/e.txt
git commit -m "Change that will be reverted"
echo "  Коміти до revert:"
git log --oneline
git revert HEAD --no-edit
echo "  Коміти після revert:"
git log --oneline
echo "Коміт скасовано через revert."

echo ""
echo "=== ЗАВДАННЯ 11: git reset --hard — видалити коміти ==="
echo "  Коміти до reset:"
git log --oneline
git reset --hard HEAD~2
echo "  Коміти після reset --hard HEAD~2:"
git log --oneline
echo "Два останні коміти видалено."

echo ""
echo "=== ЗАВДАННЯ 12: git commit --amend — змінити останній коміт ==="
echo "Amended content" >> folder3/f.txt
git add folder3/f.txt
git commit --amend -m "Add folder3 — amended commit message"
echo "  Фінальна історія:"
git log --oneline
echo "Останній коміт оновлено."

echo ""
echo "============================================================"
echo " Всі 12 завдань виконано успішно!"
echo "============================================================"

=== ЗАВДАННЯ 1: Налаштування Git ===
user.name=Your Name
user.email=your@email.com
Git налаштовано.

=== ЗАВДАННЯ 2: Створення папок і файлів ===
Структуру створено.

=== ЗАВДАННЯ 3: Ініціалізація репозиторію ===
Reinitialized existing Git repository in C:/Users/Luka/myproject/.git/
Репозиторій ініціалізовано.

=== ЗАВДАННЯ 4: Додавання в індекс ===
warning: in the working copy of 'folder1/a.txt', LF will be replaced by CRLF the
 next time Git touches it
warning: in the working copy of 'folder1/b.txt', LF will be replaced by CRLF the
 next time Git touches it
warning: in the working copy of 'folder2/c.txt', LF will be replaced by CRLF the
 next time Git touches it
warning: in the working copy of 'folder2/d.txt', LF will be replaced by CRLF the
 next time Git touches it
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   folder1/a.txt
        modified:   folder1/b.txt
        modified:   folder2/c.txt
        modified:   folder2/d.txt

Файли додано в індекс.

=== ЗАВДАННЯ 5: Перший коміт ===
[master e825dbc] Add folder1 and folder2 with initial files
 4 files changed, 4 insertions(+), 5 deletions(-)
e825dbc (HEAD -> master) Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Перший коміт створено.

=== ЗАВДАННЯ 6: Зміна файлу та новий коміт ===
warning: in the working copy of 'folder1/a.txt', LF will be replaced by CRLF the
 next time Git touches it
[master e9b6632] Update a.txt in folder1
 1 file changed, 1 insertion(+)
e9b6632 (HEAD -> master) Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Другий коміт створено.

=== ЗАВДАННЯ 7: Нова підпапка та коміт ===
warning: in the working copy of 'folder3/e.txt', LF will be replaced by CRLF the
 next time Git touches it
warning: in the working copy of 'folder3/f.txt', LF will be replaced by CRLF the
 next time Git touches it
[master 1573410] Add folder3 with e.txt and f.txt
 2 files changed, 2 insertions(+), 2 deletions(-)
1573410 (HEAD -> master) Add folder3 with e.txt and f.txt
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Третій коміт створено.

=== ЗАВДАННЯ 8: git checkout — скасування змін у файлі ===
  До скасування:
New file E content
Unwanted change
  Після скасування:
New file E content
Зміни у файлі скасовано.

=== ЗАВДАННЯ 9: git reset — прибрати файл з індексу ===
warning: in the working copy of 'folder3/e.txt', LF will be replaced by CRLF the
 next time Git touches it
  Статус після git add:
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   folder3/e.txt

Unstaged changes after reset:
M       folder3/e.txt
  Статус після git reset:
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   folder3/e.txt

no changes added to commit (use "git add" and/or "git commit -a")
Файл прибрано з індексу.

=== ЗАВДАННЯ 10: git revert — скасувати коміт ===
warning: in the working copy of 'folder3/e.txt', LF will be replaced by CRLF the
 next time Git touches it
[master 30a6bff] Change that will be reverted
 1 file changed, 1 insertion(+)
  Коміти до revert:
30a6bff (HEAD -> master) Change that will be reverted
1573410 Add folder3 with e.txt and f.txt
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
[master 7e362c8] Revert "Change that will be reverted"
 Date: Sat Jun 6 08:18:48 2026 +0300
 1 file changed, 1 deletion(-)
  Коміти після revert:
7e362c8 (HEAD -> master) Revert "Change that will be reverted"
30a6bff Change that will be reverted
1573410 Add folder3 with e.txt and f.txt
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Коміт скасовано через revert.

=== ЗАВДАННЯ 11: git reset --hard — видалити коміти ===
  Коміти до reset:
7e362c8 (HEAD -> master) Revert "Change that will be reverted"
30a6bff Change that will be reverted
1573410 Add folder3 with e.txt and f.txt
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
HEAD is now at 1573410 Add folder3 with e.txt and f.txt
  Коміти після reset --hard HEAD~2:
1573410 (HEAD -> master) Add folder3 with e.txt and f.txt
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Два останні коміти видалено.

=== ЗАВДАННЯ 12: git commit --amend — змінити останній коміт ===
warning: in the working copy of 'folder3/f.txt', LF will be replaced by CRLF the
 next time Git touches it
[master 54203a5] Add folder3 — amended commit message
 Date: Sat Jun 6 08:18:34 2026 +0300
 2 files changed, 3 insertions(+), 2 deletions(-)
  Фінальна історія:
54203a5 (HEAD -> master) Add folder3 — amended commit message
e9b6632 Update a.txt in folder1
e825dbc Add folder1 and folder2 with initial files
6e54775 Revert "Change that will be reverted"
387837c Change that will be reverted
04322c3 Add folder3 with e.txt and f.txt
1fd87ac Update a.txt in folder1
ae6e8f6 Add folder1 and folder2 with initial files
Останній коміт оновлено.
