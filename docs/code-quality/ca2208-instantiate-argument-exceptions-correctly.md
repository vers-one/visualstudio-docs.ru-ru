---
title: "CA2208: Правильно создавайте экземпляры аргументов исключений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 78d510d966f2467123105ad777d61c99ad11e99a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: правильно создавайте экземпляры аргументов исключений
|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Возможные причины включают следующие ситуации:  
  
-   Выполняется вызов конструктора по умолчанию (без параметров) типа исключения, или является производным от <xref:System.ArgumentException>.  
  
-   Неправильный аргумент строки передается параметризованному конструктору, принадлежащему к типу исключения, или унаследованный от него <xref:System.ArgumentException>.  
  
## <a name="rule-description"></a>Описание правила  
 Вместо вызова конструктора по умолчанию, вызовите одну из перегрузок конструктора, что позволяет более понятное сообщение об исключении, должны быть предоставлены. Сообщение об исключении должен предназначаться разработчикам и четко описаны условия ошибки, а также исправить или избежать возникновения этого исключения.  
  
 Сигнатуры двух и строка конструкторы <xref:System.ArgumentException> и его производных типов не соответствуют по отношению к `message` и `paramName` параметров. Убедитесь, что эти конструкторы вызываются вместе с правильными аргументами. Сигнатуры выглядят следующим образом:  
  
 <xref:System.ArgumentException>(строка `message`)  
  
 <xref:System.ArgumentException>(строка `message`, строка `paramName`)  
  
 <xref:System.ArgumentNullException>(строка `paramName`)  
  
 <xref:System.ArgumentNullException>(строка `paramName`, строка `message`)  
  
 <xref:System.ArgumentOutOfRangeException>(строка `paramName`)  
  
 <xref:System.ArgumentOutOfRangeException>(строка `paramName`, строка `message`)  
  
 <xref:System.DuplicateWaitObjectException>(строка `parameterName`)  
  
 <xref:System.DuplicateWaitObjectException>(строка `parameterName`, строка `message`)  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите конструктор, который принимает сообщение, имя параметра или оба и убедитесь, что аргументы имеют правильный тип <xref:System.ArgumentException> вызова.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила, только в том случае, если параметризованный конструктор вызывается с правильными аргументами.  
  
## <a name="example"></a>Пример  
 В следующем примере конструктор, который создает экземпляр типа ArgumentNullException неправильно.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## <a name="example"></a>Пример  
 В следующем примере нарушение устраняется путем изменения порядка аргументов конструктора.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]