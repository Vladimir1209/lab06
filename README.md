#Labwork04
Установка rvm
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace# \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
```

```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace# echo "source /usr/local/rvm/scripts/rvm" >> scripts/activate
root@LabPythonVM:/home/student/Vladimir1209/workspace# pushd .
root@LabPythonVM:/home/student/Vladimir1209/workspace# source scripts/activate
```
Установка производилась с помощью openSSl
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace# wget https://www.openssl.org/source/old/1.0.2/openssl-1.0.2u.tar.gz
root@LabPythonVM:/home/student/Vladimir1209/workspace# tar xzf openssl-1.0.2u.tar.gz
root@LabPythonVM:/home/student/Vladimir1209/workspace# cd openssl-1.0.2u
root@LabPythonVM:/home/student/Vladimir1209/workspace/openssl-1.0.2u# ./config --prefix=/usr/local/openssl-1.0.2 shared
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/openssl-1.0.2u# make

root@LabPythonVM:/home/student/Vladimir1209/workspace/openssl-1.0.2u# sudo make install

rvm install 2.4.2 --with-openssl-dir=/usr/local/openssl-1.0.2
```
Установка ruby-2.4.2
```bash
ruby-2.4.2 - #removing src/ruby-2.4.2..
```
```sh
Installing Ruby from source to: /usr/local/rvm/rubies/ruby-2.4.2, this may take a while depending on your cpu(s)...
ruby-2.4.2 - #downloading ruby-2.4.2, this may take a while depending on your connection...
ruby-2.4.2 - #extracting ruby-2.4.2 to /usr/local/rvm/src/ruby-2.4.2.....
ruby-2.4.2 - #configuring...........................................................-
ruby-2.4.2 - #post-configuration..
ruby-2.4.2 - #compiling..............................................................
ruby-2.4.2 - #installing...........
ruby-2.4.2 - #making binaries executable..
ruby-2.4.2 - #downloading rubygems-3.0.9
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  865k  100  865k    0     0  1949k      0 --:--:-- --:--:-- --:--:-- 1949k
No checksum for downloaded archive, recording checksum in user configuration.
ruby-2.4.2 - #extracting rubygems-3.0.9.....
ruby-2.4.2 - #removing old rubygems........
ruby-2.4.2 - #installing rubygems-3.0.9.............................................-
ruby-2.4.2 - #gemset created /usr/local/rvm/gems/ruby-2.4.2@global
ruby-2.4.2 - #importing gemset /usr/local/rvm/gemsets/global.gems...................-
ruby-2.4.2 - #generating global wrappers........
ruby-2.4.2 - #gemset created /usr/local/rvm/gems/ruby-2.4.2
ruby-2.4.2 - #importing gemsetfile /usr/local/rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.4.2 - #generating default wrappers........
ruby-2.4.2 - #adjusting #shebangs for (gem irb erb ri rdoc testrb rake).
Install of ruby-2.4.2 - #complete 
Ruby was built without documentation, to build it run: rvm docs generate-ri
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace# rvm use 2.4.2 --default
root@LabPythonVM:/home/student/Vladimir1209/workspace# gem install travis -v 1.10.0
```
```sh
Done installing documentation for faraday-multipart, faraday-httpclient, faraday-excon, faraday-em_synchrony, faraday-em_http, faraday, faraday_middleware, gh, highline, travis after 2 seconds
10 gems installed
```
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace# git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab05
```
```sh
Клонирование в «projects/lab05»...
remote: Enumerating objects: 19, done.
remote: Counting objects: 100% (19/19), done.
remote: Compressing objects: 100% (13/13), done.
remote: Total 19 (delta 2), reused 19 (delta 2), pack-reused 0 (from 0)
Получение объектов: 100% (19/19), готово.
Определение изменений: 100% (2/2), готово.
```
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace# cd projects/lab05
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# ls
CMakeLists.txt	examples  include  README.md  sources
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git remote remove origin
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git remote add origin https://github.com/${GITHUB_USERNAME}/lab05
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# cat > .travis.yml <<EOF
```
```sh
> language: cpp
> script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
> addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
> EOF
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# travis login --github-token ${GITHUB_TOKEN}
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# travis lint
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# ex -sc '1i|[![Build Status](https://travis-ci.com/'"${GITHUB_USERNAME}"'/lab05.svg?branch=master)](https://travis-ci.com/'"${GITHUB_USERNAME}"'/lab05)' -cx README.md
```
```sh
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git add .travis.yml
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git add README.md
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git commit -m"added CI"
```
```sh
[master f0bd37c] added CI
 2 files changed, 13 insertions(+)
 create mode 100644 .travis.yml
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# git push origin master
Username for 'https://github.com': Vladimir1209
Password for 'https://Vladimir1209@github.com': 
Перечисление объектов: 23, готово.
Подсчет объектов: 100% (23/23), готово.
При сжатии изменений используется до 4 потоков
Сжатие объектов: 100% (17/17), готово.
Запись объектов: 100% (23/23), 4.18 КиБ | 4.18 МиБ/с, готово.
Всего 23 (изменений 4), повторно использовано 17 (изменений 2), повторно использовано пакетов 0
remote: Resolving deltas: 100% (4/4), done.
To https://github.com/Vladimir1209/lab05
 * [new branch]      master -> master
```
```bash
root@LabPythonVM:/home/student/Vladimir1209/workspace/projects/lab05# popd
/home/student/Vladimir1209/workspace
root@LabPythonVM:/home/student/Vladimir1209/workspace# export LAB_NUMBER=04
root@LabPythonVM:/home/student/Vladimir1209/workspace# git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
Клонирование в «tasks/lab05»...
remote: Enumerating objects: 84, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 84 (delta 0), reused 0 (delta 0), pack-reused 81 (from 1)
Получение объектов: 100% (84/84), 2.11 МиБ | 7.32 МиБ/с, готово.
Определение изменений: 100% (23/23), готово.
root@LabPythonVM:/home/student/Vladimir1209/workspace# mkdir reports/lab${LAB_NUMBER}
root@LabPythonVM:/home/student/Vladimir1209/workspace# cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
root@LabPythonVM:/home/student/Vladimir1209/workspace# cd reports/lab${LAB_NUMBER}
```

