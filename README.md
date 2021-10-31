Подключение boost boost_1_77_0
скачиваем библиотеку с www.boost.org
разархивируем куда угодно (для WIN можно в корень для Linux usr/local/)
собираем в корне библиотеки: 
Win: 
bootstrap.bat gcc
./b2

Linux: (https://russianblogs.com/article/15101468858/)
sudo ./bootstrap.sh --prefix=local/usr/boost_1_77_0
sudo ./b2

Для Linux требуется подключить библиотеку потоков Threads в CmakeLists.txt