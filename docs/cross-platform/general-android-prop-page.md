---
title: "Общие свойства проекта (Android C++) | Документы Майкрософт"
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-mobile
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 6ec191d4f5deefd959c4647ae98a1626a0bd1d36
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="general-project-properties-android-c"></a>Общие свойства проекта (Android C++)

Свойство. | Описание: | Варианты
--- | ---| ---
Выходной каталог | Указывает относительный путь к выходному каталогу файлов; может включать в себя переменные среды.
Промежуточный каталог | Указывает относительный путь к промежуточному каталогу файлов; может включать в себя переменные среды.
Целевое имя | Задает имя файла, создаваемого проектом.
Конечное расширение | Указывает расширение файла, которое будет создано этим проектом. (Пример: EXE или DLL.)
Расширения для удаления при очистке | Спецификация из подстановочных знаков (разделитель — точка с запятой), определяющая, какие файлы в промежуточном каталоге нужно удалять при очистке или перестроении.
Файл журнала сборки | Определяет файл журнала сборки, в который будет вестись запись, если ведение журнала включено.
Набор инструментов платформы | Задает набор инструментов, используемый для сборки текущей конфигурации; если не указан, используется набор инструментов по умолчанию
Тип конфигурации | Определяет тип выходных данных, создаваемых этой конфигурацией. | **Динамическая библиотека (.so)** — динамическая библиотека (.so)<br>**Статическая библиотека (.a)** — статическая библиотека (.a)<br>**Служебная программа** — служебная программа<br>**Makefile** — файл Makefile<br>
Целевой уровень API | Целевой уровень API NDK Android для этой конфигурации.
Использование STL | Указывает, какую стандартную библиотеку C++ следует использовать для этой конфигурации. | **Минимальная библиотека среды выполнения C++ (система)**<br>**Статическая библиотека среды выполнения C++ (gabi++_static)**<br>**Общая библиотека среды выполнения C++ (gabi++_shared)**<br>**Статическая библиотека среды выполнения STLport (stlport_static)**<br>**Общая библиотека среды выполнения STLport (stlport_shared)**<br>**Статическая библиотека GNU STL (gnustl_static)**<br>**Общая библиотека GNU STL (gnustl_shared)**<br>**Статическая библиотека LLVM libc++ (c++_static)**<br>**Общая библиотека LLVM libc++ (c++_shared)**<br>
Режим Thumb | Создайте код, выполняемый для микроархитектуры Thumb. Применимо только к архитектуре ARM. | **Thumb**<br>**ARM**<br>**Отключено**<br>
