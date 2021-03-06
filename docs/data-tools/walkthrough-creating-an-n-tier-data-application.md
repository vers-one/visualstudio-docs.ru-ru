---
title: "Пошаговое руководство: Создание N-уровневое приложение | Документы Microsoft"
ms.custom: 
ms.date: 09/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 9e513fc346991912dcc91e9a56062e49760d9779
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Пошаговое руководство. Создание многоуровневого приложения для работы с данными
*N-уровневые* данных приложения, приложения, доступ к данным и разделены на несколько логических слоев или *уровни*. Разделение компонентов приложения на несколько отдельных уровней повышает удобство обслуживания и масштабируемость приложения. Это обеспечивается за счет упрощения внедрения новых технологий, которые можно применить к отдельному уровню без пересмотра всего решения. N-уровневая архитектура включает в себя уровень представления, средний уровень и уровень данных. Средний уровень обычно содержит слой доступа к данным, слой бизнес-логики и общие компоненты, такие как аутентификация и проверка. Уровень данных содержит реляционную базу данных. N-уровневые приложения обычно хранят конфиденциальную информацию на слое доступа к данным среднего уровня, чтобы обеспечить изоляцию от конечных пользователей, работающих с уровнем представления. Дополнительные сведения см. в разделе [Общие сведения о приложениях данных N-уровневые](../data-tools/n-tier-data-applications-overview.md).  
  
Один из способов разделения разных уровней в n-уровневом приложении заключается в создании отдельных проектов для каждого уровня, который требуется включить в приложение. Типизированные наборы данных содержат свойство `DataSet Project`, определяющее, в какие проекты следует передать созданный набор данных и код `TableAdapter`.  
  
В этом пошаговом руководстве показано, как разделить набор данных и `TableAdapter` код в отдельным проектам библиотеки классов с помощью **конструктора наборов данных**. После разделения кода адаптера таблицы и набора данных, будут созданы [служб Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) службы для вызова уровень доступа к данным. Наконец, вы создадите приложение Windows Forms в качестве уровня представления. Этот уровень осуществляет доступ к данным из службы данных.  
  
В этом пошаговом руководстве выполняются следующие задачи.  
  
-   Создание нового n-уровневого решения, содержащего несколько проектов.  
  
-   Добавление в n-уровневое решение двух проектов библиотеки классов.  
  
-   Создание типизированного набора данных с помощью **мастер настройки источника данных**.  
  
-   Разделение создаваемых [адаптеры таблиц TableAdapter](create-and-configure-tableadapters.md) и набора данных на отдельные проекты.  
  
-   Создание службы WCF для вызова уровня доступа к данным.  
  
-   Создание функций в службе для извлечения данных из уровня доступа к данным.  
  
-   Создание приложения Windows Forms для использования в качестве уровня представления.  
  
-   Создание элементов управления Windows Forms с привязкой к источнику данных.  
  
-   Написание кода для заполнения таблиц данных.  
  
![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") видео версию этого раздела см. в разделе [видео: создание N-уровневого приложения данных](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Предварительные требования  
В этом пошаговом руководстве используется SQL Server Express LocalDB и базе данных Northwind.  
  
1.  Если у вас нет SQL Server Express LocalDB, установите его из [страницы загрузки SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), либо с помощью **установщик Visual Studio**. Установщик Visual Studio можно установить SQL Server Express LocalDB в рамках **разработки настольных приложений .NET** рабочей нагрузки, или в отдельных компонентов.  
  
2.  Установка образца базы данных Northwind, выполните следующие действия:  

    1. В Visual Studio откройте **обозреватель объектов SQL Server** окна. (Обозреватель объектов SQL Server устанавливается как часть **хранения и обработки данных** рабочей нагрузки в установщик Visual Studio.) Разверните **SQL Server** узла. Щелкните правой кнопкой мыши на экземпляре LocalDB и выберите **нового запроса...** .  

       Откроется окно редактора запросов.  

    2. Копировать [сценарий Northwind Transact-SQL](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) в буфер обмена. Этот скрипт T-SQL создает базу данных Northwind с нуля и заполняет ее данными.  

    3. Вставьте скрипт T-SQL в редакторе запросов, а затем выберите **Execute** кнопки.  

       Через некоторое время завершения выполнения запроса и создания базы данных "Борей".  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Создание N-уровневого решения и библиотеки классов для хранения набора данных (DataEntityTier)  
 Первым шагом данного руководства является создание решения и двух проектов библиотеки классов. Первая библиотека классов будет содержать набор данных (сформированный класс типизированного набора данных и таблицы данных, которые будут содержать данные приложения). Этот проект используется в качестве слоя сущностей данных приложения и обычно находится в среднем уровне. Datasetis, используется для создания исходного набора данных и автоматического разделения кода на две библиотеки классов.  
  
> [!NOTE]
>  Убедитесь, что корректное имя проекту и решению, прежде чем нажимать кнопку **ОК**. Это облегчит выполнение данного пошагового руководства.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Создание n-уровневого решения и библиотеки классов DataEntityTier  

1. В Visual Studio на **файл** последовательно выберите пункты **New**, **проекта...** .  
  
2. Разверните **Visual C#** или **Visual Basic** на левой панели, затем выберите **классического Windows**.  

3. В средней области выберите **библиотеки классов** тип проекта.  
  
4. Назовите проект **DataEntityTier**.  
  
5. Присвойте решению имя **NTierWalkthrough**, а затем выберите **ОК**.  
  
     Создается и добавляется в решение NTierWalkthrough, содержащее проект DataEntityTier **обозревателе решений**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Создание библиотеки классов для хранения адаптеров таблицы (DataAccessTier)  
 Следующий наг после создания проекта DataEntityTier заключается в создании другого проекта библиотеки классов. Этот проект будет содержать созданные `TableAdapter`s и называется *уровень доступа к данным* приложения. Уровень доступа к данным содержит информацию, необходимую для подключения к базе данных, и обычно находится на среднем уровне.  
  
#### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Для создания отдельной библиотеке классов для адаптеров таблиц  
  
1.  Щелкните правой кнопкой мыши решение в обозревателе решений и выберите **добавить**, **новый проект...** .  
  
2.  В **новый проект** в средней области выберите диалогового **библиотеки классов**.  
  
3.  Назовите проект **DataAccessTier** и выберите **ОК**.  
  
     Создается проект DataAccessTier, который добавляется в решение NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Создание набора данных  
 Следующим шагом является создание типизированного набора данных. Типизированные наборы данных создаются с классом набора данных (включая классы таблиц данных) и классами `TableAdapter` в одном проекте. (Все классы формируются в одном файле.) При разделении набора данных и адаптеров `TableAdapter` по разным проектам именно класс набора данных перемещается в другой проект, оставляя классы `TableAdapter` в исходном проекте. Таким образом, создайте набор данных в проекте, который в конечном итоге будет содержать `TableAdapter` (проект DataAccessTier). Набор данных создается с помощью **мастер настройки источника данных**.  
  
> [!NOTE]
>  Для создания подключения необходимо иметь доступ к учебной базе данных "Борей". Сведения о настройке образца базы данных Northwind см. в разделе [как: установить образцы баз данных](../data-tools/installing-database-systems-tools-and-samples.md).  
  
#### <a name="to-create-the-dataset"></a>Создание набора данных  
  
1.  Выберите DataAccessTier в **обозревателе решений**.  
  
2.  На **данные** последовательно выберите пункты **Показать источники данных**.  
  
3.  В **источники данных** выберите **добавить новый источник данных** запуск **мастер настройки источника данных**.  
  
4.  На **Выбор типа источника данных** выберите **базы данных** , а затем выберите **Далее**.  
  
5.  На **Выбор подключения к данным** выполните одно из следующих действий:  
  
     Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.  
  
     - или -  
  
     Выберите **новое подключение** Открытие **добавить подключение** диалоговое окно.  
  
6.  Если базе данных требуется пароль, выберите параметр для включения конфиденциальных данных, а затем выберите **Далее**.  
  
    > [!NOTE]
    >  Если вы выбрали файл локальной базы данных (вместо подключения к SQL Server), может отображаться запрос о том, требуется ли включить этот файл в проект. Выберите **Да** для добавления в проект файла базы данных.  
  
7.  Выберите **Далее** на **сохранение подключения в файле конфигурации приложения** страницы.  
  
8.  Разверните узел **Таблицы** на странице **Выбор объектов базы данных** .  
  
9.  Установите флажки для **клиентов** и **заказов** , а затем нажмите **Готово**.  
  
     NorthwindDataSet добавляется в проект DataAccessTier и отображается в **источники данных** окна.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Отделение адаптеров таблиц от набора данных  
 После создания набора данных отделите сформированный класс набора данных от адаптеров таблицы. Это можно сделать, задав **DataSet проекта** на имя проекта, в котором требуется хранить отделенный класс набора данных.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Порядок отделения адаптеров таблиц от набора данных  
  
1.  Дважды щелкните **NorthwindDataSet.xsd** в **обозревателе решений** для открытия набора данных в **конструктора наборов данных**.  
  
2.  Выберите пустую область конструктора.  
  
3.  Найдите **DataSet проекта** узел в **свойства** окна.  
  
4.  В **DataSet проекта** выберите **DataEntityTier**.  
  
5.  На **построения** последовательно выберите пункты **построить решение**.  
  
 Набор данных и адаптеры таблицы делятся на два проекта библиотеки классов. Проект, который изначально содержал весь набор данных (DataAccessTier), теперь содержит только адаптеры таблицы. Проект, предназначенный **DataSet проекта** свойство (DataEntityTier) содержит типизированный набор данных: NorthwindDataSet.Dataset.Designer.vb (или NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  При разделении наборов данных и адаптеров таблиц (установив **DataSet проекта** свойства), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Их необходимо переместить в проект набора данных вручную.  
  
## <a name="creating-a-new-service-application"></a>Создание нового приложения службы  
В этом пошаговом руководстве показано, как получить доступ к уровень доступа к данным с помощью службы WCF, поэтому давайте создадим новое приложение службы WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Создание нового приложения службы WCF  
  
1.  Щелкните правой кнопкой мыши решение в обозревателе решений и выберите **добавить**, **новый проект...** .  
  
2.  В **новый проект** в левой панели выберите диалогового **WCF**.  В средней области выберите **библиотеки службы WCF**.  
  
3.  Назовите проект **DataService** и выберите **ОК**.  
  
     Создается проект DataService, который добавляется в решение NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Создание методов на уровне доступа к данным для возврата данных о клиентах и заказах  
 Служба данных должна вызывать два метода на уровне доступа к данным: GetCustomers и GetOrders. Эти методы возвращают таблицы клиентов и заказов базы данных "Борей". Создайте методы GetCustomers и GetOrders в проекте DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Создание метода на уровне доступа к данным, возвращающего таблицу клиентов  
  
1.  В **обозревателе решений**, дважды щелкните NorthwindDataset.xsd, чтобы открыть набор данных.
  
2.  Щелкните правой кнопкой мыши CustomersTableAdapter и нажмите кнопку **добавить запрос**.  
  
3.  На **Выбор типа команды** оставьте значение по умолчанию **использовать инструкции SQL** и нажмите кнопку **Далее**.  
  
4.  На **Выбор типа запроса** оставьте значение по умолчанию **SELECT, возвращающая строки** и нажмите кнопку **Далее**.  
  
5.  На **указать инструкцию SQL SELECT** , оставьте запрос по умолчанию и нажмите кнопку **Далее**.  
  
6.  На **Выбор методов для создания** введите **GetCustomers** для **имя метода** в **вернуть таблицу данных** раздела.  
  
7.  Нажмите кнопку **Готово**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Создание метода на уровне доступа к данным, возвращающего таблицу заказов  
  
1.  Щелкните правой кнопкой мыши OrdersTableAdapter и выберите **добавить запрос**.  
  
2.  На **Выбор типа команды** оставьте значение по умолчанию **использовать инструкции SQL** и нажмите кнопку **Далее**.  
  
3.  На **Выбор типа запроса** оставьте значение по умолчанию **SELECT, возвращающая строки** и нажмите кнопку **Далее**.  
  
4.  На **указать инструкцию SQL SELECT** , оставьте запрос по умолчанию и нажмите кнопку **Далее**.  
  
5.  На **Выбор методов для создания** введите **GetOrders** для **имя метода** в **вернуть таблицу данных** раздела.  
  
6.  Нажмите кнопку **Готово**.  
  
7.  В меню **Сборка** выберите **Собрать решение**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Добавление в службу данных ссылки на уровни сущностей данных и доступа к данным  
 Поскольку службе данных необходима информация из набора данных и адаптеров таблицы, добавьте ссылки на проекты DataEntityTier и DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Добавление ссылок в службу данных  
  
1.  Щелкните правой кнопкой мыши DataService в **обозревателе решений** и нажмите кнопку **добавить ссылку**.  
  
2.  Нажмите кнопку **проекты** вкладке **добавить ссылку** диалоговое окно.  
  
3.  Выберите оба **DataAccessTier** и **DataEntityTier** проектов.  
  
4.  Нажмите кнопку **ОК**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Добавление функций в службу для вызова методов GetCustomers и GetOrders на уровне доступа к данным  
 Теперь, когда уровень доступа к данным содержит методы для возврата данных, создайте в службе данных методы для вызова методов на уровне доступа к данным.  
  
> [!NOTE]
>  Для проектов C# необходимо добавить ссылку на сборку `System.Data.DataSetExtensions`, чтобы следующий код прошел компиляцию.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Создание функций GetCustomers и GetOrders в службе данных  
  
1.  В **DataService** проекта, дважды щелкните файл IService1.vb или IService1.cs.  
  
2.  Добавьте следующий код под **Добавьте здесь операции служб** комментария:  
  
    ```vb  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```csharp  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
    ```  
  
3.  В проекте DataService дважды щелкните Service1.vb (или Service1.cs).  
  
4.  Добавьте следующий код в класс Service1:  
  
    ```vb  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```csharp  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
    }  
    ```  
  
5.  В меню **Сборка** выберите **Собрать решение**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Создание уровня представления для отображения данных из службы данных  
 Теперь, когда решение содержит службу данных с методами для выполнения вызовов на уровне доступа к данным, создайте еще один проект, который будет вызывать службу данных и представлять данные пользователям. В рамках данного руководства создайте приложение Windows Forms — это уровень представления n-уровневого приложения.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Создание проекта уровня представления  
  
1.  Щелкните правой кнопкой мыши решение в обозревателе решений и выберите **добавить**, **новый проект...** .  
  
2.  В **новый проект** в левой панели выберите диалогового **классического Windows**. В средней области выберите **приложение Windows Forms**.  
  
3.  Назовите проект **PresentationTier** и нажмите кнопку **ОК**.  
  
    Создается проект PresentationTier, который добавляется в решение NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Настройка проекта PresentationTier в качестве запускаемого  
Мы настроим проекта PresentationTier Автозагружаемый проект для решения, так как он является фактически клиентским приложением, используемый для представления данных и взаимодействия с данными.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Порядок настройки нового проекта уровня представления в качестве запускаемого  
  
-   В **обозревателе решений**, щелкните правой кнопкой мыши **PresentationTier** и нажмите кнопку **Назначить запускаемым проектом**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Добавление ссылок на уровень представления  
 Клиентскому приложению PresentationTier требуется ссылка на службу в службе данных для получения доступа к методам в этой службе. Кроме того, требуется ссылка на набор данных для обеспечения совместного использования типов службой WCF. До включения совместного использования типов с помощью службы данных код, добавленный в разделяемый класс наборов данных, будет недоступен для уровня представления. Поскольку вы обычно добавляете код, например код проверки, в события таблицы данных, изменяющие строку и столбец, вполне вероятно, что вы хотите получить доступ к этому коду из клиента.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Добавление ссылки на уровень представления  
  
1.  В **обозревателе решений**, PresentationTier правой кнопкой мыши и выберите **добавить ссылку**.  
  
2.  В **добавить ссылку** выберите **проекты** вкладки.  
  
3.  Выберите **DataEntityTier** и выберите **ОК**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Добавление ссылки на службу на уровень представления  
  
1.  В **обозревателе решений**, PresentationTier правой кнопкой мыши и выберите **добавить ссылку на службу**.  
  
2.  В **добавить ссылку на службу** выберите **Discover**.  
  
3.  Выберите **Service1** и выберите **ОК**.  
  
    > [!NOTE]
    >  Если на текущем компьютере имеется несколько служб, выберите службу, созданную ранее в рамках работы с этим руководством (эта служба содержит методы GetCustomers и GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Добавление элементов DataGridView в форму для отображения данных, возвращаемых службой данных  
 После добавления ссылки на службу в службу данных **источники данных** окно автоматически заполняется данными, возвращенных службой.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Создание двух элементов DataGridView с привязкой к данным на форме  
  
1.  В **обозревателе решений**, выберите проект PresentationTier.  
  
2.  В **источники данных** окна, разверните **NorthwindDataSet** и найдите **клиентов** узла.  
  
3.  Перетащите **клиентов** узел на форму Form1.  
  
4.  В **источники данных** окна, разверните **клиентов** узла и найдите связанный **заказов** узел ( **заказов** вложен в  **Клиенты** узла).  
  
5.  Перетащите связанный **заказов** узел на форму Form1.  
  
6.  Создайте обработчик событий `Form1_Load`, дважды щелкнув пустую область на форме.  
  
7.  Добавьте следующий код в обработчик событий `Form1_Load`.  
  
    ```vb  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```csharp  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
    ```  
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Увеличение максимально допустимого размера сообщения для службы  
Значение по умолчанию для maxReceivedMessageSize недостаточен для хранения данных, полученных из таблицы Customers и Orders. В следующих шагах будет увеличить значение на 6553600. Вы измените значение на клиенте, который автоматически обновит ссылку на службу.  
  
> [!NOTE]
>  Меньший размер по умолчанию призван ограничить уязвимость для атак типа "отказ в обслуживании" (DoS). Для получения дополнительной информации см. <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Увеличение значения maxReceivedMessageSize  
  
1.  В **обозревателе решений**, дважды щелкните файл app.config в проекте PresentationTier.  
  
2.  Найдите **maxReceivedMessage** атрибут размера и измените значение на `6553600`.  
  
## <a name="testing-the-application"></a>Тестирование приложения  
Запустите приложение, нажав клавишу **F5**. Данные из таблиц клиентов и заказов извлекаются из службы данных и отображаются на форме.  
  
## <a name="next-steps"></a>Следующие шаги  
 В зависимости от требований приложения существуют несколько шагов, которые, возможно, потребуется выполнить после сохранения связанных данных в приложении Windows. Ниже приводится перечень рекомендаций, позволяющих улучшить данное приложение.  
  
-   Добавьте проверку в набор данных. 
  
-   Добавьте в службу дополнительные методы для обновления данных в базе данных.  
  
## <a name="see-also"></a>См. также  
 [Работа с наборами данных в n уровневых приложениях](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Иерархическое обновление](../data-tools/hierarchical-update.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)