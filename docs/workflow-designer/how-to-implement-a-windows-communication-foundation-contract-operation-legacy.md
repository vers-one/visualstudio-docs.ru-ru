---
title: "Как: реализовать операцию контракта Windows Communication Foundation (для прежних версий) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 8800055878c53adce195bbf7078da410c12128da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Как реализовать операцию контракта Windows Communication Foundation (для прежних версий)
В этом разделе описывается реализация операции контракта [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] с помощью средства [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] прежних версий, ориентированного на работу с [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 После перетаскивания **ReceiveActivity** действия из области элементов в область конструктора рабочих процессов либо создается новый [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] контракта или импортировать существующий контракт и реализуются операции. Выберите или создайте контракта и операции с его помощью [выберите операцию диалоговое окно (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>Реализация операции контракта WCF  
  
1.  Дважды щелкните **ReceiveActivity** действия в конструкторе или нажмите кнопку с многоточием рядом с **ServiceOperationInfo** свойство в **свойства** области.  
  
2.  Выполните одно из следующих действий.  
  
    -   Нажмите кнопку **добавить контракт** в правом верхнем углу диалогового окна. Будет создан новый контракт [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] и операция.  
  
         - или -  
  
    -   Нажмите кнопку **импорта** в правом верхнем углу диалогового окна. [Обзор и выбор диалоговое окно типа .NET (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) открывается. Найдите сборку или проект, который содержит нужный контракт. Выберите контракт и нажмите кнопку **ОК**.  
  
     После создания или импортирования контракта к нему можно добавить новые операции. Чтобы добавить новую операцию, выберите контракт и нажмите кнопку **добавить операцию** в правом верхнем углу диалогового окна. После завершения добавления операций перейдите к шагу 3.  
  
3.  Выберите операцию, которую необходимо связать с **ReceiveActivity** действия. Управлять определением операции можно с помощью изменения имени операции, параметров, свойств и параметров разрешения.  
  
     Чтобы изменить имя, введите новое имя в **имя операции** текстовое поле.  
  
     Нажмите кнопку **параметры** для получения доступа к параметрам операции. Можно изменить имя, тип, направление параметра, а также добавить или удалить параметры из операции.  
  
     Нажмите кнопку **свойства** для получения доступа к exchange операцию защиты сообщения уровня и поддерживаемые функциональные возможности операции.  
  
     Нажмите кнопку **разрешений** вкладку, чтобы указать групп, к которым разрешено реализовывать операцию.  
  
4.  Нажмите кнопку **ОК** и **ReceiveActivity** покажет имя операции для реализуемой операции.  
  
5.  Поместите действия рабочего процесса, который планируется использовать для реализации операции в рамках **ReceiveActivity** действия.  
  
## <a name="see-also"></a>См. также  
 [Выберите диалоговое окно «операция» (для прежних версий)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Как: вызвать операцию контракта WCF (для прежних версий)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Действия с рабочими процессами для прежних версий](../workflow-designer/legacy-workflow-activities.md)