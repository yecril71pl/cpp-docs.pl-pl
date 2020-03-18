---
title: Klasa korzystanie CComboBoxEx
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
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420513"
---
# <a name="ccomboboxex-class"></a>Klasa korzystanie CComboBoxEx

Rozszerza formant pola kombi, dostarczając obsługę list obrazów.

## <a name="syntax"></a>Składnia

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CComboBoxEx:: Korzystanie CComboBoxEx](#ccomboboxex)|Konstruuje obiekt `CComboBoxEx`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Korzystanie CComboBoxEx:: Create](#create)|Tworzy pole kombi i dołącza je do obiektu `CComboBoxEx`.|
|[Korzystanie CComboBoxEx:: CreateEx](#createex)|Tworzy pole kombi z określonymi stylami rozszerzonymi systemu Windows i dołącza je do obiektu `ComboBoxEx`.|
|[Korzystanie CComboBoxEx::D eleteItem](#deleteitem)|Usuwa element z kontrolki `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: GetComboBoxCtrl](#getcomboboxctrl)|Pobiera wskaźnik do formantu podrzędnego pola kombi.|
|[Korzystanie CComboBoxEx:: GetEditCtrl](#geteditctrl)|Pobiera uchwyt do części kontrolki Edycja kontrolki `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: getextendeds](#getextendedstyle)|Pobiera rozszerzone style, które są używane dla kontrolki `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: GetImageList](#getimagelist)|Pobiera wskaźnik do listy obrazów przypisanej do kontrolki `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: GetItem](#getitem)|Pobiera informacje o elemencie dla danego elementu `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: HasEditChanged](#haseditchanged)|Określa, czy użytkownik zmienił zawartość kontrolki edycji `ComboBoxEx`, wpisując ciąg.|
|[Korzystanie CComboBoxEx:: InsertItem](#insertitem)|Wstawia nowy element w kontrolce `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: setextended](#setextendedstyle)|Ustawia style rozszerzone w kontrolce `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: SetImageList](#setimagelist)|Ustawia listę obrazów dla kontrolki `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: SetItem](#setitem)|Ustawia atrybuty dla elementu w kontrolce `ComboBoxEx`.|
|[Korzystanie CComboBoxEx:: SetWindowTheme](#setwindowtheme)|Ustawia styl wizualizacji rozszerzonej kontrolki pola kombi.|

## <a name="remarks"></a>Uwagi

Przy użyciu `CComboBoxEx` do tworzenia kontrolek pola kombi nie jest już konieczne implementowanie własnego kodu rysowania obrazu. Zamiast tego użyj `CComboBoxEx`, aby uzyskać dostęp do obrazów z listy obrazów.

## <a name="image-list-support"></a>Obsługa listy obrazów

W standardowym polu kombi właściciel pola kombi jest odpowiedzialny za Rysowanie obrazu przez utworzenie pola kombi jako formantu rysowania przez właściciela. Gdy używasz `CComboBoxEx`, nie musisz ustawiać stylów rysowania CBS_OWNERDRAWFIXED i CBS_HASSTRINGS, ponieważ są one implikowane. W przeciwnym razie musisz napisać kod, aby wykonać operacje rysowania. Kontrolka `CComboBoxEx` obsługuje maksymalnie trzy obrazy na element: jeden dla wybranego stanu, jeden dla niezaznaczonego stanu i jeden dla obrazu nakładki.

## <a name="styles"></a>Style

`CComboBoxEx` obsługuje style CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST i WS_CHILD. Wszystkie inne style przenoszone podczas tworzenia okna są ignorowane przez formant. Po utworzeniu okna można podać inne style pola kombi, wywołując funkcję elementu członkowskiego `CComboBoxEx` [setextended](#setextendedstyle). Za pomocą tych stylów można:

- Ustaw wyszukiwanie ciągów na liście, aby uwzględniać wielkość liter.

- Utwórz kontrolkę pole kombi, która używa ukośnika ("/"), ukośnika odwrotnego ("\\") i kropki (".") jako ograniczników wyrazów. Pozwala to użytkownikom na przechodzenie z programu Word do programu Word przy użyciu skrótu klawiaturowego CTRL + STRZAŁKA.

- Ustaw kontrolkę pole kombi na wyświetlaną lub niewyświetlaną obrazu. Jeśli obraz nie jest wyświetlany, pole kombi może usunąć wcięcie tekstu, które posłuży do obrazu.

- Utwórz formant wąskiego pola kombi, w tym jego rozmiar, tak aby zawierał szersze pole kombi.

Te flagi stylu są opisane w dalszej [postaci przy użyciu korzystanie CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Przechowywanie elementów i atrybuty elementu wywołania zwrotnego

Informacje o elementach, takie jak indeksy dla elementów i obrazów, wartości wcięć i ciągi tekstowe, są przechowywane w strukturze Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), zgodnie z opisem w Windows SDK. Struktura zawiera również elementy członkowskie, które odnoszą się do flag wywołania zwrotnego.

Aby uzyskać szczegółowe omówienie pojęć, zobacz [using korzystanie CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

##  <a name="ccomboboxex"></a>Korzystanie CComboBoxEx:: Korzystanie CComboBoxEx

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć obiekt `CComboBoxEx`.

```
CComboBoxEx();
```

##  <a name="create"></a>Korzystanie CComboBoxEx:: Create

Tworzy pole kombi i dołącza je do obiektu `CComboBoxEx`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa kombinację stylów pól kombi zastosowanych do pola kombi. Zobacz **uwagi** poniżej, aby uzyskać więcej informacji na temat stylów.

*cinania*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , który jest pozycją i rozmiarem pola kombi.

*pParentWnd*<br/>
Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) , który jest oknem nadrzędnym pola kombi (zwykle jest to `CDialog`). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki pola kombi.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli obiekt został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Utwórz obiekt `CComboBoxEx` w dwóch krokach:

1. Wywołaj [Korzystanie CComboBoxEx](#ccomboboxex) w celu skonstruowania obiektu `CComboBoxEx`.

1. Wywołaj tę funkcję elementu członkowskiego, co spowoduje utworzenie rozszerzonego pola kombi systemu Windows i dołączenie go do obiektu `CComboBoxEx`.

Podczas wywoływania `Create`MFC inicjuje formanty standardowe.

Po utworzeniu pola kombi można określić dowolne lub wszystkie następujące style pola kombi:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Wszystkie inne style przenoszone podczas tworzenia okna zostaną zignorowane. Kontrolka `ComboBoxEx` obsługuje również rozszerzone style, które udostępniają dodatkowe funkcje. Te [Style są opisane w Windows SDK](/windows/win32/Controls/comboboxex-control-extended-styles). Ustaw te style, wywołując metodę [setextended](#setextendedstyle).

Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką, wywołaj [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>Korzystanie CComboBoxEx:: CreateEx

Wywołaj tę funkcję, aby utworzyć kontrolkę rozszerzonego pola kombi (okno podrzędne) i skojarzyć ją z obiektem `CComboBoxEx`.

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
Styl kontrolki pola kombi. Aby uzyskać listę stylów, zobacz temat [Tworzenie](#create) .

*cinania*<br/>
Odwołanie do struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) opisujące rozmiar i położenie okna, które ma zostać utworzone, we współrzędnych klienta *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator okna podrzędnego kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast `Create` do zastosowania rozszerzonych stylów systemu Windows, określonych przez **WS_EX_** wstępny stylu systemu Windows.

`CreateEx` tworzy formant przy użyciu rozszerzonych stylów systemu Windows określonych przez *dwExStyle*. Należy ustawić style rozszerzone charakterystyczne dla rozszerzonej kontrolki pola kombi przy użyciu metody [setextended](#setextendedstyle). Na przykład użyj `CreateEx`, aby ustawić takie style jako WS_EX_CONTEXTHELP, ale Użyj `SetExtendedStyle` do ustawienia takich stylów jako CBES_EX_CASESENSITIVE. Aby uzyskać więcej informacji, zobacz Style opisane w temacie [ComboBoxEx Control style rozszerzone](/windows/win32/Controls/comboboxex-control-extended-styles) w Windows SDK.

##  <a name="deleteitem"></a>Korzystanie CComboBoxEx::D eleteItem

Usuwa element z kontrolki `ComboBoxEx`.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Indeks elementu, który ma zostać usunięty (liczony od zera).

### <a name="return-value"></a>Wartość zwrócona

Liczba pozostałych elementów w formancie. Jeśli *IIndex* jest nieprawidłowy, funkcja zwraca CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje funkcjonalność [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)komunikatu, zgodnie z opisem w Windows SDK. Po wywołaniu DeleteItem komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) z powiadomieniem CBEN_DELETEITEM zostanie wysłany do okna nadrzędnego.

##  <a name="getcomboboxctrl"></a>Korzystanie CComboBoxEx:: GetComboBoxCtrl

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do kontrolki pola kombi w obrębie obiektu `CComboBoxEx`.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `CComboBox`.

### <a name="remarks"></a>Uwagi

Kontrolka `CComboBoxEx` składa się z okna nadrzędnego, które hermetyzuje `CComboBox`.

Obiekt `CComboBox` wskazywany przez wartość zwracaną jest obiektem tymczasowym i jest niszczony podczas następnego czasu bezczynności przetwarzania.

##  <a name="geteditctrl"></a>Korzystanie CComboBoxEx:: GetEditCtrl

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do kontrolki edycji pola kombi.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [CEdit](../../mfc/reference/cedit-class.md) .

### <a name="remarks"></a>Uwagi

Kontrolka `CComboBoxEx` używa pola edycji podczas tworzenia z stylem CBS_DROPDOWN.

Obiekt `CEdit` wskazywany przez wartość zwracaną jest obiektem tymczasowym i jest niszczony podczas następnego czasu bezczynności przetwarzania.

##  <a name="getextendedstyle"></a>Korzystanie CComboBoxEx:: getextendeds

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać style rozszerzone używane dla kontrolki `CComboBoxEx`.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wartość DWORD, która zawiera rozszerzone style, które są używane dla kontrolki pole kombi.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o tych stylach, zobacz [ComboBoxEx Control extended style](/windows/win32/Controls/comboboxex-control-extended-styles) w Windows SDK.

##  <a name="getimagelist"></a>Korzystanie CComboBoxEx:: GetImageList

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do listy obrazów używanej przez formant `CComboBoxEx`.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) . Jeśli to się nie powiedzie, funkcja członkowska zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

Obiekt `CImageList` wskazywany przez wartość zwracaną jest obiektem tymczasowym i jest niszczony podczas następnego czasu bezczynności przetwarzania.

##  <a name="getitem"></a>Korzystanie CComboBoxEx:: GetItem

Pobiera informacje o elemencie dla danego elementu `ComboBoxEx`.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , która będzie odbierać informacje o elemencie.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje funkcjonalność [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)komunikatu, zgodnie z opisem w Windows SDK.

##  <a name="haseditchanged"></a>Korzystanie CComboBoxEx:: HasEditChanged

Określa, czy użytkownik zmienił zawartość kontrolki edycji `ComboBoxEx`, wpisując ciąg.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli użytkownik wpisze pole edycji kontrolki; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje funkcjonalność [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)komunikatu, zgodnie z opisem w Windows SDK.

##  <a name="insertitem"></a>Korzystanie CComboBoxEx:: InsertItem

Wstawia nowy element w kontrolce `ComboBoxEx`.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , która będzie odbierać informacje o elemencie. Ta struktura zawiera wartości flag wywołania zwrotnego dla elementu.

### <a name="return-value"></a>Wartość zwrócona

Indeks, w którym wstawiono nowy element w przypadku powodzenia; w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

Gdy wywołasz `InsertItem`, komunikat [WM_NOTIFY](/windows/win32/controls/wm-notify) z powiadomieniem o [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) zostanie wysłany do okna nadrzędnego.

##  <a name="setextendedstyle"></a>Korzystanie CComboBoxEx:: setextended

Wywołaj tę funkcję elementu członkowskiego, aby ustawić style rozszerzone używane dla rozszerzonej kontrolki pola kombi.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMask*<br/>
Wartość DWORD wskazująca, których stylów w *dwExStyles* mają dotyczyć. Tylko style rozszerzone w *dwExMask* zostaną zmienione. Wszystkie inne style będą utrzymywane w postaci, w jakiej jest. Jeśli ten parametr ma wartość zero, wpłynie to na wszystkie style w *dwExStyles* .

*dwExStyles*<br/>
Wartość DWORD, która zawiera rozszerzone style kontrolki pola kombi do ustawienia dla kontrolki.

### <a name="return-value"></a>Wartość zwrócona

Wartość DWORD, która zawiera style rozszerzone wcześniej używane dla formantu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o tych stylach, zobacz [ComboBoxEx Control extended style](/windows/win32/Controls/comboboxex-control-extended-styles) w Windows SDK.

Aby utworzyć rozszerzoną kontrolkę pola kombi z rozszerzonymi stylami systemu Windows, użyj [CreateEx](#createex).

##  <a name="setimagelist"></a>Korzystanie CComboBoxEx:: SetImageList

Ustawia listę obrazów dla kontrolki `ComboBoxEx`.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Wskaźnik do obiektu `CImageList` zawierającego obrazy do użycia z kontrolką `CComboBoxEx`.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu [Korzystanie CImageList](../../mfc/reference/cimagelist-class.md) zawierającego obrazy używane wcześniej przez formant `CComboBoxEx`. Wartość NULL, jeśli nie ustawiono wcześniej listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje funkcjonalność [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)komunikatu, zgodnie z opisem w Windows SDK. Jeśli zmienisz wysokość domyślnej kontrolki edycji, wywołaj funkcję Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) , aby zmienić rozmiar kontrolki po wywołaniu `SetImageList`lub nie będzie ona wyświetlana prawidłowo.

Obiekt `CImageList` wskazywany przez wartość zwracaną jest obiektem tymczasowym i jest niszczony podczas następnego czasu bezczynności przetwarzania.

##  <a name="setitem"></a>Korzystanie CComboBoxEx:: SetItem

Ustawia atrybuty dla elementu w kontrolce `ComboBoxEx`.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do struktury [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) , która będzie odbierać informacje o elemencie.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli operacja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje funkcjonalność [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)komunikatu, zgodnie z opisem w Windows SDK.

##  <a name="setwindowtheme"></a>Korzystanie CComboBoxEx:: SetWindowTheme

Ustawia styl wizualizacji rozszerzonej kontrolki pola kombi.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Wskaźnik do ciągu Unicode, który zawiera rozszerzony styl wizualny pola kombi do ustawienia.

### <a name="return-value"></a>Wartość zwrócona

Wartość zwracana nie jest używana.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność komunikatu [CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme) , zgodnie z opisem w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Przykład MFCIE MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)
