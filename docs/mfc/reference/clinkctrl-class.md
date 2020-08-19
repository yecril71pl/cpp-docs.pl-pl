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
ms.openlocfilehash: 80548015ff9f24127280ee94421c8fbda7a647ea
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561417"
---
# <a name="clinkctrl-class"></a>Klasa CLinkCtrl

Oferuje funkcje typowej kontrolki SysLink systemu Windows.

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
|[CLinkCtrl:: Create](#create)|Tworzy formant łącza i dołącza go do `CLinkCtrl` obiektu.|
|[CLinkCtrl::CreateEx](#createex)|Tworzy formant łącza z rozszerzonymi stylami i dołącza go do `CLinkCtrl` obiektu.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Pobiera idealną wysokość kontrolki łącza.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Oblicza preferowaną wysokość tekstu linku dla bieżącego formantu linku, w zależności od określonej szerokości linku.|
|[CLinkCtrl:: GetItem](#getitem)|Pobiera Stany i atrybuty elementu kontrolki link.|
|[CLinkCtrl:: GetItemID](#getitemid)|Pobiera identyfikator elementu kontrolki łącza.|
|[CLinkCtrl::GetItemState](#getitemstate)|Pobiera stan elementu kontrolki link.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Pobiera adres URL reprezentowany przez element sterowania linkiem.|
|[CLinkCtrl::HitTest](#hittest)|Określa, czy użytkownik kliknął określone łącze.|
|[CLinkCtrl:: SetItem](#setitem)|Ustawia Stany i atrybuty elementu kontrolki link.|
|[CLinkCtrl:: setitemid](#setitemid)|Ustawia identyfikator elementu kontrolki łącza.|
|[CLinkCtrl::SetItemState](#setitemstate)|Ustawia stan elementu sterowania linkiem.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Ustawia adres URL reprezentowany przez element sterowania linkiem.|

## <a name="remarks"></a>Uwagi

"Kontrolka łącza" pozwala wygodnie osadzić Linki hipertekstowe w oknie. Rzeczywista kontrolka to okno, które renderuje zaznaczony tekst i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie link osadzony. W jednym formancie obsługiwane są wiele linków i można do nich uzyskać dostęp za pomocą indeksu od zera.

Ten formant (i w związku z tym `CLinkCtrl` Klasa) jest dostępny tylko dla programów uruchomionych w systemie Windows XP i nowszych.

Aby uzyskać więcej informacji, zobacz [Syslink Control](/windows/win32/Controls/syslink-overview) w Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn. h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a> CLinkCtrl::CLinkCtrl

Konstruuje `CLinkCtrl` obiekt.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a> CLinkCtrl:: Create

Tworzy formant łącza i dołącza go do `CLinkCtrl` obiektu.

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
Wskaźnik na ciąg zakończony zerem, który zawiera oznaczony tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "znaczniki i dostęp do łącza" w temacie [Omówienie formantów Syslink](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Określa styl kontrolki link. Zastosuj dowolną kombinację stylów kontrolek. Aby uzyskać więcej informacji, zobacz [typowe style kontrolek](/windows/win32/Controls/common-control-styles) w `Windows SDK` .

*cinania*<br/>
Określa rozmiar i położenie kontrolki łącza. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki link. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki łącza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Obiekt jest konstruowany `CLinkCtrl` w dwóch krokach. Najpierw Wywołaj konstruktora, a następnie Wywołaj `Create` , który tworzy formant łącza i dołącza go do `CLinkCtrl` obiektu. Jeśli chcesz użyć rozszerzonych stylów systemu Windows z kontrolką, wywołaj [CLinkCtrl:: CreateEx](#createex) zamiast `Create` .

Druga forma `Create` metody jest przestarzała. Użyj pierwszego formularza, który określa parametr *lpszLinkMarkup* .

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje dwie zmienne o nazwie `m_Link1` i `m_Link2` , które są używane w celu uzyskania dostępu do dwóch kontrolek łącza.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu tworzy jedną kontrolkę linku na podstawie lokalizacji innej kontrolki łącza. Moduł ładujący zasoby tworzy pierwszy formant łącza podczas uruchamiania aplikacji. Gdy aplikacja wprowadza metodę OnInitDialog, należy utworzyć drugą kontrolkę łącza względem pozycji pierwszej kontrolki łącza. Następnie zmień rozmiar drugiej kontrolki linku tak, aby mieściła się w wyświetlonym tekście.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a> CLinkCtrl::CreateEx

Tworzy formant łącza z rozszerzonymi stylami i dołącza go do `CLinkCtrl` obiektu.

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
Wskaźnik na ciąg zakończony zerem, który zawiera oznaczony tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "znaczniki i dostęp do łącza" w temacie [Omówienie formantów Syslink](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Określa rozszerzony styl kontrolki łącza. Aby zapoznać się z listą rozszerzonych stylów systemu Windows, zobacz *dwExStyle* parametru [elementu CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) w Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki link. Zastosuj dowolną kombinację stylów kontrolek. Aby uzyskać więcej informacji, zobacz [typowe style formantów](/windows/win32/Controls/common-control-styles) w Windows SDK.

*cinania*<br/>
Określa rozmiar i położenie kontrolki łącza. Może to być obiekt [CRect](../../atl-mfc-shared/reference/crect-class.md) [lub struktura.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki link. Nie może mieć wartości NULL.

*nID*<br/>
Określa identyfikator kontrolki łącza.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli Inicjalizacja zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [tworzenia](#create) , aby zastosować rozszerzone stałe stylu systemu Windows.

Druga forma `CreateEx` metody jest przestarzała. Użyj pierwszego formularza, który określa parametr *lpszLinkMarkup* .

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a> CLinkCtrl::GetIdealHeight

Pobiera idealną wysokość kontrolki łącza.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Idealna wysokość formantu (w pikselach).

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)komunikatu Win32, zgodnie z opisem w Windows SDK.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a> CLinkCtrl::GetIdealSize

Oblicza preferowaną wysokość tekstu linku dla bieżącego formantu linku, w zależności od określonej szerokości linku.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parametry

*cxMaxWidth*\
podczas Maksymalna szerokość łącza (w pikselach).

*pSize*\
określoną Wskaźnik do struktury [rozmiaru](/windows/win32/api/windef/ns-windef-size) systemu Windows. Gdy ta metoda zwraca *, element członkowski w* `SIZE` strukturze zawiera idealną wysokość tekstu linku dla szerokości tekstu linku, która jest określona przez *cxMaxWidth*. Element członkowski *CX* struktury zawiera szerokość tekstu linku, która jest faktycznie wymagana.

### <a name="return-value"></a>Wartość zwracana

Preferowana wysokość tekstu łącza (w pikselach). Wartość zwracana jest taka sama jak wartość wartości składowej *cy* `SIZE` struktury.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem `GetIdealSize` metody, zobacz przykład w [CLinkCtrl:: Create](#create).

Ta metoda wysyła komunikat [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) , który jest opisany w Windows SDK.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a> CLinkCtrl:: GetItem

Pobiera Stany i atrybuty elementu kontrolki link.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do struktury [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) do odbierania informacji o elemencie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [LM_GETITEM](/windows/win32/Controls/lm-getitem)komunikatu Win32, zgodnie z opisem w Windows SDK.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a> CLinkCtrl:: GetItemID

Pobiera identyfikator elementu kontrolki łącza.

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

*iLink*<br/>
Indeks elementu kontrolki łącza.

*strID*<br/>
Obiekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) zawierający identyfikator określonego elementu.

*szID*<br/>
Ciąg zakończony znakiem null zawierający identyfikator określonego elementu.

*cchID*<br/>
Rozmiar w znakach w buforze *szID* .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

> [!NOTE]
> Ta funkcja zwraca również wartość FALSE, jeśli bufor *szID lub Strid* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera identyfikator określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w Windows SDK.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a> CLinkCtrl::GetItemState

Pobiera stan elementu kontrolki link.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Indeks elementu kontrolki łącza.

*pnState*<br/>
Wartość określonego elementu stanu.

*stateMask*<br/>
Kombinacja flag opisujących element stanu do pobrania. Aby uzyskać listę wartości, zobacz Opis `state` elementu członkowskiego w strukturze [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) . Elementy dozwolone są identyczne z dozwolonymi w programie `state` .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Pobiera wartość określonego stanu elementu określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w Windows SDK.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a> CLinkCtrl::GetItemUrl

Pobiera adres URL reprezentowany przez element sterowania linkiem.

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

*iLink*<br/>
Indeks elementu kontrolki łącza.

*strUrl*<br/>
Obiekt [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) zawierający adres URL reprezentowany przez określony element

*szUrl*<br/>
Ciąg zakończony znakiem null zawierający adres URL reprezentowany przez określony element

*cchUrl*<br/>
Rozmiar w znakach w buforze *szURL* .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

> [!NOTE]
> Ta funkcja zwraca również wartość FALSE, jeśli bufor *szUrl lub strUrl* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera adres URL reprezentowany przez określony element kontrolki linku. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) w Windows SDK.

## <a name="clinkctrlhittest"></a><a name="hittest"></a> CLinkCtrl::HitTest

Określa, czy użytkownik kliknął określone łącze.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parametry

*phti*<br/>
Wskaźnik do `LHITTESTINFO` struktury zawierającej wszystkie informacje o połączeniu klikniętym przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [LM_HITTEST](/windows/win32/Controls/lm-hittest)komunikatu Win32, zgodnie z opisem w Windows SDK.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a> CLinkCtrl:: SetItem

Ustawia Stany i atrybuty elementu kontrolki link.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do struktury [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) zawierającej informacje do ustawienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska implementuje zachowanie [LM_SETITEM](/windows/win32/Controls/lm-setitem)komunikatu Win32, zgodnie z opisem w Windows SDK.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a> CLinkCtrl:: setitemid

Pobiera identyfikator elementu kontrolki łącza.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Indeks elementu kontrolki łącza.

*szID*<br/>
Ciąg zakończony znakiem null zawierający identyfikator określonego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ustawia identyfikator określonego elementu sterowania linkiem. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w Windows SDK.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a> CLinkCtrl::SetItemState

Pobiera stan elementu kontrolki link.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Indeks elementu kontrolki łącza.

*pnState*<br/>
Wartość określonego elementu stanu.

*stateMask*<br/>
Kombinacja flag opisujących ustawiany element stanu. Aby uzyskać listę wartości, zobacz Opis `state` elementu członkowskiego w strukturze [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) . Elementy dozwolone są identyczne z dozwolonymi w programie `state` .

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ustawia wartość określonego stanu elementu określonego elementu sterującego łącza. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w Windows SDK.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a> CLinkCtrl::SetItemUrl

Ustawia adres URL reprezentowany przez element sterowania linkiem.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Indeks elementu kontrolki łącza.

*szUrl*<br/>
Ciąg zakończony znakiem null zawierający adres URL reprezentowany przez określony element

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Ustawia adres URL reprezentowany przez określony element kontrolki linku. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
