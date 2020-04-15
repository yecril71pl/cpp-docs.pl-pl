---
title: Klasa CLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372259"
---
# <a name="clinkctrl-class"></a>Klasa CLinkCtrl

Udostępnia funkcje wspólnego formantu SysLink systemu Windows.

## <a name="syntax"></a>Składnia

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Konstruuje `CLinkCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinkCtrl::Utwórz](#create)|Tworzy formant łącza i dołącza `CLinkCtrl` go do obiektu.|
|[CLinkCtrl::CreateEx](#createex)|Tworzy formant łącza z rozszerzonymi stylami `CLinkCtrl` i dołącza go do obiektu.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Pobiera idealną wysokość formantu łącza.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Oblicza preferowaną wysokość tekstu łącza dla bieżącego formantu łącza, w zależności od określonej szerokości łącza.|
|[CLinkCtrl::GetItem](#getitem)|Pobiera stany i atrybuty elementu kontroli łącza.|
|[CLinkCtrl::GetItemID](#getitemid)|Pobiera identyfikator elementu sterującego łącza.|
|[CLinkCtrl::GetItemState](#getitemstate)|Pobiera stan elementu kontroli łącza.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Pobiera adres URL reprezentowany przez element kontroli łącza.|
|[CLinkCtrl::HitTest](#hittest)|Określa, czy użytkownik kliknął określone łącze.|
|[CLinkCtrl::SetItem](#setitem)|Ustawia stany i atrybuty elementu sterującego łącza.|
|[CLinkCtrl::SetItemID](#setitemid)|Ustawia identyfikator elementu sterującego łącza.|
|[CLinkCtrl::SetItemState](#setitemstate)|Ustawia stan elementu formantu łącza.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Ustawia adres URL reprezentowany przez element kontroli łącza.|

## <a name="remarks"></a>Uwagi

"Kontrolka łącza" zapewnia wygodny sposób osadzania łączy hipertekstowych w oknie. Rzeczywisty formant jest oknem, które renderuje oznaczony tekst i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie osadzone łącze. Wiele łączy są obsługiwane w ramach jednego formantu i mogą być dostępne za pomocą indeksu opartego na wartości zero.

Ten formant (i `CLinkCtrl` dlatego klasa) jest dostępny tylko dla programów działających w systemie Windows XP i nowszych.

Aby uzyskać więcej informacji, zobacz [SysLink Control](/windows/win32/Controls/syslink-overview) w windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl

Konstruuje `CLinkCtrl` obiekt.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>CLinkCtrl::Utwórz

Tworzy formant łącza i dołącza `CLinkCtrl` go do obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*lpszLinkMarkup*<br/>
Wskaźnik do ciągu zakończonego zerem, który zawiera zaznaczony tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczniki i dostęp do łączy" w temacie [Omówienie kontrolek SysLink](/windows/win32/Controls/syslink-overview).

*Dwstyle*<br/>
Określa styl formantu łącza. Zastosuj dowolną kombinację stylów sterowania. Aby uzyskać więcej `Windows SDK` informacji, zobacz [typowe style sterowania.](/windows/win32/Controls/common-control-styles)

*Rect*<br/>
Określa rozmiar i położenie formantu łącza. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne formantu łącza. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu łącza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Konstruowanie `CLinkCtrl` obiektu w dwóch krokach. Najpierw wywołaj konstruktora, a następnie wywołaj `Create`, co `CLinkCtrl` tworzy formant łącza i dołącza go do obiektu. Jeśli chcesz używać rozszerzonych stylów okien z formantem, zadzwoń do `Create` [CLinkCtrl::CreateEx](#createex) zamiast .

Druga forma `Create` metody jest przestarzała. Użyj pierwszego formularza, który określa parametr *lpszLinkMarkup.*

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje dwie `m_Link1` zmienne, o nazwie i `m_Link2`, które są używane do uzyskiwania dostępu do dwóch formantów łącza.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu tworzy jeden formant łącza na podstawie lokalizacji innego formantu łącza. Moduł ładujący zasoby tworzy pierwszy formant łącza po uruchomieniu aplikacji. Gdy aplikacja wchodzi OnInitDialog metody, należy utworzyć formant drugiego łącza względem położenia pierwszego formantu łącza. Następnie zmienić rozmiar drugiego formantu łącza, aby dopasować wyświetlany tekst.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>CLinkCtrl::CreateEx

Tworzy formant łącza z rozszerzonymi stylami `CLinkCtrl` i dołącza go do obiektu.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parametry

*lpszLinkMarkup*<br/>
Wskaźnik do ciągu zakończonego zerem, który zawiera zaznaczony tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczniki i dostęp do łączy" w temacie [Omówienie kontrolek SysLink](/windows/win32/Controls/syslink-overview).

*Dwexstyle*<br/>
Określa rozszerzony styl formantu łącza. Aby uzyskać listę rozszerzonych stylów systemu Windows, zobacz parametr *dwExStyle* dla [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) w zestawie Windows SDK.

*Dwstyle*<br/>
Określa styl formantu łącza. Zastosuj dowolną kombinację stylów sterowania. Aby uzyskać więcej informacji, zobacz [Typowe style sterowania](/windows/win32/Controls/common-control-styles) w panelu Windows SDK.

*Rect*<br/>
Określa rozmiar i położenie formantu łącza. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) lub [struktura RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne formantu łącza. Nie może być null.

*Nid*<br/>
Określa identyfikator formantu łącza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Utwórz,](#create) aby zastosować rozszerzone stałe stylu systemu Windows.

Druga forma `CreateEx` metody jest przestarzała. Użyj pierwszego formularza, który określa parametr *lpszLinkMarkup.*

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>CLinkCtrl::GetIdealHeight

Pobiera idealną wysokość formantu łącza.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Idealna wysokość formantu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Oblicza preferowaną wysokość tekstu łącza dla bieżącego formantu łącza, w zależności od określonej szerokości łącza.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*cxMaxWidth*|[w] Maksymalna szerokość łącza w pikselach.|
|[na zewnątrz] \* *pSize (rozmiar)*|Wskaźnik do [struktury](/windows/win32/api/windef/ns-windef-size) rozmiar systemu Windows. Gdy ta metoda zwraca, *cy* element `SIZE` członkowski struktury zawiera idealną wysokość tekstu łącza dla szerokości tekstu łącza, który jest określony przez *cxMaxWidth*. Element *członkowski struktury cx* zawiera szerokość tekstu łącza, która jest rzeczywiście potrzebna.|

### <a name="return-value"></a>Wartość zwracana

Preferowana wysokość tekstu łącza w pikselach. Zwracana wartość jest taka sama jak wartość elementu `SIZE` członkowskiego *cy* struktury.

### <a name="remarks"></a>Uwagi

Na przykład `GetIdealSize` metody, zobacz przykład w [CLinkCtrl::Create](#create).

Ta metoda wysyła komunikat [LM_GETIDEALSIZE,](/windows/win32/Controls/lm-getidealsize) który jest opisany w windows SDK.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>CLinkCtrl::GetItem

Pobiera stany i atrybuty elementu kontroli łącza.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do struktury [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) do odbierania informacji o towarach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [LM_GETITEM](/windows/win32/Controls/lm-getitem)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>CLinkCtrl::GetItemID

Pobiera identyfikator elementu sterującego łącza.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*strID*<br/>
Obiekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) zawierający identyfikator określonego elementu.

*szID*<br/>
Ciąg zakończony z wartością null zawierający identyfikator określonego elementu.

*cchID ( cchID )*<br/>
Rozmiar znaków buforu *szID.*

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

> [!NOTE]
> Ta funkcja zwraca również wartość FAŁSZ, jeśli bufor *szID lub strID* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera identyfikator określonego elementu kontroli łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w windows SDK.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>CLinkCtrl::GetItemState

Pobiera stan elementu kontroli łącza.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*pnStan*<br/>
Wartość określonego elementu stanu.

*StateMask*<br/>
Kombinacja flag opisujących element stanu, który ma zostać ujmowany. Lista wartości znajduje się w opisie `state` elementu członkowskiego w strukturze [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Dozwolone elementy są identyczne z `state`tymi dozwolonymi w pliku .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Pobiera wartość określonego elementu stanu określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w windows SDK.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>CLinkCtrl::GetItemUrl

Pobiera adres URL reprezentowany przez element kontroli łącza.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*strUrl (strUrl)*<br/>
Obiekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) zawierający adres URL reprezentowany przez określony element

*szurl (szurl)*<br/>
Ciąg zakończony z wartością null zawierający adres URL reprezentowany przez określony element

*cchUrl (cchUrl)*<br/>
Rozmiar znaków buforu *szURL.*

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

> [!NOTE]
> Ta funkcja zwraca również wartość FAŁSZ, jeśli bufor *szUrl lub strUrl* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera adres URL reprezentowany przez określony element kontroli łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w windows SDK.

## <a name="clinkctrlhittest"></a><a name="hittest"></a>CLinkCtrl::HitTest

Określa, czy użytkownik kliknął określone łącze.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parametry

*phti ( phti )*<br/>
Wskaźnik do `LHITTESTINFO` struktury zawierającej wszelkie informacje o łączu klikniętym przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [LM_HITTEST](/windows/win32/Controls/lm-hittest)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>CLinkCtrl::SetItem

Ustawia stany i atrybuty elementu sterującego łącza.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parametry

*pItem (własówce)*<br/>
Wskaźnik do struktury [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) zawierający informacje do ustawionego.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie [LM_SETITEM](/windows/win32/Controls/lm-setitem)komunikatu Win32, zgodnie z opisem w windows SDK.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>CLinkCtrl::SetItemID

Pobiera identyfikator elementu sterującego łącza.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*szID*<br/>
Ciąg zakończony z wartością null zawierający identyfikator określonego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ustawia identyfikator określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w sdk systemu Windows.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>CLinkCtrl::SetItemState

Pobiera stan elementu kontroli łącza.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*pnStan*<br/>
Wartość ustawionego określonego elementu stanu.

*StateMask*<br/>
Kombinacja flag opisujących element stanu, który jest ustawiany. Lista wartości znajduje się w opisie `state` elementu członkowskiego w strukturze [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Dozwolone elementy są identyczne z `state`tymi dozwolonymi w pliku .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ustawia wartość określonego elementu stanu określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w sdk systemu Windows.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>CLinkCtrl::SetItemUrl

Ustawia adres URL reprezentowany przez element kontroli łącza.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parametry

*Ilink*<br/>
Indeks elementu sterującego łącza.

*szurl (szurl)*<br/>
Ciąg zakończony z wartością null zawierający adres URL reprezentowany przez określony element

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE na sukces, FALSE na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ustawia adres URL reprezentowany przez określony element sterujący łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w sdk systemu Windows.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
