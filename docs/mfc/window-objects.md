---
title: Obiekty okien
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
ms.openlocfilehash: 3e20ef1f3643b9e802c7cdc399d3436ceadeae79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566702"
---
# <a name="window-objects"></a>Obiekty okien

MFC udostępnia klasy [CWnd](../mfc/reference/cwnd-class.md) do hermetyzacji `HWND` uchwyt okna. `CWnd` Obiekt jest obiektem okna języka C++ od `HWND` reprezentujący Windows, ale okno zawierające je. Użyj `CWnd` do wyprowadzenia okna podrzędnego klasy lub użyj jednego z wielu klas MFC pochodną `CWnd`. Klasa `CWnd` jest klasą bazową dla wszystkich okien, w tym okna ramowe, okna dialogowe, okien podrzędnych, formantów i pasków sterowania, takie jak paski narzędzi. Współdziałających z [relację między obiektem okna języka C++ a właściwością HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) ma kluczowe znaczenie dla skutecznego programowania z MFC.

Biblioteka MFC zawiera niektóre funkcje domyślne i zarządzanie systemem windows, ale może pochodzić klasy z `CWnd` i użyj jej funkcje Członkowskie, aby dostosować funkcjonalność podana. Można również tworzyć podrzędne okna tworząc `CWnd` obiektu i wywoływania jego [Utwórz](../mfc/reference/cwnd-class.md#create) element członkowski funkcji, a następnie dostosować okien podrzędnych za pomocą `CWnd` funkcji elementów członkowskich. Możesz osadzić obiekty opracowane na podstawie [CView](../mfc/reference/cview-class.md), takich jak widoki formularzy lub widok drzewa, w oknie ramki. Może obsługiwać wiele widoków dokumentów za pośrednictwem rozdzielacz okienka, dostarczonych przez klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Każdy obiekt pochodzi od klasy `CWnd` zawiera mapy komunikatów, za pomocą którego można mapy wiadomości Windows lub identyfikatory poleceń Twoje własne programy obsługi.

Ogólne materiały dotyczące programowania dla Windows jest dobry zasobem w nauce używania `CWnd` funkcje Członkowskie, które hermetyzują `HWND` interfejsów API.

## <a name="functions-for-operating-on-a-cwnd"></a>Funkcje działające CWnd

`CWnd` i jego [pochodne klasy okien](../mfc/derived-window-classes.md) konstruktory, destruktory i elementów członkowskich do inicjalizacji obiektu, utworzyć podstawowe struktury Windows i dostęp do zhermetyzowanego `HWND`. `CWnd` udostępnia również funkcje Członkowskie, które hermetyzują Windows API do wysyłania wiadomości, uzyskiwanie dostępu do stanu okna, Konwersja współrzędnych, aktualizowanie, przewijania, uzyskiwanie dostępu do Schowka i wiele innych zadań. Większość Windows API zarządzania systemem Windows, które umożliwiają wykorzystywanie `HWND` argument są hermetyzowane jako funkcje Członkowskie `CWnd`. Nazwy funkcji i ich parametry są zachowywane w `CWnd` funkcja elementu członkowskiego. Aby uzyskać szczegółowe informacje o interfejsach API Windows, zamknięte przez `CWnd`, można znaleźć klasy [CWnd](../mfc/reference/cwnd-class.md).

## <a name="cwnd-and-windows-messages"></a>Komunikaty Windows i CWnd

Jedną z głównych `CWnd` ma na celu dostarczenie interfejsu obsługi wiadomości Windows, takich jak WM_PAINT lub WM_MOUSEMOVE. Wiele funkcji elementu członkowskiego `CWnd` są programy obsługi dla standardowych komunikatów — zaczynających się od identyfikatora **afx_msg** i prefiksu "Włączone", takich jak `OnPaint` i `OnMouseMove`. [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md) obejmuje wiadomości i komunikatów w szczegóły. Informacje dotyczą równie framework w systemie windows, a te utworzyć samodzielnie do specjalnych celów.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Relacja między obiektem okna języka C++ a właściwością HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Pochodne klasy okien](../mfc/derived-window-classes.md)

- [Tworzenie okien](../mfc/creating-windows.md)

- [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

- [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Praca z obiektami okien](../mfc/working-with-window-objects.md)

- [Konteksty urządzenia](../mfc/device-contexts.md): obiekty, które uniezależnić Windows rysowania urządzenia

- [Obiekty graficzne](../mfc/graphic-objects.md): pióra, pędzle, czcionki, mapy bitowe, palet, regionów

## <a name="see-also"></a>Zobacz też

[Windows](../mfc/windows.md)

