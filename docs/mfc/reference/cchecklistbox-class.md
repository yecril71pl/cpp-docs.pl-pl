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
ms.openlocfilehash: 8ca8d3b2cb4ce3c5b070d883e0a418ebec3665b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352383"
---
# <a name="cchecklistbox-class"></a>Klasa CCheckListBox

Udostępnia funkcje pola listy kontrolnej systemu Windows.

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
|[CCheckListBox::Tworzenie](#create)|Tworzy pole listy kontrolnej systemu Windows `CCheckListBox` i dołącza je do obiektu.|
|[CCheckListBox::DrawItem](#drawitem)|Wywoływane przez strukturę, gdy zmienia się wizualny aspekt pola listy rysowania właściciela.|
|[CCheckListBox::Włącz](#enable)|Włącza lub wyłącza element pola listy kontrolnej.|
|[CCheckListBox::GetCheck](#getcheck)|Pobiera stan elementu pole wyboru.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Pobiera styl pól wyboru formantu.|
|[CCheckListBox::IsEnabled](#isenabled)|Określa, czy element jest włączony.|
|[CCheckListBox::MeasureItem](#measureitem)|Wywoływane przez strukturę podczas tworzenia pola listy ze stylem rysowania właściciela.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Wywoływane przez strukturę, aby uzyskać położenie elementu pole wyboru.|
|[CCheckListBox::SetCheck](#setcheck)|Ustawia stan pola wyboru elementu.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Ustawia styl pól wyboru formantu.|

## <a name="remarks"></a>Uwagi

W "polu listy kontrolnej" jest wyświetlana lista elementów, takich jak nazwy plików. Obok każdego elementu na liście znajduje się pole wyboru, które użytkownik może zaznaczyć lub wyczyścić.

`CCheckListBox`jest tylko dla formantów rysowanych przez właściciela, ponieważ lista zawiera więcej niż ciągi tekstowe. W najprostszym polu lista kontrolna zawiera ciągi tekstowe i pola wyboru, ale nie trzeba w ogóle mieć tekstu. Na przykład można mieć listę małych map bitowych z polem wyboru obok każdego elementu.

Aby utworzyć własne pole listy kontrolnej, należy `CCheckListBox`wyprowadzić własną klasę z pliku . Aby wyprowadzić własną klasę, napisz konstruktor dla klasy `Create`pochodnej, a następnie wywołaj .

Jeśli chcesz obsługiwać wiadomości powiadomień systemu Windows wysyłane przez pole listy do jego nadrzędnego (zwykle klasy pochodzące z [CDialog](../../mfc/reference/cdialog-class.md)), dodaj wpis mapy wiadomości i funkcję elementu członkowskiego obsługi wiadomości do klasy nadrzędnej dla każdej wiadomości.

Każdy wpis mapy wiadomości ma następującą formę:

**On\_**_Powiadomienie_ _(id_, _memberFxn_ **)** **(**

gdzie `id` określa identyfikator okna podrzędnego formantu `memberFxn` wysyłającego powiadomienie i jest nazwą funkcji elementu członkowskiego nadrzędnego, która została napisana w celu obsługi powiadomienia.

Prototyp funkcji rodzica jest następujący:

`afx_msg void memberFxn();`

Istnieje tylko jeden wpis mapy wiadomości, który `CCheckListBox` odnosi się konkretnie do (ale zobacz także wpisy mapy wiadomości dla [CListBox):](../../mfc/reference/clistbox-class.md)

- ON_CLBN_CHKCHANGE Użytkownik zmienił stan pola wyboru elementu.

Jeśli pole listy kontrolnej jest domyślnym polem wyboru listy kontrolnej (lista ciągów z domyślnymi polami wyboru po lewej stronie każdego z nich), można użyć domyślnego [pola CCheckListBox::DrawItem,](#drawitem) aby narysować pole listy kontrolnej. W przeciwnym razie należy zastąpić [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) funkcji i [CCheckListBox::DrawItem](#drawitem) i [CCheckListBox::MeasureItem](#measureitem) funkcje.

Pole listy kontrolnej można utworzyć z szablonu okna dialogowego lub bezpośrednio w kodzie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Clistbox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Konstruuje `CCheckListBox` obiekt.

```
CCheckListBox();
```

### <a name="remarks"></a>Uwagi

Konstruowanie `CCheckListBox` obiektu w dwóch krokach. Najpierw zdefiniuj `CCheckListBox`klasę `Create`pochodną , a następnie wywołanie , która `CCheckListBox` inicjuje pole listy kontrolnej systemu Windows i dołącza ją do obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>CCheckListBox::Tworzenie

Tworzy pole listy kontrolnej systemu Windows `CCheckListBox` i dołącza je do obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl pola listy kontrolnej. Styl musi być LBS_HASSTRINGS i LBS_OWNERDRAWFIXED (wszystkie elementy na liście mają taką samą wysokość) lub LBS_OWNERDRAWVARIABLE (elementy na liście mają różne wysokości). Ten styl można łączyć z innymi [stylami pola listy,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) z wyjątkiem LBS_USETABSTOPS.

*Rect*<br/>
Określa rozmiar i położenie pola wyboru. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub struktura [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne pola listy kontrolnej `CDialog` (zwykle obiekt). Nie może być null.

*Nid*<br/>
Określa identyfikator formantu pola wyboru.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CCheckListBox` obiektu w dwóch krokach. Najpierw zdefiniuj `CcheckListBox` klasę pochodną, a następnie wywołanie `Create`, która inicjuje pole listy kontrolnej systemu Windows i dołącza ją do pliku `CCheckListBox`. Zobacz [CCheckListBox::CCheckListBox](#cchecklistbox) dla przykładu.

Podczas `Create` wykonywania system Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) wiadomości do kontrolki pola wyboru listy kontrolnej.

Te komunikaty są obsługiwane domyślnie przez Funkcje członkowskie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)i [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) w klasie podstawowej. `CWnd` Aby rozszerzyć domyślną obsługę wiadomości, dodaj mapę wiadomości do klasy pochodnej i zastąpozaj poprzednie funkcje członkowskie obsługi wiadomości. Zastąd w celu wykonania wymaganej inicjalizacji `OnCreate`dla nowej klasy.

Zastosuj następujące [style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pola wyboru:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL Aby dodać pionowy pasek przewijania

- WS_HSCROLL Aby dodać poziomy pasek przewijania

- WS_GROUP Do grupowanie formantów

- WS_TABSTOP Aby umożliwić tabulator do tej kontroli

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::DrawItem

Wywoływane przez strukturę, gdy zmienia się wizualny aspekt pola wyboru listy losowej właściciela.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długi wskaźnik do struktury [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) który zawiera informacje o typie wymaganego rysunku.

### <a name="remarks"></a>Uwagi

Elementy `itemAction` `itemState` członkowskie `DRAWITEMSTRUCT` konstrukcji definiują akcję rysowania, która ma zostać wykonana.

Domyślnie ta funkcja rysuje domyślną listę pól wyboru, składającą się z listy ciągów, z których każdy ma domyślne pole wyboru po lewej stronie. Rozmiar listy pól wyboru jest określony w [polu Utwórz](#create).

Zastąrpnąć tę funkcję elementu członkowskiego, aby zaimplementować rysowanie pól listy kontrolnej rysowania właściciela, które nie są domyślne, takich jak pola listy kontrolne z listami, które nie są ciągami znaków, z elementami o zmiennej wysokości lub z polami wyboru, które nie znajdują się po lewej stronie. Aplikacja powinna przywrócić wszystkie obiekty interfejsu urządzenia graficznego (GDI) wybrane dla kontekstu wyświetlania dostarczonego w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Jeśli elementy pola wyboru nie mają tej samej wysokości, `Create`styl pola wyboru (określony w ) musi być **LBS_OWNERVARIABLE**i należy zastąpić funkcję [MeasureItem.](#measureitem)

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox::Włącz

Wywołanie tej funkcji, aby włączyć lub wyłączyć element pola wyboru listy kontrolnej.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks elementu pola listy kontrolnej, który ma być włączony.

*bWłach*<br/>
Określa, czy element jest włączony, czy wyłączony.

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox::GetCheck

Pobiera stan określonego pola wyboru.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera pola wyboru, które znajduje się w polu listy.

### <a name="return-value"></a>Wartość zwracana

Stan określonego pola wyboru. W poniższej tabeli wymieniono możliwe wartości.

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|To pole wyboru jest zaznaczone.|
|BST_UNCHECKED|To pole wyboru nie jest zaznaczone.|
|BST_INDETERMINATE|Stan pola wyboru jest nieokreślony.|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Wywołanie tej funkcji, aby uzyskać styl listy kontrolnej.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Wartość zwracana

Styl pól wyboru formantu.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat możliwych stylów, zobacz [SetCheckStyle](#setcheckstyle).

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox::IsEnabled

Wywołanie tej funkcji, aby ustalić, czy element jest włączony.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks towaru.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli element jest włączony; w przeciwnym razie 0.

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox::MeasureItem

Wywoływane przez platformę podczas tworzenia pola listy kontrolnej ze stylem nondefault.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długi wskaźnik do struktury [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpuj tę funkcję `MEASUREITEMSTRUCT` elementu członkowskiego i wypełnij strukturę, aby poinformować system Windows o wymiarach elementów pola listy kontrolnej. Jeśli pole listy kontrolnej jest tworzone w stylu [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) framework wywołuje tę funkcję elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ten element członkowski jest wywoływany tylko raz.

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

Struktura wywołuje tę funkcję, aby uzyskać położenie i rozmiar pola wyboru w elemencie.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parametry

*rectItem*<br/>
Położenie i rozmiar elementu listy.

*skrzynka z narzędziami do zdejmuj*<br/>
Domyślne pole wyboru położenie i rozmiar elementu.

### <a name="return-value"></a>Wartość zwracana

Pole wyboru Położenie i rozmiar elementu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca tylko domyślną pozycję`rectCheckBox`i rozmiar pola wyboru ( ). Domyślnie pole wyboru jest wyrównane w lewym górnym rogu elementu i jest standardowym rozmiarem pola wyboru. Mogą wystąpić przypadki, w których chcesz pola wyboru po prawej stronie lub chcesz większe lub mniejsze pole wyboru. W takich przypadkach należy `OnGetCheckPosition` zastąpić, aby zmienić położenie i rozmiar pola wyboru w elemencie.

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox::SetCheck

Ustawia stan określonego pola wyboru.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*Nindex*<br/>
Indeks od zera pola wyboru, które znajduje się w polu listy.

*nSprawda*<br/>
Stan przycisku dla określonego pola wyboru. Zobacz uwagi sekcji możliwe wartości.

### <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono możliwe wartości parametru *nCheck.*

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|Zaznacz określone pole wyboru.|
|BST_UNCHECKED|Wyczyść określone pole wyboru.|
|BST_INDETERMINATE|Ustaw określony stan pola wyboru na nieokreślony.<br /><br /> Ten stan jest dostępny tylko wtedy, gdy styl pola wyboru jest BS_AUTO3STATE lub BS_3STATE. Aby uzyskać więcej informacji, zobacz [Style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Wywołanie tej funkcji, aby ustawić styl pól wyboru w polu listy kontrolnej.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*styl nStyle*<br/>
Określa styl pól wyboru w polu listy kontrolnej.

### <a name="remarks"></a>Uwagi

Prawidłowe style to:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Aby uzyskać informacje na temat tych stylów, zobacz [Style przycisków](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Zobacz też

[Próbka MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
