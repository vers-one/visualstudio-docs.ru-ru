---
title: "Объект VSTextView | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f169c3302b3e6fd72e5017193e34836ed3e5340e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vstextview-object"></a>Объект VSTextView
Текстовое представление является окно, которое позволяет пользователям просматривать и изменять текст в Юникоде текстового буфера. По существу представление является то, что большинство пользователей называют редактора. Так как представление отделяется от буфера различные слои текста (перенос по словам, структуризации текста и т. д), представление не гарантированно точное представление текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 В следующей таблице показаны интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекта.  
  
|Интерфейс|Описание:|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный интерфейс OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Включает создание составных действий (действия, сгруппированные в единое один отмены и повтора).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет основные методы для управления и доступа к представлению. `IVsTextView`не является потокобезопасным.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет область окна.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с слои текста.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции на представлении из другого потока.|  
  
## <a name="see-also"></a>См. также  
 [Изменение фигур](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Объект VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Доступ к theText представления с помощью API прежних версий](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)