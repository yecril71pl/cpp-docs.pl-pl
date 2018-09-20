---
title: Klasa CComboBoxEx | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0300bee10564209237e59ccfa48c14443ae3a90c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399993"
---
# <a name="ccomboboxex-class"></a>Klasa CComboBoxEx

Rozszerza formant pola kombi, umożliwiając obsługę list obrazów.

## <a name="syntax"></a>Składnia

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Konstruuje `CComboBoxEx` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|Tworzy pola kombi i dołącza je do `CComboBoxEx` obiektu.|
|[CComboBoxEx::CreateEx](#createex)|Tworzy pola kombi w określonym stylu rozszerzonej Windows i dołącza je do `ComboBoxEx` obiektu.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Usuwa element z `ComboBoxEx` kontroli.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Pobiera wskaźnik do kontrolki pola kombi podrzędnych.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Pobiera uchwyt do części kontrolki edycji `ComboBoxEx` kontroli.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Pobiera rozszerzone style, które są używane w `ComboBoxEx` kontroli.|
|[CComboBoxEx::GetImageList](#getimagelist)|Pobiera wskaźnik do listy obrazów przypisane do `ComboBoxEx` kontroli.|
|[CComboBoxEx::GetItem](#getitem)|Pobiera element informacje dotyczące danego `ComboBoxEx` elementu.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Określa, czy użytkownik zmienił zawartość `ComboBoxEx` formant edycji, wpisując polecenie.|
|[CComboBoxEx::InsertItem](#insertitem)|Wstawia nowy element w `ComboBoxEx` kontroli.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style w ramach `ComboBoxEx` kontroli.|
|[CComboBoxEx::SetImageList](#setimagelist)|Ustawia dla listy obrazów `ComboBoxEx` kontroli.|
|[CComboBoxEx::SetItem](#setitem)|Ustawia atrybuty dla elementu w `ComboBoxEx` kontroli.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Ustawia rozszerzone pole kombi stylu wizualnego formantu pola.|

## <a name="remarks"></a>Uwagi

Za pomocą `CComboBoxEx` utworzyć kombi formantów okna, nie potrzebujesz już zaimplementować swój własny obraz kodu rysowania. Zamiast tego należy użyć `CComboBoxEx` do dostępu do obrazów z listy obrazów.

## <a name="image-list-support"></a>Obsługa listy obrazów

W polu kombi standardowe właściciel pola kombi jest odpowiedzialne za narysowanie obrazu, tworząc pole kombi jako kontrolka rysowana przez właściciela. Kiedy używasz `CComboBoxEx`, nie trzeba ustawić rysowania Style CBS_OWNERDRAWFIXED i CBS_HASSTRINGS, ponieważ są one też dorozumianych. W przeciwnym razie trzeba napisać kod do wykonywania operacji rysowania. A `CComboBoxEx` kontrolka obsługuje maksymalnie trzy obrazy na element: jeden dla wybranego stanu: jeden dla stanu niezaznaczone i jeden do obrazu w nakładce.

## <a name="styles"></a>Style

`CComboBoxEx` obsługuje style CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST i WS_CHILD. Innymi stylami przekazane podczas tworzenia okna są ignorowane przez kontrolkę. Po utworzeniu okna, możesz podać inne pole kombi Style okna, wywołując `CComboBoxEx` funkcja elementu członkowskiego [SetExtendedStyle](#setextendedstyle). Przy użyciu tych stylów możesz wykonywać następujące czynności:

- Zestaw ciągów wyszukiwania na liście, aby być uwzględniana wielkość liter.

- Tworzenie kontrolki pola kombi używającej ukośnika ("/"), ukośnika odwrotnego ("\\") i okres (".") znaków w dwukropki programu word. Dzięki temu użytkownicy przejść z programu word do programu word, za pomocą skrótu klawiaturowego CTRL + Strzałka w.

- Ustaw kombi formant pola do wyświetlenia albo nie wyświetla obraz. Jeśli obraz nie jest wyświetlany, pole kombi usunąć wcięcia tekstu, która może pomieścić obrazu.

- Tworzenie kontrolki pola kombi wąskie, w tym jej rozmiaru, więc go przycina szersze pola kombi, które zawiera.

Flagi te style są dokładniejszym opisem zawartym w [korzystanie z CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Zachowanie elementu i atrybuty elementu wywołania zwrotnego

Informacje o elementach, takich jak indeksy dla elementów i obrazów, wartości wcięcia i ciągi tekstowe są przechowywane w strukturze Win32 [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema), zgodnie z opisem w zestawie Windows SDK. Struktura zawiera również elementy członkowskie, które odpowiadają flagi wywołania zwrotnego.

Omówienie szczegółowe, opisami pojęć, zobacz [korzystanie z CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

Wywołaj tę funkcję elementu członkowskiego, aby utworzyć `CComboBoxEx` obiektu.

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

Tworzy pola kombi i dołącza je do `CComboBoxEx` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa kombinację style pola kombi stosowane do pola kombi. Zobacz **uwagi** poniżej więcej informacji o stylach.

*Rect*<br/>
Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar pola kombi.

*pParentWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt okna nadrzędnego pola kombi (zazwyczaj `CDialog`). Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki pola kombi

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Utwórz `CComboBoxEx` obiektu w dwóch etapach:

1. Wywołaj [z CComboBoxEx](#ccomboboxex) do konstruowania `CComboBoxEx` obiektu.

1. Wywołanie tej funkcji elementu członkowskiego, który tworzy rozszerzonego pola kombi Windows i dołącza go do `CComboBoxEx` obiektu.

Gdy wywołujesz `Create`, MFC inicjuje wspólnych formantów.

Podczas tworzenia pola kombi, można określić dowolne lub wszystkie następujące style pola kombi:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Innymi stylami przekazane podczas tworzenia okna są ignorowane. `ComboBoxEx` Control obsługuje także rozszerzone style, które zapewniają dodatkowe funkcje. Te style są opisane w [ComboBoxEx kontrolować rozszerzone style](/windows/desktop/Controls/comboboxex-control-extended-styles), w zestawie Windows SDK. Ustaw te style, wywołując [SetExtendedStyle](#setextendedstyle).

Style rozszerzone systemu windows za pomocą formantu należy wywołać [CreateEx](#createex) zamiast `Create`.

##  <a name="createex"></a>  CComboBoxEx::CreateEx

Wywołaj tę funkcję, aby tworzenie formantu rozszerzonego pola kombi (okno podrzędne) i powiąż ją z `CComboBoxEx` obiektu.

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
Styl kontrolki pola kombi. Zobacz [Utwórz](#create) listę style.

*Rect*<br/>
Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.

*pParentWnd*<br/>
Wskaźnik do okna, które jest elementem nadrzędnym formantu.

*nID*<br/>
Identyfikator formantu okna podrzędnego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast `Create` do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.

`CreateEx` Tworzy formant z rozszerzone style Windows określonego przez *dwExStyle*. Należy ustawić rozszerzone style określone na Rozszerzone pole kombi pola kontrolkę za pomocą [SetExtendedStyle](#setextendedstyle). Na przykład użyć `CreateEx` Ustaw takie style jako WS_EX_CONTEXTHELP, ale korzystać z `SetExtendedStyle` do ustawiania tych stylów jako CBES_EX_CASESENSITIVE. Aby uzyskać więcej informacji, zobacz opisane w temacie style [style rozszerzone kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) w zestawie Windows SDK.

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

Usuwa element z `ComboBoxEx` kontroli.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Liczony od zera indeks elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które pozostały w formancie. Jeśli *iIndex* jest nieprawidłowy, funkcja zwraca CB_ERR.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcje komunikatu [CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem), zgodnie z opisem w zestawie Windows SDK. Gdy wywołujesz DeleteItem, [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) wiadomości z powiadomieniem CBEN_DELETEITEM będą wysyłane do okna nadrzędnego.

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do kontrolki pola kombi w `CComboBoxEx` obiektu.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CComboBox` obiektu.

### <a name="remarks"></a>Uwagi

`CComboBoxEx` Kontrola składa się z okna nadrzędnego, który hermetyzuje `CComboBox`.

`CComboBox` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i jest niszczony, podczas następnego przetwarzania bezczynności.

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do kontrolki edycji pola kombi.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CEdit](../../mfc/reference/cedit-class.md) obiektu.

### <a name="remarks"></a>Uwagi

A `CComboBoxEx` kontroli używa pole edycji, gdy zostanie utworzony przy użyciu stylu CBS_DROPDOWN.

`CEdit` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i jest niszczony, podczas następnego przetwarzania bezczynności.

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać rozszerzone stylów używanych dla `CComboBoxEx` kontroli.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD, który zawiera rozszerzone style, które są używane do kontrolki pola kombi.

### <a name="remarks"></a>Uwagi

Zobacz [style rozszerzone kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) w zestawie SDK Windows, aby uzyskać więcej informacji na temat tych stylów.

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać wskaźnik do listy obrazów, używane przez `CComboBoxEx` kontroli.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu. Jeśli nie powiedzie się, ta funkcja elementu członkowskiego zwraca wartość NULL.

### <a name="remarks"></a>Uwagi

`CImageList` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i jest niszczony, podczas następnego przetwarzania bezczynności.

##  <a name="getitem"></a>  CComboBoxEx::GetItem

Pobiera element informacje dotyczące danego `ComboBoxEx` elementu.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktury, który będzie otrzymywać informacje o elementach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiodła. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcje komunikatu [CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem), zgodnie z opisem w zestawie Windows SDK.

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

Określa, czy użytkownik zmienił zawartość `ComboBoxEx` formant edycji, wpisując polecenie.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli użytkownik wpisał w polu edycji dla formantu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcje komunikatu [CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged), zgodnie z opisem w zestawie Windows SDK.

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

Wstawia nowy element w `ComboBoxEx` kontroli.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktury, który będzie otrzymywać informacje o elementach. Ta struktura zawiera wartości flagi wywołania zwrotnego dla elementu.

### <a name="return-value"></a>Wartość zwracana

Indeks, w którym dodano nowy element w przypadku powodzenia; w przeciwnym razie wartość-1.

### <a name="remarks"></a>Uwagi

Gdy wywołujesz `InsertItem`, [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583) komunikatu o [CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem) zostanie wysłane powiadomienie do okna nadrzędnego.

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

Wywołaj tę funkcję elementu członkowskiego, aby ustawić rozszerzonej stylów używanych dla rozszerzony formant pola kombi.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parametry

*dwExMask*<br/>
Wartość DWORD, która wskazuje, style, które w *dwExStyles* są, których to dotyczy. Style rozszerzone w *dwExMask* zostaną zmienione. Innymi stylami zostanie zachowana, ponieważ jest. Jeśli ten parametr ma wartość zero, a następnie wszystkie style w *dwExStyles* zostaną zmienione.

*dwExStyles*<br/>
Wartość DWORD, który zawiera formant pola kombi rozszerzone style, które można ustawić dla formantu.

### <a name="return-value"></a>Wartość zwracana

Wartość DWORD zawiera rozszerzone style, które wcześniej używane dla formantu.

### <a name="remarks"></a>Uwagi

Zobacz [style rozszerzone kontrolki ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) w zestawie SDK Windows, aby uzyskać więcej informacji na temat tych stylów.

Aby utworzyć rozszerzony formant z windows rozszerzone style pola kombi, użyj [CreateEx](#createex).

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

Ustawia dla listy obrazów `ComboBoxEx` kontroli.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Wskaźnik do `CImageList` obiekt zawierający obrazy za pomocą `CComboBoxEx` kontroli.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt zawierający obrazy używanych wcześniej przez `CComboBoxEx` kontroli. Wartość NULL, jeśli uprzednio ustawioną nie listy obrazów.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcje komunikatu [CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist), zgodnie z opisem w zestawie Windows SDK. Jeśli zmienisz wysokość domyślny formant edycji, należy wywołać funkcję Win32 [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) zmiana rozmiaru formantu po wywołaniu metody `SetImageList`, lub nie będzie on wyświetlany poprawnie.

`CImageList` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i jest niszczony, podczas następnego przetwarzania bezczynności.

##  <a name="setitem"></a>  CComboBoxEx::SetItem

Ustawia atrybuty dla elementu w `ComboBoxEx` kontroli.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parametry

*pCBItem*<br/>
Wskaźnik do [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) struktury, który będzie otrzymywać informacje o elementach.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja się powiodła. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje funkcje komunikatu [CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

Ustawia rozszerzone pole kombi stylu wizualnego formantu pola.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parametry

*pszSubAppName*<br/>
Wskaźnik do ciągu Unicode, który zawiera rozszerzone pole kombi stylu wizualnego pole można ustawić.

### <a name="return-value"></a>Wartość zwracana

Zwracana wartość nie jest używana.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska emuluje funkcjonalność [CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme) komunikat, zgodnie z opisem w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Próbki MFC MFCIE](../../visual-cpp-samples.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)
