---
title: Klasa CScrollView
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: b89daaae4bb578d328e1468cc29470825e19c670
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502591"
---
# <a name="cscrollview-class"></a>Klasa CScrollView

[CView](../../mfc/reference/cview-class.md) z możliwościami przewijania.

## <a name="syntax"></a>Składnia

```
class CScrollView : public CView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Konstruuje `CScrollView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Wskazuje, czy widok przewijania ma poziome i pionowe paski przewijania.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Wypełnia obszar widoku poza obszarem przewijania.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach urządzeń.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Pobiera bieżący tryb mapowania, łączny rozmiar oraz rozmiary wierszy i stron widoku przewijania. Rozmiary są w jednostkach urządzeń.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach logicznych.|
|[CScrollView:: GetTotalSize](#gettotalsize)|Pobiera łączny rozmiar widoku przewijania w jednostkach logicznych.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Powoduje, że rozmiar widoku jest podyktowany rozmiarem jego ramki.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Przewija widok do danego punktu, który jest określony w jednostkach logicznych.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Umieszcza Widok przewijania w trybie skalowania do-dopasowanie.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Ustawia tryb mapowania widoku przewijania, łączny rozmiar i poziome i pionowe ilości przewijania.|

## <a name="remarks"></a>Uwagi

Możesz obsłużyć przewijanie standardowe samodzielnie w dowolnej klasie `CView` pochodnej przez zastępowanie funkcji Członkowskich mapowanych [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) . Dodaje do swoich `CView` możliwości następujące funkcje: `CScrollView`

- Zarządza rozmiar okna i okienka ekranu oraz tryby mapowania.

- Jest ono automatycznie przewijane w odpowiedzi na komunikaty paska przewijania.

- Automatycznie przewija w odpowiedzi na komunikaty z klawiatury, myszy, która nie jest przewijana lub kółkiem myszy.

Aby przewijać automatycznie w odpowiedzi na komunikaty z klawiatury, Dodaj komunikat PRZETŁUMACZYŁA i przetestuj VK_DOWN, VK_PREV i Call [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Możesz obsłużyć przewijanie kółka myszy samodzielnie przez zastępowanie funkcji Członkowskich mapowanych [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) i [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) . Jak są dla `CScrollView`, te funkcje składowe obsługują zalecane zachowanie dla [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), komunikat obrotu kółkiem.

Aby skorzystać z automatycznego przewijania, Utwórz klasę widoku od `CScrollView` zamiast z. `CView` Gdy widok jest tworzony po raz pierwszy, jeśli chcesz obliczyć rozmiar widoku przewijalnego na podstawie rozmiaru dokumentu, wywołaj `SetScrollSizes` funkcję członkowską z przesłonięcia którejkolwiek z [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) lub [CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Musisz napisać własny kod, aby zbadać rozmiar dokumentu. Aby zapoznać się z przykładem, zobacz [przykładowy Bazgroły](../../overview/visual-cpp-samples.md).)

Wywołanie do `SetScrollSizes` funkcji składowej ustawia tryb mapowania widoku, łączne wymiary widoku przewijania i ilości, które mają być przewijane w poziomie i w pionie. Wszystkie rozmiary są w jednostkach logicznych. Rozmiar logiczny widoku jest zwykle obliczany na podstawie danych przechowywanych w dokumencie, ale w niektórych przypadkach może być konieczne określenie stałego rozmiaru. Aby zapoznać się z przykładami obu metod, zobacz [CScrollView:: SetScrollSizes](#setscrollsizes).

Należy określić kwoty do przewijania w poziomie i w pionie w jednostkach logicznych. Domyślnie, jeśli użytkownik kliknie wału paska przewijania poza polem przewijania, `CScrollView` przewija "stronę". Jeśli użytkownik kliknie strzałkę przewijania na dowolnym końcu paska przewijania, `CScrollView` przewija "wiersz". Domyślnie strona jest 1/10 o całkowitym rozmiarze widoku; wiersz jest 1/10 rozmiaru strony. Przesłoń te wartości domyślne, przekazując niestandardowe rozmiary w `SetScrollSizes` funkcji składowej. Można na przykład ustawić rozmiar w poziomie na część szerokości całkowitego rozmiaru i rozmiar pionowy na wysokość wiersza w bieżącej czcionce.

Zamiast przewijania, program `CScrollView` może automatycznie skalować widok do bieżącego rozmiaru okna. W tym trybie widok nie ma pasków przewijania i Widok logiczny jest rozciągany lub zmniejszany w celu dokładnego dopasowania obszaru klienta okna. Aby skorzystać z tej możliwości skalowania do rozmiaru, wywołaj [CScrollView:: SetScaleToFitSize](#setscaletofitsize). (Wywołaj `SetScaleToFitSize` albo `SetScrollSizes`, ale nie oba.)

Przed wywołaniem funkcji `CScrollView` `CPaintDC` `OnDraw`członkowskiej klasy widoku pochodnego program automatycznie dostosowuje pochodzenie okienka ekranu dla obiektu kontekstu urządzenia, do którego przekazuje. `OnDraw`

Aby dostosować Źródło okienka ekranu dla okna przewijania, `CScrollView` zastępuje [CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Ta korekta jest automatycznie stosowana `CPaintDC` dla kontekstu urządzenia `CScrollView` , który `OnDraw`przekazuje do, ale należy `CScrollView::OnPrepareDC` wywołać siebie `CClientDC`dla wszystkich innych kontekstów urządzeń, takich jak. Możesz przesłonić `CScrollView::OnPrepareDC` , aby ustawić pióro, kolor tła i inne atrybuty rysowania, ale Wywołaj klasę bazową, aby przeprowadzić skalowanie.

Paski przewijania mogą pojawić się w trzech miejscach względem widoku, jak pokazano w następujących przypadkach:

- Standardowe paski przewijania stylu okna można ustawić dla widoku przy użyciu[stylów systemu Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles)WS_HSCROLL i WS_VSCROLL.

- Kontrolki paska przewijania można także dodawać do ramki zawierającej widok. w takim przypadku struktura przekazuje komunikaty WM_HSCROLL i WM_VSCROLL z okna ramka do aktualnie aktywnego widoku.

- Struktura przekazuje także komunikaty przewijania z `CSplitterWnd` kontrolki rozdzielacza do aktualnie aktywnego okienka rozdzielacza (widok). Gdy umieszczasz w [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) z udostępnionymi paskami przewijania `CScrollView` , obiekt będzie korzystał z nich zamiast tworzyć własne.

Aby uzyskać więcej informacji na `CScrollView`temat korzystania z programu, zobacz temat [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md) i [pochodne klasy widoków dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy widok przewijania ma poziomy i pionowy pasek.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Oznacza, że aplikacja ma poziomy pasek przewijania.

*bHasVertBar*<br/>
Oznacza, że aplikacja ma pionowy pasek przewijania.

##  <a name="cscrollview"></a>CScrollView::CScrollView

Konstruuje `CScrollView` obiekt.

```
CScrollView();
```

### <a name="remarks"></a>Uwagi

Aby można było użyć `SetScrollSizes` widoku `SetScaleToFitSize` przewijania, należy wywołać opcję lub.

##  <a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Wywołaj `FillOutsideRect` , aby wypełnić obszar widoku, który pojawia się poza obszarem przewijania.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Kontekst urządzenia, w którym ma zostać wykonane wypełnienie.

*pBrush*<br/>
Pędzel, za pomocą którego obszar ma zostać wypełniony.

### <a name="remarks"></a>Uwagi

Użyj `FillOutsideRect` w funkcji `OnEraseBkgnd` obsługi widoku przewijania, aby zapobiec nadmiernemu odświeżeniu w tle.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Wywołuje `GetDeviceScrollPosition` się, gdy potrzebne są bieżące położenie w poziomie i w pionie pól przewijania na paskach przewijania.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Położenie w poziomie i w pionie (w jednostkach urządzeń) pól przewijania jako `CPoint` obiekt.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odpowiada lokalizacji w dokumencie, do której lewy górny róg widoku został przewinięty. Jest to przydatne w przypadku rozliczania pozycji myszy i urządzenia w celu przewijania widoku pozycji urządzenia.

`GetDeviceScrollPosition`zwraca wartości w jednostkach urządzeń. Jeśli chcesz, aby jednostki logiczne były `GetScrollPosition` używane w zamian.

##  <a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`Pobiera bieżący tryb mapowania, łączny rozmiar oraz rozmiary wierszy i stron widoku przewijania.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Zwraca bieżący tryb mapowania dla tego widoku. Listę możliwych wartości można znaleźć w temacie `SetScrollSizes`.

*sizeTotal*<br/>
Zwraca bieżący łączny rozmiar widoku przewijania w jednostkach urządzeń.

*sizePage*<br/>
Zwraca bieżące wartości w poziomie i pionie, aby przewijać w każdym kierunku w odpowiedzi na kliknięcie myszy w wałku paska przewijania. `cx` Element członkowski zawiera wielkość poziomą. `cy` Element członkowski zawiera kwotę pionową.

*sizeLine*<br/>
Zwraca bieżące poziomy i pionowe ilości, które mają być przewijane w każdym kierunku w odpowiedzi na kliknięcie myszy w strzałce przewijania. `cx` Element członkowski zawiera wielkość poziomą. `cy` Element członkowski zawiera kwotę pionową.

### <a name="remarks"></a>Uwagi

Rozmiary są w jednostkach urządzeń. Ta funkcja członkowska jest rzadko wywoływana.

##  <a name="getscrollposition"></a>CScrollView::GetScrollPosition

Wywołuje `GetScrollPosition` się, gdy potrzebne są bieżące położenie w poziomie i w pionie pól przewijania na paskach przewijania.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Położenie w poziomie i w pionie (w jednostkach logicznych) pól przewijania jako `CPoint` obiekt.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odpowiada lokalizacji w dokumencie, do której lewy górny róg widoku został przewinięty.

`GetScrollPosition`zwraca wartości w jednostkach logicznych. Jeśli chcesz, aby jednostki urządzenia używały `GetDeviceScrollPosition` tego programu.

##  <a name="gettotalsize"></a>CScrollView:: GetTotalSize

Wywołaj `GetTotalSize` , aby pobrać bieżące rozmiary w poziomie i w pionie widoku przewijania.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Łączny rozmiar widoku przewijania w jednostkach logicznych. Rozmiar poziomy znajduje się w `cx` elemencie członkowskim `CSize` wartości zwracanej. Rozmiar w pionie znajduje się `cy` w elemencie członkowskim.

##  <a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit

Wywołaj `ResizeParentToFit` , aby umożliwić rozmiarowi widoku dyktowanie rozmiaru okna ramki.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Rodzaj zmiany, które należy wykonać. Wartość domyślna to TRUE, w razie potrzeby zmniejsza okno ramki. Paski przewijania będą nadal wyświetlane dla dużych widoków lub małych okien ramowych. Wartość FALSE powoduje, że widok zawsze zmienia rozmiar okna ramki. Może to być nieco niebezpieczne, ponieważ okno ramki może być zbyt duże, aby zmieściło się w oknie ramki interfejsu wielu dokumentów (MDI) lub na ekranie.

### <a name="remarks"></a>Uwagi

Jest to zalecane tylko w przypadku widoków w podrzędnych oknach ramek MDI. Użyj `ResizeParentToFit` `CScrollView` w funkcji obsługi klasy pochodnej. `OnInitialUpdate` Aby zapoznać się z przykładem tej funkcji członkowskiej, zobacz [CScrollView:: SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`przyjęto założenie, że rozmiar okna widoku został ustawiony. Jeśli nie ustawiono rozmiaru okna widoku, gdy `ResizeParentToFit` jest wywoływana, otrzymasz potwierdzenie. Aby upewnić się, że to nie nastąpiło, przed wywołaniem `ResizeParentToFit`należy wykonać następujące wywołanie:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Wywołanie `ScrollToPosition` przewijania do danego punktu w widoku.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Punkt do przewijania w jednostkach logicznych. `x` Element członkowski musi być wartością dodatnią (większą lub równą 0, aż do całkowitego rozmiaru widoku). Ta sama wartość jest prawdziwa dla `y` elementu członkowskiego, gdy tryb mapowania to MM_TEXT. `y` Składowa jest ujemna w trybach mapowania innych niż MM_TEXT.

### <a name="remarks"></a>Uwagi

Widok zostanie przewinięty, aby ten punkt znajdował się w lewym górnym rogu okna. Ta funkcja członkowska nie może być wywoływana, jeśli widok jest skalowany do dopasowania.

##  <a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Wywołaj `SetScaleToFitSize` , gdy chcesz automatycznie skalować rozmiar okienka ekranu do bieżącego rozmiaru okna.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Rozmiary w poziomie i w pionie, do których widok ma być skalowany. Rozmiar widoku przewijania jest mierzony w jednostkach logicznych. Rozmiar w poziomie jest zawarty w `cx` elemencie członkowskim. Rozmiar w pionie jest zawarty w `cy` elemencie członkowskim. Oba `cx` i`cy` muszą być większe lub równe 0.

### <a name="remarks"></a>Uwagi

Przy użyciu pasków przewijania tylko część widoku logicznego może być widoczna w dowolnym momencie. Ale z możliwością skalowania do rozmiaru widok nie ma pasków przewijania, a Widok logiczny jest rozciągany lub zmniejszany, aby dokładnie dopasować obszar klienta okna. Po zmianie rozmiaru okna widok rysuje jego dane w nowej skali na podstawie rozmiaru okna.

Zwykle nastąpi wywołanie `SetScaleToFitSize` w przesłonięciu funkcji `OnInitialUpdate` składowej widoku. Jeśli nie chcesz używać automatycznego skalowania, wywołaj `SetScrollSizes` funkcję elementu członkowskiego.

`SetScaleToFitSize`może służyć do implementowania operacji "Powiększ do dopasowania". Użyj `SetScrollSizes` , aby ponownie zainicjować przewijanie.

`SetScaleToFitSize`przyjęto założenie, że rozmiar okna widoku został ustawiony. Jeśli nie ustawiono rozmiaru okna widoku, gdy `SetScaleToFitSize` jest wywoływana, otrzymasz potwierdzenie. Aby upewnić się, że to nie nastąpiło, przed wywołaniem `SetScaleToFitSize`należy wykonać następujące wywołanie:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Wywołaj `SetScrollSizes` , gdy widok ma zostać zaktualizowany.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Tryb mapowania do ustawienia dla tego widoku. Możliwe wartości obejmują:

|Tryb mapowania|Jednostka logiczna|Dodatnia oś y rozciąga się...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 piksel|Ciągnięcie|
|MM_HIMETRIC|0,01 mm|Więcej|
|MM_TWIPS|1/1440 w|Więcej|
|MM_HIENGLISH|0,001 w|Więcej|
|MM_LOMETRIC|0,1 mm|Więcej|
|MM_LOENGLISH|0,01 w|Więcej|

Wszystkie te tryby są definiowane przez system Windows. Dwa standardowe tryby mapowania, MM_ISOTROPIC i MM_ANISOTROPIC, nie są używane w `CScrollView`programie. Biblioteka klas udostępnia `SetScaleToFitSize` funkcję członkowską do skalowania widoku do rozmiaru okna. W kolumnie trzy w powyższej tabeli opisano orientację współrzędnych.

*sizeTotal*<br/>
Łączny rozmiar widoku przewijania. `cx` Element członkowski zawiera poziomy. `cy` Element członkowski zawiera zakres w pionie. Rozmiary są w jednostkach logicznych. Oba `cx` i`cy` muszą być większe lub równe 0.

*sizePage*<br/>
Ilości w poziomie i pionie, które mają być przewijane w każdym kierunku w odpowiedzi na kliknięcie myszą w wałku paska przewijania. `cx` Element członkowski zawiera wielkość poziomą. `cy` Element członkowski zawiera kwotę pionową.

*sizeLine*<br/>
Ilości w poziomie i pionie, które mają być przewijane w każdym kierunku w odpowiedzi na kliknięcie myszy w strzałce przewijania. `cx` Element członkowski zawiera wielkość poziomą. `cy` Element członkowski zawiera kwotę pionową.

### <a name="remarks"></a>Uwagi

Wywołaj je w przesłonięciu `OnUpdate` funkcji składowej, aby dostosować właściwości przewijania, gdy na przykład dokument jest początkowo wyświetlany lub zmienia rozmiar.

Informacje o rozmiarze są zazwyczaj uzyskiwane ze skojarzonego dokumentu widoku przez wywołanie funkcji składowej dokumentu, która może zostać `GetMyDocSize`wywołana, z klasy dokumentu pochodnego. Poniższy kod przedstawia takie podejście:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Czasami może być konieczne ustawienie stałego rozmiaru, tak jak w poniższym kodzie:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Należy ustawić tryb mapowania na dowolny tryb mapowania systemu Windows, z wyjątkiem MM_ISOTROPIC lub MM_ANISOTROPIC. Jeśli chcesz użyć trybu mapowania nieograniczonego, wywołaj `SetScaleToFitSize` funkcję członkowską `SetScrollSizes`zamiast.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
