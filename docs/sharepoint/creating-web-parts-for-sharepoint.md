---
title: "Создание веб-частей для SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, Веб-части"
  - "веб-части [разработка приложений SharePoint в Visual Studio], разработка"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Создание веб-частей для SharePoint
  С помощью веб\-частей можно изменять содержимое, внешний вид и поведение страниц сайта SharePoint, используя для этого браузер.  Веб\-части представляют собой серверные элементы управления, выполняемые внутри страницы веб\-части. Это составные компоненты страниц, отображаемых на сайте SharePoint.  См. раздел [Компонент: веб\-части](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 В Visual Studio предусмотрены шаблоны, которые можно использовать для создания веб\-частей и их отладки на сайте SharePoint.  
  
## Создание веб\-части в Visual Studio  
 Создайте веб\-часть, добавив элемент **Веб\-часть** в любой проект SharePoint.  Элемент **Веб\-часть** можно использовать в изолированном решении или решении фермы.  
  
 Если требуется разработать веб\-часть визуально с помощью конструктора, создайте проект **Визуальная веб\-часть** или добавьте элемент **Визуальная веб\-часть** в любой проект SharePoint.  Элемент **Визуальная веб\-часть** можно использовать только в решении фермы.  
  
### Элемент "Веб\-часть"  
 Элемент **Веб\-часть** содержит файлы, используемые для разработки веб\-части для сайтов SharePoint.  При добавлении элемента **Веб\-часть** Visual Studio создает в проекте папку и добавляет в нее несколько файлов.  В следующей таблице описан каждый файл.  
  
|Файл|Описание|  
|----------|--------------|  
|Elements.xml|Содержит сведения, используемые файлом определения компонента в проекте для развертывания веб\-части.|  
|файл с расширением .webpart|Предоставляет сведения, необходимые SharePoint для отображения веб\-части в коллекции веб\-частей.|  
|Файл исходного кода|Содержит методы, добавляющие элементы управления в веб\-часть и создающие пользовательское содержимое внутри веб\-части.|  
  
 Для получения дополнительной информации см. [Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### Элемент "Визуальная веб\-часть"  
 Визуальная веб\-часть — это веб\-часть, создаваемая в Visual Studio с использованием конструктора Visual Web Developer.  См. раздел [Карта содержимого среды веб\-разработки Visual Studio](http://msdn.microsoft.com/ru-ru/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
 Визуальная веб\-часть функционирует так же, как любая другая веб\-часть.  Чтобы добавить элементы управления, такие как кнопки и текстовые поля, к веб\-части, добавьте код в файл XML.  Однако они добавляются в визуальные веб\-части путем перетаскивания или копирования в часть Интернета из **Панель элементов** Visual Studio.  Конструктор затем выдает необходимый код в XML\-файле.  См. раздел [Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## Элементы управления SharePoint  
 Visual Studio предоставляет некоторые элементы управления для создания страницы SharePoint, например страницы приложения.  Эти элементы управления отображаются в группе **Область элементов** в разделе **Элементы управления SharePoint**.  Функция для этих элементов управления [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315) является производной от пространства имен, которое содержит серверные элементы управления ASP.NET, которые используются на сайте SharePoint и содержит страницы.  
  
|Имя элемента управления|Описание|  
|-----------------------------|--------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Вставляет меню ASP.  Дополнительные сведения см. в разделе [Обзор элементов управления меню](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Вставляет элемент **LINK** на страницу ASPX и применяет один или несколько внешних таблиц стилей, определяемых параметром **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Вставляет элемент управления DateTime на страницу ASPX.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Вставляет проверку безопасности на страницу ASPX.|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Возвращает свойство указанного списка.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Возвращает глобальное свойство текущего веб\-сайта.|  
|[RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Вставляет ссылку на RSS\-канал на страницу .aspx.|  
|[ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Предоставляет свойства и методы для регистрации ресурсы, такие как скрипты на странице, чтобы их можно было задать при обработке страницы.|  
|[Тема](http://go.microsoft.com/fwlink/?LinkId=235314)|Применяет тему к странице ASPX.|  
  
## Отладка веб\-части  
 Отладка проекта SharePoint, который содержит веб\-часть, выполняется так же, как отладка других проектов Visual Studio.  При запуске отладчика Visual Studio среда Visual Studio открывает сайт SharePoint.  
  
 Чтобы начать отладку кода, добавьте веб\-часть на страницу веб\-части в in SharePoint.  
  
 Дополнительные сведения об отладке проектов SharePoint см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Ограничения визуальной веб\-части  
 Начиная с Visual Studio можно добавить визуальные веб\-части в изолированные решения SharePoint и решения фермы.  Однако визуальные веб\-части имеют следующие ограничения.  
  
-   Визуальные веб\-части не поддерживает подстановочных параметров.  Для получения дополнительной информации см. [Подстановочные параметры](../sharepoint/replaceable-parameters.md).  
  
-   Пользовательские элементы управления или визуальные веб\-части невозможно удалить и переместить или скопировать на визуальные веб\-части.  Это действие приводит к возникновению ошибки сборки.  
  
-   Визуальные веб\-части непосредственно не поддерживают токены сервера SharePoint как $SPUrl.  Дополнительные сведения см. в разделе "Ограничения токенов в изолированных визуальных веб\-частях" в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Визуальные веб\-части в изолированном решении иногда получают ошибку "Запрос выполнения изолированного кода запрещен, поскольку основная служба изолированного кода была слишком занят, чтобы обработать запрос». Дополнительные сведения об этой ошибке см. в записи [блога команды разработчиков SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Серверная отладка JavaScript не поддерживается в Visual Studio, но клиентская отладка JavaScript поддерживается.  
  
     Хотя можно добавить в серверный файл разметки подставляемый код JavaScript, отладка для добавленных в разметку точек останова не поддерживается.  Для отладки JavaScript создайте ссылки на внешний файл JavaScript в файле разметки, а затем установите точки останова в файле JavaScript.  
  
-   Отладка подставляемого кода [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] должна выполняться в созданном файле с кодом, а не в файле разметки.  
  
-   Визуальные веб\-части не поддерживают использование директивы `<@ Assembly Src=`.  
  
-   Веб\-элементов управления SharePoint и некоторые элементы управления [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] не поддерживаются в этой среде изолированных решений SharePoint.  Если неподдерживаемые элементы управления используются в визуальной веб\-части в изолированном решении, возникает ошибка "Тип или имя пространства имен "Theme" не существует в пространстве имен "Microsoft.SharePoint.WebControls".  
  
 Дополнительные сведения об изолированных решениях см. в разделе [Различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Создание веб\-частей на основе SharePoint старого стиля  
 Шаблоны в Visual Studio позволяют создавать пользовательские веб\-части [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] для SharePoint.  Веб\-части [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] создаются поверх инфраструктуры веб\-частей [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] и представляют собой рекомендуемый тип для использования в новых проектах.  
  
 В очень редких случаях может понадобиться создать веб\-часть с использованием веб\-части на основе SharePoint старого стиля.  Для создания этих типов веб\-частей можно использовать Visual Studio, но в Visual Studio не предусмотрено шаблонов, предназначенных специально для создания этих веб\-частей.  
  
 Дополнительные сведения об уместности создания веб\-части более старого стиля SharePoint см. в разделе [Инфраструктура веб\-частей в службах Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290).  Дополнительные сведения о создании веб\-части с использованием веб\-части на основе SharePoint старого стиля см. в разделе [Walkthrough Creating a Basic SharePoint Web Part](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## Связанные разделы  
  
|Название|Описание|  
|--------------|--------------|  
|[Практическое руководство. Создание веб-части SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Демонстрируется создание веб\-частей для страниц SharePoint.|  
|[Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Демонстрируется создание веб\-частей для SharePoint с использованием визуальной рабочей области конструирования.|  
|[Практическое руководство. Создание пользовательского элемента управления для страницы приложения или веб-части SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Демонстрируется создание пользовательских элементов управления с возможностью повторного использования, которые можно размещать на страницах приложений и в веб\-частях, используемых в SharePoint.|  
|[Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Порядок разработки веб\-части для SharePoint.|  
|[Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Порядок разработки веб\-части для SharePoint путем перетаскивания элементов управления на визуальную поверхность разработки.|  
|[Пошаговое руководство. Создание веб-части Silverlight, отображающей данные OData для SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Описание порядка конструирования веб\-части для SharePoint, в которой размещается приложение Silverlight и отображаются данные из списков SharePoint.|  
|[Работа с Visual Web Developer](http://msdn.microsoft.com/ru-ru/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Порядок использования конструктора, отображаемого при открытии веб\-страницы в проекте.|  
  
  