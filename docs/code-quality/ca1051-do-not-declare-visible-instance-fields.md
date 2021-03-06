---
title: "CA1051: Не объявляйте видимые поля экземпляров | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
helpviewer_keywords:
- CA1051
- DoNotDeclareVisibleInstanceFields
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a6a22653abb4b7112e1778bf671f368e8ee28894
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1051-do-not-declare-visible-instance-fields"></a>CA1051: не объявляйте видимые поля экземпляров
|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Видимый извне тип содержит видимое извне экземпляра поле.  
  
## <a name="rule-description"></a>Описание правила  
 Поля главным образом следует использовать для данных реализации. Поля должны быть `private` или `internal` и должны быть представлены с помощью свойств. Это так же легко, для доступа к свойству, как это для доступа к полю, а код в методах доступа свойства можно изменить, как расширить функции типа без внесения критических изменений. Свойства, которые просто возвращают значение закрытому или внутреннему полю оптимизированы для выполнения наряду с доступом к полю; очень мало прирост производительности будет связан с использованием Внешне видимые поля над свойствами.  
  
 Видимый извне ссылается на `public`, `protected`, и `protected internal` (`Public`, `Protected`, и `Protected Friend` в Visual Basic) уровней доступности.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделать поле `private` или `internal` и предоставлять к нему с помощью свойства внешней видимости.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Внешне видимые поля не имеют все преимущества, которых нет в свойствах. Кроме того, открытые поля не может быть защищен [требования связывания](/dotnet/framework/misc/link-demands). В разделе [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано тип (`BadPublicInstanceFields`), приводит к нарушению данного правила. `GoodPublicInstanceFields`приводится правильный код.  
  
 [!code-csharp[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2112: защищенные типы не должны предоставлять поля](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## <a name="see-also"></a>См. также  
 [Требования связывания](/dotnet/framework/misc/link-demands)