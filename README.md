![логотип](SCV_Git_0809\git-logo.png)
# Работа с Git

## 1. Проверить наличие установленного Git
 В терминале выполнить команду `git version`
 
 Если Git установлен, то появится сообщение с информацией о версии программы, иначе появится сообщение об ошибке.

 ## 2. Установка Git
 Загружаем последнюю версию Git с сайта => https://git-scm.com/downloads и устанавливаем с настройками по умолчанию.

 ## 3. Настройка Git
 При первом запуске Git необходимо представиться. Для этого в терминале необходимо ввести две команды:
 * `git config --global user.name "Ваше имя"`
 * `git config --global user.email "example@examle.com"`

## 4. Создание репозитория для Git

Для удобства работы с Git также необходимо установить программу VSCode => https://code.visualstudio.com/download.

После этого в удобном или необходимом месте создать папку. Эта папка и будет являться в последующем репозирорием (хранилищем) файла и изменений в нём произведённых.

Шаг по созданию репозитория с применением программы VSCode:

1. Запустить программу.
2. Строка меню: `Файл` => `Открыть папку` - выбрать ранее созданную папку репозитория.
3. Открыть терминал для ввода команд. Строка меню: `Вид` => `Терминал`
3. Инициализировать папку в качестве репозитория выполнив команду `git init`. 
При успешном выполенении должно появиться сообщение в терминале
```
$ git init
Initialized empty Git repository in "имя хранилища":/путь к папке/имя папки/.git/
```
4. Проверить, что всё выполнено верно. Для этого ввести команду `git status`.
При успешном выполнении должно появиться сообщение в терминале
```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```
5. В окне программы слева в окне `ПРОВОДНИК` правым кликом мыши (или через иконки рядом с именем папки) создать файл с расширением `"имя файла".md`.
Добавить этот файл для отслеживания в нём измнений введя команду `git add "имя файла".md`

6. Сделать запись о создании файла (коммит) командой: `git commit -m "текст понятного действия с файлом, что сделано/добавлено/удалено и т.п."` Далее проверить отображение коммита: `git status`. При успешном выполнении должно появиться сообщение в терминале типа:
```
$ git commit -m "текст коммита"
[master d2223a3] текст коммита
 1 file changed, 1 insertion(+)
```   
7. Команда типа `git diff` - показывает изменения в сравнении с последним выполненным коммитом, также позволяет сравнит между собой два разных коммита, или две ветки.

8. Команда типа `git log` - позволяет посмотреть что было сделано — историю коммитов.

9. Команда типа `git checkout` - позволяет переключиться на необходимую ветку и выйти из текущей.

## 4.1. Инициализация репозитория (семинар)

Выполнить инициализацию репозитория можно двумя способами.

1. В терминале перейти к папке, в которой хотим создать репозиторий. Выполнить команду 
```
git init
````
В исходной папке появится скрытая папка `*.git`.

2. Клонировать существующий репозиторий Git из любого места. Для этого выполнить команду
```
git clone <адрес репозитория>
```

## 5. Ещё о Git
Для лучшего понимания начала работы с Git и VSCode прослушайте:
* лекцию => https://www.youtube.com/watch?v=jeIDpIKLm3M&feature=emb_imp_woyt
* интерактивный учебник по Git =>  https://learngitbranching.js.org/?locale=ru_RU

## 6. Запись изменений в репозиторий.

Чтобы посмотреть состояние файла нужно воспользоваться командой `git status`.
Чтобы начать отслеживать новый файл нужно воспользоваться командой `git add <имя файла с расширением>`.

## 7. Работа с *.gitignore*

Чтобы хранить только исходный код и ничего лишнего, необходимо создать специальный файл в корне проекта с названием `.gitignore`.
Далее в этом файле в каждой строке можно указывать, какие файлы нужно игнорировать:
```
*.png
<имя файла>.<расширение файла>
<имя папки>/
```
Тогда, например, получится, что:

* `*.png` - это игнорирование всех графических изображений с данным расширением;
* `<имя файла>.<расширение файла>` - это игнорирование конкретного файла с конкретным расширением;
* `<имя папки>/` - это игнорирование всего содержимого указанной папки;

## 8. Ветки в GIT

Ветка - это последовательность коммитов (`commit`).
Коммиты - это в хронологическом порядке идущие сохранения статуса важных моментов.
Другое определение ветки - это ссылка на последний коммит (`commit`).

![Схема к теме веток](branch-1.png)

Для чего в основном нужны ветки:
* Ветки нужны, чтобы несколько программистов могли вести работу над одним и тем же проектом или даже файлом одновременно, при этом не мешая друг другу.
* Ветки используются для тестирования экспериментальных функций: чтобы не повредить основному проекту, создается новая ветка специально для экспериментов. Если эксперимент удался, изменения с экспериментальной ветки переносятся на основную, если нет – новая ветка попросту удаляется, а проект остается нетронутым.
* Ветки можно использовать для разных выходящих параллельно релизов одного проекта.

<<<<<<< HEAD
### 8.1 Прочие команды для веток.

* `git branch` - даёт список имеющихся веток и символом `*` помечает текущую ветку в которой вы находитесь;
* `git branch -v` - позволяет посмотреть последний коммит на каждой из веток;
* `git branch --merged` и `git branch--no-merged` - фильтруют и показывают список тех веток, которые слиты или не слиты соответственно в текущую ветку;
* `git branch -d <имя ветки>` - позволяет удалиьт ветку;
* `git branch --move <имя ветки исходное> <имя ветки нужное>` - позволяет переименовать ветку;