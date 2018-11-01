---
title: Wielowątkowość z C++ i MFC
ms.date: 08/27/2018
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
ms.openlocfilehash: c707c1c117bbc0005b2b3da4ed39f083ae407b27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643420"
---
# <a name="multithreading-with-c-and-mfc"></a>Wielowątkowość z C++ i MFC

Biblioteka Microsoft Foundation Class (MFC) zapewnia obsługę aplikacji wielowątkowych. W tym temacie opisano procesy i ciągi oraz podejście MFC do wielowątkowości.

Proces jest wykonuje wystąpienie aplikacji. Na przykład gdy klikniesz dwukrotnie ikonę Notatnika, możesz uruchomić proces, który włącza Notatnik.

Wątek jest ścieżką wykonywania w ramach procesu. Kiedy uruchamiasz Notepad, system operacyjny tworzy proces i rozpoczyna wykonywanie podstawowego wątku tego procesu. Gdy ten wątek kończy, kończy również proces. Ten główny wątek jest dostarczony do systemu operacyjnego przez kod startowy w formie adresu funkcji. Zazwyczaj jest adres `main` lub `WinMain` funkcja, która jest dostarczana.

Jeśli chcesz, możesz utworzyć dodatkowe wątki nie w aplikacji. Można to zrobić, aby obsługiwać zadania tło lub konserwacji, jeśli nie chcesz, aby użytkownik czekał aż do ukończenia. Wszystkie wątki w aplikacjach MFC są reprezentowane przez [CWinThread](../mfc/reference/cwinthread-class.md) obiektów. W większości sytuacji nawet trzeba jawnie tworzyć tych obiektów; Zamiast tego, wywołaj funkcję pomocnika szablonu [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), co powoduje utworzenie `CWinThread` obiekt dla Ciebie.

MFC wyróżnia dwa rodzaje wątków: wątki interfejsu użytkownika oraz wątki robocze. Wątki interfejsu użytkownika są często używane do obsługi danych wejściowych użytkownika i reagowanie na zdarzenia i komunikaty generowane przez użytkownika. Wątki robocze są często używane do ukończenia zadania, takie jak ponowne obliczenie, które nie wymagają wprowadzenia danych przez użytkownika. Win32 API nie rozróżnia typów wątków; musi jedynie znać adres początkowy wątku, aby zacząć realizować wątek. MFC obsługuje wątki interfejsu użytkownika specjalnie poprzez dostarczanie funkcji "pompy komunikatów" zdarzeń w interfejsie użytkownika. `CWinApp` jest przykładem obiektu wątku interfejsu użytkownika, ponieważ pochodzi od `CWinThread` i obsługuje zdarzenia i komunikaty generowane przez użytkownika.

Szczególną uwagę należy do sytuacji, gdy więcej niż jeden wątek może wymagać dostępu do tego samego obiektu. [Wielowątkowość: Porady dotyczące programowania](multithreading-programming-tips.md) opisuje metody, których można użyć, aby uniknąć problemów, które mogą powstać w takich sytuacjach. [Wielowątkowość: Jak używać klas synchronizacji](multithreading-how-to-use-the-synchronization-classes.md) opisano, jak używać klas, które są dostępne do synchronizowania dostępu przez wiele wątków do pojedynczego obiektu.

Pisanie i debugowanie wielowątkowego programowania jest natury skomplikowanym i trudnym przedsięwzięciem, ponieważ należy upewnić się, że obiekty nie są dostępne przez więcej niż jeden wątek jednocześnie. Tematy o wielowątkowości nie uczą podstaw programowania wielowątkowe, lecz jak używać MFC w programach wielowątkowych. Wielowątkowe próbki MFC zawarte w programie Visual C++ ilustrują kilka wielowątkowych funkcji API Win32 i nie wchodzą w skład MFC; jednak tylko mają one punkt wyjścia.

Aby uzyskać więcej informacji na temat sposobu system operacyjny obsługuje procesy i wątki, zobacz [procesy i wątki](/windows/desktop/ProcThread/processes-and-threads) w zestawie Windows SDK.

Aby uzyskać więcej informacji dotyczących wielowątkowej obsługi MFC zobacz następujące tematy:

- [Wielowątkowość: tworzenie wątków interfejsu użytkownika](multithreading-creating-user-interface-threads.md)

- [Wielowątkowość: tworzenie wątków roboczych](multithreading-creating-worker-threads.md)

- [Wielowątkowość: jak używać klas synchronizacji](multithreading-how-to-use-the-synchronization-classes.md)

- [Wielowątkowość: przerywanie wątków](multithreading-terminating-threads.md)

- [Wielowątkowość: porady dotyczące programowania](multithreading-programming-tips.md)

- [Wielowątkowość: kiedy używać klas synchronizacji](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Zobacz też

[Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)