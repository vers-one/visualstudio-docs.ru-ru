---
title: "Отладка исходного файлы общих свойств, свойства страниц диалоговое окно решения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: aa83025b15fe3773220a2b27394890318d60c850
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/04/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Страница "Исходные файлы отладки", вкладка "Общие свойства", диалоговое окно "Страницы свойств решения"
Эта страница свойств задает место, где отладчик будет осуществлять поиск исходных файлов при отладке решения.  
  
 Чтобы получить доступ к **исходные файлы отладки** страницу свойств, щелкните правой кнопкой мыши решение в **обозревателе решений** и выберите **свойства** в контекстном меню. Разверните **общие свойства** папку и нажмите кнопку **исходные файлы отладки** страницы.  
  
 **Каталоги, содержащие исходный код**  
 Список каталогов, в которых отладчик ищет исходные файлы при отладке решения. Поиск также производится внутри подкаталогов заданных каталогов.  
  
 **Не выполнять поиск следующих исходных файлов**  
 Введите имена файлов, которые отладчик не должен считывать. Если отладчик найдет один из этих файлов в одном из указанных каталогов, отладчик пропустит этот файл. Если **найти источник** появится диалоговое окно при отладке, и вы нажмете **отменить**, найден файл будет добавлен в этот список, отладчик прекратит поиск этого файла.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Параметры отладчика и подготовка](../debugger/debugger-settings-and-preparation.md)