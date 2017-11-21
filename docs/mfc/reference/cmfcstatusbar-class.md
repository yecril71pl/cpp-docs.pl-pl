---
title: "Klasa CMFCStatusBar — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
dev_langs: C++
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 734097d8fffcbe21f17b68432d6233a03b11a28a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar — klasa
`CMFCStatusBar` Klasa implementuje paska stanu, podobnie jak `CStatusBar` klasy. Jednak `CMFCStatusBar` klasa ma funkcje nie są oferowane przez `CStatusBar` klasy, takie jak możliwość wyświetlania obrazów, animacji i paski postępu; oraz możliwość odpowiadanie na myszy kliknie dwukrotnie. 

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]   
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCStatusBar::CreateEx](#createex)|Tworzy pasek sterowania i dołącza go do [CPane](../../mfc/reference/cpane-class.md) obiektu. (Przesłania [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Określa, czy innego okienka mogą być dynamicznie między w tym okienku i dodaje ramka nadrzędny. (Przesłania [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Włącza lub wyłącza obsługę myszy kliknie pasek stanu.|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Wyświetla pasek postępu w okienku określony.|  
|[CMFCStatusBar::GetCount](#getcount)|Zwraca liczbę okienka na pasku stanu.|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Zwraca styl panelu. (Przesłania [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Zwraca szerokość w pikselach określonego okienku paska stanu.|  
|[CMFCStatusBar::GetTipText](#gettiptext)|Zwraca tekst wskazówki dla określonego okienku paska stanu.|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Okienko określony unieważnia i ponownie rysuje zawartość.|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Metoda wywoływana przez platformę przed tworzeniem okna systemu Windows dołączona do tego `CWnd` obiektu. (Przesłania [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Przypisuje animacji okienko określony.|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Ustawia kolor tła dla określonego okienku paska stanu.|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Ustawia ikony wskaźnika określonego okienku paska stanu.|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Ustawia bieżący postęp pasek postępu dla określonego okienku paska stanu.|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Ustawia styl okienka. (Przesłania [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Ustawia kolor tekstu dla określonego okienku paska stanu.|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Określa szerokość w pikselach określonego okienku paska stanu.|  
|[CMFCStatusBar::SetTipText](#settiptext)|Ustawia tekst wskazówki dla określonego okienku paska stanu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Wywoływane przez platformę, gdy ponownie go rysuje okienku paska stanu.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższy diagram przedstawia rysunek paska stanu z [próbka Demo paska stanu](../../visual-cpp-samples.md) aplikacji.  
  
 ![Przykład CMFCStatusBar —](../../mfc/reference/media/cmfcstatusbar.png "CMFCStatusBar —")  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zmiennych lokalnych, używanych przez aplikację do wywołania różnych metod `CMFCStatusBar` klasy. Te zmienne są zadeklarowane w StatusBarDemoView.h. Ramki głównej jest zadeklarowana w MainFrm.h, dokument jest zadeklarowana w StatusBarDemoDoc.h i widoku jest zadeklarowana w StatusBarDemoView.h. Następujący fragment kodu jest częścią [próbka Demo paska stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać odwołania do `CMFCStatusBar` obiektu dzięki zastosowaniu `GetStatusBar` w MainFrm.h, a następnie wywołaniem tej metody z metody `GetStatusBar` w StatusBarDemoView.h metody. Następujący fragment kodu jest częścią [próbka Demo paska stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób wywołania różnych metod `CMFCStatusBar` klasy w StatusBarDemoView.cpp. Stałe są zadeklarowane w MainFrm.h. Przykład przedstawia sposób ustawiania ikony, ustawić tekst etykietki narzędzia w okienku paska stanu wyświetlany pasek postępu w okienku określony, przypisz animacji określonej w okienku, ustawić tekst i szerokość w okienku paska stanu i ustaw wskaźnik postępu bieżącego progr pasek dostępu w okienku paska stanu. Następujący fragment kodu jest częścią [próbka Demo paska stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar —](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxstatusbar.h  
  
##  <a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bStretch`  
 [in]`bHorz`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex  

  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIDFind`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="create"></a>CMFCStatusBar::Create  

  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParentWnd`  
 [in]`dwStyle`  
 [in]`nID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="createex"></a>CMFCStatusBar::CreateEx  

  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParentWnd`  
 [in]`dwCtrlStyle`  
 [in]`dwStyle`  
 [in]`nID`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick  
 Włącza lub wyłącza obsługę myszy kliknie pasek stanu.  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Jeśli `TRUE`, Włącz przetwarzanie myszy, kliknij dwukrotnie. W przeciwnym razie wyłączenie przetwarzania podwójne kliknięcie.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu na pasku stanu do przetworzenia podwójnego kliknięcia system Windows wysyła `WM_COMMAND` powiadomienia wraz z Identyfikatorem zasobu do właściciela o stanie paska każdym razem, gdy użytkownik kliknie dwukrotnie w okienku paska stanu.  
  
##  <a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar  
 Wyświetlany pasek postępu w okienku określony.  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka którego pasek postępu, aby włączyć.  
  
 [in]`nTotal`  
 Określa maksymalną wartość pasek postępu.  
  
 [in]`bDisplayText`  
 Określa, czy bieżąca wartość postępu powinien być wyświetlany pasek postępu.  
  
 [in]`clrBar`  
 Określa kolor tła paska postępu.  
  
 [in]`clrBarDest`  
 Określa pomocniczy kolor tła paska postępu. Użyj innej wartości niż `clrBar` do wypełnienia według kolorów mieszane do gradientu.  
  
 [in]`clrProgressText`  
 Określa kolor tekstu pasek postępu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz wyłączyć połączenie pasek postępu `EnablePaneProgressBar` z `nTotal` ustawioną wartość -1. Domyślnie `nTotal` wynosi 100. W związku z tym nie wymagają żadnych dodatkowych obliczeń, aby wyświetlić postęp jako procent.  
  
 Różne wartości należy przekazać do `clrBar` i `clrBarDest` tak, aby kolor tła paska postępu Wyświetla kolor przenikaniem do gradientu. .  
  
 Aby ustawić bieżący postęp, należy wywołać [CMFCStatusBar::SetPaneProgress](#setpaneprogress) metody.  
  
##  <a name="getcount"></a>CMFCStatusBar::GetCount  
 Pobiera liczbę okienka na pasku stanu.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba okienka na pasku stanu.  
  
##  <a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea  

  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea  

  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getitemid"></a>CMFCStatusBar::GetItemID  

  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getitemrect"></a>CMFCStatusBar::GetItemRect  

  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`lpRect`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo  

  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`nID`  
 [in]`nStyle`  
 [in]`cxWidth`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress  

  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle  

  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanetext"></a>CMFCStatusBar::GetPaneText  

  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`s`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth  
 Pobiera szerokość w okienku paska stanu.  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks w okienku paska stanu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w okienku paska stanu który `nIndex` określa; w przeciwnym razie wartość zero, jeśli w okienku paska stanu nie istnieje.  
  
##  <a name="gettiptext"></a>CMFCStatusBar::GetTipText  
 Pobrania tekstu etykietki narzędzia w okienku paska stanu.  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, do których chcesz pobrać tekst wskazówki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst etykietki narzędzia w okienku paska stanu który `nIndex` określa. W przeciwnym razie wartość pustą string, jeśli w okienku paska stanu nie istnieje w określonym `nIndex` lub jeśli jego tekst elementu tooltip jest pusta.  
  
##  <a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent  
 Unieważnienie okienku paska stanu i ponownie narysuj zawartość.  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, którego zawartość ma być unieważniona i narysowany ponownie.  
  
### <a name="remarks"></a>Uwagi  
 Unieważnia na pasku stanu jest oznaczony do ponownego narysowania. Windows ponownie go rysuje podczas `UpdateWindow` wysyła metody `WM_PAINT` wiadomości do `OnPaint` metody.  
  
##  <a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane  
 Narysuj element ponownie, w okienku paska stanu.  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia do rysowania.  
  
 [in]`pPane`  
 Wskaźnik do `CMFCStatusBarPaneInfo` struktury, który zawiera informacje o okienku narysowania.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie `OnDrawPane` ponownie rysuje okienku przy użyciu kontekstu urządzenia `pDC` zgodnie z okienka styl i zawartości.  
  
 Należy przesłonić tę metodę w `CMFCStatusBar`-klasy, aby dostosować wygląd okienka.  
  
##  <a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow  

  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`cs`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea  

  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bSet`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setindicators"></a>CMFCStatusBar::SetIndicators  

  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpIDArray`  
 [in]`nIDCount`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation  
 Przypisuje animacji okienko określony.  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, do którego chcesz przypisać do niej animacji.  
  
 [in]`hImageList`  
 Określa dojścia do listy obrazów, który przechowuje ramki animacji.  
  
 [in]`nFrameRate`  
 Określa szybkość klatek (w milisekundach) dla animacji.  
  
 [in]`bUpdate`  
 Jeśli `TRUE`, natychmiast zaktualizować zawartość okienka. W przeciwnym razie utratą Trwa aktualizowanie zawartości okienka.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz wyłączyć bieżącej animacji, wywołanie `SetPaneAnimation` z `hImageList` ustawioną `NULL`.  
  
##  <a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor  
 Ustawia kolor tła w okienku paska stanu.  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks, dla którego mają zostać ustawione na nowy kolor tła okienka.  
  
 [in]`clrBackground`  
 Określa nowy kolor tła.  
  
 [in]`bUpdate`  
 Jeśli `TRUE`, natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie będą aktualizowane w okienku zawartości do momentu unieważnienia okienku przy użyciu innej metody.  
  
##  <a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon  
 Ustaw ikony w okienku paska stanu.  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, dla którego mają zostać ustawione obrazu.  
  
 [in]`hIcon`  
 Określa dojścia do ikonę, aby ustawić jako obraz okienka.  
  
 [in]`bUpdate`  
 Określa, czy można natychmiast zaktualizować zawartość okienka.  
  
 [in]`hBmp`  
 Określa dojścia do mapy bitowej do można ustawić jako obraz okienka.  
  
 [in]`clrTransparent`  
 Określa kolor przezroczysty mapy bitowej który `hBmp` wskazuje.  
  
### <a name="remarks"></a>Uwagi  
 Można przekazać `HICON` lub `HBITMAP` wraz z kolor przezroczysty, aby ustawić obraz okienka. Jeśli nie chcesz już wyświetlić obraz, Przekaż `NULL` wartość jako dojście obrazu.  
  
 W przypadku dowolnego uruchomiona Animacja który [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) została ustawiona, że animacja zostanie zatrzymana.  
  
##  <a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo  

  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`nID`  
 [in]`nStyle`  
 [in]`cxWidth`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress  
 Ustaw bieżący wskaźnik postępu paska postępu dla określonego okienka.  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, do których chcesz zaktualizować wskaźnika postępu.  
  
 [in]`nCurr`  
 Określa bieżącą wartość wskaźnika postępu.  
  
 [in]`bUpdate`  
 Określa, czy okienko powinien natychmiast zaktualizować.  
  
### <a name="remarks"></a>Uwagi  
 Tę metodę można wywołać, jeśli chcesz zaktualizować wskaźnika postępu na pasku postępu w okienku określony.  
  
 Aby użyć tej funkcji do danego okienka, należy wywołać [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) pierwszy.  
  
##  <a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle  

  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`nStyle`  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpanetext"></a>CMFCStatusBar::SetPaneText  

  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 [in]`lpszNewText`  
 [in]`bUpdate`  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor  
 Ustawia kolor tekstu określonego okienka.  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Określa indeks okienka, do którego chcesz przypisać nowy kolor tekstu.  
  
 [in]`clrText`  
 Określa kolor tekstu.  
  
 [in]`bUpdate`  
 Jeśli `TRUE`, natychmiast zaktualizować zawartość okienka. W przeciwnym razie nie będą aktualizowane w okienku zawartości do momentu unieważnienia okienku przy użyciu innej metody.  
  
##  <a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth  
 Ustawia szerokość w okienku paska stanu.  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Indeks w okienku paska stanu, dla którego mają zostać ustawione nową szerokość.  
  
 [in]`cx`  
 Nową szerokość okienku paska stanu w pikselach.  
  
##  <a name="settiptext"></a>CMFCStatusBar::SetTipText  
 Ustaw tekst etykietki narzędzia w okienku paska stanu.  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nIndex`  
 Indeks okienku, do którego chcesz przypisać tekst etykietki narzędzia.  
  
 [in]`pszTipText`  
 Nowy tekst etykietki narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)   
 [Cstatusbar — klasa](../../mfc/reference/cstatusbar-class.md)
