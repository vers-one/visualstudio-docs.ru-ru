---
title: "Поиск и замена текста | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: "31"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72081f6c140c4634918e67098493cb37bb324848
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
С помощью элементов управления **Поиск и замена** или **Поиск и замена в файлах** можно найти и заменить текст в редакторе кода Visual Studio и некоторых текстовых окнах вывода, таких как **Результаты поиска**. Также можно искать и заменять текст в некоторых окнах конструктора, таких как конструктор XAML и конструктор Windows Forms, а также окнах инструментов.  
  
 В качестве области поиска можно задать текущий документ, текущее решение или пользовательский набор папок. Вы также можете указать набор расширений имен файлов для поиска по нескольким файлам. Синтаксис поиска можно настроить с помощью регулярных выражений .NET.  
  
 Сведения о поиске и замене регулярных выражений см. в статье [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  Поле **Найти/Команда** по-прежнему доступно как элемент управления панели инструментов, но больше не отображается по умолчанию. Поле **Найти/Команда** можно отобразить, выбрав на **стандартной** панели инструментов команду **Добавить или удалить кнопки** и щелкнув **Найти**. Дополнительные сведения см. в разделе, посвященному полю [Найти/Команда](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Элемент управления "Поиск и замена"  
 Элемент управления **Поиск и замена** отображается в правом верхнем углу окна редактора кода. Элемент управления **Поиск и замена** немедленно выделяет все вхождения заданной поисковой строки в текущем документе. Вы можете переходить от одного вхождения к другому, нажав кнопку **Найти далее** или **Найти предыдущий** на элементе управления поиска.  
  
 Перейти к параметрам замены можно, нажав кнопку рядом с текстовым полем **Найти**. Чтобы изменять по одному вхождению за раз, выберите **Заменить следующий** рядом с текстовым полем **Заменить**. Чтобы заменить все найденные совпадения, нажмите кнопку **Заменить все**.  
  
 Чтобы изменить цвет выделения совпадений, в меню **Сервис** последовательно выберите **Параметры**, затем **Среда**, а затем **Шрифты и цвета**. В списке **Показать параметры для** выберите **Текстовый редактор**, а затем в списке **Отображаемые элементы** выберите **Найти выделенный текст (расширение)**.  
  
### <a name="searching-tool-windows"></a>Поиск в окнах инструментов  
 Элемент управления **Найти** можно использовать в текстовых окнах и окнах кода, таких как окна **вывода** и **результатов поиска**, выбрав **Поиск и замена** в меню **Правка** (или нажав клавиши CTRL + F).  
  
 Версия элемента управления поиска также доступна в некоторых окнах инструментов. Например, теперь можно фильтровать список элементов управления в окне **панели элементов** путем ввода текста в поле поиска. Другие окна инструментов, для которых теперь поддерживается поиск содержимого, включают **обозреватель решений**, окно **Свойства**, **Team Explorer** и т. д.  
  
## <a name="findreplace-in-files"></a>Поиск и замена в файлах  
 Функции **Найти/Заменить в файлах** аналогичны функциям элемента управления **Поиск и замена** за исключением того, что можно определить область поиска. Вы можете выполнить поиск не только в текущем открытом файле в редакторе, но также во всех открытых документах, всем решении, текущем проекте и выбранном наборе папок. Также можно выполнять поиск по расширению имени файла. Чтобы перейти к диалоговому окну **поиска и замены в файлах**, выберите **Поиск и замена** в меню **Правка** (или нажмите клавиши CTRL + SHIFT + F).  
  
 При выборе варианта **Найти все** откроется окно **Результаты поиска** со списком найденных совпадений. При выборе результата в списке отображается связанный файл и выделяется искомый текст. Если файл не открыт для редактирования, он открывается на вкладке предварительного просмотра в правой части набора вкладок. Для поиска в списке **Результаты поиска** можно использовать элемент управления **Найти**.  
  
### <a name="creating-custom-search-folder-sets"></a>Создание настраиваемых наборов папок поиска  
 Область поиска можно определить, нажав кнопку **Выбор папок поиска** (она выглядит как **...**) рядом с полем **Поиск в**. В диалоговом окне **Выбор папок поиска** можно указать набор папок для поиска и сохранить спецификацию для дальнейшего использования. Папки на удаленном компьютере можно указать только в том случае, если его диск сопоставлен с локальным компьютером.  
  
### <a name="creating-custom-component-sets"></a>Создание настраиваемых наборов компонентов  
 В качестве области поиска можно определить наборы компонентов, нажав кнопку **Изменить настраиваемый набор компонентов** рядом с полем **Поиск в**. Можно указать установленные компоненты .NET и COM, проекты Visual Studio, включенные в решение, а также любые сборки или библиотеки типов (DLL, TLB, OLB, EXE или OCX). Для поиска ссылок выберите поле **Искать по ссылкам**.  
  
## <a name="see-also"></a>См. также  
 [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)