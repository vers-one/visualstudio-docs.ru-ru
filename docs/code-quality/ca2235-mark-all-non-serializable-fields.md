---
title: "CA2235: Помечайте все несериализуемые поля | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: de8f0c035689edda0757ecffb027069aee83a65b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: помечайте все несериализуемые поля
|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.  
  
## <a name="rule-description"></a>Описание правила  
 Сериализуемый тип то, которое помечается <xref:System.SerializableAttribute?displayProperty=fullName> атрибута. При сериализации типа <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> исключения, если тип содержит поле экземпляра типа, который не может быть сериализован.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, примените <xref:System.NonSerializedAttribute?displayProperty=fullName> атрибута с полем, которое не может быть сериализован.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Только отключайте предупреждение из этого правила, если <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> объявления, позволяющий поле, чтобы сериализовать и десериализовать экземпляры типа.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, тип, который нарушает правила и тип, соответствующий этому правилу.  
  
 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2236: вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: следует правильно реализовывать методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: обеспечьте безопасность конструкторов сериализации](../code-quality/ca2120-secure-serialization-constructors.md)