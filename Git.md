## Git

### Базовые вопросы.

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

В чем разница между git pull и git push?

#### Ответ:

<details><summary>Решение</summary>
<p>

Pull - получить свежие правки из удаленного репозитория,
Push - отправить свои изменения на сервер.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Как переключиться на работу с новой веткой?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git checkout <branch>
```

</p>
</details>

#### Дополнительные вопросы:

Q: *А если ветки не существует?*

A:

<details><summary>Решение</summary>
<p>

```bash
git checkout -b <new_branch>
```

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

В чем разница между git pull и git fetch?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git pull = git fetch + git merge
```

- `git pull` - извлекает (fetch) данные с сервера и автоматически делает слияние (merge) их с кодом текущей ветки.
- `git fetch` - связывается с удаленным репозиторием и получает данные, которые отсутствуют в локальном.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

За что отвечает команда git stash?

#### Ответ:

<details><summary>Решение</summary>
<p>

`git stash` — команда сохраняющая измененное состояние рабочей директории или отдельного файла в хранилище незавершенных изменений. Это дает возможность в любой момент применить их обратно.

</p>
</details>

#### Дополнительные вопросы:

Q: *Когда стоит использовать?*

A:

<details><summary>Решение</summary>
<p>

Когда последний коммит нужно изменить, но уже были внесены новые правки в той же самой ветке.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Как отменить изменения, внесенные отдельным коммитом?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git revert <hash_commit>
```

</p>
</details>

#### Дополнительные вопросы:

Q: *Как работает revert?*

A: -

<details><summary>Решение</summary>
<p>

Создается новый коммит, накладывающий обратные изменения.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Как отменить все локальные изменения после последнего коммита?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git reset --hard HEAD
```

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Что такое MergeRequest/PullRequest?

#### Ответ:

<details><summary>Решение</summary>
<p>

Запрос на слияние ветки с изменениями в основную ветку.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Что делать, если вы пытаетесь опубликовать изменения, но в мастере появились свежие правки?

#### Ответ:

<details><summary>Решение</summary>
<p>

Подтянуть изменения к себе.
Закоммитить и опубликовать изменения.

</p>
</details>

#### Дополнительные вопросы:

Q: *А если в мастере - правки файла, который изменен у вас локально?*

A: -

<details><summary>Решение</summary>
<p>

Руками поправить изменения там, где Git не смог это сделать автоматически и затем собрать все в коммит и запушить.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @dkolesnik-->

#### Задача:

Вы начали трудиться над задачей, написали достаточное количество кода. Вдруг заметили, что вы работаете на ветке master. А вам надо было создать ветку с номером задачи и в нее запушить ваши изменения. Каковы будут ваши действия?

#### Ответ:

<details><summary>Решение</summary>
<p>

Создать новую ветку с номером тикета от текущей, а по завершении работы запушить ее в удаленный репозиторий и создать МР в мастер.
Если МР не будет принят, изменения в локальной мастер-ветке надо откатить до origin/master.

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Что делать, если некоторые файлы не нужно опубликовывать?

#### Ответ:

<details><summary>Решение</summary>
<p>

Добавить их в .gitignore

</p>
</details>

#### Дополнительные вопросы:

Q: *После добавления в .gitignore файл по прежнему отслеживается git, как исправить?*

A: -

<details><summary>Решение</summary>
<p>

Нужно почистить кэш:

```bash
git rm --cached <ignore_file>
```

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Как исправить ошибки (файлы/комментарий) в коммите?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git commit --amend
```

</p>
</details>

______________________________________________________________________

Сложность: **простая**

<!--Автор: @asvezh-->

#### Задача:

Как удалить ветку локально?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git branch -D branch_name
```

</p>
</details>

#### Дополнительные вопросы:

Q: *Как удалить ветку в удаленном репозитории?*

A: -

<details><summary>Решение</summary>
<p>

```bash
git push origin --delete branch  
git push origin :<branchName>
```

</p>
</details>

______________________________________________________________________

### Вопросы средней сложности.

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Как работает git cherry-pick?

#### Ответ:

<details><summary>Решение</summary>
<p>

Используется для перенесения отдельных коммитов из одного места репозитория в другое.

</p>
</details>

______________________________________________________________________

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Как работает git rebase?

#### Ответ:

<details><summary>Решение</summary>

Все коммиты из одной ветки в том же порядке применяются к другой ветке.

<p align="center">
  <img src="https://hsto.org/storage2/ad5/e57/930/ad5e57930d4d4e490017b2b17cb23e84.png"/>
</p>

</details>

______________________________________________________________________

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Что означает состояние DETACHED HEAD?

#### Ответ:

<details><summary>Решение</summary>
<p>

`HEAD` указывает не на вершину какой либо ветки, а просто на какой-то коммит.

</p>
</details>

#### Дополнительные вопросы:

Q: *Как пофиксить?*

A: -

<details><summary>Решение</summary>
<p>

Переключиться на какую-либо ветку/создать новую ветку.

</p>
</details>

______________________________________________________________________

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Опишите процедуру git flow для одного человека?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git clone
git add
git commit
git push
```

</p>
</details>

#### Дополнительные вопросы:

Q: *Для двух человек?*

A: -

<details><summary>Решение</summary>
<p>

```bash
git pull
git merge
git add
git commit
git push
```

</p>
</details>

#### Дополнительные вопросы:

Q: *Для команды?*

A: -

<details><summary>Решение</summary>
<p align="center">
  <img src="https://lh3.googleusercontent.com/proxy/fq54_5jHAN_7EPTXe3akcf4lBQbW2I4z8Y2S-tsArsVKL9LivTuhvzihBB61yZkAbopMWilwvGLZQrNceHxS7IELFfK_OtUqi-JmU6IOXPWsmjScgTRYQQ"/>
</p>
</details>
______________________________________________________________________

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Можно ли изменить адрес удаленного репозитория? (перезалить код по другому адресу?)

#### Ответ:

<details><summary>Решение</summary>
<p>

Да. Нужно удалить старую ссылку и добавить url нового репозитория:

```bash
git remote add origin <new_url>
```

Для проверки: `git remote -v` (показывает текущие репозитории)

</p>
</details>

______________________________________________________________________

Сложность: **средняя**

<!--Автор: @asvezh-->

#### Задача:

Как можно смержить изменения до конкретного коммита?

#### Ответ:

<details><summary>Решение</summary>
<p>

```bash
git checkout <target_branch>
git merge <commit>
```

или переключиться на нужный коммит и создать от него новую ветку.

</p>
</details>