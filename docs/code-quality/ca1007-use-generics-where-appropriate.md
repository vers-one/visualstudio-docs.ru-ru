---
title: "CA1007: Используйте универсальные уместно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d7093c437abf84bd86b520f84ffcf980491c77c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: используйте универсальные методы, если это уместно
|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Видимый извне метод содержит ссылочный параметр типа <xref:System.Object?displayProperty=fullName>и включенная сборка предназначена [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## <a name="rule-description"></a>Описание правила  
 Параметр ссылки — это параметр, при изменении с помощью `ref` (`ByRef` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ключевое слово. Тип аргумента, предоставленного для ссылочного параметра должно совпадать с типом ссылочного параметра. Использовать тип, производный от типа ссылочного параметра, тип необходимо сначала привести и присвоить переменной типа ссылочного параметра. Использование универсального метода позволяет всех типов, могут применяться ограничения, передаваемый в метод без предварительного приведения к типу для типа ссылочного параметра.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, сделайте метод универсальным и замените <xref:System.Object> параметра с помощью параметра типа.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано процедура замены общего назначения, реализованы в виде универсальных и неуниверсальных методов. Обратите внимание на то, насколько эффективно меняются местами строк с помощью метода по сравнению с неуниверсальный метод.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1005: не используйте слишком много параметров в универсальных типах](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: коллекции должны реализовывать универсальный интерфейс](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: не объявляйте статические элементы в универсальных типах](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: не следует раскрывать универсальные списки](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: не вкладывайте универсальные типы в сигнатуры членов](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: универсальные методы должны предоставлять параметр типа](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: используйте экземпляры обработчика универсальных событий](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## <a name="see-also"></a>См. также  
 [Универсальные шаблоны](/dotnet/csharp/programming-guide/generics/index)