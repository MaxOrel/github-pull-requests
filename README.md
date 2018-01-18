# Работа с Github

Перед началом работы делаем резервную копию проекта. 
Если вы уже начали работать с гитом, но что-то не получается, лучше начать с начала.

Инструкция проверена от начала и до конца и если в точности следовать тому, что здесь написано, у вас все получится.

## 1. Создание репозитория

Создаем новый репозиторий на github

![Alt text](https://monosnap.com/file/09RNBVaoUeAxVHKKB0v8eAjOZzDJgE.png)

Указываем имя репозитория, ставим галочку **Initialize this repository with a README**

![Alt text](https://monosnap.com/file/bpGRwhgDKz5iTNcXWKoHYvxodsM4nP.png)

Изменяем readme.md файл используя MARKDOWN разметку: указываем в нем
* Свое ФИО
* Имя наставника
* Название курса

![Alt text](https://monosnap.com/file/qtzdUY2xLu4r8sApNO3XpyotzBGjR2.png)
![Alt text](https://monosnap.com/file/cqESivcZuFx8NG62gL7dR5k1trO9bJ.png)
![Alt text](https://monosnap.com/file/aRGLTa0NLKXmLKEkfQxuyWWowellc5.png)

## 2. Работа с репозиторием на компьютере

Копируем адресс репозитория тип соединения выбираем в зависимости от того настроен ли ssh доступ или нет, у меня настроен поэтому я выбираю с ssh. О том как его настроить можете посмотреть тут https://youtu.be/MnU1U7GCWLk

![Alt text](https://monosnap.com/file/H5sqkqgaa2eGFnuDDTMukswyH0Ohoc.png)

Открываем терминал и заходим в папку с проектом

Пишем (вместо адресса моего репозитория ставите то что скопировали):
```{r, engine='bash', count_lines}
git clone git@github.com:MaxOrel/burgers.git
```
![Alt text](https://monosnap.com/file/2fYUM94hDLiloSZLq0EKbyJxwNjfv2.png)

Переходим в папку проекта и локально создаем новую ветку 

```{r, engine='bash', count_lines}
git checkout -b week_1
```
![Alt text](https://monosnap.com/file/LJhdKtYN08XTdVKHJ8TrNM5crtMv1X.png)

Работаем в этой ветке (вставляем файлы из сохраненной папки, то что вы уже сверстали или сделали, если они раньше были)

![Alt text](https://monosnap.com/file/ZhoN0rT4dxzN4j5pkOgkwgWGSgPsoh.png)

После делаем, только всегда смотрите в какой ветке вы находитесь в данном случае мы пока в week_1

```{r, engine='bash', count_lines}
git add .
git commit -m "Текст коммита"
```

![Alt text](https://monosnap.com/file/ZmMy24oXEziI6svQ4jiVDFKUce8yqV.png)

Коммит создан

Делаем push изменений в удаленный репозиторий 

```{r, engine='bash', count_lines}
git push -u origin week_1
```

![Alt text](https://monosnap.com/file/47Bm5rH3pUDJ5a8xYV8GcWg5W3tkAE.png)

## 3. Проверка работы

Создаем новую ветку (важно находиться нужно на ветке week_1) на github называем ее gh-pages
![Alt text](https://monosnap.com/file/1cZK9yuD5FPrkOuO6gSjWJFmZEex8o.png)
![Alt text](https://monosnap.com/file/ik7mdyA0ByFP8UghDbtrDObqVaEdjv.png)

Заходим с настройки репозитория 
1. Переходим на вкладку settings
2. Выбираем ветку gh-pages. Нажимаем save
3. Копируем получившуюся ссылку

![Alt text](https://monosnap.com/file/jP1BuGbGMATPoWB0tWOFOvJh8Bqt1j.png)

Возвращаемся во вкладку обзора репозитория, **обращаем внимание что бы находились в ветке week_1**, дописываем ссылку в README
*(Файл редактируется так же, как и в первый раз см. пару пунктов выше)*
![Alt text](https://monosnap.com/file/JeT23fkdKv0fI6hPRAmEJ9ziMIuWtJ.png)

Создаем pull request из week_1 в master
![Alt text](https://monosnap.com/file/E3IIu5ayJz969heCqVZIXKDAopCBBn.png)
![Alt text](https://monosnap.com/file/Irfj8sxDB3Z5KEe3AF82LcAD0vBVhq.png)

Получаем ветку week_1 на свой локальный компьютер, мы же удаленно поменяли файл readme.md теперь локально и удаленно у нас ветки отличаются, чтобы это исправить делаем git pull

```{r, engine='bash', count_lines}
git pull origin week_1
```
![Alt text](https://monosnap.com/file/co3Ugd1Jzyem7Goxk9LuiKF4ajIDNl.png)

### Публикуем изменения на github pages ###

После того как мы поработали локально в недельной ветке, т.е. например вы что-то доработали и хотите сдать мне на проверку в консоли пишем 

```{r, engine='bash', count_lines}
git push origin week_1:gh-pages
```
*week_1 заменяем на текущую недельную ветку*. Таким образом все актуальные изменения мы заливаем на gh-pages и они будут доступны по ссылке которую мы писали в readme.md

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

В окне pull request наставник напишет замечания, вам прийдет письмо на почту о том что я оставил комментарий
После необходимо снова зайти в терминал и написать (так мы стянем изменения, если они есть) 
```{r, engine='bash', count_lines}
git pull
```

Далее делаем доработки, коммитим их и пушим.(не забываем сделать пуш в gh-pages ветку) 

Новый pull request создавать не нужно, изменения подтянутся в прошлый. 

**Пишем наставнику, что все поправили, ждем ответа.**

## 5. Новые задания

После того как настаник примет задание вашей первой недели и смержит в мастер все изменения (это делаем именно наставник). Вы переключаетесь на мастер и делаете pull
```{r, engine='bash', count_lines}
git checkout master
git pull
```
Далее создаете ветку week_2 
```{r, engine='bash', count_lines}
git checkout -b week_2
```
Если наставник **не успел** проверить ваше задание или вы не доделали прошлую ветку, делаете новую ветку не из master, а из актуальной ветки.

Работаете в ней, делаете коммит и пуш на удаленный репозиторий 


Создаете новый pull request и снова пишите настанику

