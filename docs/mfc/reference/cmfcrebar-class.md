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
ms.openlocfilehash: af74ab381293e04c08a1fa8c601558edaeacf6c4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689195"
---
# <a name="cmfcrebar-class"></a>Klasa CMFCReBar
A `CMFCReBar` obiekt jest pasek sterowania, który zawiera układ, trwałość i informacje o stanie dla formantów rebar.  
   Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Dodaje obiekt band do paska pomocniczego.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Przesłania [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Przesłania [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza je do `CMFCReBar` obiektu.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Przesłania [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Zapewnia bezpośredni dostęp do podstawowych [z CReBarCtrl](../../mfc/reference/crebarctrl-class.md) wspólnej kontroli.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Przesłania [CPane::OnShowControlBarMenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Przesłania [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Przesłania [CBasePane::OnUpdateCmdUI](cbasepane-class.md).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Przesłania [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Uwagi  
 Element `CMFCReBar` obiektu może zawierać wiele okien podrzędnych. W tym pola tekstowe, paski narzędzi i pól listy. Można zmienić rozmiar paska pomocniczego programowo lub użytkownik może ręcznie zmienić rozmiar paska pomocniczego przeciągając pasek uchwytu. Tło obiektu paska pomocniczego można również ustawić do mapy bitowej wybranych przez użytkownika.  
  
 Obiekt paska pomocniczego działa podobnie jak obiekt paska narzędzi. Kontrolki paska pomocniczego może zawierać jeden lub więcej grup i każdej grupy mogą zawierać pasek uchwytu, mapy bitowej, etykietę tekstową i okna podrzędnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCReBar` klasy. W przykładzie pokazano, jak utworzyć kontrolkę paska pomocniczego i dodawanie grupy do niej. Funkcje pasek narzędzi wewnętrznych. Ten fragment kodu jest częścią [paska pomocniczego próbkę](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxRebar.h  
  
##  <a name="addbar"></a>  CMFCReBar::AddBar  
 Dodaje obiekt band do paska pomocniczego.  
  
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
 Wskaźnik do okna podrzędnego, który ma zostać wstawiony do paska pomocniczego. Przywoływany obiekt musi mieć **WS_CHILD** styl okna.  
  
 [in] *pszText*  
 Określa tekst do wyświetlenia na paska pomocniczego. Tekst nie jest częścią okna podrzędnego. Przeciwnie jest wyświetlany na paska pomocniczego, sam.  
  
 [in] [out] *pbmp*  
 Określa mapy bitowej, który będzie wyświetlany w tle paska pomocniczego.  
  
 [in] *dwStyle*  
 Zawiera style, które można zastosować do grupy. Aby uzyskać pełną listę style poza pasmem, zobacz opis `fStyle` w [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktury w dokumentacji zestawu Windows SDK.  
  
 [in] *clrFore*  
 Reprezentuje kolor pierwszego planu paska pomocniczego.  
  
 [in] *clrBack*  
 Reprezentuje kolor tła paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pasmo zostało pomyślnie dodane do paska pomocniczego; w przeciwnym razie wartość FALSE.  
  
##  <a name="create"></a>  CMFCReBar::Create  
 Tworzy kontrolkę paska pomocniczego i dołącza je do [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) obiektu.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parametry  
 [in] [out] *pParentWnd*  
 Wskaźnik do nadrzędnego okna tej kontrolki paska pomocniczego.  
  
 [in] *dwCtrlStyle*  
 Określa styl kontrolki paska pomocniczego. Domyślna wartość stylu jest **RBS_BANDBORDERS**, który wyświetla zawęzić zakres wierszy w celu rozdzielenia sąsiadujących paskami w formancie paska pomocniczego. Aby uzyskać listę prawidłowe style, zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w dokumentacji zestawu Windows SDK.  
  
 [in] *dwStyle*  
 Styl okna formantu paska pomocniczego. Aby uzyskać listę prawidłowe style, zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *nID*  
 Identyfikator okna podrzędnego paska pomocniczego  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie; utworzono paska pomocniczego w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getrebarctrl"></a>  CMFCReBar::GetReBarCtrl  
 Zapewnia bezpośredni dostęp do `CReBarCtrl` bazowego formantu typowego dla `CMFCReBar` obiektów.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bazowej `CReBarCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby móc korzystać z funkcji Windows paska pomocniczego wspólnej kontroli, dostosowując swoje paska pomocniczego.  
  
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
 [Klasa CReBarCtrl](../../mfc/reference/crebarctrl-class.md)   
 [Klasa CPane](../../mfc/reference/cpane-class.md)
