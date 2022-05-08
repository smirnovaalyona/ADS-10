# Алгоритмы и структуры данных (ADS-10)

![GitHub pull requests](https://img.shields.io/github/issues-pr/NNTU-CS/ADS-10)
![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/NNTU-CS/ADS-10)

Срок выполнения задания:

**до 05 июня** 

![Relative date](https://img.shields.io/date/1654462800)

## Задание

> Разработать версию дерева вариантов (возможностей) для генерации всех перестановок заданного массива цифр

## Пояснение

Одной из задач комбинаторики является генерация всех перестановок элементов. Возьмем, к примеру, цифры 1,2,3. Из этих цифр можно образовать следующие последовательности:

```
123
132
213
231
312
321
```

В качестве решения задачи генерации всех перестановок можно использовать **дерево вариантов**

![](images/51.gif)

На рисунке используются цифры 1,3,5,7. Они образуют множество потомков 1 уровня. От каждого узла вниз отходят по три связи к узлам, в которых находятся оставшиеся цифры в множестве (например 3,5,7 для 1). Передвигаясь на уровень ниже мы можем использовать цифры, которые не встречаются на пути от корня. На уровне три мы можем организовать не более двух связей для каждого узла.

Если опуститься еще на один уровень, то связей будет по одной. Так, от цифры 5 мы можем образовать потомка с 7, а от 7 - 5.

Если двигаться от корня к листьям, мы будем получать возможные комбинации. 

```
1357
1375
1537
1573
...
```

## Алгоритм построения дерева

Перед началом необходимо разработать узел дерева, в котором будет находиться массив из указателей на узлы нижнего уровня. Число указателей нужно ограничить.

1. Вызываем первый раз функцию построения дерева с массивом из исходных элементов (например, 1,3,5,7).
1. Для корня дерева образуем потомков по числу цифр в массиве (например, как на рисунке четыре).
1. Вызываем функцию построения дерева рекурсивно и передаем ей массив из оставшихся цифр. То есть, для узла с 1 массив должен содержать 3,5,7. 
1. Образуем потомков и присваиваем им значения из массива.
1. Рекурсивно для каждого потомка передаем массив из двух элементов.
1. Рекурсия должна остановится, когда передаваемый массив будет пустой.

## Алгоритм получения перестановок

Для получения перестановок необходимо сделать проход по дереву, начиная с корня и выдавая элементы, хранящиеся в узлах. Обход должен начинаться с левых значений и постепенно двигаться к правым.

## Состав проекта

В файл **include/tree.h** необходимо поместить описание дерева **Tree** с основными функциями. Рекомендуется выполнить класс **Tree** в виде шаблона.

В файл **src/alg.cpp** поместить реализацию функции **getPermut(Tree& tree, int num)**, возвращающую перестановку с номером **num** 

Файл **src/main.cpp** должен содержать примеры получения всех перестановок.


