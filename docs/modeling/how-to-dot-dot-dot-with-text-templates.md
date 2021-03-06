---
title: "Практическое руководство по текстовым шаблонам | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 47824561813dfc422dfb19460f1c90f7ed78d1ad
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="how-to--with-text-templates"></a>Практическое руководство по текстовым шаблонам
Текстовые шаблоны в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предоставляют удобный способ создания текстом любого типа. Текстовые шаблоны можно использовать для создания текста во время выполнения как часть приложения, а также во время разработки для создания часть кода проекта. Этот раздел содержит описание наиболее часто задаваемые «Как?...» вопросы.  
  
 В этом разделе несколько ответов, которым предшествует маркеры являются альтернативными предложениями.  
  
 Общие сведения о текстовых шаблонах см. в статье [создание кода и текстовые шаблоны T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Инструкции...  
  
### <a name="generate-part-of-my-application-code"></a>Создание части код моего приложения  
 У меня есть конфигурации или *модель* в файл или базу данных. Один или несколько частей кода зависят от этой модели.  
  
-   Создайте несколько файлов кода из текстовых шаблонов. Дополнительные сведения см. в разделе [создание кода во время разработки с помощью текстовых шаблонов T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) и [возможности лучше всего начать написание шаблона?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Создание файлов во время выполнения, передачи данных в шаблон  
 Во время выполнения приложение создает текстовые файлы, такие как отчеты, которые представляют собой сочетание стандартного текста и данных. Я хочу написать сотни `write` инструкции.  
  
-   Добавьте текстовый шаблон времени выполнения в проект. Этот шаблон создает класс в коде, который можно создать и использовать для создания текста. В параметрах конструктора, можно передавать в нее данные. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Если вы хотите сформировать на основе шаблонов, которые доступны только во время выполнения, можно использовать стандартные текстовые шаблоны. При создании [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения, можно вызвать службы текстовых шаблонов. Дополнительные сведения см. в разделе [вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). В других контекстах можно использовать модуль создания текстовых шаблонов. Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.  
  
     Используйте \<#@parameter#> директивы для передачи параметров в эти шаблоны. Дополнительные сведения см. в разделе [директива Parameter T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Чтение другого файла проекта из шаблона  
 Для считывания файла из того же [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проекта в качестве шаблона:  
  
-   Вставьте строку `hostSpecific="true"` в директиву `<#@template#>`.  
  
     В коде, используйте `this.Host.ResolvePath(filename)` получить полный путь к файлу.  
  
### <a name="invoke-methods-from-a-template"></a>Вызов методов из шаблона  
 Если методы уже существуют, например, в стандартном [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] классы:  
  
-   Используйте \<#@assembly#> директивы для загрузки сборки и \<#@import#> для задания контекста пространства имен. Дополнительные сведения см. в разделе [директива Import T4](../modeling/t4-import-directive.md).  
  
     Если часто приходится использовать тот же набор сборок и импортировать директивы, рекомендуется написать процессора директив. В каждом шаблоне можно вызвать процессор директив может загружать сборки и файлы модели и задавать контекст пространства имен. Дополнительные сведения см. в разделе [Создание настраиваемых T4 процессорами текстового шаблона директива](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 При создании методов самостоятельно:  
  
-   При написании текстовом шаблоне времени выполнения, запись определение разделяемого класса, который имеет имя, совпадающее с именем текстовый шаблон времени выполнения. Добавьте дополнительные методы в этот класс.  
  
-   Записать блок управления возможностями класса `<#+ ... #>` , в котором можно объявлять, методы, свойства и закрытых классов. При компиляции текстового шаблона, он преобразуется в класс. Стандартные управляющие блоки `<#...#>` текст преобразуются в один метод и блоки возможностей класса вставляются как отдельные члены. Дополнительные сведения см. в разделе [управляющие блоки текстовых шаблонов](../modeling/text-template-control-blocks.md).  
  
     Методы, определенные как компоненты класса также может содержать встроенные блоки текста.  
  
     Рекомендуется поместить возможности класса в отдельный файл, который затем можно `<#@include#>` в одной или нескольких файлов шаблонов.  
  
-   Создайте методы в отдельной сборке (библиотека классов) и вызывать их из шаблона. Используйте `<#@assembly#>` директивы для загрузки сборки, и `<#@import#>` для задания контекста пространства имен. Обратите внимание, что для перестроения сборки в процессе его отладки, может потребоваться остановить и перезапустить [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения см. в разделе [директивы текстовых шаблонов T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Создание нескольких файлов из одной схемы модели  
 Если часто создаются файлы из моделей, которые имеют одинаковую схему XML или базы данных:  
  
-   Рекомендуется написать процессора директив. Это позволяет заменять несколько инструкций сборки и импортировать инструкции в каждый шаблон с одной пользовательской директивы. Процессор директив можно также загрузить и проанализировать файл модели. Дополнительные сведения см. в разделе [Создание настраиваемых T4 процессорами текстового шаблона директива](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Создание файлов из сложной модели  
  
-   Рассмотрите возможность создания доменного языка (DSL) для представления модели. Это делает его гораздо проще создавать шаблоны, поскольку использовать типы и свойства, которые отражают имена элементов в модели. Не нужно проанализировать файл или навигации по узлам XML. Пример:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Дополнительные сведения см. в разделе [Приступая к работе с доменными языками](../modeling/getting-started-with-domain-specific-languages.md) и [формирование кода из доменного языка](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Получение данных из[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Для использования служб, предоставляемых в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], набором `hostSpecific` атрибут и нагрузки `EnvDTE` сборки. Пример:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>Выполнение текстовых шаблонов в процессе построения  
  
-   Дополнительные сведения см. в разделе [создание кода в процессе сборки](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Более общие вопросы  
  
###  <a name="starting"></a>Что такое лучший способ начать создание текстового шаблона  
  
1.  Создайте конкретный пример созданного файла.  
  
2.  Преобразуйте его в текстовый шаблон, вставив `<#@template #>` директивы и директивы и код, необходимые для загрузки входного файла или модели.  
  
3.  Последовательно замените части файла с выражением и блоков кода.  
  
### <a name="what-is-a-model"></a>Что такое «модель»  
  
-   Входные данные, считываемые с помощью шаблона. Это может быть в файле или в базе данных. Он может быть XML, или документа Visio, доменный язык (DSL) или модель UML или это может быть обычный текст. Он может быть распределены между несколькими файлами. Обычно более одного шаблона считывает одну модель.  
  
     Термин «модель» имеет, чтобы он представлял некоторых аспектов деятельности более непосредственно, чем сгенерированного программного кода или других файлов. Например она может представлять план сети обмена данными, созданной программы будет контролировать.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Что такое преимущество использования текстовых шаблонов?  
 Как правило создается несколько кода или других файлов из одной модели. Модель представляет требования более непосредственно, чем сформированный код. Он пропускает сведения о реализации и предназначена для описания требований, а не код. При изменении требований — для них действия - можно обновить модель проще и надежнее, чем разные части программного кода.  
  
 Создание кода полезна, поэтому с точки зрения методов гибкой разработки.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Какие «рекомендации» существуют для текстовых шаблонов?  
  
-   Дополнительные сведения см. в разделе [правила для текстовых шаблонов T4 записи](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Что такое «T4»?  
  
-   Другое имя для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] возможностей текстовых шаблонов, описанных здесь. Предыдущая версия, не опубликован, был сокращенное обозначение «Преобразования текстовых шаблонов».
