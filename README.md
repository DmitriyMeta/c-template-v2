# Шаблон для задач с оценкой уровня покрытия кода тестами

Все стандартные команды действуют.

Вместо автотестов выполняется сама программа (без аргументов командной строки) и оценивается уровень покрытия кода тестами.

Для локального тестирования установите программу lcov и выполните следующие команды:

```
make clean # если ранее запускали просто make
make coverage
./main
lcov --capture --directory . --no-external --output-file coverage.info
.github/coverage.sh
```

После выполнения последней команды откройте появившийся файл `coverage/index.html` в браузере, чтобы просмотреть подробный (построчный) отчёт о покрытии кода.

Обратите внимание на тот факт, что данные о покрытии накапливаются между разными запусками. Поэтому для «чистого» результата, который описывает только последнее состояние кода, лучше перед очередным запуском `./main` удалять файлы `coverage.info, *.gc*` вручную или с помощью команды `make clean`.
