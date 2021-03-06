---
title: "Типы данных (JavaScript) | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Boolean data type, supported data types
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa3a0e4cdbb25019758f89958afdf06c11f01a34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="data-types-javascript"></a>Типы данных (JavaScript)
В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] существует три основных, два составных и два специальных типа данных.  
  
## <a name="primary-data-types"></a>Основные типы данных  
 Ниже перечислены основные (примитивные) типы данных:  
  
-   Строка  
  
-   Число  
  
-   Boolean  
  
## <a name="composite-data-types"></a>Составные типы данных  
 Ниже перечислены составные (ссылочные) типы данных:  
  
-   Объект  
  
-   Массив  
  
## <a name="special-data-types"></a>Специальные типы данных  
 Ниже перечислены специальные типы данных:  
  
-   Null  
  
-   Не определено  
  
## <a name="string-data-type"></a>Тип данных String  
 Строковое значение представляет собой цепочку из нуля или более символов Юникода (букв, цифр и знаков препинания). Строковый тип данных используется для представления текста в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]. Чтобы включить строковые литералы в скрипты, заключите их в одинарные или двойные кавычки. Двойные кавычки могут содержаться в строках, заключенных в одинарные кавычки, а одинарные кавычки могут содержаться в строках, заключенных в двойные кавычки. Ниже представлены примеры строк:  
  
```JavaScript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Обратите внимание, что [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] не имеет типа для представления одного символа. Для представления одного символа в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] нужно создать строку, состоящую только из одного символа. Строка, содержащая нуль символов (""), называется пустой строкой или строкой нулевой длины.  
  
 Для представления знаков, которые невозможно ввести без преобразования, в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] предусмотрены escape-последовательности, включаемые в строки. Например, `\t` обозначает символ табуляции. См. дополнительные сведения о [специальных символах](../javascript/advanced/special-characters-javascript.md).  
  
## <a name="number-data-type"></a>Числовой тип данных  
 В [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] нет никакой разницы между целым значением и значением с плавающей запятой; число [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] может быть любым из них (на внутреннем уровне [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] представляет все числа как значения с плавающей запятой).  
  
### <a name="integer-values"></a>Целочисленные значения  
 Целочисленные значения могут быть положительными целыми числами, отрицательными целыми числами и нулем. Они могут быть представлены в десятеричной (10), шестнадцатеричной (16) и восьмеричной (8) системе счисления. Большинство чисел в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] записывается в десятичном формате.  
  
 Для обозначения шестнадцатеричных целых чисел перед ними ставится префикс "0x" (ноль и x&#124;X). Они могут содержать только цифры от 0 до 9 и буквы от A до F (прописные или строчные). Буквы от A до F используются для представления отдельных десятичных чисел от 10 до 15. То есть значение 0xF эквивалентно 15, а 0x10 — 16.  
  
 Для обозначения восьмеричных целых чисел перед ними ставится "0" (нуль). Они могут содержать только цифры от 0 до 7. Число, имеющее "0" в начале и содержащее цифры "8" и (или) "9", интерпретируется как десятичное.  
  
 Как восьмеричные, так и шестнадцатеричные числа могут быть отрицательными, однако не могут иметь дробную часть и быть записаны в экспоненциальном представлении.  
  
> [!NOTE]
>  Начиная с версии [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], [функция parseInt](../javascript/reference/parseint-function-javascript.md) не распознает строку с префиксом "0" как восьмеричную. Но если вы не используете функцию `parseInt`, строки с префиксом "0" могут по-прежнему интерпретироваться как восьмеричные.  
  
### <a name="floating-point-values"></a>Значения с плавающей запятой  
 Значения с плавающей запятой могут быть целыми числами с дробной частью. Кроме того, их можно записать в экспоненциальном представлении. В нем прописная или строчная буква "e" имеет смысл "10 в степени". [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] использует для представления чисел 8-байтовый формат с плавающей запятой, соответствующий стандарту IEEE 754. Это означает, что максимальное доступное число равно 1,79769x10<sup>308</sup>, а минимальное — 5x10<sup>-324</sup>. Число, содержащее десятичную запятую и имеющее лишь "0" перед ней, интерпретируется как десятичное с плавающей запятой.  
  
 Обратите внимание, что число, которое начинается с "0x" или "00" и содержит десятичную запятую, вызывает ошибку. Ниже приведено несколько примеров чисел [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Число|Описание|Десятичный эквивалент|  
|------------|-----------------|------------------------|  
|0,0001, 1e-4, 1,0e-4|Три эквивалентных числа с плавающей запятой.|0.0001|  
|3,45e2|Число с плавающей запятой.|345|  
|45|Значение типа integer.|45|  
|0378|Значение типа integer. Хотя это похоже на восьмеричное число (начинается с нуля), 8 не является допустимой восьмеричной цифрой, поэтому данное число интерпретируется как десятичное.|378|  
|0377|Восьмеричное целое число. Хотя кажется, что это число всего на единицу меньше предыдущего, его фактическое значение существенно отличается.|255|  
|0.0001|Число с плавающей запятой. Несмотря на то, что число начинается с нуля, оно не является восьмеричным, так как имеет десятичную запятую.|0.0001|  
|00.0001|Это ошибка. Два начальных нуля обозначают восьмеричное число, но десятичная запятая в таком числе недопустима.|Н/Д (ошибка компилятора)|  
|0Xff|Шестнадцатеричное целое число.|255|  
|0x37CF|Шестнадцатеричное целое число.|14287|  
|0x3e7|Шестнадцатеричное целое число. Обратите внимание, что "e" не считается возведением в степень.|999|  
|0x3.45e2|Это ошибка. Шестнадцатеричные числа не могут содержать дробные части.|Н/Д (ошибка компилятора)|  
  
 Кроме того, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] содержит числа с особыми значениями. Эти особые значения приведены ниже.  
  
-   NaN (не число). Используется при выполнении математической операции над недопустимыми данными, такими как строки или неопределенное значение.  
  
-   Положительная бесконечность. Используется, если положительное число слишком велико для представления в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Отрицательная бесконечность. Используется, если отрицательное число слишком велико для представления в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
-   Положительный и отрицательный нуль. [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] различает положительный и отрицательный нуль.  
  
## <a name="boolean-data-type"></a>Логический тип данных  
 Тогда как строковые и числовые типы данных могут охватывать практически неограниченное число различных значений, логический тип данных может иметь только два. Это литералы `true` и `false`. Логическое значение обозначает истинность, то есть указывает, является ли условие истинным.  
  
 Проводимые в скриптах сравнения всегда дают результат логического типа. Рассмотрим приведенную ниже строку кода [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
y = (x == 2000);  
```  
  
 Здесь значение переменной `x` сравнивается с числом 2000. Если значения равны, результатом сравнения является логическое значение **true**, которое назначается переменной `y`. Если значение `x` не равно 2000, то результатом сравнения является логическое значение `false`.  
  
 Логические значения особенно удобны в структурах управления. Приведенный ниже код объединяет в себе сравнение, создающее логическое значение с оператором, который его использует. Рассмотрим приведенный ниже пример кода [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```JavaScript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 Оператор `if/else` в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] выполняет одно действие, если логическое значение равно `true` (`z = z + 1`), и другое действие, если логическое значение равно `false` (`x = x + 1`).  
  
 Для сравнения можно использовать любое выражение. Любое выражение, вычисление которого дает 0, null, неопределенное значение или пустую строку, интерпретируется как `false`. Выражение, вычисление которого дает любое другое значение, интерпретируется как `true`. Например, можно было бы использовать следующее выражение:  
  
```JavaScript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Обратите внимание, что приведенная выше строка не проверяет, равен ли `x` сумме `y + z`, так как используется только один знак равенства (оператор присваивания). Вместо этого код присваивает значение `y + z` переменной `x`, а затем проверяет, равен ли результат всего выражения (значение `x`) нулю. Чтобы проверить, равен ли `x` сумме `y + z`, нужно использовать следующий код.  
  
```JavaScript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Дополнительные сведения о сравнениях см. в статье [Управление выполнением программы](../javascript/controlling-program-flow-javascript.md).  
  
## <a name="the-null-data-type"></a>Тип данных NULL  
 Тип данных `null` в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] имеет только одно значение: null. Ключевое слово `null` запрещено использовать в качестве имени функции или переменной.  
  
 Переменная, содержащая `null`, не содержит допустимое число, строку, логическое значение, массив или объект. Вы можете стереть содержимое переменной (не удаляя саму переменную), присвоив ей значение `null`.  
  
 Обратите внимание, что `null` в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] не совпадает с 0 (как в C и C++). Также обратите внимание, что оператор `typeof` в [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] определяет значения `null` как относящиеся к типу `Object`, а не типу `null`. Такое поведение, которое может вводить пользователей в заблуждение, служит для обеспечения обратной совместимости.  
  
## <a name="the-undefined-data-type"></a>Неопределенный тип данных  
 Значение `undefined` возвращается, когда вы используете свойство объекта, которое больше не существует, или объявленную переменную, которой не было присвоено значение.  
  
 Вы можете определить, существует ли переменная, сравнив ее с `undefined`, хотя вы можете проверить, имеет ли она тип `undefined`, сравнив тип переменной со строкой "undefined". Приведенный ниже пример показывает, как определить, что переменная `x` была объявлена:  
  
```JavaScript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 Вы также можете сравнить неопределенное значение с `null`. Это сравнение имеет значение `true`, если свойство `someObject.prop` равно `null` или если свойство `someObject.prop` не существует.  
  
```JavaScript  
someObject.prop == null;  
```  
  
 Чтобы узнать, существует ли свойство объекта, можно использовать оператор **in**:  
  
```JavaScript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## <a name="see-also"></a>См. также  
 [Объекты и массивы](../javascript/objects-and-arrays-javascript.md)   
 [Оператор typeof](../javascript/reference/typeof-operator-decrementjavascript.md)