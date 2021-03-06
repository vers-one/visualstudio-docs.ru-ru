---
title: "Идентификаторы рабочих нагрузок и компонентов для Visual Studio Build Tools 2017 | Документация Майкрософт"
description: "Идентификаторы рабочих нагрузок и компонентов Visual Studio можно использовать для создания классических приложений Windows"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 12/01/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload: multiple
ms.openlocfilehash: 4b41304a893dbee45b7de08edb9a37e07ef8656d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Каталог компонентов для Visual Studio Build Tools 2017

В таблицах на этой странице перечислены идентификаторы, которые можно использовать для установки Visual Studio с помощью командной строки. Обратите внимание, что по мере выхода обновлений для Visual Studio здесь будут появляться новые компоненты.

Также обратите внимание на следующие моменты:

* Каждая рабочая нагрузка имеет свой раздел, за которым приводится идентификатор рабочей нагрузки и таблица компонентов, доступных для этой рабочей нагрузки.
* По умолчанию при установке рабочей нагрузки устанавливаются только **обязательные** компоненты. По вашему желанию вы можете включить в установку **рекомендованные** и (или) **дополнительные** компоненты.
* Мы также добавили отдельный раздел для дополнительных компонентов, которые не связаны с конкретными рабочими нагрузками.

Дополнительные сведения об использовании идентификаторов см. в статье [Использование параметров командной строки для установки версии-кандидата Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Список идентификаторов рабочих нагрузок и компонентов для других продуктов вы найдете в статье [Идентификаторы рабочих нагрузок и компонентов Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>MSBuild Tools

**Идентификатор.** Microsoft.VisualStudio.Workload.MSBuildTools

**Описание.** Предоставляет средства для сборки приложений на основе MSBuild.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.27019.1 | Обязательно
Microsoft.VisualStudio.Component.CoreBuildTools | Ядро Visual Studio Build Tools | 15.0.27005.2 | Обязательно
Microsoft.VisualStudio.Component.Roslyn.Compiler | Компиляторы Roslyn для C# и Visual Basic | 15.0.27019.1 | Обязательно
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# - компилятор | 15.0.27019.1 | Optional

## <a name="net-core-build-tools"></a>Средства сборки .NET Core

**Идентификатор:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**Описание:** средства для сборки приложений .NET Core.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0–1.1 | 15.0.26606.0 | Обязательно
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.0.26919.1 | Обязательно
Microsoft.Net.Core.Component.SDK.1x | Средства разработки .NET Core 1.0–1.1 для классических приложений | 15.0.26919.1 | Optional

## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**Идентификатор.** Microsoft.VisualStudio.Workload.VCTools

**Описание.** Создание классических приложений для Windows с помощью набора инструментов Visual C++, библиотеки ATL и дополнительных средств, таких как MFC и C++/CLI.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Основные возможности Visual C++ Build Tools | 15.0.27005.2 | Обязательно
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Распространяемый компонент Visual C++ 2017 с обновлением | 15.0.27019.1 | Обязательно
Microsoft.VisualStudio.Component.Windows10SDK | Универсальная среда выполнения C для Windows | 15.0.26621.2 | Обязательно
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Инструменты статического анализа | 15.0.26208.0 | Рекомендованное
Microsoft.VisualStudio.Component.VC.CMake.Project | Инструменты Visual C++ для CMake | 15.0.27019.1 | Рекомендованное
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Набор инструментов VC++ 2017 версии 141 (x86, x64) | 15.0.27019.1 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | Windows 10 SDK (10.0.16299.0) для Desktop C++ [x86 и x64] | 15.0.27128.1 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C#, VB, JS | 15.0.27128.1 | Рекомендованное
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | Пакет SDK для Windows 10 (10.0.16299.0) для UWP: C++ | 15.0.27128.1 | Рекомендованное
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET и веб-разработка | 15.0.27005.2 | Рекомендованное
Microsoft.Component.VC.Runtime.UCRTSDK | Пакет SDK для Windows Universal CRT | 15.0.27019.1 | Optional
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | Набор инструментов VC++ 2015.3 v140 для настольных ПК (x86, x64) | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Поддержка библиотеки ATL для Visual C++ | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | Поддержка библиотек MFC и ATL (x86 и x64) | 15.0.27005.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (экспериментальная версия) | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | Поддержка C++/CLI | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Модули для стандартной библиотеки (экспериментальная версия) | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | Компиляторы и библиотеки Visual C++ для ARM | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | Компиляторы и библиотеки Visual C++ для ARM64 | 15.0.27019.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Пакет SDK для Windows 10 (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Пакет SDK для Windows 10 (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Пакет SDK для Windows 10 (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Пакет SDK для Windows 10 (10.0.15063.0) для Desktop C++ x86 и x64 | 15.0.27128.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C#, VB, JS | 15.0.27128.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | Пакет SDK для Windows 10 (10.0.15063.0) для UWP: C++ | 15.0.27128.1 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | Пакет SDK для Windows 10 (10.0.16299.0) для Desktop C++ [ARM и ARM64] | 15.0.27128.1 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Пакет SDK для Windows 8.1 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Пакеты SDK для Windows 8.1 и UCRT | 15.0.27019.1 | Optional

## <a name="web-development-build-tools"></a>Средства сборки для веб-разработчиков

**Идентификатор.** Microsoft.VisualStudio.Workload.WebBuildTools

**Описание.** Задачи и целевые объекты MSBuild для построения веб-приложений.

### <a name="components-included-by-this-workload"></a>Компоненты, используемые этой рабочей нагрузкой

Идентификатор компонента | name | Версия | Тип зависимости
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | Пакет SDK для .NET Framework 4.6.1 | 15.0.26621.2 | Обязательно
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Обязательно
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Средства разработки .NET Framework 4.6.1 | 15.0.27005.2 | Обязательно
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | Средства сборки для разработки WCF | 15.0.27019.1 | Обязательно
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Средства сборки для веб-разработчиков | 15.0.26323.1 | Обязательно
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | Рекомендованное
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | Рекомендованное
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | Рекомендованное
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | Рекомендованное
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | Рекомендованное
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Средства разработки для .NET Framework 4–4.6 | 15.0.26606.0 | Рекомендованное
Microsoft.Net.Core.Component.SDK | Средства разработки .NET Core 1.0–1.1 | 15.0.26606.0 | Рекомендованное
Microsoft.VisualStudio.Component.NuGet.BuildTools | Цели и задачи построения NuGet | 15.0.26919.1 | Рекомендованное
Microsoft.Net.Component.3.5.DeveloperTools | Средства разработки для .NET Framework 3.5 | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.2.SDK | Пакет SDK для .NET Framework 4.6.2 | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | Пакет SDK для .NET Framework 4.7.1 | 15.0.27128.1 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.0.27019.1 | Optional
Microsoft.Net.Component.4.7.SDK | Пакет SDK для .NET Framework 4.7 | 15.0.26419.1 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Средства разработки .NET Framework 4.6.2 | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | Средства разработки для .NET Framework 4.7.1 | 15.0.27019.1 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | Средства разработки для .NET Framework 4.7 | 15.0.27005.2 | Optional

## <a name="unaffiliated-components"></a>Самостоятельные компоненты

Здесь перечислены компоненты, которые не используются рабочими нагрузками, но могут быть выбраны в качестве отдельного компонента.

Идентификатор компонента | name | Версия
--- | --- | ---
Microsoft.VisualStudio.Component.VC.Tools.14.11 | Набор инструментов v14.11 для VC++ 2017 версии 15.4 | 15.0.27128.1

## <a name="get-support"></a>Техническая поддержка
Иногда возникают проблемы. При сбое установки Visual Studio см. инструкции по [устранению неполадок и исправлению ошибок установки и обновления Visual Studio 2017](troubleshooting-installation-issues.md). Если описанные выше действия не устраняют проблему, вы можете обратиться к нам за помощью в чате в реальном времени (только на английском языке). Дополнительные сведения см. на [странице поддержки Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ниже приведены несколько дополнительных вариантов:
* Вы можете сообщить о проблемах с продуктом в корпорацию Майкрософт, используя средство [Сообщить о проблеме](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Оно доступно как в Visual Studio Installer, так и в Visual Studio IDE.
* Вы можете оставить предложение о продукте на форуме [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Вы можете просматривать описания проблем в [сообществе разработчиков Visual Studio](https://developercommunity.visualstudio.com/). Там же можно получать ответы на интересующие вас вопросы.
* Вы также можете связаться с нами и другими разработчиками Visual Studio, используя [средство для обсуждения Visual Studio в сообществе Gitter](https://gitter.im/Microsoft/VisualStudio).  (Требуется учетная запись [GitHub](https://github.com/).)

## <a name="see-also"></a>См. также

* [Идентификаторы рабочих нагрузок и компонентов Visual Studio](workload-and-component-ids.md)
* [Руководство администратора Visual Studio](visual-studio-administrator-guide.md)
* [Использование параметров командной строки для установки Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Примеры параметров командной строки](command-line-parameter-examples.md)
* [Создание автономной установки Visual Studio](create-an-offline-installation-of-visual-studio.md)
