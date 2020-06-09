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
ms.openlocfilehash: c60d99fdebcd64ad844bc19918a30beb90b86af3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618936"
---
# <a name="drawing-in-a-view"></a>Rysowanie w widoku

Niemal cały rysunek w aplikacji występuje w `OnDraw` funkcji składowej widoku, która musi zostać przesłonięta w klasie widoku. (Wyjątkiem jest rysowanie myszy, omówione w [interpretacji danych wejściowych użytkownika przez widok](interpreting-user-input-through-a-view.md)). Twoje `OnDraw` zastąpienie:

1. Pobiera dane, wywołując funkcje składowe dokumentu, które udostępniasz.

1. Wyświetla dane przez wywoływanie funkcji członkowskich obiektu kontekstu urządzenia, do którego jest przekazywana Platforma `OnDraw` .

Gdy dane dokumentu zmieniają się w jakiś sposób, należy ponownie narysować widok, aby odzwierciedlić zmiany. Zazwyczaj dzieje się tak, gdy użytkownik wprowadza zmiany w widoku dokumentu. W takim przypadku widok wywołuje funkcję członkowską [funkcji UpdateAllViews](reference/cdocument-class.md#updateallviews) dokumentu w celu powiadomienia wszystkich widoków w tym samym dokumencie, aby je zaktualizować. `UpdateAllViews`wywołuje funkcję członkowską [OnUpdate](reference/cview-class.md#onupdate) każdego z widoków. Domyślna implementacja `OnUpdate` unieważnia cały obszar klienta widoku. Można zastąpić go, aby unieważnił tylko te regiony obszaru klienta, które są mapowane na zmodyfikowane fragmenty dokumentu.

`UpdateAllViews`Funkcja członkowska klasy `CDocument` i `OnUpdate` funkcja członkowska klasy `CView` umożliwiają przekazywanie informacji opisujących, jakie części dokumentu zostały zmodyfikowane. Ten mechanizm "podpowiedzi" umożliwia ograniczenie obszaru, który musi zostać ponownie narysowany przez widok. `OnUpdate`przyjmuje dwa argumenty "podpowiedzi". Pierwszy, *lHint*, typu **lParam**, umożliwia przekazywanie dowolnych danych, podczas gdy drugi, *pHint*typu `CObject` *, umożliwia przekazanie wskaźnika do dowolnego obiektu pochodnego od `CObject` .

Gdy widok jest nieprawidłowy, system Windows wysyła do niego komunikat **WM_PAINT** . Funkcja obsługi [OnPaint](reference/cwnd-class.md#onpaint) widoku odpowiada na komunikat przez utworzenie obiektu kontekstu urządzenia klasy [CPaintDC](reference/cpaintdc-class.md) i wywołanie `OnDraw` funkcji składowej widoku. Zwykle nie trzeba pisać zastępujące `OnPaint` funkcję procedury obsługi.

[Kontekst urządzenia](device-contexts.md) to struktura danych systemu Windows, która zawiera informacje o atrybutach rysowania urządzenia, takich jak wyświetlacz lub drukarka. Wszystkie wywołania rysowania są wykonywane za pomocą obiektu kontekstu urządzenia. Do rysowania na ekranie `OnDraw` jest przenoszona `CPaintDC` obiekt. Do rysowania na drukarce jest przenoszona obiekt [przechwytywania](reference/cdc-class.md) danych dla bieżącej drukarki.

Kod do rysowania w widoku najpierw Pobiera wskaźnik do dokumentu, a następnie nadaje się do rysowania wywołań za pomocą kontekstu urządzenia. Poniższy prosty `OnDraw` przykład ilustruje proces:

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

W tym przykładzie należy zdefiniować `GetData` funkcję jako element członkowski klasy dokumentu pochodnego.

Przykład drukuje dowolny ciąg pobierany z dokumentu, wyśrodkowany w widoku. Jeśli `OnDraw` wywołanie jest na potrzeby rysowania ekranu, `CDC` obiekt przeszedł w *PDC* , `CPaintDC` którego Konstruktor został już wywołany `BeginPaint` . Wywołania funkcji rysowania są wykonywane za pomocą wskaźnika kontekstu urządzenia. Aby uzyskać informacje na temat kontekstów urządzeń i wywołań rysowania, zobacz Klasa [przechwytywania](reference/cdc-class.md) zmian w *dokumentacji MFC* i [Praca z obiektami okien](working-with-window-objects.md).

Aby uzyskać więcej przykładów pisania `OnDraw` , zobacz [przykłady MFC](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Zobacz też

[Używanie widoków](using-views.md)
