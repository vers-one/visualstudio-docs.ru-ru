---
title: "XSLT-шаблонов по умолчанию | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fe1bf4dda6bed505f0892a18825e93f66e13e16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="xslt-default-templates"></a>XSLT-шаблоны по умолчанию
Если в таблице стилей отсутствует совпадающее явное правило шаблона, то во время обработки XSLT используется шаблон по умолчанию. Шаблон по умолчанию, называемый также встроенным правилом шаблона, определен в разделе  5.8 спецификации W3C XSLT 1.0. Шаблон по умолчанию разрешает обработчику XSLT обрабатывать узел, даже если ему не соответствует ни одно явное правило шаблона. Однако, поскольку встроенное правило шаблона явно не определено в таблице стилей, это может привести к непредвиденным или сбивающим с толку результатам XSLT-преобразования.  
  
 Отладчик XSLT теперь отображает код XSLT-шаблонов по умолчанию. При пошаговом выполнении XSLT-преобразования отладчик отображает в окне шаблон по умолчанию, если используется шаблон по умолчанию. Это позволяет выполнять по шагам код и задавать точки останова на инструкциях кода.  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)