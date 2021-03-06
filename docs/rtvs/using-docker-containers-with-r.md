---
title: "Инструменты R для Visual Studio и контейнеры Docker | Документы Майкрософт"
description: "Порядок настройки контейнеров Docker для R и подключение к ним с помощью Visual Studio."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author:
- kraigb
- karthiknadig
ms.author:
- kraigb
- karthiknadig
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 85db40a5e5b4fa05260bd62ff9857cc9b1ffebcd
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="using-docker-containers-with-r-tools-for-visual-studio"></a>Использование контейнеров Docker с инструментами R для Visual Studio

Инструменты R для Visual Studio (RTVS) версии 1.3 и более поздних версий при наличии [Docker для Windows](https://www.docker.com/docker-windows) поддерживают работу с контейнерами Docker.

## <a name="creating-a-container"></a>Создание контейнера

1. Нажмите кнопку **Контейнеры…** в правой части окна **Рабочие области** (**"Инструменты R" > "Windows" > "Рабочие области"**). Если у вас не установлено решение Docker для Windows, окно сообщит вам об этом и предоставит ссылку для загрузки. Установка Docker может потребовать перезагрузки компьютера.

    ![Окно "Рабочие области" в инструментах R для Visual Studio (VS2017) с командой "Контейнеры"](media/container-workspaces-window.png)

1. В окне **Контейнеры** выберите **Создать**:

    ![Команда "Создать" в окне "Контейнеры"](media/containers-window-create.png)

1. Заполните в диалоговом окне нужные сведения и выберите **Создать**. Введенные учетные данные также используются для создания учетной записи Linux, с которой вы позже будете входить в систему.

    ![Указание имени контейнера и учетных данных при создании контейнера](media/containers-window-create-fill.png)

1. Сборка образа в RTVS может занять некоторое время. Окно **Вывод** в Visual Studio отображает ход выполнения, но при длительной загрузке образов оно может практически не меняться, и вам нужно будет подождать. После сборки образа RTVS запускает контейнер, который отображается в окне **Контейнер**. Элементы управления справа останавливают, удаляют или перезапускают контейнер.

    ![Окно "Контейнеры" с созданным контейнером](media/containers-window-created.png)

## <a name="connecting-to-a-container"></a>Подключение к контейнеру

1. Раздел **Локальные работающие контейнеры** окна **Рабочие области** показывает контейнеры с запущенной управляющей программой RTVS на порте 5444. (Сведения о настройке управляющей программы см. в разделе [Удаленная служба R для Linux](setting-up-remote-r-service-on-linux.md).)

    ![Окно "Рабочие области" с доступными контейнерами](media/workspaces-window-running-containers.png)

1. Чтобы подключиться к контейнеру, дважды щелкните его имя или нажмите справа от него кнопку со стрелкой вперед. После подключения вы увидите **Интерактивное окно R** (см. раздел [Работа с интерактивным окном R](interactive-repl-for-r-in-visual-studio.md)):

    ![Окно "Рабочие области" и окно REPL, открытые для контейнера](media/workspaces-window-container-connected.png)

## <a name="using-custom-built-images"></a>Использование пользовательских образов

RTVS поддерживает обнаружение и управление для контейнеров, созданных с помощью пользовательских образов, например образа microsoft/rtvs, описываемого в файле Docker ниже. Используемый здесь базовый образ содержит предустановленные rtvs-daemon, R 3.4.2 и общие пакеты R. **Примечание**. Измените показанные здесь имя пользователя и пароль.

```docker
FROM microsoft/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

Используйте для сборки образа следующую команду, изменив по своему выбору имя контейнера (аргумент `--name`):

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

Аргумент `-p 6056:5444` сопоставляет порт 6056 с внутренним портом 5444, используемым RTVS для обнаружения rtvs-daemon. Все контейнеры, предоставляющие порт контейнера 5444, перечислены в окне **Рабочие области**. Затем вы можете подключиться к контейнеру в окне **Рабочие области**, используя `<<unix>>\ruser1` в качестве имени пользователя и "foobar" в качестве пароля, если вы не указали другие учетные данные в файле Docker.
