# Итоговый проект по курсу С++ разработчик

## Задание
#### Реализовать терминальный файловый менеджер.
Файловый менеджер должен уметь выполнять введенные команды от пользователя:
- remove ${file} (удалить файл, пример remove ./test.txt)
- create ${file} (создать файл, пример create ./test.txt)
- exists ${file} (проверить существование файла, пример create ./test.txt)
- info ${file} (получить информацию о файле, пример info ./test.txt)
- copy ${file1} ${file2} (скопировать файл, пример copy ./test.txt /tmp/test.txt)
- move ${file1} ${file2} (переместить файл, пример move ./test.txt /tmp/test.txt)
- rename ${file} ${new_file} (переименовать файл, пример rename ./test.txt ./new_test.txt)

Стоит обрабатывать возможные ошибки пользователей (неправильные команды пользователей, а также неправильные аргументы команд), также стоит добавить логирование в ключевых местах файлового менеджера и unit-тесты для системы парсинга пользовательских команд.

## Реализация
Проект разбит на 7 файлов.\
В файле **ManagerFunction.h** реализована основная логика работы файлового менеджера с помощью стандартной библиотеки *"filesystem"*.\
В файле **ParseUserCommand** реализована функция парсинга пользовательских команд через стандартный поток ввода-вывода.\
Файл **UnitTests** реализует функции unit-тестирвания через функцию cтандартной библиотеки *"assert"*.\
Файл **Logger.h** является реализацией простого логгера, показаного Вадимом Балуном <https://www.youtube.com/watch?v=dhtj96gYw1g> с небольшими изменениями.\
Логгер для UNIX-подобных систем(Mac, Linux) создает файл data.log во временной папке /tmp/Logger. Для семейства систем Windows создается аналогичный файл в "C:\Logger\".\

Файл **main.cpp** собирает все вместе и реализует бесконечный цикл, ожидающий ввода команды пользователя. При вводе "help" выводится краткая справка по основным командам менеджера.
При вводе "cls" производится очистка экрана терминала. При вводе "test" запускаются юнит тесты. При вводе "exit" производится завершение работы программы.\
Проект протестирован в системах Linux Mint 21.3 и Windows 10.
