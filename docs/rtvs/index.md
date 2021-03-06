---
title: "Инструменты R для Visual Studio | Документация Майкрософт"
description: "Инструменты R для Visual Studio (RTVS) — это бесплатное расширение с открытым исходным кодом, предоставляющее множество языковых функций, включая IntelliSense, отладку и удаленные рабочие области."
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: hero-article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 7e5fd1c6f2e2d33fe3841923f1b25728ad002f6e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="working-with-r-in-visual-studio"></a>Работа с R в Visual Studio

R — это расширяемый язык и среда для статистических вычислений и работы с графикой. Распространяется бесплатно на условиях лицензии GNU General Public License, пользуется поддержкой сообщества и известен возможностью создавать графику типографского качества, в том числе математические символы и формулы. Дополнительные сведения см. в на сайте [r-project.org](https://www.r-project.org/about.html) и во [введении в R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

Инструменты R для Visual Studio (RTVS) — это бесплатное расширение с [открытым кодом](https://github.com/microsoft/RTVS) для Visual Studio 2017 и Visual Studio 2015 с обновлением 3 (или более поздней версии), которое выпускается на условиях лицензии MIT. (Второй компонент с открытым кодом называется [RHost](https://github.com/microsoft/R-Host), он ссылается на двоичные файлы интерпретатора R и выпускается на условиях лицензии GNU Public License V2.)

> [!Note]
> Сейчас поддержка RTVS предусмотрена только в Visual Studio для Windows. В Visual Studio для Mac эти инструменты не поддерживаются.

Чтобы использовать R в Visual Studio, сделайте следующее.

- [Установите инструменты R](installing-r-tools-for-visual-studio.md).
- Следуйте руководству по [началу работы](getting-started-with-r.md), а также см. статьи [Примеры](getting-started-samples.md) и [Начало работы](getting-started-help.md).

Чтобы узнать больше о функциях R и общих возможностях Visual Studio, перейдите по ссылкам ниже.

| Функция | Описание: | Документация по общим возможностям Visual Studio | 
| --- | --- | --- |
| [Система проектов Visual Studio](r-projects-in-visual-studio.md) | Упорядочивайте файлы и управляйте ими в удобной структуре, используйте полезные шаблоны для таких элементов, как код R, документация R, R Markdown, запросы SQL и хранимые процедуры. Также используйте преимущества [диспетчера пакетов](r-package-manager-in-visual-studio.md) и [интеграции SQL Server](integrating-sql-server-with-r.md).  | [Решения и проекты в Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Рабочая область](r-workspaces-in-visual-studio.md) | RTVS можно привязывать к локальным и удаленным рабочим областям, что позволяет разрабатывать код R локально с небольшими наборами данных, а затем легко выполнять этот код на более мощных компьютерах в облачной среде с гораздо большими наборами данных. | Н/Д |
| [Параметры инструментов R](options-for-r-tools-in-visual-studio.md) | Управляйте различными аспектами RTVS. | [Диалоговое окно "Параметры"](../ide/reference/options-dialog-box-visual-studio.md) |
| [Расширенное редактирование, IntelliSense и фрагменты кода](editing-r-code-in-visual-studio.md) | Включает выделение цветом синтаксических конструкций, [IntelliSense](r-intellisense.md) для всего кода и библиотек, форматирование кода, справку по сигнатурам, переход к определению, поиск всех ссылок, [фрагменты кода](code-snippets-for-r.md) и т. д. | [Создание кода в редакторе кода и текста](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | Документы по R Markdown позволяют предоставлять доступ к результатам данных благодаря интегрированному коду R внутри блоков кода разметки. | Н/Д |
| [Интерактивное окно](interactive-repl-for-r-in-visual-studio.md) | Предоставляет полнофункциональную оболочку REPL для R с возможностью легко запускать код в исходном файле в интерактивном окне. | Н/Д |
| [Визуализация данных](visualizing-data-with-r-in-visual-studio.md) | Построение графиков является неотъемлемой частью интерфейса R, и RTVS поддерживает несколько независимых окон графиков, в каждом из которых есть собственный журнал и возможность перемещать графики между окнами. Графики можно сохранять в виде растровых изображений и PDF-файлов или копировать в буфер обмена как растровые изображения или метафайлы.  | Н/Д |
| [Обозреватель переменных](variable-explorer.md) | Проверяет значения переменных в глобальных областях или областях конкретных пакетов с возможностью просмотра сортируемых таблиц и экспорта в CSV-файл. | Н/Д |
| [Полнофункциональная отладка](debugging-r-in-visual-studio.md) | Включает интеграцию с помощью интерактивного окна. | [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md) |

Дополнительные сведения см. в разделе [Часто задаваемые вопросы](faq.md).

|   |   |
|---|---|
| ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео") | [Посмотрите видео (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) с обзором Инструментов R для Visual Studio (12:36). Также см. [другие видео об Инструментах R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio). |

## <a name="send-us-your-feedback"></a>Отправьте нам свой отзыв.

1. **Раздел проблем на GitHub**. Чтобы команда RTVS быстро получила ваше сообщение, [отправьте проблему на GitHub](https://github.com/Microsoft/RTVS/issues) или используйте меню **Инструменты R > Отзывы**.

1. **Смайлик (нахмуренный смайлик)**. С помощью меню **Инструменты R > Отзывы** можно легко отправить отзыв и присоединить файлы журналов RTVS для помощи в диагностике проблем. (Журналы записываются в архив `%temp%/RTVSlogs.zip`, если вы хотите отправить их отдельно.) Если вы отключили телеметрию Visual Studio с помощью команды меню **Справка > Отзыв > Параметры** или во время установки, то ведение журнала отключено.

1. **Электронная почта**. Вы можете отправить отзыв команде разработчиков по адресу *rtvsuserfeedback@microsoft.com*.
