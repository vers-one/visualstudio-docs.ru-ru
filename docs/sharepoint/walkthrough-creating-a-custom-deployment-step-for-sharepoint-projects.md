---
title: "Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 036f8d135e535547e9e5f790135186bf1f5728bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects"></a>Пошаговое руководство. Создание пользовательского шага развертывания для проектов SharePoint
  При развертывании проекта SharePoint в Visual Studio выполняет ряд шагов развертывания в определенном порядке. Visual Studio включает многие встроенные шаги развертывания, но можно также создать свои собственные.  
  
 В этом пошаговом руководстве вы создадите пользовательского шага развертывания для обновления решений на сервере, на котором выполняется SharePoint. Visual Studio включает встроенные шаги развертывания для многих задач, таких отзыва или добавления решений, но они не включают шага развертывания для обновления решений. По умолчанию при развертывании решения SharePoint, Visual Studio сначала отзывает решение (если он уже развернут) и затем повторно развертывание всего решения. Дополнительные сведения о встроенные шаги развертывания см. в разделе [развертывание, публикация и обновление пакетов решений SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Создание расширения Visual Studio, который выполняет две основные задачи:  
  
    -   Расширение определяет пользовательского шага развертывания для обновления решений SharePoint.  
  
    -   Модуль создает расширения проекта, который определяет новую конфигурацию развертывания, которая представляет собой набор шагов развертывания, которые выполняются для данного проекта. Новая конфигурация развертывания включает пользовательского шага развертывания и несколько встроенных шагов развертывания.  
  
-   Создание двух пользовательских команд SharePoint, которые вызывает сборку расширения. Команды SharePoint, методы, которые могут быть вызваны сборок расширения для использования API-интерфейсы в серверной объектной модели SharePoint. Дополнительные сведения см. в разделе [вызова объектной модели SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Построение пакета расширения Visual Studio (VSIX) для развертывания обе сборки.  
  
-   Тестирование нового шага развертывания.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимы следующие компоненты на компьютере разработчика для выполнения данного пошагового руководства.  
  
-   Поддерживаемые версии Windows, SharePoint и Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK. В этом пошаговом руководстве используется **проект VSIX** шаблона в пакет SDK, чтобы создать пакет VSIX для развертывания расширения. Дополнительные сведения см. в разделе [расширение инструментов SharePoint в Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Изучением приведенных ниже концепций будет полезно, хотя и не требуется для выполнения данного пошагового руководства.  
  
-   Использование серверной объектной модели для SharePoint. Дополнительные сведения см. в разделе [с помощью объектной модели SharePoint Foundation серверные](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Решения SharePoint. Дополнительные сведения см. в разделе [Обзор решений](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Обновление решений SharePoint. Дополнительные сведения см. в разделе [обновление решения](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="creating-the-projects"></a>Создание проектов  
 Для выполнения данного пошагового руководства, необходимо создать три проекта:  
  
-   Чтобы создать пакет VSIX для развертывания расширения проекта VSIX.  
  
-   Проект библиотеки классов, которая реализует расширение. Этот проект должны предназначаться для платформы .NET Framework 4.5.  
  
-   Проект библиотеки классов, определяющий пользовательские команды SharePoint. Этот проект должны предназначаться для платформы .NET Framework 3.5.  
  
 Пошаговое руководство начинается с создания проектов.  
  
#### <a name="to-create-the-vsix-project"></a>Создание проекта VSIX  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
3.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **расширяемости** узла.  
  
    > [!NOTE]  
    >  **Расширяемости** узел доступен, только если установлен пакет SDK для Visual Studio. Дополнительные сведения см. в разделе предварительных требований этого раздела.  
  
4.  В верхней части диалогового окна выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
5.  Выберите **проект VSIX** шаблона, имя проекта **UpgradeDeploymentStep**и нажмите кнопку **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Добавляет **UpgradeDeploymentStep** проекта **обозревателе решений**.  
  
#### <a name="to-create-the-extension-project"></a>Создание проекта расширения  
  
1.  В **обозревателе решений**откройте контекстное меню узла решения UpgradeDeploymentStep, выберите **добавить**и нажмите кнопку **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic** узлов и нажмите кнопку **Windows** узла.  
  
3.  В верхней части диалогового окна выберите **.NET Framework 4.5** в списке версий .NET Framework.  
  
4.  Выберите **библиотеки классов** шаблон проекта, присвойте проекту имя **DeploymentStepExtension**, а затем выберите **ОК** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Добавляет **DeploymentStepExtension** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Чтобы создать проект команды SharePoint  
  
1.  В **обозревателе решений**откройте контекстное меню узла решения UpgradeDeploymentStep, выберите **добавить**и нажмите кнопку **новый проект**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** или **Visual Basic**, а затем выберите **Windows** узла.  
  
3.  В верхней части диалогового окна выберите **.NET Framework 3.5** в списке версий .NET Framework.  
  
4.  Выберите **библиотеки классов** шаблон проекта, присвойте проекту имя **SharePointCommands**, а затем выберите **ОК** кнопки.  
  
     Visual Studio добавляет **SharePointCommands** в решение проект и открывает файл кода по умолчанию Class1.  
  
5.  Удалите файл Class1 код из проекта.  
  
## <a name="configuring-the-projects"></a>Настройка проектов  
 Перед написанием кода для создания пользовательского шага развертывания необходимо добавить файлы кода и ссылки на сборки и проекты необходимо настроить.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Настройка проекта DeploymentStepExtension  
  
1.  В **DeploymentStepExtension** проект, добавить двух файлах кода, которые имеют следующие имена:  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Откройте контекстное меню для проекта DeploymentStepExtension и выберите **добавить ссылку**.  
  
3.  На **Framework** вкладки, установите флажок для сборке System.ComponentModel.Composition.  
  
4.  На **расширения** , установите флажок для сборки Microsoft.VisualStudio.SharePoint и нажмите кнопку **ОК** кнопки.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Чтобы настроить проект SharePointCommands  
  
1.  В **SharePointCommands** проект, добавить файл кода с именем команды.  
  
2.  В **обозревателе решений**, откройте контекстное меню на **SharePointCommands** узел проекта, а затем выберите **добавить ссылку**.  
  
3.  На **расширения** вкладки, установите флажки для следующих сборок и затем нажмите кнопку выбрать **ОК** кнопки  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="defining-the-custom-deployment-step"></a>Определение пользовательского шага развертывания  
 Создайте класс, определяющий шаг развертывания обновления. Для определения шага развертывания класс реализует <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> интерфейса. Реализуйте этот интерфейс, каждый раз, когда требуется определить пользовательский шаг развертывания.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Определение пользовательского шага развертывания  
  
1.  В **DeploymentStepExtension** проекта, откройте файл кода UpgradeStep и вставьте в него следующий код.  
  
    > [!NOTE]  
    >  Добавьте следующий код, проект будет содержать ошибки компиляции, но они будут исчезнуть при добавлении кода в последующих шагах.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="creating-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Создание конфигурации развертывания, включающей пользовательского шага развертывания  
 Создание расширения проекта для новой конфигурации развертывания, которая включает в себя несколько встроенных шагов развертывания и новый шаг развертывания обновления. Создание этого расширения, помогает разработчикам SharePoint использование шага развертывания обновления в проектах SharePoint.  
  
 Для создания конфигурации развертывания, этот класс реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> интерфейса. Реализуйте этот интерфейс, каждый раз, когда требуется создание расширения проекта SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Для создания конфигурации развертывания  
  
1.  
  
2.  В **DeploymentStepExtension** проекта, откройте файл кода DeploymentConfigurationExtension и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Создание команд пользовательские SharePoint  
 Создание двух пользовательских команд, которые вызывают серверную объектную модель для SharePoint. Одна команда определяет решение уже развернуто ли; Вторая обновляет решение.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Для определения команды SharePoint  
  
1.  В **SharePointCommands** проекта, откройте файл кода, команды и вставьте в него следующий код.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Контрольная точка  
 На этом этапе в пошаговом руководстве, весь код пользовательского шага развертывания и команд SharePoint теперь находятся в проекты. Их, чтобы убедиться в том, что они компилируется без ошибок построения.  
  
#### <a name="to-build-the-projects"></a>Для построения проектов  
  
1.  В **обозревателе решений**, откройте контекстное меню для **DeploymentStepExtension** проекта, а затем выберите **сборки**.  
  
2.  Откройте контекстное меню для **SharePointCommands** проекта, а затем выберите **сборки**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Создание пакета VSIX для развертывания расширения  
 Для развертывания расширения, используйте проект VSIX в решении для создания пакета VSIX. Во-первых настройте пакет VSIX, изменив файл source.extension.vsixmanifest в проекте VSIX. Затем создайте пакет VSIX, построение решения.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Для настройки и создания пакета VSIX  
  
1.  В **обозревателе решений**в разделе **UpgradeDeploymentStep** проекта, откройте контекстное меню для **source.extension.vsixmanifest** файл, а затем выберите  **Откройте**.  
  
     Visual Studio открывает файл в редакторе манифестов. Файл source.extension.vsixmanifest является основой для файл extension.vsixmanifest, требующий все пакеты VSIX. Дополнительные сведения об этом файле см. в разделе [ссылки 1.0 схемы расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  В **название продукта** введите **шаг развертывания обновления для проектов SharePoint**.  
  
3.  В **автор** введите **Contoso**.  
  
4.  В **описание** введите **предоставляет пользовательский шаг развертывания обновления, можно использовать в проектах SharePoint**.  
  
5.  В **активы** вкладка редактора выберите **New** кнопки.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
6.  В **тип** выберите **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Это значение соответствует `MefComponent` элемент в файл extension.vsixmanifest. Этот элемент задает имя сборки расширения в пакете VSIX. Дополнительные сведения см. в разделе [MEFComponent элемент (Схема VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  В **источника** выберите **проект в текущем решении**.  
  
8.  В **проекта** выберите **DeploymentStepExtension**, а затем выберите **ОК** кнопки.  
  
9. В редакторе манифеста выберите **New** еще раз.  
  
     **Добавить новый актив** откроется диалоговое окно.  
  
10. В **тип** введите **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Этот элемент задает пользовательский модуль, который требуется включить в расширение Visual Studio. Дополнительные сведения см. в разделе [активов элемент (Схема VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. В **источника** выберите **проект в текущем решении**.  
  
12. В **проекта** выберите **SharePointCommands**, а затем выберите **ОК** кнопки.  
  
13. В строке меню выберите **построения**, **построить решение**, а затем убедитесь, что решение компилируется без ошибок.  
  
14. Убедитесь, что в выходную папку построения для проекта UpgradeDeploymentStep теперь содержит файл UpgradeDeploymentStep.vsix.  
  
     По умолчанию является выходной папке сборки... папку \bin\debug в папке, содержащей файл проекта.  
  
## <a name="preparing-to-test-the-upgrade-deployment-step"></a>Подготовка к тестирования шага развертывания обновления  
 Чтобы протестировать шаг развертывания обновления, необходимо сначала развернуть образец решения на сайте SharePoint. Начните отладку расширения в экспериментальном экземпляре Visual Studio. Затем создайте определения списка и экземпляра списка для тестирования шага развертывания и затем развернуть их на сайте SharePoint. Затем измените определение списка и экземпляра списка и повторно развернуть их для демонстрации того, как процесс развертывания по умолчанию решение будет перезаписано на сайте SharePoint.  
  
 Далее в этом пошаговом руководстве необходимо изменить определение списка и экземпляра списка и затем будет обновлять их на сайте SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Чтобы начать отладку расширения  
  
1.  Перезапустите Visual Studio с правами администратора и откройте решение UpgradeDeploymentStep.  
  
2.  В проекте DeploymentStepExtension, откройте файл кода UpgradeStep и затем добавьте точку останова в первой строке кода в `CanExecute` и `Execute` методы.  
  
3.  Запуск отладки, нажав клавишу F5 или выберите в строке меню, выбрав **отладки**, **начать отладку**.  
  
4.  Visual Studio устанавливает расширение для %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade шага развертывания для SharePoint Projects\1.0 и запуске экспериментального экземпляра Visual Studio. Вы сможете протестировать шаг развертывания обновления в этом экземпляре Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Создание проекта SharePoint с помощью определения списка и экземпляра списка  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **файл**, **New**, **проекта**.  
  
2.  В **новый проект** диалогового окна разверните **Visual C#** узел или **Visual Basic** узел, разверните **SharePoint** узел и нажмите кнопку **2010** узла.  
  
3.  Убедитесь, что вверху диалогового окна **.NET Framework 3.5** появится в списке версий .NET Framework.  
  
     Проекты [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] и [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] требуется эта версия платформы .NET Framework.  
  
4.  В списке шаблонов проектов выберите **проект SharePoint 2010**, назовите проект **EmployeesListDefinition**, а затем выберите **ОК** кнопки.  
  
5.  В **мастер настройки SharePoint**, введите URL-адрес сайта, который требуется использовать для отладки.  
  
6.  В разделе **Какова степень доверия для этого решения SharePoint**, выберите **развернуть как решение фермы** переключатель.  
  
    > [!NOTE]  
    >  Шаг развертывания обновления не поддерживает изолированные решения.  
  
7.  Выберите **Готово** кнопки.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Создает проект EmployeesListDefinition.  
  
8.  Откройте контекстное меню для проекта EmployeesListDefinition, **добавить**, а затем выберите **новый элемент**.  
  
9. В **добавить новый элемент — EmployeesListDefinition** диалогового окна разверните **SharePoint** узел и выберите **2010** узла.  
  
10. Выберите **списка** шаблона элемента, имя элемента **список сотрудников**и нажмите кнопку **добавить** кнопки.  
  
     Откроется мастер настройки SharePoint  
  
11. На **Выбор параметров списка** , проверьте следующие параметры, а затем выберите **Готово** кнопки:  
  
    1.  **Список сотрудников** отображается в **какое имя вы хотите отобразить списка?** поле.  
  
    2.  **Создать настраиваемый список на основе:** переключатель выбирается.  
  
    3.  **По умолчанию (пустое)** выбирается в **создать настраиваемый список на основе:** списка.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Создает элемент списка сотрудников с заголовка столбца и одной пустой экземпляр и откроется конструктор списка.  
  
12. В конструкторе списка на **столбцы** выберите **введите имя нового или существующего столбца** строк, а затем добавьте следующие столбцы в **отображаемое имя столбца** списка:  
  
    1.  Имя  
  
    2.  Компания  
  
    3.  Рабочий телефон  
  
    4.  E-Mail  
  
13. Сохраните все файлы, а затем закройте конструктор списка.  
  
14. В **обозревателе решений**, разверните **список сотрудников** узел и разверните **экземпляра списка сотрудников** дочернего узла.  
  
15. В файле Elements.xml замените имя по умолчанию XML-код в этот файл следующий XML-код. Этот XML-код изменяет имя списка, чтобы **сотрудников** и добавляет данные сотрудников, которые именованные Jim Hance.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
        <Data>  
          <Rows>  
            <Row>  
              <Field Name="Title">Hance</Field>  
              <Field Name="FirstName">Jim</Field>  
              <Field Name="Company">Contoso</Field>  
              <Field Name="Business Phone">555-555-5555</Field>  
              <Field Name="E-Mail">jim@contoso.com</Field>  
            </Row>  
          </Rows>  
        </Data>  
      </ListInstance>  
    </Elements>  
    ```  
  
16. Сохраните и закройте файл Elements.xml.  
  
17. Откройте контекстное меню для проекта EmployeesListDefinition, а затем выберите **откройте** или **свойства**.  
  
     Откроется конструктор свойства.  
  
18. На **SharePoint** снимите **автоматически отозвать после отладки** флажок, а затем сохраните свойства.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Развертывание определения списка и экземпляра списка  
  
1.  В **обозревателе решений**, выберите **EmployeesListDefinition** узел проекта.  
  
2.  В **свойства** окна, убедитесь, что **активная конфигурация развертывания** свойству **по умолчанию**.  
  
3.  Нажмите клавишу F5 или в строке меню выберите **отладки**, **начать отладку**.  
  
4.  Убедитесь, что сборка проекта выполняется успешно, что веб-браузере открывается на сайте SharePoint, **перечислены** элемент на панели быстрого запуска включает новый **сотрудников** списка и что  **Сотрудники** список содержит запись для Jim Hance.  
  
5.  Закройте веб-браузер.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Для изменения определения списка и экземпляра списка и их повторное развертывание  
  
1.  В проекте EmployeesListDefinition, откройте файл Elements.xml, который является дочерним объектом **экземпляра списка сотрудников** элемент проекта.  
  
2.  Удалить `Data` элемент и его дочерние элементы, чтобы удалить запись для Jim Hance из списка.  
  
     По завершении файл должен содержать следующий XML-код.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Сохраните и закройте файл Elements.xml.  
  
4.  Откройте контекстное меню для **список сотрудников** элемента проекта, а затем выберите **откройте** или **свойства**.  
  
5.  В конструкторе списка, выберите **представления** вкладки.  
  
6.  В **выбранные столбцы** выберите **вложения**, а затем выберите < ключ, чтобы переместить этот столбец в **доступные столбцы** список.  
  
7.  Повторите предыдущий шаг, чтобы переместить **рабочий телефон** столбец из **выбранные столбцы** список **доступные столбцы** списка.  
  
     Это действие удалит данные поля из представления по умолчанию **сотрудников** список на сайте SharePoint.  
  
8.  Запуск отладки, нажав клавишу F5 или выберите в строке меню, выбрав **отладки**, **начать отладку**.  
  
9. Убедитесь, что **конфликтов развертывания** откроется диалоговое окно.  
  
     Это диалоговое окно предназначено появляется при попытке Visual Studio развернуть решение (экземпляр списка) на сайте SharePoint, в которой уже был развернут этого решения. Это диалоговое окно предназначено не будет отображаться при выполнении шага развертывания обновления позже в этом пошаговом руководстве.  
  
10. В **конфликтов развертывания** диалогового окна выберите **автоматически разрешить** переключатель.  
  
     Visual Studio удаляет экземпляр списка на сайте SharePoint, развертывает элемента списка в проекте и затем откроется сайт SharePoint.  
  
11. В **перечислены** раздел на панели быстрого запуска выберите **сотрудников** списка, а затем проверьте следующие сведения:  
  
    -   **Вложения** и **домашний телефон** столбцы не отображаются в этом представлении списка.  
  
    -   Список пуст. При использовании **по умолчанию** конфигурации развертывания повторное развертывание решения, **сотрудников** список был заменен новым пустым списком в проекте.  
  
## <a name="testing-the-deployment-step"></a>Тестирование шага развертывания  
 Теперь все готово для тестирования шага развертывания обновления. Во-первых необходимо добавьте элемент в экземпляр списка в SharePoint. Затем измените определение списка и экземпляра списка, обновить их на сайте SharePoint и убедитесь, что шаг развертывания обновления не перезаписывает новый элемент.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Чтобы вручную добавить элемент в список  
  
1.  На ленте на сайте SharePoint в разделе **Инструменты списка** выберите **элементы** вкладки.  
  
2.  В **New** выберите **новый элемент**.  
  
     В качестве альтернативы можно выбрать **добавить новый элемент** ссылку в сам список элементов.  
  
3.  В **сотрудников — новый элемент** окна в **заголовок** введите **средства диспетчера**.  
  
4.  В **имя** введите **Энди**.  
  
5.  В **компании** введите **Contoso**.  
  
6.  Выберите **Сохранить** кнопку, убедитесь, что новый элемент появляется в списке и затем закройте веб-браузер.  
  
     Далее в этом пошаговом руководстве будет использовать этот элемент, чтобы убедиться, что шаг развертывания обновления не перезаписывает содержимое этого списка.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Для тестирования шага развертывания обновления  
  
1.  В экспериментальном экземпляре Visual Studio в **обозревателе решений**, откройте контекстное меню для **EmployeesListDefinition** узел проекта, а затем выберите **свойства**.  
  
     Откроется конструктор и редактор свойств.  
  
2.  На **SharePoint** установите **активная конфигурация развертывания** свойства **обновление**.  
  
     Эта конфигурация развертывания включает новый шаг развертывания обновления.  
  
3.  Откройте контекстное меню для **список сотрудников** элемента проекта, а затем выберите **свойства** или **откройте**.  
  
     Откроется конструктор и редактор свойств.  
  
4.  На **представления** выберите **электронной почты** столбец и выберите  **<**  клавишу, чтобы переместить этот столбец из **выбранные столбцы**список **доступные столбцы** списка.  
  
     Это действие удалит данные поля из представления по умолчанию **сотрудников** список на сайте SharePoint.  
  
5.  Запуск отладки, нажав клавишу F5 или выберите в строке меню, выбрав **отладки**, **начать отладку**.  
  
6.  Убедитесь, что код в другом экземпляре Visual Studio прервано на точке останова, заданной ранее в `CanExecute` метод.  
  
7.  Снова нажмите клавишу F5 или в строке меню выберите **отладки**, **Продолжить**.  
  
8.  Убедитесь, что выполнение кода прервано на точке останова, заданной ранее в `Execute` метод.  
  
9. Нажмите клавишу F5 или в строке меню выберите **отладки**, **Продолжить** в последний раз.  
  
     Веб-браузере откроется сайт SharePoint.  
  
10. В **перечислены** раздел панели быстрого запуска выберите **сотрудников** списка, а затем проверьте следующие сведения:  
  
    -   Элемент, добавленные вручную ранее (для Энди средства диспетчера) — по-прежнему в списке.  
  
    -   **Рабочий телефон** и **адрес электронной почты** столбцы не отображаются в этом представлении списка.  
  
     **Обновление** конфигурация развертывания изменяет существующий **сотрудников** экземпляр списка на сайте SharePoint. Если вы использовали **по умолчанию** конфигурации развертывания, а не **обновление** конфигурации, может возникнуть конфликт развертывания. Visual Studio может разрешить конфликт, заменив **сотрудников** списка, а также сам элемент для Энди manager помещениях, будут удалены.  
  
## <a name="cleaning-up-the-development-computer"></a>Очистка компьютера разработчика  
 После завершения тестирования шага развертывания обновления, удалите экземпляр списка и определение списка с сайта SharePoint и удалите расширение шага развертывания из Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Чтобы удалить экземпляр списка на сайте SharePoint  
  
1.  Откройте **сотрудников** списка на сайте SharePoint, если список еще не открыт.  
  
2.  На ленте на сайте SharePoint, выберите **Инструменты списка** , а затем выберите **списка** вкладки.  
  
3.  В **параметры** выберите **параметры списка** элемента.  
  
4.  В разделе **разрешения и управление**, выберите **удалить этот список** команд, выберите **ОК** подтверждения отправки списка в корзину, а затем закройте веб-сайте Обозреватель.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Чтобы удалить определение списка с сайта SharePoint  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **построения**, **Retract**.  
  
     Visual Studio удаляет определение списка с сайта SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Удаление расширения  
  
1.  В экспериментальном экземпляре Visual Studio в строке меню выберите **средства**, **расширения и обновления**.  
  
     Появится диалоговое окно **Расширения и обновления**.  
  
2.  В список расширений, выберите **шаг развертывания обновления для проектов SharePoint**, а затем выберите **удаления** команды.  
  
3.  В появившемся диалоговом окне, выберите **Да** для подтверждения того, что вы хотите удалить расширение, а затем выберите **Перезагрузить сейчас** для завершения удаления.  
  
4.  Закройте оба экземпляра Visual Studio (экспериментальный экземпляр и экземпляр Visual Studio, в котором открыт UpgradeDeploymentStep решения).  
  
## <a name="see-also"></a>См. также  
 [Расширение упаковки и развертывания проектов SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  