---
title: Crecttracker — klasa
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
ms.openlocfilehash: 9c54cdfecfa6c4ff0eef7e16003ab2097553953d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372274"
---
# <a name="crecttracker-class"></a>Crecttracker — klasa

Umożliwia elementu wyświetlany, przenoszone i zmiany rozmiaru w różnych fashions.

## <a name="syntax"></a>Składnia

```
class CRectTracker
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Konstruuje `CRectTracker` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Wywołuje się, gdy zmieniany jest rozmiar prostokąta.|
|[CRectTracker::Draw](#draw)|Renderuje prostokąta.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Wywołuje się, gdy rysunek obramowania `CRectTracker` obiektu.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Wywołuje się, by pobrać maska `CRectTracker` uchwyty zmiany rozmiaru elementu.|
|[CRectTracker::GetTrueRect](#gettruerect)|Zwraca szerokość i wysokość prostokąta, łącznie z uchwytami zmiany rozmiaru.|
|[CRectTracker::HitTest](#hittest)|Zwraca bieżącą pozycję kursora związane z `CRectTracker` obiektu.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje kodu testowania trafienia.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Wywoływane podczas zmiany rozmiaru lub przenieść prostokąt.|
|[CRectTracker::SetCursor](#setcursor)|Ustawia kursor, w zależności od jego pozycja w ciągu prostokąta.|
|[CRectTracker::Track](#track)|Umożliwia użytkownikowi manipulowania prostokąta.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Zezwala użytkownikowi na "gumki" wybór.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Określa rozmiar uchwytami zmiany rozmiaru.|
|[CRectTracker::m_nStyle](#m_nstyle)|Bieżący style(s) z obiektem śledzącym.|
|[CRectTracker::m_rect](#m_rect)|Bieżące położenie (w pikselach) krawędzi prostokąta.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Określa wysokość i szerokość minimalna prostokąta.|

## <a name="remarks"></a>Uwagi

`CRectTracker` nie ma klasy bazowej.

Mimo że `CRectTracker` klasa jest przeznaczona do umożliwiają użytkownikowi interakcję z elementami OLE przy użyciu interfejsu graficznego, jego użycie nie jest ograniczona do aplikacji obsługujących OLE. Może służyć wszędzie interfejs użytkownika jest wymagana.

`CRectTracker` krawędzie mogą być stałe lub linii kropkowanej. Biorąc pod uwagę kreskowanym obramowaniem lub nałożony wzorem kreskowanym do wskazania różnych stanów elementu elementu. Osiem uchwytami zmiany rozmiaru można umieścić na zewnątrz i wewnątrz obramowania elementu. (Objaśnienia dotyczące uchwytów zmiany rozmiaru, zobacz [GetHandleMask](#gethandlemask).) Na koniec `CRectTracker` pozwala zmienić orientację elementu podczas zmiany rozmiaru.

Aby użyć `CRectTracker`, konstruowania `CRectTracker` obiekt i określić, które stany wyświetlania są inicjowane. Następnie można ten interfejs zapewniają wizualną opinię użytkownika z bieżącym stanem elementu OLE skojarzonego z `CRectTracker` obiektu.

Aby uzyskać więcej informacji na temat korzystania z `CRectTracker`, zapoznaj się z artykułem [Trackery](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CRectTracker`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

Wywoływane przez platformę, gdy zmieniany jest rozmiar prostokąta śledzenia przy użyciu uchwyt zmiany rozmiaru.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*nHandle*<br/>
Indeks uchwyt używany.

*lpRect*<br/>
Wskaźnik na bieżący rozmiar prostokąta. (Rozmiar prostokąta znajduje się przez jego wysokości i szerokości).

### <a name="remarks"></a>Uwagi

Domyślne zachowanie tej funkcji umożliwia orientacji prostokąt można zmienić tylko wtedy, gdy `Track` i `TrackRubberBand` volat odwracanie dozwolone.

Należy przesłonić tę funkcję, aby kontrolować dostosowania prostokąt śledzenia podczas operacji przeciągania. Jedną z metod jest dostosowanie współrzędnych określonych przez *lprect —* przed zwróceniem.

Specjalne funkcje, które nie są bezpośrednio obsługiwane przez `CRectTracker`, takie jak przyciągania do siatki lub keep proporcje, może być implementowany przez zastąpienie tej funkcji.

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

Tworzy i inicjuje `CRectTracker` obiektu.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*lpSrcRect*<br/>
Współrzędne obiektu prostokąta.

*nStyle*<br/>
Określa styl `CRectTracker` obiektu. Obsługiwane są następujące style:

- `CRectTracker::solidLine` Linia ciągła na użytek obramowania prostokąta.

- `CRectTracker::dottedLine` Linia kropkowana na użytek obramowania prostokąta.

- `CRectTracker::hatchedBorder` Użyj wzorca zakreskowane obramowania prostokąta.

- `CRectTracker::resizeInside` Zmień rozmiar obsługuje znajdujący się wewnątrz prostokąta.

- `CRectTracker::resizeOutside` Zmień rozmiar obsługuje znajdujących się poza prostokąta.

- `CRectTracker::hatchInside` Wyklutych wzorzec obejmuje cały prostokąta.

### <a name="remarks"></a>Uwagi

Konstruktor domyślny inicjuje `CRectTracker` obiektu z wartościami z *lpSrcRect* i inicjuje ustawienia domyślne systemu o innych rozmiarach. Jeśli obiekt jest tworzony bez parametrów `m_rect` i `m_nStyle` elementy członkowskie danych są niezainicjowany.

##  <a name="draw"></a>  CRectTracker::Draw

Wywołaj tę funkcję, aby rysować linie zewnętrzne i wewnętrzne region prostokąta.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia, na którym do rysowania.

### <a name="remarks"></a>Uwagi

Styl śledzący Określa, jak jest wykonywane rysunku. Zobacz Konstruktor `CRectTracker` więcej informacji na temat dostępnych stylów.

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

Wywoływane przez platformę, zawsze wtedy, gdy zmienił stanowisko z obiektem śledzącym podczas wewnątrz `Track` lub `TrackRubberBand` funkcja elementu członkowskiego.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskaźnik do `RECT` zawierający narysować prostokąt.

*pWndClipTo*<br/>
Wskaźnik do okna do użycia w Prostokątny wycinek.

*pDC*<br/>
Wskaźnik do kontekstu urządzenia, na którym do rysowania.

*pWnd*<br/>
Wskaźnik do okna, na którym nastąpi rysunku.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wywołuje `CDC::DrawFocusRect`, który rysuje prostokąt kropkami.

Należy przesłonić tę funkcję, aby przekazać opinię różnych podczas operacji śledzenia.

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać maska dla uchwyty zmiany rozmiaru prostokąta.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Wartość zwracana

Maska `CRectTracker` uchwyty zmiany rozmiaru elementu.

### <a name="remarks"></a>Uwagi

Uchwytami zmiany rozmiaru są wyświetlane na stronach i narożników prostokąta i Zezwalaj użytkownikowi na kontrolowanie kształtu i rozmiaru prostokąta.

Prostokąt ma 8 uchwytami zmiany rozmiaru numerowane 0-7. Uchwyt zmiany rozmiaru, każdy jest reprezentowany przez z nieco maski; wartość ten bit jest równa 2 ^ *n*, gdzie *n* jest liczbą uchwyt zmiany rozmiaru. Usługa BITS 0 – 3 odpowiadają rogu uchwytów zmiany rozmiaru, od lewego górnego rogu przenoszenie do ruchu wskazówek zegara. Usługa BITS 4 – 7 odnoszą się do strony zmiany rozmiaru uchwyty, począwszy od góry z ruchem wskazówek zegara. Na poniższej ilustracji przedstawiono uchwyty zmiany rozmiaru prostokąt i odpowiadające im Zmień rozmiar uchwytu liczby i wartości:

![Zmień rozmiar uchwytu numery](../../mfc/reference/media/vc35dp1.gif "numery uchwyt zmiany rozmiaru")

Domyślna implementacja klasy `GetHandleMask` zwraca maski bitów, tak aby były wyświetlane uchwytami zmiany rozmiaru. Jeśli pojedynczy bit jest włączona, będą rysowane odpowiedniego uchwyt zmiany rozmiaru.

Zastąpienie tej funkcji elementu członkowskiego, aby ukryć lub pokazać, że wskazany uchwyty zmiany rozmiaru.

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

Wywołaj tę funkcję, aby pobrać współrzędnych prostokąta.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parametry

*lpTrueRect*<br/>
Wskaźnik do `RECT` strukturę, która będzie zawierać urządzenia współrzędne `CRectTracker` obiektu.

### <a name="remarks"></a>Uwagi

Wymiary prostokąta obejmują wysokość i szerokość z uchwytami zmiany rozmiaru, wszystkie znajdujące się na granicy zewnętrznego. Podczas zwracania, *lpTrueRect* jest zawsze prostokąt znormalizowanych współrzędnych urządzenia.

##  <a name="hittest"></a>  CRectTracker::HitTest

Wywołaj tę funkcję, aby dowiedzieć się, czy użytkownik ma złapał uchwyt zmiany rozmiaru.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
Punkt we współrzędnych urządzenia, aby przetestować.

### <a name="return-value"></a>Wartość zwracana

Wartość zwracana, opiera się na typ wyliczany `CRectTracker::TrackerHit` i może mieć jedną z następujących wartości:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

Rozmiar w pikselach, o `CRectTracker` uchwyty zmiany rozmiaru.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Uwagi

Inicjowany z wartością domyślną systemu.

##  <a name="m_rect"></a>  CRectTracker::m_rect

Bieżąca pozycja prostokąta w współrzędne klienta (w pikselach).

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

Minimalny rozmiar prostokąta.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Uwagi

Obie wartości domyślne `cx` i `cy`, są obliczane na podstawie domyślna wartość system szerokość obramowania. Ten element członkowski danych jest używany wyłącznie przez `AdjustRect` funkcja elementu członkowskiego.

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

Bieżący styl krawędzi prostokąta.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Uwagi

Zobacz [CRectTracker::CRectTracker](#crecttracker) listę możliwych stylów.

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

Wywołaj tę funkcję, aby przekonwertować potencjalnie odwróconą dojście.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parametry

*nHandle*<br/>
Dojście do wybranego przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Indeks znormalizowane dojście.

### <a name="remarks"></a>Uwagi

Gdy `CRectTracker::Track` lub `CRectTracker::TrackRubberBand` jest wywoływana z odwracanie dozwolone, istnieje możliwość, że prostokąt, który chcesz odwrócić na osi x i osi y. W takim przypadku `HitTest` zwróci uchwyty, które są także odwracane względem prostokąta. Może to być nieodpowiednie dla rysowania opinii kursora, ponieważ opinii jest zależna od pozycję prostokąt, a nie część struktury danych prostokąt, który zostanie zmodyfikowany na ekranie.

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

Wywoływane przez platformę, zawsze wtedy, gdy prostokąt monitor został zmieniony podczas wywoływania `Track`.

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parametry

*rectOld*<br/>
Zawiera stary współrzędne urządzenia `CRectTracker` obiektu.

### <a name="remarks"></a>Uwagi

W tym czasie ta funkcja jest wywoływana, wszystkie opinie z `DrawTrackerRect` został usunięty. Domyślna implementacja tej funkcji, nic nie robi.

Należy przesłonić tę funkcję, jeśli chcesz wykonać żadnych innych akcji po zmianie rozmiaru prostokąta.

##  <a name="setcursor"></a>  CRectTracker::SetCursor

Wywołaj tę funkcję, aby zmienić kształt kursora jest przemieszczany nad `CRectTracker` region obiektu.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskazuje okna zawierającego kursora.

*nHitTest*<br/>
Wyniki poprzedni test trafień z komunikat WM_SETCURSOR.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeżeli poprzednie trafień za pośrednictwem prostokąt tracker; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję z wewnątrz funkcji okna, które obsługuje komunikat WM_SETCURSOR (zazwyczaj `OnSetCursor`).

##  <a name="track"></a>  CRectTracker::Track

Wywołaj tę funkcję, aby wyświetlić interfejs użytkownika do zmiany rozmiaru prostokąta.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Obiekt okna, który zawiera prostokąta.

*Punkt*<br/>
Współrzędne urządzenia bieżącego położenia kursora myszy względem pola klienta.

*bAllowInvert*<br/>
W przypadku opcji TRUE prostokąt można odwrócić wzdłuż osi x lub osi y; w przeciwnym razie wartość FALSE.

*pWndClipTo*<br/>
W oknie, w którym rysowania operacje zostaną przycięte do. Jeśli ma wartość NULL, *pWnd* służy jako prostokątny.

### <a name="return-value"></a>Wartość zwracana

Zostanie naciśnięty klawisz ESC, proces śledzenie jest zatrzymywane, prostokąt, przechowywane w śledzący nie ulega zmianie i zwracany jest 0. Jeśli zmiana zostaje zatwierdzona, przesuwanie wskaźnika myszy, a następnie zwolnij przycisk myszy po lewej stronie, nowe położenie i/lub rozmiaru jest rejestrowana w prostokącie modułu śledzącego i zwracana jest wartość różną od zera.

### <a name="remarks"></a>Uwagi

To jest zazwyczaj wywoływana z wewnątrz funkcji aplikacji, który obsługuje `WM_LBUTTONDOWN` wiadomości (zazwyczaj `OnLButtonDown`).

Ta funkcja będzie przechwytywać mysz, dopóki użytkownik zwolni przycisk myszy po lewej stronie, naciśnięcie klawisza ESC lub naciśnie prawym przyciskiem myszy. Gdy użytkownik przesuwa wskaźnik myszy, opinii jest aktualizowana przez wywołanie metody `DrawTrackerRect` i `OnChangedRect`.

Jeśli *bAllowInvert* ma wartość PRAWDA, prostokąt śledzenia może być zmieniany na osi x lub osi y.

##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand

Wywołaj tę funkcję w celu zaznaczenia gumki.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Obiekt okna, który zawiera prostokąta.

*Punkt*<br/>
Współrzędne urządzenia bieżącego położenia kursora myszy względem pola klienta.

*bAllowInvert*<br/>
W przypadku opcji TRUE prostokąt można odwrócić wzdłuż osi x lub osi y; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli przeniesiono myszy i prostokąt nie jest pusta. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zwykle jest wywoływana z wewnątrz funkcji aplikacji, który obsługuje wiadomości WM_LBUTTONDOWN (zazwyczaj `OnLButtonDown`).

Ta funkcja będzie przechwytywać mysz, dopóki użytkownik zwolni przycisk myszy po lewej stronie, naciśnięcie klawisza ESC lub naciśnie prawym przyciskiem myszy. Gdy użytkownik przesuwa wskaźnik myszy, opinii jest aktualizowana przez wywołanie metody `DrawTrackerRect` i `OnChangedRect`.

Śledzenie odbywa się przy zaznaczeniem Gumka poza pasmem typu dojścia prawym dolnym. Jeśli odwracanie jest dozwolone, prostokąt rozmiar można zmieniać, przeciągając w górę i w lewo lub w dół i po prawej stronie.

## <a name="see-also"></a>Zobacz także

[Próbki MFC śledzenia](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleResizeBar](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)
