---
title: "Команда реализации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2704794e4683fb461dca971a3893ca831591ca0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="command-implementation"></a>Реализация команды
Реализация команды в VSPackage, необходимо выполнить следующие задачи:  
  
1.  В vsct-файле настройте группу команд и добавить команду. Дополнительные сведения см. в разделе [Visual Studio Command Table (. Файлы Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)"  
  
2.  Команда регистрации в Visual Studio.  
  
3.  Реализуйте команду.  
  
 Следующие разделы описывают для регистрации и реализации команд.  
  
## <a name="registering-commands-with-visual-studio"></a>Регистрация команд с помощью Visual Studio  
 Если команда является отображение в меню, необходимо добавить <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> VSPackage и используйте в качестве значения, либо имя меню, либо его идентификатора ресурса.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Кроме того, необходимо зарегистрировать командой <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. Эту службу можно получить с помощью <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> метод, если VSPackage является производным от <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Реализация команды  
 Существует несколько способов реализации команд. Статического меню команду, которая является командой, которая всегда отображается одинаково, так и в том же меню, создать команду с помощью <xref:System.ComponentModel.Design.MenuCommand> как показано в примерах в предыдущем разделе. Чтобы создать статические команду, необходимо предоставить обработчик событий, который отвечает за выполнение команды. Так как команда всегда включена и видимым, у вас показывают его состояние в Visual Studio. Если вы хотите изменить состояние команды в зависимости от определенных условий, можно создать команду как экземпляр <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> класса и в его конструкторе предоставить обработчик событий, чтобы выполнить команду и обработчика состояния запроса для уведомления Visual Studio при изменении состояния команды. Вы также можете реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> как часть класса команд или можно реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Если команду предоставляется как часть проекта. Два интерфейса и <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> все класса имеют методы, уведомляющие Visual Studio об изменении состояния команды и другие методы, которые обеспечивают выполнение команды.  
  
 При добавлении команды служба команд, он становится одним из цепочки команд. При реализации методов уведомления и выполнения состояние для команды аккуратно для предоставления только для этой конкретной команды и передачи во всех остальных случаях на другие команды в цепочке. Если не удалось передать команду (как правило, возвращая <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio, могут перестать правильно работать.  
  
## <a name="query-status-methods"></a>Методы запросов состояния  
 При реализации либо <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> метод, проверяют идентификатор GUID для набора команд, которому принадлежит команды и идентификатор команды. Соблюдайте следующие правила.  
  
-   Если идентификатор GUID не распознается, одного из методов реализации должен возвращать <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Если реализации одного из методов распознает идентификатор GUID, но фактически не реализован команды, то метод должен вернуть <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
-   Если реализации одного из методов распознает GUID и команды, то метод должен установить флаги команды поле каждой команды (в `prgCmds` параметра), используя следующие флаги:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда поддерживается.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда не должны быть видимыми.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда включена и отображается для были проверены.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда включена.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда должен быть скрыт, если он появляется в контекстном меню.  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Если команда контроллер меню, не включен, но его список раскрывающегося меню не пуста и по-прежнему доступен. (Этот флаг используется редко.)  
  
-   Если команда был определен в vsct-файле с `TextChanges` флаг, установите следующие параметры:  
  
    -   Задать `rgwz` элемент `pCmdText` параметр новый текст команды.  
  
    -   Задать `cwActual` элемент `pCmdText` параметра размер командной строки.  
  
 Также убедитесь, что текущего контекста не является функцией автоматизации, если команда специально предназначен для обработки функций автоматизации.  
  
 Чтобы указать, что поддерживается определенной команды, возвращают <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Другие команды возвращают <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 В следующем примере метод состояние запроса сначала гарантирует, что контекст не функцию автоматизации, а затем находит правильный набор команд GUID и идентификатор команды. Саму команду устанавливается поддерживается и включен. Другие команды не поддерживаются.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Методы выполнения  
 Реализация метода execute напоминает реализации метода состояние запроса. Во-первых убедитесь, что контекст не функцию автоматизации. Проверьте идентификатор GUID и идентификатор команды. Если идентификатор GUID или идентификатор команды не распознан, возвращают <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Обработать команду, выполнять его и вернуть <xref:Microsoft.VisualStudio.VSConstants.S_OK> после успешного выполнения. Команда отвечает за обнаружение ошибок и уведомления; Таким образом возвращается код ошибки, если происходит сбой выполнения. В следующем примере показано, как метод выполнения должен быть реализован.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)