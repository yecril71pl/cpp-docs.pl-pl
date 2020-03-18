---
title: Klasa CListBox
description: Opis klasy MFC CListBox i jej funkcji składowych.
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420338"
---
# <a name="clistbox-class"></a>Klasa CListBox

Oferuje funkcje pola listy systemu Windows.

## <a name="syntax"></a>Składnia

```
class CListBox : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CListBox:: CListBox](#clistbox)|Konstruuje obiekt `CListBox`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CListBox:: AddString](#addstring)|Dodaje ciąg do pola listy.|
|[CListBox:: CharToItem](#chartoitem)|Przesłoń, aby zapewnić niestandardową obsługę WM_CHAR dla pól listy rysowania przez właściciela, które nie zawierają ciągów.|
|[CListBox:: CompareItem](#compareitem)|Wywoływane przez platformę, by określić pozycję nowego elementu w sortowanym polu listy rozwijanej przez właściciela.|
|[CListBox:: Create](#create)|Tworzy pole listy systemu Windows i dołącza je do obiektu `CListBox`.|
|[CListBox::D eleteItem](#deleteitem)|Wywoływane przez platformę, gdy użytkownik usuwa element z pola listy rysowania przez właściciela.|
|[CListBox::D eleteString](#deletestring)|Usuwa ciąg z pola listy.|
|[CListBox::D IR](#dir)|Dodaje nazwy plików, dyski lub oba z bieżącego katalogu do pola listy.|
|[CListBox::D rawItem](#drawitem)|Wywoływane przez platformę, gdy wizualny aspekt pola listy rysowania przez właściciela zmienia się.|
|[CListBox:: FindStr](#findstring)|Wyszukuje ciąg w polu listy.|
|[CListBox:: FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pola listy, który pasuje do określonego ciągu.|
|[CListBox:: GetAnchorIndex](#getanchorindex)|Pobiera indeks (liczony od zera) bieżącego elementu zakotwiczenia w polu listy.|
|[CListBox:: GetCaretIndex](#getcaretindex)|Określa indeks elementu, który ma prostokąt fokus w polu listy wielokrotnego wyboru.|
|[CListBox:: GetCount](#getcount)|Zwraca liczbę ciągów w polu listy.|
|[CListBox:: GetCurSel](#getcursel)|Zwraca indeks (liczony od zera) aktualnie zaznaczonego ciągu w polu listy.|
|[CListBox:: GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, którą pole listy można przewijać w poziomie.|
|[CListBox:: GetItemData](#getitemdata)|Zwraca wartość skojarzoną z elementem listy.|
|[CListBox:: GetItemDataPtr](#getitemdataptr)|Zwraca wskaźnik do elementu pola listy.|
|[CListBox:: GetItemHeight](#getitemheight)|Określa wysokość elementów w polu listy.|
|[CListBox:: GetItemRect](#getitemrect)|Zwraca prostokąt ograniczenia elementu listy, który jest aktualnie wyświetlany.|
|[CListBox:: GetListBoxInfo](#getlistboxinfo)|Pobiera liczbę elementów na kolumnę.|
|[CListBox:: getLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola listy.|
|[CListBox:: GetSel](#getsel)|Zwraca stan zaznaczenia elementu listy.|
|[CListBox:: GetSelCount](#getselcount)|Zwraca liczbę ciągów aktualnie wybranych w polu listy wielokrotnego wyboru.|
|[CListBox:: GetSelItems](#getselitems)|Zwraca indeksy ciągów aktualnie wybranych w polu listy.|
|[CListBox:: gettext](#gettext)|Kopiuje element pola listy do buforu.|
|[CListBox:: GetTextLen](#gettextlen)|Zwraca długość w bajtach elementu pola listy.|
|[CListBox:: GetTopIndex](#gettopindex)|Zwraca indeks pierwszego widocznego ciągu w polu listy.|
|[CListBox:: InitStorage](#initstorage)|Wstępnie przydziela bloki pamięci dla elementów pola listy i ciągów.|
|[CListBox:: InsertString](#insertstring)|Wstawia ciąg w określonej lokalizacji w polu listy.|
|[CListBox:: ItemFromPoint](#itemfrompoint)|Zwraca indeks elementu pola listy znajdującego się w najbliższym punkcie.|
|[CListBox:: MeasureItem](#measureitem)|Wywoływane przez platformę, gdy zostanie utworzone pole listy rysowania przez właściciela, aby określić wymiary pola listy.|
|[CListBox:: ResetContent](#resetcontent)|Czyści wszystkie wpisy w polu listy.|
|[CListBox:: SelectString](#selectstring)|Wyszukuje i wybiera ciąg w polu listy z pojedynczym wyborem.|
|[CListBox:: SelItemRange](#selitemrange)|Wybiera lub anuluje zakres ciągów w polu listy wielokrotnego wyboru.|
|[CListBox:: SetAnchorIndex](#setanchorindex)|Ustawia kotwicę w polu listy wielokrotnego wyboru, aby rozpocząć rozszerzane zaznaczenie.|
|[CListBox:: SetCaretIndex](#setcaretindex)|Ustawia prostokąt fokusu na element o określonym indeksie w polu listy wielokrotnego wyboru.|
|[CListBox:: SetColumnWidth](#setcolumnwidth)|Ustawia szerokość kolumny wielokolumnowego pola listy.|
|[CListBox:: SetCurSel](#setcursel)|Wybiera ciąg w polu listy.|
|[CListBox:: SetHorizontalExtent](#sethorizontalextent)|Ustawia szerokość w pikselach, którą pole listy można przewijać w poziomie.|
|[CListBox:: SetItemData](#setitemdata)|Ustawia wartość skojarzoną z elementem listy.|
|[CListBox:: SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik do elementu pola listy.|
|[CListBox:: SetItemHeight](#setitemheight)|Ustawia wysokość elementów w polu listy.|
|[CListBox:: setlocale](#setlocale)|Ustawia identyfikator ustawień regionalnych dla pola listy.|
|[CListBox:: SetSel](#setsel)|Zaznacza lub anuluje zaznaczenie elementu listy w polu listy wielokrotnego wyboru.|
|[CListBox:: SetTabStops](#settabstops)|Ustawia położenie tabulatorów w polu listy.|
|[CListBox:: SetTopIndex](#settopindex)|Ustawia indeks (liczony od zera) pierwszego widocznego ciągu w polu listy.|
|[CListBox:: VKeyToItem](#vkeytoitem)|Przesłoń, aby zapewnić obsługę niestandardowych WM_KEYDOWN dla pól listy z ustawionym stylem LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Uwagi

W polu listy zostanie wyświetlona lista elementów, takich jak nazwy plików, które użytkownik może wyświetlać i wybierać.

W polu listy z pojedynczym wyborem użytkownik może wybrać tylko jeden element. W polu listy z wielokrotnym wyborem można wybrać zakres elementów. Gdy użytkownik wybierze element, zostanie wyróżniony, a pole listy wysyła komunikat powiadomienia do okna nadrzędnego.

Pole listy można utworzyć na podstawie szablonu okna dialogowego lub bezpośrednio w kodzie. Aby utworzyć go bezpośrednio, Konstruuj `CListBox` obiektu, a następnie wywołaj funkcję [Utwórz](#create) element członkowski, aby utworzyć kontrolkę pole listy systemu Windows i dołączyć ją do obiektu `CListBox`. Aby użyć pola listy w szablonie okna dialogowego, zadeklaruj zmienną pola listy w klasie okna dialogowego, a następnie użyj `DDX_Control` w funkcji `DoDataExchange` klasy okna dialogowego, aby połączyć zmienną członkowską z kontrolką. (jest to wykonywane automatycznie po dodaniu zmiennej sterującej do klasy okna dialogowego).

Konstrukcja może być procesem jednoetapowym klasy pochodzącej od `CListBox`. Napisz konstruktora dla klasy pochodnej i Wywołaj `Create` z poziomu konstruktora.

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows wysyłane przez pole listy do jego elementu nadrzędnego (zazwyczaj klasy pochodnej z [CDialog](../../mfc/reference/cdialog-class.md)), Dodaj wpis mapy komunikatów i funkcję elementu członkowskiego obsługi komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów przyjmuje następującą formę:

`ON_Notification( id, memberFxn )`

gdzie `id` określa identyfikator okna podrzędnego kontrolki pole listy, które wysyła powiadomienie, a `memberFxn` jest nazwą nadrzędnej funkcji członkowskiej, która została zapisywana w celu obsługi powiadomienia.

Prototyp funkcji elementu nadrzędnego jest następujący:

`afx_msg void memberFxn( );`

Poniżej znajduje się lista potencjalnych wpisów mapy komunikatów oraz opis przypadków, w których zostałyby one przesłane do elementu nadrzędnego:

- ON_LBN_DBLCLK użytkownik kliknie dwukrotnie ciąg w polu listy. Tylko pole listy, które ma styl [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , wyśle ten komunikat z powiadomieniem.

- ON_LBN_ERRSPACE pole listy nie może przydzielić wystarczającej ilości pamięci do spełnienia żądania.

- ON_LBN_KILLFOCUS pole listy utraci fokus wprowadzania.

- ON_LBN_SELCANCEL bieżące zaznaczenie pola listy zostało anulowane. Ten komunikat jest wysyłany tylko wtedy, gdy pole listy ma styl LBS_NOTIFY.

- ON_LBN_SELCHANGE zaznaczenie w polu listy zostało zmienione. To powiadomienie nie jest wysyłane, jeśli zaznaczenie zostanie zmienione przez funkcję członkowską [CListBox:: SetCurSel](#setcursel) . To powiadomienie ma zastosowanie tylko do pola listy mającego styl LBS_NOTIFY. Wiadomość z powiadomieniem LBN_SELCHANGE jest wysyłana do pola listy wielokrotnego wyboru za każdym razem, gdy użytkownik naciśnie klawisz Strzałka, nawet jeśli zaznaczenie nie zostanie zmienione.

- ON_LBN_SETFOCUS pole listy otrzymuje fokus wprowadzania.

- ON_WM_CHARTOITEM pole listy rysowania przez właściciela, które nie ma ciągów odbiera komunikat WM_CHAR.

- ON_WM_VKEYTOITEM pole listy z stylem LBS_WANTKEYBOARDINPUT otrzymuje komunikat WM_KEYDOWN.

Jeśli utworzysz obiekt `CListBox` w oknie dialogowym (za pomocą zasobu okna dialogowego), obiekt `CListBox` zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli utworzysz obiekt `CListBox` w oknie, może być konieczne zniszczenie obiektu `CListBox`. Jeśli utworzysz obiekt `CListBox` na stosie, zostanie on zniszczony automatycznie. Jeśli utworzysz obiekt `CListBox` na stercie przy użyciu **nowej** funkcji, musisz wywołać metodę **delete** dla obiektu, aby zniszczyć go, gdy użytkownik zamknie okno nadrzędne.

W przypadku przydzielenia pamięci w obiekcie `CListBox` Zastąp destruktor `CListBox`, aby usunąć alokację.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="addstring"></a>CListBox:: AddString

Dodaje ciąg do pola listy.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) do ciągu w polu listy. Wartość zwracana jest LB_ERR w przypadku wystąpienia błędu; wartość zwracana jest LB_ERRSPACE, jeśli jest za mało miejsca, aby można było zapisać nowy ciąg.

### <a name="remarks"></a>Uwagi

Jeśli pole listy nie zostało utworzone za pomocą stylu [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , ciąg zostanie dodany na końcu listy. W przeciwnym razie ciąg zostanie wstawiony do listy, a lista jest posortowana. Jeśli pole listy zostało utworzone przy użyciu LBS_SORT stylu, ale nie stylu [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , struktura sortuje listę według jednego lub większej liczby wywołań do funkcji członkowskiej `CompareItem`.

Użyj [InsertString](#insertstring) , aby wstawić ciąg do określonej lokalizacji w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>CListBox:: CharToItem

Wywoływane przez platformę, gdy okno listy nadrzędnej odbierze komunikat WM_CHARTOITEM z pola listy.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Kod ANSI znaku wpisanego przez użytkownika.

*nIndex*<br/>
Bieżąca pozycja karetki z polem listy.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość-1 lub-2 w przypadku braku dalszej akcji lub nieujemnej liczby, aby określić indeks elementu pola listy, w którym ma zostać wykonana domyślna akcja dla nacionięcia klawisza. Domyślna implementacja zwraca wartość-1.

### <a name="remarks"></a>Uwagi

Wiadomość WM_CHARTOITEM jest wysyłana przez pole listy, gdy odbierze wiadomość WM_CHAR, ale tylko wtedy, gdy pole listy spełnia wszystkie te kryteria:

- Jest polem listy rysowania przez właściciela.

- Nie ma ustawionego stylu [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Zawiera co najmniej jeden element.

Nigdy nie należy wywoływać tej funkcji samodzielnie. Zastąp tę funkcję, aby zapewnić własną niestandardową obsługę komunikatów klawiatury.

W przesłonięciu należy zwrócić wartość, aby poznać strukturę działania wykonywanego przez użytkownika. Zwracana wartość-1 lub-2 wskazuje, że zostały obsłużone wszystkie aspekty wyboru elementu i nie wymaga żadnych dalszych akcji przez pole listy. Przed zwróceniem wartości-1 lub-2 można ustawić zaznaczenie lub przenieść karetkę lub oba te elementy. Aby ustawić wybór, użyj [SetCurSel](#setcursel) lub [SetSel](#setsel). Aby przenieść karetkę, użyj [SetCaretIndex](#setcaretindex).

Wartość zwracana 0 lub większa Określa indeks elementu w polu listy i wskazuje, że pole listy powinno wykonać akcję domyślną dla naciśnięcia klawisza dla danego elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox:: CListBox

Konstruuje obiekt `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Uwagi

Należy skonstruować obiekt `CListBox` w dwóch krokach. Najpierw Wywołaj konstruktora `ClistBox` a następnie Wywołaj `Create`, który inicjuje pole listy systemu Windows i dołącza go do `CListBox`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>CListBox:: CompareItem

Wywoływane przez platformę, by określić względne położenie nowego elementu w sortowanym polu listy rozwijanej właściciela.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Długi wskaźnik do struktury `COMPAREITEMSTRUCT`.

### <a name="return-value"></a>Wartość zwrócona

Wskazuje względne położenie dwóch elementów opisanych w strukturze [COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct) . Może to być dowolna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|-1|Element 1 sortuje przed elementem 2.|
|0|Element 1 i element 2 sortują te same.|
|1|Element 1 sortuje po elemencie 2.|

Aby uzyskać opis struktury `COMPAREITEMSTRUCT`, zobacz [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) .

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja członkowska nic nie robi. Jeśli utworzysz pole listy rysowania przez właściciela z stylem LBS_SORT, musisz zastąpić tę funkcję elementu członkowskiego, aby pomóc w strukturze sortowania nowych elementów dodanych do pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>CListBox:: Create

Tworzy pole listy systemu Windows i dołącza je do obiektu `CListBox`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola listy. Zastosuj dowolną kombinację [stylów pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pola.

*cinania*<br/>
Określa rozmiar i położenie pola listy. Może być obiektem `CRect` lub strukturą `RECT`.

*pParentWnd*<br/>
Określa okno nadrzędne pola listy (zazwyczaj obiekt `CDialog`). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator formantu pola listy.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Należy skonstruować obiekt `CListBox` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który inicjuje pole listy systemu Windows i dołącza go do obiektu `CListBox`.

Gdy `Create` jest wykonywane, system Windows wysyła komunikaty [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do kontrolki pole listy.

Te komunikaty są domyślnie obsługiwane przez funkcje elementu członkowskiego [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) w klasie bazowej `CWnd`. Aby zwiększyć domyślną obsługę komunikatów, należy utworzyć klasę z `CListBox`, dodać do nowej klasy mapę komunikatów i zastąpić poprzednie funkcje składowe programu obsługi komunikatów. Przesłoń `OnCreate`, na przykład, aby wykonać wymaganą inicjalizację dla nowej klasy.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pole listy.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL dodać pionowe paski przewijania

- WS_HSCROLL dodać poziomego paska przewijania

- WS_GROUP do grup formantów

- WS_TABSTOP zezwolić na tabulację w tym formancie

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>CListBox::D eleteItem

Wywoływane przez platformę, gdy użytkownik usuwa element z obiektu `CListBox` rysowania przez właściciela lub niszczy pole listy.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Długi wskaźnik do struktury [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systemu Windows, który zawiera informacje o usuniętym elemencie.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby ponownie narysować pole listy rysowania przez właściciela zgodnie z wymaganiami.

Aby uzyskać opis struktury `DELETEITEMSTRUCT`, zobacz [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>CListBox::D eleteString

Usuwa element z pozycji *nIndex* w polu listy.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) ciągu, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwrócona

Liczba ciągów pozostałych na liście. Wartość zwracana jest LB_ERR, jeśli *nIndex* Określa indeks większy niż liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wszystkie elementy po *nIndex* teraz przechodzą w dół o jedno miejsce. Na przykład, jeśli pole listy zawiera dwa elementy, usunięcie pierwszego elementu spowoduje, że pozostały element zostanie teraz w pierwszej pozycji. *nIndex*= 0 dla elementu w pierwszej pozycji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox::D IR

Dodaje listę nazw plików, dysków lub obu do pola listy.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*atrybut*<br/>
Może być dowolną kombinacją wartości **wyliczenia** opisanych w `CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)lub dowolną kombinację następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|0x0000|Plik może być odczytywany lub zapisywana.|
|0x0001|Plik może być odczytywany z, ale nie do zapisu.|
|0x0002|Plik jest ukryty i nie znajduje się na liście katalogów.|
|0x0004|Plik jest plikiem systemowym.|
|0x0010|Nazwa określona przez *lpszWildCard* określa katalog.|
|0x0020|Plik został zarchiwizowany.|
|0x4000|Uwzględnij wszystkie dyski, które pasują do nazwy określonej przez *lpszWildCard*.|
|0x8000|Flaga wyłączna. Jeśli ustawiono flagę wyłączną, wyświetlane są tylko pliki określonego typu. W przeciwnym razie pliki określonego typu są wymienione jako uzupełnienie plików "normal".|

*lpszWildCard*<br/>
Wskazuje ciąg specyfikacji pliku. Ciąg może zawierać symbole wieloznaczne (na przykład *.\*).

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) ostatniej nazwy pliku dodany do listy. Wartość zwracana jest LB_ERR w przypadku wystąpienia błędu; wartość zwracana jest LB_ERRSPACE, jeśli jest za mało miejsca, aby można było przechowywać nowe ciągi.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt pola listy rysowania przez właściciela zmienia się.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , który zawiera informacje o wymaganym typie rysunku.

### <a name="remarks"></a>Uwagi

`itemAction` i `itemState` członkowie struktury `DRAWITEMSTRUCT` definiują akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja członkowska nic nie robi. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla obiektu `CListBox` rysowania przez właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Aby uzyskać opis struktury `DRAWITEMSTRUCT`, zobacz [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>CListBox:: FindStr

Znajduje pierwszy ciąg w polu listy, który zawiera określony prefiks bez zmiany pola listy.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* to-1, całe pole listy jest przeszukiwane od początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od wielkości liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) pasującego elementu lub LB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Użyj funkcji składowej [SelectString](#selectstring) , aby znaleźć i wybrać ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>CListBox:: FindStringExact

Znajduje ciąg pierwszego pola listy, który pasuje do ciągu określonego w *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Określa indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nIndexStart*. Jeśli *nIndexStart* to-1, całe pole listy jest przeszukiwane od początku.

*lpszFind*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać wyszukany. Ten ciąg może zawierać pełną nazwę pliku, łącznie z rozszerzeniem. W wyszukiwaniu nie jest rozróżniana wielkość liter, dlatego ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwrócona

Indeks pasującego elementu lub LB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli pole listy zostało utworzone przy użyciu stylu rysowania przez właściciela, ale bez stylu [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , funkcja elementu członkowskiego `FindStringExact` próbuje dopasować wartość DoubleWord do wartości *lpszFind*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>CListBox:: GetAnchorIndex

Pobiera indeks (liczony od zera) bieżącego elementu zakotwiczenia w polu listy.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks bieżącego elementu zakotwiczonego, jeśli powodzenie; w przeciwnym razie LB_ERR.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego wyboru element zakotwiczony jest pierwszym lub ostatnim elementem w bloku ciągłych wybranych elementów.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>CListBox:: GetCaretIndex

Określa indeks elementu, który ma prostokąt fokus w polu listy wielokrotnego wyboru.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) elementu, który ma prostokąt fokus w polu listy. Jeśli pole listy jest polem listy z pojedynczym wyborem, wartość zwracana jest indeksem elementu, który jest zaznaczony (jeśli istnieje).

### <a name="remarks"></a>Uwagi

Element może lub nie może być wybrany.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>CListBox:: GetCount

Pobiera liczbę elementów w polu listy.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów w polu listy lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Zwracana liczba jest większa niż wartość indeksu ostatniego elementu (indeks jest liczony od zera).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>CListBox:: GetCurSel

Pobiera indeks (liczony od zera) aktualnie wybranego elementu, jeśli istnieje, w polu listy z pojedynczym wyborem.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) aktualnie wybranego elementu, jeśli jest to pole listy z pojedynczym wyborem. Jest LB_ERR, jeśli żaden element nie jest aktualnie wybrany.

W polu listy wielokrotnego wyboru indeks elementu, który ma fokus.

### <a name="remarks"></a>Uwagi

Nie wywołuj `GetCurSel` dla pola listy wielokrotnego wyboru. Zamiast tego użyj [CListBox:: GetSelItems](#getselitems) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox:: GetHorizontalExtent

Pobiera z pola listy szerokość w pikselach, w której można przewijać w poziomie.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Wartość zwrócona

Szerokość pola listy w pikselach.

### <a name="remarks"></a>Uwagi

Ma to zastosowanie tylko wtedy, gdy pole listy ma poziomy pasek przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>CListBox:: GetItemData

Pobiera wartość DoubleWord dostarczoną przez aplikację skojarzoną z określonym elementem listy.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwrócona

Wartość skojarzona z elementem lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Wartość DoubleWord była parametrem *dwItemData* wywołania [SetItemData](#setitemdata) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>CListBox:: GetItemDataPtr

Pobiera wartość 32-bitowej dostarczonej przez aplikację skojarzoną z określonym elementem listy jako wskaźnikiem (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwrócona

Pobiera wskaźnik lub-1, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>CListBox:: GetItemHeight

Określa wysokość elementów w polu listy.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie powinna być ustawiona na 0.

### <a name="return-value"></a>Wartość zwrócona

Wysokość w pikselach elementów w polu listy. Jeśli pole listy ma styl [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , wartość zwracana to wysokość elementu określonego przez *nIndex*. Jeśli wystąpi błąd, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>CListBox:: GetItemRect

Pobiera wymiary prostokąta, który jest powiązany z elementem pola listy, tak jak jest aktualnie wyświetlany w oknie listy.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu.

*lpRect*<br/>
Określa długi wskaźnik do [struktury Rect](/windows/win32/api/windef/ns-windef-rect) , który odbiera współrzędne klienta pola listy.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>CListBox:: GetListBoxInfo

Pobiera liczbę elementów na kolumnę.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba elementów na kolumnę obiektu `CListBox`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) , zgodnie z opisem w Windows SDK.

##  <a name="getlocale"></a>CListBox:: getLocale

Pobiera ustawienia regionalne używane przez pole listy.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość identyfikatora ustawień regionalnych (LCID) dla ciągów w polu listy.

### <a name="remarks"></a>Uwagi

Ustawienia regionalne są używane na przykład w celu określenia kolejności sortowania ciągów w posortowanym polu listy.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: Setlocals](#setlocale).

##  <a name="getsel"></a>CListBox:: GetSel

Pobiera stan zaznaczenia elementu.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu.

### <a name="return-value"></a>Wartość zwrócona

Liczba dodatnia, jeśli wybrano określony element; w przeciwnym razie jest równa 0. Wartość zwracana jest LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska działa zarówno w przypadku pól listy pojedynczej, jak i wielokrotnego wyboru.

Aby pobrać indeks aktualnie wybranego elementu pola listy, użyj [CListBox:: GetCurSel](#getcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>CListBox:: GetSelCount

Pobiera łączną liczbę wybranych elementów w polu listy wielokrotnego wyboru.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Wartość zwrócona

Liczba wybranych elementów w polu listy. Jeśli pole listy jest polem listy z pojedynczym wyborem, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: GetSelItems](#getselitems).

##  <a name="getselitems"></a>CListBox:: GetSelItems

Wypełnia bufor z tablicą liczb całkowitych, które określają numery elementów wybranych elementów w polu listy wielokrotnego wyboru.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nMaxItems*<br/>
Określa maksymalną liczbę wybranych elementów, których numery elementów mają być umieszczane w buforze.

*rgIndex*<br/>
Określa wskaźnik do buforu wystarczająco duży dla liczby liczb całkowitych określonych przez *nMaxItems*.

### <a name="return-value"></a>Wartość zwrócona

Rzeczywista liczba elementów umieszczonych w buforze. Jeśli pole listy jest polem listy z pojedynczym wyborem, wartość zwracana jest `LB_ERR`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>CListBox:: gettext

Pobiera ciąg z pola listy.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) ciągu, który ma zostać pobrany.

*lpszBuffer*<br/>
Wskazuje bufor, który odbiera ciąg. Bufor musi mieć wystarczającą ilość miejsca dla ciągu i kończącego znaku null. Rozmiar ciągu można ustalić przed czasem, wywołując funkcję elementu członkowskiego `GetTextLen`.

*rString*<br/>
Odwołanie do obiektu `CString`.

### <a name="return-value"></a>Wartość zwrócona

Długość (w bajtach) ciągu, z wyłączeniem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest LB_ERR.

### <a name="remarks"></a>Uwagi

Druga forma tej funkcji składowej wypełnia obiekt `CString` ciągiem tekstu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>CListBox:: GetTextLen

Pobiera długość ciągu w pozycji listy.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks ciągu liczony od zera.

### <a name="return-value"></a>Wartość zwrócona

Długość ciągu znaków, z wyłączeniem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: gettext](#gettext).

##  <a name="gettopindex"></a>CListBox:: GetTopIndex

Pobiera indeks (liczony od zera) pierwszego widocznego elementu w polu listy.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) pierwszego widocznego elementu w polu listy, jeśli się powiedzie, LB_ERR w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Początkowo element 0 znajduje się u góry pola listy, ale jeśli pole listy jest przewijane, inny element może znajdować się u góry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>CListBox:: InitStorage

Przydziela pamięć do przechowywania elementów pola listy.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*nItems*<br/>
Określa liczbę elementów do dodania.

*nBytes*<br/>
Określa ilość pamięci (w bajtach) do przydzielenia dla ciągów elementów.

### <a name="return-value"></a>Wartość zwrócona

Jeśli to się powiedzie, Maksymalna liczba elementów, które mogą być przechowywane w polu listy przed ponownym alokacją pamięci, jest niezbędna, w przeciwnym razie LB_ERRSPACE, co oznacza, że jest za mało dostępnej pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję przed dodaniem dużej liczby elementów do `CListBox`.

Ta funkcja pomaga przyspieszyć inicjalizację pól listy, które mają dużą liczbę elementów (więcej niż 100). Wstępnie przydzieli określoną ilość pamięci, aby kolejne funkcje [AddString](#addstring), [InsertString](#insertstring)i [dir](#dir) miały najkrótszy możliwy czas. Można użyć oszacowań dla parametrów. W przypadku nadmiernego oszacowania część dodatkowej pamięci zostanie przypisana; w przypadku podwyższania szacunku normalna alokacja jest używana dla elementów, które przekraczają wstępnie przydzieloną kwotę.

Tylko system Windows 95/98: parametr *nItems* jest ograniczony do wartości 16-bitowych. Oznacza to, że pola listy nie mogą zawierać więcej niż 32 767 elementów. Chociaż liczba elementów jest ograniczona, łączny rozmiar elementów w polu listy jest ograniczony tylko przez dostępną pamięć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>CListBox:: InsertString

Wstawia ciąg w polu listy.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks pozycji (liczony od zera), w której ma zostać wstawiony ciąg. Jeśli ten parametr ma wartość-1, ciąg zostanie dodany na końcu listy.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwrócona

Indeks (liczony od zera) pozycji, w której został wstawiony ciąg. Wartość zwracana jest LB_ERR w przypadku wystąpienia błędu; wartość zwracana jest LB_ERRSPACE, jeśli jest za mało miejsca, aby można było zapisać nowy ciąg.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do funkcji składowej [AddString](#addstring) `InsertString` nie powoduje sortowania listy z stylem [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>CListBox:: ItemFromPoint

Określa element pola listy najbliższy punkt określony w *pkt pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
Punkt, dla którego można znaleźć najbliższy element określony względem lewego górnego rogu obszaru klienta w polu listy.

*bOutside*<br/>
Odwołanie do zmiennej LOGICZNEj, która zostanie ustawiona na wartość TRUE, jeśli *pt* znajduje się poza obszarem klienckim pola listy, wartość false, jeśli *pt* znajduje się w obszarze klienta pola listy.

### <a name="return-value"></a>Wartość zwrócona

Indeks najbliższego elementu do punktu określonego w *pkt pt*.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można określić, który element pola listy jest przesuwany nad kursorem myszy.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CListBox:: SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>CListBox:: MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony pole listy z stylem rysowania przez właściciela.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długi wskaźnik do struktury [MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja członkowska nic nie robi. Zastąp tę funkcję członkowską i wypełnij strukturę `MEASUREITEMSTRUCT`, aby informować okna o wymiarach pól listy. Jeśli pole listy jest tworzone z stylem [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski jest wywoływany tylko raz.

Aby uzyskać więcej informacji na temat używania stylu [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) w polu listy rysowania przez właściciela utworzonego za pomocą `SubclassDlgItem` funkcji składowej `CWnd`, zapoznaj się z tematem dyskusja w artykule [technicznym 14](../../mfc/tn014-custom-controls.md).

Aby uzyskać opis struktury `MEASUREITEMSTRUCT`, zobacz [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>CListBox:: ResetContent

Usuwa wszystkie elementy z pola listy.

```
void ResetContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>CListBox:: SelectString

Wyszukuje element pola listy, który pasuje do określonego ciągu, i jeśli zostanie znaleziony pasujący element, zaznacza element.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* to-1, całe pole listy jest przeszukiwane od początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od wielkości liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwrócona

Indeks wybranego elementu, jeśli wyszukiwanie zakończyło się pomyślnie. Jeśli wyszukiwanie nie powiodło się, wartość zwracana jest LB_ERR i bieżące zaznaczenie nie zostanie zmienione.

### <a name="remarks"></a>Uwagi

Pole listy jest przewijane, w razie potrzeby, aby przenieść wybrany element do widoku.

Ta funkcja członkowska nie może być używana z polem listy, które ma styl [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

Element jest wybierany tylko wtedy, gdy jego początkowe znaki (od punktu początkowego) pasują do znaków w ciągu określonym przez *lpszItem*.

Użyj funkcji składowej `FindString`, aby znaleźć ciąg bez wybierania elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>CListBox:: SelItemRange

Wybiera wiele kolejnych elementów w polu listy wielokrotnego wyboru.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bSelect*<br/>
Określa, jak ustawić wybór. Jeśli *bSelect* ma wartość true, ciąg jest zaznaczony i wyróżniony; w przypadku wartości FALSE wyróżnienie jest usuwane, a ciąg nie jest już zaznaczony.

*nFirstItem*<br/>
Określa indeks (liczony od zera) pierwszego elementu, który ma zostać ustawiony.

*nLastItem*<br/>
Określa indeks (liczony od zera) ostatniego elementu, który ma zostać ustawiony.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana tylko z polami list wielokrotnego wyboru. Jeśli musisz wybrać tylko jeden element w polu listy wielokrotnego wyboru — to znaczy, jeśli *nFirstItem* jest równa *nLastItem* — zamiast tego wywołaj funkcję członkowską [SetSel](#setsel) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>CListBox:: SetAnchorIndex

Ustawia kotwicę w polu listy wielokrotnego wyboru, aby rozpocząć rozszerzane zaznaczenie.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu pola listy, który będzie zakotwiczeniem.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego wyboru element zakotwiczony jest pierwszym lub ostatnim elementem w bloku ciągłych wybranych elementów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>CListBox:: SetCaretIndex

Ustawia prostokąt fokusu na element o określonym indeksie w polu listy wielokrotnego wyboru.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu, w którym ma zostać wyświetlony prostokąt fokus w polu listy.

*bScroll*<br/>
Jeśli ta wartość jest równa 0, element zostanie przewinięty do momentu, w którym jest w pełni widoczny. Jeśli ta wartość nie jest równa 0, element zostanie przewinięty do momentu, gdy jest on co najmniej częściowo widoczny.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Jeśli element nie jest widoczny, jest przewijany do widoku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>CListBox:: SetColumnWidth

Ustawia szerokość (w pikselach) wszystkich kolumn w wielokolumnowym polu listy (utworzonego za pomocą stylu [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth*<br/>
Określa szerokość (w pikselach) wszystkich kolumn.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>CListBox:: SetCurSel

Wybiera ciąg i przewija go do widoku, w razie potrzeby.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nWybierz*<br/>
Określa indeks (liczony od zera) ciągu, który ma zostać wybrany. Jeśli *nWybierz* ma wartość-1, pole listy nie ma żadnego wyboru.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Po wybraniu nowego ciągu pole listy usuwa wyróżnienie z wcześniej wybranego ciągu.

Ta funkcja członkowska jest używana tylko z polami listy z pojedynczym wyborem.

Aby ustawić lub usunąć zaznaczenie w polu listy wielokrotnego wyboru, użyj [CListBox:: SetSel](#setsel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox:: SetHorizontalExtent

Ustawia szerokość (w pikselach), przez którą pole listy może być przewijane w poziomie.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxExtent*<br/>
Określa liczbę pikseli, przez jaką pole listy może być przewijane w poziomie.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar pola listy jest mniejszy niż ta wartość, poziomy pasek przewijania będzie przewinąć w poziomie elementy w polu listy. Jeśli pole listy jest tak duże lub większe niż ta wartość, poziomy pasek przewijania jest ukryty.

Aby odpowiedzieć na wywołanie `SetHorizontalExtent`, pole listy musi być zdefiniowane za pomocą stylu [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) .

Ta funkcja członkowska nie jest przydatna w przypadku wielokolumnowych pól listy. Dla wielokolumnowych pól listy wywołaj funkcję członkowską `SetColumnWidth`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>CListBox:: SetItemData

Ustawia wartość skojarzoną z określonym elementem w polu listy.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu.

*dwItemData*<br/>
Określa wartość, która ma zostać skojarzona z elementem.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>CListBox:: SetItemDataPtr

Ustawia wartość 32-bitową skojarzoną z określonym elementem w polu listy jako określony wskaźnik ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu.

*pData*<br/>
Określa wskaźnik, który ma zostać skojarzony z elementem.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Ten wskaźnik pozostaje prawidłowy dla życia pola listy, nawet jeśli względne położenie elementu w polu listy może ulec zmianie, gdy elementy są dodawane lub usuwane. W związku z tym indeks elementu w polu może ulec zmianie, ale wskaźnik pozostaje niezawodny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>CListBox:: SetItemHeight

Ustawia wysokość elementów w polu listy.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie powinna być ustawiona na 0.

*cyItemHeight*<br/>
Określa wysokość (w pikselach) elementu.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR, jeśli indeks lub wysokość są nieprawidłowe.

### <a name="remarks"></a>Uwagi

Jeśli pole listy ma styl [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , ta funkcja Ustawia wysokość elementu określonego przez *nIndex*. W przeciwnym razie ta funkcja Ustawia wysokość wszystkich elementów w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>CListBox:: setlocale

Ustawia identyfikator ustawień regionalnych dla tego pola listy.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nowa wartość identyfikatora ustawień regionalnych (LCID) do ustawienia w polu listy.

### <a name="return-value"></a>Wartość zwrócona

Wartość poprzedniego identyfikatora ustawień regionalnych (LCID) dla tego pola listy.

### <a name="remarks"></a>Uwagi

Jeśli `SetLocale` nie zostanie wywołana, domyślne ustawienia regionalne są uzyskiwane z systemu. Domyślne ustawienia regionalne systemu można modyfikować za pomocą aplikacji regionalnej (lub międzynarodowej) panelu sterowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox:: SetSel

Wybiera ciąg w polu listy wielokrotnego wyboru.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) ciągu, który ma zostać ustawiony. Jeśli-1, zaznaczenie jest dodawane lub usuwane ze wszystkich ciągów, w zależności od wartości *bSelect*.

*bSelect*<br/>
Określa, jak ustawić wybór. Jeśli *bSelect* ma wartość true, ciąg jest zaznaczony i wyróżniony; w przypadku wartości FALSE wyróżnienie jest usuwane, a ciąg nie jest już zaznaczony. Określony ciąg jest domyślnie zaznaczony i wyróżniony.

### <a name="return-value"></a>Wartość zwrócona

LB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest używana tylko z polami list wielokrotnego wyboru.

Aby zaznaczyć element z pola listy z pojedynczym wyborem, użyj [CListBox:: SetCurSel](#setcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox:: SetTabStops

Ustawia położenie tabulatorów w polu listy.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Tabulatory są ustawiane dla każdej jednostki okna dialogowego *cxEachStop* . Zobacz *rgTabStops* , aby uzyskać opis jednostki okna dialogowego.

*nTabStops*<br/>
Określa liczbę zatrzymanych tabulatorów w polu listy.

*rgTabStops*<br/>
Wskazuje pierwszy element członkowski tablicy liczb całkowitych zawierających pozycje tabulatora w jednostkach okna dialogowego. Jednostka okna dialogowego to odległość pozioma lub pionowa. Jedna pozioma jednostka okna dialogowego jest równa jednej czwartej bieżącej jednostki szerokości okna dialogowego, a jedna pionowa jednostka okna dialogowego jest równa jednej ósmej aktualnej jednostki wysokości okna dialogowego. Jednostki bazowe okna dialogowego są obliczane na podstawie wysokości i szerokości bieżącej czcionki systemowej. Funkcja `GetDialogBaseUnits` systemu Windows zwraca bieżące jednostki bazowe okna dialogowego w pikselach. Tabulatory muszą być sortowane w kolejności rosnącej; karty wstecz są niedozwolone.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli wszystkie karty zostały ustawione; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby ustawić, że tabulatory mają być domyślnym rozmiarem 2 jednostek okna dialogowego, wywołaj bezparametrową wersję tej funkcji elementu członkowskiego. Aby ustawić przetrzymywanie tabulatorów o rozmiarze innym niż 2, wywołaj wersję przy użyciu argumentu *cxEachStop* .

Aby ustawić przetrzymywanie tabulatorów na tablicę rozmiarów, użyj wersji z argumentami *rgTabStops* i *nTabStops* . Tabulator zostanie ustawiony dla każdej wartości w *rgTabStops*, do numeru określonego przez *nTabStops*.

Aby odpowiedzieć na wywołanie funkcji elementu członkowskiego `SetTabStops`, pole listy musi być utworzone z stylem [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>CListBox:: SetTopIndex

Zapewnia widoczność określonego elementu pola listy.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu listy.

### <a name="return-value"></a>Wartość zwrócona

Zero jeśli kończy się pomyślnie lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

System przewija pole listy, dopóki element określony przez *nIndex* pojawia się u góry pola listy lub Osiągnięto maksymalny zakres przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>CListBox:: VKeyToItem

Wywoływane przez platformę, gdy okno listy nadrzędnej odbierze komunikat WM_VKEYTOITEM z pola listy.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Kod klucza wirtualnego klucza naciśniętego przez użytkownika. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser. h

*nIndex*<br/>
Bieżąca pozycja karetki z polem listy.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość-2 w przypadku braku dalszych akcji,-1 dla akcji domyślnej lub nieujemnej liczby, aby określić indeks elementu pola listy, w którym ma zostać wykonana domyślna akcja dla naciśnięcia klawisza.

### <a name="remarks"></a>Uwagi

Wiadomość WM_VKEYTOITEM jest wysyłana przez pole listy, gdy odbierze komunikat WM_KEYDOWN, ale tylko wtedy, gdy pole listy spełnia obie poniższe warunki:

- Ma ustawiony styl [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Zawiera co najmniej jeden element.

Nigdy nie należy wywoływać tej funkcji samodzielnie. Zastąp tę funkcję, aby zapewnić własną niestandardową obsługę komunikatów klawiatury.

Musisz zwrócić wartość, aby określić, jakie działanie przesłonięcia zostało wykonane. Zwracana wartość-2 wskazuje, że aplikacja obsłuży wszystkie aspekty wyboru elementu i nie wymaga żadnych dalszych akcji przez pole listy. Przed zwróceniem wartości-2 można ustawić zaznaczenie lub przenieść karetkę lub oba te elementy. Aby ustawić wybór, użyj [SetCurSel](#setcursel) lub [SetSel](#setsel). Aby przenieść karetkę, użyj [SetCaretIndex](#setcaretindex).

Zwracana wartość-1 oznacza, że pole listy powinno wykonać akcję domyślną w odpowiedzi na naciśnięcie klawisza. Domyślna implementacja zwraca wartość-1.

Wartość zwracana 0 lub większa Określa indeks elementu w polu listy i wskazuje, że pole listy powinno wykonać akcję domyślną dla naciśnięcia klawisza dla danego elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykład CTRLTEST MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)
