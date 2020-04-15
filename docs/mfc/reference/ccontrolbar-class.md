---
title: Klasa CControlBar
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
ms.openlocfilehash: deb95d76e6d68ba5b9fad82bca1d88fd71c5a547
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369393"
---
# <a name="ccontrolbar-class"></a>Klasa CControlBar

Klasa podstawowa dla klas paska sterowania [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)i [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Składnia

```
class CControlBar : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CControlBar::CControlBar](#ccontrolbar)|Konstruuje `CControlBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Zwraca rozmiar dynamicznego paska sterowania jako obiektu [CSize.](../../atl-mfc-shared/reference/csize-class.md)|
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Zwraca rozmiar paska sterowania jako obiektu [CSize.](../../atl-mfc-shared/reference/csize-class.md)|
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

Pasek sterowania to okno, które jest zazwyczaj wyrównane do lewej lub prawej strony okna ramki. Może zawierać elementy podrzędne, które są formantami opartymi na HWND, które są oknami, które generują i odpowiadają na komunikaty systemu Windows lub elementami nieopartymi na HWND, które nie są oknami i są zarządzane przez kod aplikacji lub kod frameworka. Pola listy i kontrolki edycji są przykładami formantów opartych na HWND; Okienka paska stanu i przyciski bitmapy są przykładami formantów innych niż HWND.

Okienka paska sterowania to zazwyczaj okienka podrzędne dla nadrzędnej ramki okna i zazwyczaj elementy równorzędne dla widoku klienta lub klienta MDI ramki okna. Obiekt `CControlBar` używa informacji dotyczących prostokąta klienta okna nadrzędnego, w celu ustalenia własnej pozycji. Następnie informuje okno nadrzędne, ile miejsca pozostaje nieprzydzielonego, w obszarze klienta okna nadrzędnego.

Aby uzyskać więcej informacji na temat funkcji `CControlBar`, zobacz:

- [Paski sterowania](../../mfc/control-bars.md)

- [Uwaga techniczna 31: Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="ccontrolbarcalcdynamiclayout"></a><a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout

Struktura wywołuje tę funkcję elementu członkowskiego, aby obliczyć wymiary dynamicznego paska narzędzi.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nLength (nLength)*<br/>
Żądany wymiar paska sterowania, poziomy lub pionowy, w zależności od *dwMode*.

*nMode*<br/>
Następujące wstępnie zdefiniowane flagi są używane do określenia wysokości i szerokości dynamicznego paska sterowania. Użyj operatora bitowego OR (&#124;), aby połączyć flagi.

|Flagi trybu układu|Co to oznacza|
|-----------------------|-------------------|
|LM_STRETCH|Wskazuje, czy pasek sterowania powinien być rozciągnięty do rozmiaru ramki. Ustaw, jeśli pasek nie jest prętem dokowania (niedostępnym do dokowania). Nie ustawia się, gdy pasek jest zadokowany lub przestawny (dostępny do dokowania). Jeśli jest ustawiona, LM_STRETCH ignoruje *nLength* i zwraca wymiary na podstawie stanu LM_HORZ. LM_STRETCH działa podobnie do parametru *bStretch* używanego w [CalcFixedLayout;](#calcfixedlayout) zobacz tę funkcję elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganiem a orientacją.|
|LM_HORZ|Wskazuje, że pasek jest ustawiony poziomo lub pionowo. Ustaw, czy pasek jest ustawiony poziomo, a jeśli jest ustawiony pionowo, nie jest ustawiony. LM_HORZ działa podobnie do parametru *bHorz* używanego w [CalcFixedLayout;](#calcfixedlayout) zobacz tę funkcję elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganiem a orientacją.|
|LM_MRUWIDTH|Ostatnio używana szerokość dynamiczna. Ignoruje parametr *nLength* i używa ostatnio używanej szerokości zapamiętanych.|
|LM_HORZDOCK|Poziome zadokowane wymiary. Ignoruje parametr *nLength* i zwraca rozmiar dynamiczny o największej szerokości.|
|LM_VERTDOCK|Wymiary zadokowane pionowo. Ignoruje parametr *nLength* i zwraca rozmiar dynamiczny o największej wysokości.|
|LM_LENGTHY|Ustaw, jeśli *nLength* wskazuje wysokość (kierunek Y) zamiast szerokości.|
|LM_COMMIT|Resetuje LM_MRUWIDTH do bieżącej szerokości przestawnego paska sterowania.|

### <a name="return-value"></a>Wartość zwracana

Rozmiar paska sterowania w pikselach obiektu [CSize.](../../atl-mfc-shared/reference/csize-class.md)

### <a name="remarks"></a>Uwagi

Zastąpokaj tę funkcję elementu członkowskiego, aby `CControlBar`zapewnić własny układ dynamiczny w klasach, z których pochodzisz. Klasy MFC pochodzące z `CControlBar`, takich jak [CToolbar](../../mfc/reference/ctoolbar-class.md), zastąpić tę funkcję elementu członkowskiego i zapewnić własną implementację.

## <a name="ccontrolbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout

Wywołanie tej funkcji elementu członkowskiego, aby obliczyć poziomy rozmiar paska sterowania.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bStieczka*<br/>
Wskazuje, czy pasek powinien być rozciągnięty do rozmiaru ramki. Parametr *bStretch* jest niezerowy, gdy pasek nie jest prętem dokowania (niedostępnym do dokowania) i wynosi 0, gdy jest zadokowany lub przestawny (dostępny do dokowania).

*Bhorz*<br/>
Wskazuje, że pasek jest ustawiony poziomo lub pionowo. Parametr *bHorz* jest niezerowy, jeśli pasek jest ustawiony poziomo i wynosi 0, jeśli jest zorientowany pionowo.

### <a name="return-value"></a>Wartość zwracana

Rozmiar paska sterowania w pikselach `CSize` obiektu.

### <a name="remarks"></a>Uwagi

Paski sterowania, takie jak paski narzędzi, mogą rozciągać się poziomo lub pionowo, aby pomieścić przyciski znajdujące się na pasku sterowania.

Jeśli *bStretch* ma wartość PRAWDA, rozciągnij wymiar wzdłuż orientacji dostarczonej przez *bHorz*. Innymi słowy, jeśli *bHorz* jest FALSE, pasek sterowania jest rozciągnięty pionowo. Jeśli *bStretch* jest FALSE, nie występuje rozciągnięcie. W poniższej tabeli przedstawiono możliwe permutacje i wynikowe style paska sterowania *bStretch* i *bHorz*.

|bStieczka|Bhorz|Rozciąganie|Orientacja|Dokowanie/Niedokowanie|
|--------------|-----------|----------------|-----------------|--------------------------|
|Prawda|Prawda|Rozciąganie poziome|Zorientowane w poziomie|Nie dokowanie|
|Prawda|FAŁSZ|Rozciąganie pionowe|Zorientowane pionowo|Nie dokowanie|
|FAŁSZ|Prawda|Brak dostępnego rozciągania|Zorientowane w poziomie|Dokowania|
|FAŁSZ|FAŁSZ|Brak dostępnego rozciągania|Zorientowane pionowo|Dokowania|

## <a name="ccontrolbarcalcinsiderect"></a><a name="calcinsiderect"></a>CControlBar::CalcInsideRect

Struktura wywołuje tę funkcję, aby obliczyć obszar klienta paska sterowania.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Zawiera bieżące wymiary paska sterowania; granic.

*Bhorz*<br/>
Wskazuje, że pasek jest ustawiony poziomo lub pionowo. Parametr *bHorz* jest niezerowy, jeśli pasek jest ustawiony poziomo i wynosi 0, jeśli jest zorientowany pionowo.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przed pomalowaniem paska sterowania.

Zastąpozuj tę funkcję, aby dostosować renderowanie obramowania i paska uchwytu paska sterowania.

## <a name="ccontrolbarccontrolbar"></a><a name="ccontrolbar"></a>CControlBar::CControlBar

Konstruuje `CControlBar` obiekt.

```
CControlBar();
```

## <a name="ccontrolbardopaint"></a><a name="dopaint"></a>CControlBar::DoPaint

Wywoływana przez strukturę do renderowania obramowania i paska chwytaka paska sterowania.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obramowań i chwytaka paska sterowania.

### <a name="remarks"></a>Uwagi

Zastądnie tej funkcji, aby dostosować zachowanie rysowania paska sterowania.

Inną metodą dostosowywania jest `DrawBorders` zastąpienie `DrawGripper` funkcji i i dodanie niestandardowego kodu rysunku dla obramowań i chwytaka. Ponieważ te metody są `DoPaint` wywoływane przez metodę `DoPaint` domyślną, zastąpienie nie jest potrzebne.

## <a name="ccontrolbardrawborders"></a><a name="drawborders"></a>CControlBar::DrawBorders

Wywoływana przez ramy, aby renderować granice paska sterowania.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obramowań paska sterowania.

*Rect*<br/>
Obiekt `CRect` zawierający wymiary paska sterowania.

### <a name="remarks"></a>Uwagi

Zastąd w tej funkcji należy dostosować wygląd obramowań paska sterowania.

## <a name="ccontrolbardrawgripper"></a><a name="drawgripper"></a>CControlBar::DrawGripper

Wywoływana przez strukturę do renderowania chwytaka paska sterowania.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania chwytaka paska sterowania.

*Rect*<br/>
Obiekt `CRect` zawierający wymiary chwytaka pręta sterującego.

### <a name="remarks"></a>Uwagi

Zastąpozuj tę funkcję, aby dostosować wygląd chwytaka paska sterowania.

## <a name="ccontrolbarenabledocking"></a><a name="enabledocking"></a>CControlBar::EnableDocking

Wywołanie tej funkcji, aby włączyć pasek sterowania do zadokowania.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*styl dwDockStyle*<br/>
Określa, czy pasek sterowania obsługuje dokowanie i boki okna nadrzędnego, do którego można zadokować pasek sterowania, jeśli jest obsługiwany. Może być co najmniej jedna z następujących czynności:

- CBRS_ALIGN_TOP Umożliwia dokowanie w górnej części obszaru klienta.

- CBRS_ALIGN_BOTTOM Umożliwia dokowanie w dolnej części obszaru klienta.

- CBRS_ALIGN_LEFT Umożliwia dokowanie po lewej stronie obszaru klienta.

- CBRS_ALIGN_RIGHT Umożliwia dokowanie po prawej stronie obszaru klienta.

- CBRS_ALIGN_ANY Umożliwia dokowanie po dowolnej stronie obszaru klienta.

- CBRS_FLOAT_MULTI Umożliwia puszczanie wielu prętów sterujących w jednym oknie miniramki.

Jeśli 0 (oznacza to, że nie flagi), pasek sterowania nie będzie dokować.

### <a name="remarks"></a>Uwagi

Określone boki muszą być zgodne z jedną z boków włączonych do dokowania w oknie ramki docelowej lub nie można zadokować paska sterowania do tego okna ramki.

## <a name="ccontrolbargetbarstyle"></a><a name="getbarstyle"></a>CControlBar::GetBarStyle

Wywołanie tej funkcji, aby określić, które **ustawienia CBRS_** (style paska sterowania) są obecnie ustawione dla paska sterowania.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Wartość zwracana

Bieżące **ustawienia CBRS_** (style paska sterowania) dla paska sterowania. Zobacz [CControlBar::SetBarStyle,](#setbarstyle) aby uzyskać pełną listę dostępnych stylów.

### <a name="remarks"></a>Uwagi

Nie obsługuje **stylów WS_** (stylu okna).

## <a name="ccontrolbargetborders"></a><a name="getborders"></a>CControlBar::GetBorders

Zwraca bieżące wartości obramowania dla paska sterowania.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CRect` zawierający bieżącą szerokość (w pikselach) każdej strony obiektu paska sterowania. Na przykład wartość *lewego* elementu członkowskiego, [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, jest szerokość lewej krawędzi.

## <a name="ccontrolbargetcount"></a><a name="getcount"></a>CControlBar::GetCount

Zwraca liczbę elementów innych niż HWND na `CControlBar` obiekcie.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów innych niż HWND na `CControlBar` obiekcie. Ta funkcja zwraca wartość 0 dla obiektu [CDialogBar.](../../mfc/reference/cdialogbar-class.md)

### <a name="remarks"></a>Uwagi

Typ elementu zależy od obiektu pochodnego: okienka dla obiektów [CStatusBar](../../mfc/reference/cstatusbar-class.md) oraz przyciski i separatory dla obiektów [CToolBar.](../../mfc/reference/ctoolbar-class.md)

## <a name="ccontrolbargetdockingframe"></a><a name="getdockingframe"></a>CControlBar::GetDockingFrame

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do bieżącego okna ramki, do którego jest zadokowany pasek sterowania.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

Jeśli pasek sterowania nie jest zadokowany do okna ramki (oznacza to, że jeśli pasek sterowania jest przestawny), ta funkcja zwróci wskaźnik do nadrzędnego [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat pasków sterowania dokowania, zobacz [CControlBar::EnableDocking](#enabledocking) i [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

## <a name="ccontrolbarisfloating"></a><a name="isfloating"></a>CControlBar::IsFloating

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy pasek sterowania jest przestawny lub zadokowany.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pasek sterowania jest zmienny; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby zmienić stan paska sterowania z zadokowanego na przestawny, wywołanie [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

## <a name="ccontrolbarm_bautodelete"></a><a name="m_bautodelete"></a>CControlBar::m_bAutoDelete

Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

*m_bAutoDelete* jest zmienną publiczną typu BOOL.

Obiekt paska sterowania jest zwykle osadzony w obiekcie okna ramki. W takim przypadku *m_bAutoDelete* jest 0, ponieważ osadzony obiekt paska sterowania jest niszczony, gdy okno ramki zostanie zniszczone.

Ustaw tę zmienną na wartość niezerową, `CControlBar` jeśli przydzielić obiekt na stercie i nie planujesz wywołać **delete**.

## <a name="ccontrolbarm_pinplaceowner"></a><a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner

Lokalny właściciel paska sterowania.

```
CWnd* m_pInPlaceOwner;
```

## <a name="ccontrolbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, aby zaktualizować stan paska narzędzi lub paska stanu.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Wskazuje okno ramki głównej aplikacji. Ten wskaźnik służy do routingu wiadomości aktualizacji.

*bDisableIfNoHndler*<br/>
Flaga, która wskazuje, czy formant, który nie ma obsługi aktualizacji powinny być automatycznie wyświetlane jako wyłączone.

### <a name="remarks"></a>Uwagi

Aby zaktualizować pojedynczy przycisk lub okienko, użyj makra ON_UPDATE_COMMAND_UI na mapie wiadomości, aby odpowiednio ustawić program obsługi aktualizacji. Zobacz [ON_UPDATE_COMMAND_UI,](message-map-macros-mfc.md#on_update_command_ui) aby uzyskać więcej informacji na temat korzystania z tego makra.

`OnUpdateCmdUI`jest wywoływana przez platformę, gdy aplikacja jest bezczynna. Okno ramki, które ma zostać zaktualizowane, musi być oknem podrzędnym, przynajmniej pośrednio, okna widocznej ramki. `OnUpdateCmdUI`jest zaawansowaną, nadpisywalną.

## <a name="ccontrolbarsetbarstyle"></a><a name="setbarstyle"></a>CControlBar::SetBarStyle

Wywołanie tej funkcji, aby ustawić żądane style **CBRS_** dla paska sterowania.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Żądane style paska sterowania. Może być co najmniej jedna z następujących czynności:

- CBRS_ALIGN_TOP Umożliwia zadokowanie paska sterowania do górnej części obszaru klienta okna ramki.

- CBRS_ALIGN_BOTTOM Umożliwia zadokowanie paska sterowania do dolnej części obszaru klienta okna ramki.

- CBRS_ALIGN_LEFT Umożliwia zadokowanie paska sterowania po lewej stronie obszaru klienta okna ramki.

- CBRS_ALIGN_RIGHT Umożliwia zadokowanie paska sterowania po prawej stronie obszaru klienta okna ramki.

- CBRS_ALIGN_ANY Umożliwia zadokowanie paska sterowania do dowolnej strony obszaru klienta okna ramki.

- CBRS_BORDER_TOP Powoduje, że obramowanie ma być rysowane na górnej krawędzi paska sterowania, gdy będzie widoczny.

- CBRS_BORDER_BOTTOM Powoduje, że obramowanie ma być rysowane na dolnej krawędzi paska sterowania, gdy będzie widoczny.

- CBRS_BORDER_LEFT Powoduje, że obramowanie ma być rysowane na lewej krawędzi paska sterowania, gdy będzie widoczny.

- CBRS_BORDER_RIGHT Powoduje, że obramowanie ma być rysowane na prawej krawędzi paska sterowania, gdy będzie widoczny.

- CBRS_FLOAT_MULTI Umożliwia puszczanie wielu prętów sterujących w jednym oknie miniramki.

- CBRS_TOOLTIPS Powoduje, że wskazówki dotyczące narzędzi mają być wyświetlane dla paska sterowania.

- CBRS_FLYBY Powoduje, że tekst wiadomości ma być aktualizowany w tym samym czasie co porady dotyczące narzędzi.

- CBRS_GRIPPER Powoduje, że chwytak, podobny do używanego `CReBar` na pasmach w `CControlBar`obiekcie, ma być rysowany dla dowolnej klasy pochodnej.

### <a name="remarks"></a>Uwagi

Nie wpływa na ustawienia **WS_** (styl okna).

## <a name="ccontrolbarsetborders"></a><a name="setborders"></a>CControlBar::SetBorders

Wywołanie tej funkcji, aby ustawić rozmiar obramowania paska sterowania.

```
void SetBorders(
    int cxLeft = 0,
    int cyTop = 0,
    int cxRight = 0,
    int cyBottom = 0);

void SetBorders(LPCRECT lpRect);
```

### <a name="parameters"></a>Parametry

*cxNaft*<br/>
Szerokość (w pikselach) lewej krawędzi paska sterowania.

*cyTop*<br/>
Wysokość (w pikselach) górnej granicy paska sterowania.

*cxRight (prawy)*<br/>
Szerokość (w pikselach) prawej krawędzi paska sterowania.

*cyBottom*<br/>
Wysokość (w pikselach) dolnej krawędzi paska sterowania.

*Lprect*<br/>
Wskaźnik do [obiektu CRect,](../../atl-mfc-shared/reference/crect-class.md) który zawiera bieżącą szerokość (w pikselach) każdego obramowania obiektu paska sterowania.

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia górną i dolną obamówcę paska sterowania na 5 pikseli, a lewą i prawą do 2 pikseli:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

## <a name="ccontrolbarsetinplaceowner"></a><a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner

Zmienia lokalnego właściciela paska sterowania.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do `CWnd` obiektu.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)<br/>
[Klasa CDialogBar](../../mfc/reference/cdialogbar-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)<br/>
[Klasa CReBar](../../mfc/reference/crebar-class.md)
