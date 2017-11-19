---
title: "Инкапсулировать поле - рефакторинга (Visual Basic) | Документы Microsoft"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.openlocfilehash: 9575ad83ead4960016ba7814642cacb1db04ea4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Инкапсулировать поле в Visual Basic
**Что:** позволяет включить поле в свойстве и обновлять все случаи использования этого поля с помощью только что созданный свойства.

**Когда:** требуется переместить поле в свойстве и обновить все ссылки на это поле.  

**Почему:** должны иметь другие классы доступа к полю, но не требуется прямой доступ этих классов.  Заключив поле в свойстве, можно написать код для проверки значения, присваиваемого, например.

**Как:**

1. Выделите или наведите курсор текста внутри имя поля для инкапсуляции:

   ![Выделенный код](media/encapsulate_highlight.png)

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl + R**, затем **Ctrl + E**.  (Обратите внимание, что сочетание клавиш может отличаться в зависимости от выбранного профиля.)
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** меню и выберите либо **инкапсуляции поля** запись из контекстного меню окна предварительного просмотра.
   * **Мышь**
     * Выберите **Правка > рефакторинг > инкапсулировать поле**.
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** меню и выберите либо **инкапсуляции поля** запись из контекстного меню окна предварительного просмотра.

   Выбранное | Описание
   --------- | -----------
   **Инкапсуляция поля (и использовать свойство)** | Инкапсулирует поле со свойством и обновляет все случаи использования поля с помощью созданного свойства
   **Инкапсуляция поля (но продолжать использовать поле)** | Инкапсулирует поле со свойством, но оставляет без изменений все случаи использования поля

   Свойство будет создан и ссылки на поле обновляется, если выбран.

   > [!TIP]
   > Используйте [ **предварительного просмотра изменений** ](../../ide/preview-changes.md) ссылку во всплывающем окне, чтобы увидеть, что это приведет к появлению перед фиксацией в его.

   ![Инкапсуляция результат свойства](media/encapsulate_result.png)

## <a name="see-also"></a>См. также  
[Рефакторинг (Visual Basic)](../refactoring-vb.md)  
[Просмотр изменений](../../ide/preview-changes.md)