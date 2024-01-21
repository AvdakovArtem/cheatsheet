# Шпаргалка. Базовые команды в консоли  
  
## Навигация  
  
- `pwd` (от англ. *print working directory*, «показать рабочую папку») — покажи, в какой я папке;  
- `ls` (от англ. *list directory contents*, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;  
- `ls -a` — покажи также скрытые файлы и папки, названия которых начинаются с символа .;  
- `cd first-project` (от англ. *change directory*, «сменить директорию») — перейди в папку `first-project`;  
- `cd first-project/html` — перейди в папку `html`, которая находится в папке `first-project`;  
- `cd ..` — перейди на уровень выше, в родительскую папку;  
- `cd ~` — перейди в домашнюю директорию (`/Users/Username`);  
- `cd /` — перейди в корневую директорию.  

## Работа с файлами и папками  
  
### Создание  
- `touch index.html` (англ. *touch*, «коснуться») — создай файл `index.html` в текущей папке;  
- `touch index.html style.css script.js` — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;  
- `mkdir second-project` (от англ. *make directory*, «создать директорию») — создай папку с именем `second-project` в текущей папке.  
  
### Копирование и перемещение  
- `cp file.txt ~/my-dir` (от англ. *copy*, «копировать») — скопируй файл в другое место;  
- `mv file.txt ~/my-dir` (от англ. *move*, «переместить») — перемести файл или папку в другое место.  
  
### Чтение  
- `cat file.txt` (от англ. *concatenate and print*, «объединить и распечатать») — распечатай содержимое текстового файла `file.txt`.  
  
### Удаление  
- `rm about.html` (от англ. *remove*, «удалить») — удали файл `about.html`;  
- `rmdir images` (от англ. *remove directory*, «удалить директорию») — удали папку `images`;  
- `rm -r second-project` (от англ. *remove*, «удалить» + *recursive*, «рекурсивный») — удали папку `second-project` и всё, что она содержит.  
  
## Полезные возможности  
- Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (`&&`).  
- У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (`↑`) и вниз (`↓`).  
- Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать `Tab`. Если файл или папка есть в текущей директории, командная строка допишет путь сама.  
- Например, вы находитесь в папке `dev`. Начните вводить `cd first` и дважды нажмите `Tab`. Если папка `first-project` есть внутри `dev`, командная строка автоматически подставит её имя. Останется только нажать `Enter`.  
  
## Хеш — основной идентификатор коммита  
- Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них рассчитывает уникальный идентификатор — хеш.  
- Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое закоммиченных файлов.  
- Все хеши, а также таблицу соответствий `хеш → информация о коммите` Git хранит в папке `.git`.  

## Исследуем лог коммита  
- Элементы описания коммита - `git log`.  
- Можно вызвать не только полный лог, но и сокращённый — это делается командой `git log --oneline`.  
- В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, как и полные.  
  
## HEAD — всему голова  
- В числе прочих файлов в папке `.git` есть служебный файл `HEAD`. Он указывает на самый свежий коммит.  
- Вместо хеша последнего коммита можно написать слово `HEAD` — Git вас поймёт.  
- Внутри `HEAD` — ссылка на служебный файл: `refs/heads/master` (или `refs/heads/main` в зависимости от названия ветки). Там находится хеш последнего коммита.  

## Статусы файлов в Git  
- `untracked/tracked` (англ. «*неотслеживаемый*»/«*отслеживаемый*») - Статусом `untracked` помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность `tracked`, в который попадают все файлы, отслеживаемые Git.  
- `staged` (англ. «*подготовленный*»)- Файл переходит в статус `staged` после выполнения `git add`.  
- `modified` (англ. «*изменённый*»)- Статус `modified` означает, что файл был изменён.  
  
####  **Для файлов в состояниях `staged` и `modified` обычно не указывают, что они также `tracked`, потому что это состояние подразумевается.**  
  
###Типичный жизненный цикл файла в Git  
- Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.  
- Схема изменения статусов коммита:  
```mermaid  
graph LR;  
untracked -- "git add"    --> staged;  
staged    -- "git commit" --> tracked/comitted;  
staged    -- "изменение"  --> modifiled;  
modifiled -- "git add"    --> staged;  
tracked   -- "изменение"  --> modifiled;  
```














