---
title: "Общие сведения об интегрированной среде разработки Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a74d123d8cb0055f01619bae25b9a1bda54b35f4
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Краткое руководство. Знакомство с интегрированной средой разработки Visual Studio

Из этого краткого (на 5–10 минут) описания возможностей среды разработки Visual Studio (IDE) вы узнаете о некоторых окнах, меню и других элементах пользовательского интерфейса.

## <a name="start-page"></a>Начальная страница

Первое, что вы увидите после запуска Visual Studio, скорее всего, будет начальной страницей. Начальная страница — это отправная точка для поиска команд и файлов проекта, к которым вам нужно получить быстрый доступ. В разделе **Последние** отображаются проекты и папки, с которыми вы недавно работали. В разделе **Новый проект**, можно щелкнуть ссылку, чтобы открыть соответствующее диалоговое окно, а в разделе **Открыть** можно открыть существующий проект или папку с кодом. Справа находится веб-канал с последними новостями для разработчиков.

![Начальная страница VS](media/quickstart-IDE-start-page.png)

Если вы закроете начальную страницу и захотите снова открыть ее, можно воспользоваться меню **Файл**.

![меню "Файл"](media/quickstart-IDE-file-menu-large.png)

Чтобы продолжить изучение IDE, давайте создадим новый проект.

1. На **начальной странице** в поле поиска в разделе **Новый проект** введите `console`, чтобы отфильтровать список типов проектов. Выберите C# или VB **Консольное приложение (.NET Framework)**. (Кроме того, если вы работаете с C++, Javascript или другим языком разработки, вы можете создать проект на одном из этих языков. Рассматриваемый нами пользовательский интерфейс выглядит одинаково для всех языков.)

1. В диалоговом окне **Новый проект** оставьте имя проекта по умолчанию и нажмите кнопку **ОК**.

   Будет создан проект. В окне **Редактор** откроется файл с именем **Program.cs** или **Program.vb**. В этом окне отображается содержимое. Кроме того, здесь вы можете выполнять основную часть работы с кодом в Visual Studio.

## <a name="solution-explorer"></a>обозреватель решений

В обозревателе решений отображается графическое представление иерархии файлов и папок в проекте, решении или папке с кодом. В обозревателе решений можно просматривать эту иерархию и переходить к нужным файлам.

![обозреватель решений](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Меню

В меню в верхней части IDE сгруппированы команды по категориям. Например, в меню **Проект** содержатся команды, связанные с проектом, над которым вы работаете. В меню **Инструменты** можно настроить IDE, выбрав **Параметры**. Также можно включить в установку нужные компоненты, выбрав **Получить средства и компоненты**.

![Строка меню](media/quickstart-IDE-menu-bar.png)

Откроем окно списка ошибок, выбрав в меню **Представление** пункт **Список ошибок**.

## <a name="error-list"></a>Список ошибок

В списке ошибок отображаются ошибки, предупреждения и сообщения о текущем состоянии кода. Если в файле или любой другой части проекта будут обнаружены ошибки (например, опечатка в коде), они будут перечислены здесь.

![Список ошибок](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>окно выходных данных

В окне вывода отображаются выходные сообщения о сборке и управлении версиями.

Давайте создадим проект, чтобы просмотреть некоторые выходные данные, записанные в журнал. В меню **Построение** выберите пункт **Построить решение**. В окне вывода автоматически отобразится сообщение об успешном выполнении сборки.

![Окно выходных данных](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Быстрый запуск

Поле быстрого запуска — это быстрый и простой способ для выполнения разных операций в IDE. Сюда можно вводить текст, связанный с тем, что вы планируете делать, чтобы получить список соответствующих возможностей. Предположим, нам нужно детализировать выходные данные о сборке, чтобы отобразить дополнительные сведения о функциях нашей сборки, записанные в журнале:

1. Введите `verbosity` в поле **Быстрый запуск**и выберите **Проекты и решения -> Сборка и запуск** в разделе **Параметры**.

   ![Поле "Быстрый запуск"](media/quickstart-IDE-quick-launch.png)

   На странице **Сборка и запуск** откроется диалоговое окно **Параметры**.

1. В разделе **Степень подробности сообщений при сборке проекта MSBuild** выберите значение **Обычная** и нажмите кнопку **ОК**.

1. Теперь мы создадим проект еще раз, щелкнув правой кнопкой мыши проект **ConsoleApp1** в **обозревателе решений** и выбрав **Перестроить** в контекстном меню.

   На этот раз в окне вывода отобразятся более подробные сведения из журнала, связанные с процессом сборки. В нашем случае — о том, какие файлы были скопированы в определенное расположение.

## <a name="send-feedback-menu"></a>Меню "Отправить отзыв"

Если у вас возникли проблемы при использовании Visual Studio или есть предложения по улучшению этого продукта, вы можете использовать меню **Отправить отзыв** в верхней части IDE (рядом с полем быстрого запуска).

![Меню "Отправить отзыв"](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Следующие шаги

Мы рассмотрели лишь некоторые из возможностей Visual Studio IDE, чтобы вы могли получить некоторое представление о пользовательском интерфейсе. Для дальнейшего ознакомления:

- Вы можете перейти к разделу документации по VS, посвященному общим элементам пользовательского интерфейса, чтобы узнать больше о таких элементах управления, как [список ошибок](../ide/reference/error-list-window.md), [окно вывода](../ide/reference/output-window.md), [окно свойств](../ide/reference/properties-window.md) и [диалоговое окно параметров](../ide/reference/options-dialog-box-visual-studio.md).

- Дополнительные сведения об IDE, включая инструкции по отладке, см. в статье [Обзор возможностей интегрированной среды разработки Visual Studio](../ide/visual-studio-ide.md).

## <a name="see-also"></a>См. также

[Краткое руководство. Персонализация IDE](../ide/personalizing-the-visual-studio-ide.md)  
[Краткое руководство. Написание кода в редакторе](../ide/quickstart-editor.md)  
[Краткое руководство. Проекты и решения](../ide/quickstart-projects-solutions.md)