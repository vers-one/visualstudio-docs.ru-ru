---
title: "Расширение проектов SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>Расширение проектов SharePoint
  Создание расширения проекта, если вы хотите настроить функции уровня проекта проектов SharePoint. Например можно добавить пользовательские свойства проекта или в ответ на события на уровне проекта, возникающие при разработке решения SharePoint в Visual Studio.  
  
## <a name="creating-project-extensions"></a>Создание проекта расширения  
 Чтобы расширить элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейса. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 При создании расширения проекта, также можно добавить следующие функциональные возможности для проектов SharePoint:  
  
-   Добавление пункта контекстного меню. Элемент меню появляется, когда открывается контекстное меню для узла проекта SharePoint в **обозревателе решений** , щелкнув правой кнопкой мыши узел или выбрав его и нажмите клавиши Shift + F10 ключей. Дополнительные сведения см. в разделе [как: Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Добавление пользовательского свойства. Это свойство отображается в **свойства** при выборе проекта SharePoint в **обозревателе решений**. Дополнительные сведения см. в разделе [как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Пошаговое руководство для создания, развертывания и тестирования расширения проекта в разделе [Пошаговое руководство: создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Основные сведения о связи между расширениями проекта и экземплярами проекта  
 При создании расширения проекта это расширение загружается при открытии любого проекта SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]включает несколько шаблонов проекта SharePoint, такие как определения списков, типы содержимого и приемников событий. Тем не менее есть только один тип проекта SharePoint. Типы проектов, которые отображаются в **новый проект** диалоговое окно — это только шаблоны, которые объединены один или несколько элементов проекта SharePoint. Поскольку имеется только один тип проекта SharePoint, расширения, созданные для одного проекта применяются ко всем проектам SharePoint. Например, нельзя создать расширение, которое применяется только к **тип содержимого** проекта.  
  
 Для доступа к определенным экземплярам проекта, обработку одного из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> события *projectService* параметр в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> метод. Например, чтобы определить, когда проект SharePoint добавляется в решение, обрабатывают <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> событий. Дополнительные сведения см. в разделе [как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>См. также  
 [Как: создание расширения проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Как: Добавление пункта контекстного меню в проекты SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Как: Добавление свойства в проекты SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Пошаговое руководство: Создание расширения проекта SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Определение типов элементов проектов SharePoint, пользовательские](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Расширение элементов проектов SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Расширение SharePoint упаковки и развертывания](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  