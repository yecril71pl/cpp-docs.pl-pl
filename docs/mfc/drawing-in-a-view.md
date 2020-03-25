---
title: Rysowanie w widoku
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214347"
---
# <a name="drawing-in-a-view"></a>Rysowanie w widoku

Niemal cały rysunek w aplikacji występuje w `OnDraw` funkcji członkowskiej widoku, która musi zostać przesłonięta w klasie widoku. (Wyjątkiem jest rysowanie myszy, omówione w [interpretacji danych wejściowych użytkownika przez widok](../mfc/interpreting-user-input-through-a-view.md)). Przesłonięcie `OnDraw`:

1. Pobiera dane, wywołując funkcje składowe dokumentu, które udostępniasz.

1. Wyświetla dane przez wywoływanie funkcji członkowskich obiektu kontekstu urządzenia, który jest przekazywany przez platformę do `OnDraw`.

Gdy dane dokumentu zmieniają się w jakiś sposób, należy ponownie narysować widok, aby odzwierciedlić zmiany. Zazwyczaj dzieje się tak, gdy użytkownik wprowadza zmiany w widoku dokumentu. W takim przypadku widok wywołuje funkcję członkowską [funkcji UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) dokumentu w celu powiadomienia wszystkich widoków w tym samym dokumencie, aby je zaktualizować. `UpdateAllViews` wywołuje funkcję elementu członkowskiego " [OnUpdate](../mfc/reference/cview-class.md#onupdate) " każdej z widoków. Domyślna implementacja `OnUpdate` unieważnia cały obszar klienta widoku. Można zastąpić go, aby unieważnił tylko te regiony obszaru klienta, które są mapowane na zmodyfikowane fragmenty dokumentu.

`UpdateAllViews` funkcja członkowska klasy `CDocument` i `OnUpdate` funkcja członkowska klasy `CView` umożliwiają przekazywanie informacji opisujących, jakie części dokumentu zostały zmodyfikowane. Ten mechanizm "podpowiedzi" umożliwia ograniczenie obszaru, który musi zostać ponownie narysowany przez widok. `OnUpdate` przyjmuje dwa argumenty "podpowiedzi". Pierwszy, *lHint*, typu **lParam**, umożliwia przekazywanie dowolnych danych, podczas gdy drugi, *pHint*typu `CObject`*, umożliwia przekazanie wskaźnika do dowolnego obiektu pochodnego od `CObject`.

Gdy widok jest nieprawidłowy, system Windows wysyła do niego komunikat **WM_PAINT** . Funkcja obsługi [OnPaint](../mfc/reference/cwnd-class.md#onpaint) widoku odpowiada na komunikat przez utworzenie obiektu kontekstu urządzenia klasy [CPaintDC](../mfc/reference/cpaintdc-class.md) i wywołuje funkcję członkowską `OnDraw`nego widoku. Zwykle nie trzeba pisać zastępujące funkcję procedury obsługi `OnPaint`.

[Kontekst urządzenia](../mfc/device-contexts.md) to struktura danych systemu Windows, która zawiera informacje o atrybutach rysowania urządzenia, takich jak wyświetlacz lub drukarka. Wszystkie wywołania rysowania są wykonywane za pomocą obiektu kontekstu urządzenia. Do rysowania na ekranie `OnDraw` jest przenoszona `CPaintDC` obiektu. Do rysowania na drukarce jest przenoszona obiekt [przechwytywania](../mfc/reference/cdc-class.md) danych dla bieżącej drukarki.

Kod do rysowania w widoku najpierw Pobiera wskaźnik do dokumentu, a następnie nadaje się do rysowania wywołań za pomocą kontekstu urządzenia. Poniższy przykład prostego `OnDraw` ilustruje proces:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

W tym przykładzie należy zdefiniować funkcję `GetData` jako element członkowski klasy dokumentu pochodnego.

Przykład drukuje dowolny ciąg pobierany z dokumentu, wyśrodkowany w widoku. Jeśli wywołanie `OnDraw` jest przeznaczone do rysowania ekranu, obiekt `CDC`, który przeszedł w *kontrolerze PDC* , jest `CPaintDC`, którego Konstruktor ma już nazwę `BeginPaint`. Wywołania funkcji rysowania są wykonywane za pomocą wskaźnika kontekstu urządzenia. Aby uzyskać informacje na temat kontekstów urządzeń i wywołań rysowania, zobacz Klasa [przechwytywania](../mfc/reference/cdc-class.md) zmian w *dokumentacji MFC* i [Praca z obiektami okien](../mfc/working-with-window-objects.md).

Aby uzyskać więcej przykładów dotyczących pisania `OnDraw`, zobacz [przykłady MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Zobacz też

[Używanie widoków](../mfc/using-views.md)
