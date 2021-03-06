---
title: "Рефакторинг поля в свойство на Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 78d2c33002e59eab1b6e8605092a74d9995453a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="encapsulate-a-field-refactoring"></a>Рефакторинг для инкапсуляции поля

Область применения этого рефакторинга:

- C#

- Visual Basic

**Что?** Эта возможность позволяет включить поле в свойство и обновлять все случаи использования этого поля, чтобы применить созданное свойство.

**Когда?** Требуется переместить поле в свойство и обновить все ссылки на это поле.

**Зачем?** Вы хотите предоставить другим классам доступ к полю, но не хотите давать им прямой доступ.  Заключив поле в свойство, можно написать код для проверки присваиваемого значения.

## <a name="how-to"></a>Практические советы

1. Выделите имя типа, который требуется инкапсулировать, или поместите в него текстовый курсор:

   - C#:

    ![Выделенный код — C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

    ![Выделенный код — Visual Basic](media/encapsulate-highlight-vb.png)

1. Затем выполните одно из следующих действий:

   - **Клавиатура**
     - Нажмите клавиши **CTRL+R**, а затем — **CTRL+E**.  (Обратите внимание, что сочетание клавиш может отличаться в зависимости от выбранного профиля.)
     - Нажмите клавиши **CTRL + .**, чтобы активировать меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Инкапсулировать поле**.
   - **Мышь**
     - Последовательно выберите **Правка >Рефакторинг > Инкапсулировать поле**.
     - Щелкните код правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Инкапсулировать поле**.

   Выбранное | Описание:
   --------- | -----------
   **Инкапсулировать поле (и использовать свойство)** | Инкапсулирует поле со свойством и обновляет все случаи использования поля, чтобы применить созданное свойство.
   **Инкапсулировать поле (но продолжать использовать поле)** | Инкапсулирует поле со свойством, но оставляет без изменений все случаи использования поля.

   Свойство создается, а ссылки на поле обновляются, если они выбраны.

   > [!TIP]
   > Перейдите по ссылке **Просмотреть изменения**, чтобы узнать, [каким будет результат](../../ide/preview-changes.md), прежде чем зафиксировать его.

   - C#:

    ![Результат инкапсуляции свойства — C#](media/encapsulate-result-cs.png)

   - Visual Basic:

    ![Результат инкапсуляции свойства — Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>См. также

[Рефакторинг](../refactoring-in-visual-studio.md)  
[Просмотр изменений](../../ide/preview-changes.md)