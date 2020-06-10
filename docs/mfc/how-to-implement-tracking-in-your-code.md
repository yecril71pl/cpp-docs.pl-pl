---
title: 'Porady: implementowanie śledzenia w kodzie'
ms.date: 11/04/2016
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
ms.openlocfilehash: 3d71543261021c7e20041d317401b7b7b8d0616e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621669"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Porady: implementowanie śledzenia w kodzie

Aby śledzić element OLE, należy obsłużyć pewne zdarzenia związane z elementem, takie jak kliknięcie elementu lub zaktualizowanie widoku dokumentu. We wszystkich przypadkach wystarczy zadeklarować tymczasowy obiekt [CRectTracker](reference/crecttracker-class.md) i manipulować elementem przy użyciu tego obiektu.

Gdy użytkownik wybierze element lub wstawi obiekt z poleceniem menu, musisz zainicjować śledzenie przy użyciu odpowiednich stylów, aby reprezentować stan elementu OLE. Poniższa tabela zawiera opis Konwencji używanych przez przykład OCLIENT. Aby uzyskać więcej informacji na temat tych stylów, zobacz `CRectTracker` .

### <a name="container-styles-and-states-of-the-ole-item"></a>Style kontenera i Stany elementu OLE

|Wyświetlany styl|Stan elementu OLE|
|---------------------|-----------------------|
|Obramowanie kropkowane|Element jest połączony|
|Stałe obramowanie|Element jest osadzony w dokumencie|
|Uchwyty zmiany rozmiaru|Element jest obecnie zaznaczony|
|Kreskowane obramowanie|Element jest obecnie aktywny|
|Element nakładający się wzorca kreskowanego|Serwer elementu jest otwarty|

Można łatwo obsługiwać tę inicjalizację przy użyciu procedury, która sprawdza stan elementu OLE i ustawia odpowiednie style. `SetupTracker`Funkcja znaleziona w przykładzie OCLIENT demonstruje inicjalizację narzędzia do śledzenia. Parametry tej funkcji są adresami modułu śledzącego, *pTracker*; wskaźnik do elementu klienta, który jest powiązany z modułem śledzącym, *pItem*; i wskaźnik do prostokąta, *pTrueRect*. Aby zapoznać się z bardziej kompletnym przykładem tej funkcji, zobacz przykład OLE MFC [OCLIENT](../overview/visual-cpp-samples.md).

Przykład kodu **SetupTracker** przedstawia pojedynczą funkcję; wiersze funkcji są przeplatane z omówieniem funkcji funkcji:

[!code-cpp[NVC_MFCOClient#1](codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]

Moduł śledzący jest inicjowany przez ustawienie minimalnego rozmiaru i wyczyszczenie stylu modułu śledzącego.

[!code-cpp[NVC_MFCOClient#2](codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]

Poniższe wiersze sprawdzają, czy element jest obecnie zaznaczony i czy element jest połączony z dokumentem lub osadzony. Uchwyty zmiany rozmiaru znajdujące się wewnątrz obramowania są dodawane do stylu, co oznacza, że element jest obecnie zaznaczony. Jeśli element jest połączony z dokumentem, używany jest styl obramowania kropkowanego. Gdy element jest osadzony, jest używany pełny obramowanie.

[!code-cpp[NVC_MFCOClient#3](codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]

Poniższy kod nakłada element z wzorcem, jeśli element jest aktualnie otwarty.

[!code-cpp[NVC_MFCOClient#4](codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]

Następnie można wywołać tę funkcję za każdym razem, gdy śledzenie ma być wyświetlane. Na przykład Wywołaj tę funkcję z `OnDraw` funkcji klasy widoku. Spowoduje to zaktualizowanie wyglądu narzędzia śledzącego za każdym razem, gdy widok zostanie odmalowany. Aby zapoznać się z kompletnym przykładem, zobacz `CMainView::OnDraw` Funkcja przykładowej klasy MFC OLE [OCLIENT](../overview/visual-cpp-samples.md).

W aplikacji są wykonywane zdarzenia wymagające kodu śledzenia, takie jak zmiana rozmiarów, przechodzenie lub wykrywanie trafień. Te akcje zwykle wskazują, że podjęto próbę pobrania lub przeniesienia elementu. W takich przypadkach należy zdecydować, co zostało wychwycone: uchwyt zmiany rozmiaru lub część obramowania między uchwytami zmiany rozmiaru. `OnLButtonDown`Program obsługi komunikatów jest dobrym miejscem do testowania pozycji myszy w odniesieniu do elementu. Wykonaj wywołanie `CRectTracker::HitTest` . Jeśli test zwróci coś poza `CRectTracker::hitOutside` , rozmiar elementu jest zmieniany lub przenoszony. W związku z tym należy wykonać wywołanie `Track` funkcji składowej. Zobacz `CMainView::OnLButtonDown` funkcję znajdującą się w przykładowej [OCLIENT](../overview/visual-cpp-samples.md) MFC OLE, aby uzyskać kompletny przykład.

`CRectTracker`Klasa zawiera kilka różnych kształtów kursorów używanych do wskazywania, czy odbywa się Operacja przenoszenia, zmiany rozmiaru lub przeciągania. Aby obsłużyć to zdarzenie, sprawdź, czy element aktualnie pod myszą jest zaznaczony. Jeśli tak, wykonaj wywołanie `CRectTracker::SetCursor` lub wywołaj domyślną procedurę obsługi. Poniższy przykład pochodzi z przykładu [OCLIENT](../overview/visual-cpp-samples.md)MFC OLE:

[!code-cpp[NVC_MFCOClient#5](codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Trackery: implementowanie trackerów w aplikacji OLE](trackers-implementing-trackers-in-your-ole-application.md)
