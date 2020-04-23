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
ms.openlocfilehash: 42d4b24222b1760bc418e904881edb2bb0e5a1f4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752308"
---
# <a name="ctabctrl-class"></a>Klasa CTabCtrl

Udostępnia funkcje wspólnej kontrolki karty systemu Windows.

## <a name="syntax"></a>Składnia

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Konstruuje `CTabCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Oblicza obszar wyświetlania formantu karty, biorąc pod uwagę prostokąt okna, lub oblicza prostokąt okna, który odpowiadałby danemu obszarowi wyświetlania.|
|[CTabCtrl::Utwórz](#create)|Tworzy formant karty i dołącza go `CTabCtrl` do wystąpienia obiektu.|
|[CTabCtrl::CreateEx](#createex)|Tworzy formant karty z określonymi stylami rozszerzonymi systemu `CTabCtrl` Windows i dołącza go do wystąpienia obiektu.|
|[CTabCtrl::DeleteWszystkie elementy](#deleteallitems)|Usuwa wszystkie elementy z kontrolki karty.|
|[CTabCtrl::DeleteItem](#deleteitem)|Usuwa element z kontrolki karty.|
|[CTabCtrl::DselectAll](#deselectall)|Resetuje elementy w formancie karty, czyszcząc wszystkie, które zostały naciśnięte.|
|[CTabCtrl::DrawItem](#drawitem)|Rysuje określony element kontrolki karty.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Pobiera kartę z bieżącym fokusem kontrolki karty.|
|[CTabCtrl::GetCurSel](#getcursel)|Określa aktualnie zaznaczoną kartę w formancie karty.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są obecnie używane dla formantu karty.|
|[CTabCtrl::Lista GetImage](#getimagelist)|Pobiera listę obrazów skojarzoną z kontrolką kart.|
|[CTabCtrl::GetItem](#getitem)|Pobiera informacje o karcie w formancie karty.|
|[CTabCtrl::GetItemCount](#getitemcount)|Pobiera liczbę kart w formancie karty.|
|[CTabCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt ograniczający dla karty w formancie karty.|
|[CTabCtrl::GetItemState](#getitemstate)|Pobiera stan wskazanego elementu kontroli karty.|
|[CTabCtrl::GetRowCount](#getrowcount)|Pobiera bieżącą liczbę wierszy kart w formancie karty.|
|[CTabCtrl::Porady dotyczące właściwości GetTool](#gettooltips)|Pobiera uchwyt formantu etykietki narzędzia skojarzonej z kontrolką tabulacji.|
|[CTabCtrl::HighlightItem](#highlightitem)|Ustawia stan podświetlenia elementu karty.|
|[CTabCtrl::HitTest](#hittest)|Określa, która karta, jeśli istnieje, znajduje się w określonej pozycji ekranu.|
|[CTabCtrl::InsertItem](#insertitem)|Wstawia nową kartę w formancie kart.|
|[CTabCtrl::UsuńImage](#removeimage)|Usuwa obraz z listy obrazów formantu karty.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Ustawia fokus na określoną kartę w formancie karty.|
|[CTabCtrl::SetCurSel](#setcursel)|Wybiera kartę w formancie kart.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla kontrolki kart.|
|[CTabCtrl::SetImageList](#setimagelist)|Przypisuje listę obrazów do kontrolki kart.|
|[CTabCtrl::SetItem](#setitem)|Ustawia niektóre lub wszystkie atrybuty karty.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Ustawia liczbę bajtów na kartę zarezerwowaną dla danych zdefiniowanych przez aplikację w formancie karty.|
|[CTabCtrl::SetItemSize](#setitemsize)|Ustawia szerokość i wysokość elementu.|
|[CTabCtrl::Stan zestawu](#setitemstate)|Ustawia stan wskazanego elementu kontroli tabulacji.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Ustawia minimalną szerokość elementów w formancie karty.|
|[CTabCtrl::SetPadding](#setpadding)|Ustawia ilość miejsca (dopełnienie) wokół każdej karty ikony i etykiety w kontrolki karty.|
|[CTabCtrl::SetToolTips](#settooltips)|Przypisuje kontrolkę etykietki narzędzia do kontrolki kart.|

## <a name="remarks"></a>Uwagi

"Kontrolka kart" jest analogiczna do dzielników w notesie lub etykiet w szafce plików. Za pomocą kontrolki karty aplikacja może zdefiniować wiele stron dla tego samego obszaru okna lub okna dialogowego. Każda strona składa się z zestawu informacji lub grupy formantów wyświetlanych przez aplikację, gdy użytkownik wybierze odpowiednią kartę. Specjalny typ kontrolki kart wyświetla karty, które wyglądają jak przyciski. Kliknięcie przycisku powinno natychmiast wykonać polecenie zamiast wyświetlania strony.

Ten formant (i `CTabCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemach Windows 95/98 i Windows NT w wersji 3.51 lub nowszych.

Aby uzyskać więcej `CTabCtrl`informacji na temat używania , zobacz [Formanty](../../mfc/controls-mfc.md) i [Korzystanie z CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect

Oblicza obszar wyświetlania formantu karty, biorąc pod uwagę prostokąt okna, lub oblicza prostokąt okna, który odpowiadałby danemu obszarowi wyświetlania.

```cpp
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bLarger*<br/>
Wskazuje, którą operację wykonać. Jeśli ten parametr ma wartość PRAWDA, *lpRect* określa prostokąt wyświetlania i odbiera odpowiedni prostokąt okna. Jeśli ten parametr ma wartość FAŁSZ, *lpRect* określa prostokąt okna i odbiera odpowiedni prostokąt wyświetlania.

*Lprect*<br/>
Wskaźnik do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która określa dany prostokąt i odbiera obliczony prostokąt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Utwórz

Tworzy formant karty i dołącza go `CTabCtrl` do wystąpienia obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl formantu karty. Zastosuj dowolną [kombinację stylów sterowania kartami,](/windows/win32/Controls/tab-control-styles)opisaną w zestawie Windows SDK. Zobacz **Uwagi** dla listy stylów okien, które można również zastosować do formantu.

*Rect*<br/>
Określa rozmiar i położenie formantu karty. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne formantu karty, zwykle `CDialog`. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu karty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli inicjowanie obiektu zakończyło się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Konstruowanie `CTabCtrl` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, `Create`a następnie wywołaj , co `CTabCtrl` tworzy formant karty i dołącza go do obiektu.

Oprócz stylów sterowania tabulatorami do formantu karty można zastosować następujące style okien:

- WS_CHILD Tworzy okno podrzędne, które reprezentuje formant karty. Nie można używać ze stylem WS_POPUP.

- WS_VISIBLE Tworzy formant karty, który jest początkowo widoczny.

- WS_DISABLED Tworzy okno, które jest początkowo wyłączone.

- WS_GROUP Określa pierwszy formant grupy formantów, w którym użytkownik może przechodzić z jednego formantu do następnego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane za pomocą stylu WS_GROUP po pierwszym formancie należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupę stylów i rozpoczyna następną grupę (oznacza to, że jedna grupa kończy się w miejscu rozpoczęcia następnego).

- WS_TABSTOP Określa jedną z wielu formantów, za pomocą których użytkownik może się poruszać za pomocą klawisza TAB. Klawisz TAB przenosi użytkownika do następnego formantu określonego przez styl WS_TABSTOP.

Aby utworzyć kontrolkę karty z rozszerzonymi stylami okien, należy wywołać [CTabCtrl::CreateEx](#createex) zamiast `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx

Tworzy formant (okno podrzędne) i `CTabCtrl` kojarzy go z obiektem.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwexstyle*<br/>
Określa rozszerzony styl tworzonego formantu. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Określa styl formantu karty. Zastosuj dowolną [kombinację stylów sterowania kartami,](/windows/win32/Controls/tab-control-styles)opisaną w zestawie Windows SDK. Zobacz **Uwagi** w [Tworzenie](#create) listy stylów okien, które można również zastosować do formantu.

*Rect*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie inaczej 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Create,](#create) aby zastosować rozszerzone style systemu Windows, określone przez przedmową styl rozszerzony systemu Windows **WS_EX_**.

`CreateEx`tworzy formant z rozszerzonymi stylami systemu Windows określonymi przez *dwExStyle*. Ustaw rozszerzone style specyficzne dla formantu za pomocą [SetExtendedStyle](#setextendedstyle). Na przykład `CreateEx` można użyć do ustawiania takich `SetExtendedStyle` stylów, jak WS_EX_CONTEXTHELP, ale służy do ustawiania takich stylów, jak TCS_EX_FLATSEPARATORS. Aby uzyskać więcej informacji, zobacz style opisane w [obszarze Rozszerzone style kontroli kart](/windows/win32/Controls/tab-control-extended-styles) w zestawie Windows SDK.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl

Konstruuje `CTabCtrl` obiekt.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteWszystkie elementy

Usuwa wszystkie elementy z kontrolki karty.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem

Usuwa określony element z kontrolki karty.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Wartość od zera elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DselectAll

Resetuje elementy w formancie karty, czyszcząc wszystkie, które zostały naciśnięte.

```cpp
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fSkusjaFocus*<br/>
Flaga, która określa zakres deselekcji elementu. Jeśli ten parametr jest ustawiony na FAŁSZ, wszystkie przyciski kart zostaną zresetowane. Jeśli jest ustawiona na WARTOŚĆ PRAWDA, wszystkie elementy karty z wyjątkiem aktualnie wybranego zostaną zresetowane.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), zgodnie z opisem w windows SDK.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem

Wywoływana przez strukturę, gdy zmienia się wizualny aspekt kontroli karty rysowania właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) struktury opisujące element, który ma być malowany.

### <a name="remarks"></a>Uwagi

Element `itemAction` członkowski `DRAWITEMSTRUCT` konstrukcji definiuje akcję rysowania, która ma być wykonana.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CTabCtrl` właściciela.

Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetCurFocus

Pobiera indeks karty z bieżącym fokusem.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera karty z bieżącym fokusem.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel

Pobiera aktualnie wybraną kartę w formancie karty.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera wybranej karty, jeśli zakończy się pomyślnie lub - 1, jeśli nie wybrano żadnej karty.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle

Pobiera rozszerzone style, które są obecnie używane dla formantu karty.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Wartość zwracana

Reprezentuje rozszerzone style obecnie używane dla formantu karty. Ta wartość jest kombinacją [rozszerzonych stylów kontroli kart,](/windows/win32/Controls/tab-control-extended-styles)zgodnie z opisem w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::Lista GetImage

Pobiera listę obrazów skojarzoną z kontrolką kart.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wskaźnik do listy obrazów formantu karty; w przeciwnym razie NULL.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem

Pobiera informacje o karcie w formancie karty.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Indeks od zera karty.

*pTabCtrlItem*<br/>
Wskaźnik do struktury [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) używany do określania informacji do pobrania. Służy również do odbierania informacji o karcie. Ta struktura jest `InsertItem`używana `GetItem`z `SetItem` funkcjami , i elementami członkowskimi.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Po wysłaniu wiadomości `mask` element członkowski określa, które atrybuty mają być zwracane. Jeśli `mask` element członkowski określa wartość TCIF_TEXT, `pszText` element członkowski musi zawierać adres buforu, `cchTextMax` który odbiera tekst elementu, a element członkowski musi określić rozmiar buforu.

- `mask`

   Wartość określająca `TCITEM` elementy struktury do pobrania lub ustawionego. Ten element członkowski może być zerowy lub kombinacją następujących wartości:

  - TCIF_TEXT Element `pszText` członkowski jest prawidłowy.

  - TCIF_IMAGE Element `iImage` członkowski jest prawidłowy.

  - TCIF_PARAM Element `lParam` członkowski jest prawidłowy.

  - TCIF_RTLREADING Tekst `pszText` jest wyświetlany przy użyciu kolejności czytania od prawej do lewej w systemach hebrajskich lub arabskich.

  - TCIF_STATE Element `dwState` członkowski jest prawidłowy.

- `pszText`

   Wskaźnik do ciągu zakończonego wartością null zawierającego tekst karty, jeśli struktura zawiera informacje o karcie. Jeśli struktura otrzymuje informacje, ten element członkowski określa adres buforu, który odbiera tekst karty.

- `cchTextMax`

   Wielkość bufora wskazana `pszText`przez . Ten element członkowski jest ignorowany, jeśli struktura nie odbiera informacji.

- `iImage`Indeks na liście obrazów formantu karty lub - 1, jeśli nie ma obrazu dla karty.

- `lParam`

   Dane zdefiniowane przez aplikację skojarzone z kartą. Jeśli na karcie jest więcej niż cztery bajty danych zdefiniowanych przez aplikację, aplikacja `TCITEM` musi zdefiniować strukturę i używać jej zamiast struktury. Pierwszym elementem struktury zdefiniowanej przez aplikację musi być struktura [TCITEMHEADER.](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw) Struktura `TCITEMHEADER` jest identyczna `TCITEM` ze strukturą, ale bez elementu `lParam` członkowskiego. Różnica między rozmiarem struktury a rozmiarem `TCITEMHEADER` struktury powinna być równa liczbie dodatkowych bajtów na kartę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount

Pobiera liczbę kart w formancie karty.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w formancie karty.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect

Pobiera prostokąt ograniczający dla określonej karty w formancie karty.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Indeks od zera elementu karty.

*Lprect*<br/>
Wskaźnik do struktury [RECT,](/windows/win32/api/windef/ns-windef-rect) która odbiera prostokąt ograniczający kartę. Współrzędne te wykorzystują bieżący tryb mapowania rzutni.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState

Pobiera stan elementu kontroli karty identyfikowanego przez *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Numer indeksu od zera elementu, dla którego mają być pobierane informacje o stanie.

*Dwmask*<br/>
Maska określająca, która z flag państwowych elementu ma powrócić. Aby uzyskać listę wartości, zobacz element członkowski maski struktury [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości DWORD odbierającej informacje o stanie. Może być jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Zostanie wybrany element formantu karty.|
|TCIS_HIGHLIGHTED|Element formantu karty zostanie wyróżniony, a karta i tekst są rysowane przy użyciu bieżącego koloru podświetlenia. Podczas korzystania z koloru podświetlenia, będzie to prawdziwa interpolacja, a nie roztrząsany kolor.|

### <a name="remarks"></a>Uwagi

Stan elementu jest określony przez `dwState` element `TCITEM` członkowski struktury.

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount

Pobiera bieżącą liczbę wierszy w formancie karty.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy kart w formancie kart.

### <a name="remarks"></a>Uwagi

Tylko kontrolki kart, które mają styl TCS_MULTILINE, mogą mieć wiele wierszy kart.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::Porady dotyczące właściwości GetTool

Pobiera uchwyt formantu etykietki narzędzia skojarzonej z kontrolką tabulacji.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt kontrolki narzędzia, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Formant tabulacji tworzy kontrolkę etykietki narzędzia, jeśli ma styl TCS_TOOLTIPS. Można również przypisać kontrolkę etykietki narzędzia `SetToolTips` do formantu karty za pomocą funkcji elementu członkowskiego.

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::HighlightItem

Ustawia stan podświetlenia elementu karty.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idItem*<br/>
Indeks od zera elementu kontroli karty.

*fWysokiejszy*<br/>
Wartość określająca stan podświetlenia, który ma zostać ustawiony. Jeśli ta wartość ma wartość PRAWDA, karta jest wyróżniona; jeśli FALSE, karta jest ustawiona na stan domyślny.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje komunikat Win32 [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), zgodnie z opisem w windows SDK.

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest

Określa, która karta, jeśli istnieje, znajduje się w określonej pozycji ekranu.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Wskaźnik do struktury [TCHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) zgodnie z opisem w windows SDK, który określa położenie ekranu do testowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca indeks od zera karty lub - 1, jeśli żadna karta nie znajduje się w określonej pozycji.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::InsertItem

Wstawia nową kartę w istniejącej kontrolki kart.

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

*nJejsza*<br/>
Indeks od zera nowej karty.

*pTabCtrlItem*<br/>
Wskaźnik do struktury [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) który określa atrybuty karty.

*lpszItem*<br/>
Adres ciągu zakończonego wartością null, który zawiera tekst karty.

*nImage (Obraz)*<br/>
Indeks od zera obrazu do wstawienia z listy obrazów.

*nMask*<br/>
Określa, `TCITEM` które atrybuty struktury mają być ustawione. Może być równa zero lub kombinacja następujących wartości:

- TCIF_TEXT Element `pszText` członkowski jest prawidłowy.

- TCIF_IMAGE Element `iImage` członkowski jest prawidłowy.

- TCIF_PARAM Element członkowski *lParam* jest ważny.

- TCIF_RTLREADING Tekst `pszText` jest wyświetlany przy użyciu kolejności czytania od prawej do lewej w systemach hebrajskich lub arabskich.

- TCIF_STATE Element członkowski *dwState* jest prawidłowy.

*Lparam*<br/>
Dane zdefiniowane przez aplikację skojarzone z kartą.

*dwPaństwo*<br/>
Określa wartości stanów elementu. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) w windows SDK.

*dwStateMask (Mask)*<br/>
Określa, które stany mają być ustawione. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera nowej karty, jeśli zakończy się pomyślnie; w przeciwnym razie - 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::UsuńImage

Usuwa określony obraz z listy obrazów formantu karty.

```cpp
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage (Obraz)*<br/>
Indeks oparty na wartości zerowej obrazu do usunięcia.

### <a name="remarks"></a>Uwagi

Formant karty aktualizuje indeks obrazu każdej karty, dzięki czemu każda karta pozostaje skojarzona z tym samym obrazem.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetCurFocus

Ustawia fokus na określoną kartę w formancie karty.

```cpp
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Określa indeks karty, która pobiera fokus.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel

Wybiera kartę w formancie kart.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Indeks od zera elementu, który ma zostać wybrany.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera wcześniej wybranej karty, jeśli zakończy się pomyślnie, w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Formant karty nie wysyła komunikatu TCN_SELCHANGING lub powiadomienia TCN_SELCHANGE, gdy karta jest zaznaczona za pomocą tej funkcji. Powiadomienia te są wysyłane, używając WM_NOTIFY, gdy użytkownik kliknie lub użyj klawiatury do zmiany kart.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle

Ustawia rozszerzone style dla kontrolki kart.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNowstyle*<br/>
Wartość określająca kombinację rozszerzonych stylów kontroli tabulacji.

*dwExMask (maseczka dwEx)*<br/>
Wartość DWORD, która wskazuje, które style w *dwNewStyle* mają mieć wpływ. Zmienią się tylko rozszerzone style w *dwExMask.* Wszystkie inne style zostaną zachowane w stanie, w jakim jest. Jeśli ten parametr wynosi zero, to wszystkie style w *dwNewStyle* będzie miało wpływ.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawierająca poprzednie [style rozszerzone fortujki karty,](/windows/win32/Controls/tab-control-extended-styles)zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Ta funkcja elementu członkowskiego implementuje zachowanie [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList

Przypisuje listę obrazów do kontrolki kart.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList (Lista pImage)*<br/>
Wskaźnik do listy obrazów, który ma być przypisany do kontrolki karty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej listy obrazów lub wartości NULL, jeśli nie ma poprzedniej listy obrazów.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem

Ustawia niektóre lub wszystkie atrybuty karty.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Indeks od zera towaru.

*pTabCtrlItem*<br/>
Wskaźnik do struktury [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) która zawiera nowe atrybuty elementu. Element `mask` członkowski określa, które atrybuty mają być ustawione. Jeśli `mask` element członkowski określa wartość TCIF_TEXT, `pszText` element członkowski jest adresem ciągu `cchTextMax` zakończonego zerem, a element członkowski jest ignorowany.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [getitem](#getitem).

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra

Ustawia liczbę bajtów na kartę zarezerwowaną dla danych zdefiniowanych przez aplikację w formancie karty.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Liczba dodatkowych bajtów do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize

Ustawia szerokość i wysokość elementów kontrolnych tabulacji.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Nowa szerokość i wysokość elementów sterujących kartą w pikselach.

### <a name="return-value"></a>Wartość zwracana

Zwraca starą szerokość i wysokość elementów kontrolnych tabulacji.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::Stan zestawu

Ustawia stan elementu kontroli karty identyfikowanego przez *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
Numer indeksu od zera elementu, dla którego mają być ustawione informacje o stanie.

*Dwmask*<br/>
Maska określająca, którą z flag państwowych elementu należy ustawić. Aby uzyskać listę wartości, zobacz element członkowski maski struktury [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) zgodnie z opisem w zestawie Windows SDK.

*dwPaństwo*<br/>
Odwołanie do wartości DWORD zawierającej informacje o stanie. Może być jedną z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Zostanie wybrany element formantu karty.|
|TCIS_HIGHLIGHTED|Element formantu karty zostanie wyróżniony, a karta i tekst są rysowane przy użyciu bieżącego koloru podświetlenia. Podczas korzystania z koloru podświetlenia, będzie to prawdziwa interpolacja, a nie roztrząsany kolor.|

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth

Ustawia minimalną szerokość elementów w formancie karty.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*Cx*<br/>
Minimalna szerokość, która ma być ustawiona dla elementu kontroli tabulacji. Jeśli ten parametr jest ustawiony na -1, formant użyje domyślnej szerokości karty.

### <a name="return-value"></a>Wartość zwracana

Poprzednia minimalna szerokość karty.

### <a name="return-value"></a>Wartość zwracana

Ta funkcja elementu członkowskiego implementuje zachowanie [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding

Ustawia ilość miejsca (dopełnienie) wokół każdej karty ikony i etykiety w kontrolki karty.

```cpp
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Ustawia ilość miejsca (dopełnienie) wokół każdej karty ikony i etykiety w kontrolki karty.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::SetToolTips

Przypisuje kontrolkę etykietki narzędzia do kontrolki kart.

```cpp
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWdTip*<br/>
Uchwyt kontrolki narzędzia.

### <a name="remarks"></a>Uwagi

Możesz uzyskać kontrolkę etykietki narzędzia skojarzoną z `GetToolTips`kontrolką kart, nawiązując połączenie z programem .

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Zobacz też

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
