---
title: "Отладка проектов Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "проекты Excel [разработка решений Office в Visual Studio], отладка"
  - "проекты Word [разработка решений Office в Visual Studio], отладка"
  - "Outlook [разработка решений Office в Visual Studio], отладка"
  - "отладка [разработка решений Office в Visual Studio], проекты Outlook"
  - "проекты Office [разработка решений Office в Visual Studio], отладка"
  - "Outlook [разработка решений Office в Visual Studio], проекты"
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Отладка проектов Office
  Для отладки проектов Office можно использовать такие же инструменты Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], как и для других проектов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Функциональные возможности отладчика [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], такие как возможность вставлять точки останова и просматривать переменные в окне **Локальные**, доступны и при отладке проектов Office. Дополнительные сведения о средствах отладки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] см. в разделе [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
> [!TIP]  
>  Чтобы упростить процесс отладки, перед выполнением сборки и отладки закройте все открытые экземпляры приложения Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Запуск и остановка отладчика  
 Отладку проекта Office можно запустить точно так же, как и отладку любых других проектов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], например, нажав клавишу F5. Если вы запускаете отладку для проекта надстройки VSTO, создается процесс для целевого приложения Office и загружается надстройка VSTO.  
  
 Если отладка запускается для проекта уровня документа, документ или книга открывается в новом процессе Word или Excel.  
  
 Если отладчик останавливается, он обрывает процесс приложения или отсоединяется \(если отладчик настроен на отсоединение\). Все остальные документы, открытые в прерываемом процессе приложения Office, также закрываются без предупреждения, а все несохраненные изменения теряются. Это относится ко всем документам или книгам, открытым во время работы отладчика.  
  
 Как правило, лучше отсоединить отладчик от процесса перед его остановкой и выйти из приложения Office обычным способом. Предварительное отсоединение от процесса рекомендуется также в том случае, если вы хотите продолжить работу с открытым документом или книгой после остановки отладчика.  
  
 При отладке настройки уровня документа для Word многократная остановка отладчика и связанное с ней непредвиденное завершение программы могут привести к повреждению шаблона Normal. В этом случае поврежденный шаблон Normal можно удалить — он будет создан автоматически, как только вы снова откроете приложение Word. При этом макросы, сохраненные в шаблоне Word, не воссоздаются.  
  
### Отладка надстроек VSTO для Office 2013 с помощью Office 2013 или Office 2016  
 Если используется Visual Studio 2015 и на компьютере параллельно установлены обе версии Office, Visual Studio запускает Office 2016. Если вы используете Visual Studio 2013, Visual Studio запускает Office 2013.  
  
 Если отладку надстройки VSTO необходимо выполнить с использованием другой версии Office \(2013 или 2016\), откройте **конструктор проектов**, перейдите на вкладку **Отладка** и установите переключатель **Запуск внешней программы**. Затем укажите расположение соответствующего исполняемого файла приложения Office.  
  
## Действие клавиш F10 и F11  
 При запуске отладки проекта Office клавиши F10 и F11 действуют не так, как при запуске отладки других проектов Visual Basic или C\#. В проектах Visual Basic или C\# отладчик останавливается на основной функции, а в случае проектов Office Visual Studio не имеет контроля над основной функции приложения Office. При этом в процессе отладки клавиши F10 и F11 работают точно так же, как в проектах Visual Basic и C\#.  
  
## Отображение исключений  
 В связи с особым взаимодействием между управляемым и неуправляемым кодом Visual Studio не отображает ошибки, которые выдают приложения Microsoft Office. Например, если надстройка VSTO, созданная с помощью средств разработки Office в Visual Studio, выдает исключение, приложение Microsoft Office продолжает работу, не выводя сообщение об ошибке. Для просмотра этих ошибок настройте отладчик на прерывание в случае исключений среды выполнения. Для получения дополнительной информации см. [Практическое руководство. Прерывание выполнения при создании исключения](~/misc/how-to-break-when-an-exception-is-thrown.md).  
  
 Если отладчик настроен на прерывание в случае исключений среды выполнения, все исключения вызывают остановку отладчика, включая обработанные исключения и некоторые исключения первого шанса, которые возникли в самой среде выполнения и могут не иметь отношения к вашему проекту. Ошибки, связанные с невозможностью обнаружения файла msosec, возникают в любом проекте и не требуют внимания. Исключения msosec никак не влияют на ваше решение.  
  
 Для перехвата исключений можно также использовать добавлять к методам операторы **Try...Catch**.  
  
 По умолчанию Visual Studio не отображает ошибки JIT\-отладки для проектов Office, но эту функцию можно включить, чтобы видеть возникающие ошибки. Для получения дополнительной информации см. [JIT-отладка в Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
## Аргументы командной строки  
 Если параметр **Действие при запуске** на странице свойств **Отладка** имеет значение **Запуск проекта**, Visual Studio не использует аргументы командной строки при отладке проекта, даже они указаны в качестве параметров запуска. Чтобы использовать аргументы командной строки при запуске отладки, выберите другое значение параметра **Действие при запуске**, отличное от значения **Запуск проекта**.  
  
## Система управления версиями  
 Отладка свойств не выполняется для всех пользователей, зарегистрированных в системе контроля версий, одновременно. Проекты Visual Basic и C\# сохраняют свойства отладки в файлы конкретных пользователей \(*имя\_проекта*.vbproj.user или *имя\_проекта*.csproj.user\), не входящие в систему управления версиями. Если отладку выполняют сразу несколько пользователей, каждый из них вводит свойства отладки вручную.  
  
## Отладка кэшированных наборов данных в проекте уровня документа  
 При каждой сборке проекта набор данных опустошается и создается заново. Чтобы отладить кэшированный набор данных, откройте документ вне Visual Studio, а затем присоедините отладчик.  
  
## Отладка проектов документов Word, основанных на формате документов Word 97\-2003 \(\*.doc\)  
 Для отладки проекта документа Word, основанного на формате документов Word 97\-2003 \(\*.doc\) необходимо добавить папку проекта в список надежных папок. Дополнительные сведения см. в разделе [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md).  
  
## Отладка отключенных надстроек  
 Приложения Microsoft Office могут отключать надстройки VSTO, которые ведут себя непредсказуемым образом. Это делается для того, чтобы предотвратить загрузку неисправного кода при каждом запуске приложения. В то же время, непредвиденное поведение может возникать и в процессе обычной отладки. Сведения о повторном включении надстроек VSTO см. в разделе [Практическое руководство. Повторное включение надстройки VSTO, которая была отключена](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 В приложениях Microsoft Office используются два вида отключения надстроек VSTO: жесткое и мягкое.  
  
### Жесткое отключение  
 Жесткое отключение происходит, если надстройка VSTO вызывает неожиданное прекращение работы приложения. На компьютере разработчика оно применяется также в случае остановки отладчика во время выполнения обработчика событий <xref:Microsoft.Office.Tools.AddIn.Startup> в надстройке VSTO. Надстройка VSTO, отключенная жестким способом, отображается в списке **Отключенные объекты** в приложении.  
  
 Если приложение Office жестко отключает надстройку VSTO, созданную с помощью средств разработки Office в Visual Studio, отключается только надстройка VSTO, которая вызвала сбой. Другие надстройки VSTO, созданные с помощью средств разработки Office в Visual Studio для того же приложения Office, будут загружаться по\-прежнему.  
  
### Мягкое отключение  
 Мягкое отключение применяется, если вызванная надстройкой VSTO ошибка не приводит к неожиданному завершению работы приложения. Например, надстройка VSTO отключается мягким способом, если создает необработанное исключение во время выполнения обработчика событий <xref:Microsoft.Office.Tools.AddIn.Startup>. Надстройка VSTO, отключенная мягким способом, отображается в приложении в списке **Неактивные надстройки приложений**, а значение записи реестра **LoadBehavior** для этой надстройки VSTO меняется, указывая на то, что эта надстройка выгружена. Подробнее о записи реестра **LoadBehavior** см. в разделе [Записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Устранение неполадок установки с помощью средства просмотра событий  
 Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] записывает сообщения в средство просмотра событий в Windows для всех исключений, возникших при установке или удалении решений Office. Эти сообщения можно использовать для решения проблем развертывания и установки.  
  
## Устранение ошибок запуска с помощью файла журнала и сообщений об ошибках  
 Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] может записывать все возникающие при запуске ошибки в файл журнала или отображать каждую ошибку в окне сообщения. По умолчанию эти параметры отключены. Для включения этих параметров необходимо создать переменные среды.  
  
 Чтобы каждая ошибка отображалась в окне сообщения, создайте переменную среды с именем `VSTO_SUPPRESSDISPLAYALERTS` и присвойте ей значение 0 \(ноль\). Чтобы отключить отображение сообщений, удалите эту переменную среды или присвойте ей значение 1 \(один\).  
  
 Чтобы ошибки записывались в файл журнала, создайте переменную среды с именем `VSTO_LOGALERTS` и присвойте ей значение 1 \(один\). Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает файл журнала в папке, содержащей манифест развертывания для надстройки VSTO, или в папке, содержащей документ или книгу, связанные с настройкой. Если это не удается, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает файл журнала в локальной папке %TEMP%. Для надстроек VSTO уровня приложения файлу журнала по умолчанию присваивается имя *имя\_надстройки*.vsto.log. Для проектов уровня документа файлу журнала присваивается имя *имя\_документа*.*extension*.log, например ExcelWorkbook1.xlsx.log. Чтобы остановить ведение журнала ошибок, удалите переменную среды или присвойте ей значение 0 \(ноль\).  
  
## См. также  
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Практическое руководство. Повторное включение надстройки VSTO, которая была отключена](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)  
  
  