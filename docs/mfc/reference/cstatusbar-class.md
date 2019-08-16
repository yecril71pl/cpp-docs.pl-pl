---
title: Klasa CStatusBar
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 48de31d95814ce5fc1fb015e69cf38d73337cb79
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502339"
---
# <a name="cstatusbar-class"></a>Klasa CStatusBar

Pasek sterowania z wierszem okienka tekstu wyjściowego lub "wskaźniki".

## <a name="syntax"></a>Składnia

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar:: CStatusBar](#cstatusbar)|Konstruuje `CStatusBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar:: CommandToIndex](#commandtoindex)|Pobiera indeks dla danego identyfikatora wskaźnika.|
|[CStatusBar:: Create](#create)|Tworzy pasek stanu, dołącza go do `CStatusBar` obiektu i ustawia początkową czcionkę i wysokość paska.|
|[CStatusBar:: CreateEx](#createex)|Tworzy obiekt z dodatkowymi stylami dla osadzonego `CStatusBarCtrl` obiektu. `CStatusBar`|
|[CStatusBar::D rawItem](#drawitem)|Wywołuje się, gdy wizualny aspekt kontrolki paska stanu rysowania przez właściciela jest zmieniany.|
|[CStatusBar:: GetItemID](#getitemid)|Pobiera identyfikator wskaźnika dla danego indeksu.|
|[CStatusBar:: GetItemRect](#getitemrect)|Pobiera prostokąt wyświetlania dla danego indeksu.|
|[CStatusBar:: GetPaneInfo](#getpaneinfo)|Pobiera identyfikator, styl i szerokość wskaźnika dla danego indeksu.|
|[CStatusBar:: getokienks](#getpanestyle)|Pobiera styl wskaźnika dla danego indeksu.|
|[CStatusBar:: GetPaneText](#getpanetext)|Pobiera tekst wskaźnika dla danego indeksu.|
|[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl)|Zezwala na bezpośredni dostęp do podstawowej kontroli wspólnej.|
|[CStatusBar:: setwskaźniks](#setindicators)|Ustawia identyfikatory wskaźnika.|
|[CStatusBar:: SetPaneInfo](#setpaneinfo)|Ustawia identyfikator, styl i szerokość wskaźnika dla danego indeksu.|
|[CStatusBar:: setokienks](#setpanestyle)|Ustawia styl wskaźnika dla danego indeksu.|
|[CStatusBar:: SetPaneText](#setpanetext)|Ustawia tekst wskaźnika dla danego indeksu.|

## <a name="remarks"></a>Uwagi

Okienka danych wyjściowych są zwykle używane jako wiersze komunikatów i jako wskaźniki stanu. Przykłady obejmują menu Pomoc — wiersze komunikatów, które krótko objaśniają wybrane polecenie menu i wskaźniki pokazujące stan blokady przewijania, NUM LOCK i innych kluczy.

[CStatusBar:: GetStatusBarCtrl](#getstatusbarctrl), funkcja członkowska New to MFC 4,0, umożliwia korzystanie z pomocy technicznej programu Windows Common Control do dostosowywania paska stanu i dodatkowych funkcji. `CStatusBar`funkcje składowe zapewniają większość funkcji formantów standardowych systemu Windows; Jednak po wywołaniu `GetStatusBarCtrl`programu można dać paski stanu jeszcze większą charakterystykę paska stanu systemu Windows 95/98. Po wywołaniu `GetStatusBarCtrl`, zwróci odwołanie `CStatusBarCtrl` do obiektu. Zobacz [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) , aby uzyskać więcej informacji na temat projektowania pasków narzędzi przy użyciu standardowych formantów systemu Windows. Aby uzyskać więcej ogólnych informacji na temat typowych kontrolek, zobacz [typowe kontrolki](/windows/win32/Controls/common-controls-intro) w Windows SDK.

Struktura przechowuje informacje o wskaźniku w tablicy z lewym wskaźnikiem na pozycji 0. Podczas tworzenia paska stanu należy użyć tablicy identyfikatorów ciągów, które struktura kojarzy z odpowiednimi wskaźnikami. Następnie można użyć identyfikatora ciągu lub indeksu, aby uzyskać dostęp do wskaźnika.

Domyślnie pierwszy wskaźnik jest "elastyczny": przyjmuje długość paska stanu, która nie jest używana przez pozostałe okienka wskaźnika, dzięki czemu pozostałe okienka są wyrównane do prawej.

Aby utworzyć pasek stanu, wykonaj następujące kroki:

1. Konstruowanie `CStatusBar` obiektu.

1. Wywołaj funkcję [Create](#create) (lub [CreateEx](#createex)), aby utworzyć okno pasek stanu i dołączyć `CStatusBar` je do obiektu.

1. Wywołaj metodę setwskaźniks, aby skojarzyć identyfikator ciągu z każdym wskaźnikiem. [](#setindicators)

Istnieją trzy sposoby aktualizowania tekstu w okienku paska stanu:

1. Wywołaj metodę [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) w celu zaktualizowania tekstu tylko w okienku 0.

1. Wywołanie [CCmdUI:: SetText](../../mfc/reference/ccmdui-class.md#settext) w OBsłudze ON_UPDATE_COMMAND_UI na pasku stanu.

1. Wywołaj [SetPaneText](#setpanetext) w celu zaktualizowania tekstu w dowolnym okienku.

Wywołanie [](#setpanestyle) metody setokienks w celu zaktualizowania stylu okienka paska stanu.

Aby uzyskać więcej informacji na `CStatusBar`temat korzystania z programu, zobacz artykuł [implementacja paska stanu artykułu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [Uwaga techniczna 31: Paski](../../mfc/tn031-control-bars.md)sterowania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

##  <a name="commandtoindex"></a>CStatusBar:: CommandToIndex

Pobiera indeks wskaźnika dla danego identyfikatora.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
Identyfikator ciągu wskaźnika, którego indeks ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Indeks wskaźnika w przypadku powodzenia; -1, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Indeks pierwszego wskaźnika to 0.

##  <a name="create"></a>CStatusBar:: Create

Tworzy pasek stanu (okno podrzędne) i kojarzy go z `CStatusBar` obiektem.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , którego okno systemu Windows jest elementem nadrzędnym paska stanu.

*dwStyle*<br/>
Styl paska stanu. Oprócz standardowych [stylów](../../mfc/reference/styles-used-by-mfc.md#window-styles)systemu Windows, te style są obsługiwane.

- CBRS_TOP pasek sterowania znajduje się w górnej części okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się u dołu okna ramowego.

- Po zmianie rozmiaru elementu nadrzędnego CBRS_NOALIGN pasek sterowania nie jest zmieniany.

*nID*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również czcionkę początkową i ustawia wysokość paska stanu na wartość domyślną.

##  <a name="createex"></a>CStatusBar:: CreateEx

Wywołaj tę funkcję, aby utworzyć pasek stanu (okno podrzędne) i skojarzyć go z `CStatusBar` obiektem.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , którego okno systemu Windows jest elementem nadrzędnym paska stanu.

*dwCtrlStyle*<br/>
Dodatkowe style tworzenia osadzonego obiektu [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) . Wartość domyślna określa pasek stanu bez uchwytu zmiany wielkości lub etykietki narzędzia. Obsługiwane są style paska stanu:

- SBARS_SIZEGRIP formant pasek stanu zawiera uchwyt zmiany wielkości na prawym końcu paska stanu. Uchwyt zmiany wielkości jest podobny do obramowania zmieniającego rozmiar; jest to prostokątny obszar, który użytkownik może kliknąć i przeciągnąć, aby zmienić rozmiar okna nadrzędnego.

- SBT_TOOLTIPS pasek stanu obsługuje etykietki narzędzi.

Aby uzyskać szczegółowe informacje na temat tych stylów, zobacz [Ustawienia dla CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Styl paska stanu. Wartość domyślna określa, że widoczny pasek stanu zostanie utworzony u dołu okna ramki. Zastosuj dowolną kombinację stylów kontrolki pasek stanu na liście [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CDialogBar:: Create](../../mfc/reference/cdialogbar-class.md#create). Jednak ten parametr powinien zawsze zawierać style WS_CHILD i WS_VISIBLE.

*nID*<br/>
Identyfikator okna podrzędnego paska stanu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia również czcionkę początkową i ustawia wysokość paska stanu na wartość domyślną.

Użyj `CreateEx`zamiast [tworzenia](#create), gdy pewne style muszą być obecne podczas tworzenia osadzonej kontrolki pasek stanu. Na przykład ustaw *dwCtrlStyle* na SBT_TOOLTIPS, aby wyświetlić etykietki narzędzi w obiekcie paska stanu.

##  <a name="cstatusbar"></a>CStatusBar:: CStatusBar

Konstruuje `CStatusBar` obiekt, w razie potrzeby tworzy domyślną czcionkę paska stanu i ustawia właściwości czcionki na wartości domyślne.

```
CStatusBar();
```

##  <a name="drawitem"></a>CStatusBar::D rawItem

Ta funkcja członkowska jest wywoływana przez platformę, gdy zmieni się wizualny pasek stanu rysowany przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , który zawiera informacje o wymaganym typie rysunku.

### <a name="remarks"></a>Uwagi

`itemAction` Element członkowski`DRAWITEMSTRUCT` struktury definiuje akcję rysowania, która ma zostać wykonana. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla `CStatusBar` obiektu rysowania przez właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

##  <a name="getitemid"></a>CStatusBar:: GetItemID

Zwraca identyfikator wskaźnika określonego przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wskaźnika, którego identyfikator ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Identyfikator wskaźnika określony przez *nIndex*.

##  <a name="getitemrect"></a>CStatusBar:: GetItemRect

Kopiuje współrzędne wskaźnika określonego przez *nIndex* do struktury wskazywanej przez *lpRect*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wskaźnika, którego współrzędne prostokątów mają zostać pobrane.

*lpRect*<br/>
Wskazuje strukturę [Rect](/previous-versions/dd162897\(v=vs.85\)) lub obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , który będzie otrzymywać współrzędne wskaźnika określonego przez *nIndex*.

### <a name="remarks"></a>Uwagi

Współrzędne są w pikselach względem lewego górnego rogu paska stanu.

##  <a name="getpaneinfo"></a>CStatusBar:: GetPaneInfo

Ustawia *NID*, *nStyle*i *cxWidth* do identyfikatora, stylu i szerokości okienka wskaźnika w lokalizacji określonej przez *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, którego informacje mają zostać pobrane.

*nID*<br/>
Odwołanie do typu UINT, który jest ustawiony na identyfikator okienka.

*nStyle*<br/>
Odwołanie do typu UINT, który jest ustawiony na styl okienka.

*cxWidth*<br/>
Odwołanie do liczby całkowitej, która jest ustawiona na szerokość okienka.

##  <a name="getpanestyle"></a>CStatusBar:: getokienks

Wywołaj tę funkcję elementu członkowskiego, aby pobrać styl okienka paska stanu.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, którego styl ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Styl okienka pasek stanu określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl okienka określa wygląd okienka.

Aby uzyskać listę stylów dostępnych dla pasków stanu, zobacz [Create](#create).

##  <a name="getpanetext"></a>CStatusBar:: GetPaneText

Wywołaj tę funkcję elementu członkowskiego, aby pobrać tekst, który pojawia się w okienku paska stanu.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, którego tekst ma zostać pobrany.

*rString*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który zawiera tekst do pobrania.

### <a name="return-value"></a>Wartość zwracana

`CString` Obiekt zawierający tekst w okienku.

### <a name="remarks"></a>Uwagi

Druga forma tej funkcji składowej wypełnia `CString` obiekt ciągiem tekstu.

##  <a name="getstatusbarctrl"></a>CStatusBar:: GetStatusBarCtrl

Ta funkcja członkowska umożliwia bezpośredni dostęp do zasadniczej kontroli wspólnej.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawiera odwołanie do obiektu [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) .

### <a name="remarks"></a>Uwagi

Użyj `GetStatusBarCtrl` , aby skorzystać z funkcji typowej kontroli paska stanu systemu Windows i skorzystać z [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) pomocy technicznej w celu dostosowania paska stanu. Na przykład przy użyciu kontrolki Common można określić styl, który zawiera uchwyt zmiany rozmiarów na pasku stanu, lub określić styl, aby pasek stanu pojawił się u góry obszaru klienckiego okna nadrzędnego.

Aby uzyskać więcej ogólnych informacji na temat typowych kontrolek, zobacz [typowe kontrolki](/windows/win32/Controls/common-controls-intro) w Windows SDK.

##  <a name="setindicators"></a>CStatusBar:: setwskaźniks

Ustawia identyfikator każdego wskaźnika na wartość określoną przez odpowiedni element tablicy *lpIDArray*, ładuje zasób ciągu określony przez każdy identyfikator i ustawia tekst wskaźnika na ciąg.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Wskaźnik na tablicę identyfikatorów.

*nIDCount*<br/>
Liczba elementów w tablicy wskazywanych przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="setpaneinfo"></a>CStatusBar:: SetPaneInfo

Ustawia dla określonego okienka wskaźnika nowy identyfikator, styl i szerokość.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka wskaźnika, którego styl ma zostać ustawiony.

*nID*<br/>
Nowy identyfikator okienka wskaźnika.

*nStyle*<br/>
Nowy styl okienka wskaźnika.

*cxWidth*<br/>
Nowa szerokość okienka wskaźnika.

### <a name="remarks"></a>Uwagi

Obsługiwane są następujące style wskaźnika:

- SBPS_NOBORDERS bez obramowania 3-D wokół okienka.

- SBPS_POPOUT odwrotne obramowanie, aby tekst "pop out".

- SBPS_DISABLED nie rysuje tekstu.

- Okienko rozciągające się SBPS_STRETCH, aby wypełnić nieużywane miejsce. Tylko jedno okienko na pasek stanu może mieć ten styl.

- SBPS_NORMAL bez rozciągania, obramowań ani wyskakujących okienek.

##  <a name="setpanestyle"></a>CStatusBar:: setokienks

Wywołaj tę funkcję elementu członkowskiego, aby ustawić styl okienka paska stanu.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, którego styl ma zostać ustawiony.

*nStyle*<br/>
Styl okienka, którego styl ma zostać ustawiony.

### <a name="remarks"></a>Uwagi

Styl okienka określa wygląd okienka.

Aby uzyskać listę stylów dostępnych dla pasków stanu, zobacz [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>CStatusBar:: SetPaneText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić tekst w okienku na ciąg wskazywany przez *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, którego tekst ma zostać ustawiony.

*lpszNewText*<br/>
Wskaźnik do tekstu nowego okienka.

*bAktualizacja*<br/>
Jeśli wartość jest równa TRUE, okienko jest unieważnione po ustawieniu tekstu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu `SetPaneText`należy dodać program obsługi aktualizacji interfejsu użytkownika w celu wyświetlenia nowego tekstu na pasku stanu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Przykład CTRLBARS MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład DLGCBR32 MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
