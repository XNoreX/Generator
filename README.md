# Generator
Процедурный генератор дорог и зданий

Для того, чтобы использовать процедурный генератор необходимо класс «BP_Generator» перенести на сцену и настроить его параметры, для этого нужно выбрать генератор на сцене и перейти во вкладку Details:
«Road Modules» – массив с тайлами дорог, можно указать прямую дорогу и перекрёсток (Этого достаточно), тайлы зданий сюда помещать не нужно.
«House Modules» – массив с тайлами зданий, можно указывать сколько угодно.
«Area Size» – параметр отвечающий за размер области генерации.

После того, как все тайлы указаны и параметр размера зоны генерации тоже первым делом необходимо сгенерировать дороги, за это отвечает кнопка «Generate Roads». Если сетка дорог Вам не понравилась, то Вы можете снова нажать на кнопку «Generate Roads» и цикл повторится. 

После того, как дорожная сетка будет создана Вы можете заполнить пустое пространство между дорог зданиями, за это отвечает кнопка «Generate House», работает аналогично генерации дорог.

Кнопки «Clear Roads» и «Clear House» отвечают за очистку сетки от соответствующих типов тайлов, при нажатии на эти кнопки полного удаления тайлов не происходит, тайлы удаляются частями при каждом нажатии.

Кнопка «Clear All»  полностью и моментально очищает область генерации от всех тайлов.

Параметры тайла
Сам actor тайла наследуется от класса BP_Module и имеет следующие параметры:
Сокеты X; -X; Y; -Y; К этим сокетам крепятся последующие тайлы при генерации, для дорог настоятельно рекомендуется не передвигать сокеты в разных направлениях по их плоскости (Необходимо доработать)
Static Mesh – основной статический меш объекта, сюда можно поместить 3д модель объекта такого масштаба, чтобы его границы помещались в границы сокетов. Так же можно добавлять дополнительные Static Mesh.

Параметры Default:
Module Type – тип данного модуля, хранятся в Enum классе «E_ModuleType». Можно добавлять свои.
Allowed Road Module Type – Массив с типами возможных дорожных модулей
Allowed Roads Sockets – Массив с доступными сокетами на местах которых будут генерироваться разрешённые дорожные модули.
Allowed House Sockets - Массив с доступными сокетами на местах которых будут генерироваться указанные в классе генератора модули зданий.




Плагин для процедурной генерации позволяет создавать сети дорог из тайлов прямого типа и перекрёстков, а так-же создавать здания внутри образовывающихся полостей, но при генерации сети дорог есть необходимость доработать алгоритм генерации в следующем:

1). Можно добавить тайлам вероятность создания для того, чтобы чаще создавались прямые участки и места для зданий было больше.
2). В некоторых местах прямая дорога подходит практически вплотную в другой прямой дороге, которая стоит боком, необходимо обратить внимание на этот момент.
3). На данном этапе невозможно создавать очень большие тайлы, их размер ограничен радиусом в 100units, это необходимо доработать в будущем.
4). При создании тайла можно спавнить тайл не на месте сокета соседнего тайла, а производить Atach Socket To Socket.
