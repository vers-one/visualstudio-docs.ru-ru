---
title: "Projectoutputfile-элемент | Документы Microsoft"
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
helpviewer_keywords: ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5b57f00960629d65f264f22532a16202d6ae5d7a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="projectoutputfile-element"></a>Элемент ProjectOutputFile
  Представляет выходные данные отдельного проекта для включения с элементом проекта при его развертывании в SharePoint.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>Тип  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|**Идентификатора проекта**|Требуется **xs: String** атрибута.<br /><br /> Идентификатор GUID зависимого проекта, который содержит выходные данные, которые требуется включить. Это соответствует **ProjectGuid** в файле зависимого проекта.|  
|**ProjectPath**|Требуется **xs: String** атрибута.<br /><br /> Относительный путь, включая имя файла проекта зависимого проекта, который содержит выходные данные, которые требуется включить. Данный путь задается относительно корневой папке проекта SharePoint, который содержит элемент проекта SharePoint.|  
|**Целевой объект**|Необязательный **xs: String** атрибута.<br /><br /> Путь, где выходные данные зависимый проект развертывается на сервере SharePoint относительно корневой папки развертывания. Корневой папки развертывания определяется типом развертывания, заданные **тип** атрибута.<br /><br /> Дополнительные сведения см. в разделе описания **путь развертывания** и **корневого каталога развертывания** свойства SharePoint элементами проекта в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Требуется **xs: String** атрибута.<br /><br /> Тип развертывания для выходных данных зависимого проекта. Дополнительные сведения о возможных значениях см. в описании для **тип развертывания** свойства элементов проекта SharePoint в [разработке решений SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Файлы](../sharepoint/files-element.md)|Указывает файлы, включаемые в элемент проекта SharePoint при его развертывании в SharePoint.|  
  
## <a name="remarks"></a>Примечания  
 Используйте **ProjectOutputFile** элемент для включения вывода проекта при развертывании элемента проекта SharePoint. Можно указать другой проект, или же проект, который содержит элемент проекта. Дополнительные сведения см. в разделе [предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Сведения об элементе  
  
|||  
|-|-|  
|**Пространство имен**|http://schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Имя схемы**|Схема элемента проекта SharePoint|  
|**Файл проверки**|ProjectItemModelSchema.xsd|  
|**Может быть пустым.**|Нет|  
  
## <a name="see-also"></a>См. также  
 [Справочник по схеме элементов проектов SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  