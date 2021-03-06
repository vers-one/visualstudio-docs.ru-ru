---
title: "Как: Создание библиотеки рабочего процесса конечного автомата (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 73fe219a3047758f66dbff47e59031adb1de9258
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Как создать библиотеку рабочих процессов конечного автомата (для прежних версий)
Выполните следующие шаги для создания проекта библиотеки рабочего процесса конечного автомата с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, предоставленного средой [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-state-machine-workflow-library-project"></a>Создание проекта библиотеки рабочего процесса конечного автомата.  
  
1.  Запустите Visual Studio.  
  
2.  На **файл** последовательно выберите пункты **New**, а затем выберите **проекта**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
3.  Выберите либо **.NET Framework 3.0** параметр или **.NET Framework 3.5** вариант в раскрывающемся списке в верхней части **новый проект** окно, чтобы открыть конструктор прежних версий.  
  
    > [!NOTE]
    >  Параметр по умолчанию в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] — **.NET Framework 4**. Он предназначен для создания приложений [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)], работающих на платформе [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)], и не использует конструктор прежних версий.  
  
4.  В **типы проектов** области, выберите Visual C# или Visual Basic (в разделе **другие языки**), а затем выберите **рабочего процесса**.  
  
5.  В **шаблоны** выберите **библиотеки рабочего процесса автомата**.  
  
6.  В **имя** введите описательное имя проекта облегчить его определение.  
  
7.  В **расположение** введите каталог, в котором требуется сохранить проект, или **Обзор** для перехода к нему.  
  
     Если требуется создать для проекта каталог решения, выберите **создать каталог для решения** флажок и введите имя в **имя решения** поле.  
  
8.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Создание проектов рабочих процессов прежних версий](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Рабочие процессы конечного автомата](/dotnet/framework/windows-workflow-foundation/state-machine-workflows)