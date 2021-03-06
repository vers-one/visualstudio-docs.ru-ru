---
title: "CA1809: Избегайте чрезмерного использования локальных переменных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8a21f6f7b24151bc1696c409c940cf8e017f9569
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: избегайте чрезмерного использования локальных переменных
|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Категория|Microsoft.Performance|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Член содержит более 64 локальных переменных, некоторые из которых могут быть компилятором.  
  
## <a name="rule-description"></a>Описание правила  
 Обычно для оптимизации производительности — хранить значение в регистре процессора, а не в памяти, который называется *регистре* значение. Общеязыковая среда выполнения считает, что до 64 локальных переменных в среде. Незарегистрированные переменные помещаются в стек и должны быть перемещены Зарегистрируйтесь до обработки. Чтобы разрешить вероятность того, все локальные переменные регистрации, ограничить количество локальных переменных в 64.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, выполните рефакторинг реализация, которую нужно использовать не более 64 локальных переменных.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно подавить предупреждение из этого правила, или отключить правило, если производительность не является проблемой.  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)