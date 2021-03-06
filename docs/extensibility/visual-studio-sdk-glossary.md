---
title: "Глоссарий Visual Studio SDK | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa0f7eaed09df717eb0746076715f9c780464df1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk-glossary"></a>Глоссарий Visual Studio SDK
Этот словарь содержит определения терминов, используемых в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] документации.  
  
## <a name="terms"></a>Термины  
 надстройка  
 Служебное приложение, драйвера или другого программного обеспечения, добавленных основного приложения. В среде разработки Visual Studio (IDE), надстройка — это приложения на основе автоматизации, который расширяет возможности интегрированной среды разработки.  
  
 модель автоматизации  
 Модель автоматизации, известен в предыдущих версиях Visual Studio как модель расширения является программный интерфейс, который предоставляет доступ к базовым процедурам этого диска интегрированной среды разработки. Надстройки, мастера и макросы используют объекты в модель автоматизации для управления или расширить функциональные возможности интегрированной среды разработки.  
  
 контекст пользовательского интерфейса командной строки  
 Связывание GUID с видимость команды пользовательского интерфейса или элемента, например панель инструментов. Контекст пользовательского интерфейса командной строки — в отличие от выбора контекста, в том, что он не присоединен к окну.  
  
 Контекст пользовательского интерфейса командной строки можно использовать для:  
  
-   Назначьте идентификатор GUID панель инструментов, которая появляется при активации определенного окна.  
  
-   Назначьте идентификатор GUID доступности команды без необходимости загрузки или запуска пакетов VSPackage.  
  
-   Назначьте идентификатор GUID, влияют на активной привязки ключей.  
  
-   Назначьте идентификатор GUID для включения записи макросов.  
  
-   Назначьте идентификатор GUID для активации в режиме отладки или для переключения между представлением конструктора и режим выполнения в редакторе.  
  
 component  
 Часть программного обеспечения, могут быть сделаны части функциональных возможностей приложения без необходимости любые существующие сведения о реализации программы приложения. Связь между компонентом и приложения является только через интерфейсы OLE стиля.  
  
 Диспетчер компонентов  
 Службы `SOleComponentManager`, предоставляющее без пользовательского интерфейса координации компонентов служб для верхнего уровня. `SOleComponentManager` Службы реализует `IOleComponentManager` интерфейса.  
  
 Диспетчер компонентов пользовательского интерфейса  
 Службы `SOleComponentUIManager`, который предоставляет службы координации пользовательского интерфейса. `SOleComponentUIManager` Службы реализует `IOleComponentUIManager` и `IOleInPlaceComponentUIManager` интерфейсов.  
  
 контекст  
 `IVsUserContext` Объекта (COM), присоединен к компоненту среды. Этот объект содержит ключевые слова подстановки, ключевые слова справки F1 и атрибуты, относящиеся к компоненту. Кроме того контекста контейнеры пункты все контейнеры подконтекст, связанных с ними.  
  
 Поставщик контекста  
 Компонент в Интегрированной среде разработки, имеющий контейнер контекст, связанный с ним. Такие компоненты включают окно инструмента, редактор или иерархии проекта.  
  
 конструктор  
 Программный интерфейс, который позволяет пользователям управлять элементами пользовательского интерфейса (формы, кнопок и других элементов управления).  
  
 DocData  
 COM-объект, инкапсулирующий базовых данных документа в мире которого разделение документов и представлений (например, в случае текстовый редактор, это будет текстовый буфер базовый все представления текстового редактора). Если EditorFactory этот объект не указан, интегрированной среды разработки могут производить один от его имени. Ответственность за этот объект является возможность управления сохраняемости данных и управления доступом семантику для нескольких представлений за этот же `DocData`. Если `DocData` поддерживает `IOleCommandTarget` интерфейс, он будет включен в маршрутизация команд UIShell.  
  
 DocObject  
 Технология, используемая для размещения пользовательского интерфейса в фрейме, предоставленный средой размещения. В частности, этот термин относится внедрения, поддерживающий `IOleDocument` и связанных интерфейсов. Эта технология имеет много потенциальных приложений, такие как реализации COM документов, окна инструментов в Visual Basic 5.0, конструкторы ActiveX в Visual Basic 6.0 и т. д.  
  
 документ  
 Используется для обозначения к документу в целом — как `DocData` и `DocView`. Например, содержит DocumentFrame `DocView`, но он также сохраняет ссылку на `DocData` для обработки сохраняемости.  
  
 DocView  
 DocObject/Embedding или WindowPane с которой взаимодействует пользователь, для просмотра и управления базовый `DocData`. Обратите внимание, что пользователи не могут использовать разделения документов и представлений, который является частью `DocObject` интерфейса конструктора. Пользователям всего DocObject использоваться в качестве представления, а не с помощью более абстрактное (и менее документально оформленными принципами) представление о базовых данных, известных как `DocData`. `DocView`объекты всегда внедряются с объектами фрейма документа (дочерние окна MDI) интегрированной среды разработки.  
  
 DTE  
 `DTE` (Расширения средств разработки) объекта является точкой доступа верхнего уровня в модели автоматизации Visual Studio, который позволяет программно автоматизации и расширения интегрированной среды разработки.  
  
 Окно динамической справки  
 Окно инструментов, которое реализуется в интегрированной среде разработки и отображает список ключевых слов для поиска или разделы справки F1.  
  
 редактор  
 Код (код CLSID класса), который реализует `DocView`. Он также реализует `DocData` , если поддерживается разделение данных и представления.  
  
 расширение  
 Функция, которая изменяет, настраивает или добавляет интегрированной среды разработки. Можно создавать расширения, с помощью модели автоматизации или пакеты VSPackage.  
  
 внешний редактор  
 Редактор, который не относится к Интегрированной среде разработки, таких как Microsoft Word. Он был зарегистрирован через собственные механизмы и может использоваться за пределами интегрированной среды разработки. Если этот редактор может быть внедрен, он отображается в окне в Интегрированной среде разработки. Если он не может быть внедрен, создается отдельное окно верхнего уровня.  
  
 иерархия  
 Дерево узлов, каждый узел, связанный с набором свойств.  
  
 независимый компонент верхнего уровня  
 Компонент, который использует немодальное окно верхнего уровня можно эффективно работать как окно автономного приложения, но реализуется как объект в процессе. Таким образом это независимый компонент верхнего уровня необходимо координировать модальности и служб цикла сообщений с помощью интегрированной среды разработки. В процессе объекты не имеют своих собственных цикл обработки сообщений.  
  
 Поставщик данных  
 Поставщика данных — это модуль, можно найти ключевые слова и возвращают список разделов, в виде `IVsUserContextItem` объектов. Чтобы предоставить элементы ключевое слово F1 и поиска для поставщика данных, зарегистрировать скомпилированном файле справки (. HxS) в системе. Разделы справки в эти файлы используются для предоставления список разделов справки отображаются в окне «Динамическая справка» и показано, является ли пользователь нажимает клавишу F1.  
  
 компонент на месте  
 Объект VSPackage, реализующий интерфейс `IOleInPlaceComponent` интерфейс для управления окна, визуально содержащихся в окне документа, принадлежащих интегрированной среды разработки. Компоненты на месте не участвуют в стандартных OLE-слияние меню; Вместо этого они интегрируют свои элементы пользовательского интерфейса в Интегрированной среде разработки.  
  
 Существует два типа компонентов на месте: аппаратный на месте компонентов и элементов управления в компонент.  
  
 Компоненты на месте жестко имеют меню, панелей инструментов и команд, которые тесно интегрируются в пользовательском интерфейсе интегрированной среды разработки, отображаются в виде, если они были созданы непосредственно в Интегрированной среде разработки.  
  
 Элементы управления компонента имеет свои собственные элементы пользовательского интерфейса, интегрированы в Интегрированной среде разработки; Вместо этого они используют меню, команд и панелей инструментов интегрированной среды разработки. Например полужирный команда может использоваться для bold отдельного слова в элемент управления форматированным текстом, внедренных в форме. Элементы управления компонента можно запросить отображение элементов пользовательского интерфейса динамически установленных зависящие от компонента.  
  
 Служба языка  
 Набор объектов, которая позволяет разработчикам VSPackage реализовать функции редакторы кода языка компьютера, такие как текст, пометки и выделения цветом.  
  
 Проект прочих файлов  
 Проект, который используется для хранения открытых файлов, не входящие в любой проект. Список элементов в этом проекте не сохраняется.  
  
 проект  
 Проекты состоят из объектов иерархии или COM-объекты, реализующие `IVsHierarchy` интерфейса.  
  
 для конкретного проекта конструкторе или редакторе  
 Конструктор, который не может использоваться независимо от типа проекта. Все конструкторы для конкретного проекта необходимо ввести сведения об их фабрики редактора в реестре. IDE затем можно создать экземпляр конструктора при открытии файлов определенных типов в конкретном проекте.  
  
 Тип проекта окна  
 Окно, которое постоянно отслеживает иерархии текущего активного проекта и элемента из контекста глобального выделения. Используйте тип проекта windows `SVsTrackSelectionEx` предупредите IDE, изменения и отображения отзывы пользователю службы. Обозреватель решений — пример окна типа проекта.  
  
 Окно \"Свойства\"  
 Обозреватель свойств ранее.  
  
 ссылки проектов  
 Проект, не требуются файлы для проекта, чтобы быть в том же каталоге. Вместо этого ссылки на файлы из других каталогов несвязанных хранятся и обслуживается сам проект.  
  
 запуска таблицы документов  
 Внутренняя структура, по которому интегрированной среды разработки поддерживает список всех открытых документов. Этот список включает все открытые документы в памяти независимо от того документы момент редактируется. Документ является любой элемент, который сохраняется, включая хранимые процедуры, открывается в редакторе, файлы в проекте или основной файл проекта (например, файл *.vcproj).  
  
 выделенный фрагмент  
 Данные, входит в состав детализации из каждого окна Интегрированной среды разработки и используется для отслеживания active выбранных элементов. Выделенный фрагмент состоит из:  
  
-   Указатель на `IVsHierarchy` интерфейс иерархии проекта  
  
-   Идентификатор элемента элемента проекта.  
  
-   Указатель на `ISelectionContainer` интерфейса, предоставляя доступ к свойствам для активных объектов.  
  
-   Массив значений элементов.  
  
 служба  
 Контракт для набора COM-интерфейсы, которые находятся в одном объекте COM. При создании службы, который определяется идентификатором GUID, можно определить набор COM-интерфейсов, который выполняет службы. COM-объектами с помощью служб взаимодействовать друг с другом.  
  
 Решение  
 Группа связанных проектов, с которыми работает пользователь.  
  
 стандартный конструктор  
 Конструктор, который может использоваться независимо от типа проекта. Все стандартные конструкторы необходимо ввести сведения об их фабрики редактора в реестре. IDE затем можно создать экземпляр конструктора при открытии файлов с определенным расширением. Данные необходимо сохранить в файл.  
  
 стандартного редактора  
 Редактор, который может использоваться независимо от любого конкретного типа проекта. Такие редакторов имеется EditorFactories зарегистрировано в реестре. Благодаря интегрированной среды разработки найти и запустить редактор.  
  
 стандартного редактора ОС  
 Внедрение, который не является Visual Studio определенных. Он зарегистрирован с помощью хорошо известных ключей Win32 (например, в обозревателе Win32 может вызвать). Если такие редактор может быть внедрен, редактор будет по-прежнему отображаться в его место в Интегрированной среде разработки. В противном случае для такой редакторы создается отдельное окно верхнего уровня.  
  
 подконтекст контейнера  
 `IVsUserContext` Контейнер контекст связан объект. Этот объект содержит ключевые слова подстановки, ключевые слова справки F1 и атрибуты для выбора в компоненте интегрированной среды разработки. Подконтекст примеры команды в окно инструментов или ключевое слово в редакторе.  
  
 Список задач  
 Окно инструментов, которое реализуется в интегрированной среде разработки и отображается список активных задач.  
  
 Буфер текста  
 Общее имя для объекта `VSTextBuffer`.  
  
 Просмотр текста  
 Общее имя для объекта `VSTextView`.  
  
 компонент верхнего уровня средства  
 Компонент, который работает как немодальное всплывающего окна, тесно согласование с помощью пользовательского интерфейса интегрированной среды разработки. Как независимые компоненты верхнего уровня верхнего уровня компоненты средства также необходимо координировать модальности и служб цикла сообщений с помощью интегрированной среды разработки.  
  
 компонент верхнего уровня  
 Объект VSPackage, который управляет немодального окна верхнего уровня вместо клиентской области окна интегрированной среды разработки. Верхнего уровня в компонентах `IOleComponent` интерфейс, чтобы воспользоваться преимуществами служб цикл сообщений, таких как доступ к времени простоя.  
  
 Активного пользовательского интерфейса  
 Объект VSPackage, который является видимым и в данный момент имеет фокус.  
  
 Иерархии пользовательского интерфейса  
 COM-объект, реализующий `IVsUIHierarchy` интерфейс, чтобы отобразить иерархии. Окно иерархии пользовательского интерфейса реализует `ISelectionContainer` интерфейс для обновления окна свойств; других типов проектов windows можно использовать эту реализацию, при необходимости.  
  
 VSCT  
 Таблицы команд Visual Studio. Vsct-файл содержит сведения о размещении и поведение меню, панелей инструментов и команд в формате XML.  
  
 VSPackage  
 Устанавливаемые часть программного обеспечения, который расширяет возможности интегрированной среды разработки Visual Studio, задавая один или несколько из следующих: пользовательский интерфейс, служб, типы проектов или редактора или конструктора. VSPackage состоит из COM-объект, реализующий `IVsPackage` интерфейс и один или несколько других COM-объекты, реализующие другие интерфейсы для поддержки выбора и другие функции. Кроме того пакет VSPackage имеет требования конкретной регистрации.