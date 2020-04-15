---
title: 'TN040: Zmiana rozmiaru i powiększania MFC-OLE w miejscu'
ms.date: 11/04/2016
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: 65f9ef04c9740e8e6f0a8e72d9d6c39008198755
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372164"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: MFC/OLE — zmienianie rozmiaru i powiększanie w miejscu

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce omówiono kwestie związane z edycją w miejscu oraz sposób, w jaki serwer powinien dokonać prawidłowego powiększania i zmiany rozmiaru w miejscu. Dzięki aktywacji w miejscu koncepcja WYSIWYG jest o krok dalej, ponieważ kontenery i serwery współpracują ze sobą, a w szczególności interpretują specyfikację OLE w taki sam sposób.

Ze względu na ścisłą interakcję między kontenerem a serwerem obsługującym aktywację w miejscu istnieje szereg oczekiwań od użytkownika końcowego, które powinny być utrzymywane:

- Wyświetlacz prezentacji (metaplik narysowany `COleServerItem::OnDraw` w zastąpieniu) powinien wyglądać dokładnie tak samo, jak wtedy, gdy jest rysowany do edycji (z tą różnicą, że narzędzia do edycji nie są widoczne).

- Gdy kontener powiększa, okno serwera powinno też!

- Kontener i serwer powinny wyświetlać obiekty do edycji przy użyciu tych samych metryk. Oznacza to użycie trybu mapowania opartego na liczbie pikseli *logicznych* na cal — nie fizycznych pikseli na cal podczas renderowania na urządzeniu wyświetlającym.

> [!NOTE]
> Ponieważ aktywacja w miejscu dotyczy tylko elementów, które są osadzone (nie połączone), powiększanie dotyczy tylko obiektów osadzonych. Zostaną wyświetlenia interfejsów `COleServerDoc` API `COleServerItem` w obu i które są używane do powiększania. Powodem tej dychotomii jest to, że tylko funkcje, `COleServerItem` które są prawidłowe zarówno dla elementów połączonych i osadzonych są `COleServerDoc` w (pozwala to na wspólną implementację) i funkcje, które są prawidłowe tylko dla obiektów osadzonych znajdują się w klasie (z punktu widzenia serwera, jest to **dokument,** który jest osadzony).

Większość obciążenia jest nakładana na realizatora serwera, ponieważ serwer musi być świadomy współczynnika powiększenia kontenera i odpowiednio zmodyfikować jego interfejs edycji. Ale w jaki sposób serwer określa współczynnik powiększenia, z jakiego korzysta kontener

## <a name="mfc-support-for-zooming"></a>Obsługa MFC dla powiększania

Bieżący współczynnik powiększenia można określić przez wywołanie `COleServerDoc::GetZoomFactor`. Wywołanie tego, gdy dokument nie jest aktywny w miejscu zawsze spowoduje współczynnik powiększenia 100% (lub stosunek 1:1). Wywołanie go w miejscu aktywnym może zwrócić coś innego niż 100%.

Na przykład powiększania poprawnie zobacz MFC OLE próbki [HIERSVR](../overview/visual-cpp-samples.md). Powiększanie HIERSVR komplikuje fakt, że wyświetla tekst, a tekst, ogólnie rzecz biorąc, nie skaluje się w sposób liniowy (wskazówki, konwencje typograficzne, szerokości projektu i wysokości komplikują sprawę). Mimo to, HIERSVR jest rozsądnym odniesieniem do prawidłowego wdrażania powiększania, podobnie jak MFC Tutorial [SCRIBBLE](../overview/visual-cpp-samples.md) (krok 7).

`COleServerDoc::GetZoomFactor`określa współczynnik powiększenia na podstawie wielu różnych metryk dostępnych z `COleServerItem` kontenera lub z implementacji i `COleServerDoc` klas. Krótko mówiąc, bieżący współczynnik powiększenia jest określany przez następującą formułę:

```
Position Rectangle (PR) / Container Extent (CE)
```

Położenie PROSTOKĄT jest określany przez pojemnik. Jest zwracany do serwera podczas aktywacji w miejscu, gdy `COleClientItem::OnGetItemPosition` jest wywoływana `COleServerDoc::OnSetItemRects` i jest `COleClientItem::SetItemRects`aktualizowany, gdy kontener wywołuje serwer (z wywołaniem ).

Zakres kontenera jest nieco bardziej złożony do obliczenia. Jeśli kontener został `COleServerItem::OnSetExtent` wywołany (z wywołaniem do), `COleClientItem::SetExtent`a następnie zakres kontenera jest ta wartość konwertowana na piksele na podstawie liczby pikseli na cal logiczny. Jeśli kontener nie wywołał SetExtent (co zwykle ma miejsce), a następnie `COleServerItem::OnGetExtent`zakres kontenera jest rozmiar zwrócony z . Tak więc, jeśli kontener nie ma nazwy SetExtent, struktura zakłada, że jeśli nie kontener nazwałby go z 100% naturalnego zasięgu (wartość zwrócona z `COleServerItem::GetExtent`). W inny sposób struktura zakłada, że kontener wyświetla 100% (nie więcej, nie mniej) elementu.

Należy pamiętać, że `COleServerItem::OnSetExtent` chociaż `COleServerItem::OnGetExtent` i mają podobne nazwy, nie manipulują tym samym atrybutem elementu. `OnSetExtent`jest wywoływana, aby poinformować serwer, ile obiektu jest widoczny w kontenerze `OnGetExtent` (niezależnie od współczynnika powiększenia) i jest wywoływana przez kontener, aby określić idealny rozmiar obiektu.

Patrząc na każdy z interfejsów API zaangażowanych, można uzyskać jaśniejszy obraz:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Ta funkcja powinna zwracać "rozmiar naturalny" w jednostkach HIMETRIC towaru. Najlepszym sposobem, aby myśleć o "rozmiar naturalny" jest zdefiniowanie go jako rozmiar może pojawić się po wydrukowaniu. Rozmiar zwrócony w tym miejscu jest stały dla określonej zawartości elementu (podobnie jak metaplik, który jest stały dla określonego elementu). Ten rozmiar nie zmienia się po zastosowaniu powiększania do elementu. Zwykle nie zmienia się, gdy kontener daje elementowi `OnSetExtent`więcej lub mniej miejsca, wywołując . Przykładem zmiany może być prosty edytor tekstu bez możliwości "margines", który zawinął tekst na podstawie ostatniego zakresu wysyłanego przez kontener. Jeśli serwer się zmieni, serwer powinien prawdopodobnie ustawić bit OLEMISC_RECOMPOSEONRESIZE w rejestrze systemowym (więcej informacji na temat tej opcji można znaleźć w dokumentacji zestawu SDK OLE).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Ta funkcja jest wywoływana, gdy kontener pokazuje "mniej lub bardziej" obiektu. Większość kontenerów w ogóle tego nie wywoła. Domyślna implementacja przechowuje ostatnią wartość otrzymaną z kontenera w `COleServerDoc::GetZoomFactor` "m_sizeExtent", który jest używany podczas obliczania wartości ZAKRESU KONTENERa opisane powyżej.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Ta funkcja jest wywoływana tylko wtedy, gdy dokument jest aktywny w miejscu. Jest wywoływana, gdy kontener aktualizuje położenie elementu lub przycinanie zastosowane do elementu. Położenie PROSTOKĄT, jak wspomniano powyżej, zapewnia licznik obliczania współczynnika powiększenia. Serwer może zażądać zmiany pozycji elementu `COleServerDoc::RequestPositionChange`przez wywołanie . Kontener może lub nie może odpowiedzieć `OnSetItemRects` na to `COleServerItem::SetItemRects`żądanie, dzwoniąc (z wywołaniem ).

## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw

Ważne jest, aby zdać sobie sprawę, że `COleServerItem::OnDraw` metaplik utworzony przez zastąpienie produkuje dokładnie ten sam metaplik, niezależnie od bieżącego współczynnika powiększenia. Kontener będzie skalować metaplik odpowiednio. Jest to ważne rozróżnienie między `OnDraw` widokiem a elementem serwera `OnDraw`. Widok obsługuje powiększanie, element po prostu tworzy *powiększalny* metaplik i pozostawia go do kontenera, aby wykonać odpowiednie powiększanie.

Najlepszym sposobem, aby zapewnić, że serwer zachowuje się poprawnie `COleServerDoc::GetZoomFactor` jest użycie implementacji, jeśli dokument jest aktywny w miejscu.

## <a name="mfc-support-for-in-place-resizing"></a>Obsługa MFC dla zmiany rozmiaru w miejscu

MFC w pełni implementuje interfejs zmiany rozmiaru w miejscu, zgodnie z opisem w specyfikacji OLE 2. Interfejs użytkownika jest obsługiwany przez `COleResizeBar` klasę, niestandardowy komunikat WM_SIZECHILD i specjalną obsługę `COleIPFrameWnd`tego komunikatu w .

Można zaimplementować inną obsługę tego komunikatu niż to, co jest dostarczane przez strukturę. Jak opisano powyżej, struktura pozostawia wyniki zmiany rozmiaru w miejscu do kontenera — serwer reaguje na zmianę współczynnika powiększenia. Jeśli kontener reaguje przez ustawienie zarówno ROZMIAR KONTENERa i POŁOŻENIE `COleClientItem::OnChangeItemPosition` PROSTOKĄT podczas przetwarzania jego (wywoływane w wyniku wywołania do), `COleServerDoc::RequestPositionChange`a następnie w miejscu zmiany rozmiaru spowoduje pokazano "mniej lub bardziej" elementu w oknie edycji. Jeśli kontener reaguje, ustawiając pozycjonowanie PROSTOKĄTa podczas `COleClientItem::OnChangeItemPosition`przetwarzania, współczynnik powiększenia ulegnie zmianie, a element zostanie wyświetlony "powiększony lub pomniejszy."

Serwer może kontrolować (do pewnego stopnia), co dzieje się podczas tych negocjacji. Arkusz kalkulacyjny, na przykład, może zdecydować się na wyświetlanie większej liczby lub mniejszej liczby komórek, gdy użytkownik zmienić rozmiar okna podczas edytowania elementu w miejscu. Edytor tekstu może zdecydować się na zmianę "marginesów strony", tak aby były takie same jak okno i ponownie zaakrwać tekst na nowy margines. Serwery implementują to, zmieniając naturalny `COleServerItem::OnGetExtent`zasięg (rozmiar zwrócony z) po zakończeniu zmiany rozmiaru. Spowoduje to, że zarówno położenie prostokąta i zakres kontenera, aby zmienić o tę samą kwotę, w wyniku tego samego współczynnika powiększenia, ale większy lub mniejszy obszar wyświetlania. Ponadto mniej więcej dokumentu będzie widoczny w metapliku generowanym przez `OnDraw`program . W takim przypadku sam dokument zmienia się, gdy użytkownik zmienia rozmiar elementu, a nie tylko obszar wyświetlania.

Można zaimplementować niestandardowe zmiany rozmiaru `COleResizeBar` i nadal korzystać z interfejsu użytkownika `COleIPFrameWnd` dostarczonego przez zastąpienie WM_SIZECHILD komunikat w klasie. Aby uzyskać więcej informacji na temat specyfiki WM_SIZECHILD, zobacz [Uwaga techniczna 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
