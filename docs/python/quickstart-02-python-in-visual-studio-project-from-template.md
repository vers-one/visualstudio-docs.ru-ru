---
title: "Краткое руководство. Создание проекта Python на основе шаблона в Visual Studio | Документация Майкрософт"
description: "Быстро создавайте проекты Python в Visual Studio на основе одного из встроенных шаблонов."
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2af5a7412b6d4a6554d4bc11f5877541a3384115
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Краткое руководство. Создание проекта Python на основе шаблона в Visual Studio

[Установив поддержку Python в Visual Studio 2017](installing-python-support-in-visual-studio.md), можно легко создать проект Python с помощью различных шаблонов.

1. Запустите Visual Studio.

1. Выберите **Файл > Создать > Проект** (CTRL+SHIFT+N). В диалоговом окне **Новый проект** выполните поиск слова "Python" и выберите нужный шаблон. Обратите внимание, что при выборе шаблона отображается его краткое описание. (См. также раздел [Проекты Python](managing-python-projects-in-visual-studio.md#project-templates).)

    ![VS2017 Диалоговое окно "Новый проект" с шаблоном Python](media/projects-new-project-dialog2.png)

1. В рамках этого краткого руководства выполните поиск шаблона "Приложение Python", назначьте проекту имя (например, "MakePI") и расположение, а затем нажмите кнопку **ОК**.

1. Visual Studio создает файл проекта (файл `.pyproj` на диске) вместе с другими файлами, описанными в этом шаблоне. При использовании шаблона "Приложение Python" проект содержит только один пустой файл, названный так же, как и проект. По умолчанию файл открывается в редакторе кода Visual Studio.

    ![Итоговый проект при использовании шаблона приложения Python](media/projects-new-structure.png)

1. Добавьте в открытый файл некоторый код, например приведенный ниже, который вычисляет и отображает 1000 знаков числа Пи:

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Запустите программу, нажав клавиши CTRL+F5 или выбрав пункт меню **Отладка > Запуск без отладки**. Результаты отображаются в окне консоли.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Руководство. Работа с Python в Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>См. также

- [Создание среды для существующего интерпретатора Python](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Установка поддержки Python в Visual Studio 2015 и более ранних версиях](installing-python-support-in-visual-studio.md).
- [Расположения установки](installing-python-support-in-visual-studio.md#install-locations).
