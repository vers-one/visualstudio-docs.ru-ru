---
title: "Шаг 6. Добавление задачи на вычитание | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: "25"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 35fc0fd7be5d060019521467851708d0c6677935
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="step-6-add-a-subtraction-problem"></a>Шаг 6. Добавление задачи на вычитание
В шестой части этого учебника вам предстоит добавить задачу на вычитание и научиться выполнять следующие задачи:  
  
-   Хранение значений, которые участвуют в операции вычитания.  
  
-   Создание случайных чисел для задачи (а также гарантия, что ответ лежит в диапазоне от 0 до 100).  
  
-   Обновление метода, который проверяет ответы, таким образом, чтобы он также проверял новую задачу на вычитание.  
  
-   Обновление обработчика событий таймера Tick таким образом, чтобы этот обработчик событий заполнял корректный ответ после истечения времени.  
  
### <a name="to-add-a-subtraction-problem"></a>Добавление задачи на вычитание  
  
1.  Добавьте в форму две целочисленные переменные для задачи на вычитание — между целочисленными переменными для задачи на сложение и для таймера. Код должен выглядеть следующим образом.  
  
     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]  
  
     Имена новых целочисленных переменных — **minuend** и **subtrahend** — не являются терминами программирования. Это принятые в арифметике обозначения для числа, которое вычитается из другого числа (subtrahend — вычитаемое), и числа, из которого производится вычитание (minuend — уменьшаемое). Остаток — это уменьшаемое за минусом вычитаемого. Можно использовать другие имена, так как программа не требует определенных имен для переменных, элементов управления, компонентов или методов. Необходимо соблюдать правила — например, не начинать имена с цифр — но вообще можно использовать такие имена, как x1, x2, x3 и x4. Однако универсальные имена ухудшают читабельность кода, и при возникновении проблем отследить их источник становится практически невозможно. Чтобы имена переменных были уникальными и информативными, для умножения и деления далее в этом учебнике мы также будем использовать традиционные имена: multiplicand (множимое) × multiplier (множитель) = product (произведение); dividend (делимое) ÷ divisor (делитель) = quotient (частное).  
  
     Затем необходимо изменить метод `StartTheQuiz()`, чтобы получить случайные значения для задачи на вычитание.  
  
2.  Добавьте после комментария "Fill in the subtraction problem" (Заполнение задачи на вычитание) следующий код.  
  
     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]  
  
     Чтобы в задаче на вычитание не было отрицательных ответов, метод `Next()` класса `Random` в этом коде используется несколько иначе, чем в задаче на сложение. Когда методу `Next()` передается два значения, он выбирает случайное число, которое больше первого значения или равно ему и меньше второго значения. Следующий код выбирает случайное число в диапазоне от 1 до 100 и сохраняет его в переменной minuend.  
  
     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]  
  
     Вызвать метод `Next()` класса `Random`, который мы ранее в этом руководстве назвали "randomizer", можно различными способами. Методы, которые можно вызывать несколькими способами, называются перегруженными. Для их изучения можно использовать IntelliSense. Посмотрите еще раз на всплывающую подсказку окна IntelliSense для метода `Next()`.  
  
     ![Подсказка окна Intellisense](../ide/media/express_overloads.png "Express_Overloads")  
Подсказка окна Intellisense  
  
     В подсказке сказано **(+2 перегрузки)**, что означает, что вызвать метод `Next()` можно еще двумя способами. Перегрузки методов содержат разное количество или типы аргументов, поэтому работают слегка по-разному. Например, метод может принимать один целочисленный аргумент, тогда как одна из его перегрузок может принимать целое число и строку. Выбирайте подходящую перегрузку в зависимости от того, что требуется сделать. При добавлении кода в метод `StartTheQuiz()` в окне Intellisense появляется дополнительная информация, как только вы введете `randomizer.Next(`. Нажимайте клавиши СТРЕЛКА ВВЕРХ и СТРЕЛКА ВНИЗ для перебора перегрузок, как показано на следующем рисунке.  
  
     ![Перегрузка метода Next() в IntelliSense](../ide/media/express_nextoverload.png "Express_NextOverload")  
Перегрузка метода Next() в IntelliSense  
  
     В данном случае необходимо выбрать последнюю перегрузку, чтобы можно было задать минимальное и максимальное значения.  
  
3.  Для проверки правильного ответа для задачи на вычитание, измените метод `CheckTheAnswer()`.  
  
     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]  
  
     В Visual C# `&&` — это оператор `logical and` . Эквивалентный оператор в языке Visual Basic — `AndAlso`. Эти операторы означают, что "Если addend1 плюс addend2 равно значению NumericUpDown с именем sum и если minuend минус subtrahend равно значению NumericUpDown с именем difference". Метод `CheckTheAnswer()` возвращает значение `true`, только если игрок дал правильные ответы и на задачу на сложение, и на задачу на вычитание.  
  
4.  Замените последнюю часть обработчика событий таймера Tick следующим кодом, чтобы по истечении времени этот обработчик событий проставлял правильный ответ.  
  
     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]  
  
5.  Сохраните и выполните код.  
  
     Теперь программа включает в себя задачу на вычитание, как показано на следующем рисунке.  
  
     ![Математическая головоломка с задачей на вычитание](../ide/media/express_addsubtract.png "Express_AddSubtract")  
Математическая головоломка с задачей на вычитание  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Step 7: Add Multiplication and Division Problems](../ide/step-7-add-multiplication-and-division-problems.md) (Шаг 7. Добавление задач на умножение и деление).  
  
-   Предыдущий шаг руководства см. в разделе [Step 5: Add Enter Event Handlers for the NumericUpDown Controls](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md) (Шаг 5. Добавление обработчиков событий входа для элементов управления NumericUpDown).