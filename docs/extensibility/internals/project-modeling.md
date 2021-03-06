---
title: "Проект моделирования | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c3d87a44838ead7663ff4c156985ab1b8e98eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="project-modeling"></a>Проект моделирования
Следующим шагом в предоставлении автоматизации для реализации стандартного проекта объектов для проекта: <xref:EnvDTE.Projects> и `ProjectItems` коллекций; `Project` и <xref:EnvDTE.ProjectItem> объекты; и оставшихся объектов, уникальные для вашей реализации. Эти стандартные объекты определены в файле Dteinternal.h. В образце BscPrj предоставляется реализация стандартные объекты. Эти классы можно использовать в качестве моделей для создания собственных объектов для стандартного проекта, которые стоят side-by-side объектами проекта из других типов проектов.  
  
 Потребитель автоматизации предполагает, что он сможет вызвать <xref:EnvDTE.Solution>(«`<UniqueProjName>")` и <xref:EnvDTE.ProjectItems> (`n`) где n — порядковый номер для получения конкретного проекта в решении. Этот вызов автоматизации приводит средой для вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> на соответствующий проект иерархии, передав в качестве параметра ItemID и VSHPROPID_ExtObject как параметр VSHPROPID VSITEMID_ROOT. `IVsHierarchy::GetProperty`Возвращает `IDispatch` указатель на объект автоматизации, предоставляя ядро `Project` интерфейс, который реализован.  
  
 Ниже приведен синтаксис `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Проекты вместить вложение и использовать коллекции для создания групп элементов проекта. Иерархия выглядит следующим образом.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Вложение означает, что <xref:EnvDTE.ProjectItem> объект может быть <xref:EnvDTE.ProjectItems> коллекции, в то же время из-за `ProjectItems` коллекция может содержать вложенные объекты. Пример базового проекта не демонстрирует это вложение. Путем реализации `Project` объекта участвовать в древовидной структуре, характеризующий структура общей модели автоматизации.  
  
 Автоматизации проектов следует пути на схеме ниже.  
  
 ![Объекты проекта Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Автоматизации проектов  
  
 Если не реализовать `Project` объекта среды по-прежнему будет возвращать универсальный `Project` объект, который содержит только имя проекта.  
  
## <a name="see-also"></a>См. также  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>