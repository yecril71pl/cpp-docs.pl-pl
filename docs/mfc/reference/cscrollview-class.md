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
ms.openlocfilehash: d60082092bd42fbe220eee08953ad5fda0ff0a85
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339585"
---
# <a name="cscrollview-class"></a>Klasa CScrollView

A [CView](../../mfc/reference/cview-class.md) z możliwościami przewijania.

## <a name="syntax"></a>Składnia

```
class CScrollView : public CView
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Konstruuje `CScrollView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Wskazuje, czy widok przewijania, ma poziome i pionowe paski przewijania.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Wypełnia obszar poza obszarem przewijania widoku.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach urządzenia.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Pobiera bieżący tryb mapowania, całkowity rozmiar i rozmiary wiersza i strony przewijany widoku. Rozmiary są w jednostkach urządzenia.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Pobiera bieżącą pozycję przewijania w jednostkach logicznych.|
|[CScrollView::GetTotalSize](#gettotalsize)|Pobiera całkowity rozmiar widoku przewijania w jednostkach logicznych.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Powoduje, że rozmiar widoku dyktowania rozmiar ramki.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Przewija widok do danego punktu, określonego w jednostkach logicznych.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Umieszcza widok przewijania z trybu skalowania do dopasowania.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Ustawia tryb mapowania widoku przewijania, całkowity rozmiar i poziome i pionowe przewijanie kwoty.|

## <a name="remarks"></a>Uwagi

Może obsługiwać standard przewijanie samodzielnie w dowolnej klasie pochodnej `CView` przez zastąpienie mapowanych komunikat [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) i [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funkcji elementów członkowskich. Ale `CScrollView` dodaje następujące funkcje, aby jego `CView` możliwości:

- Zarządza tryby mapowania i rozmiary okna i okienka ekranu.

- Automatycznie przewija w odpowiedzi na komunikaty paska przewijania.

- Automatycznie przewija w odpowiedzi na wiadomości z klawiatury, myszy bez przewijania lub kółka myszy IntelliMouse.

Automatyczne przewijanie w odpowiedzi na wiadomości przy użyciu klawiatury, Dodaj przetłumaczyła komunikat i przetestować VK_DOWN, VK_PREV i wywołania [SetScrollPos](/windows/desktop/api/winuser/nf-winuser-setscrollpos).

Może obsługiwać obrót kółkiem myszy do przewijania samodzielnie przez zastąpienie mapowanych komunikat [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) i [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) funkcji elementów członkowskich. Są one dla `CScrollView`, te funkcje elementów członkowskich obsługuje zalecane zachowania [WM_MOUSEWHEEL](/windows/desktop/inputdev/wm-mousewheel), komunikat obrót kółkiem.

Można skorzystać z automatycznego przewijania, pochodzi z klasy widoku `CScrollView` zamiast z `CView`. Widok najpierw utworzenia, aby obliczyć rozmiar przewijany widok, w zależności od rozmiaru dokumentu, wywołanie `SetScrollSizes` funkcji składowej z przesłonięcia albo [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) lub [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Należy napisać własny kod do wykonywania zapytań rozmiar dokumentu. Aby uzyskać przykład, zobacz [próbki Bazgroły](../../overview/visual-cpp-samples.md).)

Wywołanie `SetScrollSizes` funkcja elementu członkowskiego Ustawia tryb mapowania tego widoku, łączna liczba wymiarów w widoku przewijania i kwoty, aby przewijać w poziomie i w pionie. Wszystkie rozmiary są w jednostkach logicznych. Rozmiar logiczny widoku zwykle jest obliczana na podstawie danych przechowywanych w dokumencie, ale w niektórych przypadkach możesz chcieć określić stały rozmiar. Aby zapoznać się z przykładami w obu przypadkach efekt, zobacz [CScrollView::SetScrollSizes](#setscrollsizes).

Należy określić kwoty, aby przewijać w poziomie i w pionie w jednostkach logicznych. Domyślnie, jeśli użytkownik kliknie wałka paska przewijania, poza pole przewijania `CScrollView` Przewija "page". Jeśli użytkownik kliknie przycisk strzałki przewijania na końcu paska przewijania, `CScrollView` Przewija "wiersz". Domyślnie strona jest 1/10 całkowitego rozmiaru widoku. wiersz jest 1/10 rozmiaru strony. Zastąp te wartości domyślne, przekazując rozmiary niestandardowe w `SetScrollSizes` funkcja elementu członkowskiego. Na przykład możesz ustawić poziomy rozmiar do końcowej szerokości całkowity rozmiar i pionowy rozmiar, aby wysokość wiersza w bieżącej czcionki.

Zamiast przewijanie, `CScrollView` może automatycznie skalować widok, aby bieżący rozmiar okna. W tym trybie widoku nie ma pasków przewijania i widok logiczny jest rozciągany lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Aby używać tej funkcji skalowania do dopasowania, należy wywołać [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Wywołania albo `SetScaleToFitSize` lub `SetScrollSizes`, ale nie oba jednocześnie.)

Przed `OnDraw` funkcji składowej klasy pochodnej widoku jest wywoływany, `CScrollView` automatycznie dostosowuje okienka ekranu początkowego `CPaintDC` obiekt kontekstu urządzenia, który przejdzie do `OnDraw`.

Aby dopasować pochodzenia okienka ekranu okna przewijania `CScrollView` zastępuje [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). To dopasowanie jest automatyczny dla `CPaintDC` kontekstu urządzenia, `CScrollView` przekazuje do `OnDraw`, ale należy wywołać `CScrollView::OnPrepareDC` samodzielnie dla innych kontekstach urządzenia używasz, takie jak `CClientDC`. Można zastąpić `CScrollView::OnPrepareDC` zestawu pióra, kolor tła i inne atrybuty rysowania, ale wywołanie klasy bazowej w celu skalowania.

Paski przewijania mogą być wyświetlane w trzech miejscach względem widoku, jak pokazano w następujących przypadkach:

- Styl okna standardowych pasków przewijania mogą być ustawiane dla widoku przy użyciu WS_HSCROLL i WS_VSCROLL[style Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- Formanty paska przewijania mogą być również dodawane do ramki, zawierający widok, w tym przypadku ramach przekazuje WM_HSCROLL i WM_VSCROLL wiadomości z oknem ramki do aktualnie aktywnego widoku.

- Struktura również przekazuje przewiń wiadomości z `CSplitterWnd` Splitter — formant do okienka aktualnie aktywnego rozdzielacza (view). Po umieszczeniu w [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) pasków przewijania udostępnionego `CScrollView` obiektu będzie używać udostępnionego te zamiast tworzenia własnej.

Aby uzyskać więcej informacji na temat korzystania z `CScrollView`, zobacz [architektury dokument/widok](../../mfc/document-view-architecture.md) i [pochodne Widok klas dostępne w MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy poziome i pionowe paski przewijania widoku.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parametry

*bHasHorzBar*<br/>
Wskazuje, że aplikacja ma poziomy pasek przewijania.

*bHasVertBar*<br/>
Wskazuje, że aplikacja ma pionowy pasek przewijania.

##  <a name="cscrollview"></a>  CScrollView::CScrollView

Konstruuje `CScrollView` obiektu.

```
CScrollView();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `SetScrollSizes` lub `SetScaleToFitSize` przed przewijania widoku są wykorzystywane.

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

Wywołaj `FillOutsideRect` aby wypełnił obszar widoku, który pojawia się poza przewijanym obszarze.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Kontekst urządzenia, w którym ma zostać wykonane wypełniania.

*pBrush*<br/>
Pędzel, z którym ma zostać wypełniony obszaru.

### <a name="remarks"></a>Uwagi

Użyj `FillOutsideRect` w widoku przewijania `OnEraseBkgnd` funkcji obsługi, aby uniknąć nadmiernego tła odświeżenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

Wywołaj `GetDeviceScrollPosition` gdy będziesz potrzebować bieżącego poziome i pionowe położenia okna przewijania w paski przewijania.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Położenie poziome i pionowe (w jednostkach urządzenia) pola przewijania jako `CPoint` obiektu.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odnosi się do lokalizacji w dokumencie, do którego został przewijane w lewym górnym rogu widoku. Ułatwia to przesunięcie pozycji urządzenie myszy w widoku przewijania urządzenia miejsca.

`GetDeviceScrollPosition` Zwraca wartości w jednostkach urządzenia. Jeśli chcesz, aby jednostki logiczne, użyj `GetScrollPosition` zamiast tego.

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes` Pobiera bieżący tryb mapowania, całkowity rozmiar i rozmiary wiersza i strony przewijany widoku.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Zwraca bieżący tryb mapowania dla tego widoku. Aby uzyskać listę możliwych wartości, zobacz `SetScrollSizes`.

*sizeTotal*<br/>
Zwraca bieżący łączny rozmiar widoku przewijania w jednostkach urządzenia.

*sizePage*<br/>
Zwraca bieżący kwoty poziome i pionowe do przewijania w każdym kierunku w odpowiedzi na myszy kliknij wałka paska przewijania. `cx` Elementu członkowskiego zawiera poziomy kwotę. `cy` Elementu członkowskiego zawiera kwotę pionowy.

*sizeLine*<br/>
Zwraca bieżący kwoty poziome i pionowe do przewijania w każdym kierunku w odpowiedzi na myszy kliknij strzałki przewijania. `cx` Elementu członkowskiego zawiera poziomy kwotę. `cy` Elementu członkowskiego zawiera kwotę pionowy.

### <a name="remarks"></a>Uwagi

Rozmiary są w jednostkach urządzenia. Ta funkcja elementu członkowskiego rzadko są wywoływane.

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

Wywołaj `GetScrollPosition` gdy będziesz potrzebować bieżącego poziome i pionowe położenia okna przewijania w paski przewijania.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Położenie poziome i pionowe (w jednostkach logicznych) pola przewijania jako `CPoint` obiektu.

### <a name="remarks"></a>Uwagi

Ta para współrzędnych odnosi się do lokalizacji w dokumencie, do którego został przewijane w lewym górnym rogu widoku.

`GetScrollPosition` Zwraca wartości w jednostkach logicznych. Jeśli jednostki urządzenia, należy użyć `GetDeviceScrollPosition` zamiast tego.

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

Wywołaj `GetTotalSize` można pobrać bieżących rozmiarach poziome i pionowe widoku przewijania.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Całkowity rozmiar widoku przewijania w jednostkach logicznych. Trwa rozmiar poziomy `cx` członkiem `CSize` zwracają wartość. Trwa pionowy rozmiar `cy` elementu członkowskiego.

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

Wywołaj `ResizeParentToFit` umożliwiające rozmiar widoku dyktowanie rozmiar okna ramki.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bShrinkOnly*<br/>
Rodzaj zmiana rozmiaru do wykonania. Wartość domyślna to TRUE, zmniejsza okno ramowe, jeśli to stosowne. Paski przewijania nadal będą wyświetlane dla widoków dużych lub małych okna ramowe. Wartość FALSE powoduje, że w celu zawsze dokładnie zmiany rozmiaru okna ramki. Może to być nieco niebezpieczne, ponieważ okno ramowe można pobrać zbyt duży, aby zmieścił się wewnątrz okna ramki (MDI) interfejsu wielu dokumentów lub ekranu.

### <a name="remarks"></a>Uwagi

Jest to zalecane tylko dla widoków okien ramek podrzędnych MDI. Użyj `ResizeParentToFit` w `OnInitialUpdate` funkcji obsługi usługi pochodnej `CScrollView` klasy. Na przykład ta funkcja elementu członkowskiego zobacz [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit` przyjęto założenie, że ustawiono rozmiaru okna widoku. Jeśli rozmiar okna widoku nie została ustawiona podczas `ResizeParentToFit` jest wywoływana, otrzymasz potwierdzenie. Aby upewnić się, że tak nie jest, należy wykonać następujące wywołanie przed wywołaniem `ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

Wywołaj `ScrollToPosition` przewiń do danego punktu w widoku.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
Punkt przewinięcia w jednostkach logicznych. `x` Elementu członkowskiego musi być wartością dodatnią (większe niż lub równa 0, aż do całkowitego rozmiaru widoku). Dotyczy to także `y` przy włączonym trybie mapowania MM_TEXT element członkowski. `y` Elementu członkowskiego ma ujemną wartość w trybach mapowanie innych niż MM_TEXT.

### <a name="remarks"></a>Uwagi

Widok będzie przewijane, tak aby ten punkt znajduje się w lewym górnym rogu okna. Nie można wywołać tej funkcji elementu członkowskiego, jeśli widok jest skalowane w celu dopasowania.

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

Wywołaj `SetScaleToFitSize` umożliwia automatyczne skalowanie rozmiaru okienka ekranu do bieżącego rozmiaru okna.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parametry

*sizeTotal*<br/>
Poziome i pionowe rozmiary, do których ma być skalowana w widoku. Rozmiar widoku przewijania jest mierzona w jednostkach logicznych. Rozmiar poziomy znajduje się w `cx` elementu członkowskiego. Pionowy rozmiar znajduje się w `cy` elementu członkowskiego. Zarówno `cx` i `cy` musi być większa lub równa 0.

### <a name="remarks"></a>Uwagi

Z pasków przewijania w dowolnym momencie może być widoczny tylko część widok logiczny. Ale za pomocą funkcji skalowania do rozmiaru widoku nie ma pasków przewijania i widok logiczny jest rozciągany lub zmniejszyć, aby dokładnie dopasować obszaru klienckiego okna. Przy zmianie rozmiaru okna widoku rysuje swoje dane w nowej skali, w zależności od rozmiaru okna.

Zwykle będzie umieścić wywołanie `SetScaleToFitSize` w przesłonięcia widoku `OnInitialUpdate` funkcja elementu członkowskiego. Jeśli nie chcesz, automatycznego skalowania, należy wywołać `SetScrollSizes` zamiast tego funkcję członkowską.

`SetScaleToFitSize` może służyć do implementacji operacji "Powiększenie do Fit". Użyj `SetScrollSizes` ponowne zainicjowanie przewijania.

`SetScaleToFitSize` przyjęto założenie, że ustawiono rozmiaru okna widoku. Jeśli rozmiar okna widoku nie została ustawiona podczas `SetScaleToFitSize` jest wywoływana, otrzymasz potwierdzenie. Aby upewnić się, że tak nie jest, należy wykonać następujące wywołanie przed wywołaniem `SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

Wywołaj `SetScrollSizes` gdy widok jest około do zaktualizowania.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parametry

*nMapMode*<br/>
Tryb mapowania, aby ustawić dla tego widoku. Możliwe wartości obejmują:

|Tryb mapowania|Jednostka logiczna|Rozszerzenie dodatnie y...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 piksel|W dół|
|MM_HIMETRIC|0,01 mm|W górę|
|MM_TWIPS|od 1/1440 w|W górę|
|MM_HIENGLISH|0,001 w|W górę|
|MM_LOMETRIC|0,1 mm|W górę|
|MM_LOENGLISH|0,01 w|W górę|

Wszystkie te tryby są definiowane przez Windows. Dwa tryby standardowa mapowania MM_ISOTROPIC i MM_ANISOTROPIC, nie są używane przez `CScrollView`. Biblioteka klas zawiera `SetScaleToFitSize` funkcję członkowską skalowanie widok do rozmiaru okna. W kolumnie trzy w powyższej tabeli opisano współrzędnych orientacji.

*sizeTotal*<br/>
Całkowity rozmiar widoku przewijania. `cx` Elementu członkowskiego zawiera poziomy zakresu. `cy` Elementu członkowskiego zawiera pionowego. Rozmiary są w jednostkach logicznych. Zarówno `cx` i `cy` musi być większa lub równa 0.

*sizePage*<br/>
Kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy kliknij wałka paska przewijania. `cx` Elementu członkowskiego zawiera poziomy kwotę. `cy` Elementu członkowskiego zawiera kwotę pionowy.

*sizeLine*<br/>
Kwoty poziome i pionowe przewijanie w każdym kierunku w odpowiedzi na myszy kliknij strzałki przewijania. `cx` Elementu członkowskiego zawiera poziomy kwotę. `cy` Elementu członkowskiego zawiera kwotę pionowy.

### <a name="remarks"></a>Uwagi

Zakres jest wywoływany w zastąpienie metody `OnUpdate` funkcję elementu członkowskiego, aby dostosować właściwości przewijania, gdy na przykład początkowo jest wyświetlany dokument lub zmienia rozmiar.

Informacje o rozmiarze będzie zazwyczaj uzyskiwany z tego widoku powiązany dokument, przez wywołanie funkcji elementu członkowskiego dokument, może być wywoływana `GetMyDocSize`, przez użytkownika za pomocą klasy pochodnej dokumentu. Poniższy kod ilustruje takie podejście:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Alternatywnie mogą czasami musisz ustawić o stałym rozmiarze, zgodnie z poniższym kodem:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Należy ustawić tryb mapowania do dowolnego z trybów mapowania Windows z wyjątkiem MM_ISOTROPIC lub MM_ANISOTROPIC. Jeśli chcesz użyć trybu nieograniczonego mapowania wywołać `SetScaleToFitSize` funkcja elementu członkowskiego zamiast `SetScrollSizes`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
