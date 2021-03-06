---
title: "CA2143: Прозрачные методы не должны использовать требования безопасности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 073ce1d22662b46a19bf5cf36305df63500347a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: прозрачные методы не должны использовать требования безопасности
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Tranparent тип или метод декларативно помечается <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` запросу или вызовы методов <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> метод.  
  
## <a name="rule-description"></a>Описание правила  
 Прозрачный для системы безопасности код не должен отвечать за проверку безопасности операции и поэтому не должен требовать разрешений. Прозрачный для системы безопасности код должен использовать полные требования для принятия решений по безопасности, и критичный в плане безопасности код не должен полагаться на прозрачный код, чтобы создать полное требование. Вместо этого следует критичный в плане безопасности любой код, который выполняет проверки безопасности, такие как требования безопасности.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Как правило, чтобы устранить нарушение данного правила, пометьте метод <xref:System.Security.SecuritySafeCriticalAttribute> атрибута. Можно также удалить требование.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 Это правило срабатывает на следующий код, поскольку прозрачный метод создает требование декларативной безопасности.  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [CA2142: прозрачный код не должен быть защищен с помощью требований LinkDemand](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)