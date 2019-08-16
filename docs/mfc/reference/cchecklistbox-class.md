---
title: Klasa CCheckListBox
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: f8c725ea30754a42ce3045f1160b7a09c4481e39
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507351"
---
# <a name="cchecklistbox-class"></a>Klasa CCheckListBox

Oferuje funkcje pola listy kontrolnej systemu Windows.

## <a name="syntax"></a>Składnia

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Konstruuje `CCheckListBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCheckListBox:: Create](#create)|Tworzy pole listy kontrolnej systemu Windows i dołącza je do `CCheckListBox` obiektu.|
|[CCheckListBox::D rawItem](#drawitem)|Wywoływane przez platformę, gdy wizualny aspekt pola listy rysowania przez właściciela zmienia się.|
|[CCheckListBox:: Enable](#enable)|Włącza lub wyłącza element pola listy kontrolnej.|
|[CCheckListBox::GetCheck](#getcheck)|Pobiera stan pola wyboru elementu.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Pobiera styl pól wyboru kontrolki.|
|[CCheckListBox::IsEnabled](#isenabled)|Określa, czy element jest włączony.|
|[CCheckListBox::MeasureItem](#measureitem)|Wywoływane przez platformę, gdy zostanie utworzony pole listy z stylem rysowania przez właściciela.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Wywoływane przez platformę, aby uzyskać pozycję pola wyboru elementu.|
|[CCheckListBox::SetCheck](#setcheck)|Ustawia stan pola wyboru elementu.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Ustawia styl pól wyboru kontrolki.|

## <a name="remarks"></a>Uwagi

"Pole listy kontrolnej" wyświetla listę elementów, takich jak filename. Każdy element na liście ma pole wyboru obok niego, które użytkownik może sprawdzić lub wyczyścić.

`CCheckListBox`jest tylko dla kontrolek rysowanych przez właściciela, ponieważ lista zawiera więcej niż ciągi tekstowe. W najprostszej postaci pole listy kontrolnej zawiera ciągi tekstowe i pola wyboru, ale w ogóle nie trzeba mieć tekstu. Na przykład można mieć listę małych map bitowych z polem wyboru obok każdego elementu.

Aby utworzyć własne pole listy kontrolnej, należy uzyskać własną klasę z `CCheckListBox`. Aby utworzyć własną klasę, napisz konstruktora dla klasy pochodnej, a następnie Wywołaj `Create`.

Jeśli chcesz obsługiwać komunikaty powiadomień systemu Windows wysyłane przez pole listy do jego elementu nadrzędnego (zazwyczaj klasy pochodnej z [CDialog](../../mfc/reference/cdialog-class.md)), Dodaj wpis mapy komunikatów i funkcję elementu członkowskiego obsługi komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów przyjmuje następującą formę:

**On\_** _Notification_ **(** _ID_, _memberFxn_ **)**

gdzie `id` określa identyfikator okna podrzędnego kontrolki wysyłającej powiadomienie i `memberFxn` jest nazwą nadrzędnej funkcji członkowskiej, która została zapisywana w celu obsługi powiadomienia.

Prototyp funkcji elementu nadrzędnego jest następujący:

`afx_msg void memberFxn();`

Istnieje tylko jeden wpis mapy komunikatów odnoszący się do programu `CCheckListBox` (ale Zobacz również wpisy mapy komunikatów dla [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE, że użytkownik zmienił stan pola wyboru elementu.

Jeśli pole listy kontrolnej jest domyślnym polem listy kontrolnej (lista ciągów z domyślnymi polami pola wyboru po lewej stronie każdego), można użyć domyślnego [CCheckListBox::D rawitem](#drawitem) do narysowania pola listy kontrolnej. W przeciwnym razie należy zastąpić funkcję [CListBox:: CompareItem](../../mfc/reference/clistbox-class.md#compareitem) i [CCheckListBox::D rawitem](#drawitem) i [CCheckListBox:: MeasureItem](#measureitem) Functions.

Pole listy kontrolnej można utworzyć na podstawie szablonu okna dialogowego lub bezpośrednio w kodzie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Konstruuje `CCheckListBox` obiekt.

```
CCheckListBox();
```

### <a name="remarks"></a>Uwagi

`CCheckListBox` Obiekt jest konstruowany w dwóch krokach. Najpierw Zdefiniuj klasę pochodną `CCheckListBox`, a następnie Wywołaj `Create`, która inicjuje pole listy kontrolnej systemu Windows i `CCheckListBox` dołącza go do obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox:: Create

Tworzy pole listy kontrolnej systemu Windows i dołącza je do `CCheckListBox` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola listy kontrolnej. Styl musi być LBS_HASSTRINGS i LBS_OWNERDRAWFIXED (wszystkie elementy na liście mają taką samą wysokość) lub LBS_OWNERDRAWVARIABLE (elementy na liście są o różnej wysokości). Ten styl można łączyć z innymi [stylami pól listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , z wyjątkiem LBS_USETABSTOPS.

*cinania*<br/>
Określa rozmiar i położenie pola listy kontrolnej. Może być obiektem [CRect](../../atl-mfc-shared/reference/crect-class.md) lub strukturą [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Określa okno nadrzędne pola listy kontrolnej (zazwyczaj `CDialog` obiekt). Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator formantu pola listy kontrolnej.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`CCheckListBox` Obiekt jest konstruowany w dwóch krokach. Najpierw Zdefiniuj klasę pochodną od `CcheckListBox` , a następnie Wywołaj `Create`, która inicjuje pole listy kontrolnej systemu Windows i `CCheckListBox`dołącza go do. Aby uzyskać przykład, zobacz [CCheckListBox:: CCheckListBox](#cchecklistbox) .

Gdy `Create` jest wykonywane, system Windows wysyła komunikaty [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do kontrolki pole listy kontrolnej.

Te komunikaty są domyślnie obsługiwane przez funkcje elementu członkowskiego [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), OnCreate, [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) w `CWnd` klasie bazowej. [](../../mfc/reference/cwnd-class.md#oncreate) Aby zwiększyć domyślną obsługę komunikatów, Dodaj mapę komunikatów do klasy pochodnej i Przesłoń poprzednie funkcje składowe programu obsługi komunikatów. Przesłoń `OnCreate`, na przykład, aby wykonać wymaganą inicjalizację dla nowej klasy.

Zastosuj następujące [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pole listy kontrolnej:

- WS_CHILD zawsze

- WS_VISIBLE zazwyczaj

- WS_DISABLED rzadko

- WS_VSCROLL, aby dodać pionowy pasek przewijania

- WS_HSCROLL, aby dodać poziomy pasek przewijania

- WS_GROUP do grup kontrolek

- WS_TABSTOP, aby zezwolić na tabulację w tym formancie

##  <a name="drawitem"></a>CCheckListBox::D rawItem

Wywoływane przez platformę, gdy wizualny aspekt pola listy kontrolnej rysowanej przez właściciela zmienia się.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , który zawiera informacje o wymaganym typie rysunku.

### <a name="remarks"></a>Uwagi

Elementy `itemAction` i `itemState` składowe`DRAWITEMSTRUCT` struktury definiują akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja rysuje domyślną listę pól wyboru, składającą się z listy ciągów z wartością domyślną pola wyboru po lewej stronie. Rozmiar listy pól wyboru jest określony w polu [Utwórz](#create).

Przesłoń tę funkcję elementu członkowskiego, aby zaimplementować rysowanie pól listy kontrolnej rysowania przez właściciela, które nie są domyślne, takie jak pola listy kontrolnej z listami, które nie są ciągami, z elementami o zmiennej wysokości lub z polami wyboru, które nie znajdują się po lewej stronie. Aplikacja powinna przywrócić wszystkie obiekty interfejsu GDI (Graphics Device Interface) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Jeśli elementy pola listy kontrolnej nie mają tej samej wysokości, styl pola listy kontrolnej ( `Create`określony w) musi być * * LBS_OWNERVARIABLE i należy zastąpić funkcję [MeasureItem](#measureitem) .

##  <a name="enable"></a>CCheckListBox:: Enable

Wywołaj tę funkcję, aby włączyć lub wyłączyć element pola listy kontrolnej.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu pola listy kontrolnej, który ma zostać włączony.

*bEnabled*<br/>
Określa, czy element jest włączony, czy wyłączony.

##  <a name="getcheck"></a>CCheckListBox:: getcheck

Pobiera stan określonego pola wyboru.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) pola wyboru znajdującego się w polu listy.

### <a name="return-value"></a>Wartość zwracana

Stan określonego pola wyboru. Poniższa tabela zawiera listę możliwych wartości.

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|Pole wyboru jest zaznaczone.|
|BST_UNCHECKED|Pole wyboru nie jest zaznaczone.|
|BST_INDETERMINATE|Stan pola wyboru jest nieokreślony.|

##  <a name="getcheckstyle"></a>CCheckListBox:: getchecks

Wywołaj tę funkcję, aby uzyskać styl pola listy kontrolnej.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Wartość zwracana

Styl pól wyboru kontrolki.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat możliwych stylów [](#setcheckstyle), zobacz setchecks.

##  <a name="isenabled"></a>CCheckListBox:: IsEnabled

Wywołaj tę funkcję, aby określić, czy element jest włączony.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element jest włączony; w przeciwnym razie 0.

##  <a name="measureitem"></a>CCheckListBox::MeasureItem

Wywoływane przez platformę, gdy zostanie utworzony pole listy kontrolnej z stylem niestandardowym.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długi wskaźnik do struktury [MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja członkowska nic nie robi. Zastąp tę funkcję członkowską i wypełnij `MEASUREITEMSTRUCT` strukturę, aby informować okna o wymiarach elementów pola listy kontrolnej. Jeśli pole listy kontrolnej jest tworzone przy użyciu stylu [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , struktura wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski jest wywoływany tylko raz.

##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

Struktura wywołuje tę funkcję, aby uzyskać położenie i rozmiar pola wyboru w elemencie.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parametry

*rectItem*<br/>
Pozycja i rozmiar elementu listy.

*rectCheckBox*<br/>
Domyślna pozycja i rozmiar pola wyboru elementu.

### <a name="return-value"></a>Wartość zwracana

Położenie i rozmiar pola wyboru elementu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca tylko domyślną pozycję i rozmiar pola wyboru (`rectCheckBox`). Domyślnie pole wyboru jest wyrównane w lewym górnym rogu elementu i jest standardowym rozmiarem pola wyboru. Mogą jednak wystąpić sytuacje, w których pola wyboru po prawej stronie lub większe lub mniejsze pole wyboru. W takich przypadkach Przesłoń `OnGetCheckPosition` , aby zmienić położenie i rozmiar pola wyboru w elemencie.

##  <a name="setcheck"></a>CCheckListBox:: SetCheck

Ustawia stan określonego pola wyboru.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks (liczony od zera) pola wyboru znajdującego się w polu listy.

*nSprawdź*<br/>
Stan przycisku dla określonego pola wyboru. Więcej wartości można znaleźć w sekcji uwagi.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości parametru *nSprawdź* .

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|Zaznacz określone pole wyboru.|
|BST_UNCHECKED|Wyczyść określone pole wyboru.|
|BST_INDETERMINATE|Ustaw określony stan pola wyboru na nieokreślony.<br /><br /> Ten stan jest dostępny tylko wtedy, gdy styl pola wyboru to BS_AUTO3STATE lub BS_3STATE. Aby uzyskać więcej informacji, zobacz [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>CCheckListBox:: setchecks

Wywołaj tę funkcję, aby ustawić styl pól wyboru w polu listy kontrolnej.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Określa styl pól wyboru w polu listy kontrolnej.

### <a name="remarks"></a>Uwagi

Prawidłowe Style:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Aby uzyskać informacje o tych stylach, zobacz [style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Zobacz także

[Przykład TSTCON MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
