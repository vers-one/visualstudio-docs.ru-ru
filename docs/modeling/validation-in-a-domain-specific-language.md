---
title: "Проверка доменного языка | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7eb2e734bd94608584ca700223fb75387eb484fb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="validation-in-a-domain-specific-language"></a>Проверка в доменных языках
Автор доменного языка может определить ограничения проверки, позволяющие контролировать полноценность созданной пользователем модели. Например, если доменный язык позволяет рисовать генеалогическое дерево людей и их предков, можно написать ограничения, согласно которым даты рождения детей должны быть позже дат рождения родителей.  
  
 Вы можете выполнять при сохранении модели, когда он открыт, а также когда пользователь явно запускает проверочные ограничения **проверки** команду меню. Также можно выполнять проверку с помощью другого элемента управления программы. Например, можно выполнять проверку в ответ на изменение в значении или отношении свойства.  
  
 Проверка особенно важна при написании текстовых шаблонов или другие средства, обработка моделей пользователей. Проверка гарантирует, что модели удовлетворяют предусловиям, указанным в этих инструментах.  
  
> [!WARNING]
>  Также можно определить ограничения проверки в отдельных расширениях доменного языка вместе с командами меню расширения и обработчиками жестов. Пользователи могут выбрать установку таких расширений в дополнение к доменному языку. Дополнительные сведения см. в разделе [расширение доменного языка с помощью MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
## <a name="running-validation"></a>Запуск проверки  
 Когда пользователь редактирует модель, т. е. экземпляр доменного языка, запустить проверку могут следующие действия.  
  
-   Щелкните правой кнопкой мыши на диаграмме и выберите **проверки всех**.  
  
-   Щелкните правой кнопкой мыши верхний узел в обозревателе DSL и выберите **все проверки**  
  
-   Сохранение модели.  
  
-   Открытие модели.  
  
-   Кроме этого, можно написать программный код, который запускает проверку, например как часть команды меню или в ответ на изменения.  
  
 Все ошибки проверки будет отображаться в **список ошибок** окна. Пользователь может дважды щелкнуть сообщение об ошибке, чтобы выбрать элементы модели, вызвавшие ошибку.  
  
## <a name="defining-validation-constraints"></a>Определение ограничений проверки  
 Можно определить ограничения проверки, добавив методы проверки к классам доменов или отношениям DSL. Когда проверка запускается пользователем или с помощью элемента управления программой, выполняются некоторые или все методы проверки. Каждый метод применяется к каждому экземпляру своего класса, причем в каждом классе может быть несколько методов проверки.  
  
 Для каждого метода проверки создается отчет об обнаруженных ошибках.  
  
> [!NOTE]
>  Методы проверки создают отчеты об ошибках, но не изменяют модель. Если вы хотите настроить или предотвращать внесение определенных изменений см. в разделе [альтернативы проверки](#alternatives).  
  
#### <a name="to-define-a-validation-constraint"></a>Определение ограничений проверки  
  
1.  Включить проверку в **Editor\Validation** узла:  
  
    1.  Откройте **Dsl\DslDefinition.dsl**.  
  
    2.  В обозревателе DSL разверните **редактор** , а затем выберите **проверки**.  
  
    3.  В окне свойств задайте **использует** свойства `true`. Лучше всего задать все эти свойства.  
  
    4.  Нажмите кнопку **преобразовать все шаблоны** в панели инструментов обозревателя решений.  
  
2.  Напишите определения разделяемого класса для одного или нескольких классов доменов или доменных связей. Запись в файл кода в этих определений **Dsl** проекта.  
  
3.  Снабдите каждый класс префиксом в виде следующего атрибута:  
  
    ```csharp  
    [ValidationState(ValidationState.Enabled)]  
    ```  
  
    -   По умолчанию этот атрибут будет включать проверку для производных классов. Если требуется отключить проверку для определенного производного класса, можно использовать `ValidationState.Disabled`.  
  
4.  Добавьте методы проверки к классам. Каждый метод проверки может иметь любое имя и только один параметр типа <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.  
  
     Ему должен предшествовать один или несколько атрибутов `ValidationMethod`:  
  
    ```csharp  
    [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]  
    ```  
  
     ValidationCategories указывается, когда метод выполняется.  
  
 Например:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
// Allow validation methods in this class:  
[ValidationState(ValidationState.Enabled)]  
// In this DSL, ParentsHaveChildren is a domain relationship  
// from Person to Person:  
public partial class ParentsHaveChildren  
{  
  // Identify the method as a validation method:  
  [ValidationMethod  
  ( // Specify which events cause the method to be invoked:  
    ValidationCategories.Open // On file load.  
  | ValidationCategories.Save // On save to file.  
  | ValidationCategories.Menu // On user menu command.  
  )]  
  // This method is applied to each instance of the   
  // type (and its subtypes) in a model:   
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // In this DSL, the role names of this relationship  
    // are "Child" and "Parent":   
     if (this.Child.BirthYear < this.Parent.BirthYear   
        // Allow user to leave the year unset:  
        && this.Child.BirthYear != 0)  
      {  
        context.LogError(  
             // Description:  
                       "Child must be born after Parent",  
             // Unique code for this error:  
                       "FAB001ParentBirthError",   
              // Objects to select when user double-clicks error:  
                       this.Child,   
                       this.Parent);  
    }  
  }  
```  
  
 Об этом коде необходимо помнить следующее.  
  
-   Можно добавлять методы проверки к классам доменов или доменным связям. Код для этих типов находится в **Dsl\Generated Code\Domain\*.cs**.  
  
-   Каждый метод проверки применяется к каждому экземпляру его класса и подклассов. В случае доменной связи каждый экземпляр является связью между двумя элементами модели.  
  
-   Методы проверки применяются без соблюдения какого-либо порядка. То же самое относится и к применению каждого метода к экземплярам его класса.  
  
-   Не рекомендуется обновлять содержимое хранилища с помощью метода проверки, так как это может привести к недостоверным результатам. Вместо этого метод должен создать отчет об ошибке с помощью вызова `context.LogError`, `LogWarning` или `LogInfo`.  
  
-   В вызове LogError можно предоставить список элементов модели или ссылок отношений, которые будут выбраны, когда пользователь дважды щелкнет сообщение об ошибке.  
  
-   Сведения о чтении модели в программном коде см. в разделе [перехода и обновления модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Пример применяется к представленной ниже модели домена. Отношение ParentsHaveChildren имеет роли, которые называются Child и Parent.  
  
 ![Схема определения DSL &#45; Модель семейного дерева](../modeling/media/familyt_person.png "FamilyT_Person")  
  
## <a name="validation-categories"></a>Категории проверки  
 В атрибуте <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> можно указать, когда метод проверки должен быть выполнен.  
  
|Категория|Выполнение|  
|--------------|---------------|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Когда пользователь вызывает команду меню "Проверка".|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Когда открывается файл модели.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Когда сохраняется файл модели. При наличии ошибок проверки пользователю предлагается отменить или сохранить операцию.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Когда сохраняется файл модели. При наличии ошибок из-за методов в этой категории пользователь предупреждается о том, что повторное открытие файла может быть невозможно.<br /><br /> Используйте данную категорию для методов проверки, которые проверяют дубликаты имен или идентификаторов или другие условия, способные вызвать ошибки загрузки.|  
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Когда вызывается метод ValidateCustom. Проверки в этой категории могут быть вызваны только из кода программы.<br /><br /> Дополнительные сведения см. в разделе [проверки пользовательских категорий](#custom).|  
  
## <a name="where-to-place-validation-methods"></a>Размещение методов проверки  
 Зачастую того же эффекта можно достичь, разместив метод проверки в другом типе. Например, можно добавить метод к классу Person вместо отношения ParentsHaveChildren и выполнить его итерацию через связи:  
  
```  
[ValidationState(ValidationState.Enabled)]  
public partial class Person  
{[ValidationMethod  
 ( ValidationCategories.Open   
 | ValidationCategories.Save  
 | ValidationCategories.Menu  
 )  
]  
  private void ValidateParentBirth(ValidationContext context)     
  {  
    // Iterate through ParentHasChildren links:  
    foreach (Person parent in this.Parents)  
    {  
        if (this.BirthYear <= parent.BirthYear)  
        { ...  
  
```  
  
 **Статистическая обработка ограничений проверки.** Для применения проверки в предсказуемом порядке определите единый метод проверки в классе владельца, таком как корневой элемент модели. Эта технология также позволяет объединять несколько отчетов об ошибках в одно сообщение.  
  
 Недостатком является то, что объединенным методом сложнее управлять, а все ограничения должны иметь один и тот же `ValidationCategories`. В связи с этим рекомендуется по возможности хранить каждое ограничение в отдельном методе.  
  
 **Передача значений в контексте кэша.** Параметр контекста имеет словарь, в который можно поместить произвольные значения. Словарь существует в течение времени работы проверки. Определенный метод проверки может, например, хранить счетчик ошибок в контексте и использовать его во избежание переполнения окна ошибок повторяющимися сообщениями. Например:  
  
```csharp  
List<ParentsHaveChildren> erroneousLinks;  
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))  
erroneousLinks = new List<ParentsHaveChildren>();  
erroneousLinks.Add(this);  
context.SetCacheValue("erroneousLinks", erroneousLinks);  
if (erroneousLinks.Count < 5) { context.LogError( ... ); }  
  
```  
  
## <a name="validation-of-multiplicities"></a>Проверка кратностей  
 Методы проверки минимальной кратности создаются для доменного языка автоматически. Для написания кода **Dsl\Generated Code\MultiplicityValidation.cs**. Эти методы вступают в силу при включении проверки в **Editor\Validation** узел в обозревателе DSL.  
  
 Если кратность роли доменного отношения равна 1..* или 1..1, но пользователь не создает ссылку на это отношение, появляется сообщение об ошибке.  
  
 Например, если есть DSL классы человека и города и PersonLivesInTown связь с отношением **1..\***  в городе роли, затем для каждого пользователя, имеет не города, появится сообщение об ошибке.  
  
## <a name="running-validation-from-program-code"></a>Запуск проверки из кода программы  
 Можно запустить проверку, имея доступ к ValidationController или создав его. Ошибки будут отображаться для пользователя в окне ошибок, используйте ValidationController, подключенный к вашей схемы DocData. Например, при написании команды меню `CurrentDocData.ValidationController` доступен в классе наборов команд:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
partial class MyLanguageCommandSet   
{  
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)   
  {   
   ValidationController controller = this.CurrentDocData.ValidationController;   
...  
  
```  
  
 Дополнительные сведения см. в разделе [как: Добавление команды в контекстное меню](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
 Также можно создать отдельный контроллер проверки и управлять ошибками самостоятельно. Например:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
using Microsoft.VisualStudio.Modeling.Shell;  
...  
Store store = ...;  
VsValidationController validator = new VsValidationController(s);  
// Validate all elements in the Store:  
if (!validator.Validate(store, ValidationCategories.Save))  
{  
  // Deal with errors:  
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }  
}  
  
```  
  
## <a name="running-validation-when-a-change-occurs"></a>Запуск проверки при внесении изменений  
 Если нужно, чтобы пользователь получал уведомление сразу, как только модель станет недействительной, можно определить событие хранения, которое запускает проверку. Дополнительные сведения о событиях хранилища см. в разделе [обработчики распространение изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 В дополнение к проверке кода, добавьте файл пользовательского кода, чтобы ваш **DslPackage** проекта с содержимым, аналогичный приведенному ниже. В этом коде используется `ValidationController`, который вложен в документ. Этот контроллер отображает ошибки проверки в списке ошибок [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
```csharp  
using System;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Validation;  
namespace Company.FamilyTree  
{  
  partial class FamilyTreeDocData // Change name to your DocData.  
  {  
    // Register the store event handler:   
    protected override void OnDocumentLoaded()  
    {  
      base.OnDocumentLoaded();  
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(ParentsHaveChildren));  
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory  
         .FindDomainClass(typeof(Person));  
      EventManagerDirectory events = this.Store.EventManagerDirectory;  
      events.ElementAdded  
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));  
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));  
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));  
    }  
    // Handler will be called after transaction that creates a link:  
    private void ParentLinkAddedHandler(object sender,  
                                ElementAddedEventArgs e)  
    {  
      this.ValidationController.Validate(e.ModelElement,  
           ValidationCategories.Save);  
    }  
    // Called when a link is deleted:  
    private void ParentLinkDeletedHandler(object sender,   
                                ElementDeletedEventArgs e)  
    {  
      // Don't apply validation to a deleted item!   
      // - Validate store to refresh the error list.  
      this.ValidationController.Validate(this.Store,  
           ValidationCategories.Save);  
    }  
    // Called when any property of a Person element changes:  
    private void BirthDateChangedHandler(object sender,  
                      ElementPropertyChangedEventArgs e)  
    {  
      Person person = e.ModelElement as Person;  
      // Not interested in changes in other properties:  
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)  
          return;  
  
      // Validate all parent links to and from the person:  
      this.ValidationController.Validate(  
        ParentsHaveChildren.GetLinksToParents(person)  
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))  
        , ValidationCategories.Save);  
    }  
  }  
}  
  
```  
  
 Обработчики также вызываются после операций "Отменить" или "Повторить", влияющие на ссылки или элементы.  
  
##  <a name="custom"></a>Категории пользовательской проверки  
 В дополнение к категориям стандартной проверки, например "Меню" и "Открыть", можно определить собственные категории. Эти категории могут вызываться из кода программы. Пользователь не может вызвать их напрямую.  
  
 Обычно пользовательские категории используются для определения категории, которая проверяет, удовлетворяет ли модель предусловиям конкретного устройства.  
  
 Чтобы добавить метод проверки к определенному инструменту, установите для него атрибут в качестве следующего префикса:  
  
```csharp  
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]  
[ValidationMethod(ValidationCategory.Menu)]   
private void TestForCircularLinks(ValidationContext context)   
{...}  
  
```  
  
> [!NOTE]
>  Можно установить в качестве префикса метод с нужным количеством атрибутов `[ValidationMethod()]`. Можно добавить метод как в пользовательские, так и в стандартные категории.  
  
 Вызов пользовательской проверки:  
  
```csharp  
  
// Invoke all validation methods in a custom category:   
validationController.ValidateCustom  
  (store, // or a list of model elements  
   "PreconditionsForGeneratePartsList");  
```  
  
##  <a name="alternatives"></a>Альтернативы для проверки  
 Ограничения проверки создают отчеты об ошибках, но не изменяют модель. Если вместо этого требуется избежать недопустимости модели, можно использовать другие технологии.  
  
 Однако эти технологии не рекомендуются. Как правило, лучше разрешить пользователю самому решать, как исправить недопустимую модель.  
  
 **Настройте изменения для восстановления модели действия.** Например, если пользователь задает свойства выше разрешенного максимума, можно сбросить свойство до максимального значения. Для этого определите правило. Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
 **Откат транзакции при попытке недопустимое изменение.** Можно также определить правила для этой цели, но в некоторых случаях можно переопределить свойство обработчик **OnValueChanging()**, или попытка переопределения одного метода, такие как `OnDeleted().` для отката транзакции, используйте `this.Store.TransactionManager.CurrentTransaction.Rollback().` для получения дополнительных сведений сведения см. в разделе [обработчики изменений значений свойств домена](../modeling/domain-property-value-change-handlers.md).  
  
> [!WARNING]
>  Обеспечьте уведомление пользователя о том, что изменения были отрегулированы и произведен откат. Например используйте`System.Windows.Forms.MessageBox.Show("message").`  
  
## <a name="see-also"></a>См. также  
 [Навигация по модели и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Обработчики событий распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md)