---
title: "Ведущие элементы и элементы управления | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- host controls [Office development in Visual Studio], adding
- Office documents [Office development in Visual Studio, host controls
- host items [Office development in Visual Studio]
- application development [Office development in Visual Studio], host items
- Office applications [Office development in Visual Studio], host items
- host controls [Office development in Visual Studio], listed
- Excel [Office development in Visual Studio], host items
- host controls [Office Development in Visual Stuio], naming
- host controls [Office development in Visual Studio]
- host controls [Office development in Visual Studio], about host controls
- document-level customizations [Office development in Visual Studio], host controls
- Office applications [Office development in Visual Studio], host controls
- documents [Office development in Visual Studio], host controls
- controls [Office development in Visual Studio], host controls
- application development [Office development in Visual Studio], host controls
- Excel [Office development in Visual Studio], host controls
- host items [Office development in Visual Studio], about host items
- host items [Office development in Visual Studio], listed
- documents [Office development in Visual Studio], host items
- data binding [Office development in Visual Studio], host controls
- Office documents [Office development in Visual Studio, host items
- Word [Office development in Visual Studio], host items
- document-level customizations [Office development in Visual Studio], host items
- Word [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], deleting
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1512b4774efea9639f01135932ad076f6630ea12
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="host-items-and-host-controls-overview"></a>Общие сведения о ведущих элементах и элементах управления ведущего приложения
  Ведущие элементы и элементы управления ведущего приложения — это типы элементов, помогающие предоставить модель программирования для решений Office, созданных с помощью средств разработки Office в Visual Studio. Ведущие элементы и элементы управления осуществляют взаимодействие с объектными моделями Microsoft Office Word и Microsoft Office Excel, основанными на модели COM, больше похожее на взаимодействие с управляемыми объектами, такими как элементы управления Windows Forms.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="host-items"></a>Ведущие элементы  
 Ведущие элементы являются типами в верхней части иерархии объектной модели в проектах Office. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] определяет следующие ведущие элементы для решений Word и Excel.  
  
-   <xref:Microsoft.Office.Tools.Word.Document>  
  
-   <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Каждый из этих типов расширяет объект, встроенный в объектной модели Word или Excel объектной модели, который называется *собственным объектом Office*. Например, ведущий элемент <xref:Microsoft.Office.Tools.Word.Document> расширяет объект <xref:Microsoft.Office.Interop.Word.Document> , который определен в основной сборке взаимодействия для Word.  
  
 Ведущие элементы обычно имеют ту же базовую функциональность, что и соответствующие объекты Office, но улучшены путем добавления следующих возможностей.  
  
-   Возможность размещения управляемых элементов управления, включая элементы управления ведущего приложения и элементы управления Windows Forms.  
  
-   Расширенные модели событий. Некоторые события документа, книги и листа в собственных объектных моделях Word и Excel вызываются только на уровне приложения. Ведущие элементы предоставляют такие события на уровне документа; это упрощает обработку событий для конкретного документа.  
  
### <a name="understanding-host-items-in-document-level-projects"></a>Основные сведения о ведущих элементах в проектах уровня документа  
 В проектах уровня документа ведущие элементы предоставляют точку входа для вашего кода и имеют конструкторы, помогающие разрабатывать решения.  
  
 Ведущие элементы <xref:Microsoft.Office.Tools.Word.Document> и <xref:Microsoft.Office.Tools.Excel.Worksheet> имеют связанные конструкторы, являющиеся визуальным представлением документа или листа, как конструктор Windows Forms. Этот конструктор можно использовать для изменения содержимого документа или листа непосредственно в Word или Excel и для перетаскивания элементов управления в рабочую область конструирования. Дополнительные сведения см. в разделах [Document Host Item](../vsto/document-host-item.md) и [Worksheet Host Item](../vsto/worksheet-host-item.md).  
  
 Ведущий элемент <xref:Microsoft.Office.Tools.Excel.Workbook> не действует как контейнер для элементов управления, имеющихся в пользовательском интерфейсе. Вместо этого конструктор для данного ведущего элемента функционирует как область компонентов, что позволяет перетаскивать компоненты, такие как <xref:System.Data.DataSet>, в рабочую область конструирования. Для получения дополнительной информации см. [Workbook Host Item](../vsto/workbook-host-item.md).  
  
 Ведущие элементы нельзя создавать программными средствами в проектах уровня документа. Вместо этого используйте классы `ThisDocument`, `ThisWorkbook`или `Sheet`*n* , которые Visual Studio автоматически создает в проекте во время разработки. Эти созданные классы являются производными от ведущих элементов и обеспечивают точку входа для кода. Для получения дополнительной информации см. [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="understanding-host-items-in-vsto-add-in-projects"></a>Основные сведения о ведущих элементах в проектах надстроек VSTO  
 При создании надстройки VSTO вы не имеете доступа ко всем ведущим элементам по умолчанию. Тем не менее вы можете создать ведущие элементы <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook>и <xref:Microsoft.Office.Tools.Excel.Worksheet> в надстройках VSTO Word и Excel в среде выполнения.  
  
 После создания ведущего элемента вы можете выполнять такие задачи, как добавление элементов управления в документы. Для получения дополнительной информации см. [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="host-controls"></a>Элементы управления ведущего приложения  
 Элементы управления ведущего приложения расширяют различные объекты пользовательского интерфейса в объектных моделях Word и Excel, например Microsoft.Office.Interop.Word.ContentControl и <xref:Microsoft.Office.Interop.Excel.Range> объектов.  
  
 Для проектов Excel доступны следующие элементы управления ведущего приложения.  
  
-   [Chart Control](../vsto/chart-control.md)  
  
-   [Элемент управления ListObject](../vsto/listobject-control.md)  
  
-   [Элемент управления NamedRange](../vsto/namedrange-control.md)  
  
-   [Элемент управления XMLMappedRange](../vsto/xmlmappedrange-control.md)  
  
 Для проектов Word доступны следующие элементы управления ведущего приложения.  
  
-   [Элемент управления Bookmark](../vsto/bookmark-control.md)  
  
-   [Элементы управления содержимым](../vsto/content-controls.md)  
  
-   [Элемент управления XMLNode](../vsto/xmlnode-control.md)  
  
-   [Элемент управления XMLNodes](../vsto/xmlnodes-control.md)  
  
 Элементы управления ведущего приложения, добавленные в документы Office, ведут себя как встроенные объекты Office; однако элементы управления ведущего приложения имеют дополнительные функциональные возможности, включая события и возможности привязки данных. Например, если требуется записать события встроенного объекта <xref:Microsoft.Office.Interop.Excel.Range> в Excel, вы должны сначала обработать событие изменения листа. Затем необходимо определить, произошло ли изменение в <xref:Microsoft.Office.Interop.Excel.Range>. В отличие от этого, элемент управления ведущего приложения <xref:Microsoft.Office.Tools.Excel.NamedRange> имеет событие <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> , которое может обрабатываться непосредственно.  
  
 Отношение между ведущим элементом и элементами управления ведущего приложения очень похоже на отношение между формой Windows Forms и элементами управления Windows Forms. Элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> помещается в ведущий элемент <xref:Microsoft.Office.Tools.Excel.Worksheet> так же, как элемент управления "текстовое поле" помещается в форму Windows Forms. На следующем рисунке показана связь между ведущими элементами и элементами управления ведущего приложения.  
  
 ![Отношение между ведущими элементами и элементами управления ведущего приложения](../vsto/media/hostitemscontrols.png "связь между ведущими элементами и элементами управления ведущего приложения")  
  
 Вы также можете использовать в решениях Office элементы управления Windows Forms, добавляя их непосредственно в область документа Word и Excel. Дополнительные сведения см. в разделе [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
> [!NOTE]  
>  Добавление элементов управления ведущего приложения или элементов управления Windows Forms во вложенный документ Word не поддерживается.  
  
### <a name="adding-host-controls-to-your-documents"></a>Добавление элементов управления ведущего приложения в документы  
 В проектах уровня документа элементы управления ведущего приложения можно добавлять в документы Word или листы Excel во время разработки следующими способами.  
  
-   Добавляйте элементы управления ведущего приложения в документ во время разработки так же, как добавляется встроенный объект.  
  
-   Перетаскивайте элементы управления ведущего приложения из **панели элементов** в свои документы и листы. Элементы управления ведущего приложения доступны на вкладке **Элементы управления Excel** в проектах Excel, а элементы управления ведущего приложения Word доступны на вкладке **Элементы управления Word** в проектах Word.  
  
-   Перетаскивайте элементы управления ведущего приложения из окна **Источники данных** в свои документы и листы. Это позволяет добавлять элементы управления, которые уже привязаны к данным. Дополнительные сведения см. в разделе [привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 В проектах надстроек VSTO уровня документа можно также добавлять некоторые элементы управления ведущего приложения в документы во время выполнения. Для получения дополнительной информации см. [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Дополнительные сведения о добавлении элементов управления ведущего приложения в документы см. в следующих разделах.  
  
-   [Практическое руководство. Добавление элементов управления Chart на листы](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Практическое руководство. Добавление элементов управления XMLMappedRange на листы](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)  
  
-   [Практическое руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
-   [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Практическое руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)  
  
-   [Практическое руководство. Добавление элементов управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)  
  
### <a name="naming-host-controls"></a>Именование элементов управления ведущего приложения  
 При перетаскивании элемента управления ведущего приложения из **панели элементов** в документ этому элементу управления автоматически присваивается имя в виде типа элемента управления с последовательным номером. Например, закладки именуются как **bookmark1**, **bookmark2**и т. д. При добавлении элемента управления с помощью встроенной функциональности Word или Excel вы можете назначить ему определенное имя во время его создания. Вы также можете переименовывать свои элементы управления, изменяя значение свойства **Имя** в окне **Свойства** .  
  
> [!NOTE]  
>  Для именования элементов управления ведущего приложения нельзя использовать зарезервированные слова. Например, если вы добавите в лист элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> и измените его имя на **System**, при сборке проекта возникнут ошибки.  
  
### <a name="deleting-host-controls"></a>Удаление элементов управления ведущего приложения  
 В проектах уровня документа вы можете удалять элементы управления ведущего приложения во время разработки, выделив элемент управления в листе Excel или документе Word и нажав клавишу Delete. Однако для удаления элементов управления **вы должны использовать диалоговое окно** Присвоение имени <xref:Microsoft.Office.Tools.Excel.NamedRange> в Excel.  
  
 Если элемент управления ведущего приложения добавлен в документ во время разработки, не следует удалять его программными средствами во время выполнения, поскольку при следующей попытке использовать этот элемент управления в коде возникнет исключение. Метод `Delete` элемента управления ведущего приложения удаляет только элементы управления ведущего приложения, добавленные в документ во время выполнения. Если вы вызовете метод `Delete` элемента управления ведущего приложения, созданного во время разработки, возникнет исключение.  
  
 Например, метод <xref:Microsoft.Office.Tools.Excel.NamedRange.Delete%2A> элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> успешно удаляет <xref:Microsoft.Office.Tools.Excel.NamedRange> , только если он был добавлен в лист программным образом, который называется динамическим созданием элементов управления ведущего приложения. Динамически созданные элементы управления ведущего приложения можно также удалить, передав имя элемента управления в метод `Remove` свойства <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> или <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> . Для получения дополнительной информации см. [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Если конечный пользователь удаляет элемент управления ведущего приложения из документа во время выполнения, может произойти непредвиденный сбой решения. Для защиты от удаления элементов управления ведущего приложения можно использовать функции защиты документа в Word и Excel. Дополнительные сведения см. в разделе [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md).  
  
> [!NOTE]  
>  Не удаляйте программным образом элементы управления во время работы обработчика событий `Shutdown` документа или листа. Если возникает событие `Shutdown` , элементы пользовательского интерфейса становятся недоступными. Если вы хотите удалить элементы управления до закрытия приложения, добавьте свой код в другой обработчик событий, например в `BeforeClose` или `BeforeSave`.  
  
### <a name="programming-against-host-control-events"></a>Программирование реакции на события элементов управления ведущего приложения  
 Один из способов, которым элементы управления ведущего приложения расширяют объекты Office, является добавление событий. Например, объект <xref:Microsoft.Office.Interop.Excel.Range> в Excel и объект <xref:Microsoft.Office.Interop.Word.Bookmark> в Word не имеют событий, но [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] расширяет эти объекты, добавляя программируемые события. Вы можете получать доступ к этим событиям и программировать реакцию на них так же, как это делается с событиями элементов управления в Windows Forms: через раскрывающийся список событий в Visual Basic и страницу свойств событий в C#. Дополнительные сведения см. в разделе [Walkthrough: Programming Against Events of a NamedRange Control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
> [!NOTE]  
>  Не устанавливайте для свойства <xref:Microsoft.Office.Interop.Excel._Application.EnableEvents%2A> объекта <xref:Microsoft.Office.Interop.Excel.Application> в Excel значение **false**. Установка для этого свойства значения **false** предотвращает инициирование каких-либо событий в Excel, включая события элементов управления ведущего приложения.  
  
## <a name="see-also"></a>См. также  
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  