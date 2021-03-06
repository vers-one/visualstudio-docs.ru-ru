---
title: "Диалоговое окно схемы XML | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 71cff97fc87d22a4edeee3b114e9599f307ab040
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="xml-schemas-dialog-box"></a>Диалоговое окно «XML-схемы»
**XML-схем** диалоговое окно используется для выбора какие схем XML схема определения языка XSD для связывания с XML-документа. Можно выбрать схему из кэша схем или указать схему, которая не находится в кэше. Выбранные схемы считаются частью набора схем. Наборы схем применяются в технологии IntelliSense, а также служат для проверки правильности XML-документов.  
  
 Вы можете получить доступ к **XML-схем** диалоговое окно, щелкните **схемы** кнопки в окне свойств документа, либо выбрав **схемы** из **XML** меню.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Используйте**  
 Выберите, как должна использоваться XML-схема.  
  
-   **Автоматическое**. Эта схема не используется текущим документом, но доступна для автоматического установления соответствия. Если XML-документ объявляет пространство имен, соответствующее пространству имен `targetNamespace` этой схемы, схема будет автоматически привязана и включена в набор схем.  
  
-   **Использовать эту схему**. Эта схема используется текущим документом. Либо пользователь, щелкнув этот столбец, явно указал, что должна использоваться данная схема, либо схема была автоматически привязана в результате установления соответствия с пространством имен `targetNamespace`.  
  
-   **Не использовать выбранные схемы**. Данная схема не используется текущим документом, даже если имеется соответствующее пространство имен `targetNamespace`. Этот параметр может быть полезен для разрешения конфликтов, если в кэше схем или в решении имеется более одной версии одной и той же схемы.  
  
**Целевое пространство имен**  
Отображает целевое пространство имен, связанное с XML-схемой.  
  
**Имя файла**  
Отображает имя файла XML-схемы.  
  
**Добавить**  
Открывает **Открытие XSD-схемы** диалоговое окно, в котором можно выбрать дополнительные схемы для добавления в набор схем. При добавлении схемы в схеме задано, **используйте** значение столбца равно **использовать эту схему**.  
  
**Remove**  
Удаляет выбранную в настоящее время схему из набора схем. При этом схема удаляется из кэша схем, находящегося в оперативной памяти, но не из файловой системы.  
  
## <a name="see-also"></a>См. также  
 [Компоненты редактора XML](../xml-tools/xml-editor-components.md)   
 [Как: выберите для использования XML-схем](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Кэш схем](../xml-tools/schema-cache.md)