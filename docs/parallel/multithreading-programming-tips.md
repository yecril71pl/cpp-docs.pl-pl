---
title: 'Wielowątkowość: Porady dotyczące programowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9c4241b9257244de840db1f57c5e7abcb32f206
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689990"
---
# <a name="multithreading-programming-tips"></a>Wielowątkowość: porady dotyczące programowania
Aplikacje wielowątkowe wymagają uwagę na bardziej restrykcyjne niż jednowątkowe aplikacji podczas uzyskiwania dostępu do danych. Ponieważ istnieje wiele, niezależne ścieżki wykonywania w jednocześnie używać w aplikacjach wielowątkowych algorytmów, danych lub oba muszą znać te dane mogą zostać użyte przez więcej niż jeden wątek na raz. W tym temacie wyjaśniono technik w celu uniknięcia potencjalnych problemów programowania aplikacji wielowątkowych z biblioteki Microsoft Foundation Class (MFC).  
  
-   [Uzyskiwanie dostępu do obiektów z wielu wątków](#_core_accessing_objects_from_multiple_threads)  
  
-   [Uzyskiwanie dostępu do obiektów MFC z wątków innego typu niż MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Mapowania obsługi systemu Windows](#_core_windows_handle_maps)  
  
-   [Komunikacja między wątkami](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> Uzyskiwanie dostępu do obiektów z wielu wątków  
 Ze względów rozmiaru i wydajności MFC obiekty nie są wątkowo na poziomie obiektu tylko na poziomie klasy. Oznacza to, że może mieć dwóch oddzielnych wątkach manipulowanie dwóch różnych `CString` obiektów, ale nie dwoma wątkami manipulowanie takie same `CString` obiektu. Jeśli absolutnie musi mieć wiele wątków manipulowanie tego samego obiektu, chronić takiego dostępu za pomocą odpowiednich mechanizmów synchronizacji Win32, takich jak sekcje krytyczne. Aby uzyskać więcej informacji na temat sekcje krytyczne i inne powiązane obiekty, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Biblioteka klas używa sekcje krytyczne wewnętrznie do ochrony struktur danych globalnych, takich jak zasoby używane przez debugowania alokacji pamięci.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Uzyskiwanie dostępu do obiektów MFC z wątków innego typu niż MFC  
 Jeśli masz wielowątkowe aplikacji, która tworzy wątku w sposób innych niż z użyciem [cwinthread —](../mfc/reference/cwinthread-class.md) obiektu, nie masz dostępu do innych obiektów MFC z tego wątku. Innymi słowy, jeśli chcesz uzyskać dostęp każdy obiekt MFC wprowadzanych przez wątek pomocniczy, należy utworzyć tego wątku z jednej z metod opisanych w [Multithreading: Tworzenie wątków interfejsu użytkownika](../parallel/multithreading-creating-user-interface-threads.md) lub [Multithreading: Tworzenie wątków roboczych](../parallel/multithreading-creating-worker-threads.md). Te metody są jedynymi osobami, które umożliwiają biblioteki klas zainicjować wewnętrzne zmienne niezbędne do obsługi aplikacji wielowątkowych.  
  
##  <a name="_core_windows_handle_maps"></a> Mapowania obsługi systemu Windows  
 Ogólną zasadą wątku mogą uzyskiwać dostęp tylko obiekty MFC utworzonych przez siebie. Jest to spowodowane tymczasowe i stałe mapy dojście systemu Windows są przechowywane w lokalny magazyn wątków, aby zapewnić ochronę przed jednoczesny dostęp wiele wątków. Na przykład wątku roboczego nie może wykonać obliczenia, a następnie wywołać dokumentu `UpdateAllViews` funkcji członkowskiej mają okna, które zawierają widoki na nowe dane zmodyfikowane. To ustawienie nie działa, ponieważ mapowanie z `CWnd` obiekty do `HWND`s jest lokalny dla podstawowy wątku. Oznacza to, że jeden wątek może być mapowanie uchwytów okien na obiekt C++, ale inny wątek mogą być mapowane tego samego dojścia do innego obiektu języka C++. Zmiany wprowadzone w jednym wątku nie będzie zostaną uwzględnione w innym.  
  
 Istnieje kilka sposobów tego problemu. Pierwszy jest przekazanie poszczególnych dojść (takie jak `HWND`) zamiast obiektów C++ do wątku roboczego. Wątek roboczy następnie dodaje te obiekty do jego tymczasowego mapy wywołując odpowiednie `FromHandle` funkcję elementu członkowskiego. Można także dodać obiektu do mapowania stałego wątku przez wywołanie metody **Attach**, ale należy to zrobić tylko wtedy, gdy ma gwarancji, że obiekt będzie istnieć dłuższy niż wątek.  
  
 Inną metodą jest utworzenie nowych wiadomości zdefiniowane przez użytkownika odpowiadającego do różnych zadań z wątków roboczych spowoduje wykonywania i publikowania tych wiadomości do okna głównego aplikacji przy użyciu **:: funkcji PostMessage**. Ta metoda komunikacji jest podobny do dwóch różnych aplikacji konwersację z tym, że zarówno wątki są wykonywane w tej samej przestrzeni adresowej.  
  
 Aby uzyskać więcej informacji na temat map dojścia zobacz [Technical Uwaga 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Aby uzyskać więcej informacji na temat lokalny magazyn wątków, zobacz [lokalny magazyn wątków](http://msdn.microsoft.com/library/windows/desktop/ms686749) i [przy użyciu magazynu lokalnego wątku](http://msdn.microsoft.com/library/windows/desktop/ms686991) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
##  <a name="_core_communicating_between_threads"></a> Komunikacja między wątkami  
 MFC zawiera szereg klas, które wątki synchronizujący dostęp do obiektów, aby zachować bezpieczeństwo wątków. Użycie tych klas jest opisany w [Multithreading: jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md) i [Multithreading: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Aby uzyskać więcej informacji na temat tych obiektów, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)