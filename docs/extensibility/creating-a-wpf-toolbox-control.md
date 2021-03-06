---
title: "Создание элемента управления панели элементов WPF | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox control
- toolbox
- wpf
ms.assetid: 9cc34db9-b0d1-4951-a02f-7537fbbb51ad
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c1a8338f0ebd964e5d039ffa8dff000a441523f8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="creating-a-wpf-toolbox-control"></a>Создание элемента управления панели элементов WPF
Шаблон элемента управления панели элементов WPF (Windows Presentation Framework) позволяет создавать элементы управления WPF, которые автоматически добавляются в **элементов** при установке расширения. В этом разделе показано, как использовать шаблон для создания **элементов** элемента управления, который можно передавать другим пользователям.  
  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-wpf-toolbox-control"></a>Создание элемента управления панели элементов WPF  
  
#### <a name="create-an-extension-with-a-wpf-toolbox-control"></a>Создайте расширение с элементом управления панели элементов WPF  
  
1.  Создайте проект VSIX с именем `MyToolboxControl`. Шаблон проекта VSIX в можно найти **новый проект** диалогового окна в разделе **Visual C# / Extensibility**.  
  
2.  При открытии проекта, добавьте **элемента управления панели элементов WPF** шаблон элемента с именем `MyToolboxControl`. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и выберите **добавить / новый элемент**. В **Добавление нового элемента** диалоговое окно, перейдите на **Visual C# / Extensibility** и выберите **элемента управления панели элементов WPF**. В **имя** в нижней части окна, измените имя файла команд для `MyToolboxControl.cs`.  
  
     Решение теперь содержит пользовательский элемент управления `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , добавляющий элемент управления **элементов**и **Microsoft.VisualStudio.ToolboxControl** запись актива в манифесте VSIX для  развертывание.  
  
#### <a name="to-create-the-control-ui"></a>Создание элемента управления пользовательского интерфейса  
  
1.  Откройте MyToolboxControl.xaml в конструкторе.  
  
     Конструкторе показан <xref:System.Windows.Controls.Grid> управления, содержащий <xref:System.Windows.Controls.Button> элемента управления.  
  
2.  Расположите макет сетки. При выборе <xref:System.Windows.Controls.Grid> синей панели отображаются на верхнего и левого краев сетки элемента управления. Щелкая столбцы можно добавить строки и столбцы в сетку.  
  
3.  Добавление дочерних элементов сетки. Можно расположить дочернего элемента управления, перетащив его из **элементов** в раздел сетки, или установив его `Grid.Row` и `Grid.Column` атрибуты в XAML. В следующем примере добавляется две метки в верхнюю строку сетки и кнопки на второй строке.  
  
    ```xaml  
    <Grid>  
        <Label Grid.Row="0" Grid.Column="0" Name="label1" />  
        <Label Grid.Row="0" Grid.Column="1" Name="label2" />  
        <Button Name="button1" Click="button1_Click" Grid.Row="1" Grid.ColumnSpan="2" />  
    </Grid>  
    ```  
  
## <a name="renaming-the-control"></a>Переименование элемента управления  
 По умолчанию элемент управления отображается в **элементов** как **MyToolboxControl** в группу с именем **MyToolboxControl.MyToolboxControl**. Можно изменить эти имена в файле MyToolboxControl.xaml.cs.  
  
1.  Откройте MyToolboxControl.xaml.cs в представлении кода.  
  
2.  Найдите класс MyToolboxControl и переименуйте его в TestControl. (Самый быстрый способ сделать это является переименование класса, выберите **переименование** в контекстном меню и выполнение действий. (Дополнительные сведения о **переименование** см. в разделе [Переименовать рефакторинг (C#)](../ide/reference/rename.md).)
  
3.  Последовательно выберите пункты `ProvideToolboxControl` атрибута и измените значение первого параметра в **теста**. Это имя группы, которая будет содержать элемент управления в **элементов**.  
  
     Итоговый код должен выглядеть следующим образом:  
  
    ```csharp  
    [ProvideToolboxControl("Test", true)]  
    public partial class TestControl : UserControl  
    {  
        public TestControl()  
        {  
            InitializeComponent();  
        }  
    }  
    ```  
  
## <a name="building-testing-and-deployment"></a>Сборка, тестирование и развертывание  
 При отладке проекта, необходимо найти элемент управления, установленные в **элементов** экспериментального экземпляра Visual Studio.  
  
#### <a name="to-build-and-test-the-control"></a>Сборка и тестирование элемента управления  
  
1.  Перестройте проект и начните отладку.  
  
2.  В новом экземпляре Visual Studio создайте проект приложения WPF. Убедитесь, что открыт в конструкторе XAML.  
  
3.  Найдите свой элемент управления в **панели элементов** и перетащите его в рабочую область конструирования.  
  
4.  Начните отладку приложения WPF.  
  
5.  Убедитесь, что отображается элемент управления.  
  
#### <a name="to-deploy-the-control"></a>Развертывание элемента управления  
  
1.  После сборки протестированного проекта VSIX-файл можно найти в папке \bin\debug\ проекта.  
  
2.  Его можно установить на локальном компьютере, дважды щелкните VSIX-файл и выполнив процедуру установки. Чтобы удалить элемент управления, используйте **средства / расширения и обновления** искать расширения элемента управления, а затем выберите **удаления**.  
  
3.  Отправьте VSIX-файл в сеть или на веб-сайт.  
  
     Если вы отправите файл на [коллекции Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) веб-сайта, другие пользователи могли использовать **средства / расширения и обновления** в Visual Studio для поиска элемента управления в сети и установить его.