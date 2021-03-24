# Отчёт по Lab01

## При выполнении учебного материала были выполнены команды
```asm
export GITHUB_USERNAME=matveybaykalov
export GIST_TOKEN=51fa90858a0ec8d919d074aa1e6e061cbbac9e7e

mkdir -p ${GITHUB_USERNAME}/workspace
cd ${GITHUB_USERNAME}/workspace
pwd
cd ..
pwd

mkdir -p workspace/tasks/
mkdir -p workspace/projects/
mkdir -p workspace/reports/
cd workspace

wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
tar -xf node-v6.11.5-linux-x64.tar.xz
rm -rf node-v6.11.5-linux-x64.tar.xz
mv node-v6.11.5-linux-x64 node

ls node/bin
echo ${PATH}
export PATH=${PATH}:`pwd`/node/bin
echo ${PATH}
mkdir scripts
cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
source scripts/activate

gem install gist

(umask 0077 && echo ${GIST_TOKEN} > ~/.gist)

export LAB_NUMBER=01
git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
mkdir reports/lab${LAB_NUMBER}
cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
cd reports/lab${LAB_NUMBER}
edit REPORT.md
gist REPORT.md
```

## При выполнении домашнего задания были выполнены команды
1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания
    ```asm
    wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
    ```
    Результат выполнения команды
    ```asm
    --2021-03-21 17:49:47--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
    Resolving sourceforge.net (sourceforge.net)... 216.105.38.13
    Connecting to sourceforge.net (sourceforge.net)|216.105.38.13|:443... connected.
    HTTP request sent, awaiting response... 301 Moved Permanently
    Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/ [following]
    --2021-03-21 17:49:48--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
    Reusing existing connection to sourceforge.net:443.
    HTTP request sent, awaiting response... 302 Found
    Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download [following]
    --2021-03-21 17:49:48--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
    Reusing existing connection to sourceforge.net:443.
    HTTP request sent, awaiting response... 302 Found
    Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=1616338189&use_mirror=deac-ams&r= [following]
    --2021-03-21 17:49:48--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=1616338189&use_mirror=deac-ams&r=
    Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 216.105.38.13
    Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|216.105.38.13|:443... connected.
    HTTP request sent, awaiting response... 302 Found
    Location: https://deac-ams.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz [following]
    --2021-03-21 17:49:49--  https://deac-ams.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz
    Resolving deac-ams.dl.sourceforge.net (deac-ams.dl.sourceforge.net)... 185.34.27.55
    Connecting to deac-ams.dl.sourceforge.net (deac-ams.dl.sourceforge.net)|185.34.27.55|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 111710205 (107M) [application/x-gzip]
    Saving to: ‘boost_1_69_0.tar.gz’
    
    boost_1_69_0.tar.gz     100%[=============================>] 106.53M   527KB/s    in 2m 36s
    
    2021-03-21 17:52:26 (699 KB/s) - ‘boost_1_69_0.tar.gz’ saved [111710205/111710205]
    ```
2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
    
    Перед разархивированием была создана директория boost_1_69_0
    ```asm
    mkdir -p boost_1_69_0
    mv boost_1_69_0.tar.gz boost_1_69_0
    tar -xf node-v6.11.5-linux-x64.tar.xz
    ```
3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
    ```asm
    tree -aL 1 | wc -l
    ```
    Результат выполнения команды
    ```asm
    21
    ```
4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
    ```asm
    tree -aR | wc -l
    ```
    Результат выполнения команды
    ```
    66831
    ```
5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
    + Количество заголовочных файлов, файлов с расширением .cpp
      ```asm
        find . -name "*.cpp" -o -name "*.h" -o -name "*.hpp" | wc -l
        ```
      Результат выполнения команды
      ```asm
        28982
        ```
    + Количество не заголовочных и не .cpp
        ```asm
        find . -not -name "*.cpp" -o -not -name "*.h" -o -not -name "*.hpp" -type f| wc -l
        ```
        Результат выполнения команды
        ```asm
        66829
        ```
6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
    ```asm
    find . -name 'any.hpp'
    ```
    Результат выполнения команды
    ```asm
    ./boost/any.hpp
    ./boost/fusion/algorithm/query/any.hpp
    ./boost/fusion/algorithm/query/detail/any.hpp
    ./boost/fusion/include/any.hpp
    ./boost/hana/any.hpp
    ./boost/hana/fwd/any.hpp
    ./boost/proto/detail/any.hpp
    ./boost/spirit/home/support/algorithm/any.hpp
    ./boost/type_erasure/any.hpp
    ./boost/xpressive/detail/utility/any.hpp
    ```
7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
   ```asm
   grep -r -l 'boost::asio' .
   ```
8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
    ```asm
    mv boost_compil/ boost-libs
    ```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
    ```asm
    find . -type f -exec du {} + | sort -rn | head 10
    ```
    Результат выполнения команды
   ```
   4624    ./lib/libboost_wave.a
   4336    ./lib/libboost_log.a
   3384    ./lib/libboost_locale.a
   3268    ./lib/libboost_regex.a
   2864    ./lib/libboost_math_tr1.a
   2832    ./lib/libboost_math_tr1l.a
   2784    ./lib/libboost_math_tr1f.a
   2680    ./lib/libboost_log_setup.a
   2332    ./lib/libboost_test_exec_monitor.a
   2316    ./lib/libboost_unit_test_framework.a
   ```
