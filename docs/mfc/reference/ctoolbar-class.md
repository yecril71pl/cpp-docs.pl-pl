---
title: Klasa CToolBar
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752208"
---
# <a name="ctoolbar-class"></a>Klasa CToolBar

Paski sterowania, które mają rząd przycisków bitmapowych i opcjonalnych separatorów.

## <a name="syntax"></a>Składnia

```
class CToolBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|Konstruuje `CToolBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|Zwraca indeks przycisku o podanym identyfikatorze polecenia.|
|[CToolBar::Tworzenie](#create)|Tworzy pasek narzędzi systemu Windows i `CToolBar` dołącza go do obiektu.|
|[CToolBar::CreateEx](#createex)|Tworzy `CToolBar` obiekt z dodatkowymi stylami dla `CToolBarCtrl` obiektu osadzonego.|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Pobiera identyfikator, styl i numer obrazu przycisku.|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Pobiera styl przycisku.|
|[CToolBar::GetButtonText](#getbuttontext)|Pobiera tekst, który pojawi się na przycisku.|
|[CToolBar::GetItemID](#getitemid)|Zwraca identyfikator polecenia przycisku lub separatora w danym indeksie.|
|[CToolBar::GetItemRect](#getitemrect)|Pobiera prostokąt wyświetlania elementu w danym indeksie.|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.|
|[CToolBar::LoadBitmap](#loadbitmap)|Ładuje mapę bitową zawierającą obrazy przycisków bitmapy.|
|[CToolBar::LoadToolBar](#loadtoolbar)|Ładuje zasób paska narzędzi utworzony za pomocą edytora zasobów.|
|[CToolBar::SetBitmap](#setbitmap)|Ustawia obraz bitmapowy.|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Ustawia identyfikator, styl i numer obrazu przycisku.|
|[CToolBar::SetButtons](#setbuttons)|Ustawia style przycisków i indeks obrazów przycisków w mapie bitowej.|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Ustawia styl przycisku.|
|[CToolBar::SetButtonText](#setbuttontext)|Ustawia tekst, który pojawi się na przycisku.|
|[CToolBar::SetHeight](#setheight)|Ustawia wysokość paska narzędzi.|
|[CToolBar::SetSizes](#setsizes)|Ustawia rozmiary przycisków i ich bitmap.|

## <a name="remarks"></a>Uwagi

Przyciski mogą działać jak przyciski, przyciski pola wyboru lub przyciski radiowe. `CToolBar`obiekty są zazwyczaj osadzone elementy członkowskie obiektów okna ramki pochodzące z klasy [CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).

[CToolBar::GetToolBarCtrl](#gettoolbarctrl), funkcja elementu członkowskiego nowy mfc 4.0, pozwala na skorzystanie z obsługi wspólnego formantu systemu Windows dla dostosowywania paska narzędzi i dodatkowych funkcji. `CToolBar`funkcje członkowskie zapewniają większość funkcji typowych formantów systemu Windows; Jednak podczas połączenia `GetToolBarCtrl`można nadać pasom narzędzi jeszcze więcej cech pasków narzędzi systemu Windows 95/98. Po wywołaniu `GetToolBarCtrl`, zwróci odwołanie `CToolBarCtrl` do obiektu. Zobacz [CToolBarCtrl aby](../../mfc/reference/ctoolbarctrl-class.md) uzyskać więcej informacji na temat projektowania pasków narzędzi przy użyciu typowych formantów systemu Windows. Aby uzyskać bardziej ogólne informacje na temat typowych formantów, zobacz [Typowe formanty](/windows/win32/Controls/common-controls-intro) w sdk systemu Windows.

Visual C++ zapewnia dwie metody tworzenia paska narzędzi. Aby utworzyć zasób paska narzędzi za pomocą Edytora zasobów, wykonaj następujące kroki:

1. Tworzenie zasobu paska narzędzi.

1. Konstruuj `CToolBar` obiekt.

1. Wywołanie funkcji [Utwórz](#create) (lub [CreateEx),](#createex)aby utworzyć pasek `CToolBar` narzędzi systemu Windows i dołączyć go do obiektu.

1. Wywołanie [LoadToolBar](#loadtoolbar) załadować zasób paska narzędzi.

Jeśli nie, wykonaj następujące kroki:

1. Konstruuj `CToolBar` obiekt.

1. Wywołanie funkcji [Utwórz](#create) (lub [CreateEx),](#createex)aby utworzyć pasek `CToolBar` narzędzi systemu Windows i dołączyć go do obiektu.

1. Wywołanie [LoadBitmap](#loadbitmap) załadować bitmapę zawierającą obrazy przycisków paska narzędzi.

1. Wywołaj [przyciski SetButtons,](#setbuttons) aby ustawić styl przycisku i skojarzyć każdy przycisk z obrazem w mapie bitowej.

Wszystkie obrazy przycisków na pasku narzędzi są pobierane z jednej mapy bitowej, która musi zawierać jeden obraz dla każdego przycisku. Wszystkie obrazy muszą mieć ten sam rozmiar; wartość domyślna to 16 pikseli szerokości i 15 pikseli wysokości. Obrazy muszą być obok siebie na mapie bitowej.

Funkcja `SetButtons` przenosi wskaźnik do tablicy identyfikatorów kontroli i liczby całkowitej, która określa liczbę elementów w tablicy. Funkcja ustawia identyfikator każdego przycisku na wartość odpowiedniego elementu tablicy i przypisuje każdemu przyciskowi indeks obrazu, który określa położenie obrazu przycisku w mapie bitowej. Jeśli element tablicy ma wartość ID_SEPARATOR, nie jest przypisany indeks obrazu.

Kolejność obrazów w mapie bitowej jest zazwyczaj kolejność, w jakiej są rysowane na ekranie, ale można użyć [Funkcji SetButtonInfo,](#setbuttoninfo) aby zmienić relację między kolejnością obrazu a kolejnością rysowania.

Wszystkie przyciski na pasku narzędzi mają ten sam rozmiar. Wartość domyślna to 24 x 22 piksele, zgodnie z *wytycznymi dotyczącymi interfejsu systemu Windows dotyczącymi projektowania oprogramowania.* Wszelkie dodatkowe odstępy między wymiarami obrazu i przycisku są używane do tworzenia obramowania wokół obrazu.

Każdy przycisk ma jeden obraz. Różne stany i style przycisków (wciśnięty, w górę, w dół, wyłączone, wyłączone w dół i nieokreślony) są generowane z tego jednego obrazu. Chociaż mapy bitowe mogą być dowolnym kolorem, można osiągnąć najlepsze wyniki z obrazami w kolorze czarnym i odcieniami szarości.

> [!WARNING]
> `CToolBar`obsługuje mapy bitowe z maksymalnie 16 kolorami. Po załadowaniu obrazu do edytora paska narzędzi program Visual Studio automatycznie konwertuje obraz na 16-kolorową mapę bitową, jeśli to konieczne, i wyświetla komunikat ostrzegawczy, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (za pomocą zewnętrznego edytora do edycji obrazu), aplikacja może zachowywać się nieoczekiwanie.

Przyciski paska narzędzi domyślnie imitują przyciski. Jednak przyciski paska narzędzi mogą również naśladować przyciski pola wyboru lub przyciski radiowe. Przyciski pola wyboru mają trzy stany: zaznaczone, wyczyszczone i nieokreślone. Przyciski radiowe mają tylko dwa stany: sprawdzone i wyczyszczone.

Aby ustawić indywidualny styl przycisku lub separatora bez wskazywania tablicy, należy wywołać [getbuttonStyle,](#getbuttonstyle) `SetButtons`aby pobrać styl, a następnie wywołać [SetButtonStyle](#setbuttonstyle) zamiast . `SetButtonStyle`jest najbardziej przydatna, gdy chcesz zmienić styl przycisku w czasie wykonywania.

Aby przypisać tekst do wyświetlenia przycisku, zadzwoń do [GetButtonText,](#getbuttontext) aby pobrać tekst, który pojawi się na przycisku, a następnie zadzwoń do [SetButtonText,](#setbuttontext) aby ustawić tekst.

Aby utworzyć przycisk pola wyboru, przypisz mu styl TBBS_CHECKBOX `CCmdUI` lub `SetCheck` użyj funkcji elementu członkowskiego obiektu w programie obsługi ON_UPDATE_COMMAND_UI. Wywołanie `SetCheck` zamienia przycisk w przycisk pola wyboru. Przekaż `SetCheck` argument 0 dla niezaznaczonych, 1 dla sprawdzonych lub 2 dla nieokreślony.

Aby utworzyć przycisk radiowy, wywołaj funkcję elementu członkowskiego [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) obiektu [CCmdUI](../../mfc/reference/ccmdui-class.md) z obsługi ON_UPDATE_COMMAND_UI. Przekaż `SetRadio` argument 0 dla niezaznaczone lub niezerowe dla zaznaczone. Aby zapewnić wzajemnie wykluczające się zachowanie grupy radiowej, musisz mieć ON_UPDATE_COMMAND_UI programy obsługi dla wszystkich przycisków w grupie.

Aby uzyskać więcej `CToolBar`informacji na temat używania , zobacz artykuł [Implementacja paska narzędzi MFC](../../mfc/mfc-toolbar-implementation.md) i [uwaga techniczna 31: Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex

Ta funkcja elementu członkowskiego zwraca indeks pierwszego przycisku paska narzędzi, zaczynając od pozycji 0, której identyfikator polecenia odpowiada `nIDFind`.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDZnajduj*<br/>
Identyfikator polecenia przycisku paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Indeks przycisku lub -1, jeśli żaden przycisk nie ma podanego identyfikatora polecenia.

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar::Tworzenie

Ta funkcja elementu członkowskiego tworzy pasek narzędzi systemu Windows (okno podrzędne) i kojarzy go z obiektem. `CToolBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym paska narzędzi.

*Dwstyle*<br/>
Styl paska narzędzi. Dodatkowe obsługiwane style paska narzędzi to:

- CBRS_TOP pasek sterowania znajduje się w górnej części okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się w dolnej części okna ramki.

- CBRS_NOALIGN pasek sterowania nie jest zmieniany po zmianie jego zmiany.

- CBRS_TOOLTIPS pasek sterowania wyświetla wskazówki dotyczące narzędzi.

- CBRS_SIZE_DYNAMIC pasek sterowania jest dynamiczny.

- CBRS_SIZE_FIXED pasek sterowania jest stały.

- CBRS_FLOATING pasek sterowania jest zmienny.

- CBRS_FLYBY pasek stanu wyświetla informacje o przycisku.

- CBRS_HIDE_INPLACE pasek sterowania nie jest wyświetlany użytkownikowi.

*Nid*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar::CreateEx

Wywołanie tej funkcji, aby utworzyć pasek narzędzi systemu Windows `CToolBar` (okno podrzędne) i skojarzyć go z obiektem.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym paska narzędzi.

*dwCtrlStyle*<br/>
Dodatkowe style do tworzenia osadzonego [obiektu CToolBarCtrl.](../../mfc/reference/ctoolbarctrl-class.md) Domyślnie ta wartość jest ustawiona na TBSTYLE_FLAT. Aby uzyskać pełną listę stylów paska narzędzi, zobacz *dwStyle*.

*Dwstyle*<br/>
Styl paska narzędzi. Zobacz [Formant paska narzędzi i Style przycisków](/windows/win32/Controls/toolbar-control-and-button-styles) w zestawie Windows SDK, aby uzyskać listę odpowiednich stylów.

*rcBorders*<br/>
Obiekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) który definiuje szerokości obramowań paska narzędzi. Te obramowania są domyślnie ustawione na 0,0,0,0, co powoduje, że okno paska narzędzi bez obramowań.

*Nid*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również wysokość paska narzędzi na wartość domyślną.

Użyj `CreateEx`zamiast [Create](#create), gdy niektóre style muszą być obecne podczas tworzenia osadzonego paska narzędzi. Na przykład ustaw *dwCtrlStyle,* aby TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT, aby utworzyć pasek narzędzi przypominający paski narzędzi programu Internet Explorer 4.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar::CToolBar

Ta funkcja elementu `CToolBar` członkowskiego konstruuje obiekt i ustawia domyślne rozmiary.

```
CToolBar();
```

### <a name="remarks"></a>Uwagi

Wywołanie funkcji [Utwórz](#create) element członkowski, aby utworzyć okno paska narzędzi.

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar::GetButtonInfo

Ta funkcja elementu członkowskiego pobiera identyfikator formantu, styl i indeks obrazu przycisku lub separatora paska narzędzi w lokalizacji określonej przez *nIndex.*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks przycisku paska narzędzi lub separatora, którego informacje mają zostać pobrane.

*Nid*<br/>
Odwołanie do UINT, który jest ustawiony na identyfikator polecenia przycisku.

*styl nStyle*<br/>
Odwołanie do UINT, który jest ustawiony na styl przycisku.

*Iimage*<br/>
Odwołanie do liczby całkowitej, która jest ustawiona na indeks obrazu przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

Te wartości są przypisywane do zmiennych, do których się odwołuje *nID*, *nStyle*i *iImage*. Indeks obrazu jest położeniem obrazu w ujmijce w mapie bitowej zawierającej obrazy dla wszystkich przycisków paska narzędzi. Pierwszy obraz znajduje się na pozycji 0.

Jeśli *nIndex* określa separator, *iImage* jest ustawiony na szerokość separatora w pikselach.

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar::GetButtonStyle

Wywołanie tej funkcji elementu członkowskiego, aby pobrać styl przycisku lub separatora na pasku narzędzi.

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks przycisku paska narzędzi lub stylu separatora do pobrania.

### <a name="return-value"></a>Wartość zwracana

Styl przycisku lub separatora określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl przycisku określa, jak przycisk jest wyświetlany i jak reaguje na dane wejściowe użytkownika. Zobacz [SetButtonStyle](#setbuttonstyle) przykłady stylów przycisków.

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar::GetButtonText

Wywołanie tej funkcji elementu członkowskiego, aby pobrać tekst, który pojawia się na przycisku.

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks tekstu do pobrania.

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu, który będzie zawierał tekst do pobrania.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający tekst przycisku.

### <a name="remarks"></a>Uwagi

Drugi formularz tej funkcji elementu `CString` członkowskiego wypełnia obiekt tekstem ciągu.

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID

Ta funkcja elementu członkowskiego zwraca identyfikator polecenia przycisku lub separatora określonego przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks elementu, którego identyfikator ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia przycisku lub separatora określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Separatory zwracają ID_SEPARATOR.

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect

Ta funkcja elementu `RECT` członkowskiego wypełnia strukturę, której adres jest zawarty w *lpRect* współrzędnymi przycisku lub separatora określonego przez *nIndex*.

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks elementu (przycisku lub separatora), którego współrzędne prostokąta mają zostać pobrane.

*Lprect*<br/>
Adres struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która będzie zawierać współrzędne elementu.

### <a name="remarks"></a>Uwagi

Współrzędne znajdują się w pikselach względem lewego górnego rogu paska narzędzi.

Służy `GetItemRect` do pobierania współrzędnych separatora, który ma zostać zamieniona na pole kombi lub inne formantu.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::SetSizes](#setsizes).

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl

Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `CToolBarCtrl` obiektu.

### <a name="remarks"></a>Uwagi

Służy `GetToolBarCtrl` do korzystania z funkcji wspólnego formantu paska narzędzi systemu Windows i skorzystania z pomocy technicznej [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) zapewnia dostosowywanie paska narzędzi.

Aby uzyskać więcej informacji na temat używania typowych formantów, zobacz artykuł [Formanty](../../mfc/controls-mfc.md) i [typowe formanty](/windows/win32/Controls/common-controls-intro) w sdk systemu Windows.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap

Wywołanie tej funkcji elementu członkowskiego, `lpszResourceName` `nIDResource`aby załadować mapę bitową określoną przez lub .

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik do nazwy zasobu mapy bitowej, która ma zostać załadowana.

*nIDSerwród*<br/>
Identyfikator zasobu mapy bitowej, która ma zostać załadowana.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Mapa bitowa powinna zawierać jeden obraz dla każdego przycisku paska narzędzi. Jeśli obrazy nie mają standardowego rozmiaru (16 pikseli szerokości i 15 pikseli wysokości), [wywołaj setSizes,](#setsizes) aby ustawić rozmiary przycisków i ich obrazy.

> [!WARNING]
> `CToolBar`obsługuje mapy bitowe z maksymalnie 16 kolorami. Po załadowaniu obrazu do edytora paska narzędzi program Visual Studio automatycznie konwertuje obraz na 16-kolorową mapę bitową, jeśli to konieczne, i wyświetla komunikat ostrzegawczy, jeśli obraz został przekonwertowany. Jeśli używasz obrazu z więcej niż 16 kolorów (za pomocą zewnętrznego edytora do edycji obrazu), aplikacja może zachowywać się nieoczekiwanie.

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar

Wywołanie tej funkcji elementu członkowskiego w celu załadowania paska narzędzi określonego przez *lpszResourceName* lub *nIDResource*.

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>Parametry

*lpszResourceName*<br/>
Wskaźnik do nazwy zasobu paska narzędzi, który ma zostać załadowany.

*nIDSerwród*<br/>
Identyfikator zasobu paska narzędzi, który ma zostać załadowany.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tworzenia zasobu paska narzędzi, zobacz [edytor paska narzędzi.](../../windows/toolbar-editor.md)

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::CreateEx](#createex).

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap

Wywołanie tej funkcji elementu członkowskiego, aby ustawić obraz mapy bitowej dla paska narzędzi.

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>Parametry

*hbmImageWell*<br/>
Obsługa obrazu mapy bitowej skojarzonego z paskiem narzędzi.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Na przykład `SetBitmap` wywołanie zmiany obrazu bitmapowego po użytkownik podejmie akcję w dokumencie, która zmienia akcję przycisku.

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar::SetButtonInfo

Wywołanie tej funkcji elementu członkowskiego w celu skonfigurowania identyfikatora polecenia przycisku, stylu i numeru obrazu.

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera przycisku lub separatora, dla którego mają być ustawione informacje.

*Nid*<br/>
Wartość, do której jest ustawiona identyfikator polecenia przycisku.

*styl nStyle*<br/>
Nowy styl przycisku. Obsługiwane są następujące style przycisków:

- TBBS_BUTTON Standardowy przycisk (domyślnie)

- TBBS_SEPARATOR Separator

- Przycisk pola wyboru auto TBBS_CHECKBOX

- TBBS_GROUP Oznacza początek grupy przycisków

- TBBS_CHECKGROUP Oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN Tworzy przycisk listy rozwijanej.

- TBBS_AUTOSIZE Szerokość przycisku zostanie obliczona na podstawie tekstu przycisku, a nie na rozmiarze obrazu.

- TBBS_NOPREFIX Tekst przycisku nie będzie miał skojarzonego z nim prefiksu akceleratora.

*Iimage*<br/>
Nowy indeks obrazu przycisku w mapie bitowej.

### <a name="remarks"></a>Uwagi

W przypadku separatorów, które mają styl TBBS_SEPARATOR, ta funkcja ustawia szerokość separatora w pikselach na wartość przechowywaną w *iImage*.

> [!NOTE]
> Można również ustawić stany przycisków za pomocą parametru *nStyle;* jednak ponieważ stany przycisków są kontrolowane przez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obsługi, `SetButtonInfo` każdy stan, który można ustawić przy użyciu zostaną utracone podczas następnego przetwarzania bezczynnego. Zobacz [Jak zaktualizować obiekty interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski sterowania,](../../mfc/tn031-control-bars.md) aby uzyskać więcej informacji.

Aby uzyskać informacje na temat obrazów i przycisków bitmapowych, zobacz [CToolBar](../../mfc/reference/ctoolbar-class.md) Overview i [CToolBar::LoadBitmap](#loadbitmap).

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::SetButtons

Ta funkcja elementu członkowskiego ustawia identyfikator polecenia każdego przycisku paska narzędzi na wartość określoną przez odpowiedni element tablicy *lpIDArray*.

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray (lpIDArray)*<br/>
Wskaźnik do tablicy identyfikatorów poleceń. Może być null przydzielić puste przyciski.

*nIDCount (liczba NIDCount)*<br/>
Liczba elementów w tablicy wskazywionej przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli element tablicy ma wartość ID_SEPARATOR, separator jest tworzony w odpowiedniej pozycji paska narzędzi. Ta funkcja ustawia również styl każdego przycisku, aby TBBS_BUTTON i styl każdego separatora TBBS_SEPARATOR i przypisuje indeks obrazu do każdego przycisku. Indeks obrazu określa położenie obrazu przycisku w mapie bitowej.

Nie trzeba uwzględniać separatorów w mapie bitowej, ponieważ ta funkcja nie przypisuje indeksów obrazów dla separatorów. Jeśli pasek narzędzi ma przyciski w pozycjach 0, 1 i 3 oraz separator w pozycji 2, obrazy w pozycjach 0, 1 i 2 na mapie bitowej są przypisywane do przycisków odpowiednio w pozycjach 0, 1 i 3.

Jeśli *lpIDArray* ma wartość NULL, ta funkcja przydziela miejsce dla liczby elementów określonych przez *nIDCount*. Użyj [SetButtonInfo,](#setbuttoninfo) aby ustawić atrybuty każdego elementu.

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle

Wywołanie tej funkcji elementu członkowskiego, aby ustawić styl przycisku lub separatora lub przycisków grupy.

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks przycisku lub separatora, którego informacje mają być ustawione.

*styl nStyle*<br/>
Styl przycisku. Obsługiwane są następujące style przycisków:

- TBBS_BUTTON Standardowy przycisk (domyślnie)

- TBBS_SEPARATOR Separator

- Przycisk pola wyboru auto TBBS_CHECKBOX

- TBBS_GROUP Oznacza początek grupy przycisków

- TBBS_CHECKGROUP Oznacza początek grupy przycisków pola wyboru

- TBBS_DROPDOWN Tworzy przycisk listy rozwijanej

- TBBS_AUTOSIZE Szerokość przycisku zostanie obliczona na podstawie tekstu przycisku, a nie na rozmiarze obrazu

- TBBS_NOPREFIX Tekst przycisku nie będzie miał skojarzonego z nim prefiksu akceleratora

### <a name="remarks"></a>Uwagi

Styl przycisku określa, jak przycisk jest wyświetlany i jak reaguje na dane wejściowe użytkownika.

Przed `SetButtonStyle`wywołaniem wywołaj funkcję elementu członkowskiego [GetButtonStyle,](#getbuttonstyle) aby pobrać styl przycisku lub separatora.

> [!NOTE]
> Można również ustawić stany przycisków za pomocą parametru *nStyle;* jednak ponieważ stany przycisków są kontrolowane przez [ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui) obsługi, `SetButtonStyle` każdy stan, który można ustawić przy użyciu zostaną utracone podczas następnego przetwarzania bezczynnego. Zobacz [Jak zaktualizować obiekty interfejsu użytkownika](../../mfc/how-to-update-user-interface-objects.md) i [TN031: Paski sterowania,](../../mfc/tn031-control-bars.md) aby uzyskać więcej informacji.

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText

Wywołanie tej funkcji, aby ustawić tekst na przycisku.

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks przycisku, którego tekst ma być ustawiony.

*lpszText (tekst)*<br/>
Wskazuje tekst, który ma być ustawiony na przycisku.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CToolBar::GetToolBarCtrl](#gettoolbarctrl).

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight

Ta funkcja elementu członkowskiego ustawia wysokość paska narzędzi na wartość w pikselach określoną w *cyHeight*.

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>Parametry

*cyHeight (cyHeight)*<br/>
Wysokość w pikselach paska narzędzi.

### <a name="remarks"></a>Uwagi

Po wywołaniu [SetSizes](#setsizes)użyj tej funkcji elementu członkowskiego, aby zastąpić standardową wysokość paska narzędzi. Jeśli wysokość jest zbyt mała, przyciski zostaną przycięte na dole.

Jeśli ta funkcja nie jest wywoływana, struktura używa rozmiaru przycisku, aby określić wysokość paska narzędzi.

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes

Wywołanie tej funkcji elementu członkowskiego, aby ustawić przyciski paska narzędzi do rozmiaru, w pikselach, określone w *sizeButton*.

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>Parametry

*rozmiarButton*<br/>
Rozmiar w pikselach każdego przycisku.

*rozmiarImage*<br/>
Rozmiar w pikselach każdego obrazu.

### <a name="remarks"></a>Uwagi

*SizeImage* parametr musi zawierać rozmiar, w pikselach, obrazów w pasku narzędzi bitmapowych. Wymiary w *rozmiarzeButton* musi być wystarczająca do przechowywania obrazu plus 7 pikseli dodatkowej szerokości i 6 pikseli dodatkowych wysokości. Ta funkcja ustawia również wysokość paska narzędzi tak, aby pasowała do przycisków.

Wywołanie tej funkcji elementu członkowskiego tylko dla pasków narzędzi, które nie są zgodne z wytycznymi interfejsu systemu Windows dla zaleceń *dotyczących projektowania oprogramowania* dla rozmiarów przycisków i obrazów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Przykładowy DOCKTOOL MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
