---
title: "Советы и рекомендации по реализации подключаемого модуля системы управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e406bc0cd5d7e4cb082e1f5e34fa6645538d02ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Рекомендации по реализации подключаемого модуля системы управления версиями
Следующие технические сведения помогут вам надежно реализация системы управления версиями, подключаемый модуль в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Проблемы с управления памятью  
 В большинстве случаев среда разработки (IDE), являющийся вызывающего объекта, освобождает и выделяет память. Подключаемый модуль системы управления версиями возвращает строки и других элементов в буферы, выделенные вызывающим объектом. Исключения приведены в описания конкретных функций, где они возникают.  
  
## <a name="arrays-of-file-names"></a>Массив имен файлов  
 Если передается массив файлов, не передается как непрерывный массив имен файлов. Передается как массив указателей на имена файлов. Например, в [SccGet](../extensibility/sccget-function.md), имена файлов, передаются по `lpFileNames` параметр, где `lpFileNames` является указателем на `char **`. `lpFileNames`[0] — это указатель на имя, `lpFileNames`[1] — это указатель на имя второго и т. д.  
  
## <a name="large-model"></a>Большой модели  
 Все указатели являются 32 бита, даже на 16-разрядных операционных системах.  
  
## <a name="fully-qualified-paths"></a>Полные пути  
 Где имена файлов или каталогов, указываются в виде аргументов, они должны быть полные пути или UNC-пути, без конечную обратную косую черту. Он отвечает системы управления версиями для преобразования их в относительные пути, если это требование для базовой системы управления версиями.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Укажите полный путь для зарегистрированной библиотеки DLL  
 Интегрированной среды разработки больше не загружает библиотеки DLL из относительные пути (например,.\NewProvider.dll). (Например, C:\Providers\NewProvider.dll), необходимо указать полный путь к библиотеке DLL. Это требование повышает безопасность, интегрированной среды разработки, так как загрузку элемента управления источником олицетворяемых или несанкционированного библиотеки DLL.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Проверяет наличие существующего VSSCI подключаемого модуля при установке подключаемого модуля системы управления версиями  
 Пользователь, который планируется установить подключаемый модуль системы управления версиями возможно уже существующего источника подключаемый модуль системы управления на компьютере. Программа установки (программа установки) для подключаемого модуля, создаваемые следует проверить наличие существующих значений для ключей реестра. Эти ключи уже заданы, программы установки необходимо обратиться пользователь необходимость регистрации подключаемого модуля в качестве подключаемого модуля управления версиями по умолчанию и заменить еще не установлен.  
  
## <a name="error-result-codes-and-reporting"></a>Коды ошибок результатов и отчетов  
 `SCC_OK` Возвращаемое код функции управления источника указывает, что операция завершилась успешно для всех файлов. Если операция завершается с ошибкой, он должен вернуть последний код ошибки.  
  
 Правило для создания отчетов — это том, что при возникновении ошибки в Интегрированной среде разработки, интегрированной среды разработки отвечает за сообщить о нем. При возникновении ошибки в системе управления версиями, подключаемый модуль системы управления версиями отвечает за сообщить о нем. Для экземпляра «не в данный момент выбраны файлы» должны выводиться в интегрированной среде разработки, тогда как «этот файл уже извлечен» должны выводиться подключаемым модулем.  
  
## <a name="the-context-structure"></a>Структура контекста  
 При вызове [SccInitialize](../extensibility/sccinitialize-function.md), вызывающий объект передает `ppvContext` параметра, который является неинициализированный дескриптор значение void. Подключаемый модуль системы управления версиями можно пропустить этот параметр или его можно выделить структуру любого типа и поместить указатель к этой структуре в указатель, переданный. Интегрированная среда разработки не поддерживает эту структуру, но он передает указатель на эту структуру в каждый вызов в подключаемом модуле. Это обеспечивает ценные контекстных данных кэша для подключаемого модуля, его можно использовать для сохранения сведений о глобальное состояние которого сохраняется в вызовах функций без использования глобальных переменных. Подключаемый модуль отвечает за освобождение структуры при вызове [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Если подключаемый модуль наборы `SCC_CAP_REENTRANT` бит в [SccInitialize](../extensibility/sccinitialize-function.md) (в частности, в `lpSccCaps` параметра), несколько структур контекста используются для отслеживания всех проектов, которые открыты.  
  
## <a name="bitflags-and-other-command-options"></a>Битовые флаги и другие параметры команды  
 Для каждой команды такие как [SccGet](../extensibility/sccget-function.md), Интегрированной среде разработки можно задать множество параметров, которые изменяют поведение команды.  
  
 API-Интерфейс поддерживает установку определенных параметров с интегрированной средой разработки через `fOptions` параметра. Эти параметры описаны в [битовые флаги, используемые определенные команды](../extensibility/bitflags-used-by-specific-commands.md) вместе с командами, которые они влияют на. Как правило это параметры, для которых пользователь не будет предлагаться.  
  
 Наиболее пользовательских параметров не определены таким образом, поскольку они зависят от широко подключаемые модули управления версиями. Таким образом, является рекомендуемым механизмом **Дополнительно** кнопки. Например, в **получить** диалоговое окно, интегрированная среда разработки отображает только сведения, которые он поддерживает, но он также отображает **Дополнительно** кнопку, если подключаемый модуль имеет параметры для этой команды. Когда пользователь щелкает **Дополнительно** кнопку вызовы IDE [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) включить систему управления версиями подключаемого модуля, чтобы запрашивать у пользователя сведения, такие как битовые флаги или даты и времени. Подключаемый модуль возвращает эту информацию в структуру, которая передается обратно во время `SccGet` команды.  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)