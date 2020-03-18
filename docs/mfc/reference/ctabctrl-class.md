---
title: Klasa CTabCtrl
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420926"
---
# <a name="ctabctrl-class"></a>Klasa CTabCtrl

Oferuje funkcje formantu typowej karty systemu Windows.

## <a name="syntax"></a>Składnia

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CTabCtrl:: CTabCtrl](#ctabctrl)|Konstruuje obiekt `CTabCtrl`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CTabCtrl:: AdjustRect](#adjustrect)|Oblicza obszar wyświetlania kontrolki karty przy użyciu prostokąta okna lub oblicza prostokąt okna, który będzie odpowiadał podanemu obszarowi wyświetlania.|
|[CTabCtrl:: Create](#create)|Tworzy formant karty i dołącza go do wystąpienia obiektu `CTabCtrl`.|
|[CTabCtrl:: CreateEx](#createex)|Tworzy formant karty z określonymi stylami rozszerzonymi systemu Windows i dołącza go do wystąpienia obiektu `CTabCtrl`.|
|[CTabCtrl::D eleteAllItems](#deleteallitems)|Usuwa wszystkie elementy z kontrolki karta.|
|[CTabCtrl::D eleteItem](#deleteitem)|Usuwa element z kontrolki karta.|
|[CTabCtrl::D eselectAll](#deselectall)|Resetuje elementy w kontrolce karty, czyszcząc wszystkie, które zostały naciśnięte.|
|[CTabCtrl::D rawItem](#drawitem)|Rysuje określony element kontrolki karta.|
|[CTabCtrl:: GetCurFocus](#getcurfocus)|Pobiera kartę z bieżącym fokusem kontrolki karta.|
|[CTabCtrl:: GetCurSel](#getcursel)|Określa aktualnie wybraną kartę w kontrolce karty.|
|[CTabCtrl:: getextendeds](#getextendedstyle)|Pobiera Style rozszerzone, które są obecnie używane dla kontrolki karta.|
|[CTabCtrl:: GetImageList](#getimagelist)|Pobiera listę obrazów skojarzoną z kontrolką karty.|
|[CTabCtrl:: GetItem](#getitem)|Pobiera informacje o karcie w kontrolce karty.|
|[CTabCtrl:: GetItemCount](#getitemcount)|Pobiera liczbę kart w kontrolce karty.|
|[CTabCtrl:: GetItemRect](#getitemrect)|Pobiera prostokąt ograniczenia dla karty w kontrolce karty.|
|[CTabCtrl:: GetItemState](#getitemstate)|Pobiera stan wskazanego elementu kontrolki karta.|
|[CTabCtrl:: GetRowCount](#getrowcount)|Pobiera bieżącą liczbę wierszy kart w kontrolce karty.|
|[CTabCtrl:: GetToolTips](#gettooltips)|Pobiera uchwyt kontrolki etykietki narzędzia skojarzonej z kontrolką karty.|
|[CTabCtrl:: HighlightItem](#highlightitem)|Ustawia stan wyróżniania elementu tabulacji.|
|[CTabCtrl:: HitTest](#hittest)|Określa, która karta (jeśli istnieje) znajduje się na określonej pozycji ekranu.|
|[CTabCtrl:: InsertItem](#insertitem)|Wstawia nową kartę w kontrolce karty.|
|[CTabCtrl:: RemoveImage](#removeimage)|Usuwa obraz z listy obrazów kontrolki karta.|
|[CTabCtrl:: SetCurFocus](#setcurfocus)|Ustawia fokus na określoną kartę w kontrolce karty.|
|[CTabCtrl:: SetCurSel](#setcursel)|Wybiera kartę w kontrolce karty.|
|[CTabCtrl:: setextended](#setextendedstyle)|Ustawia rozszerzone style dla kontrolki karta.|
|[CTabCtrl:: SetImageList](#setimagelist)|Przypisuje listę obrazów do kontrolki karta.|
|[CTabCtrl:: SetItem](#setitem)|Ustawia niektóre lub wszystkie atrybuty karty.|
|[CTabCtrl:: SetItemExtra](#setitemextra)|Ustawia liczbę bajtów na kartę zarezerwowaną dla danych zdefiniowanych przez aplikację w kontrolce karty.|
|[CTabCtrl:: SetItemSize](#setitemsize)|Ustawia szerokość i wysokość elementu.|
|[CTabCtrl:: SetItemState](#setitemstate)|Ustawia stan wskazanego elementu kontrolki karta.|
|[CTabCtrl:: SetMinTabWidth](#setmintabwidth)|Ustawia minimalną szerokość elementów w kontrolce karty.|
|[CTabCtrl:: setuzupełnienie](#setpadding)|Ustawia ilość miejsca (uzupełnienie) wokół każdej karty i etykiety w kontrolce karty.|
|[CTabCtrl:: setetykietki narzędzi](#settooltips)|Przypisuje formant etykietki narzędzia do kontrolki karta.|

## <a name="remarks"></a>Uwagi

"Kontrolka karta" jest analogiczna do dzielników w notesie lub etykiet w pliku cabinet. Za pomocą kontrolki karta aplikacja może definiować wiele stron w tym samym obszarze okna lub oknie dialogowym. Każda strona składa się z zestawu informacji lub grupy formantów, które aplikacja wyświetla, gdy użytkownik wybierze odpowiednią kartę. Specjalny typ kontrolki karta wyświetla karty, które wyglądają jak przyciski. Kliknięcie przycisku powinno natychmiast wykonać polecenie zamiast wyświetlania strony.

Ten formant (i w związku z tym Klasa `CTabCtrl`) jest dostępny tylko dla programów uruchomionych w systemach Windows 95/98 i Windows NT w wersji 3,51 lub nowszej.

Aby uzyskać więcej informacji na temat używania `CTabCtrl`, zobacz [Controls](../../mfc/controls-mfc.md) and [using CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="adjustrect"></a>CTabCtrl:: AdjustRect

Oblicza obszar wyświetlania kontrolki karty przy użyciu prostokąta okna lub oblicza prostokąt okna, który będzie odpowiadał podanemu obszarowi wyświetlania.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bLarger*<br/>
Wskazuje, którą operację wykonać. Jeśli ten parametr ma wartość TRUE, *lpRect* określa prostokąt wyświetlania i odbiera odpowiadający mu prostokąt okna. Jeśli ten parametr ma wartość FALSE, *lpRect* określa prostokąt okna i odbiera odpowiedni prostokąt wyświetlania.

*lpRect*<br/>
Wskaźnik do struktury [prostokąta](/previous-versions/dd162897\(v=vs.85\)) , która określa dany prostokąt i odbiera obliczony prostokąt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl:: Create

Tworzy formant karty i dołącza go do wystąpienia obiektu `CTabCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl formantu karty. Zastosuj dowolną kombinację [stylów formantu karty](/windows/win32/Controls/tab-control-styles), opisanej w Windows SDK. Zobacz **uwagi** , aby zapoznać się z listą stylów okna, które można również zastosować do kontrolki.

*cinania*<br/>
Określa rozmiar i położenie kontrolki karty. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki karta, zazwyczaj `CDialog`. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator formantu karty.

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli Inicjalizacja obiektu zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Należy skonstruować obiekt `CTabCtrl` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy formant karty i dołącza go do obiektu `CTabCtrl`.

Oprócz stylów kontrolek karta, można zastosować następujące style okna do kontrolki karta:

- WS_CHILD tworzy okno podrzędne, które reprezentuje kontrolkę karta. Nie można używać z stylem WS_POPUP.

- WS_VISIBLE tworzy formant karty, który jest początkowo widoczny.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone.

- WS_GROUP Określa pierwszą kontrolkę grupy kontrolek, w której użytkownik może przechodzić z jednej kontrolki do następnej przy użyciu klawiszy strzałek. Wszystkie kontrolki zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontrolce należy do tej samej grupy. Następna kontrolka z stylem WS_GROUP spowoduje zakończenie grupy stylów i rozpoczęcie następnej grupy (oznacza to, że jedna grupa zostanie zakończona, gdy następny zaczyna).

- WS_TABSTOP określa jedną z dowolnych kontrolek, za pomocą których użytkownik może przechodzić przy użyciu klawisza TAB. Klawisz TAB przenosi użytkownika do następnej kontrolki określonej przez styl WS_TABSTOP.

Aby utworzyć kontrolkę karta z rozszerzonymi stylami okien, wywołaj [CTabCtrl:: CreateEx](#createex) , a nie `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl:: CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z obiektem `CTabCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Określa rozszerzony styl formantu, który jest tworzony. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Określa styl formantu karty. Zastosuj dowolną kombinację [stylów formantu karty](/windows/win32/Controls/tab-control-styles), opisanej w Windows SDK. Zobacz **uwagi** w temacie [Tworzenie](#create) , aby wyświetlić listę stylów okna, które można również zastosować do kontrolki.

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli w przeciwnym razie określono wartość 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzyć](#create) , aby zastosować rozszerzone style systemu Windows, określone przez **WS_EX_** prekroju stylu systemu Windows.

`CreateEx` tworzy formant przy użyciu rozszerzonych stylów systemu Windows określonych przez *dwExStyle*. Ustawianie stylów rozszerzonych specyficznych dla kontrolki przy użyciu [setextended](#setextendedstyle). Na przykład użyj `CreateEx`, aby ustawić takie style jako WS_EX_CONTEXTHELP, ale Użyj `SetExtendedStyle` do ustawienia takich stylów jako TCS_EX_FLATSEPARATORS. Aby uzyskać więcej informacji, zapoznaj się z stylami opisanymi w sekcji [kontrolki karta rozszerzone style](/windows/win32/Controls/tab-control-extended-styles) w Windows SDK.

##  <a name="ctabctrl"></a>CTabCtrl:: CTabCtrl

Konstruuje obiekt `CTabCtrl`.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl::D eleteAllItems

Usuwa wszystkie elementy z kontrolki karta.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="deleteitem"></a>CTabCtrl::D eleteItem

Usuwa określony element z kontrolki karta.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Wartość zerowa elementu do usunięcia.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl::D eselectAll

Resetuje elementy w kontrolce karty, czyszcząc wszystkie, które zostały naciśnięte.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fExcludeFocus*<br/>
Flaga określająca zakres wyboru elementu. Jeśli ten parametr ma wartość FAŁSZ, wszystkie przyciski karty zostaną zresetowane. Jeśli wartość jest równa TRUE, wówczas wszystkie elementy karty z wyjątkiem tych, które są aktualnie zaznaczone, zostaną zresetowane.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie komunikatu Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), zgodnie z opisem w Windows SDK.

##  <a name="drawitem"></a>CTabCtrl::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt kontrolki karta rysowania przez właściciela zmienia się.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) opisujący element do narysowania.

### <a name="remarks"></a>Uwagi

`itemAction` element członkowski struktury `DRAWITEMSTRUCT` definiuje akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja członkowska nic nie robi. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla obiektu `CTabCtrl` rysowania przez właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

##  <a name="getcurfocus"></a>CTabCtrl:: GetCurFocus

Pobiera indeks karty z bieżącym fokusem.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) karty z bieżącym fokusem.

##  <a name="getcursel"></a>CTabCtrl:: GetCurSel

Pobiera aktualnie wybraną kartę w kontrolce karty.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) wybranej karty w przypadku powodzenia lub-1, jeśli żadna karta nie jest zaznaczona.

##  <a name="getextendedstyle"></a>CTabCtrl:: getextendeds

Pobiera Style rozszerzone, które są obecnie używane dla kontrolki karta.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Wartość zwrócona

Reprezentuje style rozszerzone aktualnie używane dla kontrolki karta. Ta wartość jest kombinacją [rozszerzonych stylów kontrolki karta](/windows/win32/Controls/tab-control-extended-styles), zgodnie z opisem w Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="getimagelist"></a>CTabCtrl:: GetImageList

Pobiera listę obrazów skojarzoną z kontrolką karty.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli to się powiedzie, wskaźnik do listy obrazów kontrolki karta; w przeciwnym razie wartość NULL.

##  <a name="getitem"></a>CTabCtrl:: GetItem

Pobiera informacje o karcie w kontrolce karty.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks karty (liczony od zera).

*pTabCtrlItem*<br/>
Wskaźnik do struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , służący do określania informacji do pobrania. Służy również do uzyskiwania informacji o karcie. Ta struktura jest używana z funkcjami składowymi `InsertItem`, `GetItem`i `SetItem`.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość PRAWDA, jeśli powodzenie; W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Po wysłaniu wiadomości element członkowski `mask` określa, które atrybuty należy zwrócić. Jeśli element członkowski `mask` określa wartość TCIF_TEXT, element członkowski `pszText` musi zawierać adres bufora, który odbiera tekst elementu, a element członkowski `cchTextMax` musi określać rozmiar buforu.

- `mask`

   Wartość określająca, które `TCITEM` składowe struktury do pobrania lub ustawienia. Ten element członkowski może mieć wartość zero lub kombinację następujących wartości:

   - TCIF_TEXT element członkowski `pszText` jest prawidłowy.

   - TCIF_IMAGE element członkowski `iImage` jest prawidłowy.

   - TCIF_PARAM element członkowski `lParam` jest prawidłowy.

   - TCIF_RTLREADING tekst `pszText` zostanie wyświetlony przy użyciu kolejności odczytywania od prawej do lewej w systemach hebrajskich lub arabskiej.

   - TCIF_STATE element członkowski `dwState` jest prawidłowy.

- `pszText`

   Wskaźnik na ciąg zakończony znakiem null zawierający tekst karty, jeśli struktura zawiera informacje o karcie. Jeśli struktura otrzymuje informacje, ten element członkowski Określa adres buforu, który odbiera tekst tabulacji.

- `cchTextMax`

   Rozmiar buforu wskazywany przez `pszText`. Ten element członkowski jest ignorowany, jeśli struktura nie otrzymuje informacji.

- `iImage` indeks do listy obrazów kontrolki karty lub-1, jeśli nie ma obrazu dla karty.

- `lParam`

   Zdefiniowane przez aplikację dane skojarzone z kartą. Jeśli istnieje więcej niż cztery bajty danych zdefiniowanych przez aplikację na kartę, aplikacja musi zdefiniować strukturę i użyć jej zamiast struktury `TCITEM`. Pierwszy element członkowski struktury zdefiniowanej przez aplikację musi być strukturą [TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw). Struktura `TCITEMHEADER` jest taka sama jak struktura `TCITEM`, ale bez składowej `lParam`. Różnica między rozmiarem struktury i rozmiarem struktury `TCITEMHEADER` powinna być równa liczbie dodatkowych bajtów na kartę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl:: GetItemCount

Pobiera liczbę kart w kontrolce karty.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w kontrolce karty.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>CTabCtrl:: GetItemRect

Pobiera prostokąt ograniczenia dla określonej karty w kontrolce karty.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks elementu karty liczony od zera.

*lpRect*<br/>
Wskaźnik do struktury [prostokąta](/previous-versions/dd162897\(v=vs.85\)) , która otrzymuje obwiednię tabulacji. Współrzędne te używają bieżącego trybu mapowania okienka ekranu.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>CTabCtrl:: GetItemState

Pobiera stan elementu kontrolki karta identyfikowanego przez *nitem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera numer indeksu elementu, dla którego mają zostać pobrane informacje o stanie.

*dwMask*<br/>
Maska określająca, która z flag stanu elementu ma zostać zwrócona. Aby uzyskać listę wartości, zobacz maskowanie składowej struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , zgodnie z opisem w Windows SDK.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do wartości DWORD, która otrzymuje informacje o stanie. Może być jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Wybrano element kontrolki karta.|
|TCIS_HIGHLIGHTED|Element kontrolki karta zostanie wyróżniony, a karta i tekst są rysowane przy użyciu bieżącego koloru wyróżnienia. W przypadku korzystania z koloru wyróżnienia będzie to prawdziwa interpolacja, a nie kolorem.|

### <a name="remarks"></a>Uwagi

Stan elementu jest określony przez `dwState` składową struktury `TCITEM`.

##  <a name="getrowcount"></a>CTabCtrl:: GetRowCount

Pobiera bieżącą liczbę wierszy w kontrolce karty.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba wierszy kart w kontrolce karty.

### <a name="remarks"></a>Uwagi

Tylko kontrolki tabulacji mające styl TCS_MULTILINE mogą mieć wiele wierszy kart.

##  <a name="gettooltips"></a>CTabCtrl:: GetToolTips

Pobiera uchwyt kontrolki etykietki narzędzia skojarzonej z kontrolką karty.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwrócona

Dojście do kontrolki etykietki narzędzia, jeśli się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Kontrolka karta tworzy formant etykietki narzędzia, jeśli ma styl TCS_TOOLTIPS. Możesz również przypisać kontrolkę etykietki narzędzia do kontrolki karta przy użyciu funkcji składowej `SetToolTips`.

##  <a name="highlightitem"></a>CTabCtrl:: HighlightItem

Ustawia stan wyróżniania elementu tabulacji.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idItem*<br/>
Indeks (liczony od zera) elementu formantu karty.

*fHighlight*<br/>
Wartość określająca stan wyróżnienia, który ma zostać ustawiony. Jeśli ta wartość jest RÓWNa TRUE, karta zostanie wyróżniona; Jeśli wartość jest równa FALSE, na karcie jest ustawiany stan domyślny.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje komunikat Win32 [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), zgodnie z opisem w Windows SDK.

##  <a name="hittest"></a>CTabCtrl:: HitTest

Określa, która karta (jeśli istnieje) znajduje się na określonej pozycji ekranu.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Wskaźnik do struktury [TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) , zgodnie z opisem w Windows SDK, która określa pozycję ekranu do przetestowania.

### <a name="return-value"></a>Wartość zwrócona

Zwraca indeks (liczony od zera) karty lub-1, jeśli żadna karta nie znajduje się na określonej pozycji.

##  <a name="insertitem"></a>CTabCtrl:: InsertItem

Wstawia nową kartę w istniejącej kontrolce karty.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks nowej karty (liczony od zera).

*pTabCtrlItem*<br/>
Wskaźnik na strukturę [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , która określa atrybuty karty.

*lpszItem*<br/>
Adres ciągu zakończenia o wartości null, który zawiera tekst karty.

*Nokreślono*<br/>
Indeks (liczony od zera) obrazu do wstawienia z listy obrazów.

*nMask*<br/>
Określa, które `TCITEM` atrybuty struktury do ustawienia. Może być równa zero lub kombinacja następujących wartości:

- TCIF_TEXT element członkowski `pszText` jest prawidłowy.

- TCIF_IMAGE element członkowski `iImage` jest prawidłowy.

- TCIF_PARAM element członkowski *lParam* jest prawidłowy.

- TCIF_RTLREADING tekst `pszText` zostanie wyświetlony przy użyciu kolejności odczytywania od prawej do lewej w systemach hebrajskich lub arabskiej.

- TCIF_STATE element członkowski *dwState* jest prawidłowy.

*lParam*<br/>
Zdefiniowane przez aplikację dane skojarzone z kartą.

*dwState*<br/>
Określa wartości dla Stanów elementu. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) w Windows SDK.

*dwStateMask*<br/>
Określa, które Stany mają być ustawione. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) w Windows SDK.

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) nowej karty, jeśli powodzenie; w przeciwnym razie-1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl:: RemoveImage

Usuwa określony obraz z listy obrazów kontrolki karta.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*Nokreślono*<br/>
Indeks (liczony od zera) obrazu do usunięcia.

### <a name="remarks"></a>Uwagi

Kontrolka karta aktualizuje indeks obrazu każdej karty, tak aby każda karta była skojarzona z tym samym obrazem.

##  <a name="setcurfocus"></a>CTabCtrl:: SetCurFocus

Ustawia fokus na określoną kartę w kontrolce karty.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Określa indeks karty, która pobiera fokus.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="setcursel"></a>CTabCtrl:: SetCurSel

Wybiera kartę w kontrolce karty.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks (liczony od zera) elementu, który ma zostać wybrany.

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) wcześniej wybranej karty, jeśli się powiedzie, w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

Kontrolka karty nie wysyła TCN_SELCHANGING ani TCN_SELCHANGE komunikatu powiadomienia, gdy karta zostanie wybrana przy użyciu tej funkcji. Powiadomienia są wysyłane przy użyciu WM_NOTIFY, gdy użytkownik kliknie lub użyje klawiatury, aby zmienić karty.

##  <a name="setextendedstyle"></a>CTabCtrl:: setextended

Ustawia rozszerzone style dla kontrolki karta.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNewStyle*<br/>
Wartość określająca kombinację rozszerzonych stylów kontrolki karta.

*dwExMask*<br/>
Wartość DWORD wskazująca, których stylów w *dwNewStyle* mają dotyczyć. Tylko style rozszerzone w *dwExMask* zostaną zmienione. Wszystkie inne style będą utrzymywane w postaci, w jakiej jest. Jeśli ten parametr ma wartość zero, wpłynie to na wszystkie style w *dwNewStyle* .

### <a name="return-value"></a>Wartość zwrócona

Wartość DWORD, która zawiera poprzednie [Style formantu karty](/windows/win32/Controls/tab-control-extended-styles), zgodnie z opisem w Windows SDK.

### <a name="return-value"></a>Wartość zwrócona

Ta funkcja członkowska implementuje zachowanie [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="setimagelist"></a>CTabCtrl:: SetImageList

Przypisuje listę obrazów do kontrolki karta.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Wskaźnik na listę obrazów, która ma zostać przypisana do kontrolki karta.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wskaźnik do poprzedniej listy obrazów lub wartość NULL, jeśli nie ma żadnych poprzednich list obrazów.

##  <a name="setitem"></a>CTabCtrl:: SetItem

Ustawia niektóre lub wszystkie atrybuty karty.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Indeks elementu (liczony od zera).

*pTabCtrlItem*<br/>
Wskaźnik do struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , która zawiera atrybuty nowego elementu. Element członkowski `mask` określa, które atrybuty ustawić. Jeśli element członkowski `mask` określa wartość TCIF_TEXT, element członkowski `pszText` jest adresem ciągu zakończonego wartością null, a element członkowski `cchTextMax` jest ignorowany.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład dla [GetItem](#getitem).

##  <a name="setitemextra"></a>CTabCtrl:: SetItemExtra

Ustawia liczbę bajtów na kartę zarezerwowaną dla danych zdefiniowanych przez aplikację w kontrolce karty.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba dodatkowych bajtów do ustawienia.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="setitemsize"></a>CTabCtrl:: SetItemSize

Ustawia szerokość i wysokość elementów kontrolki karta.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Nowa szerokość i wysokość elementów formantu karty w pikselach.

### <a name="return-value"></a>Wartość zwrócona

Zwraca starą szerokość i wysokość elementów kontrolki karta.

##  <a name="setitemstate"></a>CTabCtrl:: SetItemState

Ustawia stan elementu kontrolki karta identyfikowanego przez *nitem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera numer indeksu elementu, dla którego mają zostać ustawione informacje o stanie.

*dwMask*<br/>
Maska określająca, która z flag stanu elementu ma zostać ustawiona. Aby uzyskać listę wartości, zobacz maskowanie składowej struktury [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , zgodnie z opisem w Windows SDK.

*dwState*<br/>
Odwołanie do wartości DWORD zawierającej informacje o stanie. Może być jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Wybrano element kontrolki karta.|
|TCIS_HIGHLIGHTED|Element kontrolki karta zostanie wyróżniony, a karta i tekst są rysowane przy użyciu bieżącego koloru wyróżnienia. W przypadku korzystania z koloru wyróżnienia będzie to prawdziwa interpolacja, a nie kolorem.|

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

##  <a name="setmintabwidth"></a>CTabCtrl:: SetMinTabWidth

Ustawia minimalną szerokość elementów w kontrolce karty.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*CX*<br/>
Minimalna szerokość ustawiona dla elementu kontrolki karta. Jeśli ten parametr ma wartość-1, formant będzie używać domyślnej szerokości tabulatora.

### <a name="return-value"></a>Wartość zwrócona

Poprzednia minimalna szerokość tabulacji.

### <a name="return-value"></a>Wartość zwrócona

Ta funkcja członkowska implementuje zachowanie [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)komunikatu Win32, zgodnie z opisem w Windows SDK.

##  <a name="setpadding"></a>CTabCtrl:: setuzupełnienie

Ustawia ilość miejsca (uzupełnienie) wokół każdej karty i etykiety w kontrolce karty.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*zmienia*<br/>
Ustawia ilość miejsca (uzupełnienie) wokół każdej karty i etykiety w kontrolce karty.

##  <a name="settooltips"></a>CTabCtrl:: setetykietki narzędzi

Przypisuje formant etykietki narzędzia do kontrolki karta.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Uchwyt kontrolki etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Możesz uzyskać kontrolkę etykietki narzędzia skojarzoną z kontrolką karty, wykonując wywołanie do `GetToolTips`.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
