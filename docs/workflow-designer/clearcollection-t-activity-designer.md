---
title: "ClearCollection&lt;T&gt; конструктора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 54cac37194a3b96d464b886c14bfbbbde4a1f861
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt; конструктора действий
**ClearCollection\<T >** конструктора действий используется для создания и настройки <xref:System.Activities.Statements.ClearCollection%601> действия.  
  
## <a name="the-clearcollectiont-activity"></a>ClearCollection < T\> действия  
 Действие <xref:System.Activities.Statements.ClearCollection%601> очищает указанную коллекцию, удаляя из нее все элементы.  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>С помощью ClearCollection\<T > конструктора действий  
 **ClearCollection\<T >** конструктора действий можно найти в **коллекции** категории **элементов**, который нажав  **Панель элементов** вкладке [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)  
  
 **ClearCollection\<T >** конструктора можно перетащить из **элементов** в [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] поверхности везде, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence>. При этом создается <xref:System.Activities.Statements.ClearCollection%601> действия по умолчанию <xref:System.Activities.Activity.DisplayName%2A> из ClearCollection < Int32\>. (По умолчанию *TypeArgument* — **Int32**. Изменяется в таблице свойств.) <xref:System.Activities.Activity.DisplayName%2A> Значение можно изменить в заголовке **ClearCollection < T\>**  конструктора или в **DisplayName** поле сетки свойств. Другие свойства следует изменять в таблице свойств.  
  
### <a name="the-clearcollectiont-properties"></a>ClearCollection < T\> свойства  
 В следующей таблице показаны свойства <xref:System.Activities.Statements.ClearCollection%601> и описано их использование в конструкторе.  
  
|Имя свойства|Обязательно|Использование|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает необязательное понятное имя действия <xref:System.Activities.Statements.ClearCollection%601>. Значение по умолчанию — ClearCollection < Int32\>. Несмотря на то, что значение <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же лучше использовать.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Задает коллекцию для очистки от элементов. Эта коллекция имеет тип **ICollection\<TypeArgument >.** Чтобы указать коллекцию, введите выражение Visual Basic в таблице свойств.|  
|*TypeArgument*|Да|Задает тип T для элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию это *TypeArgument* установлен тип **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|  
  
## <a name="see-also"></a>См. также  
 [Коллекции](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)