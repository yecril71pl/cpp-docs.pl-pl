---
title: Ccontrolbar — klasa
ms.date: 11/04/2016
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58773245"
---
# <a name="ccontrolbar-class"></a>Ccontrolbar — klasa

Klasa bazowa dla klas paska sterowania [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), i [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Składnia

```
class CControlBar : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Konstruuje `CControlBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Zwraca rozmiar dynamicznego paska sterowania jako [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Zwraca rozmiar paska sterowania jako [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.|
|[CControlBar::CalcInsideRect](#calcinsiderect)|Zwraca bieżące wymiary powierzchni paska sterowania; w tym obramowania.|
|[CControlBar::DoPaint](#dopaint)|Renderuje obramowania i uchwyt paska sterowania.|
|[CControlBar::DrawBorders](#drawborders)|Renderuje obramowania paska sterowania.|
|[CControlBar::DrawGripper](#drawgripper)|Renderuje uchwyt paska sterowania.|
|[CControlBar::EnableDocking](#enabledocking)|Umożliwia, aby pasek sterowania był zadokowany lub przestawny.|
|[CControlBar::GetBarStyle](#getbarstyle)|Pobiera ustawienia stylu paska sterowania.|
|[CControlBar::GetBorders](#getborders)|Pobiera wartości obramowania paska sterowania.|
|[CControlBar::GetCount](#getcount)|Zwraca liczbę elementów innych niż HWND na pasku sterowania.|
|[CControlBar::GetDockingFrame](#getdockingframe)|Zwraca wskaźnik do ramki, w której jest zadokowany pasek sterowania.|
|[CControlBar::IsFloating](#isfloating)|Zwraca wartość niezerową, jeśli dany pasek sterowania jest przestawny.|
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Wywołuje obsługę poleceń interfejsu użytkownika.|
|[CControlBar::SetBarStyle](#setbarstyle)|Modyfikuje ustawienia stylu paska sterowania.|
|[CControlBar::SetBorders](#setborders)|Ustawia wartości obramowania paska sterowania.|
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Zmienia lokalnego właściciela paska sterowania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.|
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Lokalny właściciel paska sterowania.|

## <a name="remarks"></a>Uwagi

Pasek sterowania to okno, które jest zazwyczaj wyrównane do lewej lub prawej strony okna ramki. Może on zawierać elementów podrzędnych, które są oparte na HWND formanty, które są okienkami i generują oraz odpowiadają na wiadomości Windows lub systemem HWND elementów, które nie są okienkami i są zarządzane przez kod aplikacji lub kodu struktury. Pola list i formanty edycji to przykłady formantów na podstawie HWND; okienka paska stanu i przyciski z mapami to przykłady formantów podstawie HWND.

Okienka paska sterowania to zazwyczaj okienka podrzędne dla nadrzędnej ramki okna i zazwyczaj elementy równorzędne dla widoku klienta lub klienta MDI ramki okna. Obiekt `CControlBar` używa informacji dotyczących prostokąta klienta okna nadrzędnego, w celu ustalenia własnej pozycji. Następnie informuje okno nadrzędne, ile miejsca pozostaje nieprzydzielonego, w obszarze klienta okna nadrzędnego.

Aby uzyskać więcej informacji na temat funkcji `CControlBar`, zobacz:

- [Paski sterowania](../../mfc/control-bars.md)

- [Uwaga techniczna 31: Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout

Struktura wywołuje tej funkcji elementu członkowskiego do obliczenia wymiarów dynamicznego paska narzędzi.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Żądana wymiaru pasek sterowania, poziomej lub pionowej, w zależności od *dwMode*.

*nMode*<br/>
Następujące flagi wstępnie zdefiniowane są używane do określenia wysokości i szerokości paska dynamicznej kontroli. Użyj Alternatywy bitowej (&#124;) operator, aby łączyć flagi.

|Flagi trybu układu|Znaczenie|
|-----------------------|-------------------|
|LM_STRETCH|Wskazuje, czy pasek sterowania powinien być rozciągnięty do rozmiaru ramki. Ustaw, jeśli nie jest pasek dokowania paska (niedostępne dla dokowanie). Nie ustawiona, gdy pasek jest zadokowany lub przestawny (dostępne dla dokowanie). Jeśli ustawiona, LM_STRETCH ignoruje *nLength* i zwraca wymiarów na podstawie stanu LM_HORZ. LM_STRETCH działa podobnie jak *bStretch* parametru użytego w [CalcFixedLayout](#calcfixedlayout); Zobacz tej funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganie i orientacji.|
|LM_HORZ|Wskazuje, czy pasek jest zorientowany poziomo czy pionowo. Ustaw, jeśli pasek jest w orientacji poziomej i jeśli jest w orientacji pionowej, nie jest ustawiona. LM_HORZ działa podobnie jak *bHorz* parametru użytego w [CalcFixedLayout](#calcfixedlayout); Zobacz tej funkcji elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganie i orientacji.|
|LM_MRUWIDTH|Ostatnio używane szerokość dynamicznych. Ignoruje *nLength* parametru i używa zapamiętanych ostatnio używane szerokości.|
|LM_HORZDOCK|Poziomy zadokowane wymiarów. Ignoruje *nLength* parametr i zwraca rozmiar dynamicznego o największej grubości.|
|LM_VERTDOCK|W pionie zadokowane wymiarów. Ignoruje *nLength* parametr i zwraca rozmiar dynamicznego o największej wysokości.|
|LM_LENGTHY|Ustaw, jeśli *nLength* wskazuje zamiast szerokość, wysokość (w kierunku Y).|
|LM_COMMIT|Resetuje LM_MRUWIDTH Bieżąca szerokość paska sterowania zmiennoprzecinkowego.|

### <a name="return-value"></a>Wartość zwracana

Pasek sterowania rozmiar, w pikselach, o [CSize](../../atl-mfc-shared/reference/csize-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Zastąpienie tej funkcji elementu członkowskiego, aby zapewnić dynamiczne układu w klasach pochodnych z `CControlBar`. Klasy MFC wyprowadzone z `CControlBar`, takich jak [CToolbar](../../mfc/reference/ctoolbar-class.md)zapewniali własną implementację i przesłonić tę funkcję elementu członkowskiego.

##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout

Wywołaj tę funkcję elementu członkowskiego, aby obliczyć rozmiar poziomy pasek sterowania.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bStretch*<br/>
Wskazuje, czy pasek powinien być rozciągnięty do rozmiaru ramki. *BStretch* parametru jest różna od zera, gdy pasek pasek dokowania (niedostępne dla dokowanie) nie jest to 0, gdy jest zadokowany lub przestawny (dostępne dla dokowanie).

*bHorz*<br/>
Wskazuje, czy pasek jest zorientowany poziomo czy pionowo. *BHorz* parametr ma wartość różną od zera, jeśli pasek jest w orientacji poziomej i wynosi 0, jeśli jest w orientacji pionowej.

### <a name="return-value"></a>Wartość zwracana

Pasek sterowania rozmiar, w pikselach, o `CSize` obiektu.

### <a name="remarks"></a>Uwagi

Paski sterowania, takie jak paski narzędzi mogą rozciągnąć poziomo lub pionowo umożliwiających przyciski znajdujących się w paska sterowania.

Jeśli *bStretch* ma wartość PRAWDA, Stretch Database wymiaru wzdłuż orientacji, dostarczone przez *bHorz*. Innymi słowy Jeśli *bHorz* ma wartość FAŁSZ, pasek sterowania jest rozciągana w pionie. Jeśli *bStretch* ma wartość FAŁSZ, stretch nie występuje. W poniższej tabeli przedstawiono możliwe permutacji, a wynikowy style pasek sterowania, z *bStretch* i *bHorz*.

|bStretch|bHorz|Rozciąganie|Orientacja|Dokowanie dokowanie/nie|
|--------------|-----------|----------------|-----------------|--------------------------|
|WARTOŚĆ TRUE|WARTOŚĆ TRUE|Rozciąganie poziome|Na poziomie|Nie dokowania|
|WARTOŚĆ TRUE|FAŁSZ|Rozciąganie w pionie|W pionie zorientowanej na|Nie dokowania|
|FAŁSZ|WARTOŚĆ TRUE|Nie rozciąganie dostępne|Na poziomie|Dokowanie|
|FAŁSZ|FAŁSZ|Nie rozciąganie dostępne|W pionie zorientowanej na|Dokowanie|

##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect

Struktura wywołuje tę funkcję, aby obliczyć obszaru klienckiego paska sterowania.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera bieżące wymiary paska sterowania; w tym obramowania.

*bHorz*<br/>
Wskazuje, czy pasek jest zorientowany poziomo czy pionowo. *BHorz* parametr ma wartość różną od zera, jeśli pasek jest w orientacji poziomej i wynosi 0, jeśli jest w orientacji pionowej.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przed narysowaniem paska sterowania.

Należy przesłonić tę funkcję, aby dostosować renderowania krawędzie i pasek uchwytu paska sterowania.

##  <a name="ccontrolbar"></a>  CControlBar::CControlBar

Konstruuje `CControlBar` obiektu.

```
CControlBar();
```

##  <a name="dopaint"></a>  CControlBar::DoPaint

Metoda wywoływana przez platformę, by renderowania krawędzie i pasek uchwytu paska sterowania.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia, które ma być używany do renderowania obramowania i uchwyt paska sterowania.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować zachowanie rysunku paska sterowania.

Inną metodą dostosowywania jest zastąpienie `DrawBorders` i `DrawGripper` funkcje i Dodaj niestandardowy kod rysowania obramowania i uchwyt. Ponieważ te metody są wywoływane przy użyciu domyślnej `DoPaint` metody, zastępowania metody `DoPaint` nie jest potrzebna.

##  <a name="drawborders"></a>  CControlBar::DrawBorders

Metoda wywoływana przez platformę, by renderować obramowania paska sterowania.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia, które ma być używany do renderowania krawędzie paska sterowania.

*Rect*<br/>
A `CRect` obiekt zawierający wymiary paska sterowania.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować wygląd obramowania paska sterowania.

##  <a name="drawgripper"></a>  CControlBar::DrawGripper

Metoda wywoływana przez platformę, by renderować uchwyt paska sterowania.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskazuje kontekst urządzenia, które ma być używany do renderowania uchwyt paska sterowania.

*Rect*<br/>
A `CRect` obiekt zawierający wymiary uchwyt paska sterowania.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę funkcję, aby dostosować wygląd uchwyt paska sterowania.

##  <a name="enabledocking"></a>  CControlBar::EnableDocking

Wywołaj tę funkcję, aby umożliwić jest zadokowany pasek sterowania.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Określa, czy pasek sterowania obsługuje dokujące i stronach jej okna nadrzędnego, do której może być zadokowany pasek sterowania, jeśli jest obsługiwany. Może być co najmniej jeden z następujących czynności:

- CBRS_ALIGN_TOP umożliwia dokowanie u góry obszaru klienta.

- CBRS_ALIGN_BOTTOM umożliwia zadokowane w dolnej części obszaru klienta.

- CBRS_ALIGN_LEFT umożliwia dokowanie po lewej stronie obszaru klienta.

- CBRS_ALIGN_RIGHT umożliwia dokowanie po prawej stronie obszaru klienta.

- CBRS_ALIGN_ANY umożliwia dokowanie na dowolnej stronie obszaru klienta.

- CBRS_FLOAT_MULTI umożliwia wielu pasków sterowania jest przestawione w oknie pojedynczy program miniramki.

Jeśli jest to 0 (oznacza to, co oznacza bez flag), pasek sterowania nie zostanie zadokowany.

### <a name="remarks"></a>Uwagi

Strony określony musi odpowiadać jednej strony, włączone dla dokowania w oknie ramki docelowej lub pasek sterowania nie może być zadokowane, do tej ramki okna.

##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle

Wywołaj tę funkcję, aby określić, które **CBRS_** (Style paska sterowania) są obecnie ustawienia paska sterowania.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący **CBRS_** (Style paska sterowania) ustawień paska sterowania. Zobacz [CControlBar::SetBarStyle](#setbarstyle) pełną listę dostępnych stylów.

### <a name="remarks"></a>Uwagi

Nie obsługuje **WS_** style (styl okna).

##  <a name="getborders"></a>  CControlBar::GetBorders

Zwraca bieżące wartości obramowania paska sterowania.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Wartość zwracana

A `CRect` obiekt, który zawiera bieżący szerokość (w pikselach) po obu stronach obiekt paska sterowania. Na przykład, wartość *po lewej stronie* elementu członkowskiego, z [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, to szerokość krawędzi lewej.

##  <a name="getcount"></a>  CControlBar::GetCount

Zwraca liczbę elementów innych niż HWND na `CControlBar` obiektu.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów innych niż HWND na `CControlBar` obiektu. Ta funkcja zwraca 0 w przypadku [CDialogBar](../../mfc/reference/cdialogbar-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Typ elementu jest zależny od obiektu pochodnej: panele dla [CStatusBar](../../mfc/reference/cstatusbar-class.md) obiekty i przyciski i separatory dla [CToolBar](../../mfc/reference/ctoolbar-class.md) obiektów.

##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do bieżącego okna ramki, do której jest zadokowany na pasku sterowania.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ramki okna, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

Jeśli jest zadokowany pasek sterowania nie do okna ramki (to znaczy, jeśli pasek sterowania jest liczb zmiennoprzecinkowych), funkcja ta będzie zwracać wskaźnik do elementu nadrzędnego [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat pasków sterowania dokowalne zobacz [CControlBar::EnableDocking](#enabledocking) i [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>  CControlBar::IsFloating

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy pasek sterowania jest ruchomy czy zadokowany.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pasek sterowania jest liczb zmiennoprzecinkowych; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zmienianie stanu pasek sterowania z zadokowanych liczb zmiennoprzecinkowych, wywołaj [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete

Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

*m_bAutoDelete* jest publiczną zmienną typu wartość logiczna.

Obiekt paska sterowania zwykle jest wbudowany w obiekt window dla ramki. W tym przypadku *m_bAutoDelete* wynosi 0, ponieważ obiekt osadzony pasek sterowania jest niszczony, kiedy niszczony jest oknem ramki.

Ustaw wartość tej zmiennej na wartość różną od zera jeśli przydzielisz `CControlBar` obiektów na stosie, nie jest planowane wywołania **Usuń**.

##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner

Lokalny właściciel paska sterowania.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI

Ta funkcja członkowska jest wywoływana przez platformę, aby zaktualizować stan paska narzędzi lub paska stanu.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Wskazuje ramką głównego okna aplikacji. This, wskaźnik jest używany do routingu wiadomości aktualizacji.

*bDisableIfNoHndler*<br/>
Flaga wskazująca, czy formant, który ma żadna procedura obsługi aktualizacji powinny być automatycznie wyświetlane jako wyłączone.

### <a name="remarks"></a>Uwagi

Aby zaktualizować poszczególnych przycisku lub okienku, umożliwia ON_UPDATE_COMMAND_UI — makro na mapie komunikatów odpowiednio ustawić programu obsługi aktualizacji. Zobacz [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) Aby uzyskać więcej informacji o korzystaniu z tego makra.

`OnUpdateCmdUI` jest wywoływane przez platformę, gdy aplikacja jest w stanie bezczynności. Okno ramowe do zaktualizowania musi być oknem podrzędnym co najmniej pośrednio okno ramowe widoczne. `OnUpdateCmdUI` jest to zaawansowany możliwym do zastąpienia.

##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle

Wywołaj tę funkcję, aby ustawić żądaną **CBRS_** Style paska sterowania.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Żądany Style paska sterowania. Może być co najmniej jeden z następujących czynności:

- CBRS_ALIGN_TOP umożliwia pasek sterowania bez możliwości dokowania na górze obszaru klienckiego okna ramki.

- CBRS_ALIGN_BOTTOM umożliwia pasek sterowania być zadokowane w dolnej części obszaru klienckiego okna ramki.

- CBRS_ALIGN_LEFT umożliwia pasek sterowania być zadokowane po lewej stronie obszaru klienckiego okna ramki.

- CBRS_ALIGN_RIGHT umożliwia pasek sterowania być zadokowane, aby po prawej stronie obszaru klienckiego okna ramki.

- CBRS_ALIGN_ANY umożliwia pasek sterowania być zadokowane, na dowolnej stronie obszaru klienckiego okna ramki.

- CBRS_BORDER_TOP powoduje, że obramowanie rysowany na górną krawędzią formantu paska, gdy będzie ono widoczne.

- CBRS_BORDER_BOTTOM powoduje, że obramowanie rysowany na dolną krawędzią formantu paska, gdy będzie ono widoczne.

- CBRS_BORDER_LEFT powoduje, że obramowanie do narysowania przy lewej krawędzi formantu paska, gdy będzie ono widoczne.

- CBRS_BORDER_RIGHT powoduje, że obramowanie do rysowania na prawej krawędzi formantu paska, gdy będzie ono widoczne.

- CBRS_FLOAT_MULTI umożliwia wielu pasków sterowania jest przestawione w oknie pojedynczy program miniramki.

- CBRS_TOOLTIPS powoduje, że etykietki narzędzia wyświetlany dla paska sterowania.

- CBRS_FLYBY powoduje, że tekst komunikatu do zaktualizowania w tym samym czasie jako etykietek narzędzi.

- CBRS_GRIPPER powoduje, że uchwytu, podobnie jak na paskami w `CReBar` obiektu do narysowania dla każdego `CControlBar`-klasy pochodnej.

### <a name="remarks"></a>Uwagi

Nie ma wpływu na **WS_** ustawienia (styl okna).

##  <a name="setborders"></a>  CControlBar::SetBorders

Wywołaj tę funkcję, aby ustawić rozmiar obramowania paska sterowania.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*cxLeft*<br/>
Szerokość (w pikselach) lewego obramowania paska sterowania.

*cyTop*<br/>
Wysokość (w pikselach) krawędzi górnego obramowania paska sterowania.

*cxRight*<br/>
Szerokość (w pikselach) prawej krawędzi paska sterowania.

*cyBottom*<br/>
Wysokość (w pikselach) pasek sterowania dolnej krawędzi.

*lpRect*<br/>
Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera bieżący szerokość (w pikselach) każdej krawędzi obiekt paska sterowania.

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia górny i dolny obramowania paska sterowania do 5 pikseli i obramowanie lewy i prawy pikseli 2:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner

Zmienia lokalnego właściciela paska sterowania.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do `CWnd` obiektu.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)<br/>
[Klasa CDialogBar](../../mfc/reference/cdialogbar-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)<br/>
[Klasa CReBar](../../mfc/reference/crebar-class.md)
