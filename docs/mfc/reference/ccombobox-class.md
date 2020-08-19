---
title: Klasa CComboBox
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: 79bcb973046c418f0bea148084da239075414790
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561677"
---
# <a name="ccombobox-class"></a>Klasa CComboBox

Oferuje funkcje pola kombi systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComboBox : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Konstruuje `CComboBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBox:: AddString](#addstring)|Dodaje ciąg do końca listy w polu listy pola kombi lub w sortowanej pozycji pól listy z stylem CBS_SORT.|
|[CComboBox:: Clear](#clear)|Usuwa (czyści) bieżące zaznaczenie, jeśli istnieje, w kontrolce Edycja.|
|[CComboBox::CompareItem](#compareitem)|Wywoływane przez platformę, by określić względne położenie nowego elementu listy w posortowanym polu kombi rysowanym przez właściciela.|
|[CComboBox:: Copy](#copy)|Kopiuje bieżące zaznaczenie, jeśli istnieje, do Schowka w formacie CF_TEXT.|
|[CComboBox:: Create](#create)|Tworzy pole kombi i dołącza je do `CComboBox` obiektu.|
|[CComboBox:: Wytnij](#cut)|Usuwa (wycina) bieżące zaznaczenie, jeśli istnieje, w kontrolce Edycja i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.|
|[CComboBox::D eleteItem](#deleteitem)|Wywoływane przez platformę, gdy element listy zostanie usunięty z pola kombi rysowanego przez właściciela.|
|[CComboBox::D eleteString](#deletestring)|Usuwa ciąg z pola listy pola kombi.|
|[CComboBox::D IR](#dir)|Dodaje listę nazw plików do pola listy pola kombi.|
|[CComboBox::D rawItem](#drawitem)|Wywoływane przez platformę, gdy wizualny aspekt pola kombi rysowanego przez właściciela jest zmieniany.|
|[CComboBox:: FindStr](#findstring)|Znajduje pierwszy ciąg, który zawiera określony prefiks w polu listy pola kombi.|
|[CComboBox::FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pola listy (w polu kombi), który pasuje do określonego ciągu.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Pobiera informacje o `CComboBox` obiekcie.|
|[CComboBox:: GetCount](#getcount)|Pobiera liczbę elementów w polu listy pola kombi.|
|[CComboBox::GetCueBanner](#getcuebanner)|Pobiera tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.|
|[CComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie wybranego elementu, jeśli istnieje, w polu listy pola kombi.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Pobiera Współrzędne ekranu widocznego (porzuconego) pola listy rozwijanej pola kombi.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Określa, czy pole listy rozwijanej pola kombi jest widoczne (usunięte w dół).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Pobiera minimalną dozwoloną szerokość części pola kombi pola listy rozwijanej.|
|[CComboBox::GetEditSel](#geteditsel)|Pobiera początkową i końcową pozycję znaku bieżącego zaznaczenia w kontrolce edycji pola kombi.|
|[CComboBox::GetExtendedUI](#getextendedui)|Określa, czy pole kombi ma domyślny interfejs użytkownika, czy rozszerzony interfejs użytkownika.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość (w pikselach), którą część pola listy pola kombi można przewijać w poziomie.|
|[CComboBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitowej dostarczonej przez aplikację skojarzoną z określonym elementem pola kombi.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Pobiera wskaźnik 32-bitowy dostarczonej przez aplikację, który jest skojarzony z określonym elementem pola kombi.|
|[CComboBox::GetItemHeight](#getitemheight)|Pobiera wysokość elementów listy w polu kombi.|
|[CComboBox::GetLBText](#getlbtext)|Pobiera ciąg z pola listy pola kombi.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Pobiera długość ciągu w polu listy pola kombi.|
|[CComboBox:: getLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola kombi.|
|[CComboBox::GetMinVisible](#getminvisible)|Pobiera minimalną liczbę widocznych elementów z listy rozwijanej bieżącego pola kombi.|
|[CComboBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego widocznego elementu w części pola kombi.|
|[CComboBox::InitStorage](#initstorage)|Wstępnie przydzieli bloki pamięci dla elementów i ciągów w części pola kombi.|
|[CComboBox::InsertString](#insertstring)|Wstawia ciąg do pola listy pola kombi.|
|[CComboBox::LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić do kontrolki edycji pola kombi.|
|[CComboBox::MeasureItem](#measureitem)|Wywoływane przez platformę, by określić wymiary pola kombi po utworzeniu pola kombi rysowanego przez właściciela.|
|[CComboBox::P Kopiuj](#paste)|Wstawia dane ze schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.|
|[CComboBox::ResetContent](#resetcontent)|Usuwa wszystkie elementy z pola listy i kontrolki edycji pola kombi.|
|[CComboBox::SelectString](#selectstring)|Wyszukuje ciąg w polu listy pola kombi i, jeśli ciąg zostanie znaleziony, wybiera ciąg w polu listy i kopiuje ciąg do kontrolki edycji.|
|[CComboBox::SetCueBanner](#setcuebanner)|Ustawia tekst kontrolny wyświetlany dla kontrolki pola kombi.|
|[CComboBox::SetCurSel](#setcursel)|Wybiera ciąg w polu listy pola kombi.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Ustawia minimalną dozwoloną szerokość części pola kombi pola listy rozwijanej.|
|[CComboBox::SetEditSel](#seteditsel)|Wybiera znaki w kontrolce edycji pola kombi.|
|[CComboBox::SetExtendedUI](#setextendedui)|Wybiera domyślny interfejs użytkownika lub rozszerzony interfejs użytkownika dla pola kombi, które ma styl CBS_DROPDOWN lub CBS_DROPDOWNLIST.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Ustawia szerokość (w pikselach), którą część pola listy pola kombi można przewijać w poziomie.|
|[CComboBox::SetItemData](#setitemdata)|Ustawia wartość 32-bitową skojarzoną z określonym elementem w polu kombi.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik 32-bitowy skojarzony z określonym elementem w polu kombi.|
|[CComboBox::SetItemHeight](#setitemheight)|Ustawia wysokość elementów listy w polu kombi lub wysokość części kontrolki edycji (lub statycznego tekstu) pola kombi.|
|[CComboBox:: setlocale](#setlocale)|Ustawia identyfikator ustawień regionalnych dla pola kombi.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącego pola kombi.|
|[CComboBox::SetTopIndex](#settopindex)|Informuje część pola kombi, aby wyświetlić element z określonym indeksem u góry.|
|[CComboBox::ShowDropDown](#showdropdown)|Pokazuje lub ukrywa pole listy pola kombi, które ma styl CBS_DROPDOWN lub CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Uwagi

Pole kombi składa się z pola listy połączonego z kontrolką statyczną lub kontrolką edycji. Część pola listy kontrolki może być wyświetlana przez cały czas lub można ją usunąć tylko wtedy, gdy użytkownik wybierze strzałkę listy rozwijanej obok formantu.

Aktualnie wybrany element (jeśli istnieje) w polu listy jest wyświetlany w kontrolce statycznej lub edycji. Ponadto, jeśli pole kombi ma styl listy rozwijanej, użytkownik może wpisać początkowy znak jednego z elementów na liście, a pole listy, jeśli jest widoczne, spowoduje wyróżnienie następnego elementu z tym znakiem początkowym.

W poniższej tabeli porównano trzy [Style](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)pola kombi.

|Styl|Gdy pole listy jest widoczne|Kontrolka statyczna lub edytuj|
|-----------|-------------------------------|-----------------------------|
|Prostota|Zawsze|Edytuj|
|Lista rozwijana|Po upuszczeniu|Edytuj|
|Lista rozwijana|Po upuszczeniu|Statyczny|

Można utworzyć `CComboBox` obiekt z poziomu szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach najpierw Wywołaj konstruktora `CComboBox` w celu skonstruowania `CComboBox` obiektu, a następnie wywołaj funkcję [tworzenia](#create) elementu członkowskiego, aby utworzyć formant i dołączyć go do `CComboBox` obiektu.

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows wysyłane przez pole kombi do jego elementu nadrzędnego (zazwyczaj klasy pochodnej `CDialog` ), Dodaj wpis mapy komunikatów i funkcję elementu członkowskiego obsługi komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów przyjmuje następującą formę:

`ON_Notification( id, memberFxn )`

gdzie `id` określa identyfikator okna podrzędnego kontrolki pola kombi wysyłającej powiadomienie i `memberFxn` jest nazwą nadrzędnej funkcji członkowskiej, która została zapisywana w celu obsługi powiadomienia.

Prototyp funkcji elementu nadrzędnego jest następujący:

`afx_msg void memberFxn( );`

Nie można przewidzieć kolejności, w której wysyłane są pewne powiadomienia. W szczególności powiadomienie CBN_SELCHANGE może odbywać się przed lub po CBN_CLOSEUP powiadomienia.

Możliwe są następujące wpisy mapy komunikatów:

- ON_CBN_CLOSEUP (system Windows 3,1 i nowsze). Pole listy pola kombi zostało zamknięte. Ten komunikat powiadomienia nie jest wysyłany dla pola kombi, które ma styl [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- ON_CBN_DBLCLK użytkownik kliknie dwukrotnie ciąg w polu listy pola kombi. Ten komunikat powiadomienia jest wysyłany tylko dla pola kombi z stylem CBS_SIMPLE. W przypadku pola kombi z stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) dwukrotne kliknięcie nie może wystąpić, ponieważ pojedyncze kliknięcie ukrywa pole listy.

- ON_CBN_DROPDOWN pole listy rozwijanej zostanie rozwiązane (być widoczne). Ten komunikat powiadomienia może wystąpić tylko w przypadku pola kombi z stylem CBS_DROPDOWN lub CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE użytkownik podjął akcję, która mogła zmienić tekst w części kontrolki edycji pola kombi. W przeciwieństwie do komunikatu CBN_EDITUPDATE, ten komunikat jest wysyłany po zaktualizowaniu ekranu przez system Windows. Nie jest wysyłane, jeśli pole kombi ma styl CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE część kontrolki Edycja pola kombi ma wyświetlać zmieniony tekst. Ten komunikat powiadomienia jest wysyłany po sformatowaniu przez kontrolkę tekstu, ale przed wyświetleniem tekstu. Nie jest wysyłane, jeśli pole kombi ma styl CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE pole kombi nie może przydzielić wystarczającej ilości pamięci do spełnienia określonego żądania.

- ON_CBN_SELENDCANCEL (system Windows 3,1 i nowsze). Wskazuje, że wybór użytkownika powinien zostać anulowany. Użytkownik klika element, a następnie klika okno lub kontrolkę, aby ukryć pole listy pola kombi. Ten komunikat powiadomienia jest wysyłany przed komunikatem powiadomienia o CBN_CLOSEUP, aby wskazać, że wybór użytkownika powinien zostać zignorowany. Wiadomość powiadomienia CBN_SELENDCANCEL lub CBN_SELENDOK jest wysyłana nawet wtedy, gdy wiadomość z powiadomieniem CBN_CLOSEUP nie jest wysyłana (podobnie jak w przypadku pola kombi ze stylem CBS_SIMPLE).

- ON_CBN_SELENDOK Wybieranie elementu przez użytkownika, a następnie naciśnięcie klawisza ENTER lub kliknięcia klawisza Strzałka w dół, aby ukryć pole listy pola kombi. Ten komunikat powiadomienia jest wysyłany przed komunikatem CBN_CLOSEUP, aby wskazać, że wybór użytkownika powinien być uznawany za ważny. Wiadomość powiadomienia CBN_SELENDCANCEL lub CBN_SELENDOK jest wysyłana nawet wtedy, gdy wiadomość z powiadomieniem CBN_CLOSEUP nie jest wysyłana (podobnie jak w przypadku pola kombi ze stylem CBS_SIMPLE).

- ON_CBN_KILLFOCUS pole kombi utraci fokus wprowadzania.

- ON_CBN_SELCHANGE wybór w polu listy kombi zostanie zmieniony w wyniku kliknięcia przycisku w polu listy lub zmiany zaznaczenia przy użyciu klawiszy strzałek w programie. Podczas przetwarzania tego komunikatu tekst w kontrolce edycji pola kombi można pobrać tylko przez `GetLBText` lub inną podobną funkcję. `GetWindowText` nie można użyć.

- ON_CBN_SETFOCUS pole kombi odbiera fokus wprowadzania.

Jeśli utworzysz `CComboBox` obiekt w oknie dialogowym (za pomocą zasobu okna dialogowego), `CComboBox` obiekt zostanie automatycznie zniszczony, gdy użytkownik zamknie okno dialogowe.

Jeśli obiekt zostanie osadzony `CComboBox` w innym obiekcie okna, nie trzeba go zniszczyć. Jeśli utworzysz `CComboBox` obiekt na stosie, zostanie on zniszczony automatycznie. Jeśli obiekt jest tworzony `CComboBox` na stercie przy użyciu **`new`** funkcji, należy wywołać **`delete`** obiekt, aby zniszczyć go, gdy pole kombi systemu Windows zostanie zniszczone.

**Uwaga** Aby obsłużyć WM_KEYDOWN i WM_CHAR komunikatów, należy utworzyć podklasę formantów pola kombi i pola listy, utworzyć klasy z `CEdit` i `CListBox` i dodać procedury obsługi dla tych komunikatów do klas pochodnych. Aby uzyskać więcej informacji, zobacz [CWnd:: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a> CComboBox:: AddString

Dodaje ciąg do pola listy pola kombi.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa lub równa 0, jest indeksem liczonym od zera do ciągu w polu listy. Wartość zwracana jest CB_ERR w przypadku wystąpienia błędu; wartość zwracana jest CB_ERRSPACE, jeśli jest za mało miejsca, aby można było zapisać nowy ciąg.

### <a name="remarks"></a>Uwagi

Jeśli pole listy nie zostało utworzone za pomocą stylu [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , ciąg zostanie dodany na końcu listy. W przeciwnym razie ciąg zostanie wstawiony do listy, a lista jest posortowana.

> [!NOTE]
> Ta funkcja nie jest obsługiwana przez formant systemu Windows `ComboBoxEx` . Aby uzyskać więcej informacji na temat tej kontrolki, zobacz [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) w Windows SDK.

Aby wstawić ciąg do określonej lokalizacji na liście, użyj funkcji składowej [InsertString](#insertstring) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a> CComboBox::CComboBox

Konstruuje `CComboBox` obiekt.

```
CComboBox();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a> CComboBox:: Clear

Usuwa (czyści) bieżące zaznaczenie, jeśli istnieje, w kontrolce Edycja pola kombi.

```cpp
void Clear();
```

### <a name="remarks"></a>Uwagi

Aby usunąć bieżące zaznaczenie i umieścić zawartość w schowku, użyj funkcji [Wytnij](#cut) element członkowski.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a> CComboBox::CompareItem

Wywoływane przez platformę, by określić względne położenie nowego elementu w części pole listy posortowanego pola kombi rysowania przez właściciela.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Długi wskaźnik do struktury [COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct) .

### <a name="return-value"></a>Wartość zwracana

Wskazuje względne położenie dwóch elementów opisanych w `COMPAREITEMSTRUCT` strukturze. Może to być dowolna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|-1|Element 1 sortuje przed elementem 2.|
|0|Element 1 i element 2 sortują te same.|
|1|Element 1 sortuje po elemencie 2.|

Aby uzyskać opis, zobacz [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) `COMPAREITEMSTRUCT` .

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja członkowska nic nie robi. Jeśli utworzysz pole kombi rysowania przez właściciela z stylem LBS_SORT, musisz zastąpić tę funkcję elementu członkowskiego, aby pomóc w strukturze sortowania nowych elementów dodanych do pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a> CComboBox:: Copy

Kopiuje bieżące zaznaczenie, jeśli istnieje, w kontrolce Edycja pola kombi do Schowka w formacie CF_TEXT.

```cpp
void Copy();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a> CComboBox:: Create

Tworzy pole kombi i dołącza je do `CComboBox` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola kombi. Zastosuj dowolną kombinację [stylów pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) do pola.

*cinania*<br/>
Wskazuje położenie i rozmiar pola kombi. Może to być [Struktura](/windows/win32/api/windef/ns-windef-rect) lub `CRect` obiekt.

*pParentWnd*<br/>
Określa okno nadrzędne (zwykle a `CDialog` ). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki pola kombi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany `CComboBox` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create` , który tworzy pole kombi systemu Windows i dołącza go do `CComboBox` obiektu.

Gdy `Create` jest wykonywane, system Windows wysyła wiadomości [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do pola kombi.

Te komunikaty są domyślnie obsługiwane przez funkcje elementu członkowskiego [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) w `CWnd` klasie bazowej. Aby zwiększyć domyślną obsługę komunikatów, należy utworzyć klasę z `CComboBox` , dodać mapę komunikatów do nowej klasy i zastąpić poprzednią funkcję elementu członkowskiego programu obsługi komunikatów. Przesłoń `OnCreate` , na przykład, aby wykonać wymaganą inicjalizację dla nowej klasy.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pole kombi. :

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL, aby dodać przewijanie w pionie dla pola listy w polu kombi

- WS_HSCROLL, aby dodać przewijanie w poziomie pola listy w polu kombi

- WS_GROUP do grup formantów

- WS_TABSTOP uwzględnić pola kombi w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a> CComboBox:: Wytnij

Usuwa (wycina) bieżące zaznaczenie, jeśli istnieje, w kontrolce Edycja pola kombi i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Uwagi

Aby usunąć bieżące zaznaczenie bez umieszczania w schowku usuniętego tekstu, wywołaj funkcję [czyszczenia](#clear) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a> CComboBox::D eleteItem

Wywoływane przez platformę, gdy użytkownik usuwa element z obiektu rysowania przez właściciela `CComboBox` lub niszczy pole kombi.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Długi wskaźnik do struktury [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) systemu Windows, który zawiera informacje o usuniętym elemencie. Aby uzyskać opis tej struktury, zobacz [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) .

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji nic nie robi. Zastąp tę funkcję, aby ponownie narysować pole kombi zgodnie z wymaganiami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a> CComboBox::D eleteString

Usuwa element z pozycji *nIndex* w polu kombi.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks ciągu, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa lub równa 0, jest to liczba ciągów pozostałych na liście. Wartość zwracana jest CB_ERR, jeśli *nIndex* Określa indeks większy niż liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wszystkie elementy po *nIndex* teraz przechodzą w dół o jedno miejsce. Na przykład, jeśli pole kombi zawiera dwa elementy, usunięcie pierwszego elementu spowoduje, że pozostały element zostanie teraz w pierwszej pozycji. *nIndex*= 0 dla elementu w pierwszej pozycji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a> CComboBox::D IR

Dodaje listę nazw plików lub dysków do pola listy pola kombi.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*atrybut*<br/>
Może być dowolną kombinacją **`enum`** wartości opisanych w [CFile:: GetStatus](../../mfc/reference/cfile-class.md#getstatus) lub dowolnej kombinacji następujących wartości:

- Plik DDL_READWRITE może być odczytywany lub zapisywana.

- Plik DDL_READONLY może zostać odczytany z, ale nie do zapisu.

- Plik DDL_HIDDEN jest ukryty i nie znajduje się na liście katalogów.

- Plik DDL_SYSTEM jest plikiem systemowym.

- DDL_DIRECTORY nazwa określona przez *lpszWildCard* określa katalog.

- Plik DDL_ARCHIVE został zarchiwizowany.

- DDL_DRIVES uwzględnić wszystkie dyski, które pasują do nazwy określonej przez *lpszWildCard*.

- DDL_EXCLUSIVE flagi wyłączności. Jeśli ustawiono flagę wyłączną, wyświetlane są tylko pliki określonego typu. W przeciwnym razie pliki określonego typu są wymienione jako uzupełnienie plików "normal".

*lpszWildCard*<br/>
Wskazuje ciąg specyfikacji pliku. Ciąg może zawierać symbole wieloznaczne (na przykład *. \* ).

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa lub równa 0, jest indeksem liczonym od zera ostatniej nazwy pliku dodany do listy. Wartość zwracana jest CB_ERR w przypadku wystąpienia błędu; wartość zwracana jest CB_ERRSPACE, jeśli jest za mało miejsca, aby można było przechowywać nowe ciągi.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana przez formant systemu Windows `ComboBoxEx` . Aby uzyskać więcej informacji na temat tej kontrolki, zobacz [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a> CComboBox::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt pola kombi rysowania przez właściciela zmienia się.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , który zawiera informacje o wymaganym typie rysunku.

### <a name="remarks"></a>Uwagi

`itemAction`Element członkowski `DRAWITEMSTRUCT` struktury definiuje akcję rysowania, która ma zostać wykonana. Aby uzyskać opis tej struktury, zobacz [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) .

Domyślnie ta funkcja członkowska nic nie robi. Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie dla obiektu rysowania przez właściciela `CComboBox` . Przed zakończeniem tej funkcji elementu członkowskiego aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania podanego w *lpDrawItemStruct*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a> CComboBox:: FindStr

Znajduje, ale nie zaznacz, pierwszy ciąg, który zawiera określony prefiks w polu listy pola kombi.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli-1, całe pole listy jest przeszukiwane od początku.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od wielkości liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa lub równa 0, jest indeksem liczonym od zera pasującego elementu. Jest CB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana przez formant systemu Windows `ComboBoxEx` . Aby uzyskać więcej informacji na temat tej kontrolki, zobacz [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a> CComboBox::FindStringExact

Wywołaj `FindStringExact` funkcję członkowską, aby znaleźć pierwszy ciąg pola listy (w polu kombi), który pasuje do ciągu określonego w *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Określa indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nIndexStart*. Jeśli *nIndexStart* to-1, całe pole listy jest przeszukiwane od początku.

*lpszFind*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać wyszukany. Ten ciąg może zawierać pełną nazwę pliku, łącznie z rozszerzeniem. W wyszukiwaniu nie jest rozróżniana wielkość liter, dlatego ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pasującego elementu lub CB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli pole kombi zostało utworzone przy użyciu stylu rysowania przez właściciela, ale bez stylu [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , program `FindStringExact` próbuje dopasować wartość DoubleWord do wartości *lpszFind*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a> CComboBox::GetComboBoxInfo

Pobiera informacje dla `CComboBox` obiektu.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parametry

*pcbi*<br/>
Wskaźnik do struktury [COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo) .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) , zgodnie z opisem w Windows SDK.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a> CComboBox:: GetCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę elementów w części pola kombi.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów. Zwracana liczba jest większa niż wartość indeksu ostatniego elementu (indeks jest liczony od zera). CB_ERR w przypadku wystąpienia błędu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a> CComboBox::GetCueBanner

Pobiera tekst wskaźnika, który jest wyświetlany dla kontrolki pola kombi.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*\
określoną Wskaźnik do buforu, który odbiera tekst banera wskaźnika.

*cchText*\
podczas Rozmiar buforu, na który wskazuje parametr *lpszText* .

### <a name="return-value"></a>Wartość zwracana

W pierwszym przeciążeniu obiekt [CString](../../atl-mfc-shared/using-cstring.md) , który zawiera tekst banera wskaźnika, jeśli istnieje; w przeciwnym razie `CString` obiekt o zerowej długości.

-lub-

W drugim przeciążeniu, wartość TRUE, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tekst podpowiedzi jest monitem, który jest wyświetlany w obszarze wejściowym kontrolki pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik nie poda danych wejściowych.

Ta metoda wysyła komunikat [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) , który jest opisany w Windows SDK.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a> CComboBox::GetCurSel

Wywołaj tę funkcję elementu członkowskiego, aby określić, który element w polu kombi jest zaznaczony.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) aktualnie zaznaczonego elementu w polu listy pola kombi lub CB_ERR, jeśli nie wybrano żadnego elementu.

### <a name="remarks"></a>Uwagi

`GetCurSel` zwraca indeks do listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a> CComboBox::GetDroppedControlRect

Wywołaj `GetDroppedControlRect` funkcję członkowską, aby pobrać Współrzędne ekranu widocznego (porzuconego) pola listy rozwijanej pola kombi.

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parametry

*lprect*<br/>
Wskazuje [strukturę Rect](/windows/win32/api/windef/ns-windef-rect) , która ma otrzymywać współrzędne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a> CComboBox::GetDroppedState

Wywołaj `GetDroppedState` funkcję członkowską, aby określić, czy pole listy rozwijanej pola kombi jest widoczne (opuszczone).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli pole listy jest widoczne; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a> CComboBox::GetDroppedWidth

Wywołaj tę funkcję, aby pobrać minimalną dozwoloną Szerokość (w pikselach) pola listy pola kombi.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, minimalna dozwolona Szerokość (w pikselach). w przeciwnym razie CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja ma zastosowanie tylko do pól kombi z stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Domyślnie minimalna dozwolona szerokość pola listy rozwijanej to 0. Minimalną dozwoloną Szerokość można ustawić, wywołując [SetDroppedWidth](#setdroppedwidth). Gdy zostanie wyświetlona część pola listy kombi, jej szerokość jest większa niż minimalna dozwolona szerokość lub szerokość pola kombi.

### <a name="example"></a>Przykład

  Zobacz przykład dla [SetDroppedWidth](#setdroppedwidth).

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a> CComboBox::GetEditSel

Pobiera początkową i końcową pozycję znaku bieżącego zaznaczenia w kontrolce edycji pola kombi.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość 32-bitowa, która zawiera pozycję początkową w wyrazie z małą kolejnością i położenie pierwszego niezaznaczonego znaku po zakończeniu zaznaczania w wyrazie o wysokiej kolejności. Jeśli ta funkcja jest używana w polu kombi bez kontrolki edycji, CB_ERR jest zwracana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a> CComboBox::GetExtendedUI

Wywołaj `GetExtendedUI` funkcję członkowską, aby określić, czy pole kombi ma domyślny interfejs użytkownika, czy rozszerzony interfejs użytkownika.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli pole kombi ma rozszerzony interfejs użytkownika; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Rozszerzony interfejs użytkownika można zidentyfikować w następujący sposób:

- Kliknięcie statycznej kontrolki powoduje wyświetlenie pola listy tylko dla pól kombi z stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- Naciśnięcie klawisza Strzałka w dół powoduje wyświetlenie pola listy (F4 jest wyłączone).

Przewijanie w kontrolce statycznej jest wyłączone, gdy lista elementów nie jest widoczna (klawisze strzałek są wyłączone).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a> CComboBox::GetHorizontalExtent

Pobiera z pola kombi Szerokość (w pikselach), o jaką część pola listy pola kombi można przewijać w poziomie.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Wartość zwracana

Szerokość pola listy pola kombi przewijalnego w pikselach.

### <a name="remarks"></a>Uwagi

Ma to zastosowanie tylko wtedy, gdy część pola listy pola kombi ma poziomy pasek przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a> CComboBox::GetItemData

Pobiera wartość 32-bitowej dostarczonej przez aplikację skojarzoną z określonym elementem pola kombi.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) elementu w polu listy pola kombi.

### <a name="return-value"></a>Wartość zwracana

32-bitowa wartość skojarzona z elementem lub CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Wartość 32-bitowej można ustawić za pomocą parametru *dwItemData* wywołania funkcji składowej [SetItemData](#setitemdata) . Użyj `GetItemDataPtr` funkcji członkowskiej, jeśli wartość 32-bitowa do pobrania jest wskaźnikiem ( **`void`** <strong>\*</strong> ).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a> CComboBox::GetItemDataPtr

Pobiera wartość 32-bitowej dostarczonej przez aplikację skojarzoną z określonym elementem pola kombi jako wskaźnikiem ( **`void`** <strong>\*</strong> ).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) elementu w polu listy pola kombi.

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik lub-1, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a> CComboBox::GetItemHeight

Wywołaj `GetItemHeight` funkcję członkowską, aby pobrać wysokość elementów listy w polu kombi.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa składnik pola kombi, którego wysokość ma zostać pobrana. Jeśli parametr *nIndex* ma wartość-1, pobierana jest wysokość części kontrolki edycji (lub statycznego tekstu) pola kombi. Jeśli pole kombi ma styl [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *nIndex* Określa indeks (liczony od zera) elementu listy, którego wysokość ma zostać pobrana. W przeciwnym razie *nIndex* powinna być ustawiona na 0.

### <a name="return-value"></a>Wartość zwracana

Wysokość (w pikselach) określonego elementu w polu kombi. Wartość zwracana jest CB_ERR w przypadku wystąpienia błędu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a> CComboBox::GetLBText

Pobiera ciąg z pola listy pola kombi.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) ciągu pola listy do skopiowania.

*lpszText*<br/>
Wskazuje bufor, który ma otrzymać ciąg. Bufor musi mieć wystarczającą ilość miejsca dla ciągu i kończącego znaku null.

*rString*<br/>
Odwołanie do `CString` .

### <a name="return-value"></a>Wartość zwracana

Długość (w bajtach) ciągu, z wyłączeniem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest CB_ERR.

### <a name="remarks"></a>Uwagi

Druga forma tej funkcji elementu członkowskiego wypełnia `CString` obiekt z tekstem elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a> CComboBox::GetLBTextLen

Pobiera długość ciągu w polu listy pola kombi.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) ciągu z polem listy.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w bajtach, z wyłączeniem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowego indeksu, wartość zwracana jest CB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CComboBox:: GetLBText](#getlbtext).

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a> CComboBox:: getLocale

Pobiera ustawienia regionalne używane przez pole kombi.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość identyfikatora ustawień regionalnych (LCID) dla ciągów w polu kombi.

### <a name="remarks"></a>Uwagi

Ustawienia regionalne są używane na przykład w celu określenia kolejności sortowania ciągów w posortowanym polu kombi.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CComboBox:: Setlocals](#setlocale).

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a> CComboBox::GetMinVisible

Pobiera minimalną liczbę widocznych elementów z listy rozwijanej bieżącej kontrolki pola kombi.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna liczba widocznych elementów na bieżącej liście rozwijanej.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , który jest opisany w Windows SDK.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a> CComboBox::GetTopIndex

Pobiera indeks (liczony od zera) pierwszego widocznego elementu w części pola kombi.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pierwszego widocznego elementu w części pole kombi w przypadku powodzenia, CB_ERR w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Początkowo element 0 znajduje się u góry pola listy, ale jeśli pole listy jest przewijane, inny element może znajdować się u góry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a> CComboBox::InitStorage

Przydziela pamięć do przechowywania elementów pola listy w części pola kombi.

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

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, Maksymalna liczba elementów w polu kombi może być przechowywana przed ponownym alokacją pamięci, w przeciwnym razie CB_ERRSPACE, co oznacza, że nie jest dostępna wystarczająca ilość pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję przed dodaniem dużej liczby elementów do części pole listy `CComboBox` .

Tylko system Windows 95/98: parametr *wParam* jest ograniczony do wartości 16-bitowych. Oznacza to, że pola listy nie mogą zawierać więcej niż 32 767 elementów. Chociaż liczba elementów jest ograniczona, łączny rozmiar elementów w polu listy jest ograniczony tylko przez dostępną pamięć.

Ta funkcja pomaga przyspieszyć inicjalizację pól listy, które mają dużą liczbę elementów (więcej niż 100). Wstępnie przydzieli określoną ilość pamięci, aby kolejne funkcje [AddString](#addstring), [InsertString](#insertstring)i [dir](#dir) miały najkrótszy możliwy czas. Można użyć oszacowań dla parametrów. W przypadku nadmiernego oszacowania część dodatkowej pamięci zostanie przypisana; w przypadku podwyższania szacunku normalna alokacja jest używana dla elementów, które przekraczają wstępnie przydzieloną kwotę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a> CComboBox::InsertString

Wstawia ciąg do pola listy pola kombi.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) do pozycji w polu listy, która będzie odbierać ciąg. Jeśli ten parametr ma wartość-1, ciąg zostanie dodany na końcu listy.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pozycji, w której został wstawiony ciąg. Wartość zwracana jest CB_ERR w przypadku wystąpienia błędu. Wartość zwracana jest CB_ERRSPACE, jeśli jest za mało miejsca, aby można było zapisać nowy ciąg.

### <a name="remarks"></a>Uwagi

W przeciwieństwie do funkcji składowej [AddString](#addstring) , `InsertString` funkcja członkowska nie powoduje sortowania listy z stylem [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

> [!NOTE]
> Ta funkcja nie jest obsługiwana przez formant systemu Windows `ComboBoxEx` . Aby uzyskać więcej informacji na temat tej kontrolki, zobacz [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a> CComboBox::LimitText

Ogranicza długość w bajtach tekstu, który użytkownik może wprowadzić do kontrolki edycji pola kombi.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Określa długość (w bajtach) tekstu, który użytkownik może wprowadzić. Jeśli ten parametr ma wartość 0, długość tekstu jest ustawiona na 65 535 bajtów.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera. Jeśli wywoływana dla pola kombi z stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub pola kombi bez kontrolki edycji, wartość zwracana jest CB_ERR.

### <a name="remarks"></a>Uwagi

Jeśli pole kombi nie ma [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)stylu, ustawienie limitu tekstu na wartość większą niż rozmiar kontrolki edycji nie będzie miało żadnego efektu.

`LimitText` ogranicza tylko tekst, który użytkownik może wprowadzić. Nie ma ono wpływu na żaden tekst znajdujący się już w kontrolce edycji, gdy wiadomość jest wysyłana, ani nie ma wpływu na długość tekstu skopiowanego do kontrolki edycji, gdy zostanie wybrany ciąg w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a> CComboBox::MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony pole kombi z stylem rysowania przez właściciela.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długi wskaźnik do struktury [MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja członkowska nic nie robi. Zastąp tę funkcję członkowską i wypełnij `MEASUREITEMSTRUCT` strukturę, aby informować okna o wymiarach pola listy w polu kombi. Jeśli pole kombi jest tworzone z stylem [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski jest wywoływany tylko raz.

Użycie stylu CBS_OWNERDRAWFIXED w polu kombi rysowania przez właściciela utworzonego za pomocą funkcji składowej [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) w programie `CWnd` obejmuje dalsze zagadnienia związane z programowaniem. Zapoznaj się z dyskusjami w artykule [technicznym 14](../../mfc/tn014-custom-controls.md).

Opis struktury można znaleźć w temacie [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) `MEASUREITEMSTRUCT` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a> CComboBox::P Kopiuj

Wstawia dane ze schowka do kontrolki edycji pola kombi w bieżącym położeniu kursora.

```cpp
void Paste();
```

### <a name="remarks"></a>Uwagi

Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a> CComboBox::ResetContent

Usuwa wszystkie elementy z pola listy i kontrolki edycji pola kombi.

```cpp
void ResetContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a> CComboBox::SelectString

Wyszukuje ciąg w polu listy pola kombi, a jeśli ciąg zostanie znaleziony, wybiera ciąg w polu listy i kopiuje go do kontrolki edycji.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera indeks (liczony od zera) elementu przed pierwszym elementem do przeszukania. Gdy wyszukiwanie osiągnie dolny koniec pola listy, kontynuuje się z góry pola listy z powrotem do elementu określonego przez *nStartAfter*. Jeśli-1, całe pole listy jest przeszukiwane od początku.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne od wielkości liter, więc ten ciąg może zawierać dowolną kombinację wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) wybranego elementu, jeśli ciąg został znaleziony. Jeśli wyszukiwanie nie powiodło się, wartość zwracana jest CB_ERR i bieżące zaznaczenie nie zostanie zmienione.

### <a name="remarks"></a>Uwagi

Ciąg jest wybierany tylko wtedy, gdy jego początkowe znaki (od punktu początkowego) pasują do znaków w ciągu prefiksu.

Należy zauważyć, `SelectString` że `FindString` funkcje i są jednocześnie znajdować ciąg, ale `SelectString` funkcja członkowska również wybiera ten ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a> CComboBox::SetCueBanner

Ustawia tekst kontrolny wyświetlany dla kontrolki pola kombi.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*\
podczas Wskaźnik na bufor zakończony zerem, który zawiera tekst kontrolny.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończy się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Tekst podpowiedzi jest monitem, który jest wyświetlany w obszarze wejściowym kontrolki pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik nie poda danych wejściowych.

Ta metoda wysyła komunikat [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_combobox*, która jest używana do programistycznego dostępu do kontrolki pola kombi. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia transparent wskaźnika dla kontrolki pole kombi.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a> CComboBox::SetCurSel

Wybiera ciąg w polu listy pola kombi.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nWybierz*<br/>
Określa indeks (liczony od zera) ciągu do wybrania. Jeśli-1, wszelkie bieżące zaznaczenie w polu listy zostanie usunięte, a kontrolka edycji zostanie wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) elementu wybranego w przypadku pomyślnego zakończenia wiadomości. Wartość zwracana jest CB_ERR, jeśli *nWybierz* jest większa niż liczba elementów na liście lub jeśli *nWybierz* jest ustawiona na wartość-1, co czyści zaznaczenie.

### <a name="remarks"></a>Uwagi

W razie potrzeby pole listy przewija ciąg do widoku (Jeśli pole listy jest widoczne). Tekst w kontrolce edycji pola kombi zostanie zmieniony w celu odzwierciedlenia nowego zaznaczenia. Wszystkie poprzednie zaznaczenia w polu listy zostaną usunięte.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a> CComboBox::SetDroppedWidth

Wywołaj tę funkcję, aby ustawić minimalną dozwoloną Szerokość (w pikselach) pola listy pola kombi.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Minimalna dozwolona szerokość fragmentu pola listy pola kombi (w pikselach).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, Nowa szerokość pola listy, w przeciwnym razie CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja ma zastosowanie tylko do pól kombi z stylem [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

Domyślnie minimalna dozwolona szerokość pola listy rozwijanej to 0. Gdy zostanie wyświetlona część pola listy kombi, jej szerokość jest większa niż minimalna dozwolona szerokość lub szerokość pola kombi.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a> CComboBox::SetEditSel

Wybiera znaki w kontrolce edycji pola kombi.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Określa pozycję początkową. Jeśli pozycja początkowa ma wartość-1, wszystkie istniejące zaznaczenia zostaną usunięte.

*nEndChar*<br/>
Określa pozycję końcową. Jeśli pozycja końcowa jest ustawiona na wartość-1, zaznaczony jest cały tekst od pozycji początkowej do ostatniego znaku w kontrolce Edycja.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja członkowska zakończyła się powodzeniem; w przeciwnym razie 0. Jest CB_ERR, jeśli `CComboBox` ma styl [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub nie ma pola listy.

### <a name="remarks"></a>Uwagi

Położenie jest zależne od zera. Aby wybrać pierwszy znak kontrolki edycji, należy określić pozycję początkową 0. Pozycja końcowa jest dla znaku tuż po ostatnim znaku do wybrania. Na przykład, aby wybrać cztery pierwsze znaki kontrolki edycji, należy użyć pozycji początkowej 0 i pozycji końcowej 4.

> [!NOTE]
> Ta funkcja nie jest obsługiwana przez formant systemu Windows `ComboBoxEx` . Aby uzyskać więcej informacji na temat tej kontrolki, zobacz [ComboBoxEx Controls](/windows/win32/Controls/comboboxex-controls) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CComboBox:: GetEditSel](#geteditsel).

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a> CComboBox::SetExtendedUI

Wywołaj `SetExtendedUI` funkcję członkowską, aby wybrać domyślny interfejs użytkownika lub rozszerzony interfejs użytkownika dla pola kombi, które ma styl [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parametry

*bExtended*<br/>
Określa, czy pole kombi ma używać rozszerzonego interfejsu użytkownika czy domyślnego interfejsu użytkownika. Wartość TRUE powoduje wybranie rozszerzonego interfejsu użytkownika; wartość FALSE powoduje wybranie standardowego interfejsu użytkownika.

### <a name="return-value"></a>Wartość zwracana

CB_OKAY, jeśli operacja zakończyła się pomyślnie lub CB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Rozszerzony interfejs użytkownika można zidentyfikować w następujący sposób:

- Kliknięcie statycznej kontrolki powoduje wyświetlenie pola listy tylko dla pól kombi z stylem CBS_DROPDOWNLIST.

- Naciśnięcie klawisza Strzałka w dół powoduje wyświetlenie pola listy (F4 jest wyłączone).

Przewijanie w kontrolce statycznej jest wyłączone, gdy lista elementów nie jest widoczna (klawisze strzałek są wyłączone).

### <a name="example"></a>Przykład

  Zobacz przykład dla [CComboBox:: GetExtendedUI](#getextendedui).

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a> CComboBox::SetHorizontalExtent

Ustawia szerokość (w pikselach), przez jaką część pola listy pola kombi można przewijać w poziomie.

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parametry

*nExtent*<br/>
Określa liczbę pikseli, przez jaką część pola listy pola kombi można przewijać w poziomie.

### <a name="remarks"></a>Uwagi

Jeśli szerokość pola listy jest mniejsza niż ta wartość, poziomy pasek przewijania będzie przewinąć w poziomie elementy w polu listy. Jeśli szerokość pola listy jest równa lub większa niż ta wartość, poziomy pasek przewijania jest ukryty lub, jeśli pole kombi ma styl [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , wyłączone.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a> CComboBox::SetItemData

Ustawia wartość 32-bitową skojarzoną z określonym elementem w polu kombi.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) dla elementu, który ma zostać ustawiony.

*dwItemData*<br/>
Zawiera nową wartość do skojarzenia z elementem.

### <a name="return-value"></a>Wartość zwracana

CB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Użyj `SetItemDataPtr` funkcji członkowskiej, jeśli element 32-bitowy ma być wskaźnikiem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a> CComboBox::SetItemDataPtr

Ustawia wartość 32-bitową skojarzoną z określonym elementem w polu kombi na określony wskaźnik ( **`void`** <strong>\*</strong> ).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera indeks (liczony od zera) do elementu.

*pData*<br/>
Zawiera wskaźnik do skojarzenia z elementem.

### <a name="return-value"></a>Wartość zwracana

CB_ERR w przypadku wystąpienia błędu.

### <a name="remarks"></a>Uwagi

Ten wskaźnik pozostaje prawidłowy dla życia pola kombi, nawet jeśli względne położenie elementu wewnątrz pola kombi może ulec zmianie, gdy elementy są dodawane lub usuwane. W związku z tym indeks elementu w polu może ulec zmianie, ale wskaźnik pozostaje niezawodny.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a> CComboBox::SetItemHeight

Wywołaj `SetItemHeight` funkcję członkowską, aby ustawić wysokość elementów listy w polu kombi lub wysokość części kontrolki edycji (lub statycznego tekstu) pola kombi.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa, czy ustawiono wysokość elementu listy lub wysokość części kontrolki edycji (lub statycznego tekstu) pola kombi.

Jeśli pole kombi ma styl [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *nIndex* Określa indeks (liczony od zera) elementu listy, którego wysokość ma być ustawiona; w przeciwnym razie *nIndex* musi mieć wartość 0, a wysokość wszystkich elementów listy zostanie ustawiona.

Jeśli *nIndex* ma wartość-1, należy ustawić wysokość kontrolki edycji lub tekstu statycznego w polu kombi.

*cyItemHeight*<br/>
Określa wysokość (w pikselach) składnika pola kombi identyfikowanego przez *nIndex*.

### <a name="return-value"></a>Wartość zwracana

CB_ERR, jeśli indeks lub wysokość są nieprawidłowe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wysokość części kontrolki edycji (lub statycznego tekstu) pola kombi jest ustawiana niezależnie od wysokości elementów listy. Aplikacja musi zapewnić, że wysokość części kontrolki edycji (lub statycznego tekstu) nie jest mniejsza niż wysokość określonego elementu pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a> CComboBox:: setlocale

Ustawia identyfikator ustawień regionalnych dla tego pola kombi.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nowa wartość identyfikatora ustawień regionalnych (LCID) do ustawienia dla pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wartość poprzedniego identyfikatora ustawień regionalnych (LCID) dla tego pola kombi.

### <a name="remarks"></a>Uwagi

Jeśli `SetLocale` nie jest wywoływana, domyślne ustawienia regionalne są uzyskiwane z systemu. Domyślne ustawienia regionalne systemu można modyfikować za pomocą aplikacji regionalnej (lub międzynarodowej) panelu sterowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a> CComboBox::SetMinVisibleItems

Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącej kontrolki pola kombi.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parametry

*niewidoczny*\
podczas Określa minimalną liczbę widocznych elementów.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , który jest opisany w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje zmienną *m_combobox*, która jest używana do programistycznego dostępu do kontrolki pola kombi. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wstawia 20 elementów do listy rozwijanej kontrolki pola kombi. Następnie określa, że co najmniej 10 elementów będzie wyświetlany, gdy użytkownik naciśnie strzałkę listy rozwijanej.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a> CComboBox::SetTopIndex

Zapewnia, że określony element jest widoczny w części pola listy pola kombi.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks (liczony od zera) elementu listy.

### <a name="return-value"></a>Wartość zwracana

Zero jeśli kończy się pomyślnie lub CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

System przewija pole listy, dopóki element określony przez *nIndex* pojawia się u góry pola listy lub Osiągnięto maksymalny zakres przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a> CComboBox::ShowDropDown

Pokazuje lub ukrywa pole listy pola kombi, które ma styl [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowIt*<br/>
Określa, czy pole listy rozwijanej ma być widoczne czy ukryte. Wartość TRUE Wyświetla pole listy. Wartość FALSE powoduje ukrycie pola listy.

### <a name="remarks"></a>Uwagi

Domyślnie pole kombi tego stylu będzie zawierać pole listy.

Ta funkcja członkowska nie ma wpływu na pole kombi utworzone przy użyciu stylu [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

### <a name="example"></a>Przykład

  Zobacz przykład dla [CComboBox:: GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Zobacz też

[Przykład CTRLBARS MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
