---
title: "Приоритет операторов (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "приоритет операторов"
  - "порядок приоритетов"
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Приоритет операторов (JavaScript)
Приоритет операторов определяет порядок выполнения операций при вычислении выражения.  Операции с более высоким приоритетом выполняются перед операциями с более низким приоритетом.  Например, умножение выполняется раньше сложения.  
  
## Операторы [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
 В следующей таблице представлен список операторов [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] в порядке убывания приоритета.  Операторы с одинаковым приоритетом выполняются в направлении слева направо.  
  
|Оператор|Описание|  
|--------------|--------------|  
|. \[ \] \( \)|Доступ к полям, индексация массивов, вызовы функций и группировка выражений|  
|\+\+ \-\- \- ~ \! delete new typeof void|Унарные операторы, тип возвращаемых данных, создание объектов, неопределенные значения|  
|\* \/ %|Умножение, деление, деление по модулю|  
|\+ \- \+|Сложение, вычитание, объединение строк|  
|\<\< \>\> \>\>\>|Сдвиг битов|  
|\< \<\= \> \>\= instanceof|Меньше, меньше или равно, больше, больше или равно, instanceof|  
|\=\= \!\= \=\=\= \!\=\=|Равенство, неравенство, строгое равенство, строгое неравенство|  
|&|Побитовое И|  
|^|Побитовое исключающее ИЛИ|  
|&#124;|Побитовое ИЛИ|  
|&&|Логическое И|  
|&#124;&#124;|Логическое ИЛИ|  
|?:|Условие|  
|\= *OP*\=|Присваивание, присваивание с операцией \(например \+\= и &\=\)|  
|,|Вычисление нескольких выражений|  
  
 Скобки служат для изменения порядка вычислений, определенного приоритетом операторов.  Это означает, что сначала вычисляется выражение в скобках, а затем полученный результат используется в остальной части выражения.  
  
 Например:  
  
```javascript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 В первом выражении используется три оператора: \=, \* и \+.  В соответствии с правилами приоритета они выполняются в следующем порядке: \*, \+, \= \(78 \* 96 \= 7488, 7488 \+ 3 \= 7491\).  
  
 Во втором выражении сначала выполняется оператор \( \), поэтому перед умножением выполняется сложение \(9 \+ 3 \= 12, 12 \* 78 \= 936\).  
  
 В следующем примере показан оператор, содержащий различные операторы, результат выполнения которых — `true`.  
  
```javascript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Операторы выполняются в следующем порядке: \( \) для группировки, \*, \+ \(в пределах группировки\), "." для функции, \( \) для функции, \/, \=\=, \=\=\= и &&.