---
title: "Шаг 3. Настройка свойств формы | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
caps.latest.revision: "18"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e703372a3b59ceee439b234e02e4a2d5a3cb6275
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="step-3-set-your-form-properties"></a>Шаг 3. Настройка свойств формы
Далее окно **Свойства** используется для изменения внешнего вида формы.  
  
 ![ссылка на видео](../data-tools/media/playvideo.gif "воспроизвести_видео")Видеоверсию этой статьи см. на следующих страницах: [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 1](http://go.microsoft.com/fwlink/?LinkId=205209) (Учебное руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 1) или [Tutorial 1: Create a Picture Viewer in C# - Video 1](http://go.microsoft.com/fwlink/?LinkId=205199) (Учебное руководство 1. Создание приложения для просмотра рисунков на C# — видео 1). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.  
  
### <a name="to-set-your-form-properties"></a>Настройка свойств формы  
  
1.  Убедитесь, что вы смотрите на конструктор Windows Forms. В интегрированной среде разработки Visual Studio откройте вкладку **Form1.cs [Design]** (или вкладку **Form1.vb [Design]** в Visual Basic).  
  
2.  Чтобы выделить форму **Form1**, щелкните в любом ее месте. Посмотрите на окно **Свойства**. Теперь оно должно отображать свойства формы. У формы есть различные свойства. Например, можно установить цвет переднего плана и фона, текст заголовка, который отображается в верхней части формы, размер формы и другие свойства.  
  
    > [!NOTE]
    >  Если окно **Свойства** не открывается, остановите программу, нажав квадратную кнопку **Остановить отладку** на панели инструментов или просто закройте окно. Если программа остановлена, но окно **Свойства** все равно не отображается, в строке меню выберите **Вид**, **Окно свойств**.  
  
3.  Когда форма будет выбрана, найдите свойство **Text** в окне **Свойства**. В зависимости от того, как отсортирован список, может потребоваться прокрутить вниз. Выберите **Text**, введите **Программа просмотра изображений**, а затем нажмите клавишу ВВОД.  Теперь форма должна содержать текст **Программа просмотра изображений** в заголовке окна. Окно **Свойства** должно выглядеть так, как показано на рисунке ниже.  
  
     ![Окно "Свойства"](../ide/media/express_edittextproperty.png "Express_EditTextProperty")  
Окно \"Свойства\"  
  
    > [!NOTE]
    >  Свойства можно упорядочить по категориям или в алфавитном порядке. Вы можете переключаться между двумя этими представлениями с помощью кнопок в окне **Свойства**. В этом руководстве свойства легче находить в представлении, в котором свойства представлены в алфавитном порядке.  
  
4.  Вернитесь к конструктору Windows Forms. Нажмите нижний правый маркер перетаскивания формы, который представляет собой небольшой белый квадрат в нижнем правом углу формы и показан на рисунке ниже.  
  
     ![Маркер перетаскивания](../ide/media/express_bottomrt_drag.png "Express_BottomRT_Drag")  
Маркер перетаскивания  
  
     Перетащите маркер, чтобы изменить размер формы — она должна стать шире и немного выше.  
  
5.  Посмотрите в окно **Свойства** и обратите внимание, что изменилось значение свойства **Size**. Свойство **Size** меняется при каждом изменении формы. Перетащите маркер, чтобы форма имела размер около 550, 350 (не обязательно точно такие значения). Такой размер вполне подходит для данного проекта. В качестве альтернативы можно вводить значения непосредственно в свойстве **Size** и затем нажимать клавишу ВВОД.  
  
6.  Снова выполните программу. Помните, что можно использовать любой из следующих методов для выполнения программы.  
  
    -   Нажмите клавишу **F5**.  
  
    -   В строке меню выберите **Отладка**, **Начать отладку**.  
  
    -   На панели инструментов нажмите кнопку **Начать отладку**, которая показана на рисунке ниже.  
  
         ![Кнопка "Начать отладку" на панели инструментов](../ide/media/express_icondebug.png "Express_IconDebug")  
Кнопка панели инструментов "Начать отладку"  
  
     Как и ранее, интегрированная среда разработки выполняет построение программы и запускает ее, открывается окно.  
  
7.  Перед переходом к следующему шагу, остановите программу, так как интегрированная среда разработки не позволяет изменять программу при ее выполнении. Помните, что можно использовать любой из следующих методов для остановки программы.  
  
    -   На панели инструментов нажмите кнопку **Остановить отладку**.  
  
    -   В строке меню выберите **Отладка**, **Остановить отладку**.  
  
    -   Нажмите кнопку X в верхнем углу окна **Form1**.  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Шаг 4. Создание макета формы с помощью элемента управления TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).  
  
-   Предыдущий шаг руководства см. в разделе [Шаг 2. Запуск программы](../ide/step-2-run-your-program.md)