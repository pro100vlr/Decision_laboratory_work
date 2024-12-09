# Решение лабораторной работы

### Задача №1

<img width="569" alt="Снимок экрана 2024-12-05 в 04 47 11" src="https://github.com/user-attachments/assets/e4d69a8a-9025-42b0-af45-260190179dde">

Перешла на рабочий стол из домашней директории. Переместилась в Decision_lab, где будет хранится решение лабораторной работы, а затем cd Task1. Создала файл words.txt с помощью команды :

`echo -e "apple\nbanana\ncherry\npeach\ngrape\nmelon\npear\nplum" > words.txt`

Использовала команду grep с регулярным выражением для поиска слов длиной ровно 5 символов:

`grep -E "^.{5}$" words.txt > five_letter_words.txt`   

Что делвет эта строчка:

grep — это утилита для поиска строк, которые соответствуют указанному шаблону.

Флаг -E включает поддержку расширенных регулярных выражений.Расширенные регулярные выражения включают такие конструкции, как {}, (), | без необходимости экранирования символов.
В данном случае: используется для интерпретации конструкции {5} как "ровно 5 символов".

"^.{5}$" - Это регулярное выражение, определяющее шаблон для поиска строк:

^ - Обозначает начало строки.

. - Означает "любой символ", кроме символа новой строки.

{5} - Указывает количество символов, которое должно быть: ровно 5 .

$ - Обозначает конец строки.

words.txt - это имя входного файла, в котором выполняется поиск.

">" — оператор перенаправления вывода.

five_letter_words.txt — это имя выходного файла.

Проверила содержимое файла five_letter_words.txt с помощью команды cat.

Конечный результат представлен на скриншоте.


### Задача №2

<img width="564" alt="Снимок экрана 2024-12-05 в 05 05 24" src="https://github.com/user-attachments/assets/a1a16973-e788-4859-80be-5dc04fba18e6">

Перешла в папку Task2, создала и открыла файл logs.txt, куда внесла необходимые данные из условия задачи. 

Команда для нахождения строки с ошибками:

`grep "ERROR" logs.txt` 

Что делает команда:

Открывает файл logs.txt.,проверяет каждую строку, содержит ли она текст "ERROR",
выводит в терминал только те строки, которые содержат слово "ERROR".

Команда для подсчета количество предупреждений:

`grep -c "WARNING" logs.txt`       

Что делает команда: 

Читает файл logs.txt построчно, ищет строки, содержащие слово "WARNING"., считает количество таких строк, с помощью флага -с, выводит это количество в терминал.

Команда для вывода строки с информацией за последние 5 минут:

`grep "INFO" logs.txt | grep -E "10:0[5-9]"` 

Что делает команда: 

Символ | - передаёт вывод предыдущей команды в качестве входных данных для следующей команды.

Первая часть: grep "INFO" logs.txt - фильтрует строки, содержащие "INFO".

Вторая часть: grep -E "10:0[5-9]" :

Второй grep использует флаг -E для включения расширенных регулярных выражений .

Шаблон "10:0[5-9]" выполняет поиск строк, которые содержат время в диапазоне от 10:05 до 10:09.

Регулярное выражение "10:0[5-9]":

10: — фиксированная часть, указывающая на часы (10 часов).

0[5-9] — описывает минуты:
0 — первая цифра минут.

[5-9] — диапазон второй цифры минут (от 5 до 9).

Это означает, что будут выбраны строки, содержащие время от 10:05 до 10:09.

Конечный результат представлен на скриншоте.

### Задача №3

<img width="431" alt="Снимок экрана 2024-12-05 в 05 31 53" src="https://github.com/user-attachments/assets/ef22e779-5cb9-4b70-9729-5235a9792fb5">

<img width="420" alt="Снимок экрана 2024-12-05 в 05 32 33" src="https://github.com/user-attachments/assets/a9c65e0e-a843-47ed-9d18-d4c2eb065014">

Перешла в папку Task3, создала и открыла файл logs.txt. Он такой же как и во втором задании, но так как я нахожусь в другой папке я создала его заново.

Создала и открыла файл find_errors.sh, прописала в нем код :

<img width="400" alt="Снимок экрана 2024-12-05 в 05 35 46" src="https://github.com/user-attachments/assets/0053ae2e-6503-4e9c-ad98-7a287d9e5582">

Распишу свой код:

1. `#!/bin/bash`  

Это "shebang" — строка, которая указывает операционной системе, какой интерпретатор нужно использовать для выполнения скрипта.В данном случае это /bin/bash, то есть скрипт будет исполняться с помощью Bash.

2. `if [ -f "logs.txt" ]; then`  - это начало условной конструкции if, которая проверяет, существует ли файл logs.txt.
   
`[ -f "logs.txt" ]`  - флаг -f проверяет, существует ли файл logs.txt и является ли он обычным файлом (а не папкой, устройством и т.д.).

Если файл существует, условие возвращает true, и выполняется код в блоке then.
Если файла нет, условие возвращает false, и выполняется код в блоке else.

3. `grep "ERROR" logs.txt > error_logs.txt`   

Если файл logs.txt существует, эта команда выполняется.Что она делает:

`grep "ERROR" logs.txt` : ищет все строки в файле logs.txt, содержащие слово "ERROR".

">": перенаправляет результат команды (строки с "ERROR") в новый файл error_logs.txt.

Если файл error_logs.txt уже существует, он будет перезаписан.

4. echo "Строки с ошибками сохранены в error_logs.txt" - если файл logs.txt существует, эта команда выводит сообщение:

Строки с ошибками сохранены в error_logs.txt , это позволяет пользователю знать, что операция прошла успешно.

5. else - если условие в блоке if возвращает false (то есть файл logs.txt не существует), выполняется этот блок.
  
6. echo "Файл logs.txt не найден." - если файла logs.txt нет, выводится сообщение:

Файл logs.txt не найден.

8. fi - это завершение конструкции if. Означает конец условия.

Сделала скрипт исполняемым:

`chmod +x find_errors.sh ` :

chmod — команда для изменения прав доступа к файлу, +x — добавляет разрешение на выполнение файла, find_errors.sh — имя файла, к которому применяются изменения.

Потом создала файл error_logs.txt, куда будет записываться результат.

Запустила скрипт напрямую и с помощью команды cat посмотрела содержимое файла.

Конечный результат представлен на скриншоте

Вывод: Данная лабораторная работа полностью решена. Вся работа расписана по всем этапам реализации и каждая команда содержит описание своих элементов. Поставленные цели достигнуты, а также отработаны навыки по работе с grep.
