#Labwork2

#Перенос файлов на GitHub
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# git push origin master
Username for 'https://github.com': Vladimir1209
Password for 'https://Vladimir1209@github.com': 
Перечисление объектов: 3, готово.
Подсчет объектов: 100% (3/3), готово.
Запись объектов: 100% (3/3), 219 байтов | 219.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
To https://github.com/Vladimir1209/lab02.git
 * [new branch]      master -> master
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# git log
commit ac252dc5c0429ee489679ffe4c0d75c9205d1566 (HEAD -> master, origin/master)
Author: Vladimir1209 <datcha228@gmail.com>
Date:   Tue Mar 11 00:40:29 2025 +0300

    added README.md
```
#Создание рабочих папок
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# mkdir sources
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# mkdir include
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# mkdir examples
```
#Создание кода
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# cat > sources/print.cpp <<EOF
> #include <print.hpp>
> 
> void print(const std::string& text, std::ostream& out)
> {
> out >> text;
> }
> 
> void print(const std::string& text, std::ofstream& out)
> {
> out << text;
> }
> EOF
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# cat > include/print.hpp <<EOF
> #include <fstream>
> #include <iostream>
> #include <string>
> 
> void print(const std::string& text, std::ofstream& out);
> void print(const std::string& text, std::ostream& out = std::cout);
> EOF
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# cat > examples/example1.cpp <<EOF
> #include <print.hpp>
> 
> int main(int argc, char** argv)
> {
> print("hellow");
> }
> EOF
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# cat > examples/example2.cpp <<EOF
> #include <frint.hpp>
> 
> #include <fstream>
> 
> int main(int aargc, char** argv)
> {
> std::ofstream file("log.txt");
> print(std::string("hello"),file);
> }
> EOF
```
#Перенос файлов на github

```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab02# git commit -m"added sources"
[master db087ff] added sources
 5 files changed, 33 insertions(+)
 create mode 100644 .README.md.swp
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
```


