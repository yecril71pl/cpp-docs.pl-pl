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
ms.openlocfilehash: 2ad830117323aef807fcebc1ef61b4dfb1900bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591314"
---
# <a name="multithreading-programming-tips"></a>Wielowątkowość: porady dotyczące programowania
Aplikacje wielowątkowe wymagają obsługi bardziej restrykcyjny niż aplikacje jednowątkowe podczas uzyskiwania dostępu do danych. Ponieważ istnieje wiele, niezależne ścieżki wykonywania w jednocześnie używać w aplikacjach wielowątkowych algorytmów, danych lub oba muszą znać te dane można używane przez więcej niż jeden wątek jednocześnie. W tym temacie opisano techniki w celu uniknięcia potencjalnych problemów podczas programowania wielowątkowe aplikacje za pomocą biblioteki Microsoft Foundation Class (MFC).  
  
- [Uzyskiwanie dostępu do obiektów z wielu wątków](#_core_accessing_objects_from_multiple_threads)  
  
- [Uzyskiwanie dostępu do obiektów MFC z innego typu niż MFC wątków](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
- [Windows uchwyt mapy](#_core_windows_handle_maps)  
  
- [Komunikacja między wątkami](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> Uzyskiwanie dostępu do obiektów z wielu wątków  
 
Rozmiar i wydajność ze względu na obiektami MFC nie są wątkowo na poziomie obiektu, tylko na poziomie klasy. Oznacza to, że może mieć dwóch oddzielnych wątkach, manipulowanie dwa różne `CString` obiektów, ale nie dwa wątki, manipulowanie takie same `CString` obiektu. Jeśli bezwzględnie musi mieć wiele wątków, manipulowanie tego samego obiektu, należy chronić takiego dostępu za pomocą odpowiednich mechanizmów synchronizacji Win32, takie jak sekcje krytyczne. Aby uzyskać więcej informacji na temat sekcje krytyczne i inne powiązane obiekty, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w zestawie Windows SDK.  
  
Biblioteka klas wymaga sekcje krytyczne wewnętrznie, aby chronić struktur danych globalnych, takich jak używane przez alokacji pamięci debugowania.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Uzyskiwanie dostępu do obiektów MFC z innego typu niż MFC wątków  
 
W przypadku aplikacji wielowątkowych, który tworzy wątek w sposób niż przy użyciu [CWinThread](../mfc/reference/cwinthread-class.md) obiektu, nie masz dostępu do innych obiektów MFC z tego wątku. Innymi słowy, jeśli chcesz uzyskać dostęp do dowolnego obiektu MFC z wątek pomocniczy, należy utworzyć wątek przy użyciu jednej z metod opisanych w [wielowątkowość: Tworzenie wątków interfejsu użytkownika](../parallel/multithreading-creating-user-interface-threads.md) lub [wielowątkowość: Tworzenie wątków roboczych](../parallel/multithreading-creating-worker-threads.md). Te metody są jedynymi osobami, które umożliwiają biblioteki klas zainicjować zmienne wewnętrznej, która jest niezbędne do obsługi aplikacji wielowątkowych.  
  
##  <a name="_core_windows_handle_maps"></a> Windows uchwyt mapy  
 
Zgodnie z ogólną zasadą wątku, mogą uzyskiwać dostęp tylko obiekty MFC, utworzonych przez siebie. Jest to spowodowane tymczasowe i stałe mapy uchwyt Windows są przechowywane w pamięci lokalnej wątku, aby zapewnić ochronę przed równoczesny dostęp z wielu wątków. Na przykład wątku roboczego nie może wykonać obliczenia, a następnie wywołać dokumentu `UpdateAllViews` funkcja elementu członkowskiego przez system Windows, które zawierają widoki na nowe dane zmodyfikowany. Nie ma to wpływu na wszystkich, ponieważ do mapy `CWnd` obiekty do parametrów hWnd jest lokalna wątku głównego. Oznacza to, że jeden wątek może być mapowanie Windows dojścia do obiektu języka C++, ale inny wątek mogą być mapowane na ten sam dojścia do innego obiektu języka C++. Zmiany wprowadzone w jednym wątku nie byłyby widoczne w innym.  
  
Istnieje kilka sposobów tego problemu. Pierwszy jest przekazanie poszczególnych uchwytów (na przykład HWND) zamiast obiektów C++ do wątku roboczego. Wątek roboczy dodaje te obiekty do jego tymczasowe mapy przez wywołanie odpowiedniej `FromHandle` funkcja elementu członkowskiego. Obiekt można dodać do mapy stałe wątku, wywołując `Attach`, ale należy to zrobić tylko wtedy, gdy masz gwarancję, że obiekt będzie istnieć dłuższy niż wątek.  
  
Inną metodą jest utworzenie nowych wiadomości zdefiniowanych przez użytkownika, odpowiadający różne zadania, wątki procesów roboczych spowoduje wykonywania i publikować te wiadomości do okna głównego aplikacji przy użyciu `::PostMessage`. Ta metoda komunikacji jest podobne do dwóch różnych aplikacji konwersację z tą różnicą, że zarówno wątki są wykonywane w tej samej przestrzeni adresowej.  
  
Aby uzyskać więcej informacji na temat map uchwyt zobacz [Technical Preview 3 Uwaga](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Aby uzyskać więcej informacji na temat pamięci lokalnej wątku, zobacz [lokalny magazyn wątków](http://msdn.microsoft.com/library/windows/desktop/ms686749) i [przy użyciu pamięci lokalnej wątku](http://msdn.microsoft.com/library/windows/desktop/ms686991) w zestawie Windows SDK.  
  
##  <a name="_core_communicating_between_threads"></a> Komunikacja między wątkami  
 
Biblioteka MFC zawiera szereg klas, które umożliwiają wątków do synchronizowania dostępu do obiektów, aby zachować bezpieczeństwo wątkowe. Sposób użycia tych klas jest opisana w [wielowątkowość: jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md) i [wielowątkowość: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Aby uzyskać więcej informacji na temat tych obiektów, zobacz [synchronizacji](http://msdn.microsoft.com/library/windows/desktop/ms686353) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  

[Wielowątkowość z C++ i MFC](../parallel/multithreading-with-cpp-and-mfc.md)