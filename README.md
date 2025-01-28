# SimpleBashUtils
Development of Bash text utilities: cat, grep.
В этом проекте тебе предстоит познакомиться с базовыми утилитами Bash по работе с текстами на языке программирования С и научиться их разрабатывать. Эти утилиты (cat и grep) достаточно часто используются при работе в терминале Linux. В рамках этого проекта ты также узнаешь, как организованы утилиты Bash, и научишься структурному подходу.  
## Chapter II

## Information

### История cat

> cat был частью ранних версий Unix, например, Версии 1, и заменил pr, утилиту PDP-7 и Multics для копирования одного файла на экран.

### Использование cat

cat — одна из наиболее часто используемых команд в Unix-подобных операционных системах. Команда имеет три взаимосвязанные функции в отношении текстовых файлов: отображение, объединение их копий и создание новых.

`cat [OPTION] [FILE]...`

### Опции cat

| № | Опции | Описание |
| ------ | ------ | ------ |
| 1 | -b (GNU: --number-nonblank) | нумерует только непустые строки |
| 2 | -e предполагает и -v (GNU only: -E то же самое, но без применения -v) | также отображает символы конца строки как $  |
| 3 | -n (GNU: --number) | нумерует все выходные строки |
| 4 | -s (GNU: --squeeze-blank) | сжимает несколько смежных пустых строк |
| 5 | -t предполагает и -v (GNU: -T то же самое, но без применения -v) | также отображает табы как ^I |

### История grep 

> Томпсон написал первую версию на PDP-11 языке ассемблера, чтобы помочь Ли Э. МакМахону проанализировать текст «Записок Федералиста» и определить авторство отдельных статей. Текстовый редактор ed (также созданный Томпсоном) имел поддержку регулярных выражений, но его нельзя было использовать для такого большого объема текста, поэтому Томпсон извлек этот код в отдельный инструмент. Он выбрал это название, потому что в ed команда g / re / p печатала все строки, соответствующие заданному шаблону. 
grep впервые был включен в Версию 4 Unix. Заявив, что он «обычно упоминается как прототип программного средства», Макилрой приписал grep «безвозвратное внедрение» философии инструментов Томпсона в Unix.

### Использование grep 

`grep [options] template [file_name]`

### Опции grep 

| № | Опции | Описание |
| ------ | ------ | ------ |
| 1 | -e | Шаблон. |
| 2 | -i | Игнорирует различия регистра.  |
| 3 | -v | Инвертирует смысл поиска соответствий. |
| 4 | -c | Выводит только количество совпадающих строк. |
| 5 | -l | Выводит только совпадающие файлы.  |
| 6 | -n | Предваряет каждую строку вывода номером строки из файла ввода. |
| 7 | -h | Выводит совпадающие строки, не предваряя их именами файлов. |
| 8 | -s | Подавляет сообщения об ошибках о несуществующих или нечитаемых файлах. |
| 9 | -f file | Получает регулярные выражения из файла. |
| 10 | -o | Печатает только совпадающие (непустые) части совпавшей строки. |


## Chapter III

- Программы должны быть разработаны на языке С стандарта C11 с использованием компилятора gcc.
- Код программ cat и grep должен находиться в ветке develop в папках src/cat/ и src/grep/ соответственно. 
- Не используй устаревшие и выведенные из употребления конструкции языка и библиотечные функции. Обращай внимание на пометки legacy и obsolete в официальной документации по языку и используемым библиотекам. Ориентируйся на стандарт POSIX.1-2017.
- При написании кода необходимо придерживаться Google Style.
- Программы должны представлять собой исполняемый файл с аргументами командной строки
- Сборка программ должна быть настроена с помощью Makefile с соответствующими целями: s21_cat, s21_grep.
- Если используешь сторонние библиотеки, в Makefile должны быть заложены сценарии сборки, предусматривающие их подключение/загрузку.
- Необходимо покрытие интеграционными тестами для всех вариантов флагов и входных значений, на базе сравнения с поведением реальных утилит Bash.
- Программа должна быть разработана в соответствии с принципами структурного программирования.
- Необходимо исключить дублирование кода, переиспользовать общие модули между утилитами. Общие модули можно вынести в отдельную папку src/common.
- Можно использовать стандартные и нестандартные библиотеки языка С, а можно собственноручно разработанные библиотеки из других проектов.
- Формулировка сообщения при возникновении ошибочной ситуации не имеет значения.
- Ввод через stdin обрабатывать не обязательно.


## Part 1. Работа с утилитой cat

Тебе необходимо разработать утилиту cat:
- Она должна поддерживать все флаги (включая GNU версии), указанные [выше](#cat-опции).
- Исходные, заголовочные и сборочные файлы должны располагаться в директории src/cat/.
- Итоговый исполняемый файл должен располагаться в директории src/cat/ и называться s21_cat.

## Part 2. Работа с утилитой grep

Тебе необходимо разработать утилиту grep:
- Поддержка следующих флагов: `-e`, `-i`, `-v`, `-c`, `-l`, `-n`.
- Для регулярных выражений можно использовать только библиотеки pcre или regex. 
- Исходные, заголовочные и make файлы должны располагаться в директории src/grep/.
- Итоговый исполняемый файл должен располагаться в директории src/grep/ и называться s21_grep.

## Part 3. Дополнительно. Реализация некоторых флагов утилиты grep

А это необязательное задание на дополнительные баллы: разработай утилиту grep:
- Поддержка всех флагов, включая: `-h`, `-s`, `-f`, `-o`.
- Для регулярных выражений можно использовать только библиотеки pcre или regex. 
- Исходные, заголовочные и make файлы должны располагаться в директории src/grep/.
- Итоговый исполняемый файл должен располагаться в директории src/grep/ и называться s21_grep.

## Part 4. Дополнительно. Реализация комбинаций флагов утилиты grep

А это необязательное задание на дополнительные баллы: разработай утилиту grep:
- Поддержка всех флагов, включая их _парные_ комбинации (например, `-iv`, `-in`).
- Для регулярных выражений можно использовать только библиотеки pcre или regex.
- Исходные, заголовочные и make файлы должны располагаться в директории src/grep/.
- Итоговый исполняемый файл должен располагаться в директории src/grep/ и называться s21_grep.

