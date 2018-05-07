---
title: Klasa CLinkCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2312861a1b13ecb432c7893a27d72c61ecd78ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clinkctrl-class"></a>Klasa CLinkCtrl
Udostępnia funkcje formantu SysLink wspólne systemu Windows.  
  
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
|[CLinkCtrl::Create](#create)|Tworzy kontrolkę łącza i dołącza go do `CLinkCtrl` obiektu.|  
|[CLinkCtrl::CreateEx](#createex)|Tworzy kontrolkę łącza z rozszerzone style i dołącza go do `CLinkCtrl` obiektu.|  
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Pobiera idealne wysokość kontrolki łącza.|  
|[CLinkCtrl::GetIdealSize](#getidealsize)|Oblicza preferowana wysokość tekst łącza dla bieżącego formantu link, w zależności od określona szerokość łącza.|  
|[CLinkCtrl::GetItem](#getitem)|Pobiera Stany i atrybuty elementu kontrolki łącza.|  
|[CLinkCtrl::GetItemID](#getitemid)|Pobiera identyfikator elementu kontrolki łącza.|  
|[CLinkCtrl::GetItemState](#getitemstate)|Pobiera stan elementu kontrolki łącza.|  
|[CLinkCtrl::GetItemUrl](#getitemurl)|Pobiera adres URL reprezentowany przez element kontroli łączy.|  
|[CLinkCtrl::HitTest](#hittest)|Określa, czy użytkownik kliknął określone łącze.|  
|[CLinkCtrl::SetItem](#setitem)|Ustawia stanów i atrybuty elementu kontrolki łącza.|  
|[CLinkCtrl::SetItemID](#setitemid)|Ustawia identyfikator elementu kontrolki łącza.|  
|[CLinkCtrl::SetItemState](#setitemstate)|Ustawia stan elementu kontrolki łącza.|  
|[CLinkCtrl::SetItemUrl](#setitemurl)|Ustawia adres URL reprezentowany przez element kontroli łączy.|  
  
## <a name="remarks"></a>Uwagi  
 "Link kontroli" oferują wygodny sposób do osadzenia linki hipertekstowe w oknie. Rzeczywiste formant jest typu window, który renderuje oznaczony tekst i uruchamia odpowiednie aplikacje, gdy użytkownik kliknie łącze osadzonych. Wiele łączy są obsługiwane w jeden formant i można uzyskać, sprawdzając liczony od zera indeks.  
  
 Ten formant (i w związku z tym `CLinkCtrl` klasy) jest dostępna tylko dla programów uruchomionych w systemie Windows XP lub nowszy.  
  
 Aby uzyskać więcej informacji, zobacz [kontroli SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706) w zestawie Windows SDK.  
  
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
 Tworzy kontrolkę łącza i dołącza go do `CLinkCtrl` obiektu.  
  
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
 `lpszLinkMarkup`  
 Wskaźnik do zakończony zerem ciąg, który zawiera oznaczony jako tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczników i łącze Access" w temacie [omówienie formanty SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwStyle`  
 Określa styl kontrolki łącza. Zastosuj dowolną kombinację stylów formantu. Zobacz [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w `Windows SDK` Aby uzyskać więcej informacji.  
  
 `rect`  
 Określa rozmiar i położenie kontrolki łącza. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki łącza. Nie może być `NULL`.  
  
 `nID`  
 Określa identyfikator kontrolki łącza.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CLinkCtrl` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać `Create`, która tworzy kontrolkę łącza i dołącza go do `CLinkCtrl` obiektu. Jeśli chcesz style rozszerzonej systemu windows za pomocą formantu wywołanie [CLinkCtrl::CreateEx](#createex) zamiast `Create`.  
  
 Drugiej formy `Create` metoda jest przestarzała. Pierwszy formularz, który określa korzystać `lpszLinkMarkup` parametru.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu definiuje dwie zmienne o nazwie `m_Link1` i `m_Link2`, które umożliwiają dostęp do dwóch formantów łącza.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy jeden formant łącza na podstawie lokalizacji inny formant łącza. Moduł ładujący zasoby tworzy pierwszą kontrolkę łącze podczas uruchamiania aplikacji. Gdy aplikacja wprowadza OnInitDialog — metoda, możesz utworzyć drugi Kontrola łącza względem położenie pierwszego formantu łącza. Następnie możesz zmienić rozmiar formantu łącze do tekstu, który jest wyświetlany.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CLinkCtrl::CreateEx  
 Tworzy kontrolkę łącza z rozszerzone style i dołącza go do `CLinkCtrl` obiektu.  
  
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
 `lpszLinkMarkup`  
 Wskaźnik do zakończony zerem ciąg, który zawiera oznaczony jako tekst do wyświetlenia. Aby uzyskać więcej informacji, zobacz sekcję "Znaczników i łącze Access" w temacie [omówienie formanty SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwExStyle`  
 Określa styl rozszerzony kontrolki łącza. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa styl kontrolki łącza. Zastosuj dowolną kombinację stylów formantu. Aby uzyskać więcej informacji, zobacz [najczęściej używane style formantu](http://msdn.microsoft.com/library/windows/desktop/bb775498) w zestawie Windows SDK.  
  
 `rect`  
 Określa rozmiar i położenie kontrolki łącza. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](../../mfc/reference/rect-structure1.md) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki łącza. Nie może być `NULL`.  
  
 `nID`  
 Określa identyfikator kontrolki łącza.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzonej stałe styl systemu Windows.  
  
 Drugiej formy `CreateEx` metoda jest przestarzała. Pierwszy formularz, który określa korzystać `lpszLinkMarkup` parametru.  
  
##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight  
 Pobiera idealne wysokość kontrolki łącza.  
  
```  
int GetIdealHeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nadaje się doskonale wysokość formantu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [LM_GETIDEALHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb760716), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize  
 Oblicza preferowana wysokość tekst łącza dla bieżącego formantu link, w zależności od określona szerokość łącza.  
  
```  
int GetIdealSize(
    int cxMaxWidth,   
    SIZE* pSize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `cxMaxWidth`|Maksymalna szerokość łącze w pikselach.|  
|[out] * `pSize`|Wskaźnik do systemu Windows [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) struktury. Gdy metoda zwróci wartość, `cy` członkiem `SIZE` struktura zawiera łącze idealne wysokość tekstu szerokości tekstu łącza, określonej przez `cxMaxWidth`. `cx` Elementu członkowskiego struktury zawiera szerokość tekstu łącza, wymaganej w danym momencie.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Preferowana wysokość tekst łącza w pikselach. Zwracana wartość jest taka sama jak wartość `cy` członkiem `SIZE` struktury.  
  
### <a name="remarks"></a>Uwagi  
 Przykład `GetIdealSize` metody, zapoznaj się z przykładem w [CLinkCtrl::Create](#create).  
  
 Ta metoda wysyła [LM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760718) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getitem"></a>  CLinkCtrl::GetItem  
 Pobiera Stany i atrybuty elementu kontrolki łącza.  
  
```  
BOOL GetItem(PLITEM pItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury otrzymywanie informacji elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720), zgodnie z opisem w zestawie Windows SDK.  
  
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
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 *strID*  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający identyfikator określonego elementu.  
  
 *szID*  
 Zerem ciąg zawierający identyfikator określonego elementu.  
  
 *cchID*  
 Rozmiar w znakach *szID* buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
> [!NOTE]
>  Ta funkcja zwraca również wartość **FALSE** Jeśli bufor o *szID lub strID* jest mniejszy niż **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Uwagi  
 Pobiera identyfikator elementu sterowania łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) w zestawie Windows SDK.  
  
##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState  
 Pobiera stan elementu kontrolki łącza.  
  
```  
BOOL GetItemState(
    int iLink,  
    UINT* pnState,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 `pnState`  
 Wartość elementu określonego stanu.  
  
 `stateMask`  
 Kombinacja flagi opisujące stan elementy do pobrania. Aby uzyskać listę wartości, zobacz opis **stanu** element członkowski w [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury. Dopuszczalne elementy są identyczne jak dozwolone w **stanu**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Pobiera wartość elementu określonego stanu elementu sterowania łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) w zestawie Windows SDK.  
  
##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl  
 Pobiera adres URL reprezentowany przez element kontroli łączy.  
  
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
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 `strUrl`  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) obiekt zawierający adres URL reprezentowany przez określony element  
  
 `szUrl`  
 Zerem ciąg zawierający adres URL reprezentowany przez określony element  
  
 *cchUrl*  
 Rozmiar w znakach *szURL* buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
> [!NOTE]
>  Ta funkcja zwraca również wartość **FALSE** Jeśli bufor o *szUrl lub strUrl* jest mniejszy niż **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Uwagi  
 Pobiera adres URL reprezentowanego przez określone łącze element kontroli. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) w zestawie Windows SDK.  
  
##  <a name="hittest"></a>  CLinkCtrl::HitTest  
 Określa, czy użytkownik kliknął określone łącze.  
  
```  
BOOL HitTest(PLHITTESTINFO phti) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *phti*  
 Wskaźnik do **LHITTESTINFO** struktury zawierającej informacje o łączu użytkownik kliknął.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [LM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb760722), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setitem"></a>  CLinkCtrl::SetItem  
 Ustawia stanów i atrybuty elementu kontrolki łącza.  
  
```  
BOOL SetItem(PLITEM pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury zawierającej informacji do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setitemid"></a>  CLinkCtrl::SetItemID  
 Pobiera identyfikator elementu kontrolki łącza.  
  
```  
BOOL SetItemID(
    int iLink,  
    LPCWSTR szID);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 *szID*  
 Zerem ciąg zawierający identyfikator określonego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia identyfikator elementu sterowania łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) w zestawie Windows SDK.  
  
##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState  
 Pobiera stan elementu kontrolki łącza.  
  
```  
BOOL SetItemState(
    int iLink,  
    UINT state,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 `pnState`  
 Wartość elementu określonego stanu ustawiany.  
  
 `stateMask`  
 Kombinacja flagi opisujące element stanu ustawiany. Aby uzyskać listę wartości, zobacz opis **stanu** element członkowski w [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) struktury. Dopuszczalne elementy są identyczne jak dozwolone w **stanu**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia wartość elementu określonego stanu elementu sterowania łącze. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) w zestawie Windows SDK.  
  
##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl  
 Ustawia adres URL reprezentowany przez element kontroli łączy.  
  
```  
BOOL SetItemUrl(
    int iLink,  
    LPCWSTR szUrl);
```  
  
### <a name="parameters"></a>Parametry  
 `iLink`  
 Indeks elementu kontrolki łącza.  
  
 `szUrl`  
 Zerem ciąg zawierający adres URL reprezentowany przez określony element  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **TRUE** w przypadku powodzenia **FALSE** w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia adres URL reprezentowanego przez określone łącze element kontroli. Aby uzyskać więcej informacji, zobacz komunikat Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)
