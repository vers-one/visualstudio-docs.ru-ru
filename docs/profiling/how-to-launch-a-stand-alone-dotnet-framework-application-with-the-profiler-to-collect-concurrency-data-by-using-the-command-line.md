---
title: "Практическое руководство. Запуск автономного приложения .NET Framework с профилировщиком для сбора данных параллелизма при помощи командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Практическое руководство. Запуск автономного приложения .NET Framework с профилировщиком для сбора данных параллелизма при помощи командной строки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описан порядок использования программ командной строки средств профилирования [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для запуска автономного \(клиентского\) приложения .NET Framework и сбора данных параллелизма потока и процесса.  
  
> [!NOTE]
>  Программы командной строки средств профилирования расположены в подкаталоге \\Team Tools\\Performance Tools каталога установки [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  На 64\-разрядных компьютерах доступны 64\-разрядные и 32\-разрядные версии программ.  Для использования программ командной строки профилировщика необходимо добавить путь к этим программам в переменную среды PATH окна командной строки или указать этот путь при вызове команды.  Для получения дополнительной информации см. [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Пока профилировщик присоединен к приложению, сбор данных можно приостанавливать и возобновлять.  Чтобы завершить сеанс профилирования, необходимо отсоединить профилировщик от приложения и явным образом завершить его работу.  
  
## Запуск приложения с профилировщиком  
 Чтобы запустить целевое приложение .NET Framework с профилировщиком, для задания переменных профилирования .NET Framework используется программа VSPerfClrEnv.exe.  Затем для инициализации профилировщика и запуска приложения используются параметры VSPerfCmd **\/start** и **\/launch**.  Команды **\/start** и **\/launch** с соответствующими параметрами можно указать в одной командной строке.  Для приостановки сбора данных при запуске целевого приложения можно также добавить параметр **\/globaloff**.  Для запуска сбора данных используется отдельная команда **\/globalon**.  
  
#### Запуск приложения с профилировщиком  
  
1.  Откройте окно командной строки.  
  
2.  Запустите профилировщик.  Type:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   Параметр [\/start](../profiling/start.md) обеспечивает инициализацию профилировщика.  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|Включает сбор данных как о конфликтах ресурсов, так и о выполнении потоков.|  
        |**\/start:concurrency,resourceonly**|Включает сбор данных только о конфликтах ресурсов.|  
        |**\/start:concurrency,threadonly**|Включает сбор данных только о выполнении потоков.|  
  
    -   Параметр [\/output](../profiling/output.md)**:**`OutputFile` является обязательным при использовании параметра **\/start**.  Параметр `OutputFile` задает имя и расположение файла с данными профилирования \(VSP\-файла\).  
  
     С параметром **\/start:concurrency** можно использовать любые из следующих параметров.  
  
    |Команда|Описание|  
    |-------------|--------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Задает необязательные домен и имя пользователя учетной записи, которой требуется предоставить доступ к профилировщику.|  
    |[\/crosssession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах входа в систему.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого следует собирать в процессе профилирования.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Используйте только с **\/wincounter**.  Задает интервал времени \(в миллисекундах\) между событиями сбора данных счетчика производительности Windows.  Значение по умолчанию — 500 мс.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает событие трассировки событий Windows, данные которого следует собирать в процессе профилирования.  События трассировки событий Windows собираются в отдельный ETL\-файл.|  
  
3.  Запустите целевое приложение.  Type:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     С параметром **\/launch** можно использовать любые из следующих параметров.  
  
    |Команда|Описание|  
    |-------------|--------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Задает строку, содержащую аргументы командной строки, которые передаются целевому приложению.|  
    |[\/console](../profiling/console.md)|Запускает целевое приложение командной строки в отдельном окне.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Задает версию среды CLR для профилирования, если в приложении загружено несколько версий среды выполнения.|  
  
## Управление сбором данных  
 Пока выполняется целевое приложение, можно управлять сбором данных путем запуска и остановки записи данных в файл с помощью параметров VSPerfCmd.exe.  Управление сбором данных позволяет собирать данные на различных этапах выполнения программы, например при запуске или завершении работы приложения.  
  
#### Запуск и остановка сбора данных  
  
1.  Пары параметров VSPerfCmd, представленные в следующей таблице, используются для запуска и остановки сбора данных.  Задайте каждый параметр в отдельной строке командной строки.  Запуск и приостановка сбора данных могут выполняться неоднократно.  
  
    |Команда|Описание|  
    |-------------|--------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Запускает \(**\/globalon**\) или останавливает \(**\/globaloff**\) сбор данных для всех процессов.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Запускает \(**\/processon**\) или останавливает \(**\/processoff**\) сбор данных для процесса с указанным идентификатором процесса \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** запускает сбор данных для процесса, определяемого идентификатором \(`PID`\) или именем процесса \(ProcName\).  **\/detach** останавливает сбор данных для указанного процесса или, если он не задан, для всех процессов.|  
  
## Завершение сеанса профилирования  
 При завершении сеанса профилирования профилировщик не должен собирать данные.  Чтобы остановить процесс сбора данных параллелизма можно закрыть профилируемое приложение или воспользоваться параметром **VSPerfCmd \/detach**.  Затем для завершения работы профилировщика и закрытия файла с данными профилирования используется параметр **VSPerfCmd \/shutdown**.  Команда **VSPerfClrEnv \/off** удаляет значения переменных среды, используемые для профилирования.  
  
#### Завершение сеанса профилирования  
  
1.  Для отсоединения профилировщика от целевого приложения выполните одно из следующих действий.  
  
    -   Закройте целевое приложение.  
  
         – или –  
  
    -   Введите **VSPerfCmd \/detach**.  
  
2.  Завершите работу профилировщика.  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## См. также  
 [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)