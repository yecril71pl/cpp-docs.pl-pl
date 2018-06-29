---
title: Klasa CPaneDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
dev_langs:
- C++
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 022fe884f611eb5bc3254ef23c7078280e2a1046
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078546"
---
# <a name="cpanedialog-class"></a>Klasa CPaneDialog
`CPaneDialog` Klasa obsługuje okno dialogowe niemodalne, dokującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPaneDialog : public CDockablePane  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CPaneDialog::CPaneDialog`|Domyślny konstruktor.|  
|`CPaneDialog::~CPaneDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaneDialog::Create](#create)|Tworzy okno dialogowe dokującego i dołącza go do `CPaneDialog` obiektu.|  
|`CPaneDialog::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CPaneDialog::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Obsługuje [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) wiadomości. (Ponownie definiuje `CBasePane::HandleInitDialog`.)|  
|`CPaneDialog::OnEraseBkgnd`|Obsługuje [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) wiadomości. (Ponownie definiuje [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|  
|`CPaneDialog::OnLButtonDblClk`|Obsługuje [WM_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) wiadomości. (Ponownie definiuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|  
|`CPaneDialog::OnLButtonDown`|Obsługuje [WM_LBUTTONDOWN](http://msdn.microsoft.com/library/windows/desktop/ms645607) wiadomości. (Ponownie definiuje [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|  
|`CPaneDialog::OnUpdateCmdUI`|Wywoływane przez platformę, by zaktualizować okno dialogowe. (Przesłania [CDockablePane::OnUpdateCmdUI](http://msdn.microsoft.com/5dd61606-1c12-40d4-b024-f3839aa5e2e0).)|  
|`CPaneDialog::OnWindowPosChanging`|Obsługuje [WM_WINDOWPOSCHANGING](http://msdn.microsoft.com/library/windows/desktop/ms632653) wiadomości. (Ponownie definiuje [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|  
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Określa szablon dla okna dialogowego, który jest kontenerze formantów OLE.|  
  
## <a name="remarks"></a>Uwagi  
 Utworzyć `CPaneDialog` obiektu w dwóch krokach. Najpierw należy utworzyć obiektu w kodzie. Po drugie, wywołaj [CPaneDialog::Create](#create). Należy określić identyfikator prawidłowego zasobu szablonu lub nazwę szablonu i wskaźnikiem do okna nadrzędnego. W przeciwnym razie proces tworzenia kończy się niepowodzeniem. Okno dialogowe musi określać ws_child — i ws_visible — styl. Zalecamy również określić ws_clipchildren — i ws_clipsiblings — style. Aby uzyskać więcej informacji, zobacz [Style okna](styles-used-by-mfc.md#window-styles).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CPaneDialog](../../mfc/reference/cpanedialog-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpanedialog.h  
  
##  <a name="create"></a>  CPaneDialog::Create  
 Tworzy okno dialogowe dokowania i dołącza go do `CPaneDialog` obiektu.  
  
```  
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID,  
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

 
BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    BOOL bHasGripper,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszWindowName*  
 Nazwa okna dialogowego dokowania.  
  
 [in] *pParentWnd*  
 Wskazuje okno nadrzędne.  
  
 [in] *bHasGripper*  
 `TRUE` Aby utworzyć okno dialogowe dokowania z tekstem (uchwytu); w przeciwnym razie `FALSE`.  
  
 [in] *lpszTemplateName*  
 Nazwa zasobu szablonu okna dialogowego.  
  
 [in] *nStyle*  
 Styl systemu Windows.  
  
 [in] *nID*  
 Identyfikator formantu.  
  
 [in] *nIDTemplate*  
 Identyfikator zasobu szablonu okna dialogowego.  
  
 [in] *dwTabbedStyle*  
 Styl okna karty wyników, gdy użytkownik przeciąga innego panelu sterowania na podpis w tym okienku formantu. Wartość domyślna to `AFX_CBRS_REGULAR_TABS`. Aby uzyskać więcej informacji, zobacz sekcję uwag [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.  
  
 [in] *dwControlBarStyle*  
 Styl dodatkowe atrybuty. Wartość domyślna to `AFX_DEFAULT_DOCKING_PANE_STYLE`. Aby uzyskać więcej informacji, zobacz sekcję uwag [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `Create` metoda `CPaneDialog` klasy. Ten przykład jest częścią [próbki Ustaw rozmiar okienka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]  
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]  
  
##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog  
 Obsługuje [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) wiadomości.  
  
```  
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *wParam*  
 Dojście do formantu, który ma fokus klawiatury domyślne.  
  
 [in] *lParam*  
 Określa dodatkowe inicjowania danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`. Ponadto `TRUE` Ustawia fokus klawiatury do kontrolki określony przez *wParam* parametru; `FALSE` uniemożliwia ustawienie domyślne fokus klawiatury.  
  
### <a name="remarks"></a>Uwagi  
 Platformę używa tej metody można zainicjować kontrolek i wyglądu w oknie dialogowym. Struktura wywołuje tę metodę, przed wyświetleniem okna dialogowego.  
  
##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo  
 Określa szablon dla okna dialogowego, który jest kontenerze formantów OLE.  
  
```  
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pOccDialogInfo*  
 Wskaźnik do szablonu okno dialogowe, który służy do tworzenia obiektu okno dialogowe. Wartość tego parametru jest następnie przekazywane do [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje [COccManager](../../mfc/reference/coccmanager-class.md) klasy, która zarządza OLE kontroli lokacji i formantów ActiveX. Struktura _AFX_OCC_DIALOG_INFO jest zdefiniowana w pliku nagłówka afxocc.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles)



