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
ms.openlocfilehash: 9c649dd979b28e2b545a797c5453a2ec9aa6d0dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206734"
---
# <a name="cchecklistbox-class"></a>Klasa CCheckListBox

Oferuje funkcje pola listy kontrolnej Windows.

## <a name="syntax"></a>Składnia

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Konstruuje `CCheckListBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCheckListBox::Create](#create)|Tworzy okno Lista kontrolna Windows i dołącza je do `CCheckListBox` obiektu.|
|[CCheckListBox::DrawItem](#drawitem)|Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmian pole listy rysowane przez właściciela.|
|[CCheckListBox::Enable](#enable)|Włącza lub wyłącza element pola listy kontrolnej.|
|[CCheckListBox::GetCheck](#getcheck)|Pobiera stan pola wyboru elementu.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Pobiera styl kontrolki pola wyboru.|
|[CCheckListBox::IsEnabled](#isenabled)|Określa, czy element jest włączony.|
|[CCheckListBox::MeasureItem](#measureitem)|Wywoływane przez platformę, gdy zostanie utworzony przy użyciu stylu rysowania przez właściciela pola listy.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Metoda wywoływana przez platformę, by uzyskać położenie elementu pola wyboru.|
|[CCheckListBox::SetCheck](#setcheck)|Ustawia stan pola wyboru elementu.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Ustawia styl kontrolki pola wyboru.|

## <a name="remarks"></a>Uwagi

"Pole listy kontrolnej" Wyświetla listę elementów, takich jak nazwy plików. Każdy element na liście ma obok niej, które użytkownik może zaznacz lub wyczyść pole wyboru.

`CCheckListBox` jest tylko w przypadku kontrolek rysowanych przez właściciela, ponieważ lista zawiera więcej niż ciągi tekstowe. W najprostszym pola listy kontrolnej zawiera ciągi tekstowe, a pola wyboru, ale nie musi być w ogóle tekstu. Na przykład można mieć małe mapy bitowej przy użyciu pola wyboru obok każdego elementu listy.

Aby utworzyć własne pola listy kontrolnej, musi pochodzić klasy z `CCheckListBox`. Do uzyskania własne klasy napisać Konstruktor dla klasy pochodnej, następnie wywołać `Create`.

Jeśli chcesz obsługiwać Windows powiadomienia wysyłane przez pole listy do elementu nadrzędnego (zazwyczaj klasą pochodną [CDialog](../../mfc/reference/cdialog-class.md)), dodanie funkcji składowej wejścia i program obsługi komunikatów mapy komunikatów do klasy nadrzędnej dla każdego komunikatu.

Każdy wpis mapy komunikatów ma następującą postać:

**ON\_**_powiadomień_ **(** _identyfikator_, _memberFxn_ **)**

gdzie `id` Określa identyfikator okna elementu podrzędnego kontrolki wysyłania powiadomienia i `memberFxn` nazywa się nadrzędny element członkowski funkcji zostały napisane do obsługi powiadomień.

Prototyp funkcji elementu nadrzędnego jest następująca:

`afx_msg void memberFxn();`

Istnieje tylko jeden wpis mapy komunikatów, które odnoszą się specjalnie do `CCheckListBox` (ale również wyświetlane wpisy mapy komunikatów dla [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE użytkownik zmienił stan elementu checkbox.

Pole z listy kontrolnej w przypadku pola listy kontrolnej domyślne (lista ciągów o rozmiarze domyślnym pola wyboru po lewej), można użyć domyślnie [CCheckListBox::DrawItem](#drawitem) narysuj pole listy kontrolnej. W przeciwnym razie konieczne jest przesłonięcie [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) funkcji i [CCheckListBox::DrawItem](#drawitem) i [CCheckListBox::MeasureItem](#measureitem) funkcji.

Można utworzyć pola listy kontrolnej, z szablonu okna dialogowego lub bezpośrednio w kodzie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox

Konstruuje `CCheckListBox` obiektu.

```
CCheckListBox();
```

### <a name="remarks"></a>Uwagi

Konstruowanie `CCheckListBox` obiektu w dwóch krokach. Należy najpierw zdefiniować klasę pochodną `CCheckListBox`, następnie wywołać `Create`, która inicjuje pola listy kontrolnej Windows i dołącza go do `CCheckListBox` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

Tworzy okno Lista kontrolna Windows i dołącza je do `CCheckListBox` obiektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl pola listy kontrolnej. Styl musi być LBS_HASSTRINGS i LBS_OWNERDRAWFIXED (wszystkie elementy na liście są sama wysokość) lub LBS_OWNERDRAWVARIABLE (elementy na liście są o różnej wysokości). Ten styl można łączyć z innymi [style pola listy](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) LBS_USETABSTOPS, z wyjątkiem.

*Rect*<br/>
Określa pole listy kontrolnej, rozmiar i położenie. Może być [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.

*pParentWnd*<br/>
Określa pole listy kontrolnej okna nadrzędnego (zazwyczaj `CDialog` obiektu). Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki. pole listy kontrolnej

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Konstruowanie `CCheckListBox` obiektu w dwóch krokach. Najpierw należy zdefiniować klasę pochodną `CcheckListBox` , a następnie wywołać `Create`, która inicjuje pola listy kontrolnej Windows i dołącza go do `CCheckListBox`. Zobacz [CCheckListBox::CCheckListBox](#cchecklistbox) dla próbki.

Gdy `Create` wykonuje Windows wysyła [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), i [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) komunikaty do kontrolki pola listy kontrolnej.

Te komunikaty są obsługiwane domyślnie [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), i [ongetminmaxinfo —](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funkcji elementów członkowskich w `CWnd` klasy bazowej. Rozszerzenie obsługi wiadomości domyślnej, należy dodać mapy komunikatów do swojej klasy pochodnej i funkcje Członkowskie zastąpienie poprzedniej obsługi wiadomości. Zastąp `OnCreate`, na przykład do przeprowadzenia wymaganych inicjowania dla nowej klasy.

Zastosuj następujące [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles) do kontrolki pola listy kontrolnej:

- WS_CHILD zawsze

- WS_VISIBLE zwykle

- WS_DISABLED rzadko

- WS_VSCROLL Aby dodać pionowy pasek przewijania

- WS_HSCROLL Aby dodać poziomy pasek przewijania

- WS_GROUP kontrolek grupy

- WS_TABSTOP zezwolić na klawiszem TAB do tego formantu

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

Metoda wywoływana przez platformę, gdy zmieni się wizualny aspekt zmiany pola rysowanych przez właściciela listy kontrolnej.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Długie wskaźnik do [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturę, która zawiera informacje o typie rysowania wymagane.

### <a name="remarks"></a>Uwagi

`itemAction` i `itemState` członkowie `DRAWITEMSTRUCT` struktury zdefiniować rysowania akcję, która ma zostać wykonane.

Domyślnie ta funkcja pobiera domyślnej listy wyboru, składający się z listą parametrów o rozmiarze domyślne pole wyboru po lewej stronie. Rozmiar listy pole wyboru jest określona w [Utwórz](#create).

Zastąpienie tej funkcji elementu członkowskiego, aby zaimplementować rysowania przez właściciela Lista kontrolna pola, które nie są domyślne, takie jak pola listy kontrolnej z listy, które nie są ciągami, z elementami o zmiennej wysokości lub za pomocą pola wyboru, które nie są po lewej stronie. Aplikacja powinna przywrócenie wszystkich obiektów grafiki urządzenia interface (GDI), wybrany dla kontekstu wyświetlana podana w *lpDrawItemStruct* przed zakończeniem tej funkcji elementu członkowskiego.

Jeśli elementy pola listy kontrolnej nie sama wysokość, listę kontrolną polu style (określony w `Create`) musi być ** przesłonięcie LBS_OWNERVARIABLE, a [measureitem —](#measureitem) funkcji.

##  <a name="enable"></a>  CCheckListBox::Enable

Wywołaj tę funkcję, aby włączyć lub wyłączyć elementu pola listy kontrolnej.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu pola listy kontrolnej do włączenia.

*bWłączony*<br/>
Określa, czy element jest włączony.

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

Pobiera stan określonego pola wyboru.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks pola wyboru, która znajduje się w polu listy.

### <a name="return-value"></a>Wartość zwracana

Stan określonego pola wyboru. Poniższa tabela zawiera listę możliwych wartości.

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|Pole wyboru jest zaznaczone.|
|BST_UNCHECKED|Pole wyboru nie jest zaznaczone.|
|BST_INDETERMINATE|Stan pola wyboru jest nieokreślony.|

##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle

Wywołaj tę funkcję, aby pobrać stylu pola listy kontrolnej.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Wartość zwracana

Styl kontrolki pola wyboru.

### <a name="remarks"></a>Uwagi

Aby uzyskać informacji na temat możliwych stylów, zobacz [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>  CCheckListBox::IsEnabled

Wywołaj tę funkcję, aby określić, czy element jest włączony.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Indeks elementu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element jest włączony; w przeciwnym razie 0.

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

Wywoływane przez platformę, po utworzeniu pola listy kontrolnej, styl niestandardowy.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Długie wskaźnik do [MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct) struktury.

### <a name="remarks"></a>Uwagi

Domyślnie ta funkcja elementu członkowskiego nic nie robi. Zastąpienie tej funkcji elementu członkowskiego, a następnie wypełnij `MEASUREITEMSTRUCT` strukturę, aby poinformować Windows wymiary elementów pola listy kontrolnej. Jeśli pole listy kontrolnej jest tworzona przy użyciu [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylu, struktura wywołuje tej funkcji elementu członkowskiego dla każdego elementu w polu listy. W przeciwnym razie ta składowa zostanie wywołana tylko raz.

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

Struktura wywołuje tę funkcję, aby uzyskać położenie i rozmiar pola wyboru w elemencie.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parametry

*rectItem*<br/>
Położenie i rozmiar elementu listy.

*rectCheckBox*<br/>
Domyślne położenie i rozmiar pola wyboru elementu.

### <a name="return-value"></a>Wartość zwracana

Położenie i rozmiar pola wyboru elementu.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zwraca tylko domyślne położenie i rozmiar pola wyboru (`rectCheckBox`). Domyślnie pole wyboru jest wyrównany w lewym górnym rogu elementu i ma rozmiar standardowe pole wyboru. Można wykluczyć sytuacji, gdzie ma pole wyboru po prawej stronie lub ma postać pola wyboru większy lub mniejszy. W takich przypadkach należy zastąpić `OnGetCheckPosition` zmienić pole wyboru pozycji i rozmiaru w elemencie.

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

Ustawia stan określonego pola wyboru.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Liczony od zera indeks pola wyboru, która znajduje się w polu listy.

*nCheck*<br/>
Stan przycisku dla określonego pola wyboru. Zobacz sekcję Spostrzeżenia, aby możliwe wartości.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości dla *nSprawdź* parametru.

|Wartość|Opis|
|-----------|-----------------|
|BST_CHECKED|Zaznacz pole wyboru określony.|
|BST_UNCHECKED|Wyczyść pole wyboru określony.|
|BST_INDETERMINATE|Ustaw stan określonego pola wyboru nieokreślony.<br /><br /> Ten stan jest dostępna tylko w przypadku stylu pola wyboru BS_AUTO3STATE lub BS_3STATE. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

Wywołaj tę funkcję, aby ustawić style pól wyboru w polu listy kontrolnej.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Określa styl pola wyboru w polu listy kontrolnej.

### <a name="remarks"></a>Uwagi

Style prawidłowe są następujące:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Aby uzyskać informacji na temat tych stylów, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Zobacz także

[MFC Sample TSTCON](../../overview/visual-cpp-samples.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CListBox](../../mfc/reference/clistbox-class.md)
