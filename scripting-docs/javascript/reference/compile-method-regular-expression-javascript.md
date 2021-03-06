---
title: "Метод Compile (Regular Expression) (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: compile
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- regular expressions, compiling
- Compile method
- compiling source code, regular expressions
ms.assetid: dc28cae3-478d-49b5-b5ea-203e5edfe195
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8de23a9e4f0e03fbf042195867ad9426e4c6bb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="compile-method-regular-expression-javascript"></a>Метод compile (Regular Expression) (JavaScript)
Компилирует регулярные выражения во внутренний формат для более быстрого выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
rgExp.compile(pattern, [flags])   
```  
  
## <a name="parameters"></a>Параметры  
 `rgExp`  
 Обязательный. Экземпляр **регулярное выражение** объекта. Можно указать имя переменной или литерал.  
  
 *шаблон*  
 Обязательный. Строковое выражение, содержащее шаблон регулярного выражения для компиляции  
  
 `flags`  
 Необязательно. Доступные флаги, которые можно совместить:  
  
-   g (глобальный поиск всех вхождений *шаблон*)  
  
-   i (не учитывать регистр);  
  
-   m (многостроковый поиск);  
  
## <a name="remarks"></a>Примечания  
 **Компиляции** метод преобразует *шаблон* во внутренний формат для более быстрого выполнения. Это позволяет более эффективно использовать регулярные выражения в циклах, например. Скомпилированное регулярное выражение ускоряет при повторном использовании того же выражения несколько раз. Не дает никаких преимуществ, однако не достигается, если регулярное выражение изменяется.  
  
## <a name="example"></a>Пример  
 Следующий пример иллюстрирует использование **компиляции** метод:  
  
```JavaScript  
function CompileDemo(){  
   var rs;  
   var s = "AaBbCcDdEeFfGgHhIiJjKkLlMmNnOoPp"  
   // Create regular expression for uppercase only.  
   var r = new RegExp("[A-Z]", "g");  
   var a1 = s.match(r)              // Find matches.  
   // Compile the regular expression for lowercase only.  
   r.compile("[a-z]", "g");  
// Find matches.  
   var a2 = s.match(r)                
   return(a1 + "\n" + a2);  
}  
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Применяется к**: [объект регулярного выражения](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>См. также  
 [Синтаксис регулярного выражения (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)