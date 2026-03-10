# lab01---report
# Laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов.

## Tutorial

1. Ознакомиться со ссылками учебного материала:  
   Ознакомился

2. Выполнить инструкцию учебного материала:
   ```bash
   $ export GITHUB_USERNAME=<имя_пользователя>
   $ export GIST_TOKEN=<сохраненный_токен>
   ```
   Выполнено

   ```bash
   $ mkdir -p ${GITHUB_USERNAME}/workspace
   $ cd ${GITHUB_USERNAME}/workspace
   $ pwd
   ```
   Вывод:
   ```
   /home/vboxuser/artoObs/workspace
   ```

   ```bash
   $ cd ..
   $ pwd
   ```
   Вывод:
   ```
   /home/vboxuser/artoObs
   ```

   ```bash
   $ mkdir -p workspace/tasks/
   $ mkdir -p workspace/projects/
   $ mkdir -p workspace/reports/
   $ cd workspace
   ```
   Папки созданы

   ```bash
   # Debian
   $ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
   $ tar -xf node-v6.11.5-linux-x64.tar.xz
   $ rm -rf node-v6.11.5-linux-x64.tar.xz
   $ mv node-v6.11.5-linux-x64 node
   ```
   Скачал и получил новую директорию

   ```bash
   $ ls node/bin
   ```
   Вывод:
   ```
   node  npm
   ```

   ```bash
   $ echo ${PATH}
   ```
   Вывод:
   ```
   /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/home/vboxuser/boost-build/bin
   ```

   ```bash
   $ export PATH=${PATH}:`pwd`/node/bin
   $ echo ${PATH}
   ```
   Вывод:
   ```
   /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/home/vboxuser/boost-build/bin:/home/vboxuser/artoObs/workspace/node/bin
   ```

   ```bash
   $ mkdir scripts
   $ cat > scripts/activate<<EOF
   export PATH=\${PATH}:`pwd`/node/bin
   EOF
   $ source scripts/activate
   ```
   Вывода не последовало.

   ```bash
   $ gem install gist
   ```
   gist уже был установлен

   Назначаны специальные права доступа с последующим помещением токена в защищённый файл
   ```bash
   $ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
   ```

## Homework

1. Скачано с wget
   ```bash
   ~$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
   ```
   Оповестил о скачивании

2. Распаковка: создал папку и распаковал
   ```bash
   ~$ mkdir ~/boost_1_69_0
   ~$ tar -xzf boost_1_69_0.tar.gz -C ~/boost_1_69_0
   ```
   Директория с файлами появилась

3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
   ```bash
   $ cd boost_1_69_0
   ~/boost_1_69_0$ find . -maxdepth 1 -type f | wc -l
   ```
   Вывод:
   ```
   12
   ```

4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
   ```bash
   ~/boost_1_69_0$ find . -type f | wc -l
   ```
   Вывод:
   ```
   61607
   ```

5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).  
   Для заголовочных файлов:
   ```bash
   ~/boost_1_69_0$ find . ~/boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" -o -name "*.hxx" \) | wc -l
   ```
   Вывод:
   ```
   15213
   ```

   Для файлов с разрешением .cpp:
   ```bash
   ~/boost_1_69_0$ find . -name "*.cpp" | wc -l
   ```
   Вывод:
   ```
   13803
   ```

   Для остальных файлов:
   ```bash
   ~/boost_1_69_0$ find . -type f ! \( -name "*.h" -o -name "*.hpp" -o -name "*.hxx" -o -name "*.cpp" \) | wc -l
   ```
   Вывод:
   ```
   32591
   ```

6. Найдите полный путь до файла any.hpp внутри библиотеки boost.
   > Здесь и в дальнейшем будут директория в директории, потому что я случайно создал лишнюю.
   ```bash
   ~/boost_1_69_0/boost_1_69_0$ find "$PWD" -name "any.hpp"
   ```
   Вывод:
   ```
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/fusion/include/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/type_erasure/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/proto/detail/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/hana/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/hana/fwd/any.hpp
   /home/vboxuser/boost_1_69_0/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
   ```

7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
   ```bash
   ~/boost_1_69_0/boost_1_69_0$ grep -rl "boost::asio" .
   ```
   Оно вывело огромное количество файлов:
   <details>
   <summary>Оно вывело огромное количество файлов: (огромное количество файлов):</summary>

   <!-- Здесь будет вставлен большой список файлов -->

   </details>

8. Скомпилируйте boost. Можно воспользоваться инструкцией или ссылкой.
   > Здесь у меня возникла проблема. Я не могу по какой-то причине использовать b2 повсеместно, она существует только локально. Но непосредственно в директории boost_1_69_0 я могу её использовать.

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
   ```bash
   $ mkdir -p ~/boost-libs
   $ mv ~/boost_1_69_0/stage/lib/*.a ~/boost-libs/
   ```

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
    ```bash
    ~/boost_1_69_0$ du -h ~/boost-libs/*
    ```
    > `-h` добавлен чисто для более удобных единиц измерения.  
    Вывод:
    ```
    4.0K	/home/vboxuser/boost-libs/libboost_atomic.a
    236K	/home/vboxuser/boost-libs/libboost_chrono.a
    156K	/home/vboxuser/boost-libs/libboost_container.a
    24K	/home/vboxuser/boost-libs/libboost_context.a
    336K	/home/vboxuser/boost-libs/libboost_contract.a
    152K	/home/vboxuser/boost-libs/libboost_date_time.a
    4.0K	/home/vboxuser/boost-libs/libboost_exception.a
    240K	/home/vboxuser/boost-libs/libboost_fiber.a
    420K	/home/vboxuser/boost-libs/libboost_filesystem.a
    832K	/home/vboxuser/boost-libs/libboost_graph.a
    168K	/home/vboxuser/boost-libs/libboost_iostreams.a
    2.0M	/home/vboxuser/boost-libs/libboost_locale.a
    216K	/home/vboxuser/boost-libs/libboost_prg_exec_monitor.a
    1.6M	/home/vboxuser/boost-libs/libboost_program_options.a
    80K	/home/vboxuser/boost-libs/libboost_random.a
    2.7M	/home/vboxuser/boost-libs/libboost_regex.a
    1.2M	/home/vboxuser/boost-libs/libboost_serialization.a
    28K	/home/vboxuser/boost-libs/libboost_stacktrace_addr2line.a
    28K	/home/vboxuser/boost-libs/libboost_stacktrace_backtrace.a
    16K	/home/vboxuser/boost-libs/libboost_stacktrace_basic.a
    4.0K	/home/vboxuser/boost-libs/libboost_stacktrace_noop.a
    4.0K	/home/vboxuser/boost-libs/libboost_system.a
    2.3M	/home/vboxuser/boost-libs/libboost_test_exec_monitor.a
    56K	/home/vboxuser/boost-libs/libboost_timer.a
    2.3M	/home/vboxuser/boost-libs/libboost_unit_test_framework.a
    4.5M	/home/vboxuser/boost-libs/libboost_wave.a
    784K	/home/vboxuser/boost-libs/libboost_wserialization.a
    ```

11. Найдите топ10 самых "тяжёлых".
    ```bash
    vboxuser@FirstTiMP:~/boost_1_69_0$ du -b ~/boost-libs/* | sort -nr
    ```
    Вывод (полный список):
    ```
    4700002	/home/vboxuser/boost-libs/libboost_wave.a
    2811642	/home/vboxuser/boost-libs/libboost_regex.a
    2359542	/home/vboxuser/boost-libs/libboost_test_exec_monitor.a
    2339254	/home/vboxuser/boost-libs/libboost_unit_test_framework.a
    2080954	/home/vboxuser/boost-libs/libboost_locale.a
    1617844	/home/vboxuser/boost-libs/libboost_program_options.a
    1214478	/home/vboxuser/boost-libs/libboost_serialization.a
    848770	/home/vboxuser/boost-libs/libboost_graph.a
    800184	/home/vboxuser/boost-libs/libboost_wserialization.a
    426024	/home/vboxuser/boost-libs/libboost_filesystem.a
    340050	/home/vboxuser/boost-libs/libboost_contract.a
    243086	/home/vboxuser/boost-libs/libboost_fiber.a
    241478	/home/vboxuser/boost-libs/libboost_chrono.a
    218846	/home/vboxuser/boost-libs/libboost_prg_exec_monitor.a
    171910	/home/vboxuser/boost-libs/libboost_iostreams.a
    155840	/home/vboxuser/boost-libs/libboost_container.a
    154866	/home/vboxuser/boost-libs/libboost_date_time.a
    81406	/home/vboxuser/boost-libs/libboost_random.a
    54552	/home/vboxuser/boost-libs/libboost_timer.a
    27148	/home/vboxuser/boost-libs/libboost_stacktrace_addr2line.a
    24874	/home/vboxuser/boost-libs/libboost_stacktrace_backtrace.a
    21032	/home/vboxuser/boost-libs/libboost_context.a
    13872	/home/vboxuser/boost-libs/libboost_stacktrace_basic.a
    2822	/home/vboxuser/boost-libs/libboost_stacktrace_noop.a
    2570	/home/vboxuser/boost-libs/libboost_atomic.a
    1646	/home/vboxuser/boost-libs/libboost_exception.a
    1428	/home/vboxuser/boost-libs/libboost_system.a
    ```

    Первые 10:
    ```bash
    vboxuser@FirstTiMP:~/boost_1_69_0$ du -b ~/boost-libs/* | sort -nr | head -10
    ```
    ```
    4700002	/home/vboxuser/boost-libs/libboost_wave.a
    2811642	/home/vboxuser/boost-libs/libboost_regex.a
    2359542	/home/vboxuser/boost-libs/libboost_test_exec_monitor.a
    2339254	/home/vboxuser/boost-libs/libboost_unit_test_framework.a
    2080954	/home/vboxuser/boost-libs/libboost_locale.a
    1617844	/home/vboxuser/boost-libs/libboost_program_options.a
    1214478	/home/vboxuser/boost-libs/libboost_serialization.a
    848770	/home/vboxuser/boost-libs/libboost_graph.a
    800184	/home/vboxuser/boost-libs/libboost_wserialization.a
    426024	/home/vboxuser/boost-libs/libboost_filesystem.a
    ```
