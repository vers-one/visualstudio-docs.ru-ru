---
title: "Элемент ParameterGroup | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ba8ea083a5479a71d39eefbc5de7a93696d06d8f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="parametergroup-element"></a>Элемент ParameterGroup
Содержит необязательный список параметров, которые будут присутствовать в задаче, созданной `UsingTask``TaskFactory`. Дополнительные сведения см. в статье [UsingTask Element (MSBuild)](../msbuild/usingtask-element-msbuild.md) (элемент UsingTask (MSBuild)).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  

## <a name="syntax"></a>Синтаксис  

```  
<ParameterGroup />  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  
 Отсутствует.  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Параметр](../msbuild/parameter-element.md)|Содержит сведения о конкретном параметре для задачи, созданной `UsingTask``TaskFactory`. Имя элемента — это имя параметра.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Предоставляет способ регистрации задач в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Проект может содержать любое число элементов `UsingTask`, включая ноль.|  

## <a name="example"></a>Пример  
 В следующем примере показано использование элемента `ParameterGroup`.  

```xml  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  

## <a name="see-also"></a>См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
