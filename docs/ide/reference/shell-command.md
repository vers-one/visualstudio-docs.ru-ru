---
title: "Команда \"Оболочка\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7744feca20a14a85c7a035a9b74ed415a43553b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="shell-command"></a>Команда Shell
Запускает исполняемые программы из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Аргументы  
 `path`  
 Обязательно. Путь и имя исполняемого файла или открываемого документа. Полный путь требуется, если указанный файл не находится в одном из каталогов, заданных в переменной среды PATH.  
  
 `args`  
 Необязательный. Все аргументы, передаваемые в вызванную программу.  
  
## <a name="switches"></a>Переключатели  
 /commandwindow [или] /command [или] /c [или] /cmd  
 Необязательный. Указывает, что выходные данные для исполняемого файла отображаются в окне **Команда**.  
  
 /dir:`folder` [или] /d: `folder`  
 Необязательный. Указывает рабочий каталог, задаваемый при запуске программы.  
  
 /outputwindow [или] /output [или] /out [или] /o  
 Необязательный. Указывает, что выходные данные для исполняемого файла отображаются в окне **Вывод**.  
  
## <a name="remarks"></a>Примечания  
 Параметры /dir /o /c должны быть указаны сразу после `Tools.Shell`. Все, что указано после имени исполняемого файла, передается в виде аргументов командной строки.  
  
 Вместо `Tools.Shell` можно использовать предопределенный псевдоним `Shell`.  
  
> [!CAUTION]
>  Если аргумент `path` указывает путь к каталогу, а также имя файла, следует заключить все имя пути в кавычки ("""), как показано ниже:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Каждый набор из трех двойных кавычек (""") интерпретируется процессором `Shell` как один символ двойной кавычки. Таким образом, предыдущий пример фактически передает в команду `Shell` следующую строку пути:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Если не заключить строку пути в кавычки ("""), Windows будет использовать только часть строки, расположенную до первого пробела. Например, если бы приведенная выше строка пути не была заключена в кавычки должным образом, Windows искала бы файл с именем "Program", расположенный в корневом каталоге C:\. Если бы исполняемый файл C:\Program.exe был реально доступен, даже будучи установленным в результате незаконного изменения, Windows попыталась бы выполнить эту программу вместо требуемой "c:\Program Files\SomeFile.exe".  
  
## <a name="example"></a>Пример  
 Следующая команда использует xcopy.exe, чтобы скопировать файл `MyText.txt` в папку `Text`. Выходные данные xcopy.exe отображаются как в окне **Команда**, так и в окне **Вывод**.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Окно вывода](../../ide/reference/output-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)