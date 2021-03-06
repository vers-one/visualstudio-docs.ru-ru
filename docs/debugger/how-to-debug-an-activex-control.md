---
title: "Как: Отладка элемента управления ActiveX | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 11d29d2d8a5ebf4774f3b71ea72a1dd9bc58cbd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-an-activex-control"></a>Практическое руководство. Отладка элемента управления ActiveX
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Чтобы выполнить отладку элемента управления ActiveX, задайте контейнер (исполняемый файл) для элемента управления.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>Задание контейнера для сеанса отладки  
  
1.  Выберите проект в Обозревателе решений.  
  
2.  Из **представление** меню, выберите **страницы свойств**.  
  
3.  В **страниц свойств проекта** открытия диалогового окна, **свойства конфигурации** папки, а затем выберите **Отладка**.  
  
4.  В разделе **Отладка** категории, найдите **команда** свойство.  
  
5.  Задайте путь к контейнеру. Например, C:\Program Files\Internet Explorer\IEXPLORE.EXE.  
  
6.  Если задать обозреватель Internet Explorer в качестве контейнера и использовать возможность Active Desktop, введите `/new` в **аргументы команды** поле.  
  
7.  Нажмите кнопку **ОК**.  
  
     Если не задавать контейнер в **страниц свойств проекта** диалоговое окно, его можно задать при запуске отладки. При выборе команды запуска отладки, [исполняемый файл для сеанса диалогового Отладка](../debugger/executable-for-debugging-session-dialog-box.md) отображается. Задайте в диалоговом окне путь к контейнеру.  
  
## <a name="see-also"></a>См. также  
 [Элементы управления ActiveX](/cpp/mfc/activex-controls)   
 [Тестирование свойств и событий с использованием тестового контейнера](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Отладка в Visual Studio](../debugger/index.md)  
 [Обзор функций отладчика](../debugger/debugger-feature-tour.md)