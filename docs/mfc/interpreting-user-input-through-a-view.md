---
title: Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 3ef23ad74e1ff53d947453faa5682c5ecc1f4e43
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310919"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretowanie danych wprowadzonych przez użytkownika za pośrednictwem widoku

Inne funkcje Członkowskie widoku obsługiwać i interpretować wszystkie dane wejściowe użytkownika. Zazwyczaj określi funkcji elementów członkowskich obsługi wiadomości w klasie widoku do przetworzenia:

- Windows [wiadomości](../mfc/messages.md) wygenerowany przez akcje myszy i klawiatury.

- [Polecenia](../mfc/user-interface-objects-and-command-ids.md) z menu, przyciski paska narzędzi i klawiszy skrótów.

Te funkcje elementów członkowskich programu obsługi komunikatów następujące akcje następuje interpretacja jako danych wejściowych, wybór lub edytowania, przenoszenie danych do i ze Schowka w tym:

- Ruchów myszy i kliknięcia, przeciągnie a dwukrotnymi kliknięciami

- Naciśnięć klawiszy

- Polecenia menu

Wiadomości, które Windows usługi obsługuje widoku zależy od potrzeb aplikacji.

[Obsługa i mapowanie tematów komunikatów](../mfc/message-handling-and-mapping.md) wyjaśniono, jak przypisać elementy menu i innych obiektów interfejsu użytkownika do poleceń i jak powiązać polecenia do obsługi funkcji. [Obsługa i mapowanie tematów komunikatów](../mfc/message-handling-and-mapping.md) także wyjaśnia, jak MFC kieruje polecenia i wysyła standardowe komunikaty Windows do obiektów, które zawierają programy obsługi dla nich.

Na przykład aplikacja może być konieczne wdrożenia bezpośrednich myszy Rysowanie w widoku. Próbki Bazgroły pokazuje, jak obsługiwać komunikaty WM_LBUTTONDOWN WM_MOUSEMOVE i WM_LBUTTONUP, odpowiednio, aby rozpocząć, kontynuować i kończyć się rysowanie segment linii. Z drugiej strony czasami konieczne może być interpretacji kliknięcie myszki w widoku jako zaznaczenia. Widoku `OnLButtonDown` funkcji obsługi będzie określić, czy rysowanie lub wybranie użytkownika. W przypadku wybrania opcji, program obsługi może określić, czy kliknięcie w granicach obiektu w widoku, a jeśli tak, należy zmienić widok, aby pokazać obiekt jako wybrany.

Widok może również obsługiwać niektórych poleceń, takich jak z menu Edytuj, aby wycinanie, kopiowanie, wklejanie lub usuwanie wybranych danych korzystanie ze Schowka. Program obsługi wywoływałby niektóre powiązane Schowka element członkowski funkcji klasy `CWnd` na przesyłanie elementu wybrane dane do lub ze Schowka.

## <a name="see-also"></a>Zobacz także

[Używanie widoków](../mfc/using-views.md)
