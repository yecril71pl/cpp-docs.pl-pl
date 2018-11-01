---
title: Pisanie wielowątkowego programu Win32
ms.date: 11/04/2016
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
ms.openlocfilehash: c7d9790cfee39fbddd9ab545d48fa375d56f3a05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561333"
---
# <a name="writing-a-multithreaded-win32-program"></a>Pisanie wielowątkowego programu Win32

Podczas pisania programu przy użyciu wielu wątków, musisz skoordynować ich zachowania i [wykorzystania zasobów programu](#_core_sharing_common_resources_between_threads). Należy również upewnić się, że każdy wątek otrzyma [własnego stosu](#_core_thread_stacks).

##  <a name="_core_sharing_common_resources_between_threads"></a> Udostępnianie wspólnych zasobów między wątkami

> [!NOTE]
>  Omówienie podobne z punktu widzenia MFC, zobacz [wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md) i [wielowątkowość: kiedy używać klas synchronizacji](multithreading-when-to-use-the-synchronization-classes.md).

Każdy wątek ma swój własny stosu i rejestruje własną kopię procesora CPU. Inne zasoby, takie jak pliki, dane statyczne i pamięć sterty są współużytkowane przez wszystkie wątki w procesie. Wątki używające tych wspólnych zasobów musi być synchronizowane. Win32 oferuje kilka sposobów, aby zsynchronizować zasoby, w tym semaforów, sekcje krytyczne, zdarzeń i muteksy.

Gdy wiele wątków uzyskują dostęp do danych statycznych, program musisz podać zasób możliwych konfliktów. Należy wziąć pod uwagę program, gdy jeden wątek aktualizacji zawierającą strukturę danych statycznych *x*,*y* współrzędnych dla elementów, które mają być wyświetlane przez inny wątek. Jeśli wątek aktualizacji zmienia *x* koordynacji i jest przerywane, zanim będzie można zmienić *y* współrzędnych, Wyświetl wątek może być zaplanowane przed *y* Współrzędna jest zaktualizowane. Element będzie wyświetlany w niewłaściwej lokalizacji. Aby uniknąć tego problemu, należy za pomocą semaforów do kontrolowania dostępu do struktury.

Mutex (skrót od *mut*usługi rejestrowania dostępu użytkowników *ex*clusion) jest metodą komunikacji między wątkach lub procesach, które są wykonywane asynchronicznie od siebie. Ta komunikacja jest zazwyczaj używana do koordynowania działania wielu wątkach lub procesach zazwyczaj kontrolowanie dostępu do zasobu udostępnionego przez blokowanie i odblokowywanie zasobu. Aby rozwiązać ten problem *x*,*y* współrzędnych aktualizacji problem, wątek aktualizacji ustawia mutex, co oznacza, że struktury danych w użyciu przed przystąpieniem do wykonywania aktualizacji. Czyścił je element mutex po przetworzył zarówno współrzędnych. Wątek wyświetlania musi czekać na element mutex za wyczyść przed aktualizacją wyświetlania. Ten proces trwa oczekiwanie na mutex jest często nazywane blokowania na mutex, ponieważ proces jest zablokowana i nie może kontynuować pracy, dopóki nie usuwa element mutex.

Program Bounce.c wyświetlany w [przykładowy Program C wielowątkowości](sample-multithread-c-program.md) używa elementu mutex o nazwie `ScreenMutex` do koordynowania aktualizacji ekranu. Każdorazowo, jeden z wątków wyświetlana jest gotowy do zapisu do ekranu, wywoływanych przez nią `WaitForSingleObject` z dojściem do `ScreenMutex` i stałe NIESKOŃCZONE, aby wskazać, że `WaitForSingleObject` wywołania powinna blokować mutex i nie przekraczają limit czasu. Jeśli `ScreenMutex` jest pusta, funkcja oczekiwania ustawia element mutex, dzięki czemu inne wątki nie może kolidować z wyświetlaniem i kontynuuje wykonywanie wątku. W przeciwnym razie wątek blokuje, dopóki czyści element mutex. Po zakończeniu aktualizacji ekranu, zwalnia element mutex, wywołując `ReleaseMutex`.

Na ekranie, a dane statyczne są tylko dwa zasoby wymagające staranne zarządzanie. Na przykład program może mieć wiele wątków, uzyskiwanie dostępu do tego samego pliku. Ponieważ inny wątek może być przeniesione wskaźnikiem pliku, każdy wątek należy zresetować wskaźnika pliku przed odczytem lub zapisem. Ponadto każdy wątek, musisz upewnić się, że nie jest przerywane między czas jego umieszcza wskaźnik i uzyskuje dostęp do pliku. Te wątki należy używać semafor do koordynacji dostępu do pliku zestawianie każdy dostęp do plików za pomocą `WaitForSingleObject` i `ReleaseMutex` wywołania. W poniższym przykładzie kodu pokazano tej techniki:

```
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

##  <a name="_core_thread_stacks"></a> Stosy wątków

Cały obszar stosu domyślnego aplikacji jest przydzielany do pierwszym wątkiem wykonywania, który jest znany jako wątek 1. W rezultacie należy określić, ilość pamięci do przydzielenia dla oddzielnych stosu dla każdego wątku dodatkowe program wymaga. System operacyjny przydziela dodatkowe stosu dla wątku, w razie potrzeby, ale musi określać wartość domyślną.

Pierwszy argument `_beginthread` wywołanie jest wskaźnikiem do `BounceProc` funkcji, która wykonuje wątków. Drugi argument określa domyślny rozmiar stosu dla wątku. Ostatni argument jest liczbą identyfikator, który jest przekazywany do `BounceProc`. `BounceProc` używa numer identyfikacyjny umieszczenia generator liczb losowych, a także wybrać atrybut kolorów dla wątku i wyświetlić znak.

Wątki, które wykonywać wywołania do biblioteki wykonawczej języka C lub Win32 API muszą zezwalać na wystarczająco dużo miejsca na stosie dla biblioteki i funkcje interfejsu API, które wywołują. C `printf` funkcja wymaga więcej niż 500 bajtów miejsca na stosie i powinien mieć 2 K dostępnego miejsca na stosie, podczas wywoływania procedury interfejsu API systemu Win32.

Ponieważ każdy wątek ma swój własny stosu, możesz uniknąć potencjalnych konfliktów za pośrednictwem elementów danych, używając jako małą ilością danych statycznych, jak to możliwe. Zaprojektuj program korzystanie ze zmiennych stosu automatyczne dla wszystkich danych, które mogą być prywatne do wątku. Zmienne tylko globalne w programie Bounce.c są muteksy lub zmienne, które nigdy nie ulegną zmianie po ich są inicjowane.

Win32 udostępnia również magazynu Thread-Local (TLS) do przechowywania danych na wątek. Aby uzyskać więcej informacji, zobacz [wątku lokalnego magazynu (TLS)](thread-local-storage-tls.md).

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z językiem C i podsystemem Win32](multithreading-with-c-and-win32.md)