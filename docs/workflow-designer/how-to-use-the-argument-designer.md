---
title: "Как: использовать конструктор аргументов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: "16"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: aa1cdd0dd563a5f87d4e32f779985afd63319032
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-argument-designer"></a>Как использовать конструктор аргументов
По сравнению с предыдущими версиями [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], конструктор аргументов упрощает передачу данных в действие и из действия. Конструктор нажав **аргументы** кнопки в нижнем левом углу визуальной разработки. Конструктор содержит список аргументов, которые появляются в табличной форме и могут быть отсортированы по каждому заголовку столбца, за исключением **значение по умолчанию** столбца. Каждый аргумент содержит имя, направление передачи свойства (IN, OUT или IN/OUT), тип и значение выражения по умолчанию (если такое существует). Имя и значение выражения по умолчанию представляют собой изменяемые текстовые поля, а тип и направление - раскрывающееся меню. [! ВКЛЮЧИТЬ[crabout](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).  
  
### <a name="to-create-a-new-argument"></a>Создание нового аргумента  
  
1.  Откройте решение рабочего процесса или действия в [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
2.  Откройте конструктор аргументов, нажав кнопку **аргументы** кнопки в нижнем левом углу визуальной разработки. Появится конструктор аргументов.  
  
3.  Щелкните пустую строку, отмеченную как **создать аргумент**. Это будет добавлена новая строка с нового аргумента, используя следующие значения по умолчанию: argumentx для **имя** где x — целое число с начальным значением 1, которое автоматически увеличивается на единицу для создания имен уникальный аргумент **в**  для **направление**, и **строка** для **тип аргумента**. Значение не добавляется для **значение по умолчанию**. В процессе разработки рабочего процесса эти значения можно изменить в любое время.  
  
    > [!NOTE]
    >  Для удаления аргумента выберите его щелчком и нажмите клавишу **удалить** ключа.  
  
## <a name="see-also"></a>См. также  
 [В конструкторе рабочих процессов](../workflow-designer/using-the-workflow-designer.md)   
 [Переменные и аргументы](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)