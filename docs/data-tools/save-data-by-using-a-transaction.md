---
title: "Как: сохранение данных с помощью транзакции | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 9f2373e3a851899d139360caf0f6bb8b6ab0efa5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Как: сохранение данных с помощью транзакции
Сохранение данных в транзакции с помощью <xref:System.Transactions> пространства имен. Используйте <xref:System.Transactions.TransactionScope> участие в транзакции, которая автоматически управляемой объекта.  
  
Проекты не создаются со ссылкой на сборку System.Transactions, поэтому вам нужно вручную добавить ссылку на проекты, использующие транзакции.  
  
Самый простой способ реализации транзакции является создание экземпляра <xref:System.Transactions.TransactionScope> объекта в `using` инструкции. (Дополнительные сведения см. в разделе [инструкции Using](/dotnet/visual-basic/language-reference/statements/using-statement), и [с помощью инструкции](/dotnet/csharp/language-reference/keywords/using-statement).) Код, выполняемый в рамках `using` инструкции участвует в транзакции.  
  
Чтобы зафиксировать транзакцию, вызвать <xref:System.Transactions.TransactionScope.Complete%2A> метод в последнем операторе в с помощью блока.  
  
Для отката транзакции, вызываются исключения до вызова метода <xref:System.Transactions.TransactionScope.Complete%2A> метод.  
  
## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Чтобы добавить ссылку на файл System.Transactions.dll  
  
1.  На **проекта** последовательно выберите пункты **добавить ссылку**.  
  
2.  На **.NET** вкладка (**SQL Server** вкладки для проектов SQL Server), выберите **System.Transactions**и выберите **ОК**.  
  
     В проект добавляется ссылка на файл System.Transactions.dll.  
  
## <a name="to-save-data-in-a-transaction"></a>Чтобы сохранить данные в транзакции  
  
-   Добавьте код для сохранения данных в посредством инструкции, которая содержит транзакции. Ниже показано, как создать и создание экземпляра <xref:System.Transactions.TransactionScope> объекта в с помощью инструкции:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## <a name="see-also"></a>См. также
[Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)  
[Пошаговое руководство. Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md)  