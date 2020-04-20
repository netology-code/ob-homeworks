# Домашнее задание к лекции «Общаемся с компьютером»

## Исходный код (без комментариев к заданию)
```javascript
function showingMiddleAge(isFemaleGender) {

  let middleAge; let genderName;if (isFemaleGender) {

  } else {

  }

  // Это вывод эталона в консоль:
  console.log("Эталон:", genderName, '-', middleAge); 
  // Подставляем присвоенные значения возраста и пола в элемент справа от таблицы с кружками:
  middleAgeElement.setAttribute('data-middle', middleAge); 
  genderElement.setAttribute('data-sex', genderName); 
  // Меняем значение переменной CSS, чтобы фигурная скобочка поменяла свою высоту:
  document.documentElement.style
    .setProperty('--lifespan', middleAge);
}
```

## Пояснение кода
В модуле `hw-2.js` описана  [функция](https://learn.javascript.ru/function-basics)  `showingMiddleAge` для отображения среднего возраста и пола пользователя в зависимости от положения переключателя полов. Эта функция принимает на вход флаг "женский пол" `isFemaleGender` и выставляет название пола и значение среднего возраста. Результаты выводятся в консоль, чтобы Вы могли проверить корректность работы (отладка) и используются в качестве значений на странице и для позиционирования фигурной скобки.

## Задача №1
1. Найдите строчки кода, требующие форматирования, и отформатируйте код так, чтобы его стало удобно читать.

```javascript
let middleAge;
let genderName;
if (isFemaleGender) {

} else {

}
```

## Задача №2
1. Мы уже создали две переменные:
```javascript
let middleAge; 
let genderName;
```
Ваша задача — определить, какие значения присвоить каждой из них. 
2. После комментариев:
```javascript
  // Задача 2.
  // Присвойте переменной среднего возраста значение 77.6 — средний возраст для женщин.
  // Присвойте переменной названия пола строку 'женщин'.
  // Пишите код ниже:
```
напишите присваивание переменным `middleAge` и `genderName` подходящих по смыслу значений из комментариев (77.6 и 'женщин').

3. Аналогично после коментариев:
```javascript
  // Задача 2.
  // Присвойте переменной среднего возраста значение 67.5 — средний возраст для мужчин.
  // Присвойте переменной названия пола строку 'мужчин'.
  // Пишите код ниже:
```
напишите присваивание переменным `middleAge` и `genderName` подходящих по смыслу значений из коментариев (67.5 и 'мужчин').

```javascript
let middleAge;
let genderName;
if (isFemaleGender) {
  middleAge = 77.6;
  genderName = 'женщин';
} else {
  middleAge = 67.5;
  genderName = 'мужчин';
}
```

## Задача №3
1. Создайте переменную `testGenderNameAndMiddleAge`
2. Присвойте переменной результат склейки переменных `middleAge`, `genderName`, используйте тире в качестве разделителя (для склейки используйте оператор `+` )
3. Выведите в консоль переменную `testGenderNameAndMiddleAge`

```javascript
let testGenderNameAndMiddleAge = middleAge + "-" + genderName;
console.log(testGenderNameAndMiddleAge);
```

## Правильное решение
```javascript
function showingMiddleAge(isFemaleGender) {

  let middleAge;
  let genderName;
  if (isFemaleGender) {
    middleAge = 77.6;
    genderName = 'женщин';
  } else {
    middleAge = 67.5;
    genderName = 'мужчин';
  }

  let testGenderNameAndMiddleAge = middleAge + "-" + genderName;
  console.log(testGenderNameAndMiddleAge);
  // Это вывод эталона в консоль:
  console.log("Эталон:", genderName, '-', middleAge); 
  // Подставляем присвоенные значения возраста и пола в элемент справа от таблицы с кружками:
  middleAgeElement.setAttribute('data-middle', middleAge); 
  genderElement.setAttribute('data-sex', genderName); 
  // Меняем значение переменной CSS, чтобы фигурная скобочка поменяла свою высоту:
  document.documentElement.style
    .setProperty('--lifespan', middleAge);
}
```

## Возможные проблемы и замечания
Если в первом задании у вас получился такой код:
```javascript
let middleAge;
let genderName;
if (isFemaleGender) {
  let middleAge = 77.6;
  let genderName = 'женщин';
} else {
  let middleAge = 67.5;
  let genderName = 'мужчин';
}
```

В таком случае вы объявляете переменные вне условного оператора (выделяя память под эти переменные), а так же вы **повторно** объявляете новые переменные внутри условного оператора. Получается, что создаются **новые** переменные, которые связаны с предыдущими только названием. Эти повторно объявленные переменные внутри условной конструкции будут иметь значения только внутри условной конструкции (вне блоков условой конструкции будут актуальны те переменные, которые вы объявили во вне). Если бы вы объявили **только один раз**, то внутри условной конструкции вы бы ссылались на уже объявленные переменные (а не выделяли бы отдельную память под новые такие же переменные).