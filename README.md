# Сборка проекта

1. На сборочной машине (СМ) перейти в папку sigma_uni
2. Запустить файл build.код_проекта
3. Выбрать нужный пункт из предложенных вариантов
4. Дождаться окончания сборки
5. Для проверки качества сборки перейти в sigma_uni/LS/arm и запустить скрипт start1
6. Убедиться , что запускается ИТО , ППВ и ЗТ

# Развертывание среды на объекте

## Первый способ:

1. Запустить на ТН виртуальную среду с операционной системой МСВС5.0
2. Проверить подключение технологического ноутбука (ТН) к сети системы (ping 192.168.1.100)
3. Запустить программу elk-term.
4. Для переходу по ssh на 184 ввести ssh root@192.168.1.100 -> enter -> пароль.
5. Убедиться, что подключились к 184 прибору.
6. В консоли запустить mc, тем самым запустится программа Mightnight Comander на 184 приборе.
7. После подключения к 184 прибору, перейти в папку /mnt/SMO/LS/arm и запусить скрипт akill, тем самым остановив среду на приборе.
8. Перейти в /mnt/update/FromCD
9. На левой панели mc перейти по пути /mnt/Indata
10 Нажать F7 и создать папку temp и скопировать сюда из /mnt/update/FromCD файлы smo.img, data.img
11. В папке /mnt/Indata/temp должно быть два файла: smo.img, data.img
12. Нажать комбинацию клавиш Ctrl+O для перехода в консоль mc.
13. Ввести mount -o loop smo.img ./
14. В папке /mnt/Indata/temp должно смонтироваться smo.img
15. Должно появится содержимое файла smo.img
16. Перейти на другой панели на ТН
17. Для переходу по ssh на ТН нажать F9, выбрать ssh-соединение и ввести root@192.168.1.105 и Enter
18. Убедиться, что на панели развернулась файловая система ТН
19. Перейти в  этой панели по пути /home/kks/sigma_uni/LS/exe
20. На другой панели (184) перейти в /mnt/Indata/temp/LS/exe
21. Удалить содержимое LS/exe на 184
22. С помощью F5 скопировать файлы из папки exe ТН в папку exe 184
23. В панели ТН перейти в home/kks/sigma_uni/LS/lib
24. Скопировать файлы с расмширением *.so в папку /mnt/Indata/temp/LS/exe 184
25. В папке (184 прибор) /mnt/Indata/temp/  выполнить команду chown -R trassa:trassa ./* (выставляем права)
26. В папке (184прибор) /mnt/Indata/  выполнить команду umount temp
27. Убедиться , что в папке /mnt/Indata/temp 2 файла - smo.img, data.img
28. Ввести mount -o loop data.img ./
29. Убедиться, что в папке /mnt/Indata/temp смонтировалась директория data
30. Выполнить пункты 16-18
31. Перейти на панели с ТН по пути  /home/kks/sigma_uni/LS/data
32. Перейти на панели с 184 по пути /mnt/data
33. Удалить содержимое /mnt/data на 184
34. Скопировать из ТН в 184 содержимое папки data (F5)
35. Выполнить пункты 25,26,27
36. Открыть новую консоль на 184 (Выполнить 3-6) в четвертом пункте вместо ssh root@192.168.1.100 
37. Открыть mc
38. Перейти в папку /mnt/update/FromCD
39. На другой панели перейти в /mnt/Indata/temp
40. Создать в папке /mnt/Indata/temp подпапку backup
41. Скопировать из  /mnt/update/FromCD в /mnt/Indata/temp/backup файлы smo.img, data.img
42. Удалить файлы smo.img и data.img в папке /mnt/update/FromCD
43. Скопировать в папку /mnt/update/FromCD из папки /mnt/Indata/temp файлы smo.img, data.img 
44. Выполнить команду touch smo.img и команду touch data.img
45. Удедиться , что у файлов smo.img и data.img изменились даты измненения на текущие.
46. Перезапустить 184 прибор
47. После загрузки прибора выполнить контроль целостности на арм аби
48. Убедиться, что все  приборы обновились
49. Перезапустить всю систему.
50. После загрузки убедиться что система стартует автоматически
51. Убедиться в обновлении ПО.
