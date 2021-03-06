---
title: "Контекст оценки выражения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ab4e57f500c2dfbfe673713c784cbc93ff52a73d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-context"></a>Контекст оценки выражения
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка, **контекста вычисления выражения**:  
  
-   Представляет контекст для вычисления выражения. Как правило контекст вычисления соответствует лексическую область видимости, в которой должно вычисляться переменные, параметры, функции и методы. Например контекст оценки выражения, связанный с кадром стека предоставляет контекст для оценки локальные переменные, параметры метода и членов класса (если применимо).  
  
-   Возникает, когда остановлено в точке останова. Само выражение — это структура данных, представляющий проанализированный выражение, которое будет готов, привязки данных и вычисления в данном контексте.  
  
     Более подробно выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. При вычислении выражения создает печатных строка, содержащая имя и тип переменной или аргумента, а его значение. Эта строка отображается в окне контрольных значений или в окне «Локальные» интегрированной среды разработки.  
  
     Получает `BSTR` и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейса модуля отладки (DE) можно создать [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейса путем синтаксического анализа выражения. Получает `IDebugExpression2` интерфейс, DE можно получить значение посредством вычисления выражения синхронным или асинхронным. Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычисление выражений](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)