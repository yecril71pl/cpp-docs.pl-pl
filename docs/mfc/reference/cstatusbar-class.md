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
ms.openlocfilehash: e7aa577d237c1800ca9df3f0af4c44acdaae9ae2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279500"
---
# <a name="cstatusbar-class"></a>Klasa CStatusBar

Pasek sterowania z wiersza tekstu wyjściowego okienka lub "wskaźniki."

## <a name="syntax"></a>Składnia

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Konstruuje `CStatusBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Pobiera indeks dla identyfikatora dla danego wskaźnika.|
|[CStatusBar::Create](#create)|Tworzy pasek stanu, dołącza go do `CStatusBar` obiektu i ustawia początkowa wysokość czcionki i paskiem.|
|[CStatusBar::CreateEx](#createex)|Tworzy `CStatusBar` obiektu o dodatkowe style osadzonego `CStatusBarCtrl` obiektu.|
|[CStatusBar::DrawItem](#drawitem)|Wywołuje się, gdy zmieni się wizualny aspekt rysowania przez właściciela stanu paska sterowania zmiany.|
|[CStatusBar::GetItemID](#getitemid)|Pobiera identyfikator wskaźnika dla podanego indeksu.|
|[CStatusBar::GetItemRect](#getitemrect)|Pobiera wyświetlane prostokąt dla podanego indeksu.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Pobiera identyfikator wskaźnika, stylu i szerokości dla podanego indeksu.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Pobiera styl wskaźnika dla podanego indeksu.|
|[CStatusBar::GetPaneText](#getpanetext)|Pobiera tekst wskaźnika dla podanego indeksu.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.|
|[CStatusBar::SetIndicators](#setindicators)|Ustawia wskaźnik identyfikatorów.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Ustawia identyfikator wskaźnika, stylu i szerokości dla podanego indeksu.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Określa styl wskaźnika dla podanego indeksu.|
|[CStatusBar::SetPaneText](#setpanetext)|Ustawia tekst wskaźnika dla podanego indeksu.|

## <a name="remarks"></a>Uwagi

Okienka danych wyjściowych są często używane jako wiersz wiadomości, a wskaźniki stanu. Przykłady obejmują linie komunikat pomocy menu krótko opisano wybrane polecenie i wskaźniki, pokazujące stan SCROLL LOCK, NUM LOCK i innych kluczy.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), funkcją składową nowe 4.0 MFC, pozwala na korzystanie z zalet obsługi Windows formantu typowego paska dostosowań i dodatkowe funkcje stanu. `CStatusBar` Funkcje Członkowskie zapewniają większość funkcji wspólnych formantów Windows; Jednak jeśli wywołasz `GetStatusBarCtrl`, Twoje paski stanu można nadać jeszcze więcej właściwości paska stanu Windows 95/98. Gdy wywołujesz `GetStatusBarCtrl`, to zostanie zwrócona odwołanie do `CStatusBarCtrl` obiektu. Zobacz [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) Aby uzyskać więcej informacji na temat projektowania pasków narzędzi za pomocą wspólnych formantów Windows. Aby uzyskać więcej ogólnych informacji o wspólnych formantów, zobacz [wspólnych formantów](/windows/desktop/Controls/common-controls-intro) w zestawie Windows SDK.

Struktura są przechowywane informacje wskaźnika tablicy skrajnie po lewej stronie wskaźnik na pozycji 0. Podczas tworzenia paska stanu, skorzystaj z tablicy parametrów identyfikatorów, które ramach kojarzy z odpowiednie wskaźniki. Wskazuje dostęp do można następnie użyć identyfikator ciągu lub indeksu.

Domyślnie pierwszego wskaźnika jest "elastyczne": zajmuje on długość paska stanu nie jest używany przez inne okienka wskaźnika, tak aby były inne okienka wyrównany do prawej.

Aby utworzyć pasek stanu, wykonaj następujące kroki:

1. Konstruowania `CStatusBar` obiektu.

1. Wywołaj [Utwórz](#create) (lub [CreateEx](#createex)) funkcji, aby utworzyć okno pasek stanu i dołączyć go do `CStatusBar` obiektu.

1. Wywołaj [SetIndicators](#setindicators) do skojarzenia Identyfikatora ciągu z każdego wskaźnika.

Istnieją trzy sposoby aktualizowana tekstu w okienku paska stanu:

1. Wywołaj [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) na aktualizowanie tekstu w okienku tylko 0.

1. Wywołaj [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) w obsłudze ON_UPDATE_COMMAND_UI na pasku stanu.

1. Wywołaj [SetPaneText](#setpanetext) do zaktualizowania tekstu dla dowolnego okienka.

Wywołaj [SetPaneStyle](#setpanestyle) aktualizacji stylu w okienku paska stanu.

Aby uzyskać więcej informacji na temat korzystania z `CStatusBar`, zapoznaj się z artykułem [implementacja paska stanu w MFC](../../mfc/status-bar-implementation-in-mfc.md) i [techniczne 31 Uwaga: Paski sterowania](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="commandtoindex"></a>  CStatusBar::CommandToIndex

Pobiera indeks wskaźnik dla o podanym identyfikatorze.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parametry

*nIDFind*<br/>
Identyfikator ciągu wskaźnika, którego indeks to do pobrania.

### <a name="return-value"></a>Wartość zwracana

Indeks wskaźnika, jeśli to się powiedzie; -1, jeśli nie powiodło się.

### <a name="remarks"></a>Uwagi

Indeks pierwszego wskaźnika jest 0.

##  <a name="create"></a>  CStatusBar::Create

Stan paska (okno podrzędne) tworzy i kojarzy ją z `CStatusBar` obiektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, którego okno Windows ma element nadrzędny paska stanu.

*dwStyle*<br/>
Styl paska stanu. Oprócz standardowych Windows [style](../../mfc/reference/styles-used-by-mfc.md#window-styles), te style są obsługiwane.

- Pasek sterowania CBRS_TOP to u góry okna ramki.

- Pasek sterowania CBRS_BOTTOM jest w dolnej części okna ramki.

- Pasek sterowania CBRS_NOALIGN nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.

*nID*<br/>
Identyfikator paska narzędzi okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ponadto Ustawia czcionkę początkowej i ustawia stan paska wysokość na wartość domyślną.

##  <a name="createex"></a>  CStatusBar::CreateEx

Wywołaj tę funkcję, aby utworzyć stanu paska (okno podrzędne) i powiąż ją z `CStatusBar` obiektu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, którego okno Windows ma element nadrzędny paska stanu.

*dwCtrlStyle*<br/>
Dodatkowe style Tworzenie osadzonego [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) obiektu. Domyślnie określa pasek stanu bez uchwyt zmiany rozmiaru lub etykietki narzędzia pomocy technicznej. Style paska stanu, obsługiwane są następujące:

- SBARS_SIZEGRIP formantu paska stanu zawiera uchwyt zmiany rozmiaru na prawym końcu paska stanu. Uchwyt zmiany rozmiaru jest podobny do granicę z ustalanym; jest prostokątny obszar, który użytkownik może kliknij i przeciągnij, aby zmienić rozmiar okna nadrzędnego.

- Na pasku stanu SBT_TOOLTIPS obsługuje etykietek narzędzi.

Szczegółowe informacje na temat tych stylów, [ustawienia formantu CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Styl paska stanu. Wartość domyślna Określa utworzony pasek stanu widoczny w dolnej części okna ramki. Zastosuj dowolną kombinację stanu paska style kontrolki, na liście [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) i [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Jednak ten parametr powinien zawsze zawierać WS_CHILD i WS_VISIBLE style.

*nID*<br/>
Identyfikator okna podrzędnego na pasku stanu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja także ustawia czcionkę początkowej i ustawia stan paska wysokość na wartość domyślną.

Użyj `CreateEx`, zamiast [Utwórz](#create), gdy określone style musi być obecny podczas tworzenia formantu paska stanu osadzonych. Na przykład ustawić *dwCtrlStyle* do SBT_TOOLTIPS do wyświetlenia etykietki narzędzi w obiekcie pasek stanu.

##  <a name="cstatusbar"></a>  CStatusBar::CStatusBar

Konstruuje `CStatusBar` obiekt, tworzy domyślną czcionkę paska stanu w razie potrzeby i ustawia domyślne wartości cech czcionki.

```
CStatusBar();
```

##  <a name="drawitem"></a>  CStatusBar::DrawItem

Ta funkcja członkowska jest wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany paska stanu rysowanych przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.

### <a name="remarks"></a>Uwagi

`itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CStatusBar` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

##  <a name="getitemid"></a>  CStatusBar::GetItemID

Zwraca identyfikator wskaźnika określonej przez *nIndex*.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wskaźnika, którego identyfikator jest do pobrania.

### <a name="return-value"></a>Wartość zwracana

Identyfikator wskaźnika określonej przez *nIndex*.

##  <a name="getitemrect"></a>  CStatusBar::GetItemRect

Kopiuje współrzędne wskaźnika określonej przez *nIndex* w strukturze wskazywany przez *lprect —*.

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks wskaźnika, którego współrzędne prostokąt, które mają być pobierane.

*lpRect*<br/>
Wskazuje [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury lub [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu, który będzie otrzymywał współrzędne wskaźnika określonej przez *nIndex*.

### <a name="remarks"></a>Uwagi

Współrzędne są podawane w pikselach względem lewego górnego rogu paska stanu.

##  <a name="getpaneinfo"></a>  CStatusBar::GetPaneInfo

Zestawy *nID*, *nStyle*, i *cxWidth* identyfikator, stylu i szerokości w okienku wskaźnika w lokalizacji określonej przez *nIndex*.

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks okienka, w których informacje są do pobrania.

*nID*<br/>
Odwołanie do UINT, który jest ustawiony na identyfikator okienka.

*nStyle*<br/>
Odwołanie do UINT, który jest ustawiony na styl okienka.

*cxWidth*<br/>
Odwołanie do liczba całkowita, która jest równa szerokość panelu.

##  <a name="getpanestyle"></a>  CStatusBar::GetPaneStyle

Wywołaj tę funkcję elementu członkowskiego, aby pobrać Styl okienka paska stanu.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks części okienka, którego styl ma zostać pobrane.

### <a name="return-value"></a>Wartość zwracana

Styl w okienku paska stanu określonego przez *nIndex*.

### <a name="remarks"></a>Uwagi

Styl w okienku określa sposób wyświetlania okienka.

Aby uzyskać listę style dostępne na paskach stanu, zobacz [Utwórz](#create).

##  <a name="getpanetext"></a>  CStatusBar::GetPaneText

Wywołaj tę funkcję elementu członkowskiego, aby przywrócić tekst, który jest wyświetlany w okienku paska stanu.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks części okienka, którego tekst jest do pobrania.

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który zawiera tekst, który ma zostać pobrane.

### <a name="return-value"></a>Wartość zwracana

A `CString` obiekt zawierający tekst w okienku.

### <a name="remarks"></a>Uwagi

Druga forma ten element członkowski funkcji wypełnienia `CString` obiektu z ciąg tekstu.

##  <a name="getstatusbarctrl"></a>  CStatusBar::GetStatusBarCtrl

Ta funkcja elementu członkowskiego umożliwia bezpośredni dostęp do podstawowych wspólnej kontroli.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawiera odwołanie do [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Użyj `GetStatusBarCtrl` wykorzystać funkcje formantu typowego paska stanu Windows i korzystać z pomocy technicznej [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) zapewnia dostosowywanie paska stanu. Na przykład za pomocą formantu typowego, można określić styl, który zawiera uchwyt zmiany rozmiaru, na pasku stanu lub określić styl pasek stanu u góry obszaru klienckiego okna nadrzędnego.

Aby uzyskać więcej ogólnych informacji o wspólnych formantów, zobacz [wspólnych formantów](/windows/desktop/Controls/common-controls-intro) w zestawie Windows SDK.

##  <a name="setindicators"></a>  CStatusBar::SetIndicators

Ustawia identyfikator każdego wskaźnika na wartość określoną przez odpowiedni element tablicy *lpIDArray*, ładuje określone przez każdy identyfikator zasobu ciągu i ustawia tekst wskaźnik do ciągu.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parametry

*lpIDArray*<br/>
Wskaźnik do tablicy identyfikatorów.

*nIDCount*<br/>
Liczba elementów w tablicy, wskazywana przez *lpIDArray*.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="setpaneinfo"></a>  CStatusBar::SetPaneInfo

Ustawia okienko określony wskaźnik do nowego Identyfikatora, stylu i szerokości.

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks w okienku wskaźnika, którego styl ma być utworzony.

*nID*<br/>
Nowy identyfikator dla tego okienka wskaźnika.

*nStyle*<br/>
Nowy styl dla okienka wskaźnika.

*cxWidth*<br/>
Nową szerokość dla okienka wskaźnika.

### <a name="remarks"></a>Uwagi

Obsługiwane są następujące style wskaźnika:

- SBPS_NOBORDERS nr 3-obramowanie wokół okienka.

- Odwróć SBPS_POPOUT obramowania, tak, aby tekst "pojawia się."

- Nie należy SBPS_DISABLED Rysowanie tekstu.

- Okienko SBPS_STRETCH Stretch do wypełnienia nieużywane miejsce. Tylko jedno okienko na pasku stanu może mieć tego stylu.

- Stretch nie SBPS_NORMAL, obramowanie lub podręcznego.

##  <a name="setpanestyle"></a>  CStatusBar::SetPaneStyle

Wywołaj tę funkcję elementu członkowskiego, aby ustawić styl paska stanu w okienku.

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks części okienka, którego styl ma być utworzony.

*nStyle*<br/>
Styl okienka, którego styl ma być utworzony.

### <a name="remarks"></a>Uwagi

Styl w okienku określa sposób wyświetlania okienka.

Aby uzyskać listę style dostępne na paskach stanu, zobacz [SetPaneInfo](#setpaneinfo).

##  <a name="setpanetext"></a>  CStatusBar::SetPaneText

Wywołaj tę funkcję elementu członkowskiego, aby ustawić tekst w okienku parametry wskazywany przez *lpszNewText*.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks części okienka, którego tekst jest do ustawienia.

*lpszNewText*<br/>
Wskaźnik do nowego tekstu w okienku.

*baktualizacji*<br/>
W przypadku opcji TRUE okienka zostaje unieważniony po ustawieniu tekstu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu metody `SetPaneText`, należy dodać program obsługi aktualizacji interfejsu użytkownika Aby wyświetlić nowy tekst w pasku stanu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLBARS](../../visual-cpp-samples.md)<br/>
[MFC Sample DLGCBR32](../../visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
