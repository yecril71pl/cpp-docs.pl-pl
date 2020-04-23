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
ms.openlocfilehash: 969edb3b1c87da851d83d390ab9d4e707bd2eb1e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753055"
---
# <a name="cstatusbar-class"></a>Klasa CStatusBar

Pasek sterowania z wierszem okienek wyjściowych tekstu lub "wskaźników".

## <a name="syntax"></a>Składnia

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Konstruuje `CStatusBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Pobiera indeks dla danego identyfikatora wskaźnika.|
|[CStatusBar::Utwórz](#create)|Tworzy pasek stanu, dołącza go `CStatusBar` do obiektu i ustawia początkową czcionkę i wysokość paska.|
|[CStatusBar::CreateEx](#createex)|Tworzy `CStatusBar` obiekt z dodatkowymi stylami dla `CStatusBarCtrl` obiektu osadzonego.|
|[CStatusBar::DrawItem](#drawitem)|Wywoływane, gdy zmienia się wizualny aspekt formantu paska stanu rysowania właściciela.|
|[CStatusBar::GetItemID](#getitemid)|Pobiera identyfikator wskaźnika dla danego indeksu.|
|[CStatusBar::GetItemRect](#getitemrect)|Pobiera prostokąt wyświetlania dla danego indeksu.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Pobiera identyfikator wskaźnika, styl i szerokość dla danego indeksu.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Pobiera styl wskaźnika dla danego indeksu.|
|[CStatusBar::GetPaneText](#getpanetext)|Pobiera tekst wskaźnika dla danego indeksu.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.|
|[CStatusBar::SetIndicators](#setindicators)|Ustawia identyfikatory wskaźników.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Ustawia identyfikator wskaźnika, styl i szerokość dla danego indeksu.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Ustawia styl wskaźnika dla danego indeksu.|
|[CStatusBar::SetPaneText](#setpanetext)|Ustawia tekst wskaźnika dla danego indeksu.|

## <a name="remarks"></a>Uwagi

Okienka danych wyjściowych są często używane jako linie komunikatów i jako wskaźniki stanu. Przykłady obejmują wiersze pomocy menu, które krótko wyjaśniają wybrane polecenie menu i wskaźniki, które pokazują stan blokady przewijania, blokady numeryczne i innych klawiszy.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), funkcja elementu członkowskiego nowy mfc 4.0, pozwala na skorzystanie z obsługi wspólnego formantu systemu Windows dla dostosowywania paska stanu i dodatkowe funkcje. `CStatusBar`funkcje członkowskie zapewniają większość funkcji typowych formantów systemu Windows; Jednak podczas wywoływania `GetStatusBarCtrl`można nadać paskach stanu jeszcze więcej cech paska stanu systemu Windows 95/98. Po wywołaniu `GetStatusBarCtrl`, zwróci odwołanie `CStatusBarCtrl` do obiektu. Zobacz [CStatusBarCtrl aby](../../mfc/reference/cstatusbarctrl-class.md) uzyskać więcej informacji na temat projektowania pasków narzędzi przy użyciu typowych formantów systemu Windows. Aby uzyskać bardziej ogólne informacje na temat typowych formantów, zobacz [Typowe formanty](/windows/win32/Controls/common-controls-intro) w sdk systemu Windows.

Struktura przechowuje informacje o wskaźniku w tablicy z lewym wskaźnikiem w pozycji 0. Podczas tworzenia paska stanu, należy użyć tablicy identyfikatorów ciągów, które struktura kojarzy z odpowiednimi wskaźnikami. Następnie można użyć identyfikatora ciągu lub indeksu, aby uzyskać dostęp do wskaźnika.

Domyślnie pierwszy wskaźnik jest "elastyczny": zajmuje długość paska stanu, która nie jest używana przez inne okienka wskaźników, dzięki czemu pozostałe okienka są wyrównane do prawej.

Aby utworzyć pasek stanu, wykonaj następujące czynności:

1. Konstruuj `CStatusBar` obiekt.

1. Wywołanie funkcji [Utwórz](#create) (lub [CreateEx),](#createex)aby utworzyć okno `CStatusBar` paska stanu i dołączyć je do obiektu.

1. Wywołaj [SetIndicators skojarzyć](#setindicators) identyfikator ciągu z każdym wskaźnikiem.

Istnieją trzy sposoby aktualizowania tekstu w okienku paska stanu:

1. Wywołanie [CWnd::SetWindowText,](../../mfc/reference/cwnd-class.md#setwindowtext) aby zaktualizować tekst tylko w okienku 0.

1. Wywołanie [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) w ON_UPDATE_COMMAND_UI programu obsługi paska stanu.

1. Wywołaj [SetPaneText,](#setpanetext) aby zaktualizować tekst dla dowolnego okienka.

Wywołanie [SetPaneStyle,](#setpanestyle) aby zaktualizować styl okienka paska stanu.

Aby uzyskać więcej `CStatusBar`informacji na temat używania , zobacz artykuł [Implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [uwaga techniczna 31 : Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusBar::CommandToIndex

Pobiera indeks wskaźnika dla danego identyfikatora.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDZnajduj*<br/>
Identyfikator ciągu wskaźnika, którego indeks ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Indeks wskaźnika, jeśli się powiedzie; -1, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Indeks pierwszego wskaźnika wynosi 0.

## <a name="cstatusbarcreate"></a><a name="create"></a>CStatusBar::Utwórz

Tworzy pasek stanu (okno podrzędne) i `CStatusBar` kojarzy go z obiektem.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd,](../../mfc/reference/cwnd-class.md) którego okno systemu Windows jest elementem nadrzędnym paska stanu.

*Dwstyle*<br/>
Styl paska stanu. Oprócz standardowych [stylów](../../mfc/reference/styles-used-by-mfc.md#window-styles)systemu Windows, style te są obsługiwane.

- CBRS_TOP pasek sterowania znajduje się w górnej części okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się w dolnej części okna ramki.

- CBRS_NOALIGN pasek sterowania nie jest zmieniany po zmianie jego zmiany.

*Nid*<br/>
Identyfikator okna podrzędnego paska narzędzi.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ustawia również czcionkę początkową i ustawia wysokość paska stanu na wartość domyślną.

## <a name="cstatusbarcreateex"></a><a name="createex"></a>CStatusBar::CreateEx

Wywołanie tej funkcji, aby utworzyć pasek stanu (okno `CStatusBar` podrzędne) i skojarzyć go z obiektem.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd,](../../mfc/reference/cwnd-class.md) którego okno systemu Windows jest elementem nadrzędnym paska stanu.

*dwCtrlStyle*<br/>
Dodatkowe style do tworzenia osadzonego [obiektu CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md) Wartość domyślna określa pasek stanu bez uchwytu zmiany rozmiaru lub podpowiecie etykietki narzędzia. Obsługiwane style paska stanu to:

- SBARS_SIZEGRIP Kontrolka paska stanu zawiera uchwyt zmiany rozmiaru na prawym końcu paska stanu. Uchwyt zmiany rozmiaru jest podobny do obramowania rozmiaru; jest to prostokątny obszar, który użytkownik może kliknąć i przeciągnąć, aby zmienić rozmiar okna nadrzędnego.

- SBT_TOOLTIPS Pasek stanu obsługuje etykietki narzędzi.

Aby uzyskać szczegółowe informacje na temat tych stylów, zobacz [Ustawienia CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*Dwstyle*<br/>
Styl paska stanu. Wartość domyślna określa, że widoczny pasek stanu ma zostać utworzony w dolnej części okna ramki. Zastosuj dowolną kombinację stylów formantu paska stanu wymienionych w [stylach okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Jednak ten parametr powinien zawsze zawierać style WS_CHILD i WS_VISIBLE.

*Nid*<br/>
Identyfikator okna podrzędnego paska stanu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja ustawia również czcionkę początkową i ustawia wysokość paska stanu na wartość domyślną.

Użyj `CreateEx`zamiast [Create](#create), gdy niektóre style muszą być obecne podczas tworzenia osadzonego paska stanu. Na przykład ustaw *dwCtrlStyle,* aby SBT_TOOLTIPS, aby wyświetlić etykietki narzędzi w obiekcie paska stanu.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>CStatusBar::CStatusBar

Konstruuje `CStatusBar` obiekt, w razie potrzeby tworzy domyślną czcionkę paska stanu i ustawia właściwości czcionki na wartości domyślne.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::DrawItem

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy zmienia się wizualny aspekt paska stanu rysowanego przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) który zawiera informacje o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Element `itemAction` członkowski `DRAWITEMSTRUCT` konstrukcji definiuje akcję rysowania, która ma być wykonana. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CStatusBar` właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar::GetItemID

Zwraca identyfikator wskaźnika określonego przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks wskaźnika, którego identyfikator ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Identyfikator wskaźnika określonego przez *nIndex*.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar::GetItemRect

Kopiuje współrzędne wskaźnika określonego przez *nIndex* do struktury wskazanej przez *lpRect*.

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks wskaźnika, którego współrzędne prostokąta mają zostać pobrane.

*Lprect*<br/>
Wskazuje na strukturę [RECT](/windows/win32/api/windef/ns-windef-rect) lub obiekt [CRect,](../../atl-mfc-shared/reference/crect-class.md) który otrzyma współrzędne wskaźnika określonego przez *nIndex*.

### <a name="remarks"></a>Uwagi

Współrzędne znajdują się w pikselach względem lewego górnego rogu paska stanu.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar::GetPaneInfo

Ustawia *nID*, *nStyle*i *cxWidth* na identyfikator, styl i szerokość okienka wskaźnika w miejscu określonym przez *nIndex*.

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka, którego informacje mają zostać pobrane.

*Nid*<br/>
Odwołanie do UINT, który jest ustawiony na identyfikator okienka.

*styl nStyle*<br/>
Odwołanie do UINT, który jest ustawiony na styl okienka.

*cxWidth ( cxWidth )*<br/>
Odwołanie do liczby całkowitej ustawionej na szerokość okienka.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>CStatusBar::GetPaneStyle

Wywołanie tej funkcji elementu członkowskiego, aby pobrać styl okienka paska stanu.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka, którego styl ma zostać pobrany.

### <a name="return-value"></a>Wartość zwracana

Styl okienka paska stanu określony przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl okienka określa sposób wyświetleń okienka.

Aby uzyskać listę stylów dostępnych dla pasków stanu, zobacz [Tworzenie](#create).

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>CStatusBar::GetPaneText

Wywołanie tej funkcji elementu członkowskiego, aby pobrać tekst, który pojawia się w okienku paska stanu.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka, którego tekst ma zostać pobrany.

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu, który zawiera tekst do pobrania.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CString` zawierający tekst okienka.

### <a name="remarks"></a>Uwagi

Drugi formularz tej funkcji elementu `CString` członkowskiego wypełnia obiekt tekstem ciągu.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl

Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowej wspólnej kontroli.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawiera odwołanie do obiektu [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md)

### <a name="remarks"></a>Uwagi

Służy `GetStatusBarCtrl` do korzystania z funkcji wspólnego formantu paska stanu systemu Windows i skorzystania z pomocy technicznej [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) zapewnia dostosowywanie paska stanu. Na przykład za pomocą wspólnego formantu można określić styl, który zawiera uchwyt zmiany rozmiaru na pasku stanu lub można określić styl, aby pasek stanu był wyświetlany w górnej części obszaru klienta okna nadrzędnego.

Aby uzyskać bardziej ogólne informacje na temat typowych formantów, zobacz [typowe formanty](/windows/win32/Controls/common-controls-intro) w sdk systemu Windows.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>CStatusBar::SetIndicators

Ustawia identyfikator każdego wskaźnika na wartość określoną przez odpowiedni element *tablicy lpIDArray*, ładuje zasób ciągu określony przez każdy identyfikator i ustawia tekst wskaźnika na ciąg.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray (lpIDArray)*<br/>
Wskaźnik do tablicy identyfikatorów.

*nIDCount (liczba NIDCount)*<br/>
Liczba elementów w tablicy wskazywionej przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CStatusBar::SetPaneInfo

Ustawia określone okienko wskaźnika na nowy identyfikator, styl i szerokość.

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka wskaźnika, którego styl ma być ustawiony.

*Nid*<br/>
Nowy identyfikator okienka wskaźnika.

*styl nStyle*<br/>
Nowy styl okienka wskaźników.

*cxWidth ( cxWidth )*<br/>
Nowa szerokość okienka wskaźnika.

### <a name="remarks"></a>Uwagi

Obsługiwane są następujące style wskaźników:

- SBPS_NOBORDERS obramowanie nr 3-W wokół okienka.

- SBPS_POPOUT Odwróć obramowanie, aby tekst "wyskakuje".

- SBPS_DISABLED Nie rysuj tekstu.

- SBPS_STRETCH okienku Rozciągliwienie, aby wypełnić nieużywane miejsce. Ten styl może mieć tylko jedno okienko na pasku stanu.

- SBPS_NORMAL Brak rozciągania, obramowania lub wyskakowania.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CStatusBar::SetPaneStyle

Wywołanie tej funkcji elementu członkowskiego, aby ustawić styl okienka paska stanu.

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka, którego styl ma być ustawiony.

*styl nStyle*<br/>
Styl okienka, którego styl ma być ustawiony.

### <a name="remarks"></a>Uwagi

Styl okienka określa sposób wyświetleń okienka.

Aby uzyskać listę stylów dostępnych dla pasków stanu, zobacz [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>CStatusBar::SetPaneText

Wywołanie tej funkcji elementu członkowskiego, aby ustawić tekst okienka na ciąg wskazywany przez *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks okienka, którego tekst ma być ustawiony.

*lpszNewText (Tekst lpszNewText)*<br/>
Wskaźnik do nowego tekstu okienka.

*bUpęb.*<br/>
Jeśli prawda, okienko zostanie unieważnione po ustawieniu tekstu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu `SetPaneText`należy dodać program obsługi aktualizacji interfejsu użytkownika, aby wyświetlić nowy tekst na pasku stanu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
