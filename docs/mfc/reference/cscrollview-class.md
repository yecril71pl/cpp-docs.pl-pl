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
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754421"
---
# <a name="cscrollview-class"></a>Klasa CScrollView

Widok [CView](../../mfc/reference/cview-class.md) z możliwościami przewijania.

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
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach urządzenia.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Pobiera bieżący tryb mapowania, całkowity rozmiar oraz rozmiary linii i stron widoku do przewijania. Rozmiary są w jednostkach urządzenia.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach logicznych.|
|[CScrollView::GetTotalSize](#gettotalsize)|Pobiera całkowity rozmiar widoku przewijania w jednostkach logicznych.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Powoduje, że rozmiar widoku, aby dyktować rozmiar jego ramki.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Przewija widok do danego punktu, określonego w jednostkach logicznych.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Przełącza widok przewijania w tryb skalowania do dopasowania.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Ustawia tryb mapowania widoku przewijania, całkowity rozmiar oraz poziomy i pionowy przewijania.|

## <a name="remarks"></a>Uwagi

Można obsługiwać standardowe przewijanie się `CView` w dowolnej klasie pochodzące z przez zastąpienie wiadomości mapowane [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funkcji członkowskich. Ale `CScrollView` dodaje następujące funkcje do swoich `CView` możliwości:

- Zarządza rozmiarami okien i rzutni oraz trybami mapowania.

- Przewijanie jest przewijane automatycznie w odpowiedzi na komunikaty z paskiem przewijania.

- Przewija się automatycznie w odpowiedzi na wiadomości z klawiatury, myszy bez przewijania lub koła IntelliMouse.

Aby przewijać automatycznie w odpowiedzi na wiadomości z klawiatury, dodaj wiadomość WM_KEYDOWN i przetestuj VK_DOWN, VK_PREV i zadzwoń [setscrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Możesz obsługiwać przewijanie kółka myszy samodzielnie, zastępując funkcje członkowskie [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) i [OnRegisteredMouseWheel.](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) Ponieważ są `CScrollView`one dla , te funkcje członkowskie obsługują zalecane zachowanie dla [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), komunikat obrotu koła.

Aby skorzystać z automatycznego przewijania, należy `CScrollView` wyprowadzić `CView`klasę widoku z zamiast od . Po utworzeniu widoku, jeśli chcesz obliczyć rozmiar widoku do przewijania na podstawie `SetScrollSizes` rozmiaru dokumentu, należy wywołać funkcję elementu członkowskiego z zastąpienia [cView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) lub [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Należy napisać własny kod, aby zbadać rozmiar dokumentu. Na przykład zobacz [przykład bazgroły](../../overview/visual-cpp-samples.md).)

Wywołanie funkcji `SetScrollSizes` elementu członkowskiego ustawia tryb mapowania widoku, całkowite wymiary widoku przewijania oraz kwoty do przewijania w poziomie i w pionie. Wszystkie rozmiary są w jednostkach logicznych. Logiczny rozmiar widoku jest zwykle obliczany na podstawie danych przechowywanych w dokumencie, ale w niektórych przypadkach można określić stały rozmiar. Przykłady obu podejść można znaleźć w części [CScrollView::SetScrollSizes](#setscrollsizes).

Należy określić kwoty przewijania w poziomie i w pionie w jednostkach logicznych. Domyślnie, jeśli użytkownik kliknie wałek paska `CScrollView` przewijania poza pole przewijania, przewija "stronę". Jeśli użytkownik kliknie strzałkę przewijania na obu `CScrollView` końcach paska przewijania, przewija "linię". Domyślnie strona to 1/10 całkowitego rozmiaru widoku; wiersz wynosi 1/10 rozmiaru strony. Zastąpozywanie tych wartości domyślnych `SetScrollSizes` przez przekazywanie rozmiarów niestandardowych w funkcji elementu członkowskiego. Na przykład można ustawić rozmiar poziomy na ułamek szerokości całkowitego rozmiaru i rozmiaru pionowego na wysokość linii w bieżącej czcionce.

Zamiast przewijania, `CScrollView` można automatycznie skalować widok do bieżącego rozmiaru okna. W tym trybie widok nie ma pasków przewijania, a widok logiczny jest rozciągnięty lub skurczony, aby dokładnie dopasować obszar klienta okna. Aby użyć tej funkcji skalowania do dopasowania, zadzwoń [do CScrollView::SetScaleToFitSize](#setscaletofitsize). (Zadzwoń albo `SetScaleToFitSize` `SetScrollSizes`lub , ale nie oba.)

Zanim `OnDraw` zostanie wywołana funkcja elementu członkowskiego `CScrollView` klasy widoku pochodnego, automatycznie `CPaintDC` dostosuje początek rzutni `OnDraw`obiektu kontekstu urządzenia, który przechodzi do .

Aby dostosować początek rzutni dla okna `CScrollView` przewijania, zastępuje [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). To dostosowanie jest `CPaintDC` automatyczne dla `CScrollView` kontekstu urządzenia, który przechodzi do `OnDraw`, ale należy wywołać `CScrollView::OnPrepareDC` siebie dla innych kontekstów urządzenia, których używasz, takich jak . `CClientDC` Można zastąpić, `CScrollView::OnPrepareDC` aby ustawić pióro, kolor tła i inne atrybuty rysunku, ale wywołać klasę podstawową, aby wykonać skalowanie.

Paski przewijania mogą pojawiać się w trzech miejscach względem widoku, jak pokazano w następujących przypadkach:

- Standardowe paski przewijania w stylu okna można ustawić dla widoku za pomocą WS_HSCROLL i WS_VSCROLL[style systemu Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Formanty paska przewijania można również dodać do ramki zawierającej widok, w którym to przypadku rama przekazuje WM_HSCROLL i WM_VSCROLL wiadomości z okna ramki do aktualnie aktywnego widoku.

- Struktura również przekazuje wiadomości przewijania z formantu `CSplitterWnd` rozdzielacza do aktualnie aktywnego okienka podziału (widoku). Po umieszczeniu w [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) z `CScrollView` udostępnionych pasków przewijania, obiekt będzie używać udostępnionych, a nie tworzenie własnych.

Aby uzyskać więcej `CScrollView`informacji na temat używania , zobacz [Architektura dokumentu/widoku](../../mfc/document-view-architecture.md) i [Klasy widoku pochodnego dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cview](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy widok przewijania ma poziome i pionowe paski.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Wskazuje, że aplikacja ma poziomy pasek przewijania.

*bVertbar*<br/>
Wskazuje, że aplikacja ma pionowy pasek przewijania.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView

Konstruuje `CScrollView` obiekt.

```
CScrollView();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `SetScrollSizes` albo `SetScaleToFitSize` lub przed widok przewijania jest użyteczny.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Wywołanie, `FillOutsideRect` aby wypełnić obszar widoku, który pojawia się poza obszarem przewijania.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Kontekst urządzenia, w którym wypełnianie ma być wykonane.

*pBrush (pędzel)*<br/>
Szczotka, którą ma być wypełniona.

### <a name="remarks"></a>Uwagi

Użyj `FillOutsideRect` w funkcji `OnEraseBkgnd` obsługi widoku przewijania, aby zapobiec nadmiernemu malowaniu tła.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Nałącz `GetDeviceScrollPosition` połączenie, gdy potrzebujesz bieżących poziomych i pionowych pozycji pól przewijania na paskach przewijania.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Pozycje poziome i pionowe (w jednostkach urządzeń) pól przewijania jako `CPoint` obiekt.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odpowiada lokalizacji w dokumencie, do której przewijano lewy górny róg widoku. Jest to przydatne w przypadku kompensowania pozycji urządzenia myszy w celu przewijania pozycji urządzeń.

`GetDeviceScrollPosition`zwraca wartości w jednostkach urządzenia. Jeśli chcesz jednostek `GetScrollPosition` logicznych, użyj zamiast tego.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`pobiera bieżący tryb mapowania, całkowity rozmiar oraz rozmiary linii i stron widoku z przewijaniem.

```cpp
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*tryb nMapMode*<br/>
Zwraca bieżący tryb mapowania dla tego widoku. Aby uzyskać listę możliwych `SetScrollSizes`wartości, zobacz .

*sizeTotal*<br/>
Zwraca bieżący całkowity rozmiar widoku przewijania w jednostkach urządzenia.

*sizePage*<br/>
Zwraca bieżące poziomye i pionowe kwoty do przewijania w każdym kierunku w odpowiedzi na kliknięcie myszą na wale paska przewijania. Element `cx` członkowski zawiera kwotę poziomą. Element `cy` członkowski zawiera kwotę pionową.

*sizeLine (linia)*<br/>
Zwraca bieżące poziomy i pionowe kwoty do przewijania w każdym kierunku w odpowiedzi na kliknięcie myszą w strzałce przewijania. Element `cx` członkowski zawiera kwotę poziomą. Element `cy` członkowski zawiera kwotę pionową.

### <a name="remarks"></a>Uwagi

Rozmiary są w jednostkach urządzenia. Ta funkcja elementu członkowskiego jest rzadko wywoływana.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition

Nałącz `GetScrollPosition` połączenie, gdy potrzebujesz bieżących poziomych i pionowych pozycji pól przewijania na paskach przewijania.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Położenie poziome i pionowe (w jednostkach logicznych) pól przewijania jako `CPoint` obiektu.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odpowiada lokalizacji w dokumencie, do której przewijano lewy górny róg widoku.

`GetScrollPosition`zwraca wartości w jednostkach logicznych. Jeśli chcesz jednostek `GetDeviceScrollPosition` urządzenia, użyj zamiast tego.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize

Wywołanie, `GetTotalSize` aby pobrać bieżące poziome i pionowe rozmiary widoku przewijania.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Całkowity rozmiar widoku przewijania w jednostkach logicznych. Rozmiar poziomy znajduje `cx` się w `CSize` człońwcu zwracanej wartości. Rozmiar pionowy znajduje `cy` się w człowiu.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit

Wywołanie, `ResizeParentToFit` aby rozmiar widoku dyktował rozmiar okna ramki.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Rodzaj zmiany rozmiaru do wykonania. Wartość domyślna, PRAWDA, zmniejsza okno ramki, jeśli to konieczne. Paski przewijania będą nadal wyświetlane dla dużych widoków lub małych okien ramek. Wartość FALSE powoduje, że widok zawsze do rozmiaru okna ramki dokładnie. Może to być nieco niebezpieczne, ponieważ okno ramki może stać się zbyt duże, aby zmieścić się w oknie ramki interfejsu wielu dokumentów (MDI) lub na ekranie.

### <a name="remarks"></a>Uwagi

Jest to zalecane tylko w przypadku widoków w oknach ramki podrzędnej MDI. Użyj `ResizeParentToFit` w `OnInitialUpdate` funkcji obsługi `CScrollView` klasy pochodnej. Na przykład tej funkcji elementu członkowskiego zobacz [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`zakłada, że rozmiar okna widoku został ustawiony. Jeśli rozmiar okna widoku nie `ResizeParentToFit` został ustawiony, gdy jest wywoływana, otrzymasz asercja. Aby upewnić się, że tak się `ResizeParentToFit`nie stanie, przed wywołaniem zadzwoń podyp.

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Wywołanie, `ScrollToPosition` aby przewinąć do danego punktu w widoku.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Punkt do przewijania w jednostkach logicznych. Element `x` członkowski musi być wartością dodatnią (większą lub równą 0, do całkowitego rozmiaru widoku). To samo dotyczy `y` elementu członkowskiego, gdy tryb mapowania jest MM_TEXT. Element `y` członkowski jest ujemny w trybach mapowania innych niż MM_TEXT.

### <a name="remarks"></a>Uwagi

Widok zostanie przewinięty tak, aby ten punkt znajduje się w lewym górnym rogu okna. Ta funkcja elementu członkowskiego nie może być wywoływana, jeśli widok jest skalowany w celu dopasowania.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Zadzwoń, `SetScaleToFitSize` jeśli chcesz automatycznie skalować rozmiar rzutni do bieżącego rozmiaru okna.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Rozmiary poziome i pionowe, do których ma być skalowany widok. Rozmiar widoku przewijania jest mierzony w jednostkach logicznych. Rozmiar poziomy znajduje się `cx` w człówka. Rozmiar pionowy znajduje się `cy` w człowiu. Oba `cx` `cy` i muszą być większe lub równe 0.

### <a name="remarks"></a>Uwagi

W przypadku pasków przewijania tylko część widoku logicznego może być widoczna w dowolnym momencie. Ale dzięki możliwości skalowania do dopasowania widok nie ma pasków przewijania, a widok logiczny jest rozciągnięty lub skurczony, aby dokładnie dopasować obszar klienta okna. Po przeskalowaniu okna widok rysuje swoje dane w nowej skali na podstawie rozmiaru okna.

Zazwyczaj można umieścić wywołanie `SetScaleToFitSize` w przesłone funkcji `OnInitialUpdate` elementu członkowskiego widoku. Jeśli nie chcesz skalowania automatycznego, zamiast tego należy wywołać `SetScrollSizes` funkcję elementu członkowskiego.

`SetScaleToFitSize`może służyć do implementacji operacji "Zoom to Fit". Służy `SetScrollSizes` do ponownego inicjowania przewijania.

`SetScaleToFitSize`zakłada, że rozmiar okna widoku został ustawiony. Jeśli rozmiar okna widoku nie `SetScaleToFitSize` został ustawiony, gdy jest wywoływana, otrzymasz asercja. Aby upewnić się, że tak się `SetScaleToFitSize`nie stanie, przed wywołaniem zadzwoń podyp.

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Zadzwoń, `SetScrollSizes` gdy widok ma zostać zaktualizowany.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*tryb nMapMode*<br/>
Tryb mapowania, aby ustawić dla tego widoku. Możliwe wartości to:

|Tryb mapowania|Jednostka logiczna|Dodatnia oś y rozszerza...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 piksel|Dół|
|MM_HIMETRIC|0,01 mm|Górę|
|MM_TWIPS|1/1440 w|Górę|
|MM_HIENGLISH|0,001 w|Górę|
|MM_LOMETRIC|0,1 mm|Górę|
|MM_LOENGLISH|0,01 w|Górę|

Wszystkie te tryby są definiowane przez system Windows. Dwa standardowe tryby mapowania, MM_ISOTROPIC i MM_ANISOTROPIC, nie `CScrollView`są używane dla . Biblioteka klas `SetScaleToFitSize` udostępnia funkcję elementu członkowskiego do skalowania widoku do rozmiaru okna. Kolumna trzecia w powyższej tabeli opisuje orientację współrzędnych.

*sizeTotal*<br/>
Całkowity rozmiar widoku przewijania. Element `cx` członkowski zawiera zakres poziomy. Element `cy` członkowski zawiera zakres pionowy. Rozmiary są w jednostkach logicznych. Oba `cx` `cy` i muszą być większe lub równe 0.

*sizePage*<br/>
Poziome i pionowe kwoty przewijania w każdym kierunku w odpowiedzi na kliknięcie myszą w wału paska przewijania. Element `cx` członkowski zawiera kwotę poziomą. Element `cy` członkowski zawiera kwotę pionową.

*sizeLine (linia)*<br/>
Poziome i pionowe kwoty przewijania w każdym kierunku w odpowiedzi na kliknięcie myszą w strzałce przewijania. Element `cx` członkowski zawiera kwotę poziomą. Element `cy` członkowski zawiera kwotę pionową.

### <a name="remarks"></a>Uwagi

Wywołaj go w zastąpieniu `OnUpdate` funkcji elementu członkowskiego, aby dostosować właściwości przewijania, gdy na przykład dokument jest początkowo wyświetlany lub gdy zmienia rozmiar.

Zazwyczaj informacje o rozmiarze można uzyskać z skojarzonego z danym dokumencie `GetMyDocSize`widoku, wywołując funkcję elementu członkowskiego dokumentu, być może wywołaną, która jest dostarczana z klasą dokumentu pochodnego. Poniższy kod przedstawia następujące podejście:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Alternatywnie czasami może być konieczne ustawienie stałego rozmiaru, jak w poniższym kodzie:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Należy ustawić tryb mapowania na dowolny z trybów mapowania systemu Windows z wyjątkiem MM_ISOTROPIC lub MM_ANISOTROPIC. Jeśli chcesz użyć trybu mapowania bez ograniczeń, `SetScaleToFitSize` należy wywołać `SetScrollSizes`funkcję elementu członkowskiego zamiast programu .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy DIBLOOK MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
