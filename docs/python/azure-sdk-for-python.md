---
title: "Пакет Azure SDK для Python | Документация Майкрософт"
description: "Пакет SDK Azure для Python — это удобное средство для работы со службами Microsoft Azure из приложений Python на любой платформе."
ms.custom: 
ms.date: 01/22/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: baa206dfbb9caf58ce872d0c9dee22e183403adb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="azure-sdk-for-python"></a>Пакет Azure SDK для Python

Пакет Azure SDK для Python — это удобное средство для использования служб Microsoft Azure и управления ими. Оно поддерживает ОС Windows, Mac OSX и Linux.

## <a name="installation"></a>Установка

Azure SDK устанавливается из [пакетов Python](https://pypi.python.org/pypi/azure).

Чтобы установить **последнюю стабильную версию** (с поддержкой Python 2.7 и 3.x), выполните следующую команду:

```command
pip install azure
```

Также вы можете воспользоваться [инструкцией по установке Python и пакета SDK](https://docs.microsoft.com/azure/python-how-to-install/), предложенной в документации по Azure.

## <a name="documentation"></a>Документация

Документацию можно найти на сайте [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

В [Центре разработчиков для языка Python](http://azure.microsoft.com/develop/python/) также содержится ряд полезных ресурсов, в том числе руководства.

- Создание веб-приложений с помощью [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) и [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Хранилище BLOB-объектов](/azure/storage/storage-python-how-to-use-blob-storage)
- [Хранилище таблиц](/azure/storage/storage-python-how-to-use-table-storage)
- [Хранилище очередей](/azure/storage/storage-python-how-to-use-queue-storage)
- [DocumentDB](/azure/documentdb/documentdb-python-application)
- [Очереди служебной шины](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Разделы и подписки, связанные со служебной шиной Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Управление службами](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Для общедоступных интерфейсов API без документации хорошим источником информации будут модульные тесты, представленные в [репозитории GitHub для пакета SDK](https://github.com/Azure/azure-sdk-for-python).

- [Модульные тесты хранилища](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Модульные тесты Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Модульные тесты управления службами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Модульные тесты управления ресурсами](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Поддержка

Репозиторий для пакета SDK находится по адресу [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Если при использовании пакета SDK у вас возникнут любые проблемы или вопросы, [оставьте в репозитории описание проблем](https://github.com/Azure/azure-sdk-for-python/issues).
