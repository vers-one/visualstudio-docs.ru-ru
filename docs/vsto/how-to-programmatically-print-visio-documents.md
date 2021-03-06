---
title: "Как: программная печать документов Visio | Документы Microsoft"
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
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Практическое руководство. Программная печать документов Visio
  Можно напечатать полный документ Microsoft Office Visio или только определенную страницу.  
  
 Подробные сведения о методах печати см. в справочной документации VBA для метода [Microsoft.Office.Interop.Visio.Document.Print](https://msdn.microsoft.com/library/office/ff767996.aspx) и метода [Microsoft.Office.Interop.Visio.Page.Print](https://msdn.microsoft.com/library/office/ff765064.aspx) .  
  
## <a name="printing-a-visio-document"></a>Печать документа Visio  
  
#### <a name="to-print-a-complete-document"></a>Печать всего документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Document.Print Microsoft.Office.Interop.Visio.Document объекта, который требуется напечатать.  
  
     В следующем примере кода печатается активный документ. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Печать страницы документа Visio  
  
#### <a name="to-print-a-page-of-a-document"></a>Печать страницы документа  
  
-   Вызовите метод Microsoft.Office.Interop.Visio.Pages.Print Microsoft.Office.Interop.Visio.Pages объекта, который требуется напечатать.  
  
     В следующем примере кода печатается первая страница активного документа. Чтобы использовать этот пример, запустите код из класса `ThisAddIn` в своем проекте.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>См. также  
 [Решения Visio](../vsto/visio-solutions.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Как: программное создание документов Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Как: открытие документов Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Как: программное закрытие документов Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Практическое руководство. Программное сохранение документов Visio](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  