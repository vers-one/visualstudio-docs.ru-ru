---
title: "Оператор вычитания (-) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- - оператор"
  - "- - оператор, сведения об операторе -"
  - "арифметические операторы, вычитание"
  - "оператор отрицания"
  - "операторы, вычитание"
  - "оператор вычитания, синтаксис"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Оператор вычитания (-) (JavaScript)
Выполняет вычитание значения одного выражения из другого или производит унарное отрицание для отдельного выражения.  
  
## Синтаксис  
  
```  
  
result = number1 - number2;  
  
```  
  
## Параметры  
 *result*  
 Любая числовая переменная.  
  
 `number`  
 Произвольное числовое выражение.  
  
 `number1`  
 Произвольное числовое выражение.  
  
 `number2`  
 Произвольное числовое выражение.  
  
## Заметки  
 В синтаксисе 1 оператор **\-** является арифметическим оператором вычитания, с помощью которого вычисляется разница между двумя числами.  В синтаксисе 2 оператор **\-** используется как унарный оператор отрицания, указывающий отрицательное значение выражения.  
  
 В случае синтаксиса 2 при вычислении выражений, как и при использовании любых других унарных операторов, используются следующие правила.  
  
-   Если оператор применяется к неопределенному значению или выражению `null`, возникает ошибка времени выполнения.  
  
-   Объекты преобразуются в строки.  
  
-   Строки преобразуются в числа, если это возможно.  Если это невозможно, возникает ошибка времени выполнения.  
  
-   Логические значения интерпретируются как числа \(0 для false, 1 для true\).  
  
 Оператор применяется к результирующему числу.  В случае синтаксиса 2, если результирующее число не равно нулю, *result* равен результирующему числу с обратным знаком.  Если результирующее число равно нулю, *result* равен нулю.  
  
## Требования  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## См. также  
 [Оператор присваивания вычитания \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Приоритет операторов](../../javascript/operator-subtractprecedence-javascript.md)   
 [Сводный список операторов \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)