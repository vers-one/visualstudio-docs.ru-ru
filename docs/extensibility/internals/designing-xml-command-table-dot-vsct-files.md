---
title: "Проектирование таблицы команд XML (. Файлы Vsct) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e007ffe8cf3cc893bc9575a3e7c083090b523467
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>Проектирование таблицы команд XML (. Файлы Vsct)
Команда таблицы (.vsct) XML-файл описывает макета и внешнего вида элементов команду для VSPackage. Команда элементы включают кнопки, поля со списком, меню, панелей инструментов и групп элементов команды. В этом разделе описываются таблицы командные файлы XML, как они влияют на элементы команд и меню и об их создании.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Команды, меню, группы и vsct-файл  
 vsct-файлами построена на основе команд, меню и группы команд. XML-теги в vsct-файле представляют каждый из этих элементов, а также другие связанные элементы, такие как кнопки, размещения команд и растровые изображения.  
  
 При создании нового пакета VSPackage, запустив [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] шаблона пакета шаблона приводит к возникновению ошибки vsct-файл с необходимые элементы для команды меню, окна инструментов или пользовательского редактора, в зависимости от сделанного. Vsct-файл, затем могут редактироваться в соответствии с требованиями конкретного пакета VSPackage. Как изменить vsct-файл, см. в примерах [расширение меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
 Чтобы создать новый, пустой vsct-файл, в разделе [как: создать. Vsct-файле](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). После создания добавить элементы XML, атрибуты и значения в файл для описания макета элемента команды. Подробные XML-схема, в разделе [Справочник по схеме XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Различия между файлами .ctc и .vsct  
 Пока значение за XML-теги в vsct-файле такие же, как в настоящем рекомендуется использовать формат файла .ctc, их реализации немного отличается.  
  
-   Новый  **\<extern >** тег — где ссылаются другие h-файлы для компиляции, такие как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] инструментов.  
  
-   Пока vsct-файлами поддержки **/ include** инструкции, как файлы .ctc, он также предоставляет новую \< **импорта >** элемента. Различие заключается в, **/ include** вводит в **все** сведениями, но \< **импорта >** переносит только имена.  
  
-   Хотя файлы .ctc требует файл заголовка, в которой вы определяете вашей директивы препроцессора, одно не является обязательным для vsct-файлами. Вместо этого поместите вашей директивы в таблице символов, расположенных в  **\<символ >** элементов, расположенных в нижней части vsct-файле.  
  
-   функция файлов .vsct  **\<заметки >** тег, который позволяет внедрить любые сведения, которые, например, заметки или даже изображений.  
  
-   Значения хранятся как атрибуты элемента.  
  
-   Флаги команды можно сохранять отдельно или в стеке.  Технология IntelliSense, тем не менее, не поддерживает флаги команды с накоплением. Дополнительные сведения о флагах командной см. в разделе [элемент Command флаг](../../extensibility/command-flag-element.md).  
  
-   Можно указать несколько типов, таких как раскрывающихся списках разбиение комбинировать, и т. д.  
  
-   Не проверять идентификаторы GUID.  
  
-   Каждый элемент пользовательского интерфейса имеет строка, представляющая текст, отображаемый вместе с ним.  
  
-   Родительским является необязательным. Если этот параметр опущен, используется значение «Unknown группы».  
  
-   Значок аргумент является необязательным.  
  
-   В разделе растрового изображения — то же, что .ctc файла, за исключением того, что теперь можно указать имя файла через href, будет извлечено компилятор vsct.exe во время компиляции.  
  
-   ResID--старый идентификатор ресурса точечного рисунка можно использовать и по-прежнему работает так же, как и файлы .ctc.  
  
-   HRef--новый метод, который позволяет указать имя файла для ресурса точечного рисунка. Предполагается, что используются все, поэтому можно опустить используемый раздел. Компилятор сначала выполняет поиск локальных ресурсов для файла, затем на любых net общих ресурсов и ресурсов, параметр/i.  
  
-   Соответствующие клавиши — Больше не нужно указать эмулятор. Если указать один, компилятор предполагает, что редактор и эмулятора совпадают.  
  
-   Keychord--была удалена. Новый формат — Key1, Mod1, ключ2, Mod2.  Можно указать символ, шестнадцатеричном или VK константа.  
  
 Новый компилятор, vsct.exe, компилирует файлы .ctc и .vsct. Компилятор старый ctc.exe, тем не менее, будет распознавать ни компиляции vsct-файлами.  
  
 Компилятор vsct.exe можно использовать для преобразования существующего файла cto в vsct-файл. Дополнительные сведения об этом см. в разделе [как: создать. Vsct-файла из существующего. Файл Cto](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
## <a name="the-vsct-file-elements"></a>Элементы файла .vsct  
 Команда таблица имеет следующие элементы и иерархии:  
  
 [Элемент CommandTable](../../extensibility/commandtable-element.md) — представляет все команды, группы меню и меню, связанных с пакетом VSPackage.  
  
 [Внешний элемент](../../extensibility/extern-element.md) — ссылается на любой внешний h-файлы, необходимо объединить с vsct-файле.  
  
 [Включить элемент](../../extensibility/include-element.md) — ссылается на все файлы дополнительных заголовков (h), чтобы скомпилировать вместе с файлом your.vsct. Vsct-файл может включать h-файлы, содержащие константы, которые определяют команды, группы меню и меню, интегрированной среды разработки или другом пакете VSPackage предоставляет.  
  
 [Команды элемент](../../extensibility/commands-element.md) — представляет все отдельных команд, которые могут быть выполнены. Каждая команда имеет следующие четыре дочерних элемента:  
  
 [Элемент меню](../../extensibility/menus-element.md) — представляет все меню и панелей инструментов в VSPackage. Меню — это контейнеры для группы команд.  
  
 [Группирует элемент](../../extensibility/groups-element.md) — представляет все группы в VSPackage. Группы-это наборы отдельных команд.  
  
 [Кнопки элемент](../../extensibility/buttons-element.md) — представляет все кнопки и пункты меню в VSPackage. Визуальные элементы управления, которые могут быть связаны с командами находятся кнопки.  
  
 [Растровые изображения элемента](../../extensibility/bitmaps-element.md) — представляет все точечных рисунков для всех кнопок в VSPackage. Точечные рисунки имеют рисунков, отображаемых рядом с или командных кнопок, в зависимости от контекста.  
  
 [Элемент CommandPlacements](../../extensibility/commandplacements-element.md) — указывает дополнительные папки, где следует поместить отдельных команд в меню VSPackage.  
  
 [Элемент VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , указывает ли команда отображает все время или только в определенных контекстах, например при отображении определенного диалогового окна или окна. Меню и команд, которые имеют значение для этого элемента будет отображаться только в том случае, когда активен указанного контекста. Поведение по умолчанию является отображение команды в любое время.  
  
 [Элемент привязки клавиш](../../extensibility/keybindings-element.md) — указывает все сочетания клавиш для команд. То есть один или несколько сочетаний клавиш, должны быть нажаты для выполнения команды, такие как **CTRL + S**.  
  
 [Элемент Используемыхкоманд](../../extensibility/usedcommands-element.md) — Informs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среде, что несмотря на то, что указанная команда реализуется другим кодом, при включенном текущий пакет VSPackage, предоставляет реализацию команд.  
  
 `Symbols Element`— Содержит имена символов, а также идентификаторы GUID для всех команд, в пакете.  
  
## <a name="vsct-file-design-guidelines"></a>. Рекомендации по проектированию Vsct-файла  
 Чтобы успешно разрабатывать vsct-файл, выполните следующие рекомендации.  
  
-   Команды могут размещаться только в группах, группы может быть помещен только в меню и меню может размещаться только в группы. Фактически только меню отображаются в Интегрированной среде разработки, группы и команды не.  
  
-   Подменю не допускается непосредственное присваивание меню, но необходимо назначить группе, которая в свою очередь назначается меню.  
  
-   Команды, подменю и групп могут назначаться в одну группу родительских связей или меню с помощью родительского поля их определение директивы.  
  
-   Упорядочение таблицы команд только через родительские поля в файл директив имеет существенное ограничение. Директивы, которые определяют объекты могут принимать только один родительский элемент аргумент.  
  
-   Повторное использование команды, группы или подменю требует использования новых директивы для создания нового экземпляра объекта с собственным `GUID:ID` пары.  
  
-   Каждый `GUID:ID` пара должна быть уникальной. Повторное использование команды, которая например, добавленную в меню, панели инструментов, или контекстного меню, обрабатывается <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса.  
  
-   Команды и подменю также могут быть назначены несколько групп и групп можно назначить несколько меню с помощью [Commands, элемент](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Заметки о Vsct-файла  
 Если внести изменения в vsct-файл, после и скомпилировать его и поместите его в машинном коде DLL-Библиотеке дополнения, следует запустить **/nosetupvstemplates/Setup devenv.exe**. Это заставляет VSPackage ресурсы, указанные в экспериментальном реестр, чтобы быть повторное считывание и внутренней базы данных, который описывает [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] создаются заново.  
  
 Во время разработки можно в нескольких проектах VSPackage будет создан и зарегистрирован в экспериментальном кусте реестра может привести к путанице помехи в Интегрированной среде разработки. Чтобы устранить эту проблему, можно сбросить экспериментальный куст значения по умолчанию для удаления всех зарегистрированных пакетов VSPackage и любые изменения, внесенных в интегрированную среду разработки. Чтобы сбросить экспериментальный куст, используйте средство CreateExpInstance.exe, входящий в состав Visual Studio SDK. Его можно найти в  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<версии > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Запустите инструмент с помощью командной строки **CreateExpInstance/reset**. Помните, что это средство удаляет из экспериментальный куст зарегистрированного VSPackages, обычно не устанавливается вместе с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../../extensibility/extending-menus-and-commands.md)