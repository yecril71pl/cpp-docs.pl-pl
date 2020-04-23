---
title: Klasa CComboBoxEx
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754824"
---
# <a name="ccomboboxex-class"></a>Klasa CComboBoxEx

Rozszerza formant pola kombi, zapewniając obsługę list obrazów.

## <a name="syntax"></a>Składnia

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Konstruuje `CComboBoxEx` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBoxEx::Tworzenie](#create)|Tworzy pole kombi i dołącza `CComboBoxEx` je do obiektu.|
|[CComboBoxEx::CreateEx](#createex)|Tworzy pole kombi z określonymi stylami rozszerzonymi `ComboBoxEx` systemu Windows i dołącza je do obiektu.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Usuwa element z `ComboBoxEx` formantu.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Pobiera wskaźnik do kontrolki pola kombi podrzędnej.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Pobiera dojście do części formantu edycji `ComboBoxEx` formantu.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są `ComboBoxEx` używane dla formantu.|
|[CComboBoxEx::Lista GetImage](#getimagelist)|Pobiera wskaźnik do listy obrazów przypisanych `ComboBoxEx` do formantu.|
|[CComboBoxEx::GetItem](#getitem)|Pobiera informacje o elemencie dla danego `ComboBoxEx` elementu.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Określa, czy użytkownik zmienił zawartość `ComboBoxEx` formantu edycji, wpisując tekst.|
|[CComboBoxEx::InsertItem](#insertitem)|Wstawia nowy element `ComboBoxEx` w formancie.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style `ComboBoxEx` w formancie.|
|[CComboBoxEx::SetImageList](#setimagelist)|Ustawia listę obrazów `ComboBoxEx` dla formantu.|
|[CComboBoxEx::SetItem](#setitem)|Ustawia atrybuty elementu w `ComboBoxEx` formancie.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny kontrolki rozszerzonego pola kombi.|

## <a name="remarks"></a>Uwagi

Za `CComboBoxEx` pomocą do tworzenia formantów pola kombi, nie trzeba już zaimplementować własny kod rysunku obrazu. Zamiast tego `CComboBoxEx` należy użyć dostępu do obrazów z listy obrazów.

## <a name="image-list-support"></a>Obsługa listy obrazów

W standardowym polu kombi właściciel pola kombi jest odpowiedzialny za rysowanie obrazu przez utworzenie pola kombi jako kontrolki rysowania przez właściciela. Podczas korzystania `CComboBoxEx`z programu nie trzeba ustawiać stylów rysunku CBS_OWNERDRAWFIXED i CBS_HASSTRINGS, ponieważ są one implikowane. W przeciwnym razie należy napisać kod do wykonywania operacji rysowania. Formant `CComboBoxEx` obsługuje maksymalnie trzy obrazy na element: jeden dla wybranego stanu, jeden dla stanu niezaznaczone i jeden dla obrazu nakładki.

## <a name="styles"></a>Style

`CComboBoxEx`obsługuje style CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST i WS_CHILD. Wszystkie inne style przekazywane podczas tworzenia okna są ignorowane przez formant. Po utworzeniu okna można podać inne style pola `CComboBoxEx` kombi, wywołując funkcję elementu członkowskiego [SetExtendedStyle](#setextendedstyle). Dzięki tym stylom możesz:

- Ustaw wyszukiwanie ciągów na liście, aby mieć rozróżnianą wielkość liter.

- Utwórz formant pola kombi, który używa znaków ukośnika ('/'), ukośnika odwrotnego ('\\i kropki ('.') jako ograniczników wyrazów. Dzięki temu użytkownicy mogą przechodzić ze słowa do wyrazu za pomocą skrótu klawiaturowego CTRL+ ARROW.

- Ustaw kontrolkę pola kombi, aby wyświetlać lub nie wyświetlać obrazu. Jeśli obraz nie jest wyświetlany, pole kombi może usunąć wcięcie tekstu, które obsługuje obraz.

- Utwórz wąską kontrolkę pola kombi, w tym rozmiar, aby przycinał szersze pole kombi, które zawiera.

Te flagi stylu są opisane dalej w [użyciu CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Atrybuty przechowywania elementów i oddzwaniania

Informacje o elementach, takie jak indeksy elementów i obrazów, wartości wcięci i ciągi tekstowe, są przechowywane w strukturze Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), zgodnie z opisem w zestawie Windows SDK. Struktura zawiera również elementy członkowskie, które odpowiadają flagi wywołania zwrotnego.

Aby uzyskać szczegółową, koncepcyjną dyskusję, zobacz [Korzystanie z CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccombobox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx

Wywołanie tej funkcji `CComboBoxEx` elementu członkowskiego, aby utworzyć obiekt.

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx::Tworzenie

Tworzy pole kombi i dołącza `CComboBoxEx` je do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa kombinację stylów pola kombi zastosowanych do pola kombi. Zobacz **Uwagi poniżej,** aby uzyskać więcej informacji na temat stylów.

*Rect*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [RECT](/windows/win32/api/windef/ns-windef-rect) struktury, która jest położenie i rozmiar pola kombi.

*pParentWnd*<br/>
Wskaźnik do [obiektu CWnd,](../../mfc/reference/cwnd-class.md) który jest nadrzędnym oknem `CDialog`pola kombi (zwykle ). Nie może być null.

*Nid*<br/>
Określa identyfikator formantu pola kombi.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt został pomyślnie utworzony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Utwórz `CComboBoxEx` obiekt w dwóch krokach:

1. Wywołanie [CComboBoxEx](#ccomboboxex) `CComboBoxEx` do konstruowania obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, która tworzy rozszerzone pole `CComboBoxEx` kombi systemu Windows i dołącza go do obiektu.

Podczas wywoływania, `Create`MFC inicjuje typowe formanty.

Podczas tworzenia pola kombi można określić dowolny lub wszystkie z następujących stylów pola kombi:

- CBS_SIMPLE

- CBS_DROPDOWN

- Cbs_dropdownlist

- CBS_AUTOHSCROLL

- Ws_child

Wszystkie inne style przekazywane podczas tworzenia okna są ignorowane. Formant `ComboBoxEx` obsługuje również rozszerzone style, które zapewniają dodatkowe funkcje. Style te są opisane w [ComboBoxEx kontroli rozszerzone style,](/windows/win32/Controls/comboboxex-control-extended-styles)w windows SDK. Ustaw te style, wywołując [SetExtendedStyle](#setextendedstyle).

Jeśli chcesz używać rozszerzonych stylów okien z formantem, zadzwoń [do CreateEx](#createex) zamiast `Create`.

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx::CreateEx

Wywołanie tej funkcji, aby utworzyć rozszerzony formant pola kombi `CComboBoxEx` (okno podrzędne) i skojarzyć go z obiektem.

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
Styl kontrolki pola kombi. Zobacz [Tworzenie](#create) listy stylów.

*Rect*<br/>
Odwołanie do struktury [RECT](/windows/win32/api/windef/ns-windef-rect) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest nadrzędnym formantu.

*Nid*<br/>
Identyfikator okna podrzędnego formantu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zamiast stosować rozszerzone style systemu Windows określone przez przedmową w stylu rozszerzonym systemu Windows WS_EX_ . **WS_EX_** `CreateEx` `Create`

`CreateEx`tworzy formant z rozszerzonymi stylami systemu Windows określonymi przez *dwExStyle*. Za pomocą [SetExtendedStyle](#setextendedstyle)należy ustawić style rozszerzone specyficzne dla rozszerzonego pola kombi. Na przykład `CreateEx` można użyć do ustawiania takich stylów, jak WS_EX_CONTEXTHELP, ale służy `SetExtendedStyle` do ustawiania takich stylów, jak CBES_EX_CASESENSITIVE. Aby uzyskać więcej informacji, zobacz style opisane w temacie [Style rozszerzone sterowania kontrolkią ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) w zestaw windows SDK.

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::DeleteItem

Usuwa element z `ComboBoxEx` formantu.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
Indeks od zera elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów pozostałych w formancie. Jeśli *iIndex* jest nieprawidłowy, funkcja zwraca CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcjonalność komunikatu [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem), zgodnie z opisem w windows SDK. Po wywołaniu DeleteItem, [WM_NOTIFY](/windows/win32/controls/wm-notify) wiadomość z powiadomieniem CBEN_DELETEITEM zostanie wysłana do okna nadrzędnego.

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać `CComboBoxEx` wskaźnik do kontrolki pola kombi w obiekcie.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CComboBox` obiektu.

### <a name="remarks"></a>Uwagi

Formant `CComboBoxEx` składa się z okna nadrzędnego, `CComboBox`które hermetyzuje .

Obiekt `CComboBox` wskazywalny przez zwracaną wartość jest obiektem tymczasowym i jest niszczony podczas następnego czasu przetwarzania bezczynnego.

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać wskaźnik do formantu edycji dla pola kombi.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CEdit.](../../mfc/reference/cedit-class.md)

### <a name="remarks"></a>Uwagi

Formant `CComboBoxEx` używa pola edycji podczas tworzenia przy użyciu stylu CBS_DROPDOWN.

Obiekt `CEdit` wskazywalny przez zwracaną wartość jest obiektem tymczasowym i jest niszczony podczas następnego czasu przetwarzania bezczynnego.

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle

Wywołanie tej funkcji elementu członkowskiego, aby `CComboBoxEx` uzyskać rozszerzone style używane dla formantu.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD, która zawiera rozszerzone style, które są używane dla formantu pola kombi.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Style rozszerzone kontrolki kontrolki ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) w zestaw windows SDK.

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx::Lista GetImage

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać `CComboBoxEx` wskaźnik do listy obrazów używane przez formant.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [obiektu CImageList.](../../mfc/reference/cimagelist-class.md) Jeśli to się nie powiedzie, ta funkcja elementu członkowskiego zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Obiekt `CImageList` wskazywalny przez zwracaną wartość jest obiektem tymczasowym i jest niszczony podczas następnego czasu przetwarzania bezczynnego.

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx::GetItem

Pobiera informacje o elemencie dla danego `ComboBoxEx` elementu.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) która otrzyma informacje o elemencie.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcjonalność [komunikatu CBEM_GETITEM](/windows/win32/Controls/cbem-getitem), zgodnie z opisem w windows SDK.

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::HasEditChanged

Określa, czy użytkownik zmienił zawartość `ComboBoxEx` formantu edycji, wpisując tekst.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik wpisał w polu edycji formantu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcjonalność komunikatu [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged), zgodnie z opisem w windows SDK.

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx::InsertItem

Wstawia nowy element `ComboBoxEx` w formancie.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) która otrzyma informacje o elemencie. Ta struktura zawiera wartości flag wywołania zwrotnego dla elementu.

### <a name="return-value"></a>Wartość zwracana

Indeks, w którym nowy element został wstawiony, jeśli zakończy się pomyślnie; w przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

Podczas rozmowy `InsertItem`do okna nadrzędnego zostanie wysłana wiadomość [WM_NOTIFY](/windows/win32/controls/wm-notify) z powiadomieniem [CBEN_INSERTITEM.](/windows/win32/Controls/cben-insertitem)

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle

Wywołanie tej funkcji elementu członkowskiego, aby ustawić rozszerzone style używane dla kontrolki rozszerzonej pola kombi.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMask (maseczka dwEx)*<br/>
Wartość DWORD, która wskazuje, które style w *dwExStyles* mają mieć wpływ. Zmienią się tylko rozszerzone style w *dwExMask.* Wszystkie inne style zostaną zachowane w stanie, w jakim jest. Jeśli ten parametr wynosi zero, to wszystkie style w *dwExStyles* będzie miało wpływ.

*dwExStyles (Np.*<br/>
Wartość DWORD, która zawiera pole kombi rozszerzone style, aby ustawić dla formantu.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD, która zawiera rozszerzone style wcześniej używane dla formantu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat tych stylów, zobacz [Style rozszerzone kontrolki kontrolki ComboBoxEx](/windows/win32/Controls/comboboxex-control-extended-styles) w zestaw windows SDK.

Aby utworzyć formant rozszerzony pola kombi z rozszerzonymi stylami okien, użyj [createex](#createex).

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::SetImageList

Ustawia listę obrazów `ComboBoxEx` dla formantu.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList (Lista pImage)*<br/>
Wskaźnik do `CImageList` obiektu zawierającego obrazy do `CComboBoxEx` użycia z formantem.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu zawierającego obrazy wcześniej `CComboBoxEx` używane przez formant. NULL, jeśli wcześniej nie ustawiono żadnej listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcjonalność komunikatu [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist), zgodnie z opisem w windows SDK. Jeśli zmienisz wysokość domyślnego formantu edycji, zadzwoń do funkcji Win32 [SetWindowPos,](/windows/win32/api/winuser/nf-winuser-setwindowpos) aby ponownie zmienić formant po wywołaniu `SetImageList`lub nie będzie ona wyświetlana poprawnie.

Obiekt `CImageList` wskazywalny przez zwracaną wartość jest obiektem tymczasowym i jest niszczony podczas następnego czasu przetwarzania bezczynnego.

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx::SetItem

Ustawia atrybuty elementu w `ComboBoxEx` formancie.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM,](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) która otrzyma informacje o elemencie.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcjonalność komunikatu [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem), zgodnie z opisem w windows SDK.

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme

Ustawia styl wizualny kontrolki rozszerzonego pola kombi.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Wskaźnik do ciągu Unicode, który zawiera rozszerzony styl wizualny pola kombi do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość nie jest używana.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego emuluje funkcjonalność [komunikatu CBEM_SETWINDOWTHEME,](/windows/win32/Controls/cbem-setwindowtheme) zgodnie z opisem w windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykładowe MFCIE MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)
