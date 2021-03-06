---
title: "Отображение личных электронных адресов в VLSC"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: "Visual Studio Subscriptions – Why Am I Seeing Hotmail or Gmail Addresses for My Subscribers?"
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 2bfe2f39d432be5fc6ff7b24be2a218d02fce961
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Подписки Visual Studio — почему я вижу адреса моих подписчиков в системах Hotmail и (или) Gmail? 

При переходе компании из Volume Licensing Service Center (VLSC) на новый [портал администрирования подписок](https://manage.visualstudio.com) Visual Studio многих администраторов удивляет наличие сторонних адресов электронной почты (например, Hotmail, Gmail или Yahoo) в поле "Адрес электронной почты для входа" у некоторых подписчиков.

## <a name="cause"></a>Причина

Такая ситуация может сложиться из-за процессов входа, применявшихся в устаревшем интерфейсе для подписчиков MSDN. Пользователи переносятся из VLSC на новый портал без каких-либо изменений. Администраторы могли даже не знать, что пользователи применяли личные учетные записи для доступа к преимуществам подписки. До миграции подписчиков Visual Studio, которая проходила в 2016 году, для успешного использования подписки Visual Studio выполнялись следующие два действия.
1. Администратор "назначал" подписку для конкретного подписчика, привязывая ее к рабочему или учебному адресу электронной почты.
2. Подписчик "активировал" назначенную подписку.

Для активации подписчика использовался следующий процесс.
1. Для входа в систему нужно ввести учетную запись Майкрософт (MSA).
2. Если подписчик не желал использовать в качестве MSA свою рабочую или учебную учетную запись (например, John@contoso.com), ему предоставлялась возможность создать новую MSA или использовать уже существующую.
3. В результате "Адрес электронной почты для входа" у таких пользователей отличался от "назначенного адреса электронной почты".

> [!NOTE] 
> Новый интерфейс для подписчиков, реализованный на портале [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs), поддерживает оба типа удостоверений: рабочие или учебные учетные записи и учетные записи Майкрософт (MSA).

Поскольку при миграции в новый интерфейс администратор переносит данные из VLSC на основе "адреса электронной почты для входа", после такой миграции администратор обнаруживает в учетных записях личные адреса. Ранее все они были незаметны, а в новом пользовательском интерфейсе их хорошо видно.

## <a name="solution"></a>Решение

Чтобы устранить проблему, измените сведения о подписчиках и внесите правильные адреса электронной почты для входа.  Такие изменения можно выполнять отдельно для каждого подписчика или в пакетном режиме. Подробные описания этих процессов вы найдете в статье [Изменение назначений для подписок Visual Studio](/visualstudio/subscriptions/edit-license).  

Обновив для подписчиков адреса электронной почты, не забудьте уведомить их об изменении данных для входа в систему.  