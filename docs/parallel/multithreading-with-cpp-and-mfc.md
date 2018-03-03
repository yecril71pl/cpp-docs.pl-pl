---
title: "Wielowątkowość z C++ i MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14d076865cd83837e2de218ad0189c037c78cd83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-with-c-and-mfc"></a>Wielowątkowość z C++ i MFC
Biblioteka Microsoft Foundation Class (MFC) zapewnia obsługę dla aplikacji wielowątkowych. W tym temacie opisano procesów i wątków oraz podejście MFC dla wielowątkowości.  
  
 Proces jest wykonywane wystąpienie aplikacji. Dwukrotne kliknięcie ikony Notatnik, na przykład uruchomić proces, który uruchamia program Notatnik.  
  
 Wątek jest ścieżką wykonywania w ramach procesu. Po ponownym uruchomieniu program Notatnik, system operacyjny tworzy proces i rozpocznie się wykonywanie podstawowy wątku tego procesu. Gdy zakończenie tego wątku, co powoduje procesu. Ten podstawowy wątek został dostarczony do systemu operacyjnego przez kod startowy w postaci adresu funkcji. Zazwyczaj jest to adres z **głównego** lub `WinMain` funkcja, która jest dostarczana.  
  
 Jeśli chcesz, możesz utworzyć dodatkowe wątki w aplikacji. Można to zrobić, aby obsłużyć zadania tła lub konserwacji, jeśli nie chcesz, aby użytkownik oczekiwania na ich zakończenie. Wszystkie wątki w aplikacjach MFC są reprezentowane przez [cwinthread —](../mfc/reference/cwinthread-class.md) obiektów. W większości przypadków nie nawet masz można jawnie utworzyć te obiekty; Zamiast tego wywołaj funkcję pomocnika framework [afxbeginthread —](../mfc/reference/application-information-and-management.md#afxbeginthread), co powoduje `CWinThread` obiekt.  
  
 Dwa typy wątków odróżnia MFC: wątków interfejsu użytkownika i wątków roboczych. Wątki interfejsu użytkownika często są używane do obsługi danych wejściowych użytkownika i reagowanie na zdarzenia i komunikaty generowane przez użytkownika. Wątki robocze są często używane do ukończenia zadania, takie jak ponowne obliczanie, które nie wymagają danych wejściowych użytkownika. Interfejs API Win32 nie rozróżnianie wątków; po prostu musi ustalić adres początkowy wątku, więc można rozpocząć do wykonania wątku. MFC obsługuje wątków interfejsu użytkownika, podając specjalnie pompowania komunikatów zdarzeń w interfejsie użytkownika. `CWinApp`jest przykładem obiektu wątku interfejsu użytkownika, ponieważ dziedziczy `CWinThread` i obsługuje zdarzenia i komunikaty generowane przez użytkownika.  
  
 Szczególną uwagę należy do sytuacji, gdy więcej niż jeden wątek może wymagać dostępu do tego samego obiektu. [Wielowątkowość: Porady dotyczące programowania](../parallel/multithreading-programming-tips.md) opisuje metody, których można pobrać wokół problemów, które mogą wystąpić w następujących sytuacjach. [Wielowątkowość: Jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md) opisano, jak używać klas, które można zsynchronizować dostęp wiele wątków do pojedynczego obiektu.  
  
 Zapisywanie i debugowanie wielowątkowe programowania w języku wynika z założenia skomplikowane i trudnych przedsiębiorstwa, należy upewnić się, że obiekty nie są dostępne przez więcej niż jeden wątek na raz. Wielowątkowość tematy uczy podstaw wielowątkowe programowania tylko sposób Użyj MFC w programie wielowątkowe. Wielowątkowe przykłady MFC uwzględnione w programie Visual C++ ilustrują kilka wielowątkowe dodawania funkcjonalności i interfejsów API Win32, której nie obejmują MFC; jednak tylko mają być punkt początkowy.  
  
 Aby uzyskać więcej informacji na temat obsługi systemu operacyjnego wątków i procesów, zobacz [procesów i wątków](http://msdn.microsoft.com/library/windows/desktop/ms684841) w [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Aby uzyskać więcej informacji na temat obsługi wielowątkowości MFC zobacz następujące tematy:  
  
-   [Wielowątkowość: tworzenie wątków interfejsu użytkownika](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [Wielowątkowość: tworzenie wątków roboczych](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Wielowątkowość: jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [Wielowątkowość: przerywanie wątków](../parallel/multithreading-terminating-threads.md)  
  
-   [Wielowątkowość: porady dotyczące programowania](../parallel/multithreading-programming-tips.md)  
  
-   [Wielowątkowość: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)