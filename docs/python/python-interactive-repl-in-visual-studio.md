---
title: "Интерактивная среда REPL Python в Visual Studio | Документы Майкрософт"
description: "Практическое руководство по быстрой разработке кода Python в Visual Studio с помощью интерактивного окна (REPL)."
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: e41e4af21a524215550c581b1e29efc2261aaa8f
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2018
---
# <a name="working-with-the-python-interactive-window"></a>Работа с интерактивным окном Python

Visual Studio предоставляет интерактивное окно цикла "чтение — оценка — вывод" (REPL) для каждой среды Python, что улучшает REPL, который вы получаете при выполнении `python.exe` в командной строке. В интерактивном окне (открывается с помощью команд меню **Просмотр > Другие окна > &lt;окружение&gt; Интерактивный**) можно ввести произвольный код Python и немедленно увидеть результаты. Это помогает вам изучать API и экспериментировать с ним, а также интерактивно разрабатывать рабочий код для добавления в проекты.

![Интерактивное окно Python](media/interactive-window.png)

Visual Studio предоставляет ряд режимов REPL Python.

| REPL | Описание: | Редактирование | Отладка | Изображения |
| --- | --- | --- | --- | --- |
| Стандартный | Режим REPL по умолчанию, взаимодействует с Python напрямую | Стандартное редактирование (многострочное редактирование и т. д.) | Да, через `$attach` | Нет |
| Отладка | Режим REPL по умолчанию, взаимодействует с отлаженным процессом Python | Стандартное редактирование | Только отладка | Нет |
| IPython | REPL взаимодействует с серверной частью IPython | Команды IPython, средства Pylab | Нет | Да, встроенные в REPL |
| IPython без Pylab | REPL взаимодействует с серверной частью IPython | Стандартный IPython | Нет | Да, в отдельном окне | 

В этой статье описывается **стандартный** режим REPL и режим **отладки** REPL. Дополнительные сведения о режимах IPython см. в статье [Using Python in the Interactive Window](interactive-repl-ipython.md) (Использование Python в интерактивном окне).

Подробное пошаговое руководство с примерами, включая взаимодействие с редактором, например с помощью клавиш CTRL+ВВОД, см. в разделе [Шаг 3. Использование интерактивного окна REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md). 

|   |   |
|---|---|
| ![значок кинокамеры для видео](../install/media/video-icon.png "Просмотреть видео") | [Просмотрите видео (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567) об интерактивных окнах (2 мин 22 с).|

## <a name="opening-an-interactive-window"></a>Открытие интерактивного окна

Существует несколько способов открыть интерактивное окно для среды.

Первый способ — переключитесь в окно сред Python (**Просмотр > Другие окна > Окружения Python** или сочетания клавиш CTRL+K, CTRL+`) и выберите команду **Открыть интерактивное окно** или нажмите кнопку выбранного окружения.

![Ссылка на интерактивное окно в окне Python Environments (Среды Python)](media/interactive-window-opening.png)

Второй способ — ближе к концу в меню **Просмотр > Другие окна** находится команда **Интерактивное окно Python** для вашей среды по умолчанию, а также команда для перехода в окно среды:

![Пункты меню интерактивного окна после выбора "Просмотр" > "Другие окна"](media/interactive-window-menu.png)

Третий способ — интерактивное окно можно открыть в файле запуска проекта или с помощью отдельного файла, выбрав команду меню **Отладка > Выполнить [файл | проект] в интерактивном окне Python** (SHIFT+ALT+F5):

![Пункт меню Execute Project in Python Interactive (Выполнить проект в интерактивном окне Python)](media/interactive-execute-project.png)

Наконец, можно выбрать код в файле и использовать описанную ниже команду [Send code to interactive](#send-code-to-interactive-command) (Отправить код в интерактивное окно).

## <a name="interactive-window-options"></a>Параметры интерактивного окна

Вы можете управлять различными аспектами интерактивного окна с помощью команды **Инструменты > Параметры > Инструменты Python > Интерактивные окна** (см. [Параметры](python-support-options-and-settings-in-visual-studio.md)):

![Параметры интерактивного окна Python](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Работа с интерактивным окном Python

Открыв интерактивное окно, можно приступить к построчному вводу кода в строках `>>>`. Интерактивное окно выполняет код в каждой строке по мере ввода, включая импорт модулей, определение переменных и т. д.

![Интерактивное окно Python](media/interactive-window.png)

Исключением является ситуация, когда для получения законченного оператора требуются дополнительные строки кода, например, когда оператор `for` заканчивается точкой с запятой, как показано выше. В таких случаях в начале строки отображаются символы `...`, что указывает, что вам нужно ввести дополнительные строки для блока, как показано в четвертой и пятой строке на приведенном выше рисунке. При нажатии клавиши ВВОД в пустой строке блок закрывается и выполняется в интерпретаторе.

> [!Tip]
> Интерактивное окно улучшает обычные условия работы с REPL в командной строке Python, автоматически выделяя отступами операторы, принадлежащие к окружающей области видимости. В журнале (можно отозвать с помощью стрелки вверх) также представлены многострочные элементы, в то время как в среде REPL с командной строкой содержатся только единичные строки.

<a name="meta-commands"></a> Интерактивное окно также поддерживает несколько метакоманд. Все метакоманды начинаются с `$`. Чтобы получить список метакоманд, введите `$help`, а для получения сведений об использовании конкретной команды введите `$help <command>`.

| Метакоманда | Описание: |
| --- | --- |
| `$$` | Вставляет комментарий, благодаря чему можно комментировать код на протяжении всего сеанса. |
| `$attach` | Присоединяет отладчик Visual Studio к процессу окна REPL для включения отладки. |
| `$cls`, `$clear` | Удаляет содержимое окна редактора, не затрагивая журнал и контекст выполнения. |
| `$help` | Выводит список команд или справку по определенной команде. |
| `$load` | Загружает команды из файла и выполняет их до завершения. |
| `$mod` | Переключает текущую область на модуль с указанным именем. |
| `$reset` | Сбрасывает среду выполнения до начального состояния, но сохраняет историю. |
| `$wait` | Ожидает на протяжении как минимум указанного числа миллисекунд. |

Команды также допускают расширение с помощью расширений Visual Studio путем реализации и экспорта `IInteractiveWindowCommand` ([пример](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)).

## <a name="switching-scopes"></a>Переключение областей

По умолчанию интерактивное окно проекта действует в приделах файла запуска проекта, как и при запуске из командной строки. Для автономного файла действия выполняются в рамках этого файла. Во время сеанса REPL можно в любой момент изменить область с помощью раскрывающегося меню в верхней части интерактивного окна:

![Области интерактивного окна](media/interactive-scopes.png)

После импорта модуля, например с помощью команды `import importlib`, в раскрывающемся списке отображаются параметры, позволяющие переключиться в любую область этого модуля. В интерактивном окне появляется сообщение, указывающее новую область, чтобы можно было отследить, как вы попали в определенное состояние во время сеанса.

После ввода `dir()` в области отобразятся допустимые идентификаторы этой области, включая имена функций, классы и переменные. Например, если ввести `import importlib`, за которым следует `dir()`, отобразится следующее:

![Интерактивное окно в области importlib](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Команда Send code to interactive (Отправить код в интерактивное окно)

Помимо выполнения действий непосредственно в интерактивном окне, можно выбрать код в редакторе, щелкнуть правой кнопкой мыши и выбрать команду **Отправить в интерактивное окно** или нажать клавиши CTRL+ВВОД.

![Команда меню "Отправить в Interactive"](media/interactive-send-to.png)

Эта команда также удобна для итеративной или эволюционной разработки кода, включая тестирование кода по мере разработки. Например, после того как вы отправили фрагмент кода в интерактивное окно и увидели его выходные данные, можно нажать стрелку вверх, чтобы отобразить код снова, внести изменения и быстро проверить его, нажав CTRL+ВВОД. (При нажатии клавиши ВВОД в конце входных данных происходит их выполнение, однако при нажатии этой клавиши в середине ввода происходит вставка новой строки.) Внеся все необходимые изменения в код, можно легко скопировать его обратно в файл проекта.

> [!Tip]
> По умолчанию Visual Studio удаляет символы ">>>" и "..." REPL при вставке кода из интерактивного окна в редактор. Это поведение можно изменить на вкладке **Инструменты > Параметры > Текстовый редактор > Python > Дополнительно** с помощью параметра **Вставка удаляет запросы REPL**. См. раздел [Параметры. Прочие параметры](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

При использовании файла кода в качестве электронного блокнота часто требуется отправить целиком небольшой блок кода. Чтобы сгруппировать код, пометьте его как *ячейку кода*, добавив в начало ячейки заметку, начинающуюся с `#%%`, чтобы завершить предыдущую. Ячейки кода можно свернуть и развернуть, а нажав клавиши CTRL+ВВОД внутри ячейки кода, можно отправить всю ее в интерактивное окно и перейти к следующей.

Visual Studio также обнаруживает ячейки кода, начинающиеся с таких заметок, как `# In[1]:`, что соответствует формату, получаемому при экспорте записной книжки Jupyter в файл Python. Такое обнаружение позволяет легко запустить записную книжку из компонента [записных книжек Azure](https://notebooks.azure.com/), скачав ее в виде файла Python, открыв в Visual Studio и используя сочетание клавиш CTRL+ВВОД для выполнения каждой ячейки.

![Интерактивные ячейки кода](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>Поведение IntelliSense

В интерактивном окне применяется технология IntelliSense на основе используемых объектов, в отличие от редактора кода, в котором IntelliSense основана только на анализе исходного кода. Эти предложения в интерактивном окне более точные, особенно при работе с динамически создаваемым кодом. Недостаток заключается в том, что функции с побочными эффектами (например, запись сообщений) могут повлиять на процесс разработки.

Если это проблема, измените параметры, выбрав **Инструменты > Параметры > Инструменты Python > Интерактивные окна** в группе **Режим завершения**, как описано в разделе [Параметры. Параметры интерактивных окон](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options).
