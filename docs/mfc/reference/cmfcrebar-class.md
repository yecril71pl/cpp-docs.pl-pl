---
title: Klasa CMFCReBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs:
- C++
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcef7bab4fd2b0cd913c0da929534d6964730215
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037964"
---
# <a name="cmfcrebar-class"></a>Klasa CMFCReBar
A `CMFCReBar` obiekt jest pasek sterowania, który zapewnia układu, trwałości i informacje o formantach paska pomocniczego stanie.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Dodaje grupy do paska pomocniczego.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Przesłania [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza go do `CMFCReBar` obiektu.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Przesłania [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Zapewnia bezpośredni dostęp do odpowiadającego [crebarctrl —](../../mfc/reference/crebarctrl-class.md) formantu wspólnego.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Przesłania [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Przesłania [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/e139f06a-9793-4ee2-bc3d-517389368c77).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Przesłania [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Uwagi  
 A `CMFCReBar` obiekt może zawierać wiele podrzędnych systemu Windows. W tym pola edycji, paski narzędzi i pola listy. Można zmienić rozmiar paska pomocniczego programowo, lub użytkownik może ręcznie zmienić rozmiar paska pomocniczego przez przeciągnięcie jego paska uchwytu. Można również ustawić tła obiektu paska pomocniczego do mapy bitowej wybranych przez użytkownika.  
  
 Obiekt paska pomocniczego działa podobnie do obiektu paska narzędzi. Formantu paska pomocniczego może zawierać jeden lub więcej grup i każdej grupy mogą zawierać pasek uchwytu, mapy bitowej etykietę tekstową i okna podrzędnego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCReBar` klasy. W przykładzie Tworzenie formantu paska pomocniczego i Dodaj do niej grupy. Funkcje poza pasmem jako wewnętrzne paska narzędzi. Następujący fragment kodu jest częścią [paska pomocniczego próbki](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRebar.h  
  
##  <a name="addbar"></a>  CMFCReBar::AddBar  
 Dodaje grupy do paska pomocniczego.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out] *pBar*  
 Wskaźnik do okna podrzędnego, który ma zostać wstawione do paska pomocniczego. Odwołuje się do obiektu musi mieć **ws_child —** styl okna.  
  
 [in] *pszText*  
 Określa tekst wyświetlany na paska pomocniczego. Tekst nie jest częścią okna podrzędnego. Zamiast jest wyświetlany na paska pomocniczego, do samej siebie.  
  
 [in] [out] *pbmp*  
 Określa mapy bitowej, który będzie wyświetlany na tła paska pomocniczego.  
  
 [in] *dwStyle*  
 Zawiera styl, aby zastosować do grupy. Pełną listę stylów poza pasmem, zobacz opis `fStyle` w [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktury w dokumentacji zestawu SDK systemu Windows.  
  
 [in] *clrFore*  
 Reprezentuje kolor pierwszego planu paska pomocniczego.  
  
 [in] *clrBack*  
 Reprezentuje kolor tła paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli grupy zostało pomyślnie dodane do paska pomocniczego; w przeciwnym razie `FALSE`.  
  
##  <a name="create"></a>  CMFCReBar::Create  
 Tworzy kontrolkę paska pomocniczego i dołącza go do [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) obiektu.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out] *pParentWnd*  
 Wskaźnik do okna nadrzędnego tego formantu paska pomocniczego.  
  
 [in] *dwCtrlStyle*  
 Określa styl formantu paska pomocniczego. Styl wartość domyślna to **RBS_BANDBORDERS**, która wyświetla zawęzić wierszy w celu rozdzielenia sąsiadujących paskami w formancie paska pomocniczego. Lista prawidłowy style, zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w dokumentacji zestawu SDK systemu Windows.  
  
 [in] *dwStyle*  
 Styl okna w formancie paska pomocniczego. Lista prawidłowy style, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *nID*  
 Identyfikator paska pomocniczego okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli pomyślnie; utworzono paska pomocniczego w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl  
 Zapewnia bezpośredni dostęp do `CReBarCtrl` podstawowej formantu wspólnego dla `CMFCReBar` obiektów.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do odpowiadającego `CReBarCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby móc korzystać z funkcji systemu Windows paska pomocniczego wspólnej kontroli w przypadku dostosowywania z paska pomocniczego.  
  
##  <a name="calcfixedlayout"></a>  CMFCReBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bStretch*  
 [in] *bHorz*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="canfloat"></a>  CMFCReBar::CanFloat  

  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enabledocking"></a>  CMFCReBar::EnableDocking  

  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *dwDockStyle*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrebarbandinfosize"></a>  CMFCReBar::GetReBarBandInfoSize  

  
```  
UINT GetReBarBandInfoSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onshowcontrolbarmenu"></a>  CMFCReBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *CPoint*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ontoolhittest"></a>  CMFCReBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *punktu*  
 [in] *pTI*  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="onupdatecmdui"></a>  CMFCReBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pTarget*  
 [in] *bDisableIfNoHndler*  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setpanealignment"></a>  CMFCReBar::SetPaneAlignment  

  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *dwAlignment*  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Crebarctrl — klasa](../../mfc/reference/crebarctrl-class.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)
