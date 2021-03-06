---
title: "Инструменты R для Visual Studio. Параметры | Документы Майкрософт"
description: "Ссылка на параметры в Visual Studio для языка R и связанных функций."
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 2a2671c5a234d4a30d64823794880dc648d219b0
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="r-tools-for-visual-studio-options"></a>Инструменты R для Visual Studio. Параметры

Параметры доступны в меню **Инструменты R > Параметры**, а также в меню **Сервис > Параметры** в разделе **Инструменты R**.

  ![Диалоговое окно параметров инструментов R](media/options-dialog.png)

Существуют следующие методы доступа к параметрам и настройкам, относящимся к R. Выберите поле **Показать все параметры** внизу диалогового окна **Параметры**, чтобы отобразить все разделы.

- Параметры форматирования кода (см. [Параметры редактора](editing-r-code-in-visual-studio.md#editor-options)): в меню **"Инструменты" > "Параметры"** последовательно выберите **"Текстовый редактор" > "R" > "Форматирование"**
- Параметры анализа кода (см. [Анализ кода](linting-r-code.md)): в меню **"Инструменты" > "Параметры"** последовательно выберите **"Текстовый редактор" > "R" > "Lint"**
- Параметры расширенного редактора ([описанные в этой статье](#text-editor--r--advanced-options)): в меню **Инструменты > Параметры** выберите **Текстовый редактор > R > Дополнительно**.
- Параметры поведения ([описанные в этом разделе](#r-tools--advanced-options)): в меню **Инструменты R > Параметры** или **Инструменты R > Параметры** прокрутите экран к разделу **Инструменты R**.

Команда **"Инструменты R" > "Параметры обработки и анализа данных"** также затрагивает ряд различных общих параметров в Visual Studio. Эта команда описана в следующем разделе.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>"Инструменты R" > "Параметры обработки и анализа данных"

Пункт меню **"Инструменты R" > "Параметры обработки и анализа данных"** позволяет использовать специальный макет для оптимизации интегрированной среды разработки Visual Studio под потребности специалистов по обработке и анализу данных. В частности, с помощью этого параметра можно открыть окна [Интерактивное окно](interactive-repl-for-r-in-visual-studio.md), [Обозреватель переменных](variable-explorer.md) и [Рабочие области](r-workspaces-in-visual-studio.md).

![Макет окна для обработки и анализа данных в Visual Studio](media/installation-data-scientist-layout-result.png)

Чтобы позже вернуться к другим параметрам Visual Studio, сначала выберите команду **Сервис > Импорт и экспорт параметров**. Для этого выберите **Экспортировать выбранные параметры среды** и укажите имя файла. Чтобы восстановить эти параметры, используйте ту же команду и выберите **Импортировать выбранные параметры среды**. Также можно использовать те же команды, если макет для обработки и анализа данных был изменен, чтобы вернуться к нему позже, вместо того, чтобы использовать команду **Параметры обработки и анализа данных** напрямую.

## <a name="text-editor--r--advanced-options"></a>"Текстовый редактор" > "R" > "Дополнительные параметры"

Эти параметры позволяют настраивать форматирование, IntelliSense, структурирование, отступы и проверку синтаксиса для R.

![Диалоговое окно дополнительных параметров текстового редактора R](media/options-dialog-advanced-text-editor.png)

Каждый параметр отвечает за определенное поведение и может быть включен или отключен. Сведения о том, на что влияет каждый параметр, см. на панели справки внизу диалогового окна. Обратите внимание, что вы можете увеличить панель справки, перетащив ее верхнюю границу.

![Расширенная панель справки в диалоговом окне дополнительных параметров текстового редактора R](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>"Инструменты R" > "Дополнительные параметры"

Меню **"Инструменты R" > "Параметры"** открывает диалоговое окно **Параметры** в параметрах R:

  ![Диалоговое окно параметров инструментов R](media/options-dialog.png)

В следующих разделах описаны различные параметры, доступные на этой странице.

### <a name="debugging"></a>Отладка

Эти параметры определяют обработку значений в [обозревателе переменных](variable-explorer.md) и в окнах отладчика, таких как "Контрольные значения" и "Локальные" (см. раздел [Отладка](debugging-r-in-visual-studio.md)).

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Оценить активные привязки | `True` | Когда выбрано значение `True`, при проверке переменных и свойств всегда отображается самое актуальное значение. Риск заключается в том, что оценка выражений, в зависимости от того, как они реализованы, может привести к побочным эффектам. |
| Показать переменные с префиксом в виде точки | `False` | Указывает, отображаются ли переменные с префиксом `.`. |

### <a name="grid-view"></a>Представление сетки

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Динамическое вычисление | `False` | По умолчанию функция `View(<expression>)` принимает моментальный снимок как кадр данных, который может занимать значительный объем памяти с большими наборами данных. Если задать для этого параметра значение `True`, выражение вычисляется при обновлении сетки для получения только отображаемых данных. Однако при изменении выражения данные также меняются, что может не подойти для выражений канала dplyr. |

### <a name="help"></a>Справка

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Веб-браузер для функции F1 | `Internal` | Управляет отображением справки при поиске терминов с помощью клавиш CTRL + F1. Если задано значение `Internal`, справка отображается в окне инструментов в Visual Studio. Если задано значение `External`, справка отображается в веб-браузере по умолчанию. |
| Строка поиска в Интернете для функции F1 | `R site:stackoverflow.com` | Определяет порядок передачи условий поиска в поисковую систему при нажатии клавиш CTRL + F1 для термина в редакторе. По умолчанию используется строка `R site:stackoverflow.com`, которая добавляет `R` к условию поиска. `site:stackoverflow.com` является директивой для поисковой системы, предписывающей ей ограничить область поиска страницами в домене `stackoverflow.com`. |
| Браузер для справки R | `Automatic` | Управляет отображением справки при поиске в документации по R с помощью клавиши F1, команды `?` или `??`. Если задано значение `Automatic`, справка отображается в соответствующем окне. Например, справка в формате HTML отображается в окне инструментов Visual Studio, а справка в формате PDF отображается в программе для работы с файлами PDF по умолчанию. Если задано значение `External`, справка отображается в веб-браузере по умолчанию. |

### <a name="history"></a>Журнал

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Всегда сохранять журнал | `True` | Определяет, записывает ли RTVS журнал команд в файл `.RHistory` в рабочем каталоге при закрытии проекта. Сохранение журнала происходит даже в том случае, если вы не сохранили проект перед закрытием. |
| Сброс фильтра поиска | `True` | Определяет, следует ли отображать в журнале команд только те команды, подстроки которых соответствуют условию фильтра в диалоговом окне журнала R. Этот параметр определяет, следует ли сбрасывать фильтр поиска в журнале при запуске новой команды или переключаться в новый проект, который инициирует загрузку другого файла `.RHistory`. Значение по умолчанию `True` позволяет свести к минимуму удивление пользователя, когда после выполнения команды с заданным фильтром она не отображается в журнале. |
| Использовать многострочный выбор | `True` | Указывает, можно ли выбирать многострочный оператор в журнале одним щелчком мыши. Также позволяет переходить вверх или вниз в интерактивных окнах по операторам, а не по строкам. |

### <a name="html"></a>HTML

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Браузер для HTML-страниц | `External` | Определяет, где следует отображать содержимое, такое как графики `ggvis`, или приложения `shiny`. При выборе значения `Internal` выходные данные HTML отображаются в окне инструментов в Visual Studio. При выборе значения `External` выходные данные HTML отображаются в браузере по умолчанию. |

### <a name="logging"></a>Ведение журнала

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Регистрация событий | `Normal` | Определяет уровень детализации при ведении журнала, используемый для диагностики ошибок RTVS. При выборе значения по умолчанию `Normal` файл журнала создается в каталоге `TEMP`. Если задано значение `Traffic`, RTVS регистрирует все команды и ответы в текущем сеансе. Эти файлы журналов всегда остаются на компьютере, однако они могут оказаться полезными для диагностики неполадок в RTVS. |

### <a name="markdown"></a>Markdown

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Браузер для предварительного просмотра Markdown | `External` | Определяет, где отображаются выходные данные HTML RMarkdown. При выборе значения `Internal` HTML-документ RMarkdown отображается в окне инструментов в Visual Studio. При выборе значения `External` HTML-документ RMarkdown отображается в браузере по умолчанию. |

### <a name="r-engine"></a>Подсистема R

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Кодовая страница | `(OS Default)` | Задает кодовую страницу (язык) для языка R. По умолчанию используется язык операционной системы. | 
| Отражение CRAN | `(Use .Rprofile)` | Задает зеркало CRAN по умолчанию для установки пакетов. Значение по умолчанию `Use .Rprofile` учитывает параметры отражения CRAN в файле `.RProfile`. |

### <a name="workspace"></a>Рабочая область

| Параметр | Значение по умолчанию | Описание: |
| --- | --- | --- |
| Загружать рабочую область при открытии проекта | `No` | Если выбрано значение `Yes`, при открытии проекта данные сеанса из файла `.RData` загружаются в глобальную среду. |
| Запрос на сохранение рабочей области при сбросе | `Yes` | Если выбрано значение `No`, при нажатии кнопки "Сброс" в интерактивном окне не отображается запрос на сохранение рабочей области. |
| Сохранять рабочую область при закрытии проекта | `No` | Если выбрано значение `Yes`, при закрытии проекта глобальная среда сохраняется в файл `.RData`. |
| Показать диалоговое окно подтверждения перед переключением рабочих областей | `Yes` | Если выбрано значение `No`, при переключении между различными рабочими областями не отображается запрос на подтверждение. См. раздел [Переключение между рабочими областями](r-workspaces-in-visual-studio.md#switching-between-workspaces) |
| Отображение индикатора загрузки компьютера | `False` | Управляет видимостью индикатора загрузки ЦП, памяти или сети в строке состояния. Так как индикатор потребляет сетевой трафик, имеет смысл использовать для него значение `False` в сценариях удаленной работы с лимитным подключением. Для изменения этого параметра необходим перезапуск Visual Studio. |
