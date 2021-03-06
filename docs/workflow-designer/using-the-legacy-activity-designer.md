---
title: "Использование конструктора действий прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: d8288db6ddca4041a409b435ccd730d0b15b013b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-legacy-activity-designer"></a>Использование конструктора действия для прежних версий
В данном разделе описано использование конструктора действий в средстве [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] более ранней версии. Используйте конструктор более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] или [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Конструктор действий позволяет создавать собственные пользовательские действия.  
  
## <a name="creating-a-custom-activity"></a>Создание пользовательского действия  
 Для создания пользовательского действия с помощью конструктора действий выполните следующие шаги:  
  
1.  На **проекта** меню, нажмите кнопку **добавить действие**.  
  
2.  Выберите **действия** или **действие (с разделением кода)** шаблона.  
  
    1.  Используйте **действия** шаблон для создания действия с определением действия и пользовательским кодом в одном файле кода.  
  
    2.  Используйте **действие (с разделением кода)** шаблон для создания действия с определением действия в виде разметки рабочего процесса и пользовательским кодом в отдельном файле кода.  
  
3.  Введите имя действия или оставьте имя по умолчанию и нажмите кнопку **добавить**.  
  
 Также можно создать набор пользовательских действий путем создания нового проекта типа **библиотека действий рабочих процессов**. Дополнительные сведения об этом типе проекта см. в разделе [как: Создание библиотеки действий (для прежних версий)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Настройка действия  
 Пока конструктор действия активен, для настройки свойств, перечисленных в следующей таблицы, можно использовать браузер свойств.  
  
|Свойство|Комментарии|  
|--------------|--------------|  
|**Name**|Имя действия.|  
|**Базовый класс**|Базовый класс от которого наследуется действие. Базовый класс по умолчанию — [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). В **свойства** окно, нажмите кнопку **базовый класс** многоточие **[...]**  для выбора другого базового класса в [Обзор и выбор диалоговое окно типа .NET (для прежних версий)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Описание**|Пользовательское описание действия.|  
|**Включено**|Значение **True** по умолчанию, чтобы включить проверку и выполнение действия. Значение **False** Чтобы выключить проверку и выполнение действия. Сведения о выполнении и проверке действия см. в разделе [разработка действий рабочего процесса](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Добавление дочерних действий  
 Можно перетащить дочерние действия с панели элементов на разрабатываемое действие. Далее, используя браузер свойств, можно настроить каждое дочернее действие.  
  
## <a name="see-also"></a>См. также  
 [Разработка действий рабочего процесса](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Создание пользовательских действий](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Действия рабочего процесса прежних версий](../workflow-designer/legacy-workflow-activities.md)   
 [Образцы пользовательских действий](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Как: Создание библиотеки действий (для прежних версий)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Использование конструктора рабочих процессов для прежних версий](../workflow-designer/using-the-legacy-workflow-designer.md)