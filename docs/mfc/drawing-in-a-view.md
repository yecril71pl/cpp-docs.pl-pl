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
ms.openlocfilehash: 77844ebd31f624229870d27c72b08a987b7533bd
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280774"
---
# <a name="drawing-in-a-view"></a>Rysowanie w widoku

Niemal we wszystkich rysowania w aplikacji występuje w widoku `OnDraw` składowa konieczne jest przesłonięcie w klasie widoku. (Wyjątek stanowi myszy rysowania, omówione w [interpretowanie danych wejściowych za pomocą widok użytkownika](../mfc/interpreting-user-input-through-a-view.md).) Twoje `OnDraw` zastąpienia:

1. Pobiera dane, wywołując funkcje Członkowskie, których udzielasz dokumentu.

1. Wyświetla określone dane przez wywołanie funkcji składowych w ramach przekazywany do obiektu kontekstu urządzenia `OnDraw`.

Po zmianie danych dokumentu w jakiś sposób, widoku musi być narysowany ponownie, aby odzwierciedlić zmiany. Zwykle dzieje się po użytkownik wprowadza zmianę za pośrednictwem widoku do dokumentu. W takim przypadku widok wywołuje dokumentu [funkcji UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcja elementu członkowskiego, aby powiadomić wszystkich widoków na tym samym dokumencie, można zaktualizować samodzielnie. `UpdateAllViews` wywołuje każdego widoku [OnUpdate](../mfc/reference/cview-class.md#onupdate) funkcja elementu członkowskiego. Domyślna implementacja klasy `OnUpdate` unieważnia widok całego obszaru klienta. Można zastąpić go do unieważnienia tylko tych regionów obszaru klienckiego mapowane zmodyfikowane części dokumentu.

`UpdateAllViews` Funkcji składowej klasy typu `CDocument` i `OnUpdate` funkcji składowej klasy typu `CView` pozwalają przekazać informacje opisujące fragmenty dokumentu, które zostały zmodyfikowane. Ten mechanizm "wskazówki" pozwala ograniczyć obszar, który należy odświeżyć widok. `OnUpdate` przyjmuje dwa argumenty "wskazówki". Pierwsza strona, *lHint*, typu **LPARAM**, pozwala przekazywać żadnych danych, które lubisz, podczas gdy drugi, *pHint*, typu `CObject`*, pozwala przekazać wskaźnik do dowolnego obiektu pochodzącego z `CObject`.

Gdy widok staje się nieprawidłowy, Windows wysyła **WM_PAINT** wiadomości. Widok [OnPaint](../mfc/reference/cwnd-class.md#onpaint) funkcji obsługi odpowiada na komunikat, tworząc obiekt kontekstu urządzenia klasy [CPaintDC](../mfc/reference/cpaintdc-class.md) i wywołuje widoku `OnDraw` funkcja elementu członkowskiego. Zazwyczaj trzeba napisać, zastępowanie `OnPaint` funkcji obsługi.

A [kontekstu urządzenia](../mfc/device-contexts.md) jest strukturą danych Windows, który zawiera informacje o atrybuty rysowania urządzenia, np. wyświetlania lub drukarki. Wszystkie wywołania rysowania są wykonywane za pośrednictwem obiektów kontekstu urządzenia. Rysowania na ekranie `OnDraw` jest przekazywany `CPaintDC` obiektu. Do celów rysowania na drukarce, jest przekazywany [CDC](../mfc/reference/cdc-class.md) obiektu dla bieżącej drukarki.

Kod rysowania w widoku najpierw pobiera wskaźnik do dokumentu, a następnie wywołań rysowania za pomocą kontekstu urządzenia. Poniżej prostym `OnDraw` przykład ilustruje ten proces:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

W tym przykładzie należy zdefiniować `GetData` działać jako składowej klasy pochodnej dokumentu.

Przykład drukuje niezależnie od ciągu otrzymuje od dokumentu, a ich tematyka w widoku. Jeśli `OnDraw` wywołanie jest do rysowania ekranu `CDC` obiekt przekazany w *kontrolera pDC* jest `CPaintDC` której Konstruktor została już wywołana `BeginPaint`. Wywołania funkcji rysowania są nawiązywane przy użyciu wskaźnika kontekstu urządzenia. Informacje o kontekstach urządzenia i wywołania rysowania, zawiera klasa [CDC](../mfc/reference/cdc-class.md) w *odwołanie MFC* i [Praca z obiektami okien](../mfc/working-with-window-objects.md).

Aby uzyskać więcej przykładów jak napisać `OnDraw`, zobacz [próbki MFC](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Używanie widoków](../mfc/using-views.md)
