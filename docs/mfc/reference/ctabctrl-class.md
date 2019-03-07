---
title: CTabCtrl Class
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
ms.openlocfilehash: ccf35c7a036a69487d5138baf8c017f9c5995bef
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425019"
---
# <a name="ctabctrl-class"></a>CTabCtrl Class

Oferuje funkcje formantu typowej zakładki Windows.

## <a name="syntax"></a>Składnia

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Konstruuje `CTabCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Oblicza podane prostokąt okna obszaru wyświetlania kontrolki karty lub oblicza prostokąt okna, które będzie odpowiadać na obszarze wyświetlanej.|
|[CTabCtrl::Create](#create)|Tworzy formant karty i dołącza go do wystąpienia `CTabCtrl` obiektu.|
|[CTabCtrl::CreateEx](#createex)|Tworzy formant karty przy użyciu określonego stylów rozszerzonej Windows i dołącza go do wystąpienia `CTabCtrl` obiektu.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Usuwa wszystkie elementy z formantem karty.|
|[CTabCtrl::DeleteItem](#deleteitem)|Usuwa element z formantem karty.|
|[CTabCtrl::DeselectAll](#deselectall)|Resetuje elementów w kontrolce karty, usuwając zaznaczenie, które zostały naciśnięte.|
|[CTabCtrl::DrawItem](#drawitem)|Rysuje określony element z formantem karty.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Pobiera karty z bieżącym fokusem formant karty.|
|[CTabCtrl::GetCurSel](#getcursel)|Określa, czy aktualnie wybrana karta formantu karty|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są obecnie używane dla formantu karty.|
|[CTabCtrl::GetImageList](#getimagelist)|Pobiera listę obrazu skojarzonego z formantem karty.|
|[CTabCtrl::GetItem](#getitem)|Pobiera informacje o karcie w kontrolce karty.|
|[CTabCtrl::GetItemCount](#getitemcount)|Pobiera numer karty w kontrolce karty.|
|[CTabCtrl::GetItemRect](#getitemrect)|Pobiera prostokąt otaczający tabulatora w kontrolce karty.|
|[CTabCtrl::GetItemState](#getitemstate)|Pobiera stan element sterowania wskazany karty.|
|[CTabCtrl::GetRowCount](#getrowcount)|Pobiera bieżącą liczbę wierszy kart w kontrolce karty.|
|[CTabCtrl::GetToolTips](#gettooltips)|Pobiera uchwyt formantem etykietki narzędzia, które są skojarzone z formantem karty.|
|[CTabCtrl::HighlightItem](#highlightitem)|Ustawia stan Wyróżnij element karty.|
|[CTabCtrl::HitTest](#hittest)|Określa, które karty, znajduje się na pozycji określonego ekranu.|
|[CTabCtrl::InsertItem](#insertitem)|Wstawia nową kartę w kontrolce karty.|
|[CTabCtrl::RemoveImage](#removeimage)|Usuwa obraz z listy obrazów z formantem karty.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Ustawia fokus do określonej karty w kontrolce karty.|
|[CTabCtrl::SetCurSel](#setcursel)|Wybiera kartę w kontrolce karty.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla formantu zakładki.|
|[CTabCtrl::SetImageList](#setimagelist)|Przypisuje listy obrazów z formantem karty.|
|[CTabCtrl::SetItem](#setitem)|Ustawia niektóre lub wszystkie atrybuty karty.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Ustawia liczbę bajtów na znak tabulacji zarezerwowane dla danych aplikacji w kontrolce karty.|
|[CTabCtrl::SetItemSize](#setitemsize)|Ustawia szerokość i wysokość elementu.|
|[CTabCtrl::SetItemState](#setitemstate)|Ustawia stan element sterowania wskazany karty.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Ustawia minimalną szerokość elementów w kontrolce karty.|
|[CTabCtrl::SetPadding](#setpadding)|Określa ilość miejsca (dopełnienie) wokół każdej karcie ikonę i etykiety w kontrolce karty.|
|[CTabCtrl::SetToolTips](#settooltips)|Przypisuje formantem etykietki narzędzia do kontrolki karty.|

## <a name="remarks"></a>Uwagi

"Formant karty" jest odpowiednikiem separatorów w notesie lub etykiety w pliku cabinet. Korzystając z formantem karty, aplikację można zdefiniować wiele stron dla tego samego obszaru okno lub okno dialogowe. Każda strona zawiera zestaw informacji lub grupą elementów sterujących, które wyświetla aplikacji, gdy użytkownik wybierze odpowiednich kart. Specjalny rodzaj kontrolka karty wyświetla karty, które wyglądają jak przyciski. Kliknięcie przycisku należy natychmiast wykonać polecenia zamiast wyświetlania strony.

Ta kontrolka (i w związku z tym `CTabCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.

Aby uzyskać więcej informacji na temat korzystania z `CTabCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [korzystanie z CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect

Oblicza podane prostokąt okna obszaru wyświetlania kontrolki karty lub oblicza prostokąt okna, które będzie odpowiadać na obszarze wyświetlanej.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*bLarger*<br/>
Wskazuje do wykonywania kolejnej operacji. Jeśli ten parametr ma wartość TRUE, *lprect —* określa prostokątny obszar wyświetlania i odbiera prostokąt odpowiednie okna. Jeśli ten parametr ma wartość FALSE, *lprect —* Określa prostokąt okna i odbiera odpowiedniego prostokątny obszar wyświetlania.

*lpRect*<br/>
Wskaźnik do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) strukturę, która określa danego prostokąt i odbiera obliczony prostokąt.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>  CTabCtrl::Create

Tworzy formant karty i dołącza go do wystąpienia `CTabCtrl` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl kontrolki karty. Zastosuj dowolną kombinację [karcie Style kontrolki](/windows/desktop/Controls/tab-control-styles), które zostały opisane w zestawie Windows SDK. Zobacz **uwagi** listę Style okna, które również można zastosować do formantu.

*Rect*<br/>
Określa rozmiar i położenie formantu karty. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki karty, zwykle `CDialog`. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki karty.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli inicjowanie obiektu powiodła się. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Konstruowanie `CTabCtrl` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołaj `Create`, który tworzy formant karty i dołącza go do `CTabCtrl` obiektu.

Oprócz style kontrolki karty należy zastosować następujące style okna ramowego do formantu karty:

- WS_CHILD tworzy okno podrzędne, który reprezentuje formant karty. Nie można używać ze stylem WS_POPUP.

- WS_VISIBLE tworzy formant karty, które jest początkowo widoczne.

- WS_DISABLED tworzy okno, które jest początkowo wyłączone.

- WS_GROUP Określa pierwszy formant grupy formantów, w których użytkownik może przechodzić z jednego formantu do drugiego za pomocą klawiszy strzałek. Wszystkie formanty zdefiniowane przy użyciu stylu WS_GROUP po pierwszej kontroli należą do tej samej grupy. Następny formant ze stylem WS_GROUP kończy grupy stylów i rozpoczyna następną grupę (oznacza to, że jedna grupa kończy się gdzie rozpoczyna się następna).

- WS_TABSTOP określa jeden z wielu formantów, za pomocą których użytkownik może poruszać się używając klawisza TAB. Klawisz TAB przesuwa użytkownika do następnej kontrolki określonej przez styl WS_TABSTOP.

Aby utworzyć formant karty przy użyciu rozszerzone Style okna, należy wywołać [CTabCtrl::CreateEx](#createex) zamiast `Create`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>  CTabCtrl::CreateEx

Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CTabCtrl` obiektu.

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
Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki karty. Zastosuj dowolną kombinację [karcie Style kontrolki](/windows/desktop/Controls/tab-control-styles), które zostały opisane w zestawie Windows SDK. Zobacz **uwagi** w [Utwórz](#create) listę Style okna, które również można zastosować do formantu.

*Rect*<br/>
Odwołanie do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator formantu okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.

`CreateEx` Tworzy formant z rozszerzone style Windows określonego przez *dwExStyle*. Rozszerzone style specyficzne dla kontrolkę za pomocą zestawu [SetExtendedStyle](#setextendedstyle). Na przykład użyć `CreateEx` Ustaw takie style jako WS_EX_CONTEXTHELP, ale korzystać z `SetExtendedStyle` do ustawiania tych stylów jako tcs_ex_flatseparators —. Aby uzyskać więcej informacji, zobacz style opisanego w [style rozszerzone kontrolki karty](/windows/desktop/Controls/tab-control-extended-styles) w zestawie Windows SDK.

##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl

Konstruuje `CTabCtrl` obiektu.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems

Usuwa wszystkie elementy z formantem karty.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem

Usuwa określony element z formantem karty.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera wartość elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>  CTabCtrl::DeselectAll

Resetuje elementów w kontrolce karty, usuwając zaznaczenie, które zostały naciśnięte.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parametry

*fExcludeFocus*<br/>
Flaga, która określa zakres deselection elementu. Jeśli ten parametr ma wartość false, spowoduje zresetowanie wszystkich przycisków karty. Jeśli jest ustawiona na wartość TRUE, a następnie kartę wszystkich elementów z wyjątkiem aktualnie wybrany zostaną zresetowane.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie wiadomości Win32 [TCM_DESELECTALL](/windows/desktop/Controls/tcm-deselectall), zgodnie z opisem w zestawie Windows SDK.

##  <a name="drawitem"></a>  CTabCtrl::DrawItem

Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt rysowania przez właściciela karty Kontrola zmian.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) struktura zawierająca opis elementu do narysowania.

### <a name="remarks"></a>Uwagi

`itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CTabCtrl` obiektu.

Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed ten element członkowski funkcja kończy.

##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus

Pobiera indeks karty z bieżącym fokusem.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks karty z bieżącym fokusem.

##  <a name="getcursel"></a>  CTabCtrl::GetCurSel

Pobiera aktualnie wybrana karta w kontrolce karty.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks wybranej karty, jeśli kończy się pomyślnie lub - 1, jeśli karta nie jest zaznaczone.

##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle

Pobiera rozszerzone style, które są obecnie używane dla formantu karty.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Wartość zwracana

Reprezentuje rozszerzone style obecnie w przypadku formantu karty. Ta wartość jest kombinacją [kartę Kontrola style rozszerzone](/windows/desktop/Controls/tab-control-extended-styles), zgodnie z opisem w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TCM_GETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-getextendedstyle), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getimagelist"></a>  CTabCtrl::GetImageList

Pobiera listę obrazu który jest skojarzony z formantem karty.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wskaźnik do listy obrazów karty kontroli w przeciwnym razie wartość NULL.

##  <a name="getitem"></a>  CTabCtrl::GetItem

Pobiera informacje o karcie w kontrolce karty.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera indeks karty.

*pTabCtrlItem*<br/>
Wskaźnik do [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury, używane do określania informacji do pobrania. Umożliwia również odbierać informacje o karcie. Ta struktura jest używana z `InsertItem`, `GetItem`, i `SetItem` funkcji elementów członkowskich.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli to się powiedzie; Wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Po wysłaniu wiadomości `mask` elementu członkowskiego określa atrybuty do zwrócenia. Jeśli `mask` elementu członkowskiego określa wartość TCIF_TEXT `pszText` elementu członkowskiego musi zawierać adres buforu, który otrzymuje tekstu elementu i `cchTextMax` element członkowski, należy określić rozmiar buforu.

- `mask`

   Wartość określająca, które `TCITEM` elementy członkowskie można pobrać lub ustawić struktury. Ten element członkowski może być zero lub kombinacją następujących wartości:

   - TCIF_TEXT `pszText` elementu członkowskiego jest nieprawidłowy.

   - TCIF_IMAGE `iImage` elementu członkowskiego jest nieprawidłowy.

   - TCIF_PARAM `lParam` elementu członkowskiego jest nieprawidłowy.

   - TCIF_RTLREADING tekst z `pszText` jest wyświetlana przy użyciu kolejność czytania od prawej do lewej w systemach hebrajskiego i arabskiego.

   - TCIF_STATE `dwState` elementu członkowskiego jest nieprawidłowy.

- `pszText`

   Wskaźnik na ciąg zakończony wartością null zawierający tekst kartę, jeśli struktura zawiera informacje o karcie. Ten element członkowski, jeśli struktura otrzymuje informacje, określa adres buforu, który otrzymuje tekstu karty.

- `cchTextMax`

   Rozmiar buforu wskazywany przez `pszText`. Ten element członkowski jest ignorowana, jeśli struktura nie otrzymuje informacji.

- `iImage` Indeksuj do formantu karty listy obrazów lub - 1, jeśli nie ma żadnego obrazu dla karty.

- `lParam`

   Zdefiniowane przez aplikację dane skojarzone z kartą. Jeśli istnieje więcej niż czterech bajtów danych zdefiniowanych przez aplikację na znak tabulacji, aplikacji, należy zdefiniować strukturę i używać go zamiast `TCITEM` struktury. Pierwszego elementu członkowskiego struktury zdefiniowany przez aplikację muszą być [TCITEMHEADER](/windows/desktop/api/commctrl/ns-commctrl-tagtcitemheadera)struktury. `TCITEMHEADER` Struktura jest taka sama jak `TCITEM` strukturę, ale bez `lParam` elementu członkowskiego. Różnica między rozmiarem struktury i rozmiar `TCITEMHEADER` struktury powinna być równa liczbie dodatkowych bajtów na znak tabulacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount

Pobiera numer karty w kontrolce karty.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w kontrolce karty.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect

Pobiera prostokąt otaczający dla określonej karty w kontrolce karty.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera indeks elementu karty.

*lpRect*<br/>
Wskaźnik do [Prostokąt](/previous-versions/dd162897\(v=vs.85\)) strukturę, która odbiera prostokąt otaczający karty. Tych współrzędnych w trybie okienka ekranu bieżące mapowania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>  CTabCtrl::GetItemState

Pobiera stan element kontrolki karty, które są identyfikowane za pomocą *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera numer indeksu elementu, dla którego mają zostać pobrane informacje o stanie.

*dwMask*<br/>
Maska określający, którego stan elementu flagi do zwrócenia. Na listę wartości, zobacz maski członkiem [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury, zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do wartości DWORD odbieranie informacji o stanie. Może być jednym z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Wybrano element kontrolki karty.|
|TCIS_HIGHLIGHTED|Element kontrolki karty zostanie wyróżniona, a karta i tekst są rysowane przy użyciu bieżący kolor wyróżnienia. Korzystając z kolor wyróżnienia, będzie to wartość true, interpolacji, a nie kolor symulowany.|

### <a name="remarks"></a>Uwagi

Stan elementu jest określona przez `dwState` członkiem `TCITEM` struktury.

##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount

Pobiera bieżącą liczbę wierszy w kontrolce karty.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wierszy kart w kontrolce karty.

### <a name="remarks"></a>Uwagi

Tylko formanty karty, które mają styl TCS_MULTILINE może mieć wiele wierszy kart.

##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips

Pobiera uchwyt formantem etykietki narzędzia, które są skojarzone z formantem karty.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt formantem etykietki narzędzia w przypadku powodzenia; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Formant karty tworzy formantem etykietki narzędzia, jeśli ma on styl TCS_TOOLTIPS. Formantem etykietki narzędzia można przypisać do formantu karty, za pomocą `SetToolTips` funkcja elementu członkowskiego.

##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem

Ustawia stan Wyróżnij element karty.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parametry

*idItem*<br/>
Liczony od zera indeks elementu kontrolki karty.

*fHighlight*<br/>
Wartość określająca stan wyróżnienia do ustawienia. Jeśli ta wartość wynosi TRUE, jest wyróżniona karcie; w przypadku wartości FAŁSZ karcie ustawiono do stanu domyślnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje komunikat Win32 [TCM_HIGHLIGHTITEM](/windows/desktop/Controls/tcm-highlightitem), zgodnie z opisem w zestawie Windows SDK.

##  <a name="hittest"></a>  CTabCtrl::HitTest

Określa, które karty, znajduje się na pozycji określonego ekranu.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parametry

*pHitTestInfo*<br/>
Wskaźnik do [TCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtchittestinfo) struktury, zgodnie z opisem w zestawie SDK Windows, która określa położenie ekranu do testowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczony od zera indeks karty lub - 1, jeśli karta nie znajduje się na określonej pozycji.

##  <a name="insertitem"></a>  CTabCtrl::InsertItem

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
Liczony od zera indeks w nowej karcie.

*pTabCtrlItem*<br/>
Wskaźnik do [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) strukturę, która określa atrybuty, które karty.

*lpszItem*<br/>
Adres ciąg zakończony wartością null zawierający tekst, na karcie.

*nImage*<br/>
Liczony od zera indeks obrazu, aby wstawić z listy obrazów.

*nMask*<br/>
Określa, która `TCITEM` struktury atrybuty do ustawienia. Może to być wartość zero lub kombinację następujących wartości:

- TCIF_TEXT `pszText` elementu członkowskiego jest nieprawidłowy.

- TCIF_IMAGE `iImage` elementu członkowskiego jest nieprawidłowy.

- TCIF_PARAM *lParam* elementu członkowskiego jest nieprawidłowy.

- TCIF_RTLREADING tekst z `pszText` jest wyświetlana przy użyciu kolejność czytania od prawej do lewej w systemach hebrajskiego i arabskiego.

- TCIF_STATE *dwState* elementu członkowskiego jest nieprawidłowy.

*lParam*<br/>
Zdefiniowane przez aplikację dane skojarzone z kartą.

*dwState*<br/>
Określa wartości dla stanów elementu. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) w zestawie Windows SDK.

*dwStateMask*<br/>
Określa, które stany mają być tworzone. Aby uzyskać więcej informacji, zobacz [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks w nowej karcie w przypadku powodzenia; w przeciwnym razie - 1.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>  CTabCtrl::RemoveImage

Usuwa określony obraz z listy obrazów z formantem karty.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parametry

*nImage*<br/>
Liczony od zera indeks obrazu do usunięcia.

### <a name="remarks"></a>Uwagi

Kontrolka karty aktualizuje indeks obrazu każdej karcie tak, aby każda karta pozostają skojarzone z tego samego obrazu.

##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus

Ustawia fokus do określonej karty w kontrolce karty.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Określa indeks kartę która pobiera fokus.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TCM_SETCURFOCUS](/windows/desktop/Controls/tcm-setcurfocus), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setcursel"></a>  CTabCtrl::SetCurSel

Wybiera kartę w kontrolce karty.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera indeks elementu do wybrania.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks wcześniej wybranej karty, jeśli to się powiedzie, w przeciwnym razie - 1.

### <a name="remarks"></a>Uwagi

Formant karty nie wysyła komunikat z powiadomieniem TCN_SELCHANGING lub TCN_SELCHANGE po wybraniu karty, za pomocą tej funkcji. Te powiadomienia są wysyłane przy użyciu WM_NOTIFY, gdy użytkownik kliknie przycisk lub korzysta z klawiatury można zmienić karty.

##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle

Ustawia rozszerzone style dla formantu zakładki.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parametry

*dwNewStyle*<br/>
Wartość określająca kombinacji kartę kontroli rozszerzone style.

*dwExMask*<br/>
Wartość DWORD, która wskazuje, style, które w *dwNewStyle* są, których to dotyczy. Style rozszerzone w *dwExMask* zostaną zmienione. Innymi stylami zostanie zachowana, ponieważ jest. Jeśli ten parametr ma wartość zero, a następnie wszystkie style w *dwNewStyle* zostaną zmienione.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD, która zawiera poprzedniej [kartę Kontrola style rozszerzone](/windows/desktop/Controls/tab-control-extended-styles), zgodnie z opisem w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TCM_SETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-setextendedstyle), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setimagelist"></a>  CTabCtrl::SetImageList

Przypisuje listy obrazów z formantem karty.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Wskaźnik do listy obrazu, który ma być przypisane do formantu karty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik na poprzedniej liście obrazu lub wartość NULL, jeśli nie określono żadnych poprzednich listy obrazów.

##  <a name="setitem"></a>  CTabCtrl::SetItem

Ustawia niektóre lub wszystkie atrybuty karty.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera indeks elementu.

*pTabCtrlItem*<br/>
Wskaźnik do [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) strukturę, która zawiera nowe atrybuty elementu. `mask` Elementu członkowskiego określa atrybuty, które można ustawić. Jeśli `mask` elementu członkowskiego określa wartość TCIF_TEXT `pszText` elementu członkowskiego jest adresem ciąg zakończony znakiem null i `cchTextMax` element jest ignorowany.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="example"></a>Przykład

  Zobacz przykład [GetItem](#getitem).

##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra

Ustawia liczbę bajtów na znak tabulacji zarezerwowane dla danych aplikacji w kontrolce karty.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba dodatkowych bajtów do ustawienia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TCM_SETITEMEXTRA](/windows/desktop/Controls/tcm-setitemextra), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize

Ustawia szerokość i wysokość karty elementy sterowania.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Nową szerokość i wysokość w pikselach elementów kontrolki karty.

### <a name="return-value"></a>Wartość zwracana

Zwraca stare szerokości i wysokości elementów kontrolki karty.

##  <a name="setitemstate"></a>  CTabCtrl::SetItemState

Ustawia stan element kontrolki karty, które są identyfikowane za pomocą *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
Liczony od zera numer indeksu elementu, dla której chcesz ustawić informacje o stanie.

*dwMask*<br/>
Maska określający, którego stan elementu flagi do ustawienia. Na listę wartości, zobacz maski członkiem [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) struktury, zgodnie z opisem w zestawie Windows SDK.

*dwState*<br/>
Odwołanie do wartości DWORD, zawierający informacje o stanie. Może być jednym z następujących wartości:

|Wartość|Opis|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Wybrano element kontrolki karty.|
|TCIS_HIGHLIGHTED|Element kontrolki karty zostanie wyróżniona, a karta i tekst są rysowane przy użyciu bieżący kolor wyróżnienia. Korzystając z kolor wyróżnienia, będzie to wartość true, interpolacji, a nie kolor symulowany.|

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth

Ustawia minimalną szerokość elementów w kontrolce karty.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parametry

*cx*<br/>
Minimalna szerokość należy ustawić dla elementu kontrolki karty. Jeśli ten parametr jest ustawiona na wartość -1, kontrolka będzie używać domyślnej szerokości karty.

### <a name="return-value"></a>Wartość zwracana

Poprzednie szerokość minimalna kartę.

### <a name="return-value"></a>Wartość zwracana

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TCM_SETMINTABWIDTH](/windows/desktop/Controls/tcm-setmintabwidth), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setpadding"></a>  CTabCtrl::SetPadding

Określa ilość miejsca (dopełnienie) wokół każdej karcie ikonę i etykiety w kontrolce karty.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parametry

*Rozmiar*<br/>
Określa ilość miejsca (dopełnienie) wokół każdej karcie ikonę i etykiety w kontrolce karty.

##  <a name="settooltips"></a>  CTabCtrl::SetToolTips

Przypisuje formantem etykietki narzędzia do kontrolki karty.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parametry

*pWndTip*<br/>
Dojście formantem etykietki narzędzia.

### <a name="remarks"></a>Uwagi

Możesz uzyskać formantem etykietki narzędzia, które są skojarzone z formantem karty, wywołuje element `GetToolTips`.

### <a name="example"></a>Przykład

  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Zobacz także

[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
