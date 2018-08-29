---
title: Biblioteki wykonawczej C funkcje do sterowania wątkami | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2eaa1a0589cb001658b18144e06956eebd302287
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131857"
---
# <a name="c-run-time-library-functions-for-thread-control"></a>Funkcje biblioteki czasu wykonywania języka C do sterowania wątkami
Wszystkie programy Win32 ma co najmniej jeden wątek. Jednym z wątków można utworzyć dodatkowe wątki. Wątek można szybko wykonać pracę, a następnie Zakończ działanie lub mogą pozostać aktywne przez cały okres istnienia programu.  
  
Biblioteki wykonawczej LIBCMT i MSVCRT C zapewniają następujące funkcje do tworzenia wątku i kończenie działania: [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_endthread, _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).  
  
`_beginthread` i `_beginthreadex` funkcji, Utwórz nowy wątek i zwraca identyfikator wątku, jeśli operacja się powiedzie. Wątek się kończy automatycznie zakończenia wykonywania, czy, może zostać przerwany się wywołaniem `_endthread` lub `_endthreadex`.  
  
> [!NOTE]
> Jeśli zamierzasz wywołanie procedury czasu wykonywania języka C z poziomu programu skompilowanych przy użyciu biblioteki Libcmt.lib, należy uruchomić wątki z `_beginthread` lub `_beginthreadex` funkcji. Nie należy używać funkcji Win32 `ExitThread` i `CreateThread`. Za pomocą `SuspendThread` może prowadzić do zakleszczenia, gdy więcej niż jeden wątek jest zablokowany, trwa oczekiwanie na wstrzymania wątku zakończyć jego dostęp do struktury danych środowiska wykonawczego języka C.  
  
##  <a name="_core_the__beginthread_function"></a> Funkcje _beginthread i _beginthreadex  
 
`_beginthread` i `_beginthreadex` functions w celu utworzenia nowego wątku. Wątek udostępni segmenty kodu i danych procesu inne wątki w procesie, ale ma swoje własne wartości rejestru unikatowych obszar stosu i bieżący adres instrukcji. System daje czas procesora CPU do każdego wątku, tak, aby wszystkie wątki w procesie można wykonywać jednocześnie.  
  
`_beginthread` i `_beginthreadex` są podobne do [CreateThread](http://msdn.microsoft.com/library/windows/desktop/ms682453) funkcji API Win32, ale ma te różnice:  
  
- Inicjowania pewne zmienne biblioteki wykonawczej C. Jest to ważne, tylko wtedy, gdy używasz biblioteki wykonawczej języka C w wątki.  
  
- `CreateThread` pomaga w zapewnieniu kontroli nad atrybutów zabezpieczeń. Można użyć tej funkcji, można uruchomić wątku w stanie wstrzymania.  
  
 `_beginthread` i `_beginthreadex` zwraca uchwyt do nowego wątku, jeśli kończy się pomyślnie lub kod błędu, jeśli wystąpił błąd.  
  
##  <a name="_core_the__endthread_function"></a> _Endthread i _endthreadex — funkcje  
 
[_Endthread](../c-runtime-library/reference/endthread-endthreadex.md) funkcja kończy się wątek, który został utworzony przez `_beginthread` (USA i podobnie `_endthreadex` kończy się wątek, który został utworzony przez `_beginthreadex`). Wątki obowiązywać automatycznie po ich zakończeniu. `_endthread` i `_endthreadex` są przydatne w przypadku warunkowego zakończenia z w ramach wątku. Na przykład wątku dedykowanego dla usługi komunikacji przetwarzania może Zamknij, jeśli nie może uzyskać kontrolę portu komunikacyjnego.  
  
## <a name="see-also"></a>Zobacz też  
 
[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)