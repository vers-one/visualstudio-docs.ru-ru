---
title: "Элемент When (MSBuild) | Документация Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 99da11e22b7e74feee4da4fa25b502bac563f0b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="when-element-msbuild"></a>Элемент When (MSBuild)
Указывает один из возможных блоков кода, который может выбрать элемент `Choose`.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>Синтаксис  

```  
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  

## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание:|  
|---------------|-----------------|  
|Условие|Обязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Необязательный элемент.<br /><br /> Вычисляет дочерние элементы, чтобы выбрать один раздел кода для выполнения. Элемент `Choose` может содержать любое число элементов `When`, включая ноль.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор определенных пользователем элементов [Item](../msbuild/item-element-msbuild.md). Элемент `ItemGroup` может содержать любое число элементов `When`, включая ноль.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор определенных пользователем элементов [Property](../msbuild/property-element-msbuild.md). Элемент `When` может содержать любое число элементов `PropertyGroup`, включая ноль.|  

### <a name="parent-elements"></a>Родительские элементы  

|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Вычисляет дочерние элементы, чтобы выбрать один раздел кода для выполнения.|  

## <a name="remarks"></a>Примечания  
 Если атрибут `Condition` имеет значение true, дочерние элементы `ItemGroup` и `PropertyGroup` элемента `When` выполняются, а все последующие элементы `When` пропускаются.  

 Элементы `Choose`, `When` и `Otherwise` используются совместно, чтобы обеспечить выбор одного блока кода для выполнения из множества доступных вариантов. См. дополнительные сведения об [условных конструкциях](../msbuild/msbuild-conditional-constructs.md).  

## <a name="example"></a>Пример  
 Следующий проект использует элемент `Choose`, чтобы выбрать набор значений свойств, который будет задан в элементах `When`. Если атрибуты `Condition` обоих элементов `When` оцениваются как `false`, в элементе `Otherwise` задаются значения свойств.  

```xml  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <PropertyGroup>  
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>ConsoleApplication1</RootNamespace>  
        <AssemblyName>ConsoleApplication1</AssemblyName>  
        <WarningLevel>4</WarningLevel>  
    </PropertyGroup>  
    <Choose>  
        <When Condition=" '$(Configuration)'=='debug' ">  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <DebugType>full</DebugType>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\Debug\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
            <ItemGroup>  
                <Compile Include="UnitTesting\*.cs" />  
                <Reference Include="NUnit.dll" />  
            </ItemGroup>  
        </When>  
        <When Condition=" '$(Configuration)'=='retail' ">  
            <PropertyGroup>  
                <DebugSymbols>false</DebugSymbols>  
                <Optimize>true</Optimize>  
                <OutputPath>.\bin\Release\</OutputPath>  
                <DefineConstants>TRACE</DefineConstants>  
            </PropertyGroup>  
        </When>  
        <Otherwise>  
            <PropertyGroup>  
                <DebugSymbols>true</DebugSymbols>  
                <Optimize>false</Optimize>  
                <OutputPath>.\bin\$(Configuration)\</OutputPath>  
                <DefineConstants>DEBUG;TRACE</DefineConstants>  
            </PropertyGroup>  
        </Otherwise>  
    </Choose>  
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
</Project>  
```  

## <a name="see-also"></a>См. также  
 [Условные конструкции](../msbuild/msbuild-conditional-constructs.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
