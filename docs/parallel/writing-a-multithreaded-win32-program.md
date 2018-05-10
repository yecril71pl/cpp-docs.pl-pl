---
title: Pisanie wielowątkowego programu Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d88add7830316ae192a728f9c9ff10320657eaf
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="writing-a-multithreaded-win32-program"></a>Pisanie wielowątkowego programu Win32
Podczas pisania programu przy użyciu wielu wątków musi być dostosowana ich zachowania i [wykorzystania zasobów programu](#_core_sharing_common_resources_between_threads). Należy również upewnić się, że każdy wątek otrzyma [własną stosu](#_core_thread_stacks).  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> Udostępnianie wspólnych zasobów między wątkami  
  
> [!NOTE]
>  Omówienie podobne z punktu widzenia MFC, zobacz [Multithreading: Programowanie porady](../parallel/multithreading-programming-tips.md) i [Multithreading: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  
  
 Każdy wątek ma własną stosu i rejestruje własną kopię Procesora. Inne zasoby, takie jak pliki, dane statyczne i pamięci sterty są współużytkowane przez wszystkie wątki w procesie. Wątki używające tych wspólnych zasobów musi być synchronizowany. Win32 udostępnia kilka sposobów, aby zsynchronizować zasobów, w tym semaforów, sekcje krytyczne i zdarzenia oraz muteksy.  
  
 Wiele wątków uzyskują dostęp do danych statycznych, program muszą przewidywać konflikty zasobów. Należy wziąć pod uwagę program, gdy jeden wątek aktualizacji zawierający struktury danych statycznych *x*,*y* współrzędnych dla elementów do wyświetlenia przez inny wątek. Jeśli wątek aktualizacji zmienia *x* koordynacji i jest wywłaszczone, zanim można go zmienić *y* współrzędnych, wątku wyświetlania może zostać zaplanowane przed *y* Współrzędna jest zaktualizowane. Element będzie wyświetlany w niewłaściwej lokalizacji. Aby uniknąć tego problemu, należy za pomocą semaforów do kontrolowania dostępu do struktury.  
  
 Obiektu mutex (skrót od *mut*rejestrowania dostępu użytkowników *ex*clusion) to sposób komunikacji między wątki lub procesy, które są wykonywane asynchronicznie od siebie. Ta komunikacja jest zwykle używany do koordynowania innych działań wiele wątków i procesów, zwykle kontrolowanie dostępu do zasobów udostępnionych przez blokowanie i odblokowywanie zasobu. Aby rozwiązać ten problem *x*,*y* współrzędnych aktualizacji problem, wątek aktualizacji ustawia mutex, co oznacza, że struktura danych przed wykonaniem aktualizacji. Czy go wyczyścić obiektu mutex, po obu współrzędne zostało przetworzone. Wątek wyświetlania należy poczekać mutex być wyczyść przed aktualizacją wyświetlania. Ten proces trwa oczekiwanie na obiektu mutex jest często nazywane blokowania na obiektu mutex, ponieważ proces jest zablokowany i nie może kontynuować dopóki czyści obiektu mutex.  
  
 Program Bounce.c wyświetlany w [przykładowy Program C wielowątkowej](../parallel/sample-multithread-c-program.md) używa obiektu mutex o nazwie `ScreenMutex` aby koordynować aktualizacje ekranu. Zawsze jeden z wątków wyświetlana jest gotowy do zapisu na ekranie wywołuje **WaitForSingleObject** z dojściem do `ScreenMutex` i stałej **NIESKOŃCZONE** z informacją, że  **WaitForSingleObject** zablokować wywołania obiektu mutex i nie upłynął limit czasu. Jeśli `ScreenMutex` jest pusta, funkcja oczekiwania ustawia obiektu mutex, więc innych wątków nie może zakłócać wyświetlania i kontynuuje wykonywanie wątku. W przeciwnym razie wątek blokuje dopóki czyści obiektu mutex. Po zakończeniu aktualizacji ekranu, zwalnia obiektu mutex przez wywołanie metody **ReleaseMutex**.  
  
 Na ekranie i dane statyczne są tylko dwa zasoby wymagające staranne zarządzanie. Na przykład program może mieć wiele wątków podczas uzyskiwania dostępu do tego samego pliku. Ponieważ inny wątek może przeniesiono wskaźnika pliku, każdy wątek należy zresetować wskaźnika pliku przed odczytu lub zapisu. Ponadto każdy wątek należy się upewnić, że nie jest wywłaszczone między czas jego umieszcza kursor i uzyskuje dostęp do pliku. Wątki te semafora powinna być używana do koordynowania dostępu do pliku przez zestawianie każdego dostęp do plików przy użyciu **WaitForSingleObject** i **ReleaseMutex** wywołania. Poniższy przykładowy kod przedstawia tej techniki:  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> Stosy wątków  
 Wszystkie miejsca na stosie domyślnej aplikacji jest przydzielony do pierwszego wątku do wykonania, znany jako wątku 1. W związku z tym należy określić ilość pamięci do przydzielenia oddzielne stosu dla każdego wątku dodatkowe program wymaga. System operacyjny przydziela miejsce dodatkowe stosu wątku, jeśli to konieczne, ale należy określić wartość domyślną.  
  
 Pierwszy argument `_beginthread` wywołanie jest wskaźnik do **BounceProc** funkcji, która wykonuje wątki. Drugi argument określa domyślny rozmiar stosu wątku. Ostatni argument jest identyfikator, który jest przekazywany do **BounceProc**. **BounceProc** używa numeru Identyfikacyjnego jako zalążek generatora liczb losowych oraz wybierz atrybut kolor wątku i wyświetlić znak.  
  
 Wątki wykonywać wywołania do biblioteki wykonawczej języka C lub interfejs API Win32 muszą zezwalać na wystarczającą ilość miejsca na biblioteki i funkcje interfejsu API, które wywołują stosu. C `printf` funkcja wymaga więcej niż 500 bajtów miejsca na stosie, a powinien mieć 2 K ilości wolnego miejsca na stosie podczas wywoływania procedury interfejsu API systemu Win32.  
  
 Ponieważ każdy wątek ma własną stosu, można uniknąć potencjalnych konfliktów nad elementami danych przy użyciu małego dane statyczne, jak to możliwe. Projekt programu używania zmiennych stosu automatyczne dla wszystkich danych, które mogą być prywatne do wątku. Zmienne globalne tylko w programie Bounce.c są muteksy lub zmiennych, które nigdy nie ulegną zmianie po ich inicjowaniu.  
  
 Win32 są także magazynu Thread-Local (TLS) do przechowywania danych dla każdego wątku. Aby uzyskać więcej informacji, zobacz [wątku lokalnego magazynu (TLS)](../parallel/thread-local-storage-tls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z językiem C i podsystemem Win32](../parallel/multithreading-with-c-and-win32.md)