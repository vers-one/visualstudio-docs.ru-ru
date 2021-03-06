---
title: "Использование CTest для C++ в Visual Studio | Документы Майкрософт"
ms.custom: 
ms.date: 11/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
author: mikeblome
ms.openlocfilehash: 529e070a3db1e6587989f8d0c55dc04e6db0388c
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-use-ctest-for-c-in-visual-studio"></a>Использование CTest для C++ в Visual Studio
Система CMake (которая включает в себя CTest) интегрирована в среду IDE Visual Studio как компонент рабочей нагрузки **Разработка классических приложений на C++**. Чтобы установить этот компонент на компьютере, откройте Visual Studio Installer и найдите пункт [Инструменты CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp) в списке компонентов рабочей нагрузки.

Поддержка CMake в Visual Studio не распространяется на систему проектов Visual Studio. Поэтому тесты CTest создаются и настраиваются так же, как в любой среде CMake. Дополнительные сведения об использовании CMake в Visual Studio см. в разделе [Инструменты CMake для Visual C++](/cpp/ide/cmake-tools-for-visual-cpp).

**Visual Studio 2017 версии 15.5**. CTest в настоящее время не интегрируется с **обозревателем тестов**. Вы можете выполнять тесты из главного меню CMake или из контекстного меню файла **CMakeLists.txt** в **обозревателе решений**. Результаты тестов направляются в **окно вывода** Visual Studio.

![Выполнение тестов CTest](media/cpp-cmake-run-tests.png "Выполнение тестов CTest")

## <a name="see-also"></a>См. также
[Создание модульных тестов для C/C++](writing-unit-tests-for-c-cpp.md)