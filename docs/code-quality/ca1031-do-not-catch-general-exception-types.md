---
title: "CA1031: Не перехватывайте типы общих исключений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1b11db50a4e6104c09a65ebe9e7616d223ef3ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: не перехватывайте типы общих исключений
|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Общие исключения, таких как <xref:System.Exception?displayProperty=fullName> или <xref:System.SystemException?displayProperty=fullName> перехватывается в `catch` инструкции или предложения catch. Общие, такие как `catch()` используется.  
  
## <a name="rule-description"></a>Описание правила  
 Общие исключения не должны перехватываться.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, перехватить исключение более конкретного характера или повторно выдать общее исключение в последнем операторе в `catch` блока.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует. Перехват типы общих исключений можно скрыть проблемы времени выполнения от пользователя библиотеки и может сделать отладку намного сложнее.  
  
> [!NOTE]
>  Начиная с [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], общеязыковой среды выполнения (CLR) больше не предоставляет поврежденного состояния исключения, возникающие в операционной системе и управляемом коде, например нарушения прав доступа в [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]для обработки в управляемом коде. Если вы хотите компиляции приложения в [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] или более поздней версии и поддерживать обработку исключений поврежденного состояния, можно применить <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> атрибут метод, который обрабатывает исключения состояния повреждения.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, тип, нарушающий это правило и тип, реализующий правильно `catch` блока.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2200: следует повторно вызывать исключение для сохранения сведений о стеке](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)