---
title: Ccombobox — klasa
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
ms.openlocfilehash: e7472b808d8b5d743d884d9e3806df7ffe499836
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178782"
---
# <a name="ccombobox-class"></a>Ccombobox — klasa

Oferuje funkcje pola kombi Windows.

## <a name="syntax"></a>Składnia

```
class CComboBox : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Konstruuje `CComboBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Dodaje ciąg do końca listy w polu listy, pola kombi lub pozycja posortowanej listy pól ze stylem CBS_SORT.|
|[CComboBox::Clear](#clear)|Usuwa (czyści) bieżące zaznaczenie w formancie edycji.|
|[CComboBox::CompareItem](#compareitem)|Metoda wywoływana przez platformę, aby określić względne położenie nowy element listy w polu kombi rysowanych przez właściciela posortowany.|
|[CComboBox::Copy](#copy)|Kopiuje bieżącego zaznaczenia, jeśli do Schowka w formacie CF_TEXT.|
|[CComboBox::Create](#create)|Tworzy pola kombi i dołącza je do `CComboBox` obiektu.|
|[CComboBox::Cut](#cut)|Usuwa (kawałki) bieżącego zaznaczenia, jeśli istnieją, w trakcie edycji kontroli i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.|
|[CComboBox::DeleteItem](#deleteitem)|Wywoływane przez platformę, gdy element listy zostanie usunięty z pola kombi rysowanych przez właściciela.|
|[CComboBox::DeleteString](#deletestring)|Usuwa ciągiem z listy rozwijanej pola kombi.|
|[CComboBox::Dir](#dir)|Dodaje listę nazw plików, do pola listy, pola kombi.|
|[CComboBox::DrawItem](#drawitem)|Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany pola kombi rysowanych przez właściciela.|
|[CComboBox::FindString](#findstring)|Znajduje pierwszy ciąg, który zawiera określony prefiks w polu listy, pola kombi.|
|[CComboBox::FindStringExact](#findstringexact)|Znajduje pierwszy ciąg pole listy (w polu kombi), który pasuje do określonego ciągu.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Pobiera informacje o `CComboBox` obiektu.|
|[CComboBox::GetCount](#getcount)|Pobiera liczbę elementów w polu listy, pola kombi.|
|[CComboBox::GetCueBanner](#getcuebanner)|Pobiera tekst wskaźnika, który jest wyświetlany formantu pola kombi.|
|[CComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie wybranego elementu, jeśli istnieje, w polu listy, pola kombi.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Pobiera współrzędne ekranu widoczne (porzuconych w dół) listy pola kombi z listy rozwijanej.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Określa, czy pole listy rozwijanej kombi jest widoczny (rozwinął).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Pobiera minimalna dozwolona szerokość dla części pole listy rozwijanej pola kombi.|
|[CComboBox::GetEditSel](#geteditsel)|Pobiera początkowy i końcowy pozycji znaku bieżące zaznaczenie w formancie edycji pola kombi.|
|[CComboBox::GetExtendedUI](#getextendedui)|Określa, czy pole kombi ma domyślny interfejs użytkownika lub interfejs użytkownika rozszerzonej.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Zwraca szerokość w pikselach, że część pola listy, pola kombi może być przewijane w poziomie.|
|[CComboBox::GetItemData](#getitemdata)|Pobiera wartość 32-bitowa aplikacja dostarczona skojarzone z elementem pola kombi.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Pobiera dostarczone przez aplikację wskaźnika 32-bitowego, który jest skojarzony z elementem pola kombi.|
|[CComboBox::GetItemHeight](#getitemheight)|Pobiera wysokość elementy listy w polu kombi.|
|[CComboBox::GetLBText](#getlbtext)|Pobiera ciąg, z listy rozwijanej pola kombi.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Pobiera długość ciągu w polu listy, pola kombi.|
|[CComboBox::GetLocale](#getlocale)|Pobiera identyfikator ustawień regionalnych dla pola kombi.|
|[CComboBox::GetMinVisible](#getminvisible)|Pobiera minimalną liczbę widocznych elementów na liście rozwijanej bieżącego pola kombi.|
|[CComboBox::GetTopIndex](#gettopindex)|Zwraca indeks pierwszego elementu widoczny w polu listy części pola kombi.|
|[CComboBox::InitStorage](#initstorage)|Preallocates bloki pamięci dla elementów i ciągi w części zawierającej pole listy pola kombi.|
|[CComboBox::InsertString](#insertstring)|Wstawia ciąg w polu listy, pola kombi.|
|[CComboBox::LimitText](#limittext)|Ogranicza długość tekstu, który użytkownik może wprowadzić do kontrolki edycji pola kombi.|
|[CComboBox::MeasureItem](#measureitem)|Metoda wywoływana przez platformę, aby określić wymiary pola kombi, po utworzeniu pola kombi rysowanych przez właściciela.|
|[CComboBox::Paste](#paste)|Wstawia dane ze Schowka do kontrolki edycji w bieżącym położeniu kursora. Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.|
|[CComboBox::ResetContent](#resetcontent)|Usuwa wszystkie elementy z listy pola i edytować kontrolki pola kombi.|
|[CComboBox::SelectString](#selectstring)|Wyszukuje ciąg w polu listy, pola kombi i, jeśli ciąg zostanie znaleziony, wybiera ten ciąg w polu listy i kopiuje ciąg do kontrolki edycji.|
|[CComboBox::SetCueBanner](#setcuebanner)|Ustawia tekst wskaźnika, który jest wyświetlany formantu pola kombi.|
|[CComboBox::SetCurSel](#setcursel)|Wybiera ciąg w polu listy, pola kombi.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Ustawia minimalna dozwolona szerokość dla części pole listy rozwijanej pola kombi.|
|[CComboBox::SetEditSel](#seteditsel)|Wybiera znaków w kontrolce edycji pola kombi.|
|[CComboBox::SetExtendedUI](#setextendedui)|Wybiera domyślny interfejs użytkownika lub interfejs użytkownika rozszerzonego pola kombi, którego styl CBS_DROPDOWN lub CBS_DROPDOWNLIST.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Określa szerokość w pikselach, że część pola listy, pola kombi może być przewijane w poziomie.|
|[CComboBox::SetItemData](#setitemdata)|Ustawia wartość 32-bitowych, skojarzone z określonym elementem w polu kombi.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Ustawia wskaźnik 32-bitowych, skojarzone z określonym elementem w polu kombi.|
|[CComboBox::SetItemHeight](#setitemheight)|Ustawia wysokość elementy listy w polu kombi lub wysokości kontrolki edycji (lub tekst statyczny) część pola kombi.|
|[CComboBox::SetLocale](#setlocale)|Określa identyfikator ustawień regionalnych dla pola kombi.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącego pola kombi.|
|[CComboBox::SetTopIndex](#settopindex)|Informuje o części pola listy pola kombi, aby wyświetlić element z określonym indeksem u góry.|
|[CComboBox::ShowDropDown](#showdropdown)|Pokazuje lub ukrywa pole listy pola kombi, którego styl CBS_DROPDOWN lub CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Uwagi

Pole kombi składa się z pola listy, w połączeniu ze statycznych kontrolki lub kontrolki edycji. Pole listy części kontrolki mogą być wyświetlane przez cały czas lub mogą tylko listę rozwijaną, gdy użytkownik wybierze strzałkę listy rozwijanej obok formantu.

Aktualnie wybranego elementu (jeśli istnieją) w polu listy są wyświetlane w statycznych lub Edytuj kontrolkę. Ponadto jeśli pole kombi stylu listy rozwijanej, którą użytkownik może wpisać litery jeden z elementów na liście, a pola listy, jeśli jest widoczne, wyróżni następny element tego początkowego znaku.

W poniższej tabeli porównano trzy pola kombi [style](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles).

|Styl|Widoczne jest pole listy|Formant statyczny lub edycji|
|-----------|-------------------------------|-----------------------------|
|Proste|zawsze|Edytowanie|
|Lista rozwijana|Gdy rozwinął|Edytowanie|
|Listy rozwijanej|Gdy rozwinął|Static|

Możesz utworzyć `CComboBox` obiektu z szablonu okna dialogowego lub bezpośrednio w kodzie. W obu przypadkach należy najpierw wywołać konstruktora `CComboBox` do konstruowania `CComboBox` obiektu; następnie wywołać [Utwórz](#create) funkcja elementu członkowskiego, aby utworzyć formantu i dołączyć go do `CComboBox` obiektu.

Jeśli chcesz obsługiwać Windows powiadomienia wysyłane przez pola kombi do elementu nadrzędnego (zazwyczaj klasą pochodną `CDialog`), dodanie funkcji składowej wejścia i program obsługi komunikatów mapy komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów ma następującą postać:

**ON\_**_powiadomień_ **(** _identyfikator_, _memberFxn_ **)**

gdzie `id` Określa identyfikator okna podrzędnego kontrolki pola kombi, wysyłania powiadomienia i `memberFxn` nazywa się nadrzędny element członkowski funkcji zostały napisane do obsługi powiadomień.

Prototyp funkcji elementu nadrzędnego jest następująca:

**afx_msg** `void` `memberFxn` **();**

Nie można przewidzieć kolejności, w której niektóre powiadomienia będą wysyłane. W szczególności powiadomienie CBN_SELCHANGE może wystąpić przed lub po powiadomieniu CBN_CLOSEUP.

Poniżej przedstawiono potencjalne wpisy mapy komunikatów:

- ON_CBN_CLOSEUP (Windows 3.1 lub nowszy). Pola listy, pola kombi zostało zamknięte. Taki komunikat powiadomienia nie są wysyłane do pola kombi, która ma [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

- ON_CBN_DBLCLK użytkownik kliknie dwukrotnie ciąg w polu listy, pola kombi. To powiadomienie jest wysyłane tylko w przypadku pole kombi stylu CBS_SIMPLE. Pola kombi z [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, dwukrotne kliknięcie nie może wystąpić, ponieważ jednym kliknięciem powoduje ukrycie pola listy.

- ON_CBN_DROPDOWN ma listę rozwijaną pola listy, pola kombi (były widoczne,). Taki komunikat powiadomienia, może wystąpić tylko w przypadku pola kombi w stylu CBS_DROPDOWN lub CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE użytkownik ma podjąć akcję, która może być zmieniony tekst w części kontrolki edycji pola kombi. W przeciwieństwie do komunikatu CBN_EDITUPDATE ta wiadomość jest wysyłana po Windows aktualizacji ekranu. Nie są wysyłane, jeśli pole kombi stylu CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE części kontrolki edycji pola kombi wkrótce zmieniony tekst. Taki komunikat powiadomienia są wysyłane po formant został sformatowany tekst, ale przed jego służy do wyświetlania tekstu. Nie są wysyłane, jeśli pole kombi stylu CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE pola kombi nie może przydzielić wystarczającej ilości pamięci, aby spełnić określonego żądania.

- ON_CBN_SELENDCANCEL (Windows 3.1 lub nowszy). Wskazuje, że wybór użytkownika powinna zostać anulowana. Użytkownik kliknie pozycję, a następnie klika przycisk innego okna lub formantu, aby ukryć pole listy, pola kombi. To powiadomienie jest wysyłane przed CBN_CLOSEUP komunikatu powiadomienia w celu wskazania, że wybór użytkownika mają być ignorowane. CBN_SELENDCANCEL lub CBN_SELENDOK komunikatu powiadomienia są wysyłane, nawet wtedy, gdy CBN_CLOSEUP komunikatu powiadomienia nie są wysyłane (jak w przypadku pole kombi stylu CBS_SIMPLE).

- ON_CBN_SELENDOK użytkownik wybierze element a następnie naciśnięcie klawisza ENTER lub kliknie klawisz Strzałka w dół, aby ukryć pole listy, pola kombi. To powiadomienie jest wysyłane przed CBN_CLOSEUP komunikat wskazujący, że wybór użytkownika powinien były uważane za prawidłowe. CBN_SELENDCANCEL lub CBN_SELENDOK komunikatu powiadomienia są wysyłane, nawet wtedy, gdy CBN_CLOSEUP komunikatu powiadomienia nie są wysyłane (jak w przypadku pole kombi stylu CBS_SIMPLE).

- Pole kombi ON_CBN_KILLFOCUS utracie fokusu wprowadzania.

- ON_CBN_SELCHANGE zaznaczenie w polu listy, pola kombi jest można zmienić po wysłaniu przez użytkownika, klikając pozycję w polu listy lub zmianę za pomocą klawiszy strzałek. Podczas przetwarzania tego komunikatu, tekst w kontrolce edycji pola kombi mogą być pobierane tylko za pośrednictwem `GetLBText` lub innego podobną funkcję. `GetWindowText` Nie można użyć.

- Pole kombi ON_CBN_SETFOCUS otrzymuje fokus wprowadzania.

Jeśli tworzysz `CComboBox` obiektu w oknie dialogowym (za pośrednictwem zasobu okna dialogowego), `CComboBox` obiektu automatycznie jest niszczony, kiedy użytkownik zamknie okno dialogowe.

W przypadku osadzenia `CComboBox` obiektu obiektu w innym oknie, nie trzeba go zniszcz. Jeśli tworzysz `CComboBox` obiektów na stosie, zostanie zniszczony automatycznie. Jeśli tworzysz `CComboBox` obiektów na stosie przy użyciu **nowe** funkcji, należy wywołać **Usuń** na obiekt, aby je zniszczyć, kiedy niszczony jest pole kombi Windows.

**Uwaga** Jeśli chcesz obsługiwać przetłumaczyła i WM_CHAR wiadomości, masz do podklasy pola kombi edycji i formanty pola listy, pochodną klasy z `CEdit` i `CListBox`, i Dodaj programy obsługi dla tych komunikatów dla klasy pochodnej. Aby uzyskać więcej informacji, zobacz [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="addstring"></a>  CComboBox::AddString

Dodaje ciąg do pola listy, pola kombi.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który ma zostać dodany.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks na ciąg w polu listy. Wartość zwracana jest CB_ERR, jeśli wystąpi błąd; Wartość zwracana jest CB_ERRSPACE, jeśli brak wystarczającej ilości miejsca do przechowywania nowego ciągu znaków.

### <a name="remarks"></a>Uwagi

Jeśli pole listy nie został utworzony za pomocą [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, ciąg zostanie dodany na końcu listy. W przeciwnym razie ten ciąg jest wstawiany do listy, a lista jest posortowana.

> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez Windows `ComboBoxEx` kontroli. Aby uzyskać więcej informacji na temat tego formantu, zobacz [kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) w zestawie Windows SDK.

Aby wstawić ciąg do konkretnej lokalizacji na liście, należy użyć [InsertString](#insertstring) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>  CComboBox::CComboBox

Konstruuje `CComboBox` obiektu.

```
CComboBox();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>  CComboBox::Clear

Usuwa (czyści) bieżące zaznaczenie w formancie edycji pola kombi.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Aby usunąć bieżące zaznaczenie i umieść usunięto zawartość do Schowka, należy użyć [Wytnij](#cut) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>  CComboBox::CompareItem

Metoda wywoływana przez platformę, aby określić względne położenie nowego elementu w polu listy części pola kombi rysowanego przez właściciela posortowany.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parametry

*lpCompareItemStruct*<br/>
Długie wskaźnik do [COMPAREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagcompareitemstruct) struktury.

### <a name="return-value"></a>Wartość zwracana

Wskazuje względne położenie dwa elementy, które opisano w `COMPAREITEMSTRUCT` struktury. Może być dowolną z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|- 1|Sortuje element 1 przed elementem 2.|
|0|Element 1 i element 2 Sortuj takie same.|
|1|Sortuje element 1 po elemencie 2.|

Zobacz [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) opis `COMPAREITEMSTRUCT`.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Jeśli tworzysz pole kombi rysowanego przez właściciela ze stylem LBS_SORT, konieczne jest przesłonięcie tej funkcji elementu członkowskiego ułatwiających ramach sortowanie nowe elementy dodane do pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>  CComboBox::Copy

Kopiuje bieżącego zaznaczenia, jeśli występują w formancie edycji pola kombi do Schowka w formacie CF_TEXT.

```
void Copy();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>  CComboBox::Create

Tworzy pola kombi i dołącza je do `CComboBox` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola kombi. Zastosuj dowolną kombinację [style pola kombi](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) do pola.

*Rect*<br/>
Wskazuje położenie i rozmiar pola kombi. Może być [struktura RECT](/windows/desktop/api/windef/ns-windef-tagrect) lub `CRect` obiektu.

*pParentWnd*<br/>
Określa pole kombi okna nadrzędnego (zazwyczaj `CDialog`). Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki pola kombi

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CComboBox` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, który tworzy pole kombi Windows i dołącza go do `CComboBox` obiektu.

Gdy `Create` wykonuje Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) Komunikaty wyjściowe do pola kombi.

Te komunikaty są obsługiwane domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [ongetminmaxinfo —](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcji elementów członkowskich w `CWnd` klasy bazowej. Aby rozszerzyć domyślnej obsługi komunikatów, należy wyprowadzić klasę z `CComboBox`, dodać mapy komunikatów do nowej klasy, a zastąpienie poprzedniej funkcji elementów członkowskich programu obsługi komunikatów. Zastąp `OnCreate`, na przykład do przeprowadzenia wymaganych inicjowania dla nowej klasy.

Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pola kombi. :

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL można dodać przewijanie w pionie pola listy w polu kombi

- WS_HSCROLL można dodać przewijania poziomego pola listy w polu kombi

- WS_GROUP kontrolek grupy

- WS_TABSTOP Aby dołączyć pola kombi w kolejności tabulacji

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>  CComboBox::Cut

Usuwa (kawałki) bieżące zaznaczenie w polu kombi edycji kontroli i kopiuje usunięty tekst do Schowka w formacie CF_TEXT.

```
void Cut();
```

### <a name="remarks"></a>Uwagi

Aby usunąć bieżące zaznaczenie bez pogarszania usunięty tekst do Schowka, wywołaj [wyczyść](#clear) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>  CComboBox::DeleteItem

Wywoływane przez platformę, gdy użytkownik usuwa element z rysowanym przez właściciela `CComboBox` obiektu lub niszczy pola kombi.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDeleteItemStruct*<br/>
Długie wskaźnik do Windows [DELETEITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdeleteitemstruct) strukturę, która zawiera informacje na temat usuniętego elementu. Zobacz [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) opis tej struktury.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji, nic nie robi. Należy przesłonić tę funkcję, aby odświeżyć pola kombi, zgodnie z potrzebami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>  CComboBox::DeleteString

Usuwa element w miejscu *nIndex* z pola kombi.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa indeks na ciąg, który ma zostać usunięty.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa niż lub równa 0, to liczba parametrów na liście. Wartość zwracana jest CB_ERR, jeśli *nIndex* Określa indeks jest większa niż liczba elementów na liście.

### <a name="remarks"></a>Uwagi

Wszystkie elementy występujące *nIndex* teraz Przenieś w dół o jedną pozycję. Na przykład jeśli pole kombi zawiera dwa elementy, usunięcie pierwszy element spowoduje, że element pozostałe które mają być teraz na pierwszym miejscu. *nIndex*= 0 dla elementu na pierwszym miejscu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>  CComboBox::Dir

Dodaje listę nazw plików lub dysków do pola listy, pola kombi.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parametry

*attr*<br/>
Może być dowolną kombinacją **wyliczenia** wartości opisane w [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) lub dowolnej kombinacji następujących wartości:

- Plik DDL_READWRITE może odczytywać lub zapisywana.

- Plik DDL_READONLY można odczytywać, ale nie zapisane.

- Plik DDL_HIDDEN jest ukryta i nie ma na liście katalogów.

- DDL_SYSTEM plik jest plikiem systemu.

- DDL_DIRECTORY nazwy określonej przez *lpszWildCard* Określa katalog.

- Plik DDL_ARCHIVE został zarchiwizowany.

- DDL_DRIVES obejmują wszystkie dyski, które odpowiada nazwie określonej przez *lpszWildCard*.

- Flaga DDL_EXCLUSIVE wyłączności. Wyłączne flaga jest ustawiona, wyświetlane są tylko pliki o określonym typie. W przeciwnym razie pliki o określonym typie są wymienione oprócz plików "normal".

*lpszWildCard*<br/>
Wskazuje ciąg specyfikacji pliku. Ciąg może zawierać symbole wieloznaczne (na przykład *.\*).

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks ostatniego filename dodany do listy. Wartość zwracana jest CB_ERR, jeśli wystąpi błąd; Wartość zwracana jest CB_ERRSPACE w przypadku niewystarczającej ilości miejsca do przechowywania nowych parametrów.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana przez Windows `ComboBoxEx` kontroli. Aby uzyskać więcej informacji na temat tego formantu, zobacz [kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>  CComboBox::DrawItem

Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany pola kombi rysowanego przez właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.

### <a name="remarks"></a>Uwagi

`itemAction` Członkiem `DRAWITEMSTRUCT` struktury definiuje rysowania akcję, która ma zostać wykonane. Zobacz [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) opis tej struktury.

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego do zaimplementowania rysunku do rysowania przez właściciela `CComboBox` obiektu. Przed kończy działanie tej funkcji elementu członkowskiego, aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>  CComboBox::FindString

Umożliwia znalezienie, ale nie wybierze pierwszy ciąg, który zawiera określony prefiks w polu listy, pola kombi.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nStartAfter*. Jeśli wartość-1, pole listy cały przeszukiwany jest od początku.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne, więc ten ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest większa niż lub równa 0, jest liczony od zera indeks pasujący element. Jest to CB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest obsługiwana przez Windows `ComboBoxEx` kontroli. Aby uzyskać więcej informacji na temat tego formantu, zobacz [kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>  CComboBox::FindStringExact

Wywołaj `FindStringExact` funkcja elementu członkowskiego, aby znaleźć pierwszy ciąg pole listy (w polu kombi), który pasuje do ciągu określonego w *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parametry

*nIndexStart*<br/>
Określa liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nIndexStart*. Jeśli *nIndexStart* wynosi -1, pole listy cały przeszukiwany jest od samego początku.

*lpszFind*<br/>
Wskazuje ciąg zakończony wartością null do wyszukania. Ten ciąg może zawierać pełną nazwę pliku, łącznie z rozszerzeniem. Wyszukiwanie nie jest uwzględniana wielkość liter, więc ten ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pasujący element lub CB_ERR, jeśli wyszukiwanie nie powiodło się.

### <a name="remarks"></a>Uwagi

Jeśli pole kombi została utworzona przy użyciu stylu rysowania przez właściciela, ale bez [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu `FindStringExact` próbuje dopasować wartość bitowego względem wartości *lpszFind*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>  CComboBox::GetComboBoxInfo

Pobiera informacje o `CComboBox` obiektu.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parametry

*pcbi*<br/>
Wskaźnik do [COMBOBOXINFO](/windows/desktop/api/winuser/ns-winuser-tagcomboboxinfo) struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność [CB_GETCOMBOBOXINFO](/windows/desktop/Controls/cb-getcomboboxinfo) komunikat, zgodnie z opisem w zestawie Windows SDK.

##  <a name="getcount"></a>  CComboBox::GetCount

Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę elementów w części zawierającej pole listy, pola kombi.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów. Zwrócona liczba jest większa o jeden od ostatniego elementu (indeks jest liczony od zera) wartości indeksu. Jeśli wystąpi błąd, jest CB_ERR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>  CComboBox::GetCueBanner

Pobiera tekst wskaźnika, który jest wyświetlany formantu pola kombi.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszText*|[out] Wskaźnik do buforu, który otrzymuje Tekst transparentu wskaźnika.|
|*cchText*|[in] Rozmiar buforu, który *lpszText* parametr wskazuje.|

### <a name="return-value"></a>Wartość zwracana

W pierwsze przeciążenie [CString](../../atl-mfc-shared/using-cstring.md) obiekt, który zawiera tekst transparentu oznak aktywacji, jeśli istnieje; w przeciwnym razie `CString` obiekt, który ma zerową długość.

—lub—

Drugie przeciążenie wartość TRUE jeśli ta metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Tekst wskaźnika jest monit jest wyświetlany w obszarze danych wejściowych formant pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik udostępnia dane wejściowe.

Ta metoda wysyła [CB_GETCUEBANNER](/windows/desktop/Controls/cb-getcuebanner) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getcursel"></a>  CComboBox::GetCurSel

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, który element w polu kombi jest zaznaczony.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera Indeks aktualnie wybranego elementu w polu listy, pola kombi lub CB_ERR, jeśli nie wybrano elementu.

### <a name="remarks"></a>Uwagi

`GetCurSel` Zwraca indeks do listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>  CComboBox::GetDroppedControlRect

Wywołaj `GetDroppedControlRect` funkcję elementu członkowskiego, aby pobrać współrzędne ekranu oknie widoczne (usunięty) listy rozwijanej pola kombi z listy rozwijanej.

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parametry

*lprect —*<br/>
Wskazuje [struktura RECT](/windows/desktop/api/windef/ns-windef-tagrect) to uzyskanie współrzędnych.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>  CComboBox::GetDroppedState

Wywołaj `GetDroppedState` funkcja elementu członkowskiego, aby ustalić, czy pole listy rozwijanej kombi jest widoczny (rozwinął).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pole listy jest widoczny; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>  CComboBox::GetDroppedWidth

Wywołaj tę funkcję, aby pobrać minimalną szerokość dopuszczalny rozmiar w pikselach, pola listy, pola kombi.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, minimalna dopuszczalna szerokość w pikselach; w przeciwnym razie CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja ma zastosowanie tylko do pola kombi z [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

Domyślnie dozwolone minimalną szerokość pola listy rozwijanej to 0. Można ustawić minimalną szerokość dozwoloną przez wywołanie metody [SetDroppedWidth](#setdroppedwidth). Po wyświetleniu część pola listy, pola kombi jej szerokość była równa minimalnej szerokości dozwolony lub szerokość pola kombi.

### <a name="example"></a>Przykład

  Zobacz przykład [SetDroppedWidth](#setdroppedwidth).

##  <a name="geteditsel"></a>  CComboBox::GetEditSel

Pobiera początkowy i końcowy pozycji znaku bieżące zaznaczenie w formancie edycji pola kombi.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Wartość zwracana

32-bitową wartość zawiera pozycja początkowa w programie word niskiego rzędu i położenie pierwszego wystąpienia znaku nonselected po zakończeniu wyboru w programie word wyższego rzędu. Jeśli ta funkcja jest używana w polu kombi bez formant edycji, zwracany jest CB_ERR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>  CComboBox::GetExtendedUI

Wywołaj `GetExtendedUI` funkcja elementu członkowskiego, aby określić, czy pole kombi ma domyślny interfejs użytkownika lub interfejs użytkownika rozszerzonej.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pole kombi ma interfejs użytkownika rozszerzone; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Interfejs użytkownika rozszerzoną można zidentyfikować w następujący sposób:

- Kliknięcie przycisku kontrolki statycznej Wyświetla pole listy tylko w przypadku pola kombi z [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

- Naciśnięcie klawisza Strzałka w dół wyświetla pola listy (F4 jest wyłączone).

Przewijanie w kontrolce statycznych jest wyłączona, gdy listy elementów nie jest widoczny (strzałka klucze są wyłączone).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>  CComboBox::GetHorizontalExtent

Pobiera z pola kombi szerokość w pikselach, za pomocą których część pola listy, pola kombi mogą być przewijane w poziomie.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Wartość zwracana

Przewijany szerokość pola listy części pola kombi, w pikselach.

### <a name="remarks"></a>Uwagi

Ma to zastosowanie tylko wtedy, gdy część pola listy, pola kombi poziomy pasek przewijania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>  CComboBox::GetItemData

Pobiera wartość 32-bitowa aplikacja dostarczona skojarzone z elementem pola kombi.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks elementu w polu listy pola kombi.

### <a name="return-value"></a>Wartość zwracana

32-bitową wartość skojarzony element lub CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

32-bitową wartość można ustawić za pomocą *dwItemData* parametru [setitemdata —](#setitemdata) wywołanie funkcji elementu członkowskiego. Użyj `GetItemDataPtr` funkcja elementu członkowskiego, jeśli wskaźnik 32-bitową wartość do pobrania (**void** <strong>\*</strong>).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>  CComboBox::GetItemDataPtr

Pobiera wartość 32-bitowa aplikacja dostarczona skojarzone z elementem pola kombi jako wskaźnik (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks elementu w polu listy pola kombi.

### <a name="return-value"></a>Wartość zwracana

Pobiera wskaźnik lub wartość -1, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>  CComboBox::GetItemHeight

Wywołaj `GetItemHeight` funkcję elementu członkowskiego, aby pobrać wysokość elementy listy w polu kombi.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa składnik pola kombi, których wysokość jest do pobrania. Jeśli *nIndex* parametru wynosi -1, wysokość kontrolki edycji (lub tekst statyczny) część pola kombi są pobierane. Jeśli pole kombi [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu *nIndex* określa liczony od zera indeks elementu listy, których wysokość jest do pobrania. W przeciwnym razie *nIndex* powinna być równa 0.

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach, określony element w polu kombi. Wartość zwracana jest CB_ERR, jeśli wystąpi błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>  CComboBox::GetLBText

Pobiera ciąg, z listy rozwijanej pola kombi.

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
Zawiera liczony od zera indeks ciągu pole listy ma być skopiowany.

*lpszText*<br/>
Wskazuje buforu, który jest na ciąg. Rozmiar buforu musi mieć wystarczającą ilość miejsca na ciąg i kończącego znaku null.

*rString*<br/>
Odwołanie do `CString`.

### <a name="return-value"></a>Wartość zwracana

Długość (w bajtach) ciąg, z wyjątkiem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowy indeks, zwracana jest wartość CB_ERR.

### <a name="remarks"></a>Uwagi

Druga forma ten element członkowski funkcji wypełnienia `CString` obiektu z tekstu elementu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>  CComboBox::GetLBTextLen

Pobiera długość ciągu w polu listy, pola kombi.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks ciągu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu w bajtach, z wyjątkiem kończącego znaku null. Jeśli *nIndex* nie określa prawidłowy indeks, zwracana jest wartość CB_ERR.

### <a name="example"></a>Przykład

  Zobacz przykład [CComboBox::GetLBText](#getlbtext).

##  <a name="getlocale"></a>  CComboBox::GetLocale

Pobiera ustawienia regionalne używane przez pola kombi.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość identyfikatora (LCID) ustawień regionalnych dla ciągów w polu kombi.

### <a name="remarks"></a>Uwagi

Ustawienia regionalne jest używany, na przykład do określenia kolejności sortowania ciągów w polu kombi posortowany.

### <a name="example"></a>Przykład

  Zobacz przykład [CComboBox::SetLocale](#setlocale).

##  <a name="getminvisible"></a>  CComboBox::GetMinVisible

Pobiera minimalną liczbę widocznych elementów na liście rozwijanej bieżącego formant pola kombi.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Wartość zwracana

Minimalna liczba widocznych elementów z bieżącej listy rozwijanej.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [CB_GETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="gettopindex"></a>  CComboBox::GetTopIndex

Pobiera liczony od zera indeks pierwszego elementu widoczny w polu listy części pola kombi.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pierwszego elementu widoczny w polu listy części pola kombi, jeśli to się powiedzie, w przeciwnym razie CB_ERR.

### <a name="remarks"></a>Uwagi

Początkowo element 0 jest w górnej części pola listy, ale jeśli jest przewijane w polu listy, innego elementu może być u góry.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>  CComboBox::InitStorage

Przydziela pamięć do przechowywania elementów pola listy w polu listy części pola kombi.

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

Jeśli operacja się powiedzie, maksymalna liczba elementów, które mogą być przechowywane przez część pola listy, pola kombi przed ponowne przydzielenie pamięci jest potrzebne, w przeciwnym razie CB_ERRSPACE, nie oznacza, jest dostępna wystarczająca ilość pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, przed dodaniem dużą liczbę elementów do pola listy części `CComboBox`.

Windows 95/98 tylko: *WParam* parametru jest ograniczona do wartości 16-bitowych. Oznacza to, że pola listy nie może zawierać więcej niż 32 767 elementów. Mimo że liczba elementów jest ograniczone, całkowity rozmiar elementów w polu listy jest ograniczony tylko ilością dostępnej pamięci.

Ta funkcja pomaga w szybszym inicjowania pola listy, które mają dużą liczbę elementów (ponad 100). Jego preallocates określonej ilości pamięci, dlatego oznacza kolejne [addstring —](#addstring), [InsertString](#insertstring), i [Dir](#dir) funkcje podejmują najkrótszym czasie. Można użyć szacunki dla parametrów. Jeśli overestimate, niektóre dodatkowe pamięć została przydzielona; Jeśli zaniżają, normalne alokacji jest używany dla elementów, które przekraczają kwotę przydzielony wstępnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>  CComboBox::InsertString

Wstawia ciąg w polu listy, pola kombi.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks w miejsce, w polu listy, który otrzyma ten ciąg. Jeśli ten parametr ma wartość -1, ciąg jest dodawany na końcu listy.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, która ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks sytuację, w którym ciąg został wstawiony. Wartość zwracana jest CB_ERR, jeśli wystąpi błąd. Wartość zwracana jest CB_ERRSPACE, jeśli brak wystarczającej ilości miejsca do przechowywania nowego ciągu znaków.

### <a name="remarks"></a>Uwagi

W odróżnieniu od [addstring —](#addstring) funkcja elementu członkowskiego `InsertString` funkcji składowej nie powoduje, że lista z [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) styl ma zostać posortowana.

> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez Windows `ComboBoxEx` kontroli. Aby uzyskać więcej informacji na temat tego formantu, zobacz [kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>  CComboBox::LimitText

Ogranicza długość w bajtach tekst, który użytkownik może wprowadzić do kontrolki edycji pola kombi.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Określa długość (w bajtach) tekst, który użytkownik może wprowadzić. Jeśli ten parametr ma wartość 0, długość tekstu wynosi 65 535 bajtów.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli to się powiedzie. Jeśli wywołania będą pola kombi ze stylem [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub pola kombi bez formant edycji, wartość zwracana jest CB_ERR.

### <a name="remarks"></a>Uwagi

Jeśli pole kombi nie ma stylu [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), ustawiając limit tekstu będzie większy niż rozmiar kontrolki edycji odniesie żadnego skutku.

`LimitText` tylko ogranicza ich tekst, który użytkownik może wprowadzić. Go nie ma wpływu na dowolny tekst już w formancie edycji, gdy komunikat jest wysyłany ani nie ogranicza długość tekstu skopiowane do kontrolki edycji, po wybraniu ciąg w polu listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>  CComboBox::MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony przy użyciu stylu rysowania przez właściciela pole kombi.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długie wskaźnik do [MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct) struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego, a następnie wypełnij `MEASUREITEMSTRUCT` strukturę, aby poinformować Windows wymiary listy pola w polu kombi. Jeśli pola kombi są tworzone za pomocą [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, struktura wywołuje tej funkcji elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ta składowa zostanie wywołana tylko raz.

Przy użyciu stylu CBS_OWNERDRAWFIXED w polu kombi rysowanego przez właściciela utworzonych za pomocą [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) funkcji składowej typu `CWnd` obejmuje zagadnienia dotyczące dalszego programowania. Zobacz Omówienie w [techniczne Uwaga 14](../../mfc/tn014-custom-controls.md).

Zobacz [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) opis `MEASUREITEMSTRUCT` struktury.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>  CComboBox::Paste

Wstawia dane ze Schowka do kontrolki edycji pola kombi w bieżącym położeniu kursora.

```
void Paste();
```

### <a name="remarks"></a>Uwagi

Dane są wstawiane tylko wtedy, gdy Schowek zawiera dane w formacie CF_TEXT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>  CComboBox::ResetContent

Usuwa wszystkie elementy z listy pola i edytować kontrolki pola kombi.

```
void ResetContent();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>  CComboBox::SelectString

Wyszukuje ciąg w polu listy, pola kombi, a jeśli ciąg zostanie znaleziony, wybiera ten ciąg w polu listy i kopiuje go do kontrolki edycji.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nStartAfter*<br/>
Zawiera liczony od zera indeks elementu przed pierwszy element do wyszukania. Podczas wyszukiwania osiągnie dolną część pola listy, kontynuuje od górnej krawędzi pola listy do elementu określonego przez *nStartAfter*. Jeśli wartość-1, pole listy cały przeszukiwany jest od początku.

*lpszString*<br/>
Wskazuje ciąg zakończony znakiem null, który zawiera prefiks do wyszukania. Wyszukiwanie jest niezależne, więc ten ciąg może zawierać dowolnej kombinacji wielkich i małych liter.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks zaznaczonego elementu, jeśli znaleziono ciąg. Jeśli wyszukiwanie nie powiodło się, wartością zwracaną jest CB_ERR i bieżącego zaznaczenia nie ulegną zmianie.

### <a name="remarks"></a>Uwagi

Ciąg jest zaznaczone, tylko wtedy, gdy jego początkowe znaki (z punktem początkowym) dopasowuje znaki do ciągu prefiksu.

Należy pamiętać, że `SelectString` i `FindString` elementów członkowskich zarówno znaleźć ciąg, ale `SelectString` funkcja elementu członkowskiego zaznacza ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>  CComboBox::SetCueBanner

Ustawia tekst wskaźnika, który jest wyświetlany formantu pola kombi.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpszText*|[in] Wskaźnik do buforu zakończony znakiem null, zawierający tekst wskaźnika.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Tekst wskaźnika jest monit jest wyświetlany w obszarze danych wejściowych formant pola kombi. Tekst wskaźnika jest wyświetlany, dopóki użytkownik udostępnia dane wejściowe.

Ta metoda wysyła [CB_SETCUEBANNER](/windows/desktop/Controls/cb-setcuebanner) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_combobox*, która jest używana do uzyskania programowego dostępu formant pola kombi. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu ustawia transparent podpowiedź dla kontrolki pola kombi.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>  CComboBox::SetCurSel

Wybiera ciąg w polu listy, pola kombi.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parametry

*nWybierz*<br/>
Określa liczony od zera indeks ciągu, aby wybrać. Jeśli wartość -1, wszystkie bieżące zaznaczenie w polu listy zostanie usunięty, a kontrolka edycji zostanie wyczyszczona.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks elementu wybierana, jeżeli komunikat zakończy się pomyślnie. Wartość zwracana jest CB_ERR, jeśli *nWybierz* jest większa niż liczba elementów na liście lub jeśli *nWybierz* jest ustawiona na wartość -1, co spowoduje wyczyszczenie zaznaczenia.

### <a name="remarks"></a>Uwagi

Jeśli to konieczne, pole listy Przewija ciąg do wyświetlenia (jeśli jest to widoczne jest pole listy). Tekstu w formancie edycji pola kombi jest zmieniany w celu odzwierciedlenia wyboru nowego. Wszelkie poprzednie zaznaczenie w polu listy są usuwane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>  CComboBox::SetDroppedWidth

Wywołaj tę funkcję, aby ustawić minimalną szerokość dopuszczalny rozmiar, w pikselach, pola listy, pola kombi.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Minimalna szerokość dopuszczalny rozmiar część pola listy, pola kombi, w pikselach.

### <a name="return-value"></a>Wartość zwracana

W przypadku powodzenia nową szerokość pola listy, w przeciwnym razie CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja ma zastosowanie tylko do pola kombi z [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

Domyślnie dozwolone minimalną szerokość pola listy rozwijanej to 0. Po wyświetleniu część pola listy, pola kombi jej szerokość była równa minimalnej szerokości dozwolony lub szerokość pola kombi.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>  CComboBox::SetEditSel

Wybiera znaków w kontrolce edycji pola kombi.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parametry

*nStartChar*<br/>
Określa położenie początkowe. Jeśli pozycja początkowa jest ustawiona na wartość -1, zostaną usunięte wszystkie zaznaczone.

*nEndChar*<br/>
Określa pozycję końcową. Jeśli pozycja końcowa jest ustawiona na wartość -1, następnie cały tekst z pozycji początkowej do ostatniego znaku w formancie edycji jest zaznaczone.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja członkowska jest kończy się pomyślnie; w przeciwnym razie 0. Jeśli występuje CB_ERR `CComboBox` ma [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu lub nie ma pola listy.

### <a name="remarks"></a>Uwagi

Położenie jest liczony od zera. Aby zaznaczyć pierwszy znak kontrolki edycji, należy określić początkową 0. Pozycja końcowa jest znaku zaraz po ostatnim znakiem, aby wybrać. Na przykład aby wybrać pierwsze cztery znaki kontrolki edycji, będą używać począwszy od pozycji 0 i pozycji końcowej 4.

> [!NOTE]
>  Ta funkcja nie jest obsługiwana przez Windows `ComboBoxEx` kontroli. Aby uzyskać więcej informacji na temat tego formantu, zobacz [kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-controls) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CComboBox::GetEditSel](#geteditsel).

##  <a name="setextendedui"></a>  CComboBox::SetExtendedUI

Wywołaj `SetExtendedUI` funkcja elementu członkowskiego, aby wybrać domyślny interfejs użytkownika lub interfejs użytkownika rozszerzonego pola kombi, która ma [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parametry

*bPrzedłużony*<br/>
Określa, czy pole kombi powinien używać interfejsu użytkownika rozszerzonej lub domyślny interfejs użytkownika. Wartość TRUE wybiera interfejs użytkownika rozszerzone; wartość FALSE wybiera standardowy interfejs użytkownika.

### <a name="return-value"></a>Wartość zwracana

CB_OKAY, jeśli operacja zakończy się pomyślnie, lub CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Interfejs użytkownika rozszerzoną można zidentyfikować w następujący sposób:

- Kliknięcie przycisku kontrolki statycznej Wyświetla pole listy tylko dla pól kombi stylu CBS_DROPDOWNLIST.

- Naciśnięcie klawisza Strzałka w dół wyświetla pola listy (F4 jest wyłączone).

Przewijanie w kontrolce statycznych jest wyłączona, gdy nie jest widoczna na liście elementów (klawisze strzałek są wyłączone).

### <a name="example"></a>Przykład

  Zobacz przykład [CComboBox::GetExtendedUI](#getextendedui).

##  <a name="sethorizontalextent"></a>  CComboBox::SetHorizontalExtent

Określa szerokość w pikselach, za pomocą których część pola listy, pola kombi mogą być przewijane w poziomie.

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parametry

*nExtent*<br/>
Określa liczbę pikseli, za pomocą których część pola listy, pola kombi mogą być przewijane w poziomie.

### <a name="remarks"></a>Uwagi

Jeśli szerokość pola listy jest mniejszy niż ta wartość, poziomych pasków przewijania w poziomie przewinie elementy w polu listy. Jeśli szerokość pola listy jest równa lub większa od tej wartości, jest ukryty poziomych pasków przewijania lub, jeśli ma pola kombi [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu, wyłączona.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>  CComboBox::SetItemData

Ustawia wartość 32-bitowych, skojarzone z określonym elementem w polu kombi.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks elementu do ustawienia.

*dwItemData*<br/>
Zawiera nową wartość do skojarzenia z elementem.

### <a name="return-value"></a>Wartość zwracana

CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

Użyj `SetItemDataPtr` funkcja elementu członkowskiego, jeśli element 32-bitowych jest jako wskaźnik.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>  CComboBox::SetItemDataPtr

Ustawia wartość 32-bitowych, skojarzone z określonym elementem w polu kombi jako określony wskaźnik (**void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Zawiera liczony od zera indeks elementu.

*pData*<br/>
Zawiera wskaźnik do skojarzenia z elementem.

### <a name="return-value"></a>Wartość zwracana

CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

This, wskaźnik pozostaje ważny przez cały okres istnienia pola kombi, mimo że względne położenie elementu w obrębie pola kombi mogą ulec zmianie, ponieważ elementy są dodawane lub usuwane. W związku z tym można zmienić indeksu elementu w polu, ale wskaźnik pozostaje niezawodne.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>  CComboBox::SetItemHeight

Wywołaj `SetItemHeight` funkcję elementu członkowskiego, aby ustawić wysokość elementy listy w polu kombi lub wysokości kontrolki edycji (lub tekst statyczny) część pola kombi.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa, czy ustawiono wysokości elementów listy lub wysokości kontrolki edycji (lub tekst statyczny) część pola kombi.

Jeśli pole kombi [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu *nIndex* liczony od zera indeks elementu listy, których wysokość jest ustawiony; w przeciwnym razie Określa *nIndex* musi mieć wartość 0 i ustawi wysokość wszystkich elementów listy.

Jeśli *nIndex* jest -1, wysokość kontrolki edycji lub statyczna tekstowym pola kombi, można ustawić.

*cyItemHeight*<br/>
Określa wysokość w pikselach, identyfikowane za pomocą składnika pola kombi *nIndex*.

### <a name="return-value"></a>Wartość zwracana

CB_ERR, jeśli indeks lub wysokość jest nieprawidłowa; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wysokość kontrolki edycji (lub tekst statyczny) część pola kombi jest ustawiona, niezależnie od wysokości elementów listy. Aplikacja musi zapewnić, wysokość części kontrolki edycji (lub tekst statyczny) nie jest mniejszy niż wysokość elementu określonego pola listy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>  CComboBox::SetLocale

Określa identyfikator ustawień regionalnych dla tego pola kombi.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parametry

*nNewLocale*<br/>
Nowych ustawień regionalnych (LCID) wartość identyfikatora można ustawić dla tego pola kombi.

### <a name="return-value"></a>Wartość zwracana

Poprzednich ustawień regionalnych (LCID) wartość identyfikatora dla tego pola kombi.

### <a name="remarks"></a>Uwagi

Jeśli `SetLocale` nie jest wywoływana, domyślne ustawienia regionalne są uzyskiwane z systemu. To domyślne ustawienia regionalne systemu można modyfikować za pomocą Panelu sterowania aplikacji regionalne (lub International).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>  CComboBox::SetMinVisibleItems

Ustawia minimalną liczbę widocznych elementów na liście rozwijanej bieżącego kombi formantu pola.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*iMinVisible*|[in] Określa minimalną liczbę widocznych elementów.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda wysyła [CB_SETMINVISIBLE](/windows/desktop/Controls/cb-setminvisible) komunikat, który jest opisany w zestawie Windows SDK.

### <a name="example"></a>Przykład

Poniższy kod definiuje zmienną, *m_combobox*, która jest używana do uzyskania programowego dostępu formant pola kombi. Ta zmienna jest używana w następnym przykładzie.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu wstawia 20 elementów na liście rozwijanej kontrolki pola kombi. Następnie określa, że co najmniej 10 elementów mają być wyświetlane po naciśnięciu klawisza strzałki listy rozwijanej.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>  CComboBox::SetTopIndex

Zapewnia, że określonego elementu jest widoczny w polu listy części pola kombi.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Określa liczony od zera indeks elementu pola listy.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli kończy się pomyślnie, lub CB_ERR, jeśli wystąpi błąd.

### <a name="remarks"></a>Uwagi

System Przewija pola listy, aż do elementu określonego przez *nIndex* pojawia się w górnej części listy pola lub zakresu maksymalnego przewijania zostanie osiągnięty.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>  CComboBox::ShowDropDown

Pokazuje lub ukrywa pole listy pola kombi, która ma [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) lub [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parametry

*bShowIt*<br/>
Określa, czy pole listy rozwijanej jest widoczny, czy ukryty. Wartość TRUE zawiera pole listy. Wartość FALSE powoduje ukrycie pola listy.

### <a name="remarks"></a>Uwagi

Domyślnie pole kombi stylu tego wyświetli pole listy.

Ta funkcja elementu członkowskiego nie ma wpływu na utworzone za pomocą pola kombi [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) stylu.

### <a name="example"></a>Przykład

  Zobacz przykład [CComboBox::GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Zobacz też

[Próbki MFC CTRLBARS](../../visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Klasa CButton](../../mfc/reference/cbutton-class.md)<br/>
[Klasa CEdit](../../mfc/reference/cedit-class.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Klasa CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Klasa CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Klasa CDialog](../../mfc/reference/cdialog-class.md)
