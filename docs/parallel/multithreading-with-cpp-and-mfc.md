---
title: Wielowątkowość z C++ i MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fd5a60908d52bf0ccdf0c0e76e076cb244e3e31
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596100"
---
# <a name="multithreading-with-c-and-mfc"></a>Wielowątkowość z C++ i MFC
Biblioteka Microsoft Foundation Class (MFC) zapewnia obsługę aplikacji wielowątkowych. W tym temacie opisano procesy i ciągi oraz podejście MFC do wielowątkowości.  
  
Proces jest wykonuje wystąpienie aplikacji. Na przykład gdy klikniesz dwukrotnie ikonę Notatnika, możesz uruchomić proces, który włącza Notatnik.  
  
Wątek jest ścieżką wykonywania w ramach procesu. Kiedy uruchamiasz Notepad, system operacyjny tworzy proces i rozpoczyna wykonywanie podstawowego wątku tego procesu. Gdy ten wątek kończy, kończy również proces. Ten główny wątek jest dostarczony do systemu operacyjnego przez kod startowy w formie adresu funkcji. Zazwyczaj jest adres `main` lub `WinMain` funkcja, która jest dostarczana.  
  
Jeśli chcesz, możesz utworzyć dodatkowe wątki nie w aplikacji. Można to zrobić, aby obsługiwać zadania tło lub konserwacji, jeśli nie chcesz, aby użytkownik czekał aż do ukończenia. Wszystkie wątki w aplikacjach MFC są reprezentowane przez [CWinThread](../mfc/reference/cwinthread-class.md) obiektów. W większości sytuacji nawet trzeba jawnie tworzyć tych obiektów; Zamiast tego, wywołaj funkcję pomocnika szablonu [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), co powoduje utworzenie `CWinThread` obiekt dla Ciebie.  
  
MFC wyróżnia dwa rodzaje wątków: wątki interfejsu użytkownika oraz wątki robocze. Wątki interfejsu użytkownika są często używane do obsługi danych wejściowych użytkownika i reagowanie na zdarzenia i komunikaty generowane przez użytkownika. Wątki robocze są często używane do ukończenia zadania, takie jak ponowne obliczenie, które nie wymagają wprowadzenia danych przez użytkownika. Win32 API nie rozróżnia typów wątków; musi jedynie znać adres początkowy wątku, aby zacząć realizować wątek. MFC obsługuje wątki interfejsu użytkownika specjalnie poprzez dostarczanie funkcji "pompy komunikatów" zdarzeń w interfejsie użytkownika. `CWinApp` jest przykładem obiektu wątku interfejsu użytkownika, ponieważ pochodzi od `CWinThread` i obsługuje zdarzenia i komunikaty generowane przez użytkownika.  
  
Szczególną uwagę należy do sytuacji, gdy więcej niż jeden wątek może wymagać dostępu do tego samego obiektu. [Wielowątkowość: Porady dotyczące programowania](../parallel/multithreading-programming-tips.md) opisuje metody, których można użyć, aby uniknąć problemów, które mogą powstać w takich sytuacjach. [Wielowątkowość: Jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md) opisano, jak używać klas, które są dostępne do synchronizowania dostępu przez wiele wątków do pojedynczego obiektu.  
  
Pisanie i debugowanie wielowątkowego programowania jest natury skomplikowanym i trudnym przedsięwzięciem, ponieważ należy upewnić się, że obiekty nie są dostępne przez więcej niż jeden wątek jednocześnie. Tematy o wielowątkowości nie uczą podstaw programowania wielowątkowe, lecz jak używać MFC w programach wielowątkowych. Wielowątkowe próbki MFC zawarte w programie Visual C++ ilustrują kilka wielowątkowych funkcji API Win32 i nie wchodzą w skład MFC; jednak tylko mają one punkt wyjścia.  
  
Aby uzyskać więcej informacji na temat sposobu system operacyjny obsługuje procesy i wątki, zobacz [procesy i wątki](http://msdn.microsoft.com/library/windows/desktop/ms684841) w zestawie Windows SDK.  
  
Aby uzyskać więcej informacji dotyczących wielowątkowej obsługi MFC zobacz następujące tematy:  
  
- [Wielowątkowość: tworzenie wątków interfejsu użytkownika](../parallel/multithreading-creating-user-interface-threads.md)  
  
- [Wielowątkowość: tworzenie wątków roboczych](../parallel/multithreading-creating-worker-threads.md)  
  
- [Wielowątkowość: jak używać klas synchronizacji](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
- [Wielowątkowość: przerywanie wątków](../parallel/multithreading-terminating-threads.md)  
  
- [Wielowątkowość: porady dotyczące programowania](../parallel/multithreading-programming-tips.md)  
  
- [Wielowątkowość: kiedy używać klas synchronizacji](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>Zobacz też  
 
[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)