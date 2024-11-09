
[< к содержанию](/readme.md)

# git stash

Команда ``git stash`` позволяет на время «сдать в архив» (или отложить) изменения, сделанные в рабочей копии, чтобы вы могли применить их позже. Откладывание изменений полезно, если вам необходимо переключить контекст и вы пока не готовы к созданию коммита.

## Откладывание кода
Команда ``git stash`` сохраняет неподтвержденные изменения (индексированные и неиндексированные) в отдельном хранилище, чтобы вы могли вернуться к ним позже. Затем происходит откат до исходной рабочей копии. Например:

```
$ git status
On branch main
Changes to be committed:

    new file:   style.css

Changes not staged for commit:

    modified:   index.html

$ git stash
Saved working directory and index state WIP on main: 5002d47 our new homepage
HEAD is now at 5002d47 our new homepage

$ git status
On branch main
nothing to commit, working tree clean
```

Теперь вы можете вносить изменения, создавать новые коммиты, переключаться между ветками и выполнять другие операции **Git**. По необходимости отложенные изменения можно будет применить позже.

Отложенные изменения сохраняются в локальном репозитории **Git** и не передаются на сервер при выполнении команды **push**.

## Применение отложенных изменений

Чтобы применить ранее отложенные изменения, воспользуйтесь командой ``git stash pop``:

```
$ git status
On branch main
nothing to commit, working tree clean
$ git stash pop
On branch main
Changes to be committed:

    new file:   style.css

Changes not staged for commit:

    modified:   index.html

Dropped refs/stash@{0} (32b3aa1d185dfe6d57b3c3cc3b32cbf3e380cc6a)
```

При извлечении отложенных изменений они удаляются из набора и применяются к рабочей копии.

Вы также можете применить изменения к рабочей копии, не удаляя их из набора отложенных изменений. Для этого воспользуйтесь командой ``git stash apply``:

```
$ git stash apply
On branch main
Changes to be committed:

    new file:   style.css

Changes not staged for commit:

    modified:   index.html
```

Это полезно, если вам нужно применить одни и те же отложенные изменения к нескольким веткам.

Теперь вы умеете выполнять основные операции с отложенными изменениями. Однако необходимо помнить о следующей особенности команды ``git stash``: по умолчанию **Git** *не* создает отложенные изменения для неотслеживаемых или игнорируемых файлов.

[< к содержанию](/readme.md)