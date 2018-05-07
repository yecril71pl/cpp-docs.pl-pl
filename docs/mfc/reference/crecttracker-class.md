---
title: Crecttracker — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eff57e1fde0af6e794c2c47db7d1e31daf545715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="crecttracker-class"></a>Crecttracker — klasa
Umożliwia element do wyświetlenia, przenieść i zmiany rozmiaru w różnych fashions.  
  
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
|[CRectTracker::AdjustRect](#adjustrect)|Wywoływane, gdy zmieni się rozmiar prostokąta.|  
|[CRectTracker::Draw](#draw)|Renderuje prostokąta.|  
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Wywoływane, gdy rysunek obramowania `CRectTracker` obiektu.|  
|[CRectTracker::GetHandleMask](#gethandlemask)|Wywołuje się, by pobrać maska `CRectTracker` uchwyty zmiany rozmiaru elementu.|  
|[CRectTracker::GetTrueRect](#gettruerect)|Zwraca szerokość i wysokość prostokąta, w tym uchwytów zmiany rozmiaru.|  
|[CRectTracker::HitTest](#hittest)|Zwraca wartość bieżącej pozycji kursora związane z `CRectTracker` obiektu.|  
|[CRectTracker::NormalizeHit](#normalizehit)|Normalizuje kod testu trafień.|  
|[CRectTracker::OnChangedRect](#onchangedrect)|Wywoływane podczas zmiany rozmiaru lub przenieść prostokąta.|  
|[CRectTracker::SetCursor](#setcursor)|Ustawia kursor, w zależności od położenia za pośrednictwem prostokąta.|  
|[CRectTracker::Track](#track)|Umożliwia użytkownikowi manipulowania prostokąta.|  
|[CRectTracker::TrackRubberBand](#trackrubberband)|Umożliwia użytkownikowi "gumki" zaznaczenia.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Określa rozmiar uchwyt zmiany rozmiaru.|  
|[CRectTracker::m_nStyle](#m_nstyle)|Bieżący style(s) śledzący.|  
|[CRectTracker::m_rect](#m_rect)|Bieżąca pozycja (w pikselach) prostokąta.|  
|[CRectTracker::m_sizeMin](#m_sizemin)|Określa prostokątne minimalna szerokość i wysokość.|  
  
## <a name="remarks"></a>Uwagi  
 `CRectTracker` nie ma klasy podstawowej.  
  
 Mimo że `CRectTracker` klasy zaprojektowano w celu Zezwalaj użytkownikom na interakcję z elementami OLE przy użyciu interfejsu graficznego, jego użycie nie jest ograniczony do aplikacji obsługujących OLE. Mogą być używane wszędzie interfejs użytkownika jest wymagana.  
  
 `CRectTracker` Obramowanie może być stałe lub przerywana wierszy. Element można podany kreskowane obramowanie lub umieszczenia wzorem kreskowanym wskazująca innych stanów elementu. Osiem uchwytów zmiany rozmiaru można umieścić na zewnątrz lub wewnątrz obramowania elementu. (Aby uzyskać informacje o uchwytów zmiany rozmiaru, zobacz [GetHandleMask](#gethandlemask).) Na koniec `CRectTracker` umożliwia zmianę orientacji elementu podczas zmiany rozmiaru.  
  
 Aby użyć `CRectTracker`, utworzyć `CRectTracker` obiektu i określić, które stany wyświetlania są inicjowane. Następnie można ten interfejs Prześlij opinię visual użytkownika na bieżący stan elementu OLE skojarzonego z `CRectTracker` obiektu.  
  
 Aby uzyskać więcej informacji na temat używania `CRectTracker`, zapoznaj się z artykułem [Trackerów](../../mfc/trackers.md).  
  
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
 `nHandle`  
 Indeks uchwyt używany.  
  
 `lpRect`  
 Wskaźnik do bieżącego rozmiaru prostokąta. (Rozmiar prostokąta znajduje się przez jego wysokość i szerokość).  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta funkcja umożliwia orientacji prostokąta można zmienić tylko wtedy, gdy `Track` i `TrackRubberBand` są nazywane z odwracanie dozwolone.  
  
 Należy przesłonić tę funkcję, aby kontrolować dostosowania prostokąt śledzenia podczas operacji przeciągania. Na przykład dopasować współrzędne określony przez `lpRect` przed zwróceniem.  
  
 Specjalne funkcje, które nie są bezpośrednio obsługiwane przez `CRectTracker`, takie jak przyciąganie do siatki lub keep proporcje, może być zaimplementowany przez zastępowanie tej funkcji.  
  
##  <a name="crecttracker"></a>  CRectTracker::CRectTracker  
 Tworzy i inicjuje `CRectTracker` obiektu.  
  
```  
CRectTracker();

 
CRectTracker(
    LPCRECT lpSrcRect,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `lpSrcRect`  
 Współrzędne obiektu prostokąta.  
  
 `nStyle`  
 Określa styl `CRectTracker` obiektu. Obsługiwane są następujące style:  
  
- **CRectTracker::solidLine** Użyj linię ciągłą obramowania prostokąta.  
  
- **CRectTracker::dottedLine** Użyj przerywana linia obramowania prostokąta.  
  
- **CRectTracker::hatchedBorder** stosowany jest wzorzec kreskowanym obramowania prostokąta.  
  
- **CRectTracker::resizeInside** uchwyty znajdujących się w prostokącie zmiany rozmiaru.  
  
- **CRectTracker::resizeOutside** znajduje się poza prostokątem uchwyty zmiany rozmiaru.  
  
- **CRectTracker::hatchInside** Hatched wzorzec obejmuje całą prostokąta.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor domyślny inicjuje `CRectTracker` obiektu wartościami z `lpSrcRect` i inicjuje innych rozmiarach do wartości domyślnych systemu. Jeśli obiekt jest tworzony bez parametrów `m_rect` i `m_nStyle` elementy członkowskie danych są niezainicjowany.  
  
##  <a name="draw"></a>  CRectTracker::Draw  
 Wywołanie tej funkcji do rysowania linii zewnętrzne i wewnętrzne region prostokąta.  
  
```  
void Draw(CDC* pDC) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia, na którym ma zostać narysowany.  
  
### <a name="remarks"></a>Uwagi  
 Styl śledzący Określa, jak jest wykonywane rysunku. Zobacz Konstruktor `CRectTracker` uzyskać więcej informacji o dostępnych style.  
  
##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect  
 Wywoływana przez platformę, gdy pozycja śledzący została zmieniona podczas wewnątrz `Track` lub `TrackRubberBand` funkcję elementu członkowskiego.  
  
```  
virtual void DrawTrackerRect(
    LPCRECT lpRect,  
    CWnd* pWndClipTo,  
    CDC* pDC,  
    CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskaźnik do `RECT` zawierający prostokąta do rysowania.  
  
 `pWndClipTo`  
 Wskaźnik do okna do użycia w wycinka prostokąta.  
  
 `pDC`  
 Wskaźnik do kontekstu urządzenia, na którym ma zostać narysowany.  
  
 `pWnd`  
 Wskaźnik do okna, na którym zostanie przeprowadzona rysunku.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wywołuje `CDC::DrawFocusRect`, która rysuje prostokąt kropkami.  
  
 Należy przesłonić tę funkcję, aby przekazać opinię różnych podczas operacji śledzenia.  
  
##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby pobrać maski dla prostokąta uchwyty zmiany rozmiaru.  
  
```  
virtual UINT GetHandleMask() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maska `CRectTracker` uchwyty zmiany rozmiaru elementu.  
  
### <a name="remarks"></a>Uwagi  
 Uchwyty zmiany rozmiaru są wyświetlane na stronach i narożników prostokąta i Zezwalaj użytkownikowi na kontrolowanie kształt i rozmiar.  
  
 Prostokąt ma 8 uchwytów zmiany rozmiaru nr 7-0. Każdy uchwyt zmiany rozmiaru odpowiada bit maski; wartość tego bit jest równa 2 ^ *n*, gdzie *n* jest numerem uchwyt zmiany rozmiaru. Bity 0-3 odpowiadają rogu uchwytów zmiany rozmiaru, zaczynając od góry po lewej przenoszenie do ruchu wskazówek zegara. Bity 4-7 odpowiadają stronie Zmień rozmiar dojść, począwszy od góry z ruchem wskazówek zegara. Na poniższej ilustracji przedstawiono zmiany rozmiaru prostokąta obsługuje i odpowiednie Zmień rozmiar uchwytu liczb i wartości:  
  
 ![Zmień rozmiar uchwytu numery](../../mfc/reference/media/vc35dp1.gif "vc35dp1")  
  
 Domyślna implementacja **GetHandleMask** zwraca maską bitów, dzięki czemu uchwytów zmiany rozmiaru. Jeśli jeden bit jest włączona, będzie rysowany odpowiedniego uchwyt zmiany rozmiaru.  
  
 Przesłonić tę funkcję elementu członkowskiego do ukrywania lub pokazywania się, że wskazany uchwyty zmiany rozmiaru.  
  
##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect  
 Wywołanie tej funkcji można pobrać współrzędne prostokąta.  
  
```  
void GetTrueRect(LPRECT lpTrueRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpTrueRect`  
 Wskaźnik do `RECT` struktury, która będzie zawierać urządzenia współrzędne `CRectTracker` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wymiary prostokąta obejmują wysokość i szerokość uchwytów wszelkie zmiany rozmiaru znajduje się na granicy zewnętrznej. Na zwrócenie, `lpTrueRect` jest zawsze znormalizowane prostokąt we współrzędnych urządzenia.  
  
##  <a name="hittest"></a>  CRectTracker::HitTest  
 Wywołanie tej funkcji, aby dowiedzieć się, czy użytkownik ma chwycić uchwyt zmiany rozmiaru.  
  
```  
int HitTest(CPoint point) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `point`  
 Punkt we współrzędnych urządzenia, aby przetestować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana jest oparta na typ wyliczeniowy **CRectTracker::TrackerHit** i może mieć jeden z następujących wartości:  
  
- **CRectTracker::hitNothing** -1  
  
- **CRectTracker::hitTopLeft** 0  
  
- **CRectTracker::hitTopRight** 1  
  
- **CRectTracker::hitBottomRight** 2  
  
- **CRectTracker::hitBottomLeft** 3  
  
- **CRectTracker::hitTop** 4  
  
- **CRectTracker::hitRight** 5  
  
- **CRectTracker::hitBottom** 6  
  
- **CRectTracker::hitLeft** 7  
  
- **CRectTracker::hitMiddle** 8  
  
##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize  
 Rozmiar wyrażony w pikselach, o `CRectTracker` uchwyty zmiany rozmiaru.  
  
```  
int m_nHandleSize;  
```  
  
### <a name="remarks"></a>Uwagi  
 Zainicjowany z wartością domyślną systemu.  
  
##  <a name="m_rect"></a>  CRectTracker::m_rect  
 Bieżąca pozycja prostokąta we współrzędnych klienta (w pikselach).  
  
```  
CRect m_rect;  
```  
  
##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin  
 Minimalny rozmiar prostokąta.  
  
```  
CSize m_sizeMin;  
```  
  
### <a name="remarks"></a>Uwagi  
 Obie wartości domyślne **cx** i **cy**, jest obliczana na podstawie wartości domyślne systemu szerokości obramowania. Ten element członkowski danych jest używany tylko przez `AdjustRect` funkcję elementu członkowskiego.  
  
##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle  
 Bieżący styl krawędzi prostokąta.  
  
```  
UINT m_nStyle;  
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [CRectTracker::CRectTracker](#crecttracker) listę możliwych stylów.  
  
##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit  
 Wywołanie tej funkcji można przekonwertować uchwyt potencjalnie odwrócony.  
  
```  
int NormalizeHit(int nHandle) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nHandle`  
 Dojście wybrane przez użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks znormalizowane dojścia.  
  
### <a name="remarks"></a>Uwagi  
 Gdy `CRectTracker::Track` lub `CRectTracker::TrackRubberBand` jest wywoływana z odwracanie dozwolone, jest możliwe, prostokąt, aby być zmieniany na osi x i y. W takim przypadku `HitTest` zwróci dojść, które są także odwracane względem prostokąta. Może to być nieodpowiednie rysowania opinii kursora, ponieważ opinii jest zależna od pozycji ekranu prostokąta nie część prostokąt struktury danych, które zostaną zmodyfikowane.  
  
##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect  
 Wywoływane przez platformę, gdy prostokąt śledzenia został zmieniony podczas wywoływania `Track`.  
  
```  
virtual void OnChangedRect(const CRect& rectOld);
```  
  
### <a name="parameters"></a>Parametry  
 *rectOld*  
 Zawiera współrzędne urządzenia starego `CRectTracker` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 W tym czasie ta funkcja jest wywoływana, wszystkie opinie narysowany `DrawTrackerRect` został usunięty. Domyślna implementacja ta funkcja nie działa.  
  
 Należy przesłonić tę funkcję, jeśli chcesz wykonać żadnej akcji po zmianie rozmiaru okna.  
  
##  <a name="setcursor"></a>  CRectTracker::SetCursor  
 Wywołanie tej funkcji, aby zmienić kształt kursora, gdy znajduje się nad `CRectTracker` region obiektu.  
  
```  
BOOL SetCursor(
    CWnd* pWnd,  
    UINT nHitTest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskazuje okna zawierającego kursora.  
  
 `nHitTest`  
 Wyniki poprzedniego testu trafienia z `WM_SETCURSOR` wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeżeli Poprzednie trafienie za pośrednictwem prostokąt tracker; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji z wewnątrz funkcji okna obsługująca `WM_SETCURSOR` komunikatu (zazwyczaj `OnSetCursor`).  
  
##  <a name="track"></a>  CRectTracker::Track  
 Wywołanie tej funkcji, aby wyświetlić interfejs użytkownika do zmiany rozmiaru okna.  
  
```  
BOOL Track(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = FALSE,  
    CWnd* pWndClipTo = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Obiekt okna, który zawiera prostokąta.  
  
 `point`  
 Współrzędne urządzenia bieżącego położenia kursora myszy względem obszaru klienckiego.  
  
 `bAllowInvert`  
 Jeśli **TRUE**, prostokąt może być odwrócony wzdłuż osi x i y; w przeciwnym razie **FALSE**.  
  
 `pWndClipTo`  
 Okno operacje rysowania zostanie obcięta do. Jeśli **NULL**, `pWnd` jest używany jako Prostokątny wycinek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zostanie naciśnięty klawisz ESC, proces śledzenie jest zatrzymywane, prostokąt przechowywane w module śledzącym nie ulega zmianie i zwracane jest 0. Jeśli zmiana zostaje zatwierdzona, przesuwanie wskaźnika myszy i zwolnienie lewego przycisku myszy, nowe położenie i/lub rozmiar jest rejestrowany w monitorze prostokąt i zwracany jest różna od zera.  
  
### <a name="remarks"></a>Uwagi  
 Jest to zazwyczaj wywoływana z wewnątrz funkcji aplikacji, która obsługuje `WM_LBUTTONDOWN` komunikatu (zazwyczaj `OnLButtonDown`).  
  
 Ta funkcja będzie przechwytywać mysz, dopóki użytkownik zwalnia lewego przycisku myszy, naciśnie klawisz ESC lub naciśnie prawym przyciskiem myszy. Jako użytkownik przesuwa wskaźnik myszy, opinii jest aktualizowany przez wywołanie metody `DrawTrackerRect` i `OnChangedRect`.  
  
 Jeśli `bAllowInvert` jest **TRUE**, prostokąt śledzenia może być zmieniany na osi x lub osi y.  
  
##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand  
 Wywołanie tej funkcji w celu zaznaczenia gumki —.  
  
```  
BOOL TrackRubberBand(
    CWnd* pWnd,  
    CPoint point,  
    BOOL bAllowInvert = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Obiekt okna, który zawiera prostokąta.  
  
 `point`  
 Współrzędne urządzenia bieżącego położenia kursora myszy względem obszaru klienckiego.  
  
 `bAllowInvert`  
 Jeśli **ma wartość TRUE,** prostokąt może być odwrócony wzdłuż osi x i y; w przeciwnym razie **FALSE**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wskaźnik myszy została przeniesiona i prostokąt nie jest pusty; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj jest wywoływana z wewnątrz funkcji aplikacji, która obsługuje `WM_LBUTTONDOWN` komunikatu (zazwyczaj `OnLButtonDown`).  
  
 Ta funkcja będzie przechwytywać mysz, dopóki użytkownik zwalnia lewego przycisku myszy, naciśnie klawisz ESC lub naciśnie prawym przyciskiem myszy. Jako użytkownik przesuwa wskaźnik myszy, opinii jest aktualizowany przez wywołanie metody `DrawTrackerRect` i `OnChangedRect`.  
  
 Śledzenie jest wykonywane z zaznaczenia kauczuku pasmem typu dojścia prawym dolnym. Jeśli odwracanie jest dozwolone, prostokąt mogą być określane przez przeciągnięcie w górę i w lewo lub w dół i po prawej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC śledzenia](../../visual-cpp-samples.md)   
 [Przykładowe MFC DRAWCLI](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleResizeBar](../../mfc/reference/coleresizebar-class.md)   
 [CRect, klasa](../../atl-mfc-shared/reference/crect-class.md)
