# Домашнее задание к лекции «Интернет — большая библиотека»

## Исходный код (без комментариев)
```javascript
let retireAge; 

function calcRetiredAge(isFemaleGender) {

}
// calcRetiredAge — это функция вычисления пенсионного возраста, в качестве аргумента передаём пол (isFemaleGender).

function colorizeDots(weeks) {
  let dots = document.getElementsByClassName("app-table__body-dot"); 
  emptyDots(); 
  for (let i = 0; i < weeks && i < dots.length; i++) {
    let colorClass; 

    // Удаляем класс пустой точки:
    dots[i].classList.remove('_empty'); 
    // Добавляем новый класс, который вычислили выше:
    dots[i].classList.add(colorClass);
  }
}
```

## Пояснение кода
В коде описана функция `calcRetiredAge`, которая должна вычислять пенсионный возраст в зависимости от передаваемого пола. И функция `colorizeDots`, которая должна закрашивать все прожитые недели. Внутри функции в переменную `dots` помещаются все объекты точек со страницы. Затем вызывается функция `emptyDots`, которая очищает все закрашенные точки (её реализация была в прошлом домашнем задании). После обнуления всех точек их необходимо закрасить. Поэтому реализован цикл, который будет перебирать столько точек, сколько было прожитых недель. Внутри цикла каждая точка должна быть закрашена (реализация домашнего задания). Для закрашивания в переменную `colorClass` должно присваиваться строковое значение, соответствующее жизненному промежутку. После присвоения нужного значения. У перебираемой точки необходимо убрать класс `_empty` и добавить класс, соответствующий жизненному интервалу.

# Задание 1
Первое условие должно быть в функции `calcRetiredAge`. 
1. Если значения аргумента `isFemaleGender` является *истиной*, то присвоить в переменную `retireAge` значение 60.
2. Если значения аргумента `isFemaleGender` является *ложью*, то присвоить в переменную `retireAge` значение 65.

```javascript
if(isFemaleGender){
    retireAge = 60;
} else {
    retireAge = 65;
}
```
Так как в переменной `isFemaleGender` может быть только логическое сравнение, то существует только 2 варианта сравнения `true === true` (в результате будет `true`) и `false === true` (в результате будет `false`). Так что в данном случае можно даже не использовать сравнение, а просто проверять аргумент `isFemaleGender`. Сравнение `isFemaleGender === true` тоже рабочее, но менее аккуратное.

## Задача №2
Второе условие должно быть в функции `colorizeDots` (в этой функции проверка будет выполняться на каждой итерации цикла).
1. Если значение перебираемой недели меньше произведения 18 (количества лет) на 52 (количество недель в году), то присвойте переменной `colorClass` значение `_young` (это детство).
2. Если значение перебираемой недели меньше, чем произведение `retireAge` на количество недель в году, то присвойте переменной `colorClass` значение `_adult` (это взрослая жизнь).
3. Если значение перебираемой недели больше либо равно произведению `retireAge` на количество недель в году, то присвойте переменной `colorClass` значение `_senior` (это старость).

```javascript
if(i < 18 * 52) {
    colorClass = '_young';
}
else if(i < retireAge * 52) {
    colorClass = '_adult';
}
else {
    colorClass = '_senior';
}
```

## Правильное решение
```javascript
let retireAge; 

function calcRetiredAge(isFemaleGender) {
    if(isFemaleGender){
        retireAge = 60;
    } else {
        retireAge = 65;
    }
}
// calcRetiredAge — это функция вычисления пенсионного возраста, в качестве аргумента передаём пол (isFemaleGender).

function colorizeDots(weeks) {
  let dots = document.getElementsByClassName("app-table__body-dot"); 
  emptyDots(); 
  for (let i = 0; i < weeks && i < dots.length; i++) {
    let colorClass; 

    if(i < 18 * 52) {
        colorClass = '_young';
    }
    else if(i < retireAge * 52) {
        colorClass = '_adult';
    }
    else {
        colorClass = '_senior';
    }

    // Удаляем класс пустой точки:
    dots[i].classList.remove('_empty'); 
    // Добавляем новый класс, который вычислили выше:
    dots[i].classList.add(colorClass);
  }
}
```

## Возможные проблемы и замечания
В строке `if(isFemaleGender=true)` значение `isFemaleGender` **не сравнивается** со значением `true`. В данной команде значение `true` **присваивается** в аргумент `isFemaleGender`, таким образом происходит не проверка аргумента, а его изменение. Для сравнения используются операторы `==` и `===`.

```javascript
if(i < 18*52) {
    colorClass = '_young';
}
else if(i < retireAge*52) {
    colorClass = '_adult';
}
else {
    colorClass = '_senior';
}
```

## Правильное решение
```javascript
let retireAge; 

function calcRetiredAge(isFemaleGender) {
    if(isFemaleGender){
        retireAge = 60;
    } else {
        retireAge = 65;
    }
}
// calcRetiredAge — это функция вычисления пенсионного возраста, в качестве аргумента передаём пол (isFemaleGender).

function colorizeDots(weeks) {
  let dots = document.getElementsByClassName("app-table__body-dot"); 
  emptyDots(); 
  for (let i = 0; i < weeks && i < dots.length; i++) {
    let colorClass; 

    if(i < 18*52) {
        colorClass = '_young';
    }
    else if(i < retireAge*52) {
        colorClass = '_adult';
    }
    else {
        colorClass = '_senior';
    }

    // Удаляем класс пустой точки:
    dots[i].classList.remove('_empty'); 
    // Добавляем новый класс, который вычислили выше:
    dots[i].classList.add(colorClass);
  }
}
```

## Возможные проблемы и замечания
В строке `if(isFemaleGender=true)` значение `isFemaleGender` **не сравнивается** со значением `true`. В данной команде значение `true` **присваивается** в аргумент `isFemaleGender`, таким образом происходит не проверка аргумента, а его изменение. Для сравнения используются операторы `==` и `===`.

В проверках используется переменная `weeks`. В этой переменной хранится значение, количества прожитых недель. Это значение всегда одинаковое, а значит проверка на всех итерациях всегда будет выполнять одинаковую проверку, поэтому и точки закрашиваются в одинаковый цвет. Необходимо использовать итератор в  проверках, для того, что-бы все проверки были разные на всех итерациях цикла.

Присутствует сравнение `меньше (retireAge*52)` и `больше (retireAge*52)`, а на равенство нету. Поэтому в случае, когда `i равно (retireAge*52)` условие пропускается и точка не закрашивается. Получается баг. Нужно переделать условие так, что бы в случае равенства точка закрашивалась в желтый цвет. Например, можете использовать просто `else`.
![](https://sun9-42.userapi.com/c205716/v205716028/a9c25/1T-y1mORP00.jpg)