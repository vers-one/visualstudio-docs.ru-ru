---
title: "Подготовка к отладке: Службы Windows | Документы Microsoft"
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
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0c359e2989b1768c9c8814b11a338968bf849f59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-windows-services"></a>Подготовка к отладке: службы Windows
Служба Windows – это программа, которая выполнятся в фоновом режиме в Microsoft Windows. Примерами таких служб является служба Telnet и служба времени Windows, изменяющая часы, отображаемые на рабочем столе. Служба Windows не может быть запущена из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; ее необходимо запускать из диспетчера управления службами. Дополнительные сведения см. в разделе [создание служб Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [отладка служб Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications), и [приложения служб Windows](/dotnet/framework/windows-services/index).  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Параметры проекта для конфигураций отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Практическое руководство. Отладка метода OnStart](../debugger/how-to-debug-the-onstart-method.md)