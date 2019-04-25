---
title: Clistbox — klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: b448f725bac68c2b67dc44d660c664c075aa86da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225272"
---
# <a name="clistbox-class"></a>Clistbox — klasa

Oferuje funkcje pola listy Windows.

## <a name="syntax"></a>Składnia

```
class CListBox : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Konstruuje `CListBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Dodaje ciąg do pola listy.|
|[CListBox::CharToItem](#chartoitem)|Należy przesłonić, aby podać niestandardowy WM_CHAR obsługi rysowania przez właściciela pola listy, które nie zawierają ciągi.|
|[CListBox::CompareItem](#compareitem)|Metoda wywoływana przez platformę, by określić pozycję Nowy element w polu listy rysowane przez właściciela posortowany.|
|[CListBox::Create](#create)|W polu listy Windows tworzy i dołącza je do `CListBox` obiektu.|
|[CListBox::DeleteItem](#deleteitem)|Wywoływane przez platformę, gdy użytkownik usuwa element w polu listy rysowane przez właściciela.|
|[CListBox::DeleteString](#deletestring)|Usuwa ciągiem w polu listy.|
|[CListBox::Dir](#dir)|Dodaje nazw plików, dysków lub oba z bieżącego katalogu, do pola listy.|
|[CListBox::DrawItem](#drawitem)|Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmian pole listy rysowane przez właściciela.|
|[CListBox::FindString](#findstring)|Wyszukuje ciąg w polu listy.|
|[CListBox::FindStringExact](#findstringexact)|Umożliwia znalezienie ciągu pierwszego pola listy, który pasuje do określonego ciągu.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Pobiera liczony od zera indeks bieżącego elementu zakotwiczenia w polu listy.|
|[CListBox::GetCaretIndex](#getcaretindex)|Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego wyboru.|
|[CListBox::GetCount](#getcount)|Zwraca liczbę ciągów, w polu listy.|
|[CListBox::GetCurSel](#getcursel)|Zwraca liczony od zera indeks zaznaczonego ciągu w polu listy.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, że pole listy może być przewijane w poziomie.|
|[CListBox::GetItemData](#getitemdata)|Zwraca 32-bitową wartość skojarzona z elementem pola listy.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Zwraca wskaźnik do elementu pola listy.|
|[CListBox::GetItemHeight](#getitemheight)|Określa wysokość elementów w polu listy.|
|[CListBox::GetItemRect](#getitemrect)|Zwraca prostokąt otaczający element pola listy jest aktualnie wyświetlany.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Pobiera liczbę elementów w kolumnie.|
|[CListBox::GetLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola listy.|
|[CListBox::GetSel](#getsel)|Zwraca stan zaznaczenia elementu pola listy.|
|[CListBox::GetSelCount](#getselcount)|Zwraca liczbę ciągów, które aktualnie wybrane w polu listy wielokrotnego wyboru.|
|[CListBox::GetSelItems](#getselitems)|Zwraca indeksów ciągów aktualnie wybrane w polu listy.|
|[CListBox::GetText](#gettext)|Kopiuje element pola listy do bufora.|
|[CListBox::GetTextLen](#gettextlen)|Zwraca długość w bajtach elementu pola listy.|
|[CListBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego ciągu widoczny w polu listy.|
|[CListBox::InitStorage](#initstorage)|Preallocates bloki pamięci dla elementów pola listy i ciągów.|
|[CListBox::InsertString](#insertstring)|Wstawia ciąg z określonej lokalizacji, w polu listy.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Zwraca indeks elementu pola listy najbliższy punkt.|
|[CListBox::MeasureItem](#measureitem)|Wywoływane przez platformę, podczas tworzenia pole listy rysowane przez właściciela, aby określić wymiary pole listy.|
|[CListBox::ResetContent](#resetcontent)|Czyści wszystkie wpisy w polu listy.|
|[CListBox::SelectString](#selectstring)|Wyszukuje i wybiera ciąg w polu listy z pojedynczym wyborem.|
|[CListBox::SelItemRange](#selitemrange)|Powoduje wybranie lub anulowanie szeroką gamę ciągów w polu listy wielokrotnego wyboru.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Ustawia zakotwiczenia w polu listy wielokrotnego wyboru umożliwiającą wybór rozszerzonej.|
|[CListBox::SetCaretIndex](#setcaretindex)|Ustawia element pod określonym indeksem prostokąt fokusu w polu listy wielokrotnego wyboru.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Ustawia szerokość kolumny wielokolumnowe pole listy.|
|[CListBox::SetCurSel](#setcursel)|Określa ciąg w polu listy.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Określa szerokość w pikselach, że pole listy może być przewijane w poziomie.|
|[CListBox::SetItemData](#setitemdata)|Ustawia wartość 32-bitowych, skojarzone z elementem pola listy.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik do elementu pola listy.|
|[CListBox::SetItemHeight](#setitemheight)|Określa wysokość elementów w polu listy.|
|[CListBox::SetLocale](#setlocale)|Określa identyfikator ustawień regionalnych dla pola listy.|
|[CListBox::SetSel](#setsel)|Wybiera lub usuwa ich zaznaczenie elementu pola listy w polu listy wielokrotnego wyboru.|
|[CListBox::SetTabStops](#settabstops)|Ustawienie pozycji tabulatorów w polu listy.|
|[CListBox::SetTopIndex](#settopindex)|Ustawia liczony od zera indeks pierwszego ciągu widoczny w polu listy.|
|[CListBox::VKeyToItem](#vkeytoitem)|Należy przesłonić ten element, aby podać niestandardowy przetłumaczyła obsługi dla pola listy z zestawem styl LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Uwagi

Pole listy wyświetla listę elementów, takich jak nazwy plików, które użytkownik może wyświetlać i wybierać.

W polu listy z pojedynczym wyborem użytkownik może wybrać tylko jeden element. W polu listy wielokrotnego wyboru można wybrać zakres elementów. Gdy użytkownik wybierze element, jest wyróżniona i pole listy wysyła powiadomienie do okna nadrzędnego.

Można utworzyć pola listy, z szablonu okna dialogowego lub bezpośrednio w kodzie. Aby utworzyć bezpośrednio, należy utworzyć `CListBox` obiektu, a następnie wywołaj [Utwórz](#create) funkcja elementu członkowskiego, aby utworzyć formant pola listy Windows i dołączyć go do `CListBox` obiektu. Aby korzystać z pola listy w szablonu okna dialogowego, Zadeklaruj zmienną pola listy w klasie okno dialogowe, a następnie użyj `DDX_Control` w klasie okno dialogowe `DoDataExchange` funkcję, aby połączyć zmiennej składowej do kontrolki. (to jest wykonywane automatycznie po dodaniu zmienna sterująca do klasy okno dialogowe.)

Konstrukcja może być jednoetapowy proces w klasę pochodną `CListBox`. Zapisywanie konstruktora dla klasy pochodnej i wywołanie `Create` z w konstruktorze.

Jeśli chcesz obsługiwać Windows powiadomienia wysyłane przez pole listy do elementu nadrzędnego (zazwyczaj klasą pochodną [CDialog](../../mfc/reference/cdialog-class.md)), dodanie funkcji składowej wejścia i program obsługi komunikatów mapy komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów ma następującą postać:

`ON_Notification( id, memberFxn )`

gdzie `id` Określa identyfikator okna elementu podrzędnego kontrolki pola listy, wysyłania powiadomienia i `memberFxn` nazywa się nadrzędny element członkowski funkcji zostały napisane do obsługi powiadomień.

Prototyp funkcji elementu nadrzędnego jest następująca:

`afx_msg void memberFxn( );`

Poniżej przedstawiono listę potencjalnych wpisy mapy komunikatów i opis przypadków, w których będą one wysyłane do elementu nadrzędnego:

- ON_LBN_DBLCLK użytkownik kliknie dwukrotnie ciąg w polu listy. Tylko pole listy, który ma [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl wyśle taki komunikat powiadomienia.

- ON_LBN_ERRSPACE pola listy nie może przydzielić wystarczającej ilości pamięci, aby spełnić żądania.

- Pole listy ON_LBN_KILLFOCUS utracie fokusu wprowadzania.

- Bieżące zaznaczenie pola listy ON_LBN_SELCANCEL zostało anulowane. Ta wiadomość jest wysyłana tylko wtedy, gdy pole listy ma styl LBS_NOTIFY.

- Zmieniono ON_LBN_SELCHANGE zaznaczenia w polu listy. Tego powiadomienia nie są wysyłane, jeśli zaznaczenie zostanie zmienione przez [CListBox::SetCurSel](#setcursel) funkcja elementu członkowskiego. To powiadomienie dotyczy tylko pola listy, którego styl LBS_NOTIFY. LBN_SELCHANGE komunikatu powiadomienia są wysyłane pola listy wielokrotnego wyboru zawsze wtedy, gdy użytkownik naciśnie klawisz strzałki, nawet wtedy, gdy nie zmienia zaznaczenia.

- ON_LBN_SETFOCUS pola listy otrzymuje fokus wprowadzania.

- ON_WM_CHARTOITEM pole listy rysowane przez właściciela, które ma nie ciągi odbiera komunikat WM_CHAR.

- Pole listy A ON_WM_VKEYTOITEM ze stylem LBS_WANTKEYBOARDINPUT odbiera przetłumaczyła komunikat.

Jeśli tworzysz `CListBox` obiektu w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CListBox` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

Jeśli tworzysz `CListBox` obiekt w tym oknie, konieczne może być zniszczyć `CListBox` obiektu. Jeśli tworzysz `CListBox` obiektów na stosie, zostanie zniszczony automatycznie. Jeśli tworzysz `CListBox` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** obiektu zniszczyć ją, gdy użytkownik zamknie okno nadrzędne.

Jeśli przydzielisz wszystkie pamięci w `CListBox` obiektów, Zastąp `CListBox` destruktora w celu usunięcia alokacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

Dodaje ciąg do pola listy.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks na ciąg w polu listy. Wartość zwracana jest LB_ERR, jeśli wystąpi błąd; Wartość zwracana jest LB_ERRSPACE, jeśli brak wystarczającej ilości miejsca do przechowywania nowego ciągu znaków.

### <a name="remarks"></a>Uwagi

Jeśli pole listy nie został utworzony za pomocą [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, ciąg zostanie dodany na końcu listy. W przeciwnym razie ten ciąg jest wstawiany do listy, a lista jest posortowana. Jeśli pole listy zostało utworzone przy użyciu stylu LBS_SORT, ale nie [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, w ramach sortuje listę według jedną lub więcej wywołań `CompareItem` funkcja elementu członkowskiego.

Użyj [InsertString](#insertstring) Aby wstawić ciąg do określonej lokalizacji w obrębie pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

Wywoływane przez platformę, gdy okno nadrzędne pola listy otrzymuje komunikat WM_CHARTOITEM z listy rozwijanej.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Kod ANSI znak wpisany przez użytkownika.

*nIndex*<br/>
Bieżące położenie karetki pola listy.

### <a name="return-value"></a>Wartość zwracana

Zwraca - 1 lub - 2, żadne dalsze działania lub nieujemna liczba, aby określić indeks elementu pola listy, na którym należy wykonać domyślną akcję dla naciśnięcia klawisza. Domyślna implementacja zwraca - 1.

### <a name="remarks"></a>Uwagi

WM_CHARTOITEM komunikat jest wysyłany przez pole listy, gdy otrzyma komunikat WM_CHAR, ale tylko wtedy, gdy pole listy spełnia wszystkie poniższe kryteria:

- To pole listy rysowane przez właściciela.

- Nie ma [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu zestawu.

- Ma co najmniej jeden element.

Możesz nigdy nie powinien wywoływać tę funkcję samodzielnie. Należy przesłonić tę funkcję, aby zapewnić własną niestandardową obsługę komunikatów klawiatury.

W przypadku przesłonięcia musi zwracać wartość, aby poinformować szablon, jaką akcję należy wykonać. Zwracana wartość - 1 lub - 2 wskazuje obsługiwane wszystkie aspekty zaznaczenie elementu, a następnie wymaga żadne dalsze działania, w polu listy. Przed zwróceniem - 1 lub - 2, możesz można ustawić zaznaczenie lub Przenieś karetkę i / lub. Aby ustawić zaznaczenie, należy użyć [setcursel —](#setcursel) lub [SetSel](#setsel). Aby przenieść karetki, należy użyć [SetCaretIndex](#setcaretindex).

Zwracana wartość wynosząca 0 lub większy Określa indeks elementu w polu listy i wskazuje, że pole listy należy wykonywać domyślną akcję dla naciśnięcia klawisza dla danego elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>  CListBox::CListBox

Konstruuje `CListBox` obiektu.

```
CListBox();
```

### <a name="remarks"></a>Uwagi

Konstruowanie `CListBox` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora `ClistBox` , a następnie wywołać `Create`, która inicjuje polu listy Windows i dołącza go do `CListBox`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

Metoda wywoływana przez platformę, aby określić względne położenie nowego elementu w polu listy rysowane przez właściciela posortowany.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Długie wskaźnik do `COMPAREITEMSTRUCT` struktury.

### <a name="return-value"></a>Wartość zwracana

Wskazuje względne położenie dwa elementy, które opisano w [COMPAREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct) struktury. Może to być dowolny z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|-1|Sortuje element 1 przed elementem 2.|
|0|Element 1 i element 2 Sortuj takie same.|
|1|Sortuje element 1 po elemencie 2.|

Zobacz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) opis `COMPAREITEMSTRUCT` struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Jeśli tworzysz pole listy rysowane przez właściciela ze stylem LBS_SORT, konieczne jest przesłonięcie tej funkcji elementu członkowskiego ułatwiających ramach sortowanie nowe elementy dodane do pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

W polu listy Windows tworzy i dołącza je do `CListBox` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola listy. Zastosuj dowolną kombinację [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) do pola.

*Rect*<br/>
Określa pole listy rozmiar i położenie. Może być `CRect` obiektu lub `RECT` struktury.

*pParentWnd*<br/>
Określa pole listy okna nadrzędnego (zazwyczaj `CDialog` obiektu). Nie może być równa NULL.

*nID*<br/>
Określa identyfikator pola listy kontroli.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CListBox` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, która inicjuje polu listy Windows i dołącza go do `CListBox` obiektu.

Gdy `Create` wykonuje Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) komunikaty do kontrolki pola listy.

Te komunikaty są obsługiwane domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [ongetminmaxinfo —](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcji elementów członkowskich w `CWnd` klasy bazowej. Aby rozszerzyć domyślnej obsługi komunikatów, należy wyprowadzić klasę z `CListBox`, dodać mapy komunikatów do nowej klasy, a zastąpienie poprzedniej funkcji elementów członkowskich programu obsługi komunikatów. Zastąp `OnCreate`, na przykład do przeprowadzenia wymaganych inicjowania dla nowej klasy.

Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pola listy.

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL Aby dodać pionowy pasek przewijania

- WS_HSCROLL Aby dodać poziomy pasek przewijania

- WS_GROUP kontrolek grupy

- WS_TABSTOP zezwolić na klawiszem TAB do tego formantu

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

Wywoływane przez platformę, gdy użytkownik usuwa element z rysowanym przez właściciela `CListBox` obiektu lub niszczy pola listy.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Długie wskaźnik do Windows [DELETEITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct) strukturę, która zawiera informacje na temat usuniętego elementu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Należy przesłonić tę funkcję, by narysować ponownie rysowane przez właściciela pola listy, zgodnie z potrzebami.

Zobacz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) opis `DELETEITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

Usuwa element w miejscu *nIndex* z listy rozwijanej.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks ciągu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Liczba parametrów na liście. Wartość zwracana jest LB_ERR, jeśli *nIndex* Określa indeks jest większa niż liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wszystkie elementy występujące *nIndex* teraz Przenieś w dół o jedną pozycję. Na przykład jeśli pole listy zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałe które mają być teraz na pierwszym miejscu. *nIndex*= 0 dla elementu na pierwszym miejscu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>  CListBox::Dir

Dodaje listę nazw plików, dysków lub obydwa elementy w polu listy.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*attr*<br/>
Może być dowolną kombinacją **wyliczenia** wartości opisane w `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus), lub dowolnej kombinacji następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|0x0000|Plik może odczytywać lub zapisywana.|
|0x0001|Plik można odczytać z, ale nie zapisane.|
|0x0002|Plik jest ukryta i nie ma na liście katalogów.|
|0x0004|Plik jest plikiem systemu.|
|0x0010|Nazwa określona przez *lpszWildCard* Określa katalog.|
|0x0020|Plik został zarchiwizowany.|
|0x4000|Obejmują wszystkie dyski, które odpowiada nazwie określonej przez *lpszWildCard*.|
|0x8000|Flaga wyłączności. Wyłączne flaga jest ustawiona, wyświetlane są tylko pliki o określonym typie. W przeciwnym razie pliki o określonym typie są wymienione oprócz plików "normal".|

*lpszWildCard*<br/>
Wskazuje ciąg specyfikacji pliku. Ciąg może zawierać symbole wieloznaczne (na przykład *.\*).

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks ostatniego filename dodany do listy. Wartość zwracana jest LB_ERR, jeśli wystąpi błąd; Wartość zwracana jest LB_ERRSPACE w przypadku niewystarczającej ilości miejsca do przechowywania nowych parametrów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>  CListBox::DrawItem

Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmian pole listy rysowane przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długie wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.

### <a name="remarks"></a>Uwagi

`itemAction` i `itemState` członkowie `DRAWITEMSTRUCT` struktury zdefiniować rysowania akcję, która ma zostać wykonane.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CListBox` obiektu. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed ten element członkowski funkcja kończy.

Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis `DRAWITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

Znajduje pierwszy ciąg w polu listy, który zawiera określony prefiks bez zmiany zaznaczenia pola listy.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* wynosi -1, pole listy cały przeszukiwany jest od samego początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne, więc ten ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pasujący element lub LB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Użyj [SelectString](#selectstring) funkcja elementu członkowskiego, aby znaleźć i wybrać ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

Wyszukuje pierwszy ciąg pola listy, który pasuje do ciągu określonego w *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Określa liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nIndexStart*. Jeśli *nIndexStart* wynosi -1, pole listy cały przeszukiwany jest od samego początku.

*lpszFind*<br/>
Wskazuje ciąg zakończony wartością null do wyszukania. Ten ciąg może zawierać pełną nazwę pliku, łącznie z rozszerzeniem. Wyszukiwanie nie jest uwzględniana wielkość liter, więc ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks pasujący element lub LB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli pole listy został utworzony przy użyciu stylu rysowania przez właściciela, ale bez [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu `FindStringExact` funkcja elementu członkowskiego podejmuje próbę dopasowania wartości bitowego względem wartości *lpszFind*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

Pobiera liczony od zera indeks bieżącego elementu zakotwiczenia w polu listy.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks bieżącego elementu zakotwiczenia w przypadku powodzenia; w przeciwnym razie LB_ERR.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego wyboru elementu zakotwiczenia jest pierwszego lub ostatniego elementu w bloku ciągłych wybrane elementy.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

Określa indeks elementu, który ma prostokąt fokusu w polu listy wielokrotnego wyboru.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks elementu, który ma prostokąt fokusu w polu listy. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, wartość zwracana jest indeks elementu, który jest wybrany, jeśli istnieje.

### <a name="remarks"></a>Uwagi

Elementu może lub nie mogą być zaznaczone.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>  CListBox::GetCount

Pobiera liczbę elementów w polu listy.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Zwrócona liczba jest większa o jeden od ostatniego elementu (indeks jest liczony od zera) wartości indeksu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

Pobiera liczony od zera Indeks aktualnie wybranego elementu, jeśli istnieje, w polu listy z pojedynczym wyborem.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera Indeks aktualnie wybranego elementu, jeśli jest polem listy z pojedynczym wyborem. Jest to LB_ERR, jeśli żaden element nie jest aktualnie wybrany.

W polu listy wielokrotnego wyboru indeks elementu, który ma fokus.

### <a name="remarks"></a>Uwagi

Nie wywołuj `GetCurSel` pola listy wielokrotnego wyboru. Użyj [CListBox::GetSelItems](#getselitems) zamiast tego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>  CListBox::GetHorizontalExtent

Pobiera z listy rozwijanej szerokość w pikselach, według których go może być przewijane w poziomie.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Wartość zwracana

Przewijany szerokość pola listy, w pikselach.

### <a name="remarks"></a>Uwagi

Ma to zastosowanie tylko wtedy, gdy pole listy ma poziomy pasek przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

Pobiera wartość bitowego dostarczonych aplikacji skojarzone z elementem pola listy.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

32-bitową wartość skojarzony element lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Wartość bitowego *dwItemData* parametru [setitemdata —](#setitemdata) wywołania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

Pobiera 32-bitowa aplikacja dostarczona wartość skojarzone z elementem pola listy jako wskaźnik (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik lub wartość -1, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

Określa wysokość elementów w polu listy.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie należy ustawić na wartość 0.

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach elementów w polu listy. Jeśli pole listy ma [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, wartość zwracana jest wysokość elementu określonego przez *nIndex*. Jeśli wystąpi błąd, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

Pobiera dany element granice pole listy wymiary prostokąta, gdy jest aktualnie wyświetlany w oknie pola listy.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu.

*lpRect*<br/>
Określa długie wskaźnik [struktura RECT](/windows/desktop/api/windef/ns-windef-tagrect) odbierająca współrzędne klienta pole listy elementu.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

Pobiera liczbę elementów w kolumnie.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na kolumnie `CListBox` obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność [LB_GETLISTBOXINFO](/windows/desktop/Controls/lb-getlistboxinfo) komunikat, zgodnie z opisem w zestawie Windows SDK.

##  <a name="getlocale"></a>  CListBox::GetLocale

Pobiera ustawienia regionalne używane przez pola listy.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość identyfikatora (LCID) ustawień regionalnych dla ciągów w polu listy.

### <a name="remarks"></a>Uwagi

Ustawienia regionalne jest używany na przykład, aby określić kolejność sortowania ciągów w polu posortowanej listy.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetLocale](#setlocale).

##  <a name="getsel"></a>  CListBox::GetSel

Pobiera stan zaznaczenia elementu.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu.

### <a name="return-value"></a>Wartość zwracana

Liczba dodatnia, jeśli określony element jest wybrany; w przeciwnym razie to 0. Wartość zwracana jest LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego współpracuje z obu pól listy wyboru wielu i jednego.

Aby uzyskać indeks elementu aktualnie wybrany listy, pola, użyj [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

Pobiera całkowitą liczbę wybranych elementów w polu listy wielokrotnego wyboru.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba wybranych elementów w polu listy. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, wartość zwracana jest LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::GetSelItems](#getselitems).

##  <a name="getselitems"></a>  CListBox::GetSelItems

Wypełnia bufor tablicy liczb całkowitych, który określa element liczby wybranych elementów w polu listy wielokrotnego wyboru.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parametry

*nMaxItems*<br/>
Określa maksymalną liczbę wybranych elementów, których numery elementów, które mają być umieszczone w buforze.

*rgIndex*<br/>
Określa wskaźnik do buforu wystarczająco duży dla liczb całkowitych, określony przez *nMaxItems*.

### <a name="return-value"></a>Wartość zwracana

Rzeczywista liczba elementów jest umieszczony w buforze. Jeśli pole listy ma postać pola listy z pojedynczym wyborem, wartość zwracana jest `LB_ERR`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

Pobiera ciąg w polu listy.

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
Określa liczony od zera indeks ciągu, które mają zostać pobrane.

*lpszBuffer*<br/>
Wskazuje buforu, który odbiera ciąg. Rozmiar buforu musi mieć wystarczającą ilość miejsca na ciąg i kończącego znaku null. Można określić rozmiar ciągu wcześniej przez wywołanie metody `GetTextLen` funkcja elementu członkowskiego.

*rString*<br/>
Odwołanie do `CString` obiektu.

### <a name="return-value"></a>Wartość zwracana

Długość (w bajtach) ciąg, z wyjątkiem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowy indeks, zwracana jest wartość LB_ERR.

### <a name="remarks"></a>Uwagi

Druga forma ten element członkowski funkcji wypełnienia `CString` obiektu z ciąg tekstu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

Pobiera długość ciągu w elemencie pola listy.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks w ciągu.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu znaków, z wyjątkiem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowy indeks, zwracana jest wartość LB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::GetText](#gettext).

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

Pobiera liczony od zera indeks pierwszego elementu widoczny w polu listy.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pierwszego elementu widoczny w polu listy, jeśli to się powiedzie, w przeciwnym razie LB_ERR.

### <a name="remarks"></a>Uwagi

Początkowo element 0 jest w górnej części pola listy, ale jeśli jest przewijane w polu listy, innego elementu może być u góry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

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
Określa ilość pamięci w bajtach, można przydzielić elementu ciągów.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja się powiedzie, maksymalna liczba elementów, które mogą być przechowywane na liście przed ponowne przydzielenie pamięci jest potrzebne, w przeciwnym razie LB_ERRSPACE, nie oznacza, jest dostępna wystarczająca ilość pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, przed dodaniem dużą liczbę elementów do `CListBox`.

Ta funkcja pomaga w szybszym inicjowania pola listy, które mają dużą liczbę elementów (ponad 100). Jego preallocates określonej ilości pamięci, dlatego oznacza kolejne [addstring —](#addstring), [InsertString](#insertstring), i [Dir](#dir) funkcje podejmują najkrótszym czasie. Można użyć szacunki dla parametrów. Jeśli overestimate, niektóre dodatkowe pamięć została przydzielona; Jeśli zaniżają, normalne alokacji jest używany dla elementów, które przekraczają kwotę przydzielony wstępnie.

Windows 95/98 tylko: *NItems* parametru jest ograniczona do wartości 16-bitowych. Oznacza to, że pola listy nie może zawierać więcej niż 32 767 elementów. Mimo że liczba elementów jest ograniczone, całkowity rozmiar elementów w polu listy jest ograniczony tylko ilością dostępnej pamięci.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

Wstawia ciąg w polu listy.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks pozycji, aby wstawić ciąg. Jeśli ten parametr ma wartość -1, ciąg jest dodawany na końcu listy.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, która ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks sytuację, w którym ciąg został wstawiony. Wartość zwracana jest LB_ERR, jeśli wystąpi błąd; Wartość zwracana jest LB_ERRSPACE, jeśli brak wystarczającej ilości miejsca do przechowywania nowego ciągu znaków.

### <a name="remarks"></a>Uwagi

W odróżnieniu od [addstring —](#addstring) funkcja elementu członkowskiego `InsertString` nie powoduje, że lista z [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl ma zostać posortowana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

Określa element pole listy najbliższego punktu określonego w *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
Punkt, dla której wyszukiwany element najbliższej określony względem lewego górnego rogu obszaru klienckiego pola listy.

*bOutside*<br/>
Odwołanie do zmiennej wartość logiczna, która zostanie ustawiony na wartość TRUE, jeśli *pt* znajduje się poza obszar kliencki najbliższej elementu pola listy FAŁSZ Jeśli *pt* znajduje się wewnątrz obszaru klienckiego najbliższej elementu pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu najbliższego punktu określonego w *pt*.

### <a name="remarks"></a>Uwagi

Aby określić, który element pola listy, kursor myszy przesuwa się nad, można użyć tej funkcji.

### <a name="example"></a>Przykład

  Zobacz przykład [CListBox::SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>  CListBox::MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony przy użyciu stylu rysowania przez właściciela pola listy.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długie wskaźnik do [MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct) struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego, a następnie wypełnij `MEASUREITEMSTRUCT` strukturę, aby poinformować Windows wymiary pola listy. Jeśli w polu listy są tworzone za pomocą [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, struktura wywołuje tej funkcji elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ta składowa zostanie wywołana tylko raz.

Aby uzyskać więcej informacji na temat używania [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) style w polu listy rysowane przez właściciela utworzonych za pomocą `SubclassDlgItem` funkcji składowej typu `CWnd`, zobacz Omówienie w [techniczne Uwaga 14](../../mfc/tn014-custom-controls.md).

Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

Usuwa wszystkie elementy w polu listy.

```
void ResetContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

Wyszukiwanie elementu pola listy, które odpowiadają określony ciąg, a jeśli zostanie znaleziony pasujący element, powoduje zaznaczenie elementu.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nStartAfter*. Jeśli *nStartAfter* wynosi -1, pole listy cały przeszukiwany jest od samego początku.

*lpszItem*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne, więc ten ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks zaznaczonego elementu, jeśli wyszukiwanie zakończyło się pomyślnie. Jeśli wyszukiwanie nie powiodło się, wartością zwracaną jest LB_ERR i bieżącego zaznaczenia nie ulegną zmianie.

### <a name="remarks"></a>Uwagi

Pola listy jest przewijane, jeśli to konieczne wyświetlić wybranego elementu w widoku.

Ta funkcja elementu członkowskiego nie można używać z pola listy, który ma [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.

Element jest wybrany tylko wtedy, gdy jego początkowe znaki (z punktem początkowym) dopasowuje znaki w ciągu określonej przez *lpszItem*.

Użyj `FindString` funkcja elementu członkowskiego, aby znaleźć ciąg bez zaznaczania elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

Umożliwia zaznaczenie wielu kolejnych elementów w polu listy wielokrotnego wyboru.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parametry

*bbWybierz*<br/>
Określa sposób ustawiania zaznaczenia. Jeśli *bbWybierz* ma wartość PRAWDA, ciąg jest zaznaczone i wyróżnione; w przypadku wartości FAŁSZ Podświetlenie jest usuwany, a ciąg nie jest zaznaczone.

*nFirstItem*<br/>
Określa liczony od zera indeks pierwszego elementu, aby ustawić.

*nLastItem*<br/>
Określa liczony od zera indeks ostatniego elementu, aby ustawić.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko z polami listy wielokrotnego wyboru. Jeśli musisz wybrać tylko jeden element w polu listy wielokrotnego wyboru — oznacza to, jeśli *nFirstItem* jest równa *nLastItem* — wywołania [SetSel](#setsel) zamiast tego funkcję członkowską.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

Ustawia zakotwiczenia w polu listy wielokrotnego wyboru umożliwiającą wybór rozszerzonej.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu pola listy, który ma być zakotwiczenia.

### <a name="remarks"></a>Uwagi

W polu listy wielokrotnego wyboru elementu zakotwiczenia jest pierwszego lub ostatniego elementu w bloku ciągłych wybrane elementy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

Ustawia element pod określonym indeksem prostokąt fokusu w polu listy wielokrotnego wyboru.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu do odbierania prostokąt fokusu w polu listy.

*bScroll*<br/>
Jeśli ta wartość wynosi 0, element jest przewijane, dopóki nie zostanie całkowicie widoczna. Jeśli ta wartość nie jest 0, jest przewijane elementu, dopóki nie zostanie co najmniej częściowo widoczny.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Jeśli element nie jest widoczny, wartość jest przewijane do widoku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

Określa szerokość w pikselach wszystkie kolumny w wielokolumnowe pole listy (utworzonych za pomocą [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parametry

*cxWidth*<br/>
Określa szerokość w pikselach wszystkie kolumny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

Wybiera ciągu i przewija do widoku, jeśli to konieczne.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nSelect*<br/>
Określa liczony od zera indeks ciągu do wybrania. Jeśli *nWybierz* wynosi -1, jest równa mają Brak zaznaczenia pola listy.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Po wybraniu nowego ciągu znaków pole listy usuwa zaznaczenie z poprzednio wybrane parametry.

Za pomocą tej funkcji elementu członkowskiego tylko pola listy z pojedynczym wyborem.

Aby ustawić lub usunąć zaznaczenie w polu listy wielokrotnego wyboru, należy użyć [CListBox::SetSel](#setsel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>  CListBox::SetHorizontalExtent

Ustawia szerokość w pikselach, według których pole listy może być przewijane w poziomie.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parametry

*cxExtent*<br/>
Określa liczbę pikseli, według których pole listy może być przewijane w poziomie.

### <a name="remarks"></a>Uwagi

Jeśli rozmiar listy jest mniejszy niż ta wartość, poziomych pasków przewijania w poziomie przewinie elementy w polu listy. Jeśli pole to jest za duży lub większe niż ta wartość, poziomy pasek przewijania jest ukryta.

Aby odpowiedzieć na wywołanie `SetHorizontalExtent`, pole listy muszą zdefiniowane za pomocą [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) stylu.

Ta funkcja elementu członkowskiego nie jest przydatne w przypadku pól listy wielokolumnowych. Pola list wielokolumnowe, można wywołać `SetColumnWidth` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

Ustawia wartość 32-bitowych, skojarzone z określonym elementem w polu listy.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu.

*dwItemData*<br/>
Określa wartość, która ma zostać skojarzony z elementem.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

Ustawia wartość 32-bitowych, skojarzone z określonym elementem w polu listy jako określony wskaźnik ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu.

*pData*<br/>
Określa wskaźnik, który ma zostać skojarzony z elementem.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

This, wskaźnik pozostaje ważny przez cały okres istnienia pola listy, mimo że względne położenie elementu w obrębie pola listy może ulec zmianie, elementy są dodawane lub usuwane. W związku z tym można zmienić indeksu elementu w polu, ale wskaźnik pozostaje niezawodne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

Określa wysokość elementów w polu listy.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu w polu listy. Ten parametr jest używany tylko wtedy, gdy pole listy ma styl LBS_OWNERDRAWVARIABLE; w przeciwnym razie należy ustawić na wartość 0.

*cyItemHeight*<br/>
Określa wysokość w pikselach, elementu.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli indeks lub wysokość jest nieprawidłowa.

### <a name="remarks"></a>Uwagi

Jeśli pole listy ma [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, funkcja ta Ustawia wysokość elementu określonego przez *nIndex*. W przeciwnym razie funkcja ta Ustawia wysokość wszystkich elementów w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

Określa identyfikator ustawień regionalnych dla tego pola listy.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nowych ustawień regionalnych (LCID) wartość identyfikatora można ustawić pola listy.

### <a name="return-value"></a>Wartość zwracana

Poprzednich ustawień regionalnych (LCID) wartość identyfikatora dla tego pola listy.

### <a name="remarks"></a>Uwagi

Jeśli `SetLocale` nie jest wywoływana, domyślne ustawienia regionalne są uzyskiwane z systemu. To domyślne ustawienia regionalne systemu można modyfikować za pomocą Panelu sterowania aplikacji regionalne (lub International).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>  CListBox::SetSel

Wybiera ciąg w polu listy wielokrotnego wyboru.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks ciąg do ustawienia. Jeśli wartość -1, wybór jest dodane lub usunięte ze wszystkich ciągów, w zależności od wartości *bbWybierz*.

*bbWybierz*<br/>
Określa sposób ustawiania zaznaczenia. Jeśli *bbWybierz* ma wartość PRAWDA, ciąg jest zaznaczone i wyróżnione; w przypadku wartości FAŁSZ Podświetlenie jest usuwany, a ciąg nie jest zaznaczone. Określony ciąg jest zaznaczone i wyróżnione domyślnie.

### <a name="return-value"></a>Wartość zwracana

LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji elementu członkowskiego tylko z polami listy wielokrotnego wyboru.

Aby wybrać element z pola listy z pojedynczym wyborem, użyj [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>  CListBox::SetTabStops

Ustawienie pozycji tabulatorów w polu listy.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parametry

*cxEachStop*<br/>
Tabulatorów są ustawione na poziomie co *cxEachStop* jednostki okna dialogowego. Zobacz *rgTabStops* opis jednostki okna dialogowego.

*nTabStops*<br/>
Określa liczbę pozycji tabulatorów w polu listy.

*rgTabStops*<br/>
Wskazuje pierwszego elementu członkowskiego tablicy liczb całkowitych, zawierający pozycji tabulatorów w jednostkach okna dialogowego. Do okna dialogowego jest odległość pozioma lub pionowa. Jednostki okna dialogowego w poziomie jest równy jednej czwartej bieżącej jednostki podstawowej szerokość okna dialogowego, a jedna jednostka w pionie okno dialogowe jest równa jednej ósmej bieżącej jednostki podstawowej wysokość okna dialogowego. Okno dialogowe stanowiącej są obliczane na podstawie wysokość i szerokość bieżącej czcionki systemowej. `GetDialogBaseUnits` Windows funkcja zwraca bieżące okno dialogowe stanowiącej w pikselach. Pozycji tabulatorów muszą być posortowane rosnąco; Tabulatory wsteczne są niedozwolone.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wybrano ustawienia wszystkich kart; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby ustawienie pozycji tabulatorów na domyślny rozmiar 2 jednostki okna dialogowego, należy wywołać bez parametrów wersja tej funkcji elementu członkowskiego. Aby ustawienie pozycji tabulatorów rozmiar niż 2, należy wywołać wersja, która *cxEachStop* argumentu.

Aby ustawienie pozycji tabulatorów tablicę rozmiarów, należy użyć wersji za pomocą *rgTabStops* i *nTabStops* argumentów. Tabulator zostanie ustawiona dla każdej wartości w *rgTabStops*, maksymalna liczba określona przez *nTabStops*.

Aby odpowiedzieć na wywołanie `SetTabStops` funkcja elementu członkowskiego w polu listy muszą zostać utworzone za pomocą [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

Zapewnia, że element określonego pola listy jest widoczna.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu pola listy.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie, lub LB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

System Przewija pola listy, aż do elementu określonego przez *nIndex* pojawia się w górnej części listy pola lub zakresu maksymalnego przewijania zostanie osiągnięty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

Wywoływane przez platformę, gdy okno nadrzędne pola listy otrzymuje komunikat WM_VKEYTOITEM z listy rozwijanej.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nKey*<br/>
Użytkownik wirtualny kod klawisza klawisz naciśnięty klawisz. Aby uzyskać listę standardowa wirtualnej kody klawiszy Zobacz Winuser.h

*nIndex*<br/>
Bieżące położenie karetki pola listy.

### <a name="return-value"></a>Wartość zwracana

Zwraca - 2, żadne dodatkowe działania, - 1 dla domyślnej akcji lub nieujemna liczba, aby określić indeks elementu do pola listy, na którym należy wykonać domyślną akcję dla naciśnięcia klawisza.

### <a name="remarks"></a>Uwagi

Komunikat WM_VKEYTOITEM są wysyłane przez pola listy, po odebraniu przetłumaczyła komunikat, ale tylko wtedy, gdy pole listy spełnia z następującymi czynnościami:

- Ma [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu zestawu.

- Ma co najmniej jeden element.

Możesz nigdy nie powinien wywoływać tę funkcję samodzielnie. Należy przesłonić tę funkcję, aby zapewnić własną niestandardową obsługę komunikatów klawiatury.

Musi zwracać wartość, aby poinformować szablon, jaką akcję wykonać przesłonięcia. Zwracana wartość wynosząca - 2 wskazuje, że aplikacja obsługi wszystkich aspektów zaznaczenie elementu i wymaga żadne dalsze działania, w polu listy. Przed zwróceniem - 2, można ustawić zaznaczenie lub Przenieś karetkę i / lub. Aby ustawić zaznaczenie, należy użyć [setcursel —](#setcursel) lub [SetSel](#setsel). Aby przenieść karetki, należy użyć [SetCaretIndex](#setcaretindex).

Zwracana wartość - 1 wskazuje, że pole listy, należy wykonać domyślnej akcji w odpowiedzi na naciśnięcie klawisza. Domyślna implementacja zwraca - 1.

Zwracana wartość wynosząca 0 lub większy Określa indeks elementu w polu listy i wskazuje, że pole listy należy wykonywać domyślną akcję dla naciśnięcia klawisza dla danego elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)
