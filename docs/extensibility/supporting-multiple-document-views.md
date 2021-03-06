---
title: "Поддержка нескольких представлений документов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4efd76830356996bdf75c923f457d19d2381763c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-multiple-document-views"></a>Поддержка нескольких представлений документов
Можно обеспечить более одного представления документа, создав отдельный документ данных и объекты представления документа для редактора. Ниже перечислены некоторые случаи, в которых может потребоваться дополнительный документ-представление  
  
-   Поддержка нового окна: требуется редактора для создания двух или более представлений того же типа, чтобы пользователь, уже открыт в редакторе окно можно открыть новое окно, выбрав **новое окно** из **окна** меню.  
  
-   Формы и код в представлении поддержки: требуется редактора представления различных типов. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], например, предоставляет представление формы и представление кода.  
  
 Дополнительные сведения об этом см. в процедуре CreateEditorInstance в файле EditorFactory.cs в проект пользовательский редактор, созданный с шаблона пакета Visual Studio. Дополнительные сведения о данном проекте см. в разделе [Пошаговое руководство: Создание специализированного редактора](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## <a name="synchronizing-views"></a>Синхронизация представлений  
 При реализации несколько представлений, объект данных документа несет ответственность за хранение всех представлений с данными. Можно использовать обработки интерфейсы на события <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> синхронизировать несколько представлений с данными.  
  
 Если вы не используете <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> объект для синхронизации несколько представлений, то необходимо реализовать собственную систему событий для обработки изменений, внесенных в объект данных документа. Можно использовать различные уровни детализации обновлять несколько представлений. Параметр максимального гранулярности, при вводе в одном представлении других представлений немедленно обновляется. С минимальным гранулярности других представлений не обновляются, пока они активируются.  
  
## <a name="determining-whether-document-data-is-already-open"></a>Определение ли данные документа открыт уже  
 Запущенной таблице документов (RDT) в интегрированной среде разработки (IDE) помогает отслеживать ли данных для документа уже открыт, как показано на следующей схеме.  
  
 ![График DocDataView](../extensibility/media/docdataview.gif "Docdataview")  
Несколько представлений  
  
 По умолчанию каждое представление (объект представления документа) содержится в окне фрейма (<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>). Как уже отмечалось Однако данные документа могут отображаться в нескольких представлениях. Чтобы включить эту возможность, Visual Studio проверяет RDT, чтобы определить, является ли этот документ уже открыт в редакторе. При вызове метода IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> для создания редактора, возвращается НЕНУЛЕВОЕ значение в `punkDocDataExisting` параметр указывает, что документ открыт в другом редакторе. Дополнительные сведения о том, как в разделе функции RDT [под управлением таблицы Document](../extensibility/internals/running-document-table.md).  
  
 В вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> реализацию, проверьте объект данных документа, возвращаемый в `punkDocDataExisting` для определения того, подходит ли для редактора данных документа. (Например, только данные HTML должен отображаться с помощью редактора HTML.) При необходимости, редактор фабрики должен предоставить во втором представлении данных. Если `punkDocDataExisting` не `NULL`, можно либо что объект данных документа открыт в другом редакторе или, скорее всего, данные документ открыт в другое представление с таким же редактор. Если данные документа открыт в другом редакторе, не поддерживающий фабрику редактора, Visual Studio не открывается редактор фабрики. Дополнительные сведения см. в разделе [как: присоединение представлений данных документа](../extensibility/how-to-attach-views-to-document-data.md).