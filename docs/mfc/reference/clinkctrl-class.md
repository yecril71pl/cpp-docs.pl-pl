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
ms.openlocfilehash: b24b92006b73dff2ae9f091256ef8401efc64fe9
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178048"
---
# <a name="clinkctrl-class"></a>Klasa CLinkCtrl

Oferuje funkcje formantu typowego SysLink Windows.

## <a name="syntax"></a>Składnia

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Konstruuje `CLinkCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|Tworzy formant łącza i dołącza je do `CLinkCtrl` obiektu.|
|[CLinkCtrl::CreateEx](#createex)|Tworzy formant łącza przy użyciu rozszerzonych stylów i dołącza je do `CLinkCtrl` obiektu.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Pobiera idealne wysokość kontrolki łącza.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Oblicza preferowana wysokość tekstu linku dla bieżącego kontrolki linku w zależności od określonej szerokości łącza.|
|[CLinkCtrl::GetItem](#getitem)|Pobiera Stany i atrybuty element kontroli łączy.|
|[CLinkCtrl::GetItemID](#getitemid)|Pobiera identyfikator elementu kontrolki łącza.|
|[CLinkCtrl::GetItemState](#getitemstate)|Pobiera stan element kontroli łączy.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Pobiera adres URL, reprezentowane przez element kontroli łączy.|
|[CLinkCtrl::HitTest](#hittest)|Określa, czy użytkownik kliknął element określone łącze.|
|[CLinkCtrl::SetItem](#setitem)|Ustawia stanów i atrybuty element kontroli łączy.|
|[CLinkCtrl::SetItemID](#setitemid)|Określa identyfikator elementu kontrolki łącza.|
|[CLinkCtrl::SetItemState](#setitemstate)|Ustawia stan element kontroli łączy.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Ustawia adres URL, reprezentowane przez element kontroli łączy.|

## <a name="remarks"></a>Uwagi

"Link kontroli" zapewnia wygodny sposób osadzania linki hipertekstowe w oknie. Rzeczywistego formantu jest oknem które powoduje wyświetlenie tekstu oznaczone w górę i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie łącze osadzonych. Wiele połączeń są obsługiwane w ramach jednego formantu i może zostać oceniony przez liczony od zera indeks.

Ta kontrolka (i w związku z tym `CLinkCtrl` klasy) jest dostępna tylko dla programów uruchomionych w obszarze Windows XP lub nowszy.

Aby uzyskać więcej informacji, zobacz [kontroli SysLink](/windows/desktop/Controls/syslink-overview) w zestawie Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

Konstruuje `CLinkCtrl` obiektu.

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

Tworzy formant łącza i dołącza je do `CLinkCtrl` obiektu.

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
Wskaźnik na ciąg zakończony zerem, zawierający oznaczone tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczników i łącze dostępu", która znajduje się w temacie [Przegląd formanty SysLink](/windows/desktop/Controls/syslink-overview).

*dwStyle*<br/>
Określa styl kontrolki łącza. Zastosuj dowolną kombinację style kontrolki. Zobacz [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles) w `Windows SDK` Aby uzyskać więcej informacji.

*Rect*<br/>
Określa rozmiar i położenie kontrolki łącza. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki łącza. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki łącza.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli inicjowanie się powiodła. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Konstruowanie `CLinkCtrl` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, a następnie wywołać `Create`, która tworzy formant łączy i dołącza go do `CLinkCtrl` obiektu. Style rozszerzone systemu windows za pomocą formantu należy wywołać [CLinkCtrl::CreateEx](#createex) zamiast `Create`.

Drugiej formy `Create` metoda jest przestarzała. Użyj pierwszego formularza, który określa *lpszLinkMarkup* parametru.

### <a name="example"></a>Przykład

Poniższy przykład kodu definiuje dwie zmienne, o nazwie `m_Link1` i `m_Link2`, które umożliwiają dostęp do dwóch formantów łączy.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Przykład

Poniższy przykład kodu tworzy jeden formant łączy na podstawie lokalizacji innej kontrolki łącza. Moduł ładujący zasobów tworzy pierwszy formant łącza, podczas uruchamiania aplikacji. Gdy aplikacja wprowadza oninitdialog — metoda, utworzysz drugi formant łącza względem pozycji pierwszy formant łącza. Następnie można zmienić rozmiar drugi formant łącza do tekstu, który jest wyświetlany.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

Tworzy formant łącza przy użyciu rozszerzonych stylów i dołącza je do `CLinkCtrl` obiektu.

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
Wskaźnik na ciąg zakończony zerem, zawierający oznaczone tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczników i łącze dostępu", która znajduje się w temacie [Przegląd formanty SysLink](/windows/desktop/Controls/syslink-overview).

*dwExStyle*<br/>
Określa styl rozszerzony kontrolki łącza. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.

*dwStyle*<br/>
Określa styl kontrolki łącza. Zastosuj dowolną kombinację style kontrolki. Aby uzyskać więcej informacji, zobacz [najczęściej używane style kontrolki](/windows/desktop/Controls/common-control-styles) w zestawie Windows SDK.

*Rect*<br/>
Określa rozmiar i położenie kontrolki łącza. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) struktury.

*pParentWnd*<br/>
Określa okno nadrzędne kontrolki łącza. Nie może być równa NULL.

*nID*<br/>
Określa identyfikator kontrolki łącza.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli inicjowanie się powiodła. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzonej stałe style Windows.

Drugiej formy `CreateEx` metoda jest przestarzała. Użyj pierwszego formularza, który określa *lpszLinkMarkup* parametru.

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

Pobiera idealne wysokość kontrolki łącza.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Idealna wysokość formantu w pikselach.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

Oblicza preferowana wysokość tekstu linku dla bieżącego kontrolki linku w zależności od określonej szerokości łącza.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*cxMaxWidth*|[in] Maksymalna szerokość łącza, w pikselach.|
|[out] \* *pSize*|Wskaźnik do Windows [rozmiar](/windows/desktop/api/windef/ns-windef-tagsize) struktury. Po powrocie z tej metody *cy* członkiem `SIZE` struktura zawiera wysokość tekstu łącza idealne rozwiązanie dla szerokość tekstu łącza, który jest określony przez *cxMaxWidth*. *Cx* element członkowski struktury zawiera szerokość tekstu łącza, wymaganej w danym momencie.|

### <a name="return-value"></a>Wartość zwracana

Preferowany wysokość tekstu łącza, w pikselach. Zwracana wartość jest taka sama jak wartość *cy* członkiem `SIZE` struktury.

### <a name="remarks"></a>Uwagi

Na przykład `GetIdealSize` metody, zobacz przykład w [CLinkCtrl::Create](#create).

Ta metoda wysyła [LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize) komunikat, który jest opisany w zestawie Windows SDK.

##  <a name="getitem"></a>  CLinkCtrl::GetItem

Pobiera Stany i atrybuty element kontroli łączy.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury, aby otrzymywać informacje o elementach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem), zgodnie z opisem w zestawie Windows SDK.

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

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
A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający identyfikator określonego elementu.

*szID*<br/>
Ciąg zakończony wartością null zawierający identyfikator określonego elementu.

*cchID*<br/>
Rozmiar w znakach *szID* buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

> [!NOTE]
>  Ta funkcja także zwraca wartość FALSE, jeśli bufor o *szID lub strID* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera identyfikator elementu sterowania jedno łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) w zestawie Windows SDK.

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

Pobiera stan element kontroli łączy.

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
Wartość elementu określonego stanu.

*stateMask*<br/>
Kombinacja flagi opisujące element stanu, które można pobrać. Aby uzyskać listę wartości, zobacz opis `state` elementu członkowskiego w [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury. Dopuszczalne elementy są identyczne z tymi dozwolone w `state`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Pobiera wartość elementu określonego stanu elementu sterowania jedno łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) w zestawie Windows SDK.

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

Pobiera adres URL, reprezentowane przez element kontroli łączy.

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
A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL, reprezentowane przez określony element

*szUrl*<br/>
Ciąg zakończony wartością null zawierający adres URL, reprezentowane przez określony element

*cchUrl*<br/>
Rozmiar w znakach *szURL* buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

> [!NOTE]
>  Ta funkcja także zwraca wartość FALSE, jeśli bufor o *szUrl lub strUrl* jest mniejszy niż MAX_LINKID_TEXT.

### <a name="remarks"></a>Uwagi

Pobiera adres URL reprezentowanego przez określone łącze elementu kontrolki. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) w zestawie Windows SDK.

##  <a name="hittest"></a>  CLinkCtrl::HitTest

Określa, jeśli użytkownik kliknął element określone łącze.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parametry

*phti*<br/>
Wskaźnik do `LHITTESTINFO` struktury zawierającej wszystkie informacje o łączu użytkownik kliknął element.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [LM_HITTEST](/windows/desktop/Controls/lm-hittest), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setitem"></a>  CLinkCtrl::SetItem

Ustawia stanów i atrybuty element kontroli łączy.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parametry

*pItem*<br/>
Wskaźnik do [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury zawierające informacje, które można ustawić.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem), zgodnie z opisem w zestawie Windows SDK.

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

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
Ciąg zakończony wartością null zawierający identyfikator określonego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Określa identyfikator elementu sterowania jedno łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) w zestawie Windows SDK.

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

Pobiera stan element kontroli łączy.

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
Wartość elementu określonego stanu, zostanie ustawiony.

*stateMask*<br/>
Kombinacja flagi opisujące element stan zostanie ustawiony. Aby uzyskać listę wartości, zobacz opis `state` elementu członkowskiego w [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) struktury. Dopuszczalne elementy są identyczne z tymi dozwolone w `state`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ustawia wartość elementu określonego stanu elementu sterowania jedno łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) w zestawie Windows SDK.

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

Ustawia adres URL, reprezentowane przez element kontroli łączy.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parametry

*iLink*<br/>
Indeks elementu kontrolki łącza.

*szUrl*<br/>
Ciąg zakończony wartością null zawierający adres URL, reprezentowane przez określony element

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ustawia adres URL, reprezentowane przez element kontroli określone łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
