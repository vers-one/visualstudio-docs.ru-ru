---
title: "CA1018: Пометьте атрибуты с AttributeUsageAttribute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2b94cb7c11c803e713609036db12c47e2027cb61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: помечайте атрибуты как AttributeUsageAttribute
|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 <xref:System.AttributeUsageAttribute?displayProperty=fullName> Атрибут не задан для настраиваемого атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 При определении настраиваемого атрибута его нужно пометить атрибутом с помощью <xref:System.AttributeUsageAttribute> для указания, где в исходном коде, в котором можно применять этот настраиваемый атрибут. Допустимое положение атрибута в коде зависит от значения атрибута и его применения. Например можно определить атрибут, который идентифицирует лица, ответственного за обслуживание и расширение каждого типа в библиотеке, а ответственность всегда назначается на уровне типа. В этом случае компиляторы должны включать атрибут для классов, интерфейсов и перечислений, но не следует включать его на методы, события или свойства. Организации политики и процедуры будет определяют, включены ли атрибут в сборках.  
  
 <xref:System.AttributeTargets?displayProperty=fullName> Перечисление определяет целевые объекты, которые можно указать для настраиваемого атрибута. Если не указан <xref:System.AttributeUsageAttribute>, пользовательский атрибут будет применяться для всех целевых объектов, в соответствии с определением `All` значение <xref:System.AttributeTargets> перечисления.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, укажите целевые объекты для атрибута с помощью <xref:System.AttributeUsageAttribute>. См. следующий пример.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Следует устранить нарушение данного правила, вместо отключения сообщения. Даже если атрибут наследует <xref:System.AttributeUsageAttribute>, чтобы упростить обслуживание кода должен присутствовать атрибут.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется двумя атрибутами. `BadCodeMaintainerAttribute`неправильно опускает <xref:System.AttributeUsageAttribute> инструкции и `GoodCodeMaintainerAttribute` правильно реализован атрибутов, описанных выше в этом разделе. Обратите внимание, что свойство `DeveloperName` предусмотренного правило проектирования [CA1019 необходимо: определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) и включен для обеспечения полноты.  
  
 [!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1019: необходимо определять методы доступа для аргументов атрибутов](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: избегайте распечатанных атрибутов](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>См. также  
 [Атрибуты](/dotnet/standard/design-guidelines/attributes)