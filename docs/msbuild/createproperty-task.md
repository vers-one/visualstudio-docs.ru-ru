---
title: "Задача CreateProperty | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f1dbd799bd709347bb0c60b34a7ebb19546b6f54
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="createproperty-task"></a>Задача CreateProperty
Заполняет свойства переданными значениями. Это позволяет копировать значения из одного свойства или строки в другое свойство или строку.  
  
## <a name="attributes"></a>Атрибуты  
 В следующей таблице приводятся параметры задачи `CreateProperty` .  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Value`|Необязательный выходной параметр `String`.<br /><br /> Указывает значение для копирования в новое свойство.|  
|`ValueSetByTask`|Необязательный выходной параметр `String`.<br /><br /> Содержит то же значение, что и параметр `Value`. Используйте этот параметр только в том случае, если вы не хотите, чтобы [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] задавал выходное свойство при пропуске вложенного целевого объекта из-за актуальных выходных данных.|  
  
## <a name="remarks"></a>Примечания  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример использует задачу `CreateProperty`, чтобы создать свойство `NewFile` с помощью сочетания значений свойств `SourceFilename` и `SourceFileExtension`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <SourceFilename>Module1</SourceFilename>  
        <SourceFileExtension>vb</SourceFileExtension>  
    </PropertyGroup>  
  
    <Target Name="CreateProperties">  
  
        <CreateProperty  
            Value="$(SourceFilename).$(SourceFileExtension)">  
            <Output  
                TaskParameter="Value"  
                PropertyName="NewFile" />  
        </CreateProperty>  
  
    </Target>  
  
</Project>  
```  
  
 После запуска проекта значение свойства `NewFile` равно `Module1.vb`.  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)