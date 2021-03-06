---
title: "Сообщения об ошибках в конструкторе рабочих процессов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: a167848362c8979046ba4dc02c6396616ccb71ec
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="error-messages-in-workflow-designer"></a>Сообщения об ошибках в конструкторе рабочего процесса
Данный раздел описывает типы сообщений об ошибках, которые могут возникнуть при работе с [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Ситуации, в которых возникают ошибки при работе с конструктором рабочих процессов  
 Ошибки в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] возникают в следующих ситуациях.  
  
1.  В выражении имеется ошибка.  
  
2.  Не удовлетворены проверочные ограничения для действия.  
  
3.  В файле XAML имеются ошибки, которые не позволяют загрузить действие.  
  
4.  В файле XAML имеются ошибки, которые не позволяют загрузить рабочий процесс.  
  
 Недопустимые выражения и неудовлетворенные проверочные ограничения не препятствуют сборке рабочего процесса. Сборка рабочего процесса завершается успешно, но во время выполнения вызывается исключение <xref:System.Activities.InvalidWorkflowException>. При наличии ошибок в файле XAML сборка завершается с ошибкой.  
  
 Внутри [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], при загрузке рабочего процесса ошибки отображаются в **список ошибок**. Чтобы перейти к действию, являющийся источником ошибки, дважды щелкните ошибку в **список ошибок**.  
  
### <a name="expression-errors"></a>Ошибки выражений  
 Недопустимое выражение обозначается красным кружком с белым восклицательным знаком рядом с выражением. Если навести курсор мыши на этот значок, отобразится подсказка с описанием источника ошибки. Щелкните выражение в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], чтобы увидеть линию, которая подчеркивает источник ошибки. Если навести курсор мыши на подчеркнутый текст, отобразится подсказка с описанием источника ошибки.  
  
### <a name="activity-validation-errors"></a>Ошибки проверки действий  
 Если не удовлетворены проверочные ограничения для некоторого действия, в правом верхнем углу этого действия отображается красный круг с белым восклицательным знаком. Если навести курсор мыши на этот значок, отобразится подсказка с описанием источника ошибки.  
  
### <a name="xaml-load-errors"></a>Ошибки загрузки XAML  
 Если действие не удается загрузить, отображается красная рамка с текстом «действие не удалось загрузить из-за ошибок в XAML». Обычно это происходит, если не удается разрешить тип действия. Недопустимое действие можно удалить в конструкторе, выбрав красную рамку и удалив ее.  
  
### <a name="workflow-load-errors"></a>Ошибки загрузки рабочих процессов  
 При сбое загрузки рабочего процесса, текст «Конструктор рабочих процессов обнаружил проблемы с вашим документом» отображается в рабочей области конструктора, а также сведения об исключении, вызвавшей сбой рабочего процесса для загрузки. Обычно это происходит в случае, когда не удается произвести синтаксический анализ файла XAML.