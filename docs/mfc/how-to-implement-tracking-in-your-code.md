---
title: 'Porady: Implementowanie śledzenia w kodzie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc21369dd8d241bd00da2a0a8005c977094c3abf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932097"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Porady: implementowanie śledzenia w kodzie
Aby śledzić element OLE, musi obsługiwać określone zdarzenia związanego z elementem, na przykład klikając je lub aktualizowanie widoku dokumentu. We wszystkich przypadkach jest wystarczające, aby zadeklarować tymczasowej [crecttracker —](../mfc/reference/crecttracker-class.md) obiektu i manipulowania elementem za pomocą tego obiektu.  
  
 Gdy użytkownik wybiera element lub obiektu za pomocą polecenia menu wstawia, należy zainicjować śledzenia przy użyciu właściwego stylów do reprezentowania stanu elementu OLE. W poniższej tabeli przedstawiono konwencje użytego w próbce OCLIENT. Aby uzyskać więcej informacji na temat tych stylów, zobacz `CRectTracker`.  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>Style kontenera i stanów elementu OLE  
  
|Styl wyświetlane|Stan elementu OLE|  
|---------------------|-----------------------|  
|Obramowanie kropkowanej|Element jest połączony|  
|Stałe obramowania|Element jest osadzony w dokumencie|  
|Uchwyty zmiany rozmiaru|Zaznaczonego elementu|  
|Kreskowane obramowanie|Element jest obecnie aktywny w miejscu|  
|Element nakładki wzorzec kreskowaniu|Elementu server jest otwarty|  
  
 Może obsługiwać ten inicjowania za pomocą procedury, która sprawdza stan elementu OLE i ustawia odpowiednie style. `SetupTracker` Funkcji dostępnej w przykładowym OCLIENT pokazuje inicjowania śledzenia. Parametry dla tej funkcji są adres śledzenia, *pTracker*; wskaźnik do elementu klienta, który jest powiązany z obiektem śledzącym, *pItem*; i wskaźnika do prostokąta, *pTrueRect* . Na pełniejsze przykład tej funkcji, zobacz przykład MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 **SetupTracker** przykładowy kod przedstawia informacje o jednej funkcji; rozmieszczonymi wierszy funkcji z omówieniem funkcji funkcji:  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 Śledzący został zainicjowany przez ustawienie minimalnego rozmiaru i wyczyszczenie styl śledzący.  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 Następujące wiersze Sprawdź, czy element jest aktualnie zaznaczony i określa, czy element jest połączony z dokumentem lub osadzonych w niej. Uchwyty zmiany rozmiaru znajduje się wewnątrz obramowania są dodawane do stylu, wskazujący, że element jest aktualnie zaznaczony. Jeśli element jest połączony z dokumentu, jest używany styl obramowania kropkami. Ciągłe obramowanie zostanie użyty, jeśli element jest wbudowany.  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 Otwórz element wzorem kreskowanym, jeśli element jest obecnie następujące nakładki kodu.  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 Ta funkcja może wywoływać, zawsze, gdy obiektem śledzącym ma być wyświetlana. Na przykład wywołanie tej funkcji z `OnDraw` funkcji klasy widoku. Spowoduje to zaktualizowanie wygląd tracker zawsze, gdy widok jest odowieżany. Pełny przykład, zobacz `CMainView::OnDraw` funkcja próbki MFC OLE [OCLIENT](../visual-cpp-samples.md).  
  
 W aplikacji zdarzenia, które wymagają kodu śledzenia, na przykład zmiany rozmiaru, przesuwania lub trafień wykrywanie, zostanie przeprowadzona. Te akcje zazwyczaj wskazują, że trwa próby pobrania lub Przenieś element. W takich sytuacjach należy zdecydować, co zostało chwycić: uchwyt zmiany rozmiaru lub części granicy między uchwyty zmiany rozmiaru. `OnLButtonDown` Obsługi wiadomości jest dobrym miejscem do testowania położenie myszy w odniesieniu do elementu. Wywoływania `CRectTracker::HitTest`. Jeśli test zwraca wartość inną niż `CRectTracker::hitOutside`, element jest zmiany rozmiaru lub przeniesiony. W związku z tym należy wywołanie `Track` funkcję elementu członkowskiego. Zobacz `CMainView::OnLButtonDown` funkcji znajduje się w przykładowym MFC OLE [OCLIENT](../visual-cpp-samples.md) pełny przykład.  
  
 `CRectTracker` Klasa udostępnia kilka kształtów inny kursor służy do wskazania, czy ruch, Zmień rozmiar lub przeciągnij operacja odbywa się. Obsługa tego zdarzenia, sprawdź, czy jest zaznaczony element obecnie w użyciu myszy. Jeśli tak jest, wywoływania `CRectTracker::SetCursor`, lub wywołaj domyślny program obsługi. Poniższy przykład pochodzi z przykładowej MFC OLE [OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Trackery: implementowanie trackerów w aplikacji OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

