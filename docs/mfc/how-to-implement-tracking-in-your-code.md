---
title: 'Instrukcje: Implementowanie śledzenia w kodzie'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 0f037480e83b8ca1ba12af56904afe25a33e4d6c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58774467"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Instrukcje: Implementowanie śledzenia w kodzie

Aby śledzić elementu OLE, musi obsługiwać określonych zdarzeń związanych z elementu, na przykład klikając je lub aktualizowania widoku dokumentu. We wszystkich przypadkach jest wystarczające, aby zadeklarować tymczasowego [CRectTracker](../mfc/reference/crecttracker-class.md) obiektu i manipulowania elementem przy użyciu tego obiektu.

Gdy użytkownik wybierze element lub wstawienie obiektu za pomocą polecenia menu, musi zostać zainicjowany śledzenia przy użyciu odpowiednich stylów do reprezentowania stanu elementu OLE. W poniższej tabeli przedstawiono Konwencji używanych przez przykład OCLIENT. Aby uzyskać więcej informacji na temat tych stylów, zobacz `CRectTracker`.

### <a name="container-styles-and-states-of-the-ole-item"></a>Style kontenera i stany elementu OLE

|Styl wyświetlane|Stan elementu OLE|
|---------------------|-----------------------|
|Kropkowane obramowanie|Połączony element|
|Obramowanie ciągłe|Element jest osadzony w dokumencie|
|Uchwyty zmiany rozmiaru|Element jest aktualnie wybrany.|
|Kreskowane obramowanie|Element jest aktualnie aktywny w miejscu|
|Element nakładki wzorzec kreskowaniu|Serwer elementu jest otwarty|

Może obsługiwać ten proces inicjowania przy użyciu procedury, która sprawdza stan elementu OLE i ustawia odpowiednie style. `SetupTracker` Funkcji dostępnej w przykładzie OCLIENT pokazuje inicjowania śledzenia. Parametry dla tej funkcji to adres modułu śledzącego *pTracker*; wskaźnik do elementu klienta, który jest powiązany z obiektem śledzącym, *pItem*; i wskaźnik prostokąt, *pTrueRect* . Aby uzyskać bardziej szczegółowy przykład tej funkcji, zobacz przykład MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

**SetupTracker** przykładowy kod przedstawia jednej funkcji; wiersze funkcji są grupową dyskusję na temat funkcji funkcji:

[!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

Śledzenie jest inicjowany przez ustawienie minimalnego rozmiaru i wyczyszczenie styl śledzący.

[!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Następujące wiersze Sprawdź, czy jest aktualnie wybrany element i tego, czy element jest połączony z dokumentem lub osadzone w nim. Uchwytami zmiany rozmiaru, znajduje się wewnątrz obramowania są dodawane do stylu, wskazującą, czy element jest aktualnie wybrany. Jeśli element jest połączony z dokumentu, używany jest styl obramowania kropkowana. Ciągłe obramowanie jest używana, jeśli element jest osadzony.

[!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

Otwórz element z kreskowanym wzorca, jeśli element znajduje się obecnie następujące nakładki kodu.

[!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

Następnie możesz wywołać tę funkcję, zawsze, gdy obiektem śledzącym ma być wyświetlana. Na przykład wywołać tę funkcję z `OnDraw` funkcji klasy widoku. Spowoduje to zaktualizowanie wygląd modułu śledzącego zawsze wtedy, gdy widok jest odświeżana. Aby uzyskać kompletny przykład, zobacz `CMainView::OnDraw` funkcja próbki MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

W aplikacji zdarzenia, które wymagają śledzenia kodu, takich jak wykrywanie zmiany rozmiaru, przenoszenie lub trafień, wystąpi. Te akcje zazwyczaj wskazują, że jest podejmowana jest próba pobrania lub Przenieś element w. W takich przypadkach należy zdecydować, co zostało złapał: uchwyt zmiany rozmiaru lub części granicy między uchwyty zmiany rozmiaru. `OnLButtonDown` Obsługi wiadomości jest dobrym miejscem do testowania położenie kursora myszy w odniesieniu do elementu. Wywołanie `CRectTracker::HitTest`. Jeśli test zwraca coś, co oprócz `CRectTracker::hitOutside`, element jest rozmiar lub przenieść. W związku z tym, należy po wywołaniu `Track` funkcja elementu członkowskiego. Zobacz `CMainView::OnLButtonDown` funkcji znajduje się w próbce MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) pełny przykład.

`CRectTracker` Klasa udostępnia kilka kształtów różne kursora służy do wskazywania, czy przenoszenie, zmiana rozmiaru, przeciągnij działanie odbywa się. Aby obsługiwać to zdarzenie, sprawdź, czy element umieszczono wskaźnik myszy jest zaznaczone. Jeśli tak jest, wywołania `CRectTracker::SetCursor`, lub wywołaj domyślny program obsługi. Poniższy przykład pochodzi z przykładu MFC OLE [OCLIENT](../overview/visual-cpp-samples.md):

[!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Zobacz także

[Trackery: Implementowanie Trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)
