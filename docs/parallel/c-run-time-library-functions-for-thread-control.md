---
title: Funkcje biblioteki wykonawczej języka C do sterowania wątkami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- _beginthread function
- _endthread function
- threading [C++], controlling threads
- multithreading [C++], controlling threads
- _beginthreadex function
- _endthreadex function
ms.assetid: 39d0529c-c392-4c6f-94f5-105d1e8054e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a505bae156edba6798812b807d7ab5c6ea9e396
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Funkcje biblioteki czasu wykonywania języka C do sterowania wątkami
Wszystkie programy Win32 ma co najmniej jeden wątek. Którymkolwiek wątku można utworzyć dodatkowe wątki. Wątek można szybko wykonać pracę i następnie zakończyć lub mogą pozostać aktywne przez cały okres istnienia program.  
  
 Biblioteki wykonawczej LIBCMT i MSVCRT C zapewniają następujące funkcje tworzenia wątku i zakończenie: [_beginthread —, _beginthreadex —](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_endthread —, _endthreadex —](../c-runtime-library/reference/endthread-endthreadex.md).  
  
 `_beginthread` i `_beginthreadex` funkcji tworzenia nowego wątku i zwraca identyfikator wątku, jeśli operacja się powiodła. Wątek kończy automatycznie wykonuje wykonywania, czy go jego zakończenia w wyniku wywołania `_endthread` lub `_endthreadex`.  
  
> [!NOTE]
>  Jeśli zamierzasz wywołać procedury czasu wykonywania języka C z poziomu programu skompilowane z Libcmt.lib, należy uruchomić z wątków z `_beginthread` lub `_beginthreadex` funkcji. Nie należy używać funkcji Win32 `ExitThread` i `CreateThread`. Przy użyciu `SuspendThread` może doprowadzić do zakleszczenia, gdy więcej niż jeden wątek jest zablokowany oczekiwania na ukończenie jego dostępu do struktury danych wykonawcze języka C wstrzymania wątku.  
  
##  <a name="_core_the__beginthread_function"></a> _Beginthread — i _beginthreadex — funkcje  
 `_beginthread` i `_beginthreadex` funkcji tworzenia nowego wątku. Wątek współużytkuje procesu segmenty kodu i danych z innych wątków w procesie, ale ma swoją własną wartości rejestru unikatowy, miejsca na stosie i adres bieżącej instrukcji. System umożliwia czas procesora CPU do każdy wątek, aby wszystkie wątki w procesie można wykonywać jednocześnie.  
  
 `_beginthread` i `_beginthreadex` są podobne do [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) te różnice, lecz jest funkcja w interfejsie API Win32:  
  
-   Inicjowania pewnych zmiennych biblioteki wykonawczej języka C. Jest to ważne, tylko w przypadku używania biblioteki wykonawczej języka C z wątków.  
  
-   `CreateThread` pomaga zapewnić kontrolę nad atrybutów zabezpieczeń. Ta funkcja służy do uruchamiania wątku w stanie zawieszone.  
  
 `_beginthread` i `_beginthreadex` zwraca uchwyt do nowego wątku w przypadku powodzenia lub kod błędu, jeśli wystąpił błąd.  
  
##  <a name="_core_the__endthread_function"></a> _Endthread — i _endthreadex — funkcje  
 [_Endthread —](../c-runtime-library/reference/endthread-endthreadex.md) funkcja kończy utworzone przez wątek `_beginthread` (i podobnie `_endthreadex` kończy utworzone przez wątek `_beginthreadex`). Wątki przerwanie automatycznie po zakończeniu. `_endthread` i `_endthreadex` są przydatne w przypadku warunkowego zakończenia od w wątku. Na przykład wątku dedykowane do obsługi komunikacji przetwarzania, można Zamknij, jeśli nie może uzyskać kontrolę nad port komunikacyjny.  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)