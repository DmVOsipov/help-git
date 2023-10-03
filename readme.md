#Git. Базовые команды в консоли
```
##Навигация
* pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;
* ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;
* ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;
* cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;
* cd first-project/html — перейди в папку html, которая находится в папке first-project;
* cd .. — перейди на уровень выше, в родительскую папку;
* cd ~ — перейди в домашнюю директорию (/Users/Username);
* cd / — перейди в корневую директорию.


## Работа с файлами и папками

###Создание
* touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;
* touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;
* mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

###Копирование и перемещение
* cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;
* mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.

###Чтение
* cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

###Удаление
* rm about.html (от англ. remove, «удалить») — удали файл about.html;
* rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;
* rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.

###Полезные возможности
* Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).
* У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
* Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама. Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.

```

#Git.Репозиторий
```
##Инициализируем репозиторий
1. Переместиться в парку репрозитория 
2. Ввести команду git init (от англ. initialize — «инициализировать»).
3. Проверить состояние репозитория команда git status

##Добавляем файлы в репозиторий
1. Добавим в файлы репозиторий
2. Подготовить файлы к сохранению. Пример,  git add todo.txt (git add --all # подготовили к сохранению все файлы в репозитории)

## Коммиты
1. Для выполнения коммита используется команда git commit "Комментарий". Команда git commit выведет информацию о коммите.
2. Просмотреть историю коммитов — git log

#Git.Синхронизация с GitHub

##Инструкция по созданию репозитория на GitHub
1. Зайдите в свой профиль по ссылке https://github.com/username, где username — имя, которое вы указали при регистрации.
2. Создайте репозиторий. Для этого перейдите на вкладку Repositories (англ. «репозитории»), а затем нажмите на зелёную кнопку New (англ. «новый») справа. Открылось окно создания нового репозитория. Назовите его. Название удалённого репозитория необязательно должно совпадать с именем папки проекта у вас на компьютере. Но чтобы не путаться, будем называть их одинаково. Другие поля вам пока не понадобятся. Для завершения нажимаем на зелёную кнопку Create repository (англ. «создать репозиторий») внизу.

##Инструкция по генерации SSH-ключа
1. Для генерации SSH-пары используется программа ssh-keygen. В терминале перейдите в домашнюю директорию и введите следующую команду ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub". Используйте электронную почту, к которой привязан ваш GitHub-аккаунт. Если вы видите сообщение об ошибке, то, скорее всего, ваша система не поддерживает алгоритм шифрования ed25519. Ничего страшного: используйте другой алгоритм.ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
2. Проверка, что ключи действительно сгенерировались. Для этого вызовите эту команду ls -a ~/.ssh. На экране должны появиться два файла — один с расширением .pub, другой — без. Файл в .pub — публичный, им можно делиться с веб-сайтами или коллегами. Файл без расширения .pub — приватный. Ни в коем случае не передавайте его никому! 

##Привязываем SSH-ключ к GitHub
1. Скопируйте содержимое файла с публичным ключом в буфер обмена.Команда clip < ~/.ssh/id_rsa.pub. или для ed25519: clip < ~/.ssh/id_ed25519.pub 
2. Перейдите на GitHub и выберите пункт Settings (англ. «настройки») в меню аккаунта.
3. В меню слева нажмите на пункт SSH and GPG keys.
4. В открывшейся вкладке выберите New SSH key (англ. «новый SSH-ключ»).
* В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»).
* В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).
* В поле Key скопируйте ваш ключ из буфера обмена.
* Нажмите на кнопку Add SSH key (англ. «добавить SSH-ключ»).
5. Проверьте правильность ключа с помощью следующей команды. ssh -T git@github.com 

##Привязка удалённого репозитория к локальному 

1. Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.
2. Откройте консоль, перейдите в каталог локального репозитория и введите команду git remote add (от англ. remote — «удалённый» и add — «добавить»). Пример, git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
3. Убедиться, что репозитории связаны. Команда git remote -v
