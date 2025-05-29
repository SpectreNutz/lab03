dts@dts-HP-Pavilion-Notebook:~$ export GITHUB_USERNAME=SpectreNutz
dts@dts-HP-Pavilion-Notebook:~$ cd ${GITHUB_USERNAME}/workspace
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace$ pushd .
~/SpectreNutz/workspace ~/SpectreNutz/workspace
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace$ source scripts/activate
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab02.git projects/lab03
Клонирование в «projects/lab03»...
remote: Enumerating objects: 24, done.
remote: Counting objects: 100% (24/24), done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 24 (delta 4), reused 10 (delta 0), pack-reused 0 (from 0)
Получение объектов: 100% (24/24), 7.95 КиБ | 1.33 МиБ/с, готово.
Определение изменений: 100% (4/4), готово.
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace$ cd projects/lab03
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git remote remove origin
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ g++ -std=c++11 -I./include -c sources/print.cpp
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ls print.o
print.o
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ nm print.o | grep print
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ar rvs print.a print.o
ar: создаётся print.a
a - print.o
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ file print.a
print.a: current ar archive
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example1.cpp
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ls example1.o
example1.o
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ g++ example1.o print.a -o example1
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ./example1 && echo
hello
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ g++ -std=c++11 -I./include -c examples/example2.cpp
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ nm example2.o
0000000000000000 V DW.ref.__gxx_personality_v0
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED2Ev
0000000000000000 n _ZNSt15__new_allocatorIcED5Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZSt21ios_base_library_initv
0000000000000000 r _ZStL19piecewise_construct
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ g++ example2.o print.a -o example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ./example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat log.txt && echo
hello
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf example1.o example2.o print.o
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf print.a
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf example1 example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf log.txt
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ $ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(print)
> EOF
$: команда не найдена
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat > CMakeLists.txt <<EOF
> cmake_minimum_required(VERSION 3.4)
> project(print)
> EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
> EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (2.2s)
-- Generating done (0.0s)
-- Build files have been written to: /home/dts/SpectreNutz/workspace/projects/lab03/_build
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> 
add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat >> CMakeLists.txt <<EOF
> 
> target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/dts/SpectreNutz/workspace/projects/lab03/_build
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build --target print
[100%] Built target print
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build --target example1
[ 50%] Built target print
[100%] Built target example1
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build --target example2
[ 50%] Built target print
[100%] Built target example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ ls -la _build/libprint.a
-rw-rw-r-- 1 dts dts 2246 мая 29 21:40 _build/libprint.a
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ _build/example1 && echo
hello
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ _build/example2
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat log.txt && echo
hello
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf log.txt
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git clone https://github.com/tp-labs/lab03 tmp
Клонирование в «tmp»...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61 (from 1)
Получение объектов: 100% (91/91), 1.02 МиБ | 1.54 МиБ/с, готово.
Определение изменений: 100% (41/41), готово.
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ mv -f tmp/CMakeLists.txt .
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ rm -rf tmp
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cat CMakeLists.txt
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.1s)
-- Generating done (0.0s)
-- Build files have been written to: /home/dts/SpectreNutz/workspace/projects/lab03/_build
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ cmake --build _build --target install
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/dts/SpectreNutz/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/dts/SpectreNutz/workspace/projects/lab03/_install/include
-- Installing: /home/dts/SpectreNutz/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/dts/SpectreNutz/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/dts/SpectreNutz/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ tree _install
Команда «tree» не найдена, но может быть установлена с помощью:
sudo snap install tree  # version 2.1.3+pkg-5852, or
sudo apt  install tree  # version 2.1.1-2
См. 'snap info tree', чтобы посмотреть дополнительные версии.
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ sudo apt install tree
[sudo] пароль для dts: 
Чтение списков пакетов… Готово
Построение дерева зависимостей… Готово
Чтение информации о состоянии… Готово
Следующие НОВЫЕ пакеты будут установлены:
  tree
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 11 пакетов не обновлено.
Необходимо скачать 47,1 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 111 kB.
Пол:1 http://archive.ubuntu.com/ubuntu noble/universe amd64 tree amd64 2.1.1-2ubuntu3 [47,1 kB]
Получено 47,1 kB за 1с (78,0 kB/s)
Выбор ранее не выбранного пакета tree.
(Чтение базы данных … на данный момент установлено 217157 файлов и каталогов.)
Подготовка к распаковке …/tree_2.1.1-2ubuntu3_amd64.deb …
Распаковывается tree (2.1.1-2ubuntu3) …
Настраивается пакет tree (2.1.1-2ubuntu3) …
Обрабатываются триггеры для man-db (2.12.0-4build2) …
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ tree _install
_install
├── cmake
│   ├── print-config.cmake
│   └── print-config-noconfig.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

4 directories, 4 files
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git add CMakeLists.txt
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git commit -m"added CMakeLists.txt"
[main 70621d1] added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git push origin master
error: src refspec master ничему не соответствует
error: не удалось отправить некоторые ссылки в «https://github.com/SpectreNutz/lab03.git»
dts@dts-HP-Pavilion-Notebook:~/SpectreNutz/workspace/projects/lab03$ git push origin main

