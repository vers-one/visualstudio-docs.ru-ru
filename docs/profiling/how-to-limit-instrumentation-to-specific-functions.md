---
title: "Практическое руководство. Ограничение инструментирования указанными функциями | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 69cc476dc43562e5226ebd6564dfb2733f1d57ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Практическое руководство. Ограничение инструментирования указанными функциями
Можно ограничить инструментирование и сбор данных одной или несколькими функциями, задав параметры на странице **Дополнительно** **сеанса анализа производительности** или страниц свойств целевого двоичного файла.  
  
-   Если вы указываете функции на странице свойств сеанса производительности, инструментирование будет выполняться только для этих функций во всех инструментированных двоичных файлах сеанса.  
  
-   Если функции указываются на странице свойств целевого двоичного файла, инструментирование будет выполняться только для тех функций, которые содержатся в этом конкретном двоичном файле. Функции в других двоичных файлах сеанса производительности будут инструментироваться обычным образом.  
  
 Ограничение сбора данных таким образом поддерживается, только если выбран метод профилирования "Инструментирование".  
  
> [!NOTE]
>  Вы можете также использовать страницу **Дополнительно** страниц свойств **сеанса анализа производительности**, чтобы задать другие параметры, доступные для программы командной строки средств профилирования [VSInstr](../profiling/vsinstr.md).  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Ограничение инструментирования указанными функциями в сеансе производительности  
  
1.  В **обозревателе производительности** щелкните правой кнопкой мыши имя сеанса и выберите пункт **Свойства**.  
  
     Откроется диалоговое окно **Страницы свойств**.  
  
2.  В диалоговом окне **Страницы свойств** щелкните **Дополнительно**.  
  
3.  В текстовом поле **Дополнительные параметры инструментирования** используйте следующий синтаксис для ввода имени функции, которую вы хотите инструментировать:  
  
     **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
     `FuncSpec` — пространство имен и имя функции. Этот параметр имеет следующий формат: `Namespace`**::**`FunctionName`. Для разделения нескольких функций используйте точку с запятой. В качестве подстановочного знака для одного или нескольких символов можно использовать звездочку (\*). Например, **/include:MyNS::\*** указывает все функции в пространстве имен MyNS.  
  
    > [!NOTE]
    >  Чтобы получить список функций в двоичном файле, откройте окно командной строки в каталоге установки средств профилирования (как правило, каталог \Team Tools\Performance Tools под каталогом установки [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]), а затем введите команду **vsinstr /DumpFuncs**.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Ограничение инструментирования указанными функциями в двоичном файле  
  
1.  В **обозревателе производительности** найдите имя двоичного файла в узле **Цели** сеанса анализа производительности.  
  
2.  Щелкните правой кнопкой мыши двоичный файл и выберите пункт **Свойства**.  
  
     Откроется диалоговое окно **Страницы свойств**.  
  
3.  В диалоговом окне **Страницы свойств** щелкните **Дополнительно**.  
  
4.  В текстовом поле **Дополнительные параметры инструментирования** используйте следующий синтаксис для ввода имени функции, которую вы хотите инструментировать:  
  
     **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
     `FuncSpec` — пространство имен и имя функции. Этот параметр имеет следующий формат: `Namespace`**::**`FunctionName`. Для разделения нескольких функций используйте точку с запятой. В качестве подстановочного знака для одного или нескольких символов можно использовать звездочку (\*). Например, **/include:MyNS::\*** указывает все функции в пространстве имен MyNS.  
  
    > [!NOTE]
    >  Чтобы получить список функций в двоичном файле, откройте окно командной строки в каталоге установки средств профилирования (как правило, каталог \Team Tools\Performance Tools под каталогом установки [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]), а затем введите команду **vsinstr /DumpFuncs**.  
  
## <a name="see-also"></a>См. также  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Практическое руководство. Ограничение инструментирования указанными библиотеками DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Практическое руководство. Указание дополнительных параметров инструментирования](../profiling/how-to-specify-additional-instrumentation-options.md)