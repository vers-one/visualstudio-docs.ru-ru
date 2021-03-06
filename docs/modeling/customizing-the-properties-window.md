---
title: "Настройка окна свойств | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 545c8181cdaa3f13d2de04f13101d2678f9fd0ab
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-the-properties-window"></a>Настройка окна свойств
Можно настроить внешний вид и поведение окна свойств в доменный язык (DSL) в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. В определении DSL определить свойства домена для каждого класса домена. По умолчанию при выборе экземпляра класса на схеме или в обозревателе моделей, каждое свойство домена указывается в окне «Свойства». Это позволяет просмотреть и изменить значения свойств домена, даже если они не были сопоставлены для полей фигур на схеме.  
  
## <a name="names-descriptions-and-categories"></a>Имена, описания и категории  
 **Имя и отображаемое имя**. В определении свойства домена отображаемое имя свойства является имя, которое отображается во время выполнения в окне «Свойства». В отличие от этого имя используется при написании кода программы для обновления свойства. Имя должно быть правильно буквенно-цифровое имя среды CLR, но отображаемое имя может содержать пробелы.  
  
 При установке имени свойства в определения DSL его отображаемое имя автоматически присваивается имя копии. При написании регистром имя языка Pascal, например «FuelGauge», отображаемое имя автоматически будет содержать пробел: «Топливо датчика». Тем не менее можно явно задать отображаемое имя с другим значением.  
  
 **Описание**. Описание свойства домена отображается в двух местах:  
  
-   В нижней части окна свойств, когда пользователь выбирает свойство. Он используется для объяснить пользователю представляет свойство.  
  
-   В код, созданный программой. При использовании средства документации для получения документации по API, он будет отображаться как описание этого свойства в API.  
  
 **Категория**. Категория — заголовок окна "Свойства".  
  
## <a name="exposing-style-features"></a>Предоставление доступа к функции стиля  
 Некоторые средства динамического графические элементы могут быть представлены или *предоставляется* как свойства домена. Это компонент, который был предоставлен таким образом можно обновить пользователем и могут более легко обновляться, программным кодом.  
  
 Щелкните правой кнопкой мыши фигуру класса в определение DSL, укажите **добавьте предоставляется**и выберите компонент.  
  
 На фигурах можно предоставлять **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** и **FillGradientMode** свойства. О соединителях можно предоставлять **цвет**`,`**TextColor**, **DashStyle**, и **толщину** свойства. На схемах можно предоставлять **FillColor** и **TextColor** свойства.  
  
## <a name="forwarding-displaying-properties-of-related-elements"></a>Перенаправление: Отображение свойств связанных элементов  
 Когда пользователь DSL выбирает элемент в модели, свойства этого элемента отображаются в окне «Свойства». Тем не менее можно также отобразить свойства указанного связанных элементов. Это полезно, если вы определили группу элементов, который работает как единое целое. Например можно определить основной и дополнительный элемент подключаемого модуля. Если это основной элемент сопоставляется с формой, а другой — нет, полезно просмотреть все их свойства, как если бы они находились в одном элементе.  
  
 Этот эффект называется *пересылки свойство*, и в некоторых случаях это происходит автоматически. В других случаях можно добиться свойство пересылки, определив дескриптор типа домена.  
  
### <a name="default-property-forwarding-cases"></a>По умолчанию свойство пересылки вариантов  
 При выборе фигуры или соединителя или элемент в проводнике, в окне «Свойства» отображаются следующие свойства:  
  
-   Свойства домена, которые определены в классе домена элемента модели, включая те, которые определены в базовых классах. Исключение составляют свойства домена, для которых установлены **является отображаемым** для `False`.  
  
-   Имена элементов, связанные через связи с кратностью от 0 до 1. Это обеспечивает удобный способ просмотра при необходимости связанные элементы, даже если сопоставление соединитель для связи не определены.  
  
-   Свойства домена внедрения отношение, которое обращается к элементам. Поскольку внедрение связи обычно не отображаются явным образом, это позволяет пользователю видеть их свойства.  
  
-   Свойства домена, определенные для выбранной фигуры или соединителя.  
  
### <a name="adding-property-forwarding"></a>Добавление свойства пересылки  
 Чтобы переслать свойство, определить дескриптор типа домена. При наличии доменной связи между двумя классами домена дескриптор типа домена можно использовать для задания свойства домена в первом классе значение свойства домена во втором классе домена. Например, если у вас есть связь между **книги** класса домена и **автор** домена, можно использовать дескриптор типа домена делать **имя** свойство Книга создана **автор** отображаются в окне «Свойства», когда пользователь выбирает книги.  
  
> [!NOTE]
>  Свойство пересылки влияет на окне свойств, если пользователь редактирует модели. Он не определяет свойство домена на принимающего класса. Если вы хотите получить доступ к свойству перенаправленных домена в других частях определения DSL или в программном коде, для доступа к элемент пересылки.  
  
 В следующей процедуре предполагается, что вы создали DSL. Первые несколько шаги приведены необходимые компоненты.  
  
##### <a name="to-forward-a-property-from-another-element"></a>Для перенаправления из другого элемента, свойство  
  
1.  Создание [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] решение, которое содержит по крайней мере два класса, называемых в этом примере **книги** и **автор**. Должно существовать отношение вида между **книги** и **автор**.  
  
     Кратность исходной роли (роль в **книги** стороне) должно быть от 0 до 1 или 1.. 1, таким образом, каждая из которых **книги** имеет один **автор**.  
  
2.  В **обозреватель DSL**, щелкните правой кнопкой мыши **книги** класса домена, а затем щелкните **добавьте новый DomainTypeDescriptor**.  
  
     Узел с именем **пути для настраиваемых дескрипторы свойств** отображается под **пользовательский дескриптор типа** узла.  
  
3.  Щелкните правой кнопкой мыши **пользовательский дескриптор типа** , а затем щелкните **добавьте новый PropertyPath**.  
  
     Отображается новый путь к свойству **пути для настраиваемых дескрипторы свойств** узла.  
  
4.  Выберите новый путь к свойству и в **свойства** задайте **путь к свойству** в путь элемента соответствующие модели.  
  
     Можно изменить путь в виде дерева, щелкнув стрелку вниз справа от этого свойства. Дополнительные сведения о путях домена см. в разделе [синтаксис пути домена](../modeling/domain-path-syntax.md). После изменения его пути должен выглядеть **BookReferencesAuthor.Author/! Автор**.  
  
5.  Задать **свойство** для **имя** свойство домена **автор**.  
  
6.  Задать **отображаемое имя** для **создавать имя**.  
  
7.  Преобразовать все шаблоны, постройте и запустите DSL.  
  
8.  В схеме модели создать книгу автора и свяжите их с помощью ссылочная связь. Выбор элемента книги, в окне свойств отобразится имя автора наряду со свойствами книги. Измените имя связанного автора или связать с другим именем книги и обратите внимание, что изменяется имя автора книги.  
  
## <a name="custom-property-editors"></a>Пользовательские редакторы свойств  
 В окне свойств предоставляет используемого по умолчанию, редакторов для типа свойства каждого домена. Например для перечисляемого типа, пользователь видит раскрывающегося списка и числовые свойства, пользователь может ввести цифр. Это верно только для встроенных типов. При указании внешнего типа пользователь будет иметь возможность видеть значения этого свойства, но не изменять.  
  
 Тем не менее можно указать следующие типы и редакторы:  
  
1.  Другой редактор, используемый с стандартного типа. Например можно указать в редакторе пути файла для строкового свойства.  
  
2.  Внешний тип для свойства домена и редактор для него.  
  
3.  В редакторе .NET, например Редактор пути файла, или можно создать собственные настраиваемые свойства редактор.  
  
     Преобразование между внешнего типа и типа, такие как строки, которая имеет редактор по умолчанию.  
  
 В доменный язык DSL *внешнего типа* является любым типом, не является одним из простых типов (например, логическое значение или Int32) или строкой.  
  
#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Для определения свойства домена, который имеет внешний тип  
  
1.  В **обозревателе решений**, добавьте ссылку на сборку (DLL), содержащую внешний тип в **Dsl** проекта.  
  
     Сборка может быть сборкой .NET или сборку, предоставленные пользователем.  
  
2.  Добавьте тип для **типы доменов** списка, если вы еще.  
  
    1.  Откройте DslDefinition.dsl и в **обозреватель DSL**, щелкните правой кнопкой мыши корневой узел и нажмите кнопку **добавить новый внешний тип**.  
  
         В списке появится новый элемент **типы доменов** узла.  
  
        > [!WARNING]
        >  Элемент меню не на корневом узле DSL, **типы доменов** узла.  
  
    2.  В окне «Свойства» можно задайте имя и пространство имен для нового типа.  
  
3.  Добавление класса домена свойства домена в обычном режиме.  
  
     В окне «Свойства» выберите внешний тип из раскрывающегося списка в **типа** поля.  
  
 На этом этапе пользователи могут просматривать значения свойства, но их нельзя изменить. Отображаемые значения извлекаются из `ToString()` функции. Можно написать программный код, который задает значение свойства, например в команде или правило.  
  
### <a name="setting-a-property-editor"></a>Настройка редактора свойств  
 Добавьте атрибут CLR свойства домена в следующем формате:  
  
```  
[System.ComponentModel.Editor (  
   typeof(AnEditor),  
   typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Атрибут можно задать для свойства с помощью **пользовательский атрибут** запись в окне «Свойства».  
  
 Тип `AnEditor` должен быть производным от типа, указанного в качестве второго параметра. Второй параметр должен быть либо <xref:System.Drawing.Design.UITypeEditor> или <xref:System.ComponentModel.ComponentEditor>. Дополнительные сведения см. в разделе <xref:System.ComponentModel.EditorAttribute>.  
  
 Можно указать собственный редактор или редактор в [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], такие как <xref:System.Windows.Forms.Design.FileNameEditor> или <xref:System.Drawing.Design.ImageEditor>. Например используйте следующую процедуру в свойств, в котором пользователь может ввести имя файла.  
  
##### <a name="to-define-a-file-name-domain-property"></a>Для определения свойства домена имя файла  
  
1.  Добавление класса домена в определение DSL свойством домена.  
  
2.  Выберите новое свойство. В **пользовательский атрибут** поле в окне «Свойства», введите следующий атрибут. Чтобы ввести этот атрибут, нажмите кнопку с многоточием **[...]**  и введите имя атрибута, а также параметры отдельно:  
  
    ```  
    [System.ComponentModel.Editor (  
       typeof(System.Windows.Forms.Design.FileNameEditor)  
       , typeof(System.Drawing.Design.UITypeEditor))]  
  
    ```  
  
3.  Оставьте настройки по умолчанию для типа свойства домена **строка**.  
  
4.  Тестирование редактора, убедитесь, что пользователи могут открыть редактор имя файла для редактирования свойства домена.  
  
    1.  Нажмите клавиши CTRL + F5 или F5. В решении отладки откройте файл теста. Создайте элемент класса домена и выберите его.  
  
    2.  В окне «Свойства» установите свойство домена. В этом поле значение отображается многоточие **[...]** .  
  
    3.  Нажмите кнопку с многоточием. Появится диалоговое окно файла. Выберите файл и закройте диалоговое окно. Путь к файлу теперь является значением свойства домена.  
  
### <a name="defining-your-own-property-editor"></a>Определение собственный редактор свойств  
 Можно определить собственный редактор. Это делается разрешения пользователю, чтобы изменить тип, который определен или изменение стандартного типа особым образом. Например можно разрешить пользователю вводить строку, представляющую формулы.  
  
 Редактор определяется путем написания класса, который является производным от <xref:System.Drawing.Design.UITypeEditor>. Ваш класс должен переопределять:  
  
-   <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, для взаимодействия с пользователем и обновите значение свойства.  
  
-   <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, чтобы указать, будет открыть диалоговое окно или укажите раскрывающееся меню редактора.  
  
 Можно также обеспечивают графическое представление значения этого свойства, которое будет отображаться в сетке свойств. Чтобы сделать это, переопределите `GetPaintValueSupported`, и `PaintValue`.  Дополнительные сведения см. в разделе <xref:System.Drawing.Design.UITypeEditor>.  
  
> [!NOTE]
>  Добавьте код в отдельном файле кода в **Dsl** проекта.  
  
 Пример:  
  
```  
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor  
{  
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)  
  {  
    base.InitializeDialog(openFileDialog);  
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";  
    openFileDialog.Title = "Select a text file";  
  }  
}  
  
```  
  
 Чтобы использовать этот редактор, установите **пользовательский атрибут** свойства домена:  
  
```  
[System.ComponentModel.Editor (  
   typeof(MyNamespace.TextFileNameEditor)  
   , typeof(System.Drawing.Design.UITypeEditor))]  
  
```  
  
 Дополнительные сведения см. в разделе <xref:System.Drawing.Design.UITypeEditor>.  
  
## <a name="providing-a-drop-down-list-of-values"></a>Предоставляет список раскрывающегося списка значений  
 Можно предоставить список значений, пользователь может выбрать.  
  
> [!NOTE]
>  Этот метод предоставляет список значений, которые могут измениться во время выполнения. Если вы хотите предоставить список, который не изменяется, рекомендуется вместо использование перечисляемого типа в качестве типа свойства домена.  
  
 Чтобы задать список стандартных значений, необходимо добавить свойство домена атрибут CLR, который имеет следующий вид:  
  
```  
[System.ComponentModel.TypeConverter   
(typeof(MyTypeConverter))]  
  
```  
  
 Определите класс, производный от класса <xref:System.ComponentModel.TypeConverter>. Добавьте код в отдельном файле в **Dsl** проекта. Пример:  
  
```csharp  
/// <summary>  
/// Type converter that provides a list of values   
/// to be displayed in the property grid.  
/// </summary>  
/// <remarks>This type converter returns a list   
/// of the names of all "ExampleElements" in the   
/// current store.</remarks>  
public class MyTypeConverter : System.ComponentModel.TypeConverter  
{  
  /// <summary>  
  /// Return true to indicate that we return a list of values to choose from  
  /// </summary>  
  /// <param name="context"></param>  
  public override bool GetStandardValuesSupported  
    (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Returns true to indicate that the user has   
  /// to select a value from the list  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>If we returned false, the user would   
  /// be able to either select a value from   
  /// the list or type in a value that is not in the list.</returns>  
  public override bool GetStandardValuesExclusive  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    return true;  
  }  
  
  /// <summary>  
  /// Return a list of the values to display in the grid  
  /// </summary>  
  /// <param name="context"></param>  
  /// <returns>A list of values the user can choose from</returns>  
  public override StandardValuesCollection GetStandardValues  
      (System.ComponentModel.ITypeDescriptorContext context)  
  {  
    // Try to get a store from the current context  
    // "context.Instance"  returns the element(s) that   
    // are currently selected i.e. whose values are being  
    // shown in the property grid.   
    // Note that the user could have selected multiple objects,   
    // in which case context.Instance will be an array.  
    Store store = GetStore(context.Instance);  
  
    List<string> values = new List<string>();  
  
    if (store != null)  
    {  
      values.AddRange(store.ElementDirectory  
        .FindElements<ExampleElement>()  
        .Select<ExampleElement, string>(e =>   
      {  
        return e.Name;  
      }));  
    }  
    return new StandardValuesCollection(values);  
  }  
  
  /// <summary>  
  /// Attempts to get to a store from the currently selected object(s)  
  /// in the property grid.  
  /// </summary>  
  private Store GetStore(object gridSelection)  
  {  
    // We assume that "instance" will either be a single model element, or   
    // an array of model elements (if multiple items are selected).  
  
    ModelElement currentElement = null;  
  
    object[] objects = gridSelection as object[];  
    if (objects != null && objects.Length > 0)  
    {  
      currentElement = objects[0] as ModelElement;  
    }  
    else  
    {  
        currentElement = gridSelection as ModelElement;  
    }  
  
    return (currentElement == null) ? null : currentElement.Store;  
  }  
  
}  
  
```  
  
## <a name="see-also"></a>См. также  
 [Перемещение по модели и обновление модели в коде программы](../modeling/navigating-and-updating-a-model-in-program-code.md)