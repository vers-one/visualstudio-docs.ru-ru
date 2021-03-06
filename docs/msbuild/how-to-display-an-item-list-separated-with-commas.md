---
title: "Практическое руководство. Отображение списка элементов, разделенных запятыми | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 57701bd540aeac097ee1efb4c2f7d881ffb4f00a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Практическое руководство. Отображение списка элементов, разделенных запятыми
При работе со списками элементов в [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]) иногда бывает полезно отобразить содержимое этих списков в удобном для чтения виде. Либо у вас может быть задача, принимающая список элементов, разделенных специальной строкой. В обоих случаях вы можете указать строку разделителя для списка элементов.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Разделение элементов в списке запятыми  
 По умолчанию [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] разделяет элементы в списке точками с запятой. Например, рассмотрим элемент `Message` со следующим значением:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Когда список элементов `@(TXTFile)` содержит элементы App1.txt, App2.txt и App3.txt, сообщение имеет вид:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Если вы хотите изменить поведение по умолчанию, можете задать свой разделитель. Для этого используется следующий синтаксис:  
  
 `@(ItemListName, '<separator>')`  
  
 Разделитель может быть отдельным знаком или строкой и должен быть заключен в одиночные кавычки.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Вставка запятой и пробела между элементами  
  
-   Используйте нотацию элемента, аналогичную следующей:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Пример  
 В этом примере задача [Exec](../msbuild/exec-task.md) запускает средство findstr для поиска указанных текстовых строк в файле Phrases.txt. В команде findstr искомые литеральные строки обозначены параметром **/c:**, поэтому между элементами в списке `@(Phrase)` вставляется разделитель элементов `/c:`.  
  
 Для этого примера эквивалентная команда в командной строке имеет вид:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```xml  
<Project DefaultTargets = "Find"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <Phrase Include="hello"/>  
        <Phrase Include="world"/>  
        <Phrase Include="msbuild"/>  
    </ItemGroup>  
  
    <Target Name = "Find">  
        <!-- Find some strings in a file -->  
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Элементы](../msbuild/msbuild-items.md)