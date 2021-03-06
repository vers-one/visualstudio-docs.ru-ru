---
title: "Пошаговое руководство. Создание простого приложения с помощью C# или Visual Basic | Документация Майкрософт"
ms.custom: 
ms.date: 10/03/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: b33816e074cf63826c931bcda0978ebdb5bb8bbe
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="walkthrough-create-a-simple-application-with-c-or-visual-basic"></a>Пошаговое руководство. Создание простого приложения с помощью C# или Visual Basic
Выполняя данное пошаговое руководство, вы ознакомитесь со многими инструментами, диалоговыми окнами и конструкторами, которые можно использовать для создания приложений с помощью Visual Studio. Вам предстоит создать простое приложение "Hello, World", разработать пользовательский интерфейс, добавить код и отладить ошибки, одновременно приобретая навыки работы в интегрированной среде разработки (IDE).
  
##  <a name="BKMK_ConfigureIDE"></a> Настройка интегрированной среды разработки (IDE)  
При первом запуске Visual Studio вам будет предложено выполнить вход. Для этого пошагового руководства делать это необязательно. Затем может появиться диалоговое окно, в котором предлагается выбрать параметры разработки и цветовую тему. Оставьте значения по умолчанию и нажмите **Запуск Visual Studio**.  

![Диалоговое окно выбора параметров](../ide/media/exploreide-settings.png "exploreide-settings")
  
После запуска Visual Studio вы увидите окна инструментов, меню и панели инструментов, а также основную область окна. Окна инструментов закреплены в левой и правой частях окна приложения, а панель **Быстрый запуск**, строка меню и стандартная панель инструментов закреплены в верхней его части. В центре окна приложения находится **Начальная страница**. При загрузке решения или проекта редакторы и конструкторы отображаются в области **Начальной страницы** . При разработке приложения чаще всего используется именно эта область.  
  
![Интегрированная среда разработки, в которой установлены общие параметры](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-IDEwithgeneralsettings")  
  
##  <a name="BKMK_CreateApp"></a> Создание простого приложения  
  
### <a name="create-the-project"></a>Создание проекта  
При создании приложения в Visual Studio необходимо сначала создать проект и решение. Этот пример демонстрирует создание проекта Windows Presentation Foundation (WPF).  
  
#### <a name="to-create-the-wpf-project"></a>Создание проекта WPF  
  
1.  Создайте новый проект. В строке меню выберите **Файл**, **Создать**, **Проект...**.  
  
     ![Выбор пунктов "Файл", "Создать", "Проект"](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")  
  
2.  Выберите шаблон приложения WPF Visual Basic или Visual C#, например, выбрав в левой области **Установленные**, **Visual C#**, **Классический рабочий стол Windows**, а затем выбрав **Приложение WPF (.NET Framework)** в средней области.  В нижней части диалогового окна нового проекта назовите проект HelloWPFApp.  
  
     ![Создание проекта WPF C# с именем HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")  
  
Visual Studio создает решение и проект HelloWPFApp, а в **обозревателе решений** выводятся различные файлы. Конструктор WPF отображает представление кода и представление XAML MainWindow.xaml в представлении с разделением. Сдвигая разделитель, можно делать любое из представлений больше или меньше.  Можно выбрать для просмотра только визуальное представление или только представление XAML. (Дополнительные сведения см. в разделе [Конструктор WPF для разработчиков Windows Forms](http://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca).) В **Обозревателе решений**отображаются следующие элементы.  
  
![Обозреватель решений с добавленными файлами HelloWPFApp](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")  
  
После создания проекта его можно настраивать. С помощью окна **Свойства** (в меню **Вид** ) можно отображать и изменять параметры элементов проекта, элементов управления и других элементов в приложении.  
  
#### <a name="to-change-the-name-of-mainwindowxaml"></a>Изменение имени MainWindow.xaml  
Давайте присвоим файлу MainWindow более конкретное имя.  

1. В **Обозревателе решений**выберите файл MainWindow.xaml. Должно появиться окно **Свойства**, но если его нет, выберите в меню **Вид** пункт **Окно свойств**.  
2. Измените значение свойства **Имя файла** на `Greetings.xaml`.  
  
     ![Окно свойств с выделенным именем файла](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-FilenameinPropertiesWindow")  
  
     В **обозревателе решений** видно, что файл теперь имеет имя Greetings.xaml, а имя вложенного файла кода поменялось на Greetings.xaml.vb или Greetings.xaml.cs. Этот файл с текстом программы вложен в узел файла XAML, что означает их тесную связь.  
  
### <a name="design-the-user-interface-ui"></a>Конструирование пользовательского интерфейса (ИП)  
В приложение будет добавлено три типа элементов управления: элемент управления TextBlock, два элемента управления RadioButton, и элемент управления Button.  
  
#### <a name="to-add-a-textblock-control"></a>Добавление элемента управления TextBlock  
  
1.  Откройте окно **Панель элементов** , выбрав в меню **Вид** пункт **Панель элементов** .  
  
2.  В окне **Панель элементов** разверните узел **Типовые элементы управления WPF**, чтобы увидеть элемент управления TextBlock.  
  
     ![Панель элементов с выделенным элементом управления TextBlock](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-TextBlockToolbox")  
  
3.  Добавьте элемент управления TextBlock в область конструктора, выбрав элемент управления **TextBlock** и перетащив его в окно. Отцентрируйте этот элемент в верхней части окна.  
  
Окно должно выглядеть так, как показано на следующем рисунке:  
  
![Элемент управления TextBlock в форме Greetings](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-GreetingswithTextblockonly")  
  
Разметка XAML должна выглядеть приблизительно так, как показано ниже:  
  
```xaml  
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>  
```  

#### <a name="to-customize-the-text-in-the-text-block"></a>Настройка текста в текстовом блоке  
  
1.  В представлении XAML найдите разметку для TextBlock и измените атрибут Text:  

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```  
  
2.  При необходимости снова разместите элемент TextBlock по центру и сохраните изменения, нажав клавиши **CTRL+S** или выбрав пункт в меню **Файл**.  
  
Следующий шаг — добавить в форму два элемента управления [RadioButton](/dotnet/framework/wpf/controls/radiobutton).  
  
#### <a name="to-add-radio-buttons"></a>Добавление переключателей  
  
1.  На **панели элементов** найдите элемент управления **RadioButton**.  
  
     ![Окно панели элементов с выбранным элементом управления RadioButton](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")  
  
2.  Добавьте два элемента управления RadioButton в область конструктора, выбрав элемент **RadioButton** и перетащив его в область конструктора. Переместите кнопки (выбрав их и используя клавиши со стрелками), чтобы кнопки отображались рядом под элементом управления TextBlock.  
  
     Окно должно выглядеть следующим образом:  
  
     ![Форма Greetings с блоком текста и двумя переключателями](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Greetingswithradiobuttons")  
  
3.  В окне **Свойства** для левого элемента управления RadioButton измените свойство **Имя** (свойство в верхней части окна **Свойства**), присвоив ему значение **HelloButton**.  

     ![Окно свойств RadioButton](../ide/media/exploreide-buttonproperties.png "exploreide-buttonproperties")  
  
4.  В окне **Свойства** правого элемента управления RadioButton измените значение свойства **Имя** на **GoodbyeButton**, а затем сохраните изменения.  
  
Теперь можно добавить отображаемый текст для каждого элемента управления RadioButton. Следующая процедура обновляет свойство **Content** элемента управления RadioButton.  
  
#### <a name="to-add-display-text-for-each-radio-button"></a>Добавление отображаемого текста для каждого переключателя  
  
1.  В области конструктора откройте контекстное меню элемента управления HelloButton, щелкнув его правой кнопкой мыши, выберите команду **Изменить текст**, а затем введите "Hello".  
  
2.  Откройте контекстное меню элемента управления GoodbyeButton, щелкнув его правой кнопкой мыши, выберите команду **Изменить текст**, а затем введите "Goodbye".  

### <a name="to-set-a-radio-button-to-be-checked-by-default"></a>Задание переключателя, выбранного по умолчанию  
В этом шаге мы настроим элемент HelloButton как выбранный по умолчанию, чтобы всегда был выбран один из переключателей.  

В представлении XAML найдите разметку для элемента HelloButton и добавьте атрибут **IsChecked**:

```xaml
IsChecked="True"
```  

Последний элемент пользовательского интерфейса, который вам предстоит добавить, — это [Button](/dotnet/framework/wpf/controls/button).  
  
#### <a name="to-add-the-button-control"></a>Добавление элемента управления Button  
  
1.  На **панели элементов** найдите элемент управления **Button** и добавьте его в область конструктора под элементами управления RadioButton, перетащив его на форму в представлении конструирования.  
  
2.  В представлении XAML измените значение свойства **Содержимое** элемента управления Button с `Content="Button"` на `Content="Display"` и сохраните изменения.  
  
     Разметка должна быть аналогична разметке, приведенной в следующем примере:  
     `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`  
  
     Окно должно выглядеть так, как показано на следующем рисунке.  
  
     ![Форма Greetings с метками элементов управления](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Greetingswithconrollabels")  
  
### <a name="add-code-to-the-display-button"></a>Добавление кода к кнопке Display  
После запуска приложения окно сообщения появится только тогда, когда пользователь выберет переключатель, а затем нажмет кнопку **Display**. Одно окно сообщения появится для Hello, и другое — для Goodbye. Для создания такого поведения добавьте код в событие Button_Click в файле Greetings.xaml.vb или Greetings.xaml.cs.  
  
#### <a name="add-code-to-display-message-boxes"></a>Добавление кода для отображения окон сообщений    
1.  На поверхности разработки дважды щелкните кнопку **Display** .  
  
     Будет открыт файл Greetings.xaml.vb или Greetings.xaml.cs, а курсор будет установлен в событии Button_Click. 
  
    ```vb  
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)  
  
    End Sub  
    ```    
    ```csharp  
    private void Button_Click_1(object sender, RoutedEventArgs e)  
    {  
  
    }  
    ```  
  
2.  Введите следующий код:  
  
    ```vb  
    If HelloButton.IsChecked = True Then  
        MessageBox.Show("Hello.")  
    ElseIf GoodbyeButton.IsChecked = True Then 
        MessageBox.Show("Goodbye.")  
    End If  
  
    ```    
    ```csharp  
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```  
  
3.  Сохраните приложение.  
  
##  <a name="BKMK_DebugTest"></a> Отладка и тестирование приложения  
После этого вам предстоит отладить приложение для выявления ошибок и тестирования того, что оба окна сообщений отображаются правильно. Приведенные ниже инструкции описывают, как выполнить сборку и запустить отладчик (дополнительные сведения см. в разделах [Building a WPF Application (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) (Построение приложения WPF) и [Debugging WPF](../debugger/debugging-wpf.md) ).  
  
### <a name="find-and-fix-errors"></a>Поиск и исправление ошибок  
В этом шаге вам предстоит найти ошибку, которую мы намеренно допустили ранее, изменив имя файла MainWindow.xaml.  
  
#### <a name="to-start-debugging-and-find-the-error"></a>Начало отладки и поиск ошибки  
  
1.  Запустите отладчик, выбрав **Отладка**, затем **Начать отладку**.  
  
     ![Команда "Начать отладку" в меню "Отладка"](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")  
  
     Появится окно **Режим приостановки выполнения**, а в окне **Вывод** будет указано, что произошло исключение IOException: "Не удается найти ресурс mainwindow.xaml".  
  
2.  Остановите отладчик, выбрав в меню **Отладка** пункт **Остановить отладку**.  
  
     ![Команда "Остановить отладку" в меню "Отладка"](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")  
  
Файл MainWindow.xaml был переименован в Greetings.xaml в начале этого пошагового руководства, но код по-прежнему ссылается на файл mainwindow.xaml как на начальный универсальный код ресурса (URI) для приложения, поэтому проект не может быть запущен.  
  
#### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Задание Greetings.xaml в качестве начального универсального кода ресурса (URI)  
  
1.  В **обозревателе решений** откройте файл App.xaml (в проекте C#) или файл Application.xaml (в проекте Visual Basic).  
  
2.  Измените `StartupUri="MainWindow.xaml"` на `StartupUri="Greetings.xaml"` и сохраните изменения.  
  
Запустите отладчик снова (клавишей **F5**). Должно появиться окно Greetings приложения. Теперь закройте окно приложения, чтобы остановить отладку.  
  
### <a name="to-debug-with-breakpoints"></a>Отладка с точками останова  
Добавив точки останова, можно тестировать код во время отладки. Точки останова можно добавлять, выбирая в меню **Отладка** пункт **Точка останова**, щелкая в левом поле редактора рядом со строкой кода, в которой требуется приостановить выполнение, или нажимая клавишу **F9**.  
  
#### <a name="to-add-breakpoints"></a>Добавление точек останова  
  
1.  Откройте файл Greetings.xaml.vb или Greetings.xaml.cs и выделите следующею строку: `MessageBox.Show("Hello.")`  
  
2.  Добавьте точку останова, выбрав меню **Отладка**, затем — **Точка останова**.  
  
     ![Команда "Точка останова" в меню "Отладка"](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")  
  
     Рядом со строкой кода в крайнем левом поле окна редактора появится красный кружок.  
  
3.  Выделите следующую строку: `MessageBox.Show("Goodbye.")`.  
  
4.  Нажмите клавишу **F9**, чтобы добавить точку останова, а затем нажмите клавишу **F5**, чтобы начать отладку.  
  
5.  В окне **Greetings** выберите переключатель **Hello** и нажмите кнопку **Display** .  
  
     Строка `MessageBox.Show("Hello.")` выделяется желтым цветом. В нижней части интегрированной среды разработки окна «Видимые», «Локальные» и «Контрольные значения» закреплены вместе на левой стороне, а окна «Стек вызовов», «Точки останова», «Команда», «Интерпретация» и окно вывода закреплены вместе на правой стороне.  
  
6.  В меню **Отладка**выберите **Шаг с выходом**.  
  
     Приложение возобновит выполнение, и появится окно сообщения со словом "Hello".  
  
7.  Нажмите кнопку **ОК** в окне сообщения, чтобы закрыть его.  
  
8.  В окне **Greetings** выберите переключатель **Goodbye** и нажмите кнопку **Display** .  
  
     Строка `MessageBox.Show("Goodbye.")` выделяется желтым цветом.  
  
9. Нажмите клавишу **F5**, чтобы продолжить отладку. Когда появится окно сообщения, нажмите в нем кнопку **ОК** , чтобы закрыть его.  
  
10. Закройте окно приложения, чтобы остановить отладку.  
  
11. В меню **Отладка**выберите **Выключить все точки останова**.  
  
### <a name="build-a-release-version-of-the-application"></a>Сборка окончательной версии приложения  
 Теперь, когда вы проверили, что все работает, можно подготовить окончательную сборку приложения.  
  
#### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Очистка файлов решения и сборка окончательной версии  
  
1.  Выберите в главном меню **Сборка**, **Очистить решение** для удаления промежуточных файлов и выходных файлов, которые были созданы в ходе предыдущих сборок. Это не является обязательным, но очищает результаты отладочной сборки.  
  
     ![Команда "Очистить решение" в меню "Сборка"](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")  
  
2.  Измените конфигурацию сборки для HelloWPFApp с **Отладка** на **Выпуск** с помощью раскрывающегося списка на панели инструментов (сейчас это "Отладка").  
  
     ![Панель инструментов "Стандартная" с выбранной конфигурацией "Выпуск"](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")  
  
3.  Выполните сборку решения, выбрав **Сборка**, а затем **Собрать решение**.  
  
     ![Команда "Собрать решение" в меню "Сборка"](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")  
  
Поздравляем с завершением этого пошагового руководства! Построенный EXE-файл находится в каталоге решения и проекта (...\HelloWPFApp\HelloWPFApp\bin\Release\\). Чтобы изучить больше примеров, см. раздел [Visual Studio Samples](../ide/visual-studio-samples.md).  
  
## <a name="see-also"></a>См. также
[Новые возможности Visual Studio 2017](../ide/whats-new-in-visual-studio.md)   
[Начало разработки в Visual Studio](../ide/get-started-developing-with-visual-studio.md)   
[Советы по повышению производительности](../ide/productivity-tips-for-visual-studio.md)