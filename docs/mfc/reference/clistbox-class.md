---
title: Klasa CListBox
description: Opis klasy MFC CListBox i jej funkcji członkowskich.
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
ms.openlocfilehash: 171038ebaaed815aa687c200fe3210bde8000be3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753590"
---
# <a name="clistbox-class"></a>Klasa CListBox

Udostępnia funkcje pola listy systemu Windows.

## <a name="syntax"></a>Składnia

```
class CListBox : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Konstruuje `CListBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Dodaje ciąg do pola listy.|
|[CListBox::CharToItem](#chartoitem)|Zastąrpnąć, aby zapewnić niestandardową obsługę WM_CHAR dla pól listy rysowania właściciela, które nie mają ciągów.|
|[CListBox::CompareItem](#compareitem)|Wywoływane przez strukturę, aby określić położenie nowego elementu w posortowanym polu listy rysowania właściciela.|
|[CListBox::Tworzenie](#create)|Tworzy pole listy systemu Windows i `CListBox` dołącza je do obiektu.|
|[CListBox::DeleteItem](#deleteitem)|Wywoływane przez strukturę, gdy użytkownik usuwa element z pola listy rysowania właściciela.|
|[CListBox::DeleteString](#deletestring)|Usuwa ciąg z pola listy.|
|[CListBox::Dir](#dir)|Dodaje nazwy plików, dyski lub oba z bieżącego katalogu do pola listy.|
|[CListBox::DrawItem](#drawitem)|Wywoływane przez strukturę, gdy zmienia się wizualny aspekt pola listy rysowania właściciela.|
|[CListBox::ZnajdźStrączenie](#findstring)|Wyszukuje ciąg w polu listy.|
|[CListBox::FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pola listy, który pasuje do określonego ciągu.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Pobiera indeks od zera bieżącego elementu kotwicy w polu listy.|
|[CListBox::GetCaretIndex](#getcaretindex)|Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego zaznaczenia.|
|[CListBox::GetCount](#getcount)|Zwraca liczbę ciągów w polu listy.|
|[CListBox::GetCurSel](#getcursel)|Zwraca indeks od zera aktualnie wybranego ciągu w polu listy.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, w których pole listy można przewijać w poziomie.|
|[CListBox::GetItemData](#getitemdata)|Zwraca wartość skojarzoną z elementem pola listy.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Zwraca wskaźnik do elementu pola listy.|
|[CListBox::GetItemHeight](#getitemheight)|Określa wysokość elementów w polu listy.|
|[CListBox::GetItemRect](#getitemrect)|Zwraca prostokąt obwiedniowy elementu pola listy, który jest aktualnie wyświetlany.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Pobiera liczbę elementów na kolumnę.|
|[CListBox::GetLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola listy.|
|[CListBox::GetSel](#getsel)|Zwraca stan wyboru elementu pola listy.|
|[CListBox::GetSelCount](#getselcount)|Zwraca liczbę ciągów aktualnie zaznaczonych w polu listy wielokrotnego wyboru.|
|[CListBox::GetSelItems](#getselitems)|Zwraca indeksy ciągów aktualnie zaznaczonych w polu listy.|
|[CListBox::GetText](#gettext)|Kopiuje element pola listy do buforu.|
|[CListBox::GetTextLen](#gettextlen)|Zwraca długość w bajtach elementu pola listy.|
|[CListBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego widocznego ciągu w polu listy.|
|[CListBox::InitStorage](#initstorage)|Wstępnie przydziela bloki pamięci dla elementów pola listy i ciągów.|
|[CListBox::Wstawianie](#insertstring)|Wstawia ciąg w określonej lokalizacji w polu listy.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Zwraca indeks elementu pola listy znajdującego się najbliżej punktu.|
|[CListBox::MeasureItem](#measureitem)|Wywoływane przez strukturę, gdy jest tworzony pole listy rysowania właściciela w celu określenia wymiarów pola listy.|
|[CListBox::ResetContent](#resetcontent)|Czyści wszystkie wpisy z pola listy.|
|[CListBox::SelectString](#selectstring)|Wyszukuje i wybiera ciąg w polu listy pojedynczego zaznaczenia.|
|[CListBox::SelItemRange](#selitemrange)|Zaznacza lub odznacza zakres ciągów w polu listy wielokrotnego zaznaczenia.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Ustawia zakotwiczenie w polu listy wielokrotnego wyboru, aby rozpocząć wybór rozszerzony.|
|[CListBox::SetCaretIndex](#setcaretindex)|Ustawia prostokąt fokusu na element w określonym indeksie w polu listy wielokrotnego wyboru.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Ustawia szerokość kolumny pola listy wielokolumnowej.|
|[CListBox::SetCurSel](#setcursel)|Wybiera ciąg pola listy.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Ustawia szerokość w pikselach, że pole listy można przewijać w poziomie.|
|[CListBox::SetItemData](#setitemdata)|Ustawia wartość skojarzoną z elementem pola listy.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik do elementu pola listy.|
|[CListBox::SetItemHeight](#setitemheight)|Ustawia wysokość elementów w polu listy.|
|[CListBox::SetLocale](#setlocale)|Ustawia identyfikator ustawień regionalnych dla pola listy.|
|[CListBox::SetSel](#setsel)|Zaznacza lub odznacza element pola listy w polu listy z wieloma zaznaczeniami.|
|[CListBox::SetTabStops](#settabstops)|Ustawia pozycje tabulatora w polu listy.|
|[CListBox::SetTopIndex](#settopindex)|Ustawia indeks od zera pierwszego widocznego ciągu w polu listy.|
|[CListBox::VKeyToItem](#vkeytoitem)|Zastąp, aby zapewnić niestandardową obsługę WM_KEYDOWN dla pól list z zestawem stylu LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Uwagi

W polu listy jest wyświetlana lista elementów, takich jak nazwy plików, które użytkownik może wyświetlać i wybierać.

W polu listy z pojedynczym wyborem użytkownik może wybrać tylko jeden element. W polu listy wielokrotnego wyboru można wybrać zakres elementów. Gdy użytkownik wybierze element, jest wyróżniony, a pole listy wysyła komunikat z powiadomieniem do okna nadrzędnego.

Pole listy można utworzyć z szablonu okna dialogowego lub bezpośrednio w kodzie. Aby utworzyć go bezpośrednio, `CListBox` skonstruuj obiekt, a następnie [wywołaj](#create) funkcję Utwórz `CListBox` element członkowski, aby utworzyć kontrolkę pola listy systemu Windows i dołączyć go do obiektu. Aby użyć pola listy w szablonie okna dialogowego, zadeklaruj `DDX_Control` zmienną pola listy `DoDataExchange` w klasie okna dialogowego, a następnie użyj funkcji klasy okna dialogowego, aby połączyć zmienną elementu członkowskiego z formantem. (Odbywa się to automatycznie po dodaniu zmiennej sterującej do klasy okna dialogowego).

Budowa może być procesem jednoetapowym w `CListBox`klasie wywodzącej się z . Napisz konstruktora dla klasy `Create` pochodnej i wywołać z wewnątrz konstruktora.

Jeśli chcesz obsługiwać wiadomości powiadomień systemu Windows wysyłane przez pole listy do jego nadrzędnego (zwykle klasy pochodzące z [CDialog](../../mfc/reference/cdialog-class.md)), dodaj wpis mapy wiadomości i funkcję elementu członkowskiego obsługi wiadomości do klasy nadrzędnej dla każdej wiadomości.

Każdy wpis mapy wiadomości ma następującą formę:

`ON_Notification( id, memberFxn )`

gdzie `id` określa identyfikator okna podrzędnego formantu pola listy `memberFxn` wysyłającego powiadomienie i jest nazwą funkcji elementu członkowskiego nadrzędnego, która została napisana w celu obsługi powiadomienia.

Prototyp funkcji rodzica jest następujący:

`afx_msg void memberFxn( );`

Poniżej znajduje się lista potencjalnych wpisów mapy wiadomości i opis przypadków, w których będą one wysyłane do rodzica:

- ON_LBN_DBLCLK Użytkownik kliknie dwukrotnie ciąg w polu listy. Ten komunikat powiadomienia wysyła tylko pole listy z [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylem.

- ON_LBN_ERRSPACE Pole listy nie może przydzielić wystarczającej ilości pamięci, aby spełnić żądanie.

- ON_LBN_KILLFOCUS Pole listy traci fokus wejściowy.

- ON_LBN_SELCANCEL Bieżący wybór pola listy zostanie anulowany. Ta wiadomość jest wysyłana tylko wtedy, gdy pole listy ma styl LBS_NOTIFY.

- ON_LBN_SELCHANGE Wybór w polu listy został zmieniony. To powiadomienie nie jest wysyłane, jeśli wybór zostanie zmieniony przez funkcję elementu członkowskiego [CListBox::SetCurSel.](#setcursel) To powiadomienie dotyczy tylko pola listy, które ma styl LBS_NOTIFY. Komunikat powiadomienia LBN_SELCHANGE jest wysyłany dla pola listy wielokrotnego wyboru za każdym razem, gdy użytkownik naciśnie klawisz strzałki, nawet jeśli zaznaczenie nie ulegnie zmianie.

- ON_LBN_SETFOCUS Pole listy odbiera fokus wejściowy.

- ON_WM_CHARTOITEM Pole listy rysowania właściciela, które nie ma żadnych ciągów, odbiera komunikat WM_CHAR.

- ON_WM_VKEYTOITEM Pole listy ze stylem LBS_WANTKEYBOARDINPUT odbiera wiadomość WM_KEYDOWN.

Jeśli obiekt `CListBox` zostanie utworzony w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CListBox` obiekt zostanie automatycznie zniszczony po zamknięciu okna dialogowego przez użytkownika.

Jeśli tworzysz `CListBox` obiekt w oknie, może być `CListBox` konieczne zniszczenie obiektu. Jeśli utworzysz `CListBox` obiekt na stosie, zostanie on automatycznie zniszczony. Jeśli `CListBox` obiekt zostanie utworzony na stercie przy użyciu **nowej** funkcji, należy **wywołać delete** na obiekcie, aby go zniszczyć, gdy użytkownik zamknie okno nadrzędne.

Jeśli przydzielić dowolną `CListBox` pamięć w obiekcie, zastąpić `CListBox` destruktora do usuwania alokacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString

Dodaje ciąg do pola listy.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
Wskazuje ciąg zakończony z wartością null, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera do ciągu w polu listy. Zwracana wartość jest LB_ERR, jeśli wystąpi błąd; zwracana wartość jest LB_ERRSPACE, jeśli nie ma wystarczającego miejsca do przechowywania nowego ciągu.

### <a name="remarks"></a>Uwagi

Jeśli pole listy nie zostało utworzone w stylu [LBS_SORT,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ciąg zostanie dodany na końcu listy. W przeciwnym razie ciąg zostanie wstawiony do listy, a lista jest sortowana. Jeśli pole listy zostało utworzone przy LBS_SORT stylu, ale nie w stylu [LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) struktura sortuje listę `CompareItem` według jednego lub więcej wywołań funkcji elementu członkowskiego.

Użyj [insertstring,](#insertstring) aby wstawić ciąg do określonej lokalizacji w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem

Wywoływane przez strukturę, gdy okno nadrzędne pola listy odbiera komunikat WM_CHARTOITEM z pola listy.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*klawisze*<br/>
Kod ANSI znaku wpisanego przez użytkownika.

*Nindex*<br/>
Bieżąca pozycja list-box caret.

### <a name="return-value"></a>Wartość zwracana

Zwraca — 1 lub - 2 dla braku dalszych działań lub nieujemny numer, aby określić indeks elementu pola listy, na którym ma być wykonać domyślną akcję dla naciśnięcia klawisza. Domyślna implementacja zwraca - 1.

### <a name="remarks"></a>Uwagi

Wiadomość WM_CHARTOITEM jest wysyłana przez pole listy po odebraniu wiadomości WM_CHAR, ale tylko wtedy, gdy pole listy spełnia wszystkie te kryteria:

- Jest polem listy rysowania przez właściciela.

- Nie ma zestawu stylu [LBS_HASSTRINGS.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

- Posiada co najmniej jeden element.

Nigdy nie należy nazywać tej funkcji samodzielnie. Zastąd w tej funkcji należy zapewnić własną niestandardową obsługę komunikatów klawiatury.

W zastąpienia należy zwrócić wartość, aby poinformować strukturę, jakie działania zostały wykonane. Zwracana wartość - 1 lub - 2 wskazuje, że obsługiwane wszystkie aspekty wyboru elementu i nie wymaga dalszych działań przez pole listy. Przed zwróceniem - 1 lub - 2, można ustawić zaznaczenie lub przenieść daszek lub obu. Aby ustawić zaznaczenie, użyj [setcursel](#setcursel) lub [SetSel](#setsel). Aby przenieść cieszę, użyj [funkcji SetCaretIndex](#setcaretindex).

Zwracana wartość 0 lub większa określa indeks elementu w polu listy i wskazuje, że pole listy powinno wykonać domyślną akcję dla naciśnięcia klawisza w danym elemencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox

Konstruuje `CListBox` obiekt.

```
CListBox();
```

### <a name="remarks"></a>Uwagi

Konstruowanie `CListBox` obiektu w dwóch krokach. Najpierw zadzwoń do `ClistBox` konstruktora, a następnie zadzwoń , `Create`który inicjuje pole listy systemu Windows i dołącza go do pliku `CListBox`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem

Wywoływane przez ramy, aby określić względną pozycję nowego elementu w posortowanym polu listy rysowania właściciela.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Długi wskaźnik do `COMPAREITEMSTRUCT` struktury.

### <a name="return-value"></a>Wartość zwracana

Wskazuje względne położenie dwóch elementów opisanych w strukturze [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct) Może to być dowolna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|-1|Pozycja 1 sortuje przed punktem 2.|
|0|Pozycja 1 i pozycja 2 sortować tak samo.|
|1|Pozycja 1 sortuje po pozycji 2.|

Zobacz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) opis `COMPAREITEMSTRUCT` struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Jeśli utworzysz pole listy rysowania właściciela ze stylem LBS_SORT, należy zastąpić tę funkcję elementu członkowskiego, aby pomóc platformie w sortowaniu nowych elementów dodanych do pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox::Tworzenie

Tworzy pole listy systemu Windows i `CListBox` dołącza je do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl pola listy. Zastosuj dowolną [kombinację stylów pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pola.

*Rect*<br/>
Określa rozmiar i położenie pola listy. Może to być `CRect` obiekt `RECT` lub struktura.

*pParentWnd*<br/>
Określa okno nadrzędne pola listy (zwykle `CDialog` obiekt). Nie może być null.

*Nid*<br/>
Określa identyfikator formantu pola listy.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CListBox` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `Create`, który inicjuje pole listy systemu Windows i dołącza go do `CListBox` obiektu.

Podczas `Create` wykonywania system Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) wiadomości do formantu pola listy.

Te komunikaty są obsługiwane domyślnie przez Funkcje członkowskie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) w klasie podstawowej. `CWnd` Aby rozszerzyć domyślną obsługę wiadomości, `CListBox`należy wyprowadzić klasę z , dodać mapę wiadomości do nowej klasy i zastąpić poprzednie funkcje członkowskie programu obsługi wiadomości. Zastąd w celu wykonania wymaganej inicjalizacji `OnCreate`dla nowej klasy.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do formantu pola listy.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL Aby dodać pionowy pasek przewijania

- WS_HSCROLL Aby dodać poziomy pasek przewijania

- WS_GROUP Do grupowanie formantów

- WS_TABSTOP Aby umożliwić tabulator do tej kontroli

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem

Wywoływane przez strukturę, gdy użytkownik usuwa element `CListBox` z obiektu rysowania właściciela lub niszczy pole listy.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Długi wskaźnik do struktury WINDOWS [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) zawierający informacje o usuniętym elemencie.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. W razie potrzeby należy ponownie narysować tę funkcję, aby ponownie narysować pole listy rysowania przez właściciela.

Zobacz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) opis `DELETEITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

Usuwa element w pozycji *nIndex* z pola listy.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera ciągu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Liczba ciągów pozostałych na liście. Zwracana wartość jest LB_ERR, jeśli *nIndex* określa indeks większy niż liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wszystkie elementy następujące po *nIndex* teraz przenieść w dół o jedną pozycję. Na przykład jeśli pole listy zawiera dwa elementy, usunięcie pierwszego elementu spowoduje, że pozostały element będzie teraz na pierwszej pozycji. *nIndex*=0 dla towaru na pierwszej pozycji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::Dir

Dodaje listę nazwy plików, dysków lub obu tych plików do pola listy.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*Attr*<br/>
Może to być dowolna kombinacja wartości **wyliczenia** `CFile::GetStatu` [opisana](../../mfc/reference/cfile-class.md#getstatus)w s lub dowolna kombinacja następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|0x0000|Plik można odczytać lub zapisać.|
|0x0001|Plik może być odczytywany z, ale nie zapisywane.|
|0x0002|Plik jest ukryty i nie pojawia się na liście katalogów.|
|0x0004|Plik jest plikiem systemowym.|
|0x0010|Nazwa określona przez *lpszWildCard* określa katalog.|
|0x0020|Plik został zarchiwizowany.|
|0x4000|Uwzględnij wszystkie dyski, które pasują do nazwy określonej przez *lpszWildCard*.|
|0x8000|Ekskluzywna flaga. Jeśli flaga wyłączności jest ustawiona, wyświetlane są tylko pliki określonego typu. W przeciwnym razie pliki określonego typu są wyświetlane oprócz plików "normalnych".|

*lpszWildCard*<br/>
Wskazuje ciąg specyfikacji pliku. Ciąg może zawierać symbole wieloznaczne\*(na przykład *. ).

### <a name="return-value"></a>Wartość zwracana

Indeks od zera ostatniej nazwy pliku dodany do listy. Zwracana wartość jest LB_ERR, jeśli wystąpi błąd; zwracana wartość jest LB_ERRSPACE, jeśli nie ma wystarczającego miejsca do przechowywania nowych ciągów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem

Wywoływane przez strukturę, gdy zmienia się wizualny aspekt pola listy rysowania właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) który zawiera informacje o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Elementy `itemAction` `itemState` członkowskie `DRAWITEMSTRUCT` konstrukcji definiują akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpokaj tę funkcję elementu członkowskiego, aby zaimplementować rysunek dla obiektu rysowania `CListBox` właściciela. Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::ZnajdźStrączenie

Znajduje pierwszy ciąg w polu listy, który zawiera określony prefiks bez zmiany zaznaczenia pola listy.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartPo*<br/>
Zawiera indeks od zera elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolną część pola listy, kontynuuje od góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* jest -1, całe pole listy jest wyszukiwane od początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pasującego elementu lub LB_ERR, jeśli wyszukiwanie zakończyło się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Użyj [selectstring](#selectstring) funkcji elementu członkowskiego, aby zarówno znaleźć i wybrać ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact

Znajduje pierwszy ciąg pola listy, który pasuje do ciągu określonego w *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart (Początek)*<br/>
Określa indeks od zera elementu przed pierwszym elementem, który ma zostać przeszukany. Gdy wyszukiwanie osiągnie dolną część pola listy, kontynuuje od góry pola listy z powrotem do elementu określonego przez *nIndexStart*. Jeśli *nIndexStart* wynosi -1, całe pole listy jest wyszukiwane od początku.

*Lpszfind*<br/>
Wskazuje ciąg zakończony z wartością null do wyszukania. Ten ciąg może zawierać pełną nazwę pliku, w tym rozszerzenie. W wyszukiwaniu nie rozróżnia się wielkość liter, więc ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks pasującego elementu lub LB_ERR, jeśli wyszukiwanie zakończyło się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Jeśli pole listy zostało utworzone w stylu rysowania właściciela, ale `FindStringExact` bez stylu [LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) funkcja elementu członkowskiego próbuje dopasować wartość doubleword do wartości *lpszFind*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex

Pobiera indeks od zera bieżącego elementu zakotwiczenia w polu listy.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks bieżącego elementu kotwicy, jeśli zakończy się pomyślnie; w przeciwnym razie LB_ERR.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego zaznaczenia element zakotwiczenia jest pierwszym lub ostatnim elementem w bloku sąsiadujących wybranych elementów.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex

Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego zaznaczenia.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera elementu, który ma prostokąt fokusu w polu listy. Jeśli pole listy jest polem listy pojedynczego wyboru, zwracana jest wartość zwracana jest indeksem wybranego elementu, jeśli istnieje.

### <a name="remarks"></a>Uwagi

Element może, ale nie musi być wybrany.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetCaretIndex](#setcaretindex).

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount

Pobiera liczbę elementów w polu listy.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Zwrócona liczba jest o jeden większa niż wartość indeksu ostatniego elementu (indeks jest oparty na wartości zerowej).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel

Pobiera indeks od zera aktualnie wybranego elementu, jeśli istnieje, w polu listy pojedynczego wyboru.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera aktualnie zaznaczonego elementu, jeśli jest to pole listy pojedynczego wyboru. Jest LB_ERR, jeśli żaden element nie jest aktualnie zaznaczony.

W polu listy wielokrotnego wyboru indeks elementu, który ma fokus.

### <a name="remarks"></a>Uwagi

Nie należy `GetCurSel` wywoływać pola listy wielokrotnego wyboru. Zamiast tego użyj [CListBox::GetSelItems.](#getselitems)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent

Pobiera z pola listy szerokość w pikselach, za pomocą której można przewijać w poziomie.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Wartość zwracana

Przewijana szerokość pola listy w pikselach.

### <a name="remarks"></a>Uwagi

Ma to zastosowanie tylko wtedy, gdy pole listy ma poziomy pasek przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData

Pobiera wartość dwusłowa dostarczoną przez aplikację skojarzoną z określonym elementem pola listy.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wartość skojarzona z elementem lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Doubleword wartość była *dwItemData* parametr [wywołania SetItemData.](#setitemdata)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr

Pobiera dostarczoną przez aplikację wartość 32-bitową skojarzoną z określonym elementem pola listy jako wskaźnik **(void).** <strong>\*</strong>

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik lub -1, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight

Określa wysokość elementów w polu listy.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie należy ustawić na 0.

### <a name="return-value"></a>Wartość zwracana

Wysokość elementów w polu listy w pikselach. Jeśli pole listy ma styl [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) zwracaną wartością jest wysokość towaru określonego przez *nIndex*. Jeśli wystąpi błąd, zwracana wartość jest LB_ERR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect

Pobiera wymiary prostokąta, który ogranicza element pola listy, ponieważ jest on aktualnie wyświetlany w oknie pola listy.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera towaru.

*Lprect*<br/>
Określa długi wskaźnik do [struktury RECT,](/windows/win32/api/windef/ns-windef-rect) która odbiera współrzędne klienta pola listy elementu.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo

Pobiera liczbę elementów na kolumnę.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na `CListBox` kolumnę obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu LB_GETLISTBOXINFO,](/windows/win32/Controls/lb-getlistboxinfo) zgodnie z opisem w windows SDK.

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale

Pobiera ustawienia regionalne używane przez pole listy.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość identyfikatora ustawień regionalnych (LCID) dla ciągów w polu listy.

### <a name="remarks"></a>Uwagi

Ustawienia regionalne są używane, na przykład, do określenia kolejności sortowania ciągów w polu listy posortowane.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetLocale](#setlocale).

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel

Pobiera stan wyboru elementu.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera towaru.

### <a name="return-value"></a>Wartość zwracana

Liczba dodatnia, jeśli zaznaczony jest określony element; w przeciwnym razie jest to 0. Wartość zwracana jest LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego działa zarówno z polami listy pojedynczego, jak i wielokrotnego wyboru.

Aby pobrać indeks aktualnie zaznaczonego elementu pola listy, użyj [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount

Pobiera całkowitą liczbę zaznaczonych elementów w polu listy wielokrotnego wyboru.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba zaznaczonych elementów w polu listy. Jeśli pole listy jest polem listy z pojedynczym wyborem, zwracana wartość jest LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::GetSelItems](#getselitems).

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems

Wypełnia bufor tablicą liczb całkowitych określającą numery towarów wybranych elementów w polu listy wielokrotnego zaznaczenia.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nMaxItems ( nMaxItems )*<br/>
Określa maksymalną liczbę wybranych elementów, których numery towarów mają być umieszczone w buforze.

*rgIndex ( rgIndex )*<br/>
Określa wskaźnik do buforu wystarczająco duży dla liczby całkowitych określonych przez *nMaxItems*.

### <a name="return-value"></a>Wartość zwracana

Rzeczywista liczba elementów umieszczonych w buforze. Jeśli pole listy jest polem listy z pojedynczym wyborem, zwracaną wartością jest `LB_ERR`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox::GetText

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

*Nindex*<br/>
Określa indeks od zera ciągu do pobrania.

*lpszBuffer (lpszBuffer)*<br/>
Wskazuje bufor, który odbiera ciąg. Bufor musi mieć wystarczającą ilość miejsca dla ciągu i kończący się znak null. Rozmiar ciągu można określić z wyprzedzeniem, `GetTextLen` wywołując funkcję elementu członkowskiego.

*rString*<br/>
Odwołanie do `CString` obiektu.

### <a name="return-value"></a>Wartość zwracana

Długość (w bajtach) ciągu, z wyłączeniem kończącego się znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest LB_ERR.

### <a name="remarks"></a>Uwagi

Drugi formularz tej funkcji elementu `CString` członkowskiego wypełnia obiekt tekstem ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen

Pobiera długość ciągu w elemencie pola listy.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera ciągu.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w znakach, z wyłączeniem kończącego się znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::GetText](#gettext).

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex

Pobiera indeks od zera pierwszego widocznego elementu w polu listy.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pierwszego widocznego elementu w polu listy, jeśli zakończy się pomyślnie, LB_ERR w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Początkowo element 0 znajduje się u góry pola listy, ale jeśli pole listy jest przewijane, inny element może znajdować się u góry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage

Przydziela pamięć do przechowywania elementów pola listy.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parametry

*nNauki*<br/>
Określa liczbę elementów do dodania.

*n Bajty*<br/>
Określa ilość pamięci w bajtach, aby przydzielić dla ciągów towarów.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, maksymalna liczba elementów, które pole listy można przechowywać przed ponownego przydzielenia pamięci jest potrzebne, w przeciwnym razie LB_ERRSPACE, co oznacza, że nie jest dostępna wystarczająca ilość pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji przed dodaniem `CListBox`dużej liczby elementów do pliku .

Ta funkcja pomaga przyspieszyć inicjowanie pól listy, które mają dużą liczbę elementów (więcej niż 100). Preallocates określonej ilości pamięci, tak aby kolejne [AddString](#addstring), [InsertString](#insertstring)i [Dir](#dir) funkcje zająć jak najkrótszy czas. Można użyć oszacowań dla parametrów. Jeśli przecenić, niektóre dodatkowe pamięci jest przydzielany; Jeśli nie doceniasz, normalna alokacja jest używana dla towarów, które przekraczają wstępnie przydzieloną kwotę.

Tylko system Windows 95/98: Parametr *nItems* jest ograniczony do wartości 16-bitowych. Oznacza to, że pola listy nie mogą zawierać więcej niż 32 767 pozycji. Chociaż liczba elementów jest ograniczona, całkowity rozmiar elementów w polu listy jest ograniczony tylko przez dostępną pamięć.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::Wstawianie

Wstawia ciąg do pola listy.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera pozycji do wstawienia ciągu. Jeśli ten parametr jest -1, ciąg jest dodawany na końcu listy.

*lpszItem*<br/>
Wskazuje ciąg zakończony z wartością null, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pozycji, po której ciąg został wstawiony. Zwracana wartość jest LB_ERR, jeśli wystąpi błąd; zwracana wartość jest LB_ERRSPACE, jeśli nie ma wystarczającego miejsca do przechowywania nowego ciągu.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do Funkcji `InsertString` elementu członkowskiego [AddString,](#addstring) nie powoduje listy z [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu do sortowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint

Określa element pola listy najbliższy punktowi określonej w *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Punkt, dla którego ma być odnajdywać najbliższy element, określony względem lewego górnego rogu obszaru klienta pola listy.

*bOutside (Z boku)*<br/>
Odwołanie do zmiennej BOOL, która zostanie ustawiona na WARTOŚĆ PRAWDA, jeśli *pt* znajduje się poza obszarem klienta pola listy, FALSE, jeśli *pt* znajduje się wewnątrz obszaru klienta pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks najbliższej pozycji do punktu określonego w *pt*.

### <a name="remarks"></a>Uwagi

Za pomocą tej funkcji można określić, który element pola listy kursor myszy zostanie przeniesiony.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem

Wywoływane przez strukturę podczas tworzenia pola listy ze stylem rysowania właściciela.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długi wskaźnik do struktury [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpuj tę funkcję `MEASUREITEMSTRUCT` elementu członkowskiego i wypełnij strukturę, aby poinformować system Windows o wymiarach pola listy. Jeśli pole listy jest tworzony z [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, framework wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski jest wywoływany tylko raz.

Aby uzyskać więcej informacji na temat [używania](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu LBS_OWNERDRAWFIXED w `SubclassDlgItem` polu listy `CWnd`rysowania właściciela utworzonego za pomocą funkcji członkowskiej , zobacz dyskusję w [notatce technicznej 14](../../mfc/tn014-custom-controls.md).

Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent

Usuwa wszystkie elementy z pola listy.

```cpp
void ResetContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString

Wyszukuje element pola listy, który pasuje do określonego ciągu, a jeśli zostanie znaleziony pasujący element, wybiera element.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartPo*<br/>
Zawiera indeks od zera elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolną część pola listy, kontynuuje od góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* jest -1, całe pole listy jest wyszukiwane od początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony z wartością null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks wybranego elementu, jeśli wyszukiwanie zakończyło się pomyślnie. Jeśli wyszukiwanie nie powiodło się, zwracana wartość jest LB_ERR, a bieżące zaznaczenie nie zostanie zmienione.

### <a name="remarks"></a>Uwagi

Pole listy zostanie przewijane, jeśli to konieczne, aby wyświetlić zaznaczony element.

Tej funkcji elementu członkowskiego nie można używać z polem listy, które ma [styl LBS_MULTIPLESEL.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

Element jest wybierany tylko wtedy, gdy jego początkowe znaki (od punktu początkowego) pasują do znaków w ciągu określonym przez *lpszItem*.

Użyj `FindString` funkcji elementu członkowskiego, aby znaleźć ciąg bez zaznaczania elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange

Zaznacza wiele kolejnych elementów w polu listy wielokrotnego wyboru.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bWybierz*<br/>
Określa sposób ustawiania zaznaczenia. Jeśli *bWybieracz* ma wartość PRAWDA, ciąg jest zaznaczony i wyróżniony; jeśli FAŁSZ, podświetlenie zostanie usunięte, a ciąg nie jest już zaznaczony.

*nFirstItem*<br/>
Określa indeks oparty na wartości zero pierwszego elementu do skonfigurowania.

*nLastItem*<br/>
Określa indeks od zera ostatniego elementu do ustawionego.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko w polach listy wielokrotnego wyboru. Jeśli chcesz wybrać tylko jeden element w polu listy wielokrotnego wyboru — to znaczy, jeśli *nFirstItem* jest równa *nLastItem* — zamiast tego należy wywołać funkcję elementu członkowskiego [SetSel.](#setsel)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex

Ustawia zakotwiczenie w polu listy wielokrotnego wyboru, aby rozpocząć wybór rozszerzony.

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu pola listy, który będzie kotwicą.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego zaznaczenia element zakotwiczenia jest pierwszym lub ostatnim elementem w bloku sąsiadujących wybranych elementów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex

Ustawia prostokąt fokusu na element w określonym indeksie w polu listy wielokrotnego wyboru.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu, który ma otrzymać prostokąt fokusu w polu listy.

*bScroll (właśc.*<br/>
Jeśli ta wartość wynosi 0, element jest przewijany, dopóki nie będzie w pełni widoczny. Jeśli ta wartość nie jest 0, element jest przewijany, dopóki nie jest przynajmniej częściowo widoczne.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Jeśli element nie jest widoczny, jest przewijany do widoku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth

Ustawia szerokość w pikselach wszystkich kolumn w polu listy wielokolumnowej (utworzonej w stylu [LBS_MULTICOLUMN).](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth ( cxWidth )*<br/>
Określa szerokość w pikselach wszystkich kolumn.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel

Wybiera ciąg i przewija go do widoku, jeśli to konieczne.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nWybranek*<br/>
Określa indeks od zera wybranego ciągu. Jeśli *nSelect* ma -1, pole listy jest ustawione na brak zaznaczenia.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Po zaznaczeniu nowego ciągu pole listy usuwa podświetlenie z poprzednio wybranego ciągu.

Tej funkcji elementu członkowskiego należy używać tylko w polach listy pojedynczego wyboru.

Aby ustawić lub usunąć zaznaczenie w polu listy z wieloma zaznaczeniami, użyj [CListBox::SetSel](#setsel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent

Ustawia szerokość w pikselach, za pomocą której pole listy można przewijać w poziomie.

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxWysekcja*<br/>
Określa liczbę pikseli, za pomocą których pole listy może być przewijane w poziomie.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar pola listy jest mniejszy niż ta wartość, poziomy pasek przewijania przewija elementy w poziomie w polu listy. Jeśli pole listy jest tak duże lub większe niż ta wartość, poziomy pasek przewijania jest ukryty.

Aby odpowiedzieć na `SetHorizontalExtent`wywołanie , pole listy musi zostać zdefiniowane za pomocą stylu [WS_HSCROLL.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

Ta funkcja elementu członkowskiego nie jest przydatna w przypadku pól listy wielokolumnowej. W przypadku pól listy wielokolumnowej należy wywołać `SetColumnWidth` funkcję elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData

Ustawia wartość skojarzoną z określonym elementem w polu listy.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera towaru.

*dwItemData*<br/>
Określa wartość skojarzoną z elementem.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr

Ustawia wartość 32-bitową skojarzoną z określonym elementem w polu listy jako określony wskaźnik **(void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera towaru.

*Pdata*<br/>
Określa wskaźnik, który ma być skojarzony z elementem.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Ten wskaźnik pozostaje prawidłowy przez cały okres ważności pola listy, nawet jeśli względna pozycja elementu w polu listy może ulec zmianie w miarę dodawania lub usuwania elementów. W związku z tym indeks elementu w polu można zmienić, ale wskaźnik pozostaje niezawodny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight

Ustawia wysokość elementów w polu listy.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie należy ustawić na 0.

*cyItemHeight*<br/>
Określa wysokość elementu w pikselach.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli indeks lub wysokość jest nieprawidłowa.

### <a name="remarks"></a>Uwagi

Jeśli pole listy ma [styl LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ta funkcja ustawia wysokość elementu określonego przez *nIndex*. W przeciwnym razie ta funkcja ustawia wysokość wszystkich elementów w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale

Ustawia identyfikator ustawień regionalnych dla tego pola listy.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNoweLocale*<br/>
Wartość nowego identyfikatora ustawień regionalnych (LCID) ustawiona dla pola listy.

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość identyfikatora ustawień regionalnych (LCID) dla tego pola listy.

### <a name="remarks"></a>Uwagi

Jeśli `SetLocale` nie jest wywoływana, domyślne ustawienia regionalne są uzyskiwane z systemu. To domyślne ustawienia regionalne systemu można modyfikować za pomocą aplikacji regionalnej (lub międzynarodowej) Panelu sterowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel

Wybiera ciąg w polu listy wielokrotnego zaznaczenia.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Zawiera indeks od zera ciągu, który ma zostać ustawiony. Jeśli -1, zaznaczenie jest dodawane lub usuwane ze wszystkich ciągów, w zależności od wartości *bSelect*.

*bWybierz*<br/>
Określa sposób ustawiania zaznaczenia. Jeśli *bWybieracz* ma wartość PRAWDA, ciąg jest zaznaczony i wyróżniony; jeśli FAŁSZ, podświetlenie zostanie usunięte, a ciąg nie jest już zaznaczony. Określony ciąg jest zaznaczony i wyróżniony domyślnie.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Tej funkcji elementu członkowskiego należy używać tylko w polach listy wielokrotnego wyboru.

Aby zaznaczyć element z pola listy pojedynczego zaznaczenia, użyj [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops

Ustawia pozycje tabulatora w polu listy.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Tabulatory są ustawiane na każdym *cxEachStop* jednostek dialogowych. Opis jednostki dialogowej można znaleźć w *rgTabStops.*

*nTabStops (Niem.*<br/>
Określa liczbę tabulatorów, które mają być w polu listy.

*rgTabStops (100)*<br/>
Wskazuje pierwszy element członkowski tablicy liczby całkowitych zawierający pozycje tabulatora w jednostkach dialogowych. Jednostka dialogowa jest odległością poziomą lub pionową. Jedna pozioma jednostka okna dialogowego jest równa jednej czwartej bieżącej jednostki szerokości podstawy okna dialogowego, a jedna pionowa jednostka okna dialogowa jest równa jednej ósmej bieżącej jednostki wysokości bazowej okna dialogowego. Jednostki podstawowe okna dialogowego są obliczane na podstawie wysokości i szerokości bieżącej czcionki systemowej. Funkcja `GetDialogBaseUnits` Systemu Windows zwraca bieżące jednostki bazowe okna dialogowego w pikselach. Tabulatory muszą być sortowane w kolejności rosnącej; tylne karty nie są dozwolone.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli wszystkie karty zostały ustawione; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby ustawić tabulatory na domyślny rozmiar 2 jednostek dialogowych, należy wywołać wersję bez parametrów tej funkcji elementu członkowskiego. Aby ustawić tabulatory na rozmiar inny niż 2, wywołaj wersję z argumentem *cxEachStop.*

Aby ustawić tabulatory na tablicę rozmiarów, użyj wersji z *argumentami rgTabStops* i *nTabStops.* Dla każdej wartości w *rgTabStops*zostanie ustawiony tabulator , do liczby określonej przez *nTabStops*.

Aby odpowiedzieć na `SetTabStops` wywołanie funkcji elementu członkowskiego, pole listy musi zostać utworzone w stylu [LBS_USETABSTOPS.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex

Zapewnia, że określony element pola listy jest widoczny.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Określa indeks od zera elementu pola listy.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

System przewija pole listy, dopóki element określony przez *nIndex* nie pojawi się u góry pola listy lub nie zostanie osiągnięty maksymalny zakres przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem

Wywoływane przez strukturę, gdy okno nadrzędne pola listy odbiera komunikat WM_VKEYTOITEM z pola listy.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*klawisze*<br/>
Kod klucza wirtualnego klucza, który użytkownik nacisnął. Aby uzyskać listę standardowych kodów kluczy wirtualnych, zobacz Winuser.h

*Nindex*<br/>
Bieżąca pozycja list-box caret.

### <a name="return-value"></a>Wartość zwracana

Zwraca — 2 dla braku dalszych działań, - 1 dla akcji domyślnej lub numer nieujemny, aby określić indeks elementu pola listy, na którym ma być wykonać domyślną akcję dla naciśnięcia klawisza.

### <a name="remarks"></a>Uwagi

Wiadomość WM_VKEYTOITEM jest wysyłana przez pole listy po odebraniu wiadomości WM_KEYDOWN, ale tylko wtedy, gdy pole listy spełnia obie następujące elementy:

- Ma zestaw stylu [LBS_WANTKEYBOARDINPUT.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

- Posiada co najmniej jeden element.

Nigdy nie należy nazywać tej funkcji samodzielnie. Zastąd w tej funkcji należy zapewnić własną niestandardową obsługę komunikatów klawiatury.

Należy zwrócić wartość, aby poinformować platformę, jakie działania wykonano przez zastąpienie. Zwracana wartość — 2 wskazuje, że aplikacja obsługiwała wszystkie aspekty wyboru elementu i nie wymaga dalszych działań w polu listy. Przed powrotem - 2, można ustawić zaznaczenie lub przenieść daszek lub obu. Aby ustawić zaznaczenie, użyj [setcursel](#setcursel) lub [SetSel](#setsel). Aby przenieść cieszę, użyj [funkcji SetCaretIndex](#setcaretindex).

Zwracana wartość — 1 wskazuje, że pole listy powinno wykonać akcję domyślną w odpowiedzi na naciśnięcie klawisza. Domyślna implementacja zwraca - 1.

Zwracana wartość 0 lub większa określa indeks elementu w polu listy i wskazuje, że pole listy powinno wykonać domyślną akcję dla naciśnięcia klawisza w danym elemencie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)
