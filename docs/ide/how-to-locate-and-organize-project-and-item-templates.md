---
title: "Упорядочение шаблонов в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c58bda5570be9cdb7fba7a8f90a282df7b7167a2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Практическое руководство. Размещение и упорядочение шаблонов проектов и элементов

Чтобы шаблоны отображались в диалоговых окнах **Новый проект** и **Добавление нового элемента**, файлы шаблонов следует помещать в расположение, которое Visual Studio распознает. Можно также создать пользовательские подкатегории в расположении с пользовательскими шаблонами. Категории будут отображаться в диалоговых окнах **Новый проект** и **Добавление нового элемента**.

## <a name="locate-templates"></a>Локальные шаблоны

Установленные шаблоны и пользовательские шаблоны хранятся в двух различных местах.

### <a name="user-templates"></a>Шаблоны пользователя

Если добавить сжатый файл (ZIP-файл), содержащий VSTEMPLATE-файл, в каталог с пользовательскими шаблонами, шаблон будет отображаться в диалоговом окне **Новый проект** или **Добавление нового элемента**. По умолчанию пользовательские шаблоны находятся в следующих расположениях:

- %USERPROFILE%\Documents\Visual Studio \<версия\>\Templates\ProjectTemplates

- %USERPROFILE%\Documents\Visual Studio \<версия\>\Templates\ItemTemplates

Например, следующий каталог содержит шаблоны проектов пользователя на C#:

   C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\

> [!TIP]
> Расположение пользовательских шаблонов можно задать, последовательно выбрав **Сервис** > **Параметры** > **Проекты и решения**  >   **Расположения**.

### <a name="installed-templates"></a>Установленные шаблоны

По умолчанию шаблоны, установленные с Visual Studio, находятся в следующих расположениях:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Язык программирования*\\*ИД языка*

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Язык программирования*\\*ИД языка*

Например, следующий каталог содержит шаблоны элементов Visual Basic для английского языка (LCID 1033):

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

## <a name="organize-templates"></a>Упорядочивание шаблонов

Категории в диалоговых окнах **Новый проект** и **Добавление нового элемента** отражают структуры каталогов, которые существуют в расположениях установленных и пользовательских шаблонов. Пользовательские шаблоны можно упорядочить по собственным категориям путем добавления новых папок в каталог с пользовательскими шаблонами. Диалоговые окна **Новый проект** и **Добавление нового элемента** отражают все изменения, вносимые в категории шаблонов.

> [!NOTE]
> Вы не можете создать новую категорию на уровне языка программирования. Новые категории можно создавать только в рамках каждого отдельного языка.

### <a name="to-create-new-user-project-template-categories"></a>Создание категорий пользовательских шаблонов проектов

1. Создайте папку в папке языка программирования, находящейся в каталоге пользовательских шаблонов проектов. Например, чтобы создать категорию **HelloWorld** для шаблонов проектов C#, необходимо создать следующий каталог:

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld\

1. Поместите все шаблоны для этой категории в новую папку.

1. В меню **Файл** последовательно выберите пункты **Создать** > **Проект**.

   Категория **HelloWorld** появится в диалоговом окне **Новый проект** в разделе **Установленные** > **Visual C#**.

### <a name="to-create-new-user-item-template-categories"></a>Создание категорий пользовательских шаблонов элементов

1. Создайте папку в папке языка программирования, находящейся в каталоге пользовательских шаблонов элементов. Например, чтобы создать категорию **HelloWorld** для шаблонов элементов C#, необходимо создать следующий каталог:

    \%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld\

1. Поместите все шаблоны для этой категории в новую папку.

1. Создайте новый проект или откройте уже имеющийся. Затем в меню **Проект** выберите пункт **Добавить новый элемент**.

   Категория **HelloWorld** появится в диалоговом окне **Добавление нового элемента** в разделе **Установленные** > **Элементы Visual C#**.

### <a name="display-templates-in-parent-categories"></a>Отображение шаблонов в родительских категориях

Можно включить шаблоны в подкатегориях, чтобы они отображались в их родительских категориях, с помощью элемента `NumberOfParentCategoriesToRollUp` в VSTEMPLATE-файле. Эти действия идентичны как для шаблонов проектов, так и для шаблонов элементов.

#### <a name="to-display-templates-in-parent-categories"></a>Отображение шаблонов в родительских категориях

1. Найдите ZIP-файл, содержащий шаблон.

1. Извлеките ZIP-файл.

1. Откройте VSTEMPLATE-файл в Visual Studio.

1. В элементе `TemplateData` добавьте элемент `NumberOfParentCategoriesToRollUp`. Например, следующий код делает шаблон видимым в родительской категории, но не на более высоких уровнях.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Сохраните VSTEMPLATE-файл и закройте его.

1. Выберите файлы в шаблоне, щелкните выделение правой кнопкой мыши и выберите пункты **Отправить** > **Сжатая ZIP-папка**.

   Файлы сжимаются в ZIP-файл.

1. Удалите извлеченные файлы шаблона и ZIP-файл старого шаблона.

1. Поместите новый ZIP-файл в каталог, где находился удаленный ZIP-файл.

## <a name="see-also"></a>См. также

[Настройка шаблонов](../ide/customizing-project-and-item-templates.md)  
[Справочник по схемам шаблонов Visual Studio (расширяемость)](../extensibility/visual-studio-template-schema-reference.md)  
[Элемент NumberOfParentCategoriesToRollUp (шаблоны Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Практическое руководство. Создание шаблонов проектов](../ide/how-to-create-project-templates.md)  
[Практическое руководство. Создание шаблонов элементов](../ide/how-to-create-item-templates.md)
