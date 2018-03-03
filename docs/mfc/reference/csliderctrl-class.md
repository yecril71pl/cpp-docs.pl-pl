---
title: "Csliderctrl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2788777b9a5014790e094cf39871b3e4d40750fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csliderctrl-class"></a>Csliderctrl — klasa
Udostępnia funkcje systemu Windows wspólnej suwaka.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Konstruuje `CSliderCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|Usuwa bieżące zaznaczenie w kontrolce slider.|  
|[CSliderCtrl::ClearTics](#cleartics)|Usuwa bieżący znaczników za pomocą formantu suwaka.|  
|[CSliderCtrl::Create](#create)|Tworzy formantu suwaka i dołącza go do `CSliderCtrl` obiektu.|  
|[CSliderCtrl::CreateEx](#createex)|Tworzy kontrolkę suwak w określonym stylu rozszerzonej systemu Windows i dołącza go do `CSliderCtrl` obiektu.|  
|[CSliderCtrl::GetBuddy](#getbuddy)|Pobiera dojścia do okna buddy formantu suwaka w podanej lokalizacji.|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Pobiera informacje o rozmiarze kanał kontrolny suwaka.|  
|[CSliderCtrl::GetLineSize](#getlinesize)|Pobiera rozmiar wiersza formantu suwaka.|  
|[CSliderCtrl::GetNumTics](#getnumtics)|Pobiera liczbę znaczników w kontrolce slider.|  
|[CSliderCtrl::GetPageSize](#getpagesize)|Pobiera rozmiar strony formantu suwaka.|  
|[CSliderCtrl::GetPos](#getpos)|Pobiera bieżące położenie suwaka.|  
|[CSliderCtrl::GetRange](#getrange)|Pobiera minimalną i maksymalną pozycji suwaka.|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|Pobiera maksymalną położenie suwaka.|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|Pobiera minimalną położenie suwaka.|  
|[CSliderCtrl::GetSelection](#getselection)|Pobiera zakres bieżącego zaznaczenia.|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|Pobiera długość suwak w bieżącym TrackBar — formant.|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Pobiera rozmiar przycisku przewijania suwaka.|  
|[CSliderCtrl::GetTic](#gettic)|Pobiera pozycję określonego znacznika.|  
|[CSliderCtrl::GetTicArray](#getticarray)|Pobiera tablicę pozycji znaczników osi dla kontrolki suwaka.|  
|[CSliderCtrl::GetTicPos](#getticpos)|Pobiera położenie znacznika określony we współrzędnych klienta.|  
|[CSliderCtrl::GetToolTips](#gettooltips)|Pobiera dojścia do formantu tooltip przypisany do kontrolki suwaka, jeśli istnieje.|  
|[CSliderCtrl::SetBuddy](#setbuddy)|Przypisuje okno jako partner okna dla kontrolki suwaka.|  
|[CSliderCtrl::SetLineSize](#setlinesize)|Ustawia rozmiar linii formantu suwaka.|  
|[CSliderCtrl::SetPageSize](#setpagesize)|Ustawia rozmiar strony formantu suwaka.|  
|[CSliderCtrl::SetPos](#setpos)|Ustawia bieżący pozycji suwaka.|  
|[CSliderCtrl::SetRange](#setrange)|Ustawia położenie minimalną i maksymalną dla kontrolki slider.|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|Ustawia maksymalną położenie suwaka.|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|Ustawia minimalną położenie suwaka.|  
|[CSliderCtrl::SetSelection](#setselection)|Ustawia zakres bieżącego zaznaczenia.|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|Ustawia długość suwak w bieżącym formancie trackbar.|  
|[CSliderCtrl::SetTic](#settic)|Ustawia położenie określonego znacznika.|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|Określa częstotliwość znaczników znaczniki na przyrost formantu suwaka.|  
|[CSliderCtrl::SetTipSide](#settipside)|Pozycji formantu tooltip używany przez TrackBar — formant.|  
|[CSliderCtrl::SetToolTips](#settooltips)|Przypisuje formantu tooltip do formantu suwaka.|  
  
## <a name="remarks"></a>Uwagi  
 "Suwaka" (trackbar) to okno zawierające suwaka i opcjonalnie znaczników. Gdy użytkownik przesuwa suwak, za pomocą myszy lub klucze kierunku, formantu wysyła komunikaty powiadomień, aby wskazać zmianę.  
  
 Formanty suwaka są przydatne, gdy użytkownik ma zaznacz wartość discrete lub zestaw kolejnych wartości w zakresie. Na przykład można użyć formantu suwaka umożliwia użytkownikom ustawić częstotliwość powtarzania klawiatury za pomocą suwaka do danego znacznika.  
  
 Ten formant (i w związku z tym `CSliderCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Suwak jest przesuwany w przyrostach określające podczas jego tworzenia. Na przykład, jeśli określono, że suwak powinny mieć zakresu pięć, suwak można tylko zajmują sześciu położenia: pozycji suwaka i jedną pozycję dla każdego kolejnego przyrostu wartości z zakresu po lewej stronie. Zazwyczaj każdego z tych pozycji jest identyfikowany przez znacznika.  
  
 Utwórz suwaka przy użyciu konstruktora i **Utwórz** funkcji członkowskiej klasy `CSliderCtrl`. Po utworzeniu formantu suwaka, można użyć funkcji Członkowskich w `CSliderCtrl` zmiany wielu jego właściwości. Zmiany, które można wprowadzić obejmują ustawienie pozycji minimalną i maksymalną dla suwaka, rysowania znaczniki ustawienie wybranego zakresu i położenia suwaka.  
  
 Aby uzyskać więcej informacji na temat używania `CSliderCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="clearsel"></a>CSliderCtrl::ClearSel  
 Usuwa bieżące zaznaczenie w kontrolce slider.  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRedraw`  
 Narysuj element ponownie flagi. Jeśli ten parametr ma **TRUE**, suwak jest narysowany ponownie po wyboru jest wyczyszczone; w przeciwnym razie nie jest rysowane suwaka.  
  
##  <a name="cleartics"></a>CSliderCtrl::ClearTics  
 Usuwa bieżący znaczników za pomocą formantu suwaka.  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRedraw`  
 Narysuj element ponownie flagi. Jeśli ten parametr ma **TRUE**, suwak jest narysowany ponownie po znaczniki zostały wyczyszczone; w przeciwnym razie nie jest rysowane suwaka.  
  
##  <a name="create"></a>CSliderCtrl::Create  
 Tworzy formantu suwaka i dołącza go do `CSliderCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl formantu suwaka. Zastosuj dowolną kombinację [style formantu suwaka](http://msdn.microsoft.com/library/windows/desktop/bb760147), które zostały opisane w zestawie SDK systemu Windows do formantu.  
  
 `rect`  
 Określa rozmiar i położenie kontrolki suwaka. Może być albo [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury.  
  
 `pParentWnd`  
 Określa okno nadrzędne kontrolki suwaka, zwykle `CDialog`. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu suwaka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli inicjowanie zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CSliderCtrl` w dwóch krokach. Najpierw należy wywołać konstruktora, a następnie wywołać **Utwórz**, która tworzy suwaka i dołącza go do `CSliderCtrl` obiektu.  
  
 W zależności od wartości `dwStyle`, suwak może mieć orientacji pionowej lub poziomej. Znaczniki osi po obu stronach może mieć obu stronach lub nie. Można go również używane do określania zakresu kolejnych wartości.  
  
 Aby zastosować rozszerzone Style okna dla kontrolki suwaka, wywołaj [CreateEx](#createex) zamiast **Utwórz**.  
  
##  <a name="createex"></a>CSliderCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CSliderCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa styl formantu suwaka. Zastosuj dowolną kombinację [style formantu suwaka](http://msdn.microsoft.com/library/windows/desktop/bb760147), które zostały opisane w zestawie SDK systemu Windows do formantu.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 Konstruuje `CSliderCtrl` obiektu.  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 Pobiera dojścia do okna buddy formantu suwaka w podanej lokalizacji.  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `fLocation`  
 Wartość logiczna, która wskazuje, które dwóch buddy okna dojść do pobrania. Może to być jedna z następujących wartości:  
  
- **Wartość TRUE,** pobiera dojścia do buddy po lewej stronie suwaka. Jeśli używa suwaka `TBS_VERT` styl komunikatu pobierze buddy powyżej suwaka.  
  
- **FALSE** pobiera dojścia do przyjaciół z prawej strony suwaka. Jeśli używa suwaka `TBS_VERT` styl komunikatu pobierze buddy poniżej suwaka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno buddy w lokalizacji określonej przez `fLocation`, lub **NULL** Jeśli zaprzyjaźnione okno cyklu nie istnieje w tej lokalizacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178), zgodnie z opisem w zestawie Windows SDK. Opis elementu style formantu suwaka, zobacz [stylów formantu Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) w zestawie Windows SDK.  
  
##  <a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 Pobiera rozmiar i położenie prostokątem dla kontrolki suwaka kanału.  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Wskaźnik do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który zawiera rozmiar i położenie kanału do ograniczenia prostokąt po powrocie z funkcji.  
  
### <a name="remarks"></a>Uwagi  
 Kanał jest obszar za pośrednictwem zostanie przesunięty suwak i zawierający wyróżnienie, gdy zaznaczony jest zakres.  
  
##  <a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 Pobiera rozmiar wiersza dla kontrolki suwaka.  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar wiersza dla kontrolki suwaka.  
  
### <a name="remarks"></a>Uwagi  
 Ma wpływ na rozmiar wiersza, ile suwak przenosi dla **TB_LINEUP** i **TB_LINEDOWN** powiadomienia. Ustawieniem domyślnym dla rozmiar wiersza to 1.  
  
##  <a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 Pobiera liczbę znaczników w kontrolce slider.  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaczników osi suwaka.  
  
##  <a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 Pobiera rozmiar strony dla kontrolki suwaka.  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar strony dla kontrolki suwaka.  
  
### <a name="remarks"></a>Uwagi  
 Ma wpływ na rozmiar strony, ile suwak przenosi dla **TB_PAGEUP** i **TB_PAGEDOWN** powiadomienia.  
  
##  <a name="getpos"></a>CSliderCtrl::GetPos  
 Pobiera bieżący pozycji suwaka w kontrolce slider.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca pozycja.  
  
##  <a name="getrange"></a>CSliderCtrl::GetRange  
 Pobiera maksymalne i minimalne dla pozycji suwaka w kontrolce slider.  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Odwołanie do liczba całkowita, która odbiera minimalna pozycji.  
  
 `nMax`  
 Odwołanie do liczba całkowita, która odbiera maksymalną pozycji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja skopiowanie wartości do liczb całkowitych, odwołuje się `nMin` i `nMax`.  
  
##  <a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 Pobiera maksymalną położenie suwaka w kontrolce slider.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja maksymalną formantu.  
  
##  <a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 Pobiera minimalną położenie suwaka w kontrolce slider.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja minimalna formantu.  
  
##  <a name="getselection"></a>CSliderCtrl::GetSelection  
 Pobiera początkowy i końcowy pozycji bieżące zaznaczenie w kontrolce slider.  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Odwołanie do liczba całkowita, która odbiera pozycja początkowa bieżącego zaznaczenia.  
  
 `nMax`  
 Odwołanie do liczba całkowita, która odbiera pozycji końcowej bieżącego zaznaczenia.  
  
##  <a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 Pobiera długość suwak w bieżącym TrackBar — formant.  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość suwak w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 Pobiera rozmiar i położenie prostokątem dla suwak w kontrolce slider.  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Wskaźnik do `CRect` obiekt, który zawiera prostokątem na suwaku, gdy funkcja zwraca wartość.  
  
##  <a name="gettic"></a>CSliderCtrl::GetTic  
 Pobiera położenie znacznika w kontrolce slider.  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Liczony od zera indeks identyfikacji znacznika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja określonego znacznika lub - 1, gdy `nTic` nie określa prawidłowego indeksu.  
  
##  <a name="getticarray"></a>CSliderCtrl::GetTicArray  
 Pobiera adres tablicę zawierającą położenie znaczników osi dla kontrolki suwaka.  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adres tablicę zawierającą pozycje znacznik osi dla kontrolki suwaka.  
  
##  <a name="getticpos"></a>CSliderCtrl::GetTicPos  
 Pobiera bieżącą pozycję fizycznych znacznika w kontrolce slider.  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Liczony od zera indeks identyfikacji znacznika.  
  
### <a name="return-value"></a>Wartość zwracana  
 Fizyczny pozycja, we współrzędnych klienta określonego znacznika lub - 1, gdy `nTic` nie określa prawidłowego indeksu.  
  
##  <a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 Pobiera dojścia do formantu tooltip przypisany do kontrolki suwaka, jeśli istnieje.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiekt, lub **NULL** Jeśli etykietki narzędzi nie są używane. Jeśli nie wykorzystuje suwaka **TBS_TOOLTIPS** styl, jest zwracana wartość **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209), zgodnie z opisem w zestawie Windows SDK. Należy pamiętać, że ta funkcja elementu członkowskiego zwraca `CToolTipCtrl` obiektu zamiast dojścia do formantu.  
  
 Opis elementu style formantu suwaka, zobacz [stylów formantu Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) w zestawie Windows SDK.  
  
##  <a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 Przypisuje okno jako partner okna dla kontrolki suwaka.  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndBuddy`  
 Wskaźnik do `CWnd` obiekt, który zostanie ustawiony jako partner kontrolka suwaka.  
  
 `fLocation`  
 Wartość określający lokalizację, w której do wyświetlenia okna buddy. Ta wartość może być jedną z następujących czynności:  
  
- **Wartość TRUE,** buddy pojawi się na lewo od elemencie trackbar, jeśli używa TrackBar — formant `TBS_HORZ` stylu. Jeśli używany w elemencie trackbar `TBS_VERT` styl buddy pojawia się powyżej TrackBar — formant.  
  
- **FALSE** buddy pojawi się po prawej stronie w elemencie trackbar, jeśli używa TrackBar — formant `TBS_HORZ` stylu. Jeśli używany w elemencie trackbar `TBS_VERT` styl buddy pojawia się poniżej TrackBar — formant.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który został wcześniej przypisany do kontrolki suwaka w tej lokalizacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213), zgodnie z opisem w zestawie Windows SDK. Należy pamiętać, że ta funkcja członkowska używa wskaźników do `CWnd` dojścia okna dla jej wartości zwracanej i parametr, a nie obiektów.  
  
 Opis elementu style formantu suwaka, zobacz [stylów formantu Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) w zestawie Windows SDK.  
  
##  <a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 Ustawia rozmiar linii dla kontrolki suwaka.  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nSize`  
 Nowy rozmiar wiersza suwaka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni rozmiar wiersza.  
  
### <a name="remarks"></a>Uwagi  
 Ma wpływ na rozmiar wiersza, ile suwak przenosi dla **TB_LINEUP** i **TB_LINEDOWN** powiadomienia.  
  
##  <a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 Ustawia rozmiar strony dla kontrolki suwaka.  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>Parametry  
 `nSize`  
 Nowy rozmiar strony suwaka.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie rozmiar strony.  
  
### <a name="remarks"></a>Uwagi  
 Ma wpływ na rozmiar strony, ile suwak przenosi dla **TB_PAGEUP** i **TB_PAGEDOWN** powiadomienia.  
  
##  <a name="setpos"></a>CSliderCtrl::SetPos  
 Ustawia bieżący pozycji suwaka w kontrolce slider.  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Określa nowe położenie suwaka.  
  
##  <a name="setrange"></a>CSliderCtrl::SetRange  
 Ustawia zakresu (pozycje minimalną i maksymalną) suwak w kontrolce slider.  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimalna pozycja suwaka.  
  
 `nMax`  
 Maksymalna pozycja suwaka.  
  
 `bRedraw`  
 Flaga ponownego rysowania. Jeśli ten parametr ma **TRUE**, suwak jest narysowany ponownie po ustawiono zakres; w przeciwnym razie nie jest rysowane suwaka.  
  
##  <a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 Ustawia maksymalną wielkość zakresu suwak w kontrolce slider.  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMax`  
 Maksymalna pozycja suwaka.  
  
 `bRedraw`  
 Flaga ponownego rysowania. Jeśli ten parametr ma **TRUE**, suwak jest narysowany ponownie po ustawiono zakres; w przeciwnym razie nie jest rysowane suwaka.  
  
##  <a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
 Ustawia minimalny zakres suwak w kontrolce slider.  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Minimalna pozycja suwaka.  
  
 `bRedraw`  
 Flaga ponownego rysowania. Jeśli ten parametr ma **TRUE**, suwak jest narysowany ponownie po ustawiono zakres; w przeciwnym razie nie jest rysowane suwaka.  
  
##  <a name="setselection"></a>CSliderCtrl::SetSelection  
 Ustawia położenie datę początkową i końcową dla bieżącego zaznaczenia w kontrolce slider.  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `nMin`  
 Pozycja początkowa suwaka.  
  
 `nMax`  
 Pozycja końcowa suwaka.  
  
##  <a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 Ustawia długość suwak w bieżącym formancie trackbar.  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`nLength`|Długość suwak w pikselach.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wymaga, aby mieć ustawioną TrackBar — formant [TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147) stylu.  
  
 Ta metoda wysyła [TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_sliderCtrl`, która jest używane do dostępu bieżącego TrackBar — formant. W przykładzie zdefiniowano także zmiennej, `thumbLength`, która jest używana do przechowywania domyślną długość TrackBar — formant thumb składnika. Te zmienne są używane w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia składnik thumb TrackBar — formant dwukrotnie długość jego domyślny.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>CSliderCtrl::SetTic  
 Ustawia położenie znacznika w kontrolce slider.  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>Parametry  
 `nTic`  
 Pozycja znacznika. Ten parametr należy określić wartość dodatnią.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ustawiono znacznika; w przeciwnym razie 0.  
  
##  <a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 Określa częstotliwość, z których znaczników są widoczne w suwaka.  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>Parametry  
 *nFreq*  
 Częstotliwość znaczników.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład jeśli częstotliwość jest równa 2, co inne przyrostem suwaka zakresu jest wyświetlany znacznika. Domyślne ustawienie częstotliwości to 1 (co przyrostu w zakresie jest skojarzony z znacznika).  
  
 Należy utworzyć kontrolki z `TBS_AUTOTICKS` styl, aby użyć tej funkcji. Aby uzyskać więcej informacji, zobacz [CSliderCtrl::Create](#create).  
  
##  <a name="settipside"></a>CSliderCtrl::SetTipSide  
 Pozycji formantu tooltip używany przez TrackBar — formant.  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>Parametry  
 `nLocation`  
 Wartość reprezentująca lokalizację, w której można wyświetlić formantu tooltip. Listę możliwych wartości wyświetlony komunikat Win32 [TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która reprezentuje poprzedniej lokalizacji formantu tooltip. Zwracana wartość jest równa jedną z możliwych wartości dla `nLocation`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 **TBM_SETTIPSIDE**, zgodnie z opisem w zestawie Windows SDK. Określa zasady używające **TBS_TOOLTIPS** styl wyświetlania etykietek narzędzi. Opis elementu style formantu suwaka, zobacz [stylów formantu Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) w zestawie Windows SDK.  
  
##  <a name="settooltips"></a>CSliderCtrl::SetToolTips  
 Przypisuje formantu tooltip do formantu suwaka.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parametry  
 `pWndTip`  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiekt zawierający etykietki narzędzi, aby za pomocą suwaka.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242), zgodnie z opisem w zestawie Windows SDK. Po utworzeniu formantu suwaka z **TBS_TOOLTIPS** stylu, tworzy domyślną formantu tooltip, obok suwaka, wyświetlanie bieżące położenie suwaka. Opis elementu style formantu suwaka, zobacz [stylów formantu Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL2 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CProgressCtrl](../../mfc/reference/cprogressctrl-class.md)
