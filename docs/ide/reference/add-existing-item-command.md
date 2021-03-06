---
title: "Команда \"Добавить существующий элемент\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a94546b8e480a661c175f946cc376fa92b30cbf8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="add-existing-item-command"></a>Команда Add Existing Item
Добавляет существующий файл в текущее решение и открывает его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Обязательно. Полный путь и имя файла с расширением для элемента, который нужно добавить в текущее решение. Если имя или путь файла содержат пробелы, нужно заключить весь путь в кавычки.  
  
## <a name="switches"></a>Переключатели  
 /e: `editorname`  
 Необязательный. Имя редактора, в котором будет открыт файл. Если аргумент указан, но имя редактора не предоставляется, отображается диалоговое окно **Открыть с помощью**.  
  
 В синтаксической структуре аргумента /e:`editorname` имена редакторов используются в том виде, в каком они отображаются в диалоговом окне **Открыть с помощью**, с заключением в кавычки. Например, чтобы открыть таблицу стилей в редакторе исходного кода, необходимо ввести для аргумента /e:`editorname` следующую строку:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Примечания  
 Когда вы вводите данные, функция автозавершения пытается определить правильный путь и правильное имя файла.  
  
## <a name="example"></a>Пример  
 Этот пример добавляет файл Form1.frm в текущее решение.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)