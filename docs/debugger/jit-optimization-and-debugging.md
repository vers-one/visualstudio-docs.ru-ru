---
title: "JIT-компилятора отладка и оптимизация | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c3dcd57568bdfaac3ba0f7aff33cefca8a0ee32
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="jit-optimization-and-debugging"></a>JIT-отладка и оптимизация
При отладке управляемого приложения, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] по умолчанию подавляет оптимизацию кода just-in-time (JIT). Подавление JIT-оптимизации означает, что отлаживается не оптимизированный код. Код выполняется немного медленнее, поскольку он не оптимизирован, но отладка получается гораздо более тщательной. Отладка оптимизированного кода сложнее и рекомендуется, только если ошибки возникают в оптимизированном коде, но не могут быть воспроизведены в не оптимизированной версии.  
  
 JIT-оптимизация контролируется в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] по **Отключить JIT-оптимизацию при загрузке модуля** параметр. Этот параметр можно найти на **Общие** в разделе **Отладка** узел в **параметры** диалоговое окно.  
  
 Если снять флажок **Отключить JIT-оптимизацию при загрузке модуля** параметр, можно отлаживать оптимизированный JIT-код, но возможности отладки могут быть ограничены, поскольку оптимизированный код не соответствует исходному коду. В результате отладчика, такие как **локальные** и **видимые** гораздо меньше сведений, чем при отладке не оптимизированного кода может не отображаться в окне.  
  
 Другое важное различие касается отладки с использованием "Только мой код". При отладке с "Только мой код" отладчик рассматривает оптимизированный код как код, не написанный пользователем, который не следует отображать во время отладки. Следовательно, при отладке JIT-оптимизированного кода вам, возможно, следует отключить "Только мой код". Дополнительные сведения см. в разделе [пошаговое выполнение только мой код](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Следует помнить, что **Отключить JIT-оптимизацию при загрузке модуля** отключает оптимизацию кода при загрузке модулей. При присоединении к уже запущенному процессу, он может содержать код, который уже загружен, скомпилирован JIT и оптимизирован. **Отключить JIT-оптимизацию при загрузке модуля** не оказывает никакого влияния на такой код, хотя будет влиять на модули, которые будут загружены после подключения. Кроме того **Отключить JIT-оптимизацию при загрузке модуля** параметр не влияет на модули, созданные с помощью NGEN — например WinForms.dll.  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Навигация по коду с помощью отладчика](../debugger/navigating-through-code-with-the-debugger.md)   
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Процесс управляемого выполнения](/dotnet/standard/managed-execution-process)