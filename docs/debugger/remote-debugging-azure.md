---
title: "Удаленная отладки ASP.NET Core для служб IIS и Azure | Документы Microsoft"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0527d33e47ce42449f2ae2bb75ee3e342b04c2b
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/29/2017
---
# <a name="remote-debug-aspnet-core-on-iis-and-azure-in-visual-studio-2017"></a>Удаленная отладка ASP.NET Core для служб IIS и Azure в Visual Studio 2017 г.
Развертывание веб-приложения ASP.NET на компьютере Windows Server с IIS и настроить его для удаленной отладки. В этом руководстве объясняется, как установить и настроить приложение ASP.NET Core Visual Studio 2017 г., развернуть его в службах IIS с помощью Azure и присоединить удаленный отладчик из Visual Studio.

> [!WARNING]
> Не забудьте удалить ресурсы Azure, созданные после завершения действия в этом учебнике. Таким образом можно избежать дополнительной ненужных затрат.

В этом разделе показано как:

* Удаленная отладка ASP.NET Core на службу приложений Azure

* Удаленная отладка ASP.NET Core на Виртуальной машине Azure

Для службы приложений Azure необходимо развернуть приложение из Visual Studio в Azure, но необходимо вручную установить или настроить IIS или удаленный отладчик (эти компоненты, были представлены пунктирной линией), как показано на следующем рисунке.

![Компоненты удаленной отладки](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

Для виртуальной Машины Azure необходимо развернуть приложение из Visual Studio в Azure, а также необходимо вручную установить роль IIS и удаленным отладчиком, как показано на следующем рисунке.

![Компоненты удаленной отладки](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

> [!NOTE]
> Отладке ASP.NET Core в Azure Service Fabric см. в разделе [отладки удаленного приложения Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

### <a name="requirements"></a>Требования

Отладка между двумя компьютерами, подключенными через прокси-сервер не поддерживается. Отладка в различных странах через высокой задержкой или низкой пропускной способностью, таких как удаленный доступ к Интернету, либо через Интернет не рекомендуется и может произойти сбой или медленную неприемлемо. Полный список требований см. в разделе [требования](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Создание приложения ASP.NET Core на компьютере Visual Studio 2017 г. 

1. Создание нового приложения ASP.NET Core. (Выберите **файл > Создать > проект**, а затем выберите **Visual C# > Web > веб-приложения ASP.NET Core (.NET Core)**).

    В **ASP.NET Core** шаблонов выберите пункт **веб-приложение**.

2. Убедитесь, что **Включение поддержки Docker** — **не** выбранного и что **проверки подлинности** равно **без проверки подлинности**.

3. Назовите проект **MyASPApp** и нажмите кнопку **ОК** для создания нового решения.

4. Откройте файл About.cshtml.cs и установите точку останова в `OnGet` метода (в старые шаблоны откройте HomeController.cs вместо и задать точку останова в `About()` метода).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a>Удаленная отладка ASP.NET Core в службе приложений Azure

Из Visual Studio можно быстро публиковать и отладка приложения, чтобы полностью подготовленные экземпляр IIS. Однако предустановку конфигурации IIS и его нельзя настроить. Подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure, с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Если требуется возможность настройки IIS, попробуйте отладить [виртуальной Машины Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug"></a>Чтобы развернуть приложение и удаленной отладки

1. В Visual Studio, щелкните правой кнопкой мыши узел проекта и выберите команду **публикации**.

2. Выберите **службу приложений Microsoft Azure** из **публикации** выберите **создать новый**и следуйте инструкциям на экране для публикации.

    Подробные инструкции см. в разделе [развернуть веб-приложение ASP.NET Core в Azure, с помощью Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. В **обозревателя серверов**, щелкните правой кнопкой мыши в экземпляре приложения и выберите **подключить отладчик**.

4. В работающем приложении ASP.NET, щелкните ссылку, чтобы **о** страницы.

    В Visual Studio должна быть достигнута точка останова.

    Ну вот! Остальные шаги в этом разделе применяются к удаленную отладку на Виртуальной машине Azure.

## <a name="BKMK_azure_vm"></a>Удаленная отладка ASP.NET Core на Виртуальной машине Azure

Можно создать Azure VM для Windows Server и затем установить и настройки служб IIS и другие необходимые программные компоненты. Это занимает больше времени, чем развертывание для службы приложения Azure и требует выполните оставшиеся действия в этом учебнике.

Во-первых, выполните действия, описанные в [установки и запуска IIS](/azure/virtual-machines/virtual-machines-windows-hero-role).

Если открыть порт 80 в группу безопасности сети, также можно откройте порт 4022 удаленного отладчика. В этом случае не придется открыть его позже.

### <a name="update-browser-security-settings-on-windows-server"></a>Обновить параметры безопасности браузера в Windows Server

В зависимости от настройки безопасности браузера, он может сэкономить время, чтобы добавить следующие надежные сайты в браузер, поэтому можно легко загрузить программное обеспечение, описанный в этом учебнике. Возможно, потребуется доступ к этим сайтам:

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- загружаемые

При использовании Internet Explorer, можно добавить надежных сайтов, перейдя **свойства обозревателя > Безопасность > надежных узлов > сайтов**. Эти шаги для других браузеров различаются. (Если требуется загрузить более раннюю версию удаленного отладчика из my.visualstudio.com некоторые дополнительные надежные сайты необходимы для входа.)

При загрузке программного обеспечения, можно получить запросы на предоставление разрешения на загрузку различные сценарии веб-сайт и ресурсы. В большинстве случаев эти дополнительные ресурсы не требуется устанавливать программное обеспечение.

### <a name="install-aspnet-core-on-windows-server"></a>Установка ASP.NET Core в Windows Server

1. Установка [.NET Core Windows Server, где размещены](https://aka.ms/dotnetcore-2-windowshosting) пакета на хост-системы. Пакет для установки среды выполнения .NET Core, основной библиотеке .NET и модуль ASP.NET Core. Более подробные инструкции см. в разделе [публикация в службах IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Если система не использует подключение к Интернету, загрузка и установка  *[Visual C++ 2015 распространяемый компонент Microsoft](https://www.microsoft.com/download/details.aspx?id=53840)*  перед установкой пакета .NET Core Windows Server, где размещены.

3. Перезагрузку системы (или выполните **net stop был /y** следуют **net start w3svc** из командной строки, чтобы отобразить изменение в системе путь).

### <a name="BKMK_install_webdeploy"></a>(Необязательно) Установка веб-развертывания 3.6 в Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a>Настройка веб-сайта ASP.NET на сервере Windows Server

1. Откройте **Диспетчер служб IIS** и перейдите к разделу **Сайты**.

2. Щелкните правой кнопкой мыши узел **Веб-сайт по умолчанию** и выберите команду **Добавить приложение**.

3. Задать **псевдоним** на **MyASPApp** и поле пула приложения **без управляемого кода**. Задать **физический путь** для **C:\Publish** (где будут развернуты позднее проекта ASP.NET).

4. С сайта, выбранного в диспетчере служб IIS, выберите **изменение разрешений**и убедитесь, что учетная запись IUSR, IIS_IUSRS или пользователь, настроен для пула приложений имеет полномочному пользователю с правами на чтение и выполнение.

    Если вы не видите одному из этих пользователей с доступом, выполните действия, чтобы добавить IUSR в качестве пользователя с правами на чтение и выполнение.

### <a name="bkmk_webdeploy"></a>(Необязательно) Публикация и развертывание приложения с помощью веб-развертывание из Visual Studio

Если вы установили веб-развертывания с помощью установщика веб-платформы, можно развернуть приложение непосредственно из Visual Studio.

1. Запустите Visual Studio с повышенными привилегиями и повторно открыть проект.

    Это может потребоваться для развертывания приложения с помощью веб-развертывания.

2. В **обозревателе решений**щелкните правой кнопкой мыши узел проекта и выберите пункт **Опубликовать**.

3. Для **выберите цель публикации**выберите **виртуальной машине Microsoft Azure** и нажмите кнопку **публикации**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. В диалоговом окне выберите виртуальную Машину Azure, созданной ранее.

4. Введите параметры конфигурации исправления для настройки виртуальной Машины Azure и IIS.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Если имя узла не разрешается при попытке проверить в следующий шаги **сервера** текстовое поле, попробуйте использовать IP-адрес. Убедитесь, что используется порт 80 в **сервера** текстовое поле и убедитесь, что в брандмауэре открыт порт 80.

6. Нажмите кнопку **Далее**, выберите **отладки** конфигурации и выберите **удалить дополнительные файлы в месте назначения** под **опубликовать файл** Параметры.

5. Нажмите кнопку **Prev**, а затем выберите **проверки**. Если проверка прошла установку подключения, можно попытаться опубликовать.

6. Нажмите кнопку **публикации** для публикации приложения.

    Вкладка «Вывод» отображается при публикации прошла успешно, и в браузере откроется приложение.

    Если возникает ошибка, в которых упоминаются веб-развертывание, повторно проверьте действия установки веб-развертывания и убедитесь, что [правильные порты открыты](#bkmk_openports) находятся на сервере.

    Если приложение выполняет развертывание успешно, но работает неправильно, повторно проверьте, что службы IIS и проекта Visual Studio используется одна и та же версия ASP.NET. Если это не проблема, возможно, проблема с вашей конфигурации IIS или конфигурации веб-сайта. На сервере Windows Server откройте веб-сайта из IIS для сообщений об ошибках, а затем повторно проверьте описание предыдущих шагов.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Необязательно) Публикация и развертывание приложения путем публикации в локальную папку из Visual Studio

Если вы не используете веб-развертывания, необходимо опубликовать и развертывание приложения с помощью файловой системы или других средств. Можно начать с создания пакета в файловой системе и затем развернуть пакет вручную или использовать другие средства, такие как PowerShell, XCopy или RoboCopy. В этом разделе предполагается, что пакет выполняется копирование вручную в случае, если вы не используете веб-развертывания.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Загрузите и установите инструменты удаленной отладки на Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>Настройка удаленного отладчика на Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Если необходимо добавить разрешения для других пользователей, изменение режима проверки подлинности, или номер порта удаленного отладчика, в разделе [настроить удаленный отладчик](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Подключение к приложению ASP.NET с компьютера с Visual Studio

1. На компьютере с Visual Studio, откройте **MyASPApp** решения.
2. В Visual Studio щелкните **Отладка > присоединить к процессу** (Ctrl + Alt + P).

    > [!TIP]
    > В Visual Studio 2017 г., вы можете повторно присоединить с тем же процессом, ранее присоединена к с помощью **Отладка > повторно присоединиться к процессу...** (Shift + Alt + P). 

3. Задайте для поля квалификатор  **\<имя удаленного компьютера >: 4022**.
4. Нажмите кнопку **Обновить**.
    В окне **Доступные процессы** должен появиться ряд процессов.

    Если вы не видите все процессы, попробуйте использовать IP-адрес вместо имени удаленного компьютера (порт является обязательным). Можно использовать `ipconfig` в командной строке, чтобы получить адрес IPv4.

    Если вы хотите использовать **найти** кнопки, может потребоваться [откройте порт UDP 3702](#bkmk_openports) на сервере.

5. Установите флажок  **Показать процессы, запущенные всеми пользователями**.
6. Введите имя процесса, чтобы быстро найти первую букву **dotnet.exe** (для ASP.NET Core).
    >Примечание: Для приложения ASP.NET Core предыдущее имя процесса было dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Нажмите кнопку **Присоединить**.

8. Откройте веб-сайт удаленного компьютера. В браузере, перейдите к **http://\<имя удаленного компьютера >**.
    
    Должна открыться веб-страница ASP.NET.
9. В работающем приложении ASP.NET, щелкните ссылку, чтобы **о** страницы.

    В Visual Studio должна быть достигнута точка останова.

### <a name="bkmk_openports"></a>Устранение неполадок: Откройте требуемых портов в Windows Server

В большинстве установок необходимые порты открыты путем установки ASP.NET и удаленный отладчик. Тем не менее если приложение будет размещено за брандмауэром Устранение неполадок развертывания, может потребоваться убедитесь, что необходимые порты открыты.

На виртуальной Машине Azure, необходимо открыть порты, через [сетевой группы безопасности](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Необходимые порты:

- 80 - требуется для служб IIS
- 4022 - необходимых для удаленной отладки из Visual Studio 2017 г. (см. [назначение портов удаленного отладчика](../debugger/remote-debugger-port-assignments.md) для получения дополнительной информации).
- UDP 3702 - порта (необязательно) обнаружения позволяет **найти** кнопку при присоединении удаленного отладчика в Visual Studio.

Кроме того эти порты уже открывать путем установки ASP.NET:
- 8172 - (требуется необязательно) для веб-развертывания для развертывания приложения из Visual Studio
