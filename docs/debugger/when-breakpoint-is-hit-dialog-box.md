---
title: "Если точка останова задана попаданий диалоговое окно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c03e68315c8c0818d6b9cf6a102adde4ea4f8a10
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>Диалоговое окно "Попадание в точку останова"
С помощью этого диалогового окна можно произвести настройку действия, выполняемого при достижении точки останова.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Напечатать сообщение**  
 Печатает сообщение, используя синтаксис DebuggerDisplay. Дополнительные сведения см. в разделе [с помощью атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Это текстовое поле также поддерживает специальные ключевые слова (например, $ADDRESS), которые можно использовать без дополнительных параметров или заключать в фигурные скобки выражений DebuggerDisplay. Доступные ключевые слова перечислены в диалоговом окне.  
  
 **Продолжить выполнение**  
 Этот элемент управления включен только если **напечатать сообщение** выбран. При выборе указанного элемента управления точку останова можно использовать в качестве точки трассировки для отслеживания выполнения программы вместо останова при достижении точки.  
  
## <a name="see-also"></a>См. также  
 [Использование точек останова](../debugger/using-breakpoints.md)   
 [Использование атрибута DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)