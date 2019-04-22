---
title: 'TN040: Praca w miejscu MFC / OLE — Zmienianie rozmiaru i powiększanie'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: c2cb25388184ac969bec7c01d8077a458c03a03a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775286"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: Praca w miejscu MFC/OLE — Zmienianie rozmiaru i powiększanie

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga omówi zagadnienia odnoszące się do edycji w miejscu oraz jak serwer powinien wykonać poprawną powiększanie i zmiany rozmiaru w miejscu. Za pomocą aktywacji w miejscu WYSIWYG pojęcia są podejmowane krok dalej w tym kontenery i serwery współpracują ze sobą, a w szczególności interpretacji specyfikacji OLE w taki sam sposób.

Ze względu na zamknięcia interakcji między kontenera i serwera obsługi aktywacji w miejscu istnieje szereg oczekiwań od użytkownika końcowego, który należy utrzymywać:

- Wyświetlanie prezentacji (metaplik rysowania w `COleServerItem::OnDraw` zastąpić) powinna wyglądać dokładnie takie same jak podczas jej rysowania do edycji (z tą różnicą, że narzędzia do edycji nie jest widoczna).

- Gdy kontener powiększa, okno serwer powinien to robić!

- Kontener i serwer powinien być wyświetlany obiektów do edycji przy użyciu tych samych metryk. Oznacza to, przy użyciu trybu mapowania, w oparciu o liczbę *logiczne* pikseli na cal — nie fizycznych pikseli na cal, podczas renderowania na urządzenia.

> [!NOTE]
>  Ponieważ aktywacji w miejscu ma zastosowanie tylko do elementów, które są osadzone (nie jest połączony), powiększanie ma zastosowanie tylko do obiektów osadzonych. Interfejsy API będą widoczne w obu `COleServerDoc` i `COleServerItem` służące do powiększania. Przyczyną tego dichotomy jest, czy tylko te funkcje, które są prawidłowe dla połączonych i osadzone elementy znajdują się w `COleServerItem` (umożliwia to mają wspólne implementacji) i funkcje, które są prawidłowe tylko w przypadku obiektów osadzonych znajdują się w `COleServerDoc` klasy (z perspektywy serwera jest **dokumentu** który jest osadzony).

Większość obciążeń jest umieszczany na implementujący serwera, serwer musi mieć świadomość współczynnika powiększenia kontenera i zmodyfikować jego edycji interfejs zgodnie z potrzebami. Ale jaki sposób serwer określa współczynnika powiększenia używanej kontenera

## <a name="mfc-support-for-zooming"></a>Obsługa MFC dla powiększania

Można określić bieżące współczynnika powiększenia przez wywołanie metody `COleServerDoc::GetZoomFactor`. To wywołanie, gdy dokument nie jest aktywny w miejscu zawsze spowoduje współczynnik powiększeniu 100% (lub współczynnik 1:1). Jej wywołanie gdy aktywny w miejscu może zwrócić coś innego niż 100%.

Na przykład powiększanie poprawnie zobacz przykładową MFC OLE [HIERSVR](../overview/visual-cpp-samples.md). Powiększanie HIERSVR jest skomplikowane faktem, że wyświetla tekst i tekstu, ogólnie rzecz biorąc, nie działa w sposób liniowy (wskazówek, konwencje związane z typografią, projekt szerokości i wysokości wszystkich skomplikować sprawy). Jednak HIERSVR jest uzasadnione odwołanie do implementowania powiększanie poprawnie, a więc jest to samouczek MFC [BAZGROŁY](../overview/visual-cpp-samples.md) (krok 7).

`COleServerDoc::GetZoomFactor` Określa współczynnika powiększenia, w oparciu o szereg różnych dostępnych metryk z kontenera lub z wdrożenia usługi `COleServerItem` i `COleServerDoc` klasy. Krótko mówiąc bieżący współczynnika powiększenia jest określany za pomocą następującego wzoru:

```
Position Rectangle (PR) / Container Extent (CE)
```

Pozycja prostokąta jest określana przez kontener. Jest zwracany do serwera podczas aktywacji w miejscu po `COleClientItem::OnGetItemPosition` nosi nazwę i jest aktualizowany, gdy kontener wywoła serwera `COleServerDoc::OnSetItemRects` (z wywołaniem `COleClientItem::SetItemRects`).

W zakresie kontenera jest nieco bardziej skomplikowane obliczenia. Jeśli kontener została wywołana `COleServerItem::OnSetExtent` (z wywołaniem `COleClientItem::SetExtent`), w zakresie kontenera jest tę wartość, konwertowana na piksele na podstawie liczby pikseli na cal logiczny. Jeśli kontener nie wywołał SetExtent (co zwykle tak jest), a następnie w zakresie kontenera jest rozmiar zwrócony przez `COleServerItem::OnGetExtent`. Tak, jeśli kontener nie wywołał SetExtent, struktura przyjęto założenie, jeśli tak kontenera będzie wywołaniu go w 100% naturalnych zakresu (wartość zwracana z `COleServerItem::GetExtent`). Wyrażam innym sposobem ramach przyjęto założenie, że w kontenerze są wyświetlane 100% (większa, nie mniejszą) elementu.

Ważne jest, aby pamiętać, że chociaż `COleServerItem::OnSetExtent` i `COleServerItem::OnGetExtent` podobnych nazwach mogą nie manipulowania tego samego atrybutu elementu. `OnSetExtent` jest wywoływana, aby umożliwić serwera wiedzieć, ile obiekt jest widoczny w kontenerze (niezależnie od współczynnika powiększenia) i `OnGetExtent` jest wywoływany przez kontener, aby określić rozmiar idealny obiektu.

Patrząc na poszczególnych interfejsów API, które są zaangażowani, można uzyskać lepszy obraz:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Ta funkcja powinna zwrócić "naturalny rozmiar" w jednostkach HIMETRIC elementu. Najlepiej jest myśleć o "naturalny rozmiar" jest jego wartość jest definiowana jako rozmiar, który może pojawić się po wydrukowaniu. Rozmiar zwrócony w tym miejscu jest stałe dla zawartości elementu (podobnie do metaplik, który jest stałe dla określonego elementu). Ten rozmiar nie zmienia się podczas powiększania jest stosowany do elementu. Zazwyczaj nie zmienia się podczas kontenera zapewnia elementu miejsce więcej lub mniej, wywołując `OnSetExtent`. Przykładem zmiany może być w przypadku prostego edytora tekstów nie możliwości "Marża", który zawiniętego tekstu w oparciu o w zakresie ostatnich wysłana przez kontener. Jeśli serwer ulega zmianie, serwer prawdopodobnie należy ustawić OLEMISC_RECOMPOSEONRESIZE bit w rejestrze systemowym (zobacz w dokumentacji zestawu SDK OLE, aby uzyskać więcej informacji na temat tej opcji).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Ta funkcja jest wywoływana, gdy kontener zawiera "więcej lub mniej" obiektu. Większość kontenerów nie wywoła to wcale. Domyślna implementacja przechowuje ostatnią wartość odebranych z kontenera w usłudze "m_sizeExtent", który jest używany w `COleServerDoc::GetZoomFactor` podczas obliczania wartości zakresu kontenera opisanych powyżej.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Ta funkcja jest wywoływana tylko wtedy, gdy dokument jest aktywny w miejscu. Jest ona wywoływana po zaktualizowaniu kontenera, położenie elementu lub wycinka stosowany do elementu. Pozycja prostokąta, jak wspomniano powyżej, zapewnia licznik Obliczanie współczynnika powiększenia. Serwer może żądać, że położenie elementu można zmienić, wywołując `COleServerDoc::RequestPositionChange`. Kontener może lub nie może odpowiedzieć na to żądanie, wywołując `OnSetItemRects` (z wywołaniem `COleServerItem::SetItemRects`).

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

Ważne jest, aby należy pamiętać, że metaplik utworzonych przez zastąpienie `COleServerItem::OnDraw` tworzy dokładnie tych samych metaplik, niezależnie od bieżącej współczynnika powiększenia. Kontener będzie skalowana metaplik zgodnie z potrzebami. Jest to ważna różnica między wyświetlaniem `OnDraw` i element serwera `OnDraw`. Po prostu tworzy powiększania uchwytów widoku elementu *którą można powiększać* metaplik i pozostawi je do kontenera w celu odpowiedniego powiększanie.

Najlepszym sposobem, aby mieć pewność, że serwer działa poprawnie, jest użycie wdrożenia `COleServerDoc::GetZoomFactor` Jeśli Twój dokument jest aktywny w miejscu.

## <a name="mfc-support-for-in-place-resizing"></a>Obsługa MFC dla rozmiaru w miejscu

MFC w pełni implementuje interfejs zmiany rozmiaru w miejscu, jak opisano w specyfikacji OLE 2. Interfejs użytkownika jest obsługiwany przez `COleResizeBar` klasy, niestandardowy komunikat WM_SIZECHILD i specjalnej obsługi tego komunikatu w `COleIPFrameWnd`.

Można zaimplementować obsługę różnych tego komunikatu, niż dostarczanych przez platformę. Zgodnie z powyższym opisem ramach pozostawia wyniki rozmiaru w miejscu do kontenera — serwer odpowiada, aby zmiana współczynnika powiększenia. Jeśli kontener reaguje, ustawiając zarówno zakres kontenera i pozycja prostokąta podczas przetwarzania jego `COleClientItem::OnChangeItemPosition` (nazywane w wyniku wywołania `COleServerDoc::RequestPositionChange`), a następnie zmiany rozmiaru w miejscu spowoduje wyświetlanie "więcej lub mniej" elementu w edycji okno. Jeśli kontener reaguje, ustawienie pozycja prostokąta tylko podczas przetwarzania `COleClientItem::OnChangeItemPosition`zmieni współczynnika powiększenia i elementu zostaną wyświetlone "element wewnątrz lub na zewnątrz."

Serwer można kontrolować (w pewnym stopniu), co się stanie podczas tej negocjacji. Arkusz kalkulacyjny, na przykład może zdecydować się na Pokaż więcej lub mniej komórek po użytkownik zmienia rozmiar okna podczas edycji elementu w miejscu. Word-processor mogą postanowić zmiany "marginesy strony", dlatego są takie same jak okna i zawijany do nowego marginesu. Serwery implementacji, zmieniając zakres fizycznych (rozmiar zwrócony przez `COleServerItem::OnGetExtent`) po zakończeniu zmiany rozmiaru. Spowoduje to KONTENER, w jakim zmiany przez tę samą wartość, co w tym samym współczynnika powiększenia, ale większe lub mniejsze obszaru wyświetlania i pozycja prostokąta. Ponadto, bardziej lub mniej dokumentu będą widoczne w metaplik generowane przez `OnDraw`. W tym przypadku samego dokumentu ulegnie zmianie, gdy użytkownik zmienia rozmiar elementu, a nie tylko z obszaru wyświetlania.

Można zaimplementować niestandardowy zmiana rozmiaru i w dalszym ciągu używać interfejsu użytkownika dostarczonego przez `COleResizeBar` przez zastąpienie komunikatu WM_SIZECHILD w swojej `COleIPFrameWnd` klasy. Aby uzyskać więcej informacji na temat WM_SIZECHILD, zobacz [techniczne 24 Uwaga](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
