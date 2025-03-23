# Реализация фундаментальной структуры данных - однонаправленного связанного списка.

## Содержание:

- [Описание проекта:](#описание-проекта)
- [Некоторые особенности:](#некоторые-особенности)
- [Предоставляемый функционал:](#предоставляемый-функционал)
  - [Итераторы:](#итераторы)
  - [Информация о списке:](#информация-о-списке)
  - [Обращение к элементам:](#обращение-к-элементам)
  - [Удаление элементов:](#удаление-элементов)
  - [Добавление элементов:](#добавление-элементов)
  - [Сортировка:](#сортировка)
- [Примеры использования:](#примеры-использования)
- [Лицензия:](#лицензия)
- [Автор:](#автор)

## Описание проекта:

Данный проект содержит реализацию однонаправленного связанного списка на языке программирования C++. Объект класса *LinkedList* представляет собой односвязный список. Вышеупомянутый класс включает в себя все основные операции, необходимые для эффективной работы со списком:

1) `ДОБАВЛЕНИЕ ЭЛЕМЕНТОВ В СПИСОК:` *добавление элементов в начало и конец списка.*
2) `УДАЛЕНИЕ ЭЛЕМЕНТОВ ИЗ СПИСКА:` *удаление элементов с начала и конца списка, удаление элементов по значению, полная очистка списка.*
3) `ПРОВЕРКА НАЛИЧИЯ ЭЛЕМЕНТА В СПИСКЕ:` *методы для определения, содержится ли определённый элемент в списке.*
4) `СОРТИРОВКА СПИСКА:` *реализация алгоритма сортировки элементов списка.*
5) `ДОСТУП К ЭЛЕМЕНТАМ СПИСКА:` *методы для получения значений первого и последнего элементов списка по ссылке, а также поддержка обращения к элементам списка по индексу.*
6) `ИНФОРМАЦИЯ О СПИСКЕ:` *методы для получения длины списка и проверка списка на пустоту.*
7) `ВЫВОД ЭЛЕМЕНТОВ СПИСКА:` *метод для удобного вывода всех элементов списка в консоль.*

- Кроме того, в проекте реализован итератор, позволяющий работать с данным контейнером через STL, что облегчает жизнь пользователю. Реализованы все необходимые конструкторы, обеспечено грамотное управление всеми ресурсами и строгое соблюдение принципов инкапсуляции. Также перегружены все необходимые операторы для удобства и эффективности использования класса.

## Некоторые особенности:

### Класс *LinkedList:*
1) Находится в пространстве имен *Containers*.
2) Является **шаблонным**, что позволяет пользователю работать с различными типами данных.

## Предоставляемый функционал:

### *Итераторы:*
- ```begin()``` -> возвращает итератор на первый элемент списка.
- ```end()``` -> возвращает итератор на элемент, который следует за последним ( это всегда nullptr ).

### *Информация о списке:*
- ```size()``` -> возвращает текущую длину списка.
- ```print()``` -> выводит в консоль значения всех элементов в порядке их расположения в списке.
- ```isEmpty()``` -> показывает, является ли список пустым ( возвращает соответствующее булевое значение ).
- ```find(const T& value)``` -> ищет первый элемент со значением value и возвращает указатель на этот элемент. Если элемент не был найден - возвращает nullptr.
- ```contains(const T& value)``` -> проверяет, есть ли в списке элемент со значением value. Возвращает соответствующее булевое значение.

### *Обращение к элементам:*
- ```front()``` -> возвращает значение первого элемента по ссылке.
- ```back()``` -> возвращает значение последнего элемента по ссылке.
- ```operator[int index]``` -> предоставляет доступ к элементам списка по индексу ( аналогично массивам ). Доступна как положительная индексация ( первый элемент имеет индекс 0 ), так и отрицательная ( последний элемент имеет индекс -1 ). Оператор возвращает значение элемента по ссылке. Важно! Обращение к элементу по индексу имеет сложность O(n), что может быть неэффективно для больших списков.

### *Удаление элементов:*
- ```clear()``` -> полностью очищает список.
- ```popFront()``` -> удаляет первый элемент из списка. Возвращает значение удаленного элемента.
- ```popBack()``` -> удаляет последний элемент из списка. Возвращает значение удаленного элемента.
- ```remove(const T& valueToRemove)``` -> удаляет первый элемент со значением valueToRemove. Возвращает true, если элемент с соответствующим значением был найден и удалён, иначе - false.
- ```removeAll(const T& valueToRemove)``` -> удаляет все элементы со значением valueToRemove. Возвращает true, если хотя бы один элемент был удалён, иначе - false.

### *Добавление элементов:*
- ```pushBack(const T& value)``` -> добавляет элемент со значением value в конец списка.
- ```pushFront(const T& value)``` -> добавляет элемент со значением value в начало списка.

### *Сортировка:*
- ```sort()``` -> сортирует список, используя пузырьковую сортировку. Важно! Данный метод использует алгоритм со сложностью O(n^2), что может быть неэффективно для больших списков.

## Примеры использования:

### *Итераторы:*
```
    // Создаём экземпляр связанного списка и инициализируем его элементами.
    Containers::LinkedList<int> numbers{1, 2, 3, 4, 5};

    // Используем стандартный алгоритм std::for_each для применения лямбда-функции к каждому элементу списка.
    std::for_each(numbers.begin(), numbers.end(), [](int& n) { n *= 2; });

    // Выводим содержимое списка после применения алгоритма.
    numbers.print(); // Вывод: 2 4 6 8 10
```
