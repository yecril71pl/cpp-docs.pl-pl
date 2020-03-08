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
ms.openlocfilehash: 41e40b3da7b4a294fe396a9d93f7c6a93593ff95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866444"
---
# <a name="ccontrolbar-class"></a>Klasa CControlBar

Klasa bazowa dla klas paska sterowania [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md)i [COleResizeBar](../../mfc/reference/coleresizebar-class.md).

## <a name="syntax"></a>Składnia

```
class CControlBar : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CControlBar:: CControlBar](#ccontrolbar)|Konstruuje obiekt `CControlBar`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CControlBar:: CalcDynamicLayout](#calcdynamiclayout)|Zwraca rozmiar dynamicznego paska sterowania jako obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar:: CalcFixedLayout](#calcfixedlayout)|Zwraca rozmiar paska sterowania jako obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) .|
|[CControlBar:: CalcInsideRect](#calcinsiderect)|Zwraca bieżące wymiary powierzchni paska sterowania; w tym obramowania.|
|[CControlBar::D oPaint](#dopaint)|Renderuje obramowania i uchwyt paska sterowania.|
|[CControlBar::D rawBorders](#drawborders)|Renderuje obramowania paska sterowania.|
|[CControlBar::D rawGripper](#drawgripper)|Renderuje uchwyt paska sterowania.|
|[CControlBar:: EnableDocking](#enabledocking)|Umożliwia, aby pasek sterowania był zadokowany lub przestawny.|
|[CControlBar:: GetBarStyle](#getbarstyle)|Pobiera ustawienia stylu paska sterowania.|
|[CControlBar:: GetBorders](#getborders)|Pobiera wartości obramowania paska sterowania.|
|[CControlBar:: GetCount](#getcount)|Zwraca liczbę elementów innych niż HWND na pasku sterowania.|
|[CControlBar:: GetDockingFrame](#getdockingframe)|Zwraca wskaźnik do ramki, w której jest zadokowany pasek sterowania.|
|[CControlBar:: isfloating](#isfloating)|Zwraca wartość niezerową, jeśli dany pasek sterowania jest przestawny.|
|[CControlBar:: OnUpdateCmdUI](#onupdatecmdui)|Wywołuje obsługę poleceń interfejsu użytkownika.|
|[CControlBar:: SetBarStyle](#setbarstyle)|Modyfikuje ustawienia stylu paska sterowania.|
|[CControlBar:: setborderers](#setborders)|Ustawia wartości obramowania paska sterowania.|
|[CControlBar:: SetInPlaceOwner](#setinplaceowner)|Zmienia lokalnego właściciela paska sterowania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CControlBar:: m_bAutoDelete](#m_bautodelete)|Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.|
|[CControlBar:: m_pInPlaceOwner](#m_pinplaceowner)|Lokalny właściciel paska sterowania.|

## <a name="remarks"></a>Uwagi

Pasek sterowania to okno, które jest zazwyczaj wyrównane do lewej lub prawej strony okna ramki. Może zawierać elementy podrzędne, które są kontrolkami opartymi na elemencie HWND, które są systemu Windows, które generują i reagują na komunikaty systemu Windows lub nie są elementami opartymi na elemencie HWND, które nie są oknami i są zarządzane przez kod aplikacji lub kod struktury. Pola list i kontrolki edycji są przykładami kontrolek opartych na formancie HWND; paski narzędzi stanu i przyciski mapy bitowej są przykładami formantów nieopartych na HWND.

Okienka paska sterowania to zazwyczaj okienka podrzędne dla nadrzędnej ramki okna i zazwyczaj elementy równorzędne dla widoku klienta lub klienta MDI ramki okna. Obiekt `CControlBar` używa informacji dotyczących prostokąta klienta okna nadrzędnego, w celu ustalenia własnej pozycji. Następnie informuje okno nadrzędne, ile miejsca pozostaje nieprzydzielonego, w obszarze klienta okna nadrzędnego.

Aby uzyskać więcej informacji na temat funkcji `CControlBar`, zobacz:

- [Paski sterowania](../../mfc/control-bars.md)

- [Uwaga techniczna 31: Paski kontroli](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CControlBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="calcdynamiclayout"></a>CControlBar:: CalcDynamicLayout

Struktura wywołuje tę funkcję elementu członkowskiego, aby obliczyć wymiary dynamicznego paska narzędzi.

```
virtual CSize CalcDynamicLayout(
    int nLength,
    DWORD nMode);
```

### <a name="parameters"></a>Parametry

*nLength*<br/>
Żądany wymiar paska sterowania, w poziomie lub pionie, w zależności od *dwMode*.

*nMode*<br/>
Następujące wstępnie zdefiniowane flagi są używane do określania wysokości i szerokości dynamicznego paska kontroli. Użyj operatora bitowego lub (&#124;), aby połączyć flagi.

|Flagi trybu układu|Co to oznacza|
|-----------------------|-------------------|
|LM_STRETCH|Wskazuje, czy pasek kontroli ma być rozciągany do rozmiaru ramki. Ustaw, jeśli pasek nie jest paskiem dokującym (niedostępnym do dokowania). Nie ustawiaj, gdy pasek jest zadokowany lub przestawny (dostępny do dokowania). Jeśli jest ustawiona, LM_STRETCH ignoruje *nLength* i zwraca wymiary na podstawie stanu LM_HORZ. LM_STRETCH działa podobnie do parametru *bStretch* używanego w [CalcFixedLayout](#calcfixedlayout); Zobacz tę funkcję elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganiem i orientacją.|
|LM_HORZ|Wskazuje, że pasek jest poziomy lub pionowo. Ustaw, jeśli pasek ma orientację poziomą, a jeśli jest zorientowany pionowo, nie jest ustawiony. LM_HORZ działa podobnie do parametru *bHorz* używanego w [CalcFixedLayout](#calcfixedlayout); Zobacz tę funkcję elementu członkowskiego, aby uzyskać więcej informacji na temat relacji między rozciąganiem i orientacją.|
|LM_MRUWIDTH|Ostatnio używana Szerokość dynamiczna. Ignoruje parametr *nLength* i używa zapamiętanej ostatnio używanej szerokości.|
|LM_HORZDOCK|Poziome wymiary zadokowane. Ignoruje parametr *nLength* i zwraca rozmiar dynamiczny o największej szerokości.|
|LM_VERTDOCK|Wymiary zadokowane w pionie. Ignoruje parametr *nLength* i zwraca rozmiar dynamiczny o największej wysokości.|
|LM_LENGTHY|Ustaw, jeśli *nLength* wskazuje wysokość (kierunek Y), a nie szerokość.|
|LM_COMMIT|Resetuje LM_MRUWIDTH do bieżącej szerokości zmiennoprzecinkowego paska sterowania.|

### <a name="return-value"></a>Wartość zwracana

Rozmiar paska sterowania (w pikselach) obiektu [CSize](../../atl-mfc-shared/reference/csize-class.md) .

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję elementu członkowskiego, aby zapewnić własny układ dynamiczny w klasach pochodzących od `CControlBar`. Klasy MFC pochodne od `CControlBar`, takie jak [CToolBar](../../mfc/reference/ctoolbar-class.md), przesłaniają tę funkcję członkowską i zapewniają własne implementacje.

##  <a name="calcfixedlayout"></a>CControlBar:: CalcFixedLayout

Wywołaj tę funkcję elementu członkowskiego, aby obliczyć poziomy rozmiar paska sterowania.

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*bStretch*<br/>
Wskazuje, czy pasek ma być rozciągany do rozmiaru ramki. Parametr *bStretch* ma wartość różną od zera, gdy pasek nie jest paskiem dokującym (niedostępnym do dokowania) i ma wartość 0, gdy jest zadokowany lub przestawny (dostępny do dokowania).

*bHorz*<br/>
Wskazuje, że pasek jest poziomy lub pionowo. Parametr *bHorz* jest różny od zera, jeśli pasek jest zorientowany w poziomie i ma wartość 0, jeśli jest zorientowana w pionie.

### <a name="return-value"></a>Wartość zwracana

Rozmiar paska sterowania (w pikselach) obiektu `CSize`.

### <a name="remarks"></a>Uwagi

Paski sterowania, takie jak paski narzędzi, można rozciągnąć w poziomie lub w pionie, aby pomieścić przyciski zawarte na pasku sterowania.

Jeśli *bStretch* ma wartość true, Rozciągaj wymiary na orientację zapewnioną przez *bHorz*. Innymi słowy, jeśli *bHorz* ma wartość false, pasek sterowania jest rozciągany pionowo. Jeśli *bStretch* ma wartość false, nie występuje rozciąganie. W poniższej tabeli przedstawiono możliwe permutacje i wypływające Style pasków kontrolek: *bStretch* i *bHorz*.

|bStretch|bHorz|Rozciąganie|Orientacja|Dokowanie/oddokowywanie|
|--------------|-----------|----------------|-----------------|--------------------------|
|TRUE|TRUE|Rozciąganie w poziomie|Orientacja pozioma|Nie dockowanie|
|TRUE|FAŁSZ|Rozciąganie pionowe|Zorientowane w pionie|Nie dockowanie|
|FAŁSZ|TRUE|Brak dostępnych rozciągnięcia|Orientacja pozioma|Dokowania|
|FAŁSZ|FAŁSZ|Brak dostępnych rozciągnięcia|Zorientowane w pionie|Dokowania|

##  <a name="calcinsiderect"></a>CControlBar:: CalcInsideRect

Struktura wywołuje tę funkcję, aby obliczyć obszar klienta na pasku sterowania.

```
virtual void CalcInsideRect(
    CRect& rect,
    BOOL bHorz) const;
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Zawiera bieżące Wymiary paska sterowania; dołączenie obramowań.

*bHorz*<br/>
Wskazuje, że pasek jest poziomy lub pionowo. Parametr *bHorz* jest różny od zera, jeśli pasek jest zorientowany w poziomie i ma wartość 0, jeśli jest zorientowana w pionie.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przed narysowaniem paska sterowania.

Przesłoń tę funkcję w celu dostosowania renderowania obramowania i paska uchwytu na pasku sterowania.

##  <a name="ccontrolbar"></a>CControlBar:: CControlBar

Konstruuje obiekt `CControlBar`.

```
CControlBar();
```

##  <a name="dopaint"></a>CControlBar::D oPaint

Wywoływane przez platformę, by renderować obramowanie i pasek uchwytu na pasku sterowania.

```
virtual void DoPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obramowań i uchwytu paska sterowania.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować zachowanie rysowania na pasku sterowania.

Inną metodą dostosowywania jest przesłonięcie `DrawBorders` i `DrawGripper` funkcji i dodanie niestandardowego kodu rysowania dla obramowania i uchwytu. Ponieważ te metody są wywoływane przez domyślną metodę `DoPaint`, przesłonięcie `DoPaint` nie jest wymagane.

##  <a name="drawborders"></a>CControlBar::D rawBorders

Wywoływane przez platformę, aby renderować obramowania paska sterowania.

```
virtual void DrawBorders(
    CDC* pDC,
    CRect& rect);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania obramowania paska sterowania.

*cinania*<br/>
Obiekt `CRect` zawierający wymiary paska sterowania.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować wygląd obramowania paska sterowania.

##  <a name="drawgripper"></a>CControlBar::D rawGripper

Wywoływane przez platformę, aby renderować uchwyt paska sterowania.

```
virtual void DrawGripper(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskazuje kontekst urządzenia, który ma być używany do renderowania uchwytu paska formantu.

*cinania*<br/>
Obiekt `CRect` zawierający wymiary uchwytu paska sterowania.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby dostosować wygląd uchwytu paska sterowania.

##  <a name="enabledocking"></a>CControlBar:: EnableDocking

Wywołaj tę funkcję, aby włączyć dokowanie paska sterowania.

```
void EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>Parametry

*dwDockStyle*<br/>
Określa, czy pasek sterowania obsługuje dokowanie i boki okna nadrzędnego, do którego można zadokować pasek sterowania, jeśli jest obsługiwany. Może to być jeden lub więcej z następujących elementów:

- CBRS_ALIGN_TOP umożliwia dokowanie w górnej części obszaru klienckiego.

- CBRS_ALIGN_BOTTOM umożliwia dokowanie w dolnej części obszaru klienckiego.

- CBRS_ALIGN_LEFT umożliwia dokowanie po lewej stronie obszaru klienckiego.

- CBRS_ALIGN_RIGHT umożliwia dokowanie po prawej stronie obszaru klienckiego.

- CBRS_ALIGN_ANY umożliwia dokowanie na każdej stronie obszaru klienckiego.

- CBRS_FLOAT_MULTI umożliwia przestawianie wielu pasków sterowania w jednym oknie mini-frame.

Jeśli 0 (oznacza to, że nie ma flag), pasek sterowania nie zostanie zadokowany.

### <a name="remarks"></a>Uwagi

Określone boki muszą być zgodne z jedną ze stron z włączoną obsługą dokowania w oknie ramki docelowej lub nie można zadokować paska sterowania do tego okna ramki.

##  <a name="getbarstyle"></a>CControlBar:: GetBarStyle

Wywołaj tę funkcję, aby określić, które ustawienia **CBRS_** (style paska sterowania) są obecnie ustawione na pasku sterowania.

```
DWORD GetBarStyle();
```

### <a name="return-value"></a>Wartość zwracana

Bieżące ustawienia **CBRS_** (style paska kontroli) dla paska sterowania. Aby uzyskać pełną listę dostępnych stylów, zobacz [CControlBar:: SetBarStyle](#setbarstyle) .

### <a name="remarks"></a>Uwagi

Nie obsługuje stylów **WS_** (styl okna).

##  <a name="getborders"></a>CControlBar:: GetBorders

Zwraca bieżące wartości obramowania paska sterowania.

```
CRect GetBorders() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `CRect`, który zawiera bieżącą Szerokość (w pikselach) każdej strony obiektu paska sterowania. Na przykład wartość *lewego* elementu członkowskiego obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) jest szerokość lewej krawędzi obramowania.

##  <a name="getcount"></a>CControlBar:: GetCount

Zwraca liczbę elementów niebędących elementem HWND w obiekcie `CControlBar`.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów niebędących HWNDmi w obiekcie `CControlBar`. Ta funkcja zwraca wartość 0 dla obiektu [CDialogBar](../../mfc/reference/cdialogbar-class.md) .

### <a name="remarks"></a>Uwagi

Typ elementu zależy od obiektu pochodnego: okienka dla obiektów [CStatusBar](../../mfc/reference/cstatusbar-class.md) oraz przyciski i separatory dla obiektów [CToolBar](../../mfc/reference/ctoolbar-class.md) .

##  <a name="getdockingframe"></a>CControlBar:: GetDockingFrame

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do bieżącego okna ramki, do którego pasek sterowania jest zadokowany.

```
CFrameWnd* GetDockingFrame() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna ramki, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

Jeśli pasek sterowania nie jest zadokowany do okna ramki (oznacza to, że jeśli pasek sterowania jest przestawny), ta funkcja zwróci wskaźnik do jego elementu nadrzędnego [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat było dokowaćych pasków sterowania, zobacz [CControlBar:: EnableDocking](#enabledocking) i [obiektu CFrameWnd::D ockcontrolbar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).

##  <a name="isfloating"></a>CControlBar:: isfloating

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy pasek sterowania jest przestawny, czy zadokowany.

```
BOOL IsFloating() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli pasek sterowania jest przestawny; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby zmienić stan paska sterowania z zadokowanego na zmiennoprzecinkowe, wywołaj [obiektu CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).

##  <a name="m_bautodelete"></a>CControlBar:: m_bAutoDelete

Jeśli wartość jest niezerowa, obiekt `CControlBar` zostanie usunięty, gdy pasek sterowania systemu Windows zostanie zniszczony.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Uwagi

*m_bAutoDelete* jest publiczną ZMIENNĄ typu bool.

Obiekt paska sterowania jest zwykle osadzony w obiekcie okna ramki. W tym przypadku *m_bAutoDelete* jest równa 0, ponieważ osadzony obiekt paska sterowania jest niszczony, gdy okno ramki jest niszczone.

Ta zmienna jest ustawiana na wartość różną od zera w przypadku przydzielenia obiektu `CControlBar` na stercie i nie planujesz wywoływania metody **delete**.

##  <a name="m_pinplaceowner"></a>CControlBar:: m_pInPlaceOwner

Lokalny właściciel paska sterowania.

```
CWnd* m_pInPlaceOwner;
```

##  <a name="onupdatecmdui"></a>CControlBar:: OnUpdateCmdUI

Ta funkcja członkowska jest wywoływana przez platformę w celu zaktualizowania stanu paska narzędzi lub paska stanu.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler) = 0;
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
Wskazuje główne okno ramek aplikacji. Ten wskaźnik służy do przesyłania komunikatów aktualizacji.

*bDisableIfNoHndler*<br/>
Flaga wskazująca, czy kontrolka, która nie ma procedury obsługi aktualizacji, powinna być automatycznie wyświetlana jako wyłączona.

### <a name="remarks"></a>Uwagi

Aby zaktualizować pojedynczy przycisk lub okienko, użyj makra ON_UPDATE_COMMAND_UI w mapie wiadomości, aby odpowiednio ustawić procedurę obsługi aktualizacji. Aby uzyskać więcej informacji na temat korzystania z tego makra, zobacz [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) .

`OnUpdateCmdUI` jest wywoływana przez platformę, gdy aplikacja jest bezczynna. Okno ramki do zaktualizowania musi być oknem podrzędnym, co najmniej pośrednio, widocznego okna ramki. `OnUpdateCmdUI` jest zaawansowanym zaawansowaniem.

##  <a name="setbarstyle"></a>CControlBar:: SetBarStyle

Wywołaj tę funkcję, aby ustawić odpowiednie style **CBRS_** na pasku sterowania.

```
void SetBarStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Wymagane style na pasku sterowania. Może to być jeden lub więcej z następujących elementów:

- CBRS_ALIGN_TOP umożliwia zadokowanie paska sterowania na górze obszaru klienta okna ramki.

- CBRS_ALIGN_BOTTOM umożliwia zadokowanie paska sterowania do dołu obszaru klienta okna ramki.

- CBRS_ALIGN_LEFT umożliwia zadokowanie paska sterowania po lewej stronie obszaru klienta okna ramki.

- CBRS_ALIGN_RIGHT umożliwia zadokowanie paska sterowania po prawej stronie obszaru klienta okna ramki.

- CBRS_ALIGN_ANY umożliwia zadokowanie paska sterowania do dowolnej strony w obszarze klienta okna ramki.

- CBRS_BORDER_TOP powoduje, że obramowanie ma być rysowane na górnej krawędzi paska sterowania, gdy będzie widoczne.

- CBRS_BORDER_BOTTOM powoduje, że obramowanie ma być rysowane na dolnej krawędzi paska sterowania, gdy będzie widoczne.

- CBRS_BORDER_LEFT powoduje, że obramowanie ma być rysowane na lewej krawędzi paska sterowania, gdy będzie widoczne.

- CBRS_BORDER_RIGHT powoduje, że obramowanie ma być rysowane na prawej krawędzi paska sterowania, gdy będzie widoczne.

- CBRS_FLOAT_MULTI umożliwia przestawianie wielu pasków sterowania w jednym oknie mini-frame.

- CBRS_TOOLTIPS powoduje, że etykietki narzędzi są wyświetlane na pasku sterowania.

- CBRS_FLYBY powoduje, że tekst komunikatu będzie aktualizowany w tym samym czasie co etykietki narzędzi.

- CBRS_GRIPPER powoduje, że uchwyt jest podobny do tego, który jest używany na pasmach w obiekcie `CReBar`, do rysowania dla każdej klasy pochodnej `CControlBar`.

### <a name="remarks"></a>Uwagi

Nie ma wpływu na ustawienia **WS_** (styl okna).

##  <a name="setborders"></a>CControlBar:: setborderers

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
Wysokość (w pikselach) górnego obramowania paska sterowania.

*cxRight*<br/>
Szerokość (w pikselach) prawej krawędzi paska sterowania.

*cyBottom*<br/>
Wysokość (w pikselach) dolnego obramowania paska sterowania.

*lpRect*<br/>
Wskaźnik do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) , który zawiera bieżącą Szerokość (w pikselach) każdego obramowania obiektu paska sterowania.

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia górne i dolne obramowanie paska sterowania do 5 pikseli, a lewe i prawe obramowanie do 2 pikseli:

[!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]

##  <a name="setinplaceowner"></a>CControlBar:: SetInPlaceOwner

Zmienia lokalnego właściciela paska sterowania.

```
void SetInPlaceOwner(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do obiektu `CWnd`.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Przykład CTRLBARS MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)<br/>
[Klasa CDialogBar](../../mfc/reference/cdialogbar-class.md)<br/>
[Klasa CStatusBar](../../mfc/reference/cstatusbar-class.md)<br/>
[Klasa CReBar](../../mfc/reference/crebar-class.md)
