# Работа с Github

Перед началом работы делаем резервную копию проекта. 
Если вы уже начали работать с гитом, но что-то не получается, лучше начать с начала.

Инструкция проверена от начала и до конца и если в точности следовать тому, что здесь написано, у вас все получится.

## 1. Клонирование репозитория наставнка и создание своего

Копируем адрес репозитория тип соединения не важен т.к. к моему репозиторию у вас доступа не будет. Но для своего репозитория о том как его настроить можете посмотреть тут https://youtu.be/MnU1U7GCWLk

![Alt text](https://monosnap.com/image/05vq8WpL2a5ZHRI9Sz1LZ5NvyJ4RRA)

Открываем терминал и заходим в папку с проектом

Пишем (если хотим склонировать проект со сборкой):
```{r, engine='bash', count_lines}
git clone git@github.com:MaxOrel/BuilderBurger.git burger
```

После чего в папке, где вы сделали эту команду должны появиться папка со сборкой проекта

![Alt text](https://monosnap.com/image/ZysGjK2XswbNRSIkroUkSp3FYZ3had)


### 1.1 Создаем свой репозиторий

Создаем новый репозиторий на github

![Alt text](https://monosnap.com/file/09RNBVaoUeAxVHKKB0v8eAjOZzDJgE.png)

## 2. Работа с репозиторием на компьютере

### 2.1 Создаем связь с личным удаленным репозиторием
Открываем терминал и заходим в папку с проектом (папка в которой есть папка .git)

![Alt text](https://monosnap.com/image/ywneOkHjLECDwQGvXN9aFsZp0aQFmi)

Далее выполняем связь своего удаленного репозитория с этой папкой, но командой которая вам предлагается на gitHub этого не получится сделать, т.к. при клонировании репозитория вы автоматические локальный привязали к репозиторию наставника. Эту связь разрушаем командой
```{r, engine='bash', count_lines}
git remote set-url origin git@github.com:unosmart/burger.git
```
Где git@github.com:unosmart/burger.git - ваш репозиторий

![Alt text](https://monosnap.com/image/o2fkvG5YSy4QrxYZnIA5xpkjoURPFC)

После того как создали связь с личным репоиторием делаем команду
```{r, engine='bash', count_lines}
git push -u origin master
```
У Вас запросит название аккаунта и пароль (если не подключен ssh), после корректного ввода произойдет загрузка файлов в ваш удаленный репозиторий.

### 2.2 Создаем недельную ветку и начинаем разработку

Переходим в папку проекта и локально создаем новую ветку (напоминаю корнем вашего проекта будет папка в которой лежит папка .git, не путайтесь, если какие-то вопросы пишите мне в личку) 

```{r, engine='bash', count_lines}
git checkout -b week_1
```
![Alt text](https://monosnap.com/image/WIsQgyVyky3QYfw165HfKtJIeW6Nq8.png)

Работаем в этой ветке (вставляем файлы из сохраненной папки в сборку то, что вы уже сверстали или сделали или пишем с нуля если ничего не делали)

Изменяем readme.md файл используя MARKDOWN разметку: указываем в нем
* Свое ФИО
* Имя наставника
* Название курса

![Alt text](https://monosnap.com/file/ZhoN0rT4dxzN4j5pkOgkwgWGSgPsoh.png)

После делаем, только всегда смотрите в какой ветке вы находитесь в данном случае мы пока в week_1

```{r, engine='bash', count_lines}
git add .
git commit -m "Текст коммита"
```

![Alt text](https://monosnap.com/file/ZmMy24oXEziI6svQ4jiVDFKUce8yqV.png)

Коммит создан

Делаем push изменений в удаленный репозиторий (ВНИМАТЕЛЬНО мы делаем пуш уже не в ветку MASTER, а в ветку week_1 она автоматически создаться в вашем личном удаленном репозитории если ее там нет)

```{r, engine='bash', count_lines}
git push -u origin week_1
```

![Alt text](https://monosnap.com/file/47Bm5rH3pUDJ5a8xYV8GcWg5W3tkAE.png)

## 3. Проверка работы и сдача работы наставнику

Для того чтобы показать работу настанику ее необходимо отобразить либо на хостинге, либо на Github Pages. Второй вариант предпочтительнее.

Создаем новую ветку (ВАЖНО ветку создаем на удаленном репозитории и находиться нужно на ветке week_1) на github называем ее gh-pages

![Alt text](https://monosnap.com/file/1cZK9yuD5FPrkOuO6gSjWJFmZEex8o.png)
![Alt text](https://monosnap.com/file/ik7mdyA0ByFP8UghDbtrDObqVaEdjv.png)

Заходим с настройки репозитория 
1. Переходим на вкладку settings
2. Выбираем ветку gh-pages. Нажимаем save

![Alt text](https://monosnap.com/file/jP1BuGbGMATPoWB0tWOFOvJh8Bqt1j.png)

Создаем pull request из week_1 в master
![Alt text](https://monosnap.com/file/E3IIu5ayJz969heCqVZIXKDAopCBBn.png)
![Alt text](https://monosnap.com/file/Irfj8sxDB3Z5KEe3AF82LcAD0vBVhq.png)

### Публикуем изменения на github pages ###

После того как мы поработали локально в недельной ветке, т.е. например вы что-то доработали или исправили и хотите сдать мне на проверку в консоли пишем 

(Это если у вас локально что-то изменилось)
```{r, engine='bash', count_lines}
git push origin week_1
```
Потом обновляем то что в ветке gh-pages на удаленном.
```{r, engine='bash', count_lines}
git push origin week_1
git push origin week_1:gh-pages
```
*week_1 заменяем на текущую недельную ветку*. Таким образом все актуальные изменения мы заливаем на gh-pages и они будут доступны по ссылке которую вы пришлете наставнику.

![Alt text](https://monosnap.com/file/2nPgbMhUh6Y1FMMeysVwlOdTAR8p7G.png)

На гите появится вот такая запись 

![Alt text](https://monosnap.com/file/78CzTAbrGBJ2r63ThgmuoNO9gzVyqq.png)

### Добавляем настаника в collaborators ###
1. Открываем вкладку Settings
2. Переходим в раздел collaborators
3. Пишем ник настаника 
4. Жмем на кнопку

![Alt text](https://monosnap.com/file/oqwoZDGLf9mHzJJzizjO3sVVijb1Xn.png)

### Пишем наставнику, что все сделали, ждем ответа. ###

## 4. Доработка

Далее делаем доработки, коммитим их и пушим в туже ветку из которой создавали pull request.(не забываем сделать пуш в gh-pages ветку, чтобы изменения отобразились на gh-pages) 

**Новый pull request создавать не нужно** (вы и не сможете создать новый, пока я не закрыл старый), изменения подтянутся в прошлый. 

**Пишем наставнику, что все поправили, ждем ответа.**

## 5. Новые задания

После того как настаник примет задание вашей первой недели он смержит в мастер все изменения (это делаем именно наставник, т.е. **сами** пулреквест **не закрываем!**). 
Вы проверяете что находитесь на нужно(актуальной) ветке и из нее создаете новую ветку week_2 (или друю недельную ветку)
```{r, engine='bash', count_lines}
git checkout -b week_2
```
Работаете в новой ветке, делаете коммит и пуш на удаленный репозиторий 


Создаете новый pull request и снова пишите настанику

