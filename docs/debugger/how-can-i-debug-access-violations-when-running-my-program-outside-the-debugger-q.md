---
title: "Как отладить нарушения доступа при запуске программы без отладчика? | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0af98932a940126c8f7288d7b5c830bb40f270fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Как отладить нарушения доступа при запуске программы без отладчика?
## <a name="problem-description"></a>Описание проблемы  
 Программа прекрасно работает в среде Visual Studio, но при автономном запуске под операционной системой Windows возникает нарушение доступа. Как это отладить?  
  
## <a name="solution"></a>Решение  
 Задать [непосредственно времени отладки](../debugger/just-in-time-debugging-in-visual-studio.md) параметр и запустите автономное выполнение программы до момента возникновения нарушения доступа. Затем в **нарушение прав доступа** диалоговое окно, следует щелкнуть **отменить** для запуска отладчика.  
  
 Кроме того, обратитесь к статье Q133174 информационной базы данных, "How to Locate Where a General Protection (GP) Fault Occurs". Статьи базы знаний можно найти на компакт-диске библиотеки MSDN или поиска [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)