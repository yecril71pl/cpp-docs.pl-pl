---
title: Klasa CPaneDialog
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502981"
---
# <a name="cpanedialog-class"></a>Klasa CPaneDialog

`CPaneDialog` Klasa obsługuje niemodalne, było dokować okno dialogowe.

## <a name="syntax"></a>Składnia

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Konstruktor domyślny.|
|`CPaneDialog::~CPaneDialog`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDialog:: Create](#create)|Tworzy okno dialogowe było dokować i dołącza je do `CPaneDialog` obiektu.|
|`CPaneDialog::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CPaneDialog::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Obsługuje komunikat [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Ponownie zdefiniuj `CBasePane::HandleInitDialog`).|
|`CPaneDialog::OnEraseBkgnd`|Obsługuje komunikat [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd) . (Ponownie definiuje [CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)).|
|`CPaneDialog::OnLButtonDblClk`|Obsługuje komunikat [WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk) . (Ponownie definiuje [CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)).|
|`CPaneDialog::OnLButtonDown`|Obsługuje komunikat [WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown) . (Ponownie definiuje [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)).|
|`CPaneDialog::OnUpdateCmdUI`|Wywoływane przez platformę w celu zaktualizowania okna dialogowego. (Przesłania [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Obsługuje komunikat [WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging) . (Ponownie definiuje [CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)).|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Określa szablon okna dialogowego, które jest kontenerem kontrolki OLE.|

## <a name="remarks"></a>Uwagi

`CPaneDialog` Utwórz obiekt w dwóch krokach. Najpierw Utwórz obiekt w kodzie. Następnie zadzwoń do [CPaneDialog:: Create](#create). Należy określić prawidłową nazwę szablonu zasobu lub identyfikator szablonu i przekazać wskaźnik do okna nadrzędnego. W przeciwnym razie proces tworzenia zakończy się niepowodzeniem. W oknie dialogowym należy określić styl WS_CHILD i WS_VISIBLE. Zalecamy również określanie stylów WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Aby uzyskać więcej informacji, zobacz [Style okna](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpanedialog. h

##  <a name="create"></a>CPaneDialog:: Create

Tworzy okno dialogowe dokowanie i dołącza je do `CPaneDialog` obiektu.

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

*lpszWindowName*<br/>
podczas Nazwa okna dialogowego dokowanie.

*pParentWnd*<br/>
podczas Wskazuje okno nadrzędne.

*bHasGripper*<br/>
podczas Wartość TRUE powoduje utworzenie okna dialogowego Docking z podpisem (uchwyt); w przeciwnym razie FALSE.

*lpszTemplateName*<br/>
podczas Nazwa szablonu okna dialogowego zasobu.

*nStyle*<br/>
podczas Styl systemu Windows.

*nID*<br/>
podczas Identyfikator formantu.

*nIDTemplate*<br/>
podczas Identyfikator zasobu szablonu okna dialogowego.

*dwTabbedStyle*<br/>
podczas Styl okna z kartami, który jest wynikiem, gdy użytkownik przeciągnie inne okienko sterowania na podpis tego okienka. Wartość domyślna to AFX_CBRS_REGULAR_TABS. Aby uzyskać więcej informacji, zobacz sekcję Uwagi w metodzie [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

*dwControlBarStyle*<br/>
podczas Dodatkowe atrybuty stylu. Wartość domyślna to AFX_DEFAULT_DOCKING_PANE_STYLE. Aby uzyskać więcej informacji, zobacz sekcję Uwagi w metodzie [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) .

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `Create` metody `CPaneDialog` w klasie. Ten przykład jest częścią [przykładu Ustawianie rozmiaru okienka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Obsługuje komunikat [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) .

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
podczas Dojście do formantu, który ma otrzymać domyślny fokus klawiatury.

*lParam*<br/>
podczas Określa dodatkowe dane inicjujące.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE. Ponadto TRUE ustawia fokus klawiatury dla kontrolki określonej przez parametr *wParam* ; Wartość FALSE uniemożliwia ustawienie domyślnego fokusu klawiatury.

### <a name="remarks"></a>Uwagi

Struktura używa tej metody do inicjowania kontrolek i wyglądu okna dialogowego. Struktura wywołuje tę metodę przed wyświetleniem okna dialogowego.

##  <a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Określa szablon okna dialogowego, które jest kontenerem kontrolki OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
podczas Wskaźnik do szablonu okna dialogowego, który jest używany do tworzenia obiektu okna dialogowego. Wartość tego parametru jest następnie przesyłana do metody [COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) .

### <a name="return-value"></a>Wartość zwracana

Zawsze prawda.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje klasę [COccManager](../../mfc/reference/coccmanager-class.md) , która zarządza lokacjami formantów OLE i kontrolkami ActiveX. Struktura _AFX_OCC_DIALOG_INFO jest zdefiniowana w pliku nagłówkowym afxocc. h.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles)
