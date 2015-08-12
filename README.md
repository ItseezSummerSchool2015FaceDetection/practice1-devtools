# Практика 1. Инструменты разработки программного обеспечения

[![Build Status](https://travis-ci.org/Itseez-NNSU-SummerSchool2015/practice1-devtools.svg)](https://travis-ci.org/Itseez-NNSU-SummerSchool2015/practice1-devtools)

## Цели

__Цель данной работы__ - реализовать набор простых фильтров, а именно фильтра 
сглаживания посредством вычисления среднего по окрестности, линейного фильтра 
с произвольным ядром, медианного фильтра, горизонтального фильтра Собеля. 
В задаче предполагается, что задана двумерная матрица с элементами типа 
`unsigned char`. Также для некоторых фильтров имеется размер ядра, либо само 
ядро фильтра, которое используется для вычисления линейной свертки. По существу 
ядро также является двумерной матрицей.

Проект представляет собой инфраструктуру для проведения практики по освоению
следующих инструментов разработки:

  - Система контроля версий [Git](https://git-scm.com/book/en/v2).
  - [Google Test Framework](https://code.google.com/p/googletest).
  - Утилита [CMake](http://www.cmake.org) для сборки исходных кодов.

## Общая структура проекта

Структура проекта:

  - `3rdparty` - библиотека Google Test.
  - `include` - директория для размещения заголовочных файлов.
  - `samples` - директория для размещения демо-приложений.
  - `src` - директория с исходными кодами.
  - `test` - директория с тестами.
  - `.gitignore` - перечень файлов, игнорируемых Git.
  - `.travis.yml` - конфигурационный файл для системы автоматического 
     тестирования Travis-CI.
  - `CMakeLists.txt` - корневой файл для сборки проекта с помощью CMake.
  - `README.md` - информация о проекте, которую вы сейчас читаете.

В проекте содержатся следующие модули:

  - Общий модуль `matrix` (`./include/matrix.hpp`, `./src/matrix.cpp`),
    содержащий простейшую реализацию класса матриц. Предполагается, что он не
    редактируется при реализации фильтров.
  - Модуль `filters`( `./include/filters.hpp`, `./src/filters_opencv.cpp`, 
    `./src/filters_fabrics.cpp`), содержащий объявление асбстрактного класса
    фильтров и его наследника, который реализует перечисленные фильтры 
    средствами библиотеки OpenCV.
  - Тесты для класса матриц и фильтров (`matrix_test.cpp`, `filters_test.cpp`).
  - Пример использования фильтра (`matrix_sample.cpp`).

## Задачи

__Основные задачи__:

  1. Разработать программную реализацию сглаживания посредством вычисления 
     среднего по окрестности, линейного фильтра с произвольным ядром, медианного 
     фильтра, горизонтального фильтра Собеля.
  2. Обеспечить работоспособность тестов, при необходимости отладить
     разработанную программную реализацию.
  3. Расширить реализацию класса матриц следующиими операциями и тестами к ним:
     1. Транспонирование матрицы.
     2. Умножение матриц (в виде перегрузки операции).
     3. Поэлементные операции сложения и вычитания (в виде перегрузки операции).
     4. Методы инициализации фиксированной константой, инициализация единичной 
        матрицы, инициализация диагональной матрицы с фиксированной константой.
     5. Вычисление детерминанта.
  4. Расширить программную реализацию вертикальным фильтром Собеля и 
     морфологическими операциями эрозии и дилатации.
     

__Дополнительные задачи__:
  1. 
  2. 

## Общие инструкции по работе с Git

В данном разделе описана типичная последовательность действий, которую 
необходимо выполнить перед тем, как начать работать с проектом. Далее 
для определенности используется репозиторий practice1-devtools.

  1. Создать аккаунт на [github.com](https://github.com), если такой
     отсутствует. Для определенности обозначим аккаунт `github-account`.

  2. Сделать fork репозитория
     <https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools> (в
     терминологии Git upstream-репозиторий) к себе в личный профиль с названием
     github-account. В результате будет создана копия репозитория с названием
     <https://github.com/github-account/practice1-devtools>
     (origin-репозиторий).

  3. Клонировать [origin][origin] репозиторий к себе на локальный компьютер,
     воспользовавшись следующей командой:

    ```
    $ git clone https://github.com/github-account/practice1-devtools
    ```

  4. Настроить адрес upstream-репозитория (потребуется при обновлении локальной 
     версии репозитория):

    ```
    $ git remote add upstream https://github.com/Itseez-NNSU-SummerSchool2015/practice1-devtools
    ```

  5. Настроить имя пользователя, из под которого будут выполняться все операции
     с репозиторием Git:

    ```
    $ git config --global user.name "github-account"
    ```

Когда сделан форк репозитория у вас создается по умолчанию единственная ветка 
master. Тем не менее, при решении независимых задач следует создавать рабочие 
ветки. Далее показаны основные команды для управления ветками на примере ветки
`filter-implementation`.

  1. Получение списка веток:
  
    ```
    $ git branch [-v]
    [-v] - список с информацией о последних коммитах
    ```

  2. Создание ветки:

    ```
    $ git branch filter-implementation
    ```

  3. Создать ветку `filter-implementation` и перейти в нее:

    ```
    $ git checkout [-b] filter-implementation
    # [-b] - создание и переход в ветку <branch_name>
    ```
  4. Удаление ветки в локальном репозитории:

    ```
    $ git branch -d <branch_name>
    ```

  5. Удаление ветки на сервере:

    ```
    $ git push [remotename] :[branch]
    ```

## Инструкция по выполнению работы

  7. Проверить, что загруженная версия проекта собирается и успешно выполняются
     все тесты. Для этого необходимо выполнить следующую последовательность
     действий:
     1. Рядом с директорией `practice1-devtools` создайте
        `practice1-devtools-build`. В новой директории будут размещены файлы
        решения и проектов, сгенерированные с помощью CMake.
     2. Перейдите в директорию `practice1-devtools-build`:

      ```
      $ cd ./practice1-devtools-build
      ```

     3. Сгенерируйте файлы решения и проектов с помощью утилиты CMake. Для этого
        можно воспользоваться графическим приложением, входящим в состав
        утилиты, либо выполнить команду

      ```
      $ cmake -DOpenCV_DIR="<OpenCVConfig.cmake-path>" -G <generator-name> <path-to-practice1-devtools>
      # <OpenCVConfig.cmake-path> - директория, в которой установлена 
        библиотека OpenCV и расположен файл OpenCVConfig.cmake
      # `<generator-name>` - название генератора, в случае тестовой
        инфраструктуры участников школы "Visual Studio 10 Win64"
      # `<path-to-practice1-devtools>` - путь до директории
        `practice1-devtools`, где лежат исходные коды проекта
      ```

     4. Откройте сгенерированный файл решения `practice1.sln`.
     
     5. Нажмите правой кнопкой мыши по проекту `ALL_BUILD` и выберите пункт
        `Rebuild` контекстного меню, чтобы собрать решение. В результате все
        бинарные файлы будут размещены в директории
        `practice1-devtools-build/bin`.
        
     6. Чтобы проверить работоспособность тестов, достаточно запустить
        `practice1_test.exe`. Если все тесты "зеленые", то можно двигаться
        дальше.

  8. Создать файл `filters_SURNAME.cpp` (файл с реализацией в файловой системе) 
     для собственных реализаций фильтров. В качестве шаблона необходимо 
     воспользоваться `filters_opencv.cpp`. Не забудьте после создания 
     файлов в файловой системе запустить еще раз CMake, чтобы подцепить 
     их в решение.

  9. Реализовать в созданном модуле необходимый набор из четырх фильтров 
     (фильтра сглаживания посредством вычисления среднего по окрестности, 
     линейного фильтра с произвольным ядром, медианного фильтра, 
     горизонтального фильтра Собеля). Прототипы методов фильтрации
     изменять нельзя! Не забывайте компилировать решение и проверять
     работоспособность тестов (см. п.7).

  10. После получения каждой стабильной версии не забудьте проверить
      работоспособность тестов и выложить изменения в ветку.

  ```
  $ git status # Получить список текущих изменений
  
  $ git add [<file_name>] # Добавить файл в репозиторий
  # <file_name> - название файла для добавления в commit
    если вместо имени указан символ *, то будут добавлены все новые файлы, 
    расширение которых не указано в .gitignore
  
  $ git commit [-m "<message_to_commit>"] [-a]
  # [-a] - автоматически добавляет изменения для существующих на сервере файлов
    без выполнения команды git add
  # [--amend] - перезаписывает последний коммит (используется, если не забыты
    изменения)
  
  $ git push origin filter-implementation
  ```

  11. Разработать пример использования фильтра. Разместить пример следует в
      модуле `filter_sample_SURNAME.cpp`. В качестве шаблона можно
      воспользоваться примером использования класса матриц.

  12. Не забудьте сделать Pull Request, чтобы проверить работоспособность тестов
      на Travis-CI и позволить преподавателям сделать ревью Вашего кода.

  13. При наличии времени можно расширить реализацию класса матриц операциями 
      и тестами к ним (перечень операций приведен в п.3 раздела "Цели и задачи").
      Также можно реализовать дополнительные фильтры (см. п.4 раздела "Цели 
      и задачи")

<!-- LINKS -->

[origin]: https://github.com/github-account/practice1-devtools
