---
title: 'Wielowątkowość: porady dotyczące programowania MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 79e7d440b478c759c5d4fd683d6af3423e7e8661
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140444"
---
# <a name="multithreading-mfc-programming-tips"></a>Wielowątkowość: porady dotyczące programowania MFC

Aplikacje wielowątkowe wymagają bardziej rygorystycznych zastosowań niż aplikacje jednowątkowe, aby zapewnić, że operacje są wykonywane w zamierzonej kolejności, a wszystkie dane, do których dostęp jest wykonywany przez wiele wątków, nie są uszkodzone. W tym temacie objaśniono techniki pozwalające uniknąć potencjalnych problemów związanych z programowaniem aplikacji wielowątkowych za pomocą biblioteki Microsoft Foundation Class (MFC).

- [Uzyskiwanie dostępu do obiektów z wielu wątków](#_core_accessing_objects_from_multiple_threads)

- [Uzyskiwanie dostępu do obiektów MFC z wątków nienależących do MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Mapy uchwytów systemu Windows](#_core_windows_handle_maps)

- [Komunikacja między wątkami](#_core_communicating_between_threads)

## <a name="_core_accessing_objects_from_multiple_threads"></a>Uzyskiwanie dostępu do obiektów z wielu wątków

Obiekty MFC nie są bezpieczne wątkowo. Dwa oddzielne wątki nie mogą manipulować tym samym obiektem, chyba że używasz klas synchronizacji MFC i/lub odpowiednich obiektów synchronizacji Win32, takich jak sekcje krytyczne. Aby uzyskać więcej informacji na temat sekcji krytycznych i innych powiązanych obiektów, zobacz [Synchronizacja](/windows/win32/Sync/synchronization) w Windows SDK.

Biblioteka klas wykorzystuje wewnętrznie krytyczne sekcje w celu ochrony globalnych struktur danych, takich jak te używane przez alokację pamięci debugowania.

## <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>Uzyskiwanie dostępu do obiektów MFC z wątków nienależących do MFC

Jeśli masz aplikację wielowątkową, która tworzy wątek w inny sposób niż przy użyciu obiektu [CWinThread](../mfc/reference/cwinthread-class.md) , nie możesz uzyskać dostępu do innych obiektów MFC z tego wątku. Innymi słowy, jeśli chcesz uzyskać dostęp do dowolnego obiektu MFC z wątku pomocniczego, musisz utworzyć ten wątek przy użyciu jednej z metod opisanych w wielowątkowości [: Tworzenie wątków interfejsu użytkownika](multithreading-creating-user-interface-threads.md) lub [wielowątkowość: Tworzenie wątków roboczych](multithreading-creating-worker-threads.md). Te metody są jedynymi, które umożliwiają bibliotece klas zainicjowanie zmiennych wewnętrznych wymaganych do obsługi aplikacji wielowątkowych.

## <a name="_core_windows_handle_maps"></a>Mapy uchwytów systemu Windows

Jako ogólna reguła wątek może uzyskać dostęp tylko do utworzonych obiektów MFC. Wynika to z faktu, że tymczasowe i stałe mapy uchwytów systemu Windows są przechowywane w lokalnym magazynie wątków, aby zapewnić ochronę przed równoczesnym dostępem z wielu wątków. Na przykład wątek roboczy nie może wykonać obliczenia, a następnie wywołać funkcję członkowską `UpdateAllViews` dokumentu, aby zostały zmodyfikowane okna zawierające widoki dla nowych danych. Nie ma to żadnego wpływu, ponieważ mapa z `CWnd` obiektów do HWND jest lokalna dla wątku głównego. Oznacza to, że jeden wątek może mieć mapowanie z dojścia systemu Windows do C++ obiektu, ale inny wątek może mapować ten sam uchwyt do innego C++ obiektu. Zmiany wprowadzone w jednym wątku nie zostaną odzwierciedlone w drugim.

Istnieje kilka sposobów na obejście tego problemu. Pierwszym z nich jest przekazanie poszczególnych dojścia (takich jak HWND), C++ a nie obiektów do wątku roboczego. Wątek roboczy dodaje te obiekty do tymczasowej mapy, wywołując odpowiednią funkcję składową `FromHandle`. Można również dodać obiekt do trwałej mapy wątku, wywołując `Attach`, ale należy to zrobić tylko wtedy, gdy masz gwarancję, że obiekt będzie istniał dłużej niż wątek.

Inna metoda polega na tworzeniu nowych komunikatów zdefiniowanych przez użytkownika, które odpowiadają różnym czynnościom, które będą wykonywane przez wątki robocze, i ogłaszają te komunikaty w oknie głównym aplikacji przy użyciu `::PostMessage`. Ta metoda komunikacji jest podobna do dwóch różnych aplikacji, z wyjątkiem tego, że oba wątki są wykonywane w tej samej przestrzeni adresowej.

Aby uzyskać więcej informacji na temat map uchwytów, zobacz [Uwaga techniczna 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Aby uzyskać więcej informacji na temat lokalnego magazynu wątków, zobacz temat [lokalny magazyn](/windows/win32/ProcThread/thread-local-storage) wątków i [Używanie lokalnego magazynu wątków](/windows/win32/ProcThread/using-thread-local-storage) w Windows SDK.

## <a name="_core_communicating_between_threads"></a>Komunikacja między wątkami

MFC udostępnia wiele klas, które umożliwiają wątkom synchronizowanie dostępu do obiektów w celu zapewnienia bezpieczeństwa wątków. Użycie tych klas zostało opisane w temacie [wielowątkowość: jak używać klas synchronizacji](multithreading-how-to-use-the-synchronization-classes.md) i [wielowątkowości: Kiedy używać klas synchronizacji](multithreading-when-to-use-the-synchronization-classes.md). Aby uzyskać więcej informacji na temat tych obiektów, zobacz [Synchronizacja](/windows/win32/Sync/synchronization) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Wielowątkowość z C++ i MFC](multithreading-with-cpp-and-mfc.md)
