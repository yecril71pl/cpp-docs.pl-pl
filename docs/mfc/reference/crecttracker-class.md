---
title: Klasa CRectTracker
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 4d262ab5f88481d56de1c236effb66fcbf6a706a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368380"
---
# <a name="crecttracker-class"></a>Klasa CRectTracker

Umożliwia wyświetlanie, przenoszenie i przenoszenie i przenoszenie kształtu elementu w różnych stylach.

## <a name="syntax"></a>Składnia

```
class CRectTracker
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Konstruuje `CRectTracker` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Wywoływana po przesaniu prostokąta.|
|[CRectTracker::Draw](#draw)|Renderuje prostokąt.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Wywoływane podczas rysowania `CRectTracker` obramowania obiektu.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Wywoływany, aby uzyskać `CRectTracker` maskę uchwytów ponownego rozmiaru elementu.|
|[CRectTracker::GetTrueRect](#gettruerect)|Zwraca szerokość i wysokość prostokąta, w tym uchwyty o rozmiarze.|
|[CRectTracker::HitTest](#hittest)|Zwraca bieżącą pozycję kursora powiązanego `CRectTracker` z obiektem.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje kod testu trafień.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Wywoływana, gdy prostokąt został przesunięty lub przeniesiony.|
|[CRectTracker::SetCursor](#setcursor)|Ustawia kursor, w zależności od jego położenia nad prostokątem.|
|[CRectTracker::Utwór](#track)|Umożliwia użytkownikowi manipulowanie prostokątem.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Pozwala użytkownikowi na "guma-band" wybór.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Określa rozmiar uchwytów o rozmiarze.|
|[CRectTracker::m_nStyle](#m_nstyle)|Aktualny styl(y) trackera.|
|[CRectTracker::m_rect](#m_rect)|Bieżąca pozycja (w pikselach) prostokąta.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Określa minimalną szerokość i wysokość prostokąta.|

## <a name="remarks"></a>Uwagi

`CRectTracker`nie ma klasy podstawowej.

Mimo `CRectTracker` że klasa jest przeznaczona do umożliwienia użytkownikowi interakcji z elementami OLE przy użyciu interfejsu graficznego, jego użycie nie jest ograniczone do aplikacji z obsługą OLE. Może być używany wszędzie tam, gdzie wymagany jest taki interfejs użytkownika.

`CRectTracker`mogą być linie stałe lub kropkowane. Element może otrzymać kreskowane obramowanie lub nałożony kreskowanym wzorem, aby wskazać różne stany towaru. Można umieścić osiem uchwytów o rozmiarze na zewnętrznej lub wewnętrznej granicy elementu. (Aby uzyskać wyjaśnienie uchwytów o rozmiarze, zobacz [GetHandleMask](#gethandlemask).) Na koniec `CRectTracker` a umożliwia zmianę orientacji elementu podczas zmiany rozmiaru.

Aby `CRectTracker`użyć , `CRectTracker` zbudować obiekt i określić, które stany wyświetlania są inicjowane. Następnie można użyć tego interfejsu, aby przekazać użytkownikowi wizualne opinie na `CRectTracker` temat bieżącego stanu elementu OLE skojarzonego z obiektem.

Aby uzyskać więcej `CRectTracker`informacji na temat korzystania , zobacz artykuł [Trackery](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRectTracker`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect

Wywoływana przez strukturę, gdy prostokąt śledzenia jest zmieniany przy użyciu uchwytu ponownego rozmiaru.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*nRęksja*<br/>
Indeks używanego dojścia.

*Lprect*<br/>
Wskaźnik do bieżącego rozmiaru prostokąta. (Rozmiar prostokąta jest podana przez jego wysokość i szerokość.)

### <a name="remarks"></a>Uwagi

Domyślne zachowanie tej funkcji umożliwia orientację prostokąta, `Track` aby `TrackRubberBand` zmienić tylko wtedy, gdy i są wywoływane z odwrócenie dozwolone.

Zastąpij tę funkcję, aby kontrolować dopasowanie prostokąta śledzenia podczas operacji przeciągania. Jedną z metod jest dostosowanie współrzędnych określonych przez *lpRect* przed zwróceniem.

Specjalne funkcje, które nie `CRectTracker`są bezpośrednio obsługiwane przez , takich jak przyciąganie do siatki lub zachować proporcje, można zaimplementować przez zastąpienie tej funkcji.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker

Tworzy i inicjuje `CRectTracker` obiekt.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*lpSrcrect*<br/>
Współrzędne obiektu prostokąta.

*styl nStyle*<br/>
Określa styl `CRectTracker` obiektu. Obsługiwane są następujące style:

- `CRectTracker::solidLine`Użyj linii ciągłej dla obramowania prostokąta.

- `CRectTracker::dottedLine`Użyj linii kropkowanejedna dla obramowania prostokąta.

- `CRectTracker::hatchedBorder`Użyj kreskowanego wzoru dla obramowania prostokąta.

- `CRectTracker::resizeInside`Uchwyty ponownego rozmiaru znajdujące się wewnątrz prostokąta.

- `CRectTracker::resizeOutside`Uchwyty ponownego rozmiaru znajdujące się poza prostokątem.

- `CRectTracker::hatchInside`Kreskowany wzór obejmuje cały prostokąt.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor inicjuje `CRectTracker` obiekt z wartościami z *lpSrcRect* i inicjuje inne rozmiary do ustawień domyślnych systemu. Jeśli obiekt jest tworzony bez `m_rect` parametrów, elementy członkowskie i `m_nStyle` dane są uninitialized.

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw

Wywołanie tej funkcji, aby narysować linie zewnętrzne prostokąta i region wewnętrzny.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia, na którym można rysować.

### <a name="remarks"></a>Uwagi

Styl modułu śledzącego określa sposób rysowania. Zobacz konstruktora, `CRectTracker` aby uzyskać więcej informacji na temat dostępnych stylów.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect

Wywoływane przez strukturę, gdy pozycja trackera `Track` uległa zmianie podczas wewnątrz funkcji lub `TrackRubberBand` elementu członkowskiego.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskaźnik do `RECT` tego, który zawiera prostokąt do rysowania.

*pWndClipTo*<br/>
Wskaźnik do okna, który ma być używany do przycinania prostokąta.

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia, na którym można rysować.

*Pwnd*<br/>
Wskaźnik do okna, w którym będzie się pojawiał rysunek.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `CDC::DrawFocusRect`, który rysuje kropkowany prostokąt.

Zastąpić tę funkcję, aby zapewnić różne opinie podczas operacji śledzenia.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask

Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać maskę dla prostokąta uchwyty resize.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Wartość zwracana

Maska `CRectTracker` uchwytów o rozmiarze elementu.

### <a name="remarks"></a>Uwagi

Uchwyty o rozmiarze są wyświetlane po bokach i rogach prostokąta i umożliwiają użytkownikowi kontrolowanie kształtu i rozmiaru prostokąta.

Prostokąt ma 8 uchwytów o rozmiarze 0-7. Każdy uchwyt o rozmiarze jest reprezentowany przez nieco w masce; wartość tego bitu wynosi 2^ *n*, gdzie *n* jest numerem uchwytu o rozmiarze. Bity 0-3 odpowiadają uchwytom do rozmiaru narożnika, zaczynając od lewego górnego ruchu w prawo. Bity 4-7 odpowiadają bocznym uchwytom o rozmiarze, zaczynając od góry poruszającej się zgodnie z ruchem wskazówek zegara. Na poniższej ilustracji przedstawiono uchwyty o rozmiarze prostokąta i odpowiadające im numery i wartości uchwytów o rozmiarze:

![Ponowne rozmiary numerów uchwytów](../../mfc/reference/media/vc35dp1.gif "Ponowne rozmiary numerów uchwytów")

Domyślna implementacja `GetHandleMask` zwraca maskę bitów, tak aby były wyświetlane uchwyty o rozmiarze. Jeśli pojedynczy bit jest włączony, zostanie narysowany odpowiedni uchwyt o rozmiarze.

Zastąpokaj tę funkcję elementu członkowskiego, aby ukryć lub pokazać wskazane uchwyty rozmiaru.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect

Wywołanie tej funkcji, aby pobrać współrzędne prostokąta.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parametry

*lpTrueRect (lpTrueRect)*<br/>
Wskaźnik do `RECT` struktury, która będzie zawierać `CRectTracker` współrzędne urządzenia obiektu.

### <a name="remarks"></a>Uwagi

Wymiary prostokąta obejmują wysokość i szerokość uchwytów o rozmiarze znajdujących się na zewnętrznej krawędzi. Po powrocie *lpTrueRect* jest zawsze znormalizowanym prostokątem we współrzędnych urządzenia.

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest

Wywołanie tej funkcji, aby dowiedzieć się, czy użytkownik chwycił uchwyt o rozmiarze.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt, we współrzędnych urządzenia, do testowania.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość jest oparta na `CRectTracker::TrackerHit` typie wyliczonym i może mieć jedną z następujących wartości:

- `CRectTracker::hitNothing`-1

- `CRectTracker::hitTopLeft`0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop`4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize

Rozmiar uchwytów `CRectTracker` o rozmiarze w pikselach.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Uwagi

Zainicjowany z domyślną wartością systemową.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRectTracker::m_rect

Bieżąca pozycja prostokąta we współrzędnych klienta (pikselach).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

Minimalny rozmiar prostokąta.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Uwagi

Obie wartości `cx` domyślne i `cy`, są obliczane na podstawie domyślnej wartości systemowej dla szerokości obramowania. Ten element członkowski danych `AdjustRect` jest używany tylko przez funkcję elementu członkowskiego.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle

Bieżący styl prostokąta.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Uwagi

Zobacz [CRectTracker::CRectTracker](#crecttracker) listę możliwych stylów.

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit

Wywołanie tej funkcji, aby przekonwertować potencjalnie odwrócony uchwyt.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parametry

*nRęksja*<br/>
Obsługa wybrana przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Indeks znormalizowanego dojścia.

### <a name="remarks"></a>Uwagi

Gdy `CRectTracker::Track` `CRectTracker::TrackRubberBand` lub jest wywoływana z dopuszczeniem odwracania, możliwe jest odwrócenie prostokąta na osi x, osi y lub na obu tych. W takim `HitTest` przypadku zwróci uchwyty, które są również odwrócone w odniesieniu do prostokąta. Jest to niewłaściwe w przypadku rysowania informacji zwrotnych kursora, ponieważ informacje zwrotne zależą od położenia ekranu prostokąta, a nie od części struktury danych prostokąta, która zostanie zmodyfikowana.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect

Wywoływane przez strukturę, gdy prostokąt trackera zmienił `Track`się podczas wywołania .

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parametry

*reectStar*<br/>
Zawiera stare współrzędne `CRectTracker` urządzenia obiektu.

### <a name="remarks"></a>Uwagi

W czasie, gdy ta funkcja jest `DrawTrackerRect` wywoływana, wszystkie sprzężenia zwrotne rysowane z został usunięty. Domyślna implementacja tej funkcji nic nie robi.

Zastąpokaj tę funkcję, jeśli chcesz wykonać wszystkie akcje po przesiąknięciu prostokąta.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetCursor

Wywołanie tej funkcji, aby zmienić kształt `CRectTracker` kursora, gdy znajduje się nad regionem obiektu.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskazuje okno, które obecnie zawiera kursor.

*nHitTest (test)*<br/>
Wyniki poprzedniego testu trafienia, z komunikatu WM_SETCURSOR.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli poprzednie trafienie było nad prostokątem trackera; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji od wewnątrz funkcji okna, która obsługuje komunikat `OnSetCursor`WM_SETCURSOR (zazwyczaj).

## <a name="crecttrackertrack"></a><a name="track"></a>CRectTracker::Utwór

Wywołanie tej funkcji, aby wyświetlić interfejs użytkownika do zmiany rozmiaru prostokąta.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Obiekt okna zawierający prostokąt.

*Punkt*<br/>
Współrzędne urządzenia bieżącej pozycji myszy względem obszaru klienta.

*bAllowInvert (Nieumieja)*<br/>
Jeśli prawda, prostokąt można odwrócić wzdłuż osi x lub osi y; w przeciwnym razie FALSE.

*pWndClipTo*<br/>
Okno, do które zostaną przycięte operacje rysowania. Jeśli NULL, *pWnd* jest używany jako prostokąt przycinania.

### <a name="return-value"></a>Wartość zwracana

Jeśli klawisz ESC zostanie naciśnięty, proces śledzenia zostanie zatrzymany, prostokąt przechowywany w trackerze nie zostanie zmieniony, a 0 zostanie zwrócony. Jeśli zmiana zostanie zatwierdzona, przesuwając myszką i zwalniając lewy przycisk myszy, nowa pozycja i/lub rozmiar są rejestrowane w prostokącie modułu śledzącego i zwracana jest liczba niezerowa.

### <a name="remarks"></a>Uwagi

Jest to zwykle wywoływane od wewnątrz funkcji `WM_LBUTTONDOWN` aplikacji, która `OnLButtonDown`obsługuje komunikat (zazwyczaj).

Ta funkcja przechwytuje mysz, dopóki użytkownik nie zwolni lewego przycisku myszy, nie naciśnie klawisza ESC lub nie naciśnie prawego przycisku myszy. Gdy użytkownik przesuwa kursor myszy, informacja zwrotna `DrawTrackerRect` `OnChangedRect`jest aktualizowana przez wywołanie i .

Jeśli *bAllowInvert* ma wartość PRAWDA, prostokąt śledzenia można odwrócić na osi x lub osi y.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::TrackRubberBand

Wywołanie tej funkcji, aby wykonać wybór gumki.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Obiekt okna zawierający prostokąt.

*Punkt*<br/>
Współrzędne urządzenia bieżącej pozycji myszy względem obszaru klienta.

*bAllowInvert (Nieumieja)*<br/>
Jeśli prawda, prostokąt można odwrócić wzdłuż osi x lub osi y; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli mysz została przeniesiona i prostokąt nie jest pusty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zwykle jest wywoływana od wewnątrz funkcji aplikacji, która obsługuje komunikat WM_LBUTTONDOWN `OnLButtonDown`(zazwyczaj).

Ta funkcja przechwytuje mysz, dopóki użytkownik nie zwolni lewego przycisku myszy, nie naciśnie klawisza ESC lub nie naciśnie prawego przycisku myszy. Gdy użytkownik przesuwa kursor myszy, informacja zwrotna `DrawTrackerRect` `OnChangedRect`jest aktualizowana przez wywołanie i .

Śledzenie odbywa się za pomocą wyboru typu gumki z prawego dolnego uchwytu. Jeśli odwrócenie jest dozwolone, prostokąt można dopasowywać, przeciągając w górę i w lewo lub w dół i w prawo.

## <a name="see-also"></a>Zobacz też

[Przykładowy TRACKER MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleResizeBar](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)
