---
title: "Шаг 6. Присвоение имен элементам управления \"Кнопка\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d1981e8003941f14295cd137ba238808ec49229a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="step-6-name-your-button-controls"></a>Шаг 6. Присвоение имен элементам управления "Кнопка"
В форме существует только один элемент управления PictureBox. Когда он был добавлен, интегрированная среда разработки автоматически присвоила ему имя **pictureBox1**. Существует только один элемент управления CheckBox с именем **checkBox1**. Скоро будет написан некоторый код. В этом коде будет обращение к элементам управления CheckBox и PictureBox. Так как существуют только по одному экземпляру каждого компонента, то становится ясно, что означает упоминание имен **pictureBox1** или **checkBox1** в коде.  
  
> [!NOTE]
>  В Visual Basic по умолчанию первая буква любого имени элемента управления является заглавной, поэтому у элементов управления имена **PictureBox1**, **CheckBox1**и так далее.  
  
 В форме есть четыре кнопки. Интегрированная среда разработки назвала их как **button1**, **button2**, **button3**и **button4**. Только по их текущему имени нельзя узнать, какая кнопка является кнопкой **Закрыть** , а какая кнопкой **Показать рисунок** . Вот почему присвоение элементам управления в виде кнопок более осмысленных названий полезно.  
  
 ![ссылка на видео](../data-tools/media/playvideo.gif "воспроизвести_видео")Видеоверсию этой статьи см. на следующих страницах: [Tutorial 1: Create a Picture Viewer in Visual Basic - Video 3](http://go.microsoft.com/fwlink/?LinkId=205213) (Учебное руководство 1. Создание приложения для просмотра рисунков на Visual Basic — видео 3) или [Tutorial 1: Create a Picture Viewer in C# - Video 3](http://go.microsoft.com/fwlink/?LinkId=205202) (Учебное руководство 1. Создание приложения для просмотра рисунков на C# — видео 3). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.  
  
### <a name="to-name-your-button-controls"></a>Присвоение имен элементам управления "Кнопка"  
  
1.  В форме нажмите кнопку **Закрыть** . (Если все еще выделены все кнопки, для отмены выделения нажмите клавишу ESC.) Прокрутите содержимое окна **Свойства**, пока не появится свойство **(Name)**. (Свойство **(Name)** расположено в верхней части, когда свойства расположены в алфавитном порядке.) Измените имя на **closeButton**, как показано на рисунке ниже.  
  
     ![Окно "Свойства" с именем closeButton](../ide/media/express_setnameproperty.png "Express_SetNameProperty")  
Окно "Свойства" с именем closeButton  
  
    > [!NOTE]
    >  If you try changing the name of your button to **closeButton**, with a space between the words close and Button, the IDE displays an error message: "Property value is not valid." Пробелы (а также несколько других символов) запрещено использовать в именах элементов управления.  
  
2.  Переименуйте другие три кнопки как **backgroundButton**, **clearButton**, **showButton**. Имена можно проверить в раскрывающемся списке селектора элементов управления в окне **Свойства** . Отобразятся новые имена кнопок.  
  
3.  Двойным щелчком нажмите кнопку **Показать рисунок** в форме. В качестве альтернативы можно нажать кнопку **Показать рисунок** в форме, а затем нажать клавишу ВВОД. При этом интегрированная среда разработки открывает в главном окне дополнительную вкладку, которая называется **Form1.cs** (**Form1.vb** , если используется Visual Basic). На этой вкладке отображается файл кода для формы, как показано на следующем рисунке.  
  
     ![Вкладка Form1.cs с кодом Visual C#](../ide/media/express_showbuttoncode.png "Express_ShowButtonCode")  
Вкладка Form1.cs с кодом Visual C#  
  
4.  Обратите внимание на эту часть кода. (Откройте вкладку **VB** ниже, если используется Visual Basic для просмотра Visual Basic-версии кода.)  
  
     [!code-vb[VbExpressTutorial1Step6#1](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_1.vb)]
     [!code-csharp[VbExpressTutorial1Step6#1](../ide/codesnippet/CSharp/step-6-name-your-button-controls_1.cs)]  
  
     Вы видите код с именем `showButton_Click()`. Интегрированная среда разработки добавила его в код формы при открытии файла кода для кнопки **showButton** . Во время разработки при открытии файла кода для элемента управления в форме для элемента управления создается код, если он еще не существует. Этот код, известный как *метод*, выполняется при запуске программы и использовании этого элемента управления (в данном случае — кнопка **Показать рисунок** ).  
  
    > [!NOTE]
    >  В этом руководстве код Visual Basic, который создается автоматически, был упрощен путем удаления всего, что находилось в круглых скобках (). Когда это происходит, одинаковый код можно удалить. Программа будет работать в любом случае. В оставшейся части руководства весь автоматически созданный код был упрощен везде, где это было возможным.  
  
5.  Снова выберите вкладку конструктора Windows Forms (**Form1.cs [Design]** в Visual C#, **Form1.vb [Design]** в Visual Basic), а затем откройте файл кода для кнопки **Очистить рисунок** , чтобы создать метод для нее в коде формы. Повторите это действие для двух оставшихся кнопок. Каждый раз при этом действии среда интегрированной разработки добавляет в файл кода формы новый метод.  
  
6.  Чтобы добавить еще один метод, откройте файл кода для элемента управления CheckBox в конструкторе Windows Forms, чтобы интегрированная среда разработки создала метод `checkBox1_CheckedChanged()` . Этот метод вызывается каждый раз, когда пользователь устанавливает или снимает флажок.  
  
    > [!NOTE]
    >  При работе с программой необходимо часто переключаться между редактором кода и конструктором Windows Forms. Среда интегрированной разработки упрощает передвижение по проекту. Используйте **Обозреватель решений** , чтобы открыть конструктор Windows Forms с помощью двойного щелчка по **Form1.cs** в Visual C# или **Form1.vb** в Visual Basic; или выберите **Вид**, **Конструктор**в строке меню.  
  
     Ниже показан новый код, который представлен в редакторе кода.  
  
     [!code-vb[VbExpressTutorial1Step6#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]
     [!code-csharp[VbExpressTutorial1Step6#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]  
  
     Пять методов, которые были добавлены, называются *обработчики событий*, так как программа вызывает их каждый раз, когда происходит событие (например, пользователь нажимает кнопку или устанавливает флажок).  
  
     При просмотре кода для элемента управления в интегрированной среде разработки во время разработки Visual Studio добавляет метод обработчика событий для элемента управления, если он не существует. Например, при двойном щелчке по кнопке интегрированная среда разработки добавляет обработчик события Click, который вызывается каждый раз, когда пользователь нажимает кнопку. Если дважды щелкнуть флажок, интегрированная среда разработки добавляет обработчик события CheckedChanged, который вызывается каждый раз, когда пользователь устанавливает или снимает флажок.  
  
     После добавления обработчика событий для элемента управления к нему можно вернуться в любой момент из конструктора Windows Forms с помощью двойного щелчка по элементу управления или путем выбора пунктов **Вид**, **Код**в строке меню.  
  
     Имена являются важными при выполнении построения программы, и методы (включая обработчики событий) могут иметь любые имена, которые нужны. При добавлении обработчика событий с помощью интегрированной среды разработки она создает имя на основе имени элемента управления и обрабатываемого события. Например, событие Click для кнопки с именем **showButton** вызывает метод обработчика событий `showButton_Click()` . Также обычно после имени метода добавляются открывающая и закрывающая круглые скобки () для индикации того, какие методы рассматриваются. Если вы примете решение изменить имя переменной кода, щелкните правой кнопкой мыши по переменной в коде, а затем выберите команду **Рефакторинг**, **Переименовать**. Все экземпляры этой переменной в коде будут переименованы. Дополнительные сведения см. в разделе [Оптимизация кода с помощью переименования](../ide/reference/rename.md).
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства см. в разделе [Step 7: Add Dialog Components to Your Form](../ide/step-7-add-dialog-components-to-your-form.md) (Шаг 7. Добавление компонентов диалогового окна в форму).  
  
-   Предыдущий шаг руководства см. в разделе [Step 5: Add Controls to Your Form](../ide/step-5-add-controls-to-your-form.md) (Шаг 5. Добавление элементов управления в форму).