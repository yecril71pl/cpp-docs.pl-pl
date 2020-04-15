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
ms.openlocfilehash: ad1225034cc5eca8ca53b042ebe3b55db4a2cf09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364125"
---
# <a name="cpanedialog-class"></a>Klasa CPaneDialog

Klasa `CPaneDialog` obsługuje niemodalne, dokowane okno dialogowe.

## <a name="syntax"></a>Składnia

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|Domyślny konstruktor.|
|`CPaneDialog::~CPaneDialog`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneDialog::Utwórz](#create)|Tworzy okno dialogowe z dokowania `CPaneDialog` i dołącza je do obiektu.|
|`CPaneDialog::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CPaneDialog::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Obsługuje komunikat [WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog) (Redefines `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Obsługuje komunikat [WM_ERASEBKGND.](/windows/win32/winmsg/wm-erasebkgnd) (Redefines [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Obsługuje komunikat [WM_LBUTTONDBLCLK.](/windows/win32/inputdev/wm-lbuttondblclk) (Redefiniuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Obsługuje komunikat [WM_LBUTTONDOWN.](/windows/win32/inputdev/wm-lbuttondown) (Redefines [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Wywoływane przez strukturę, aby zaktualizować okno okna dialogowego. (Zastępuje [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Obsługuje komunikat [WM_WINDOWPOSCHANGING.](/windows/win32/winmsg/wm-windowposchanging) (Redefines [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Określa szablon okna dialogowego, które jest kontenerem sterowania OLE.|

## <a name="remarks"></a>Uwagi

Konstruuj `CPaneDialog` obiekt w dwóch krokach. Najpierw skonstruować obiekt w kodzie. Po drugie, wywołaj [CPaneDialog::Create](#create). Należy określić prawidłową nazwę szablonu zasobu lub identyfikator szablonu i przekazać wskaźnik do okna nadrzędnego. W przeciwnym razie proces tworzenia kończy się niepowodzeniem. Okno dialogowe musi określać styl WS_CHILD i WS_VISIBLE. Zaleca się również określenie stylów WS_CLIPCHILDREN i WS_CLIPSIBLINGS. Aby uzyskać więcej informacji, zobacz [Style okien](styles-used-by-mfc.md#window-styles).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[Cdockablepane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpanedialog.h

## <a name="cpanedialogcreate"></a><a name="create"></a>CPaneDialog::Utwórz

Tworzy okno dialogowe dokowania i `CPaneDialog` dołącza je do obiektu.

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
[w] Nazwa okna dialogowego dokowania.

*pParentWnd*<br/>
[w] Wskazuje okno nadrzędne.

*bHasGripper*<br/>
[w] PRAWDA, aby utworzyć okno dialogowe dokowania z podpisem (chwytacz); w przeciwnym razie FALSE.

*lpszTemplateName*<br/>
[w] Nazwa szablonu okna dialogowego zasobu.

*styl nStyle*<br/>
[w] Styl systemu Windows.

*Nid*<br/>
[w] Identyfikator sterowania.

*nIDTemplate*<br/>
[w] Identyfikator zasobu szablonu okna dialogowego.

*dwTabbedStyle*<br/>
[w] Styl okna z kartami, który powoduje, gdy użytkownik przeciągnie innego okienka sterowania na podpis tego okienka formantu. Wartość domyślna jest AFX_CBRS_REGULAR_TABS. Aby uzyskać więcej informacji, zobacz uwagi sekcji [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

*styl dwControlBarStyle*<br/>
[w] Dodatkowe atrybuty stylu. Wartość domyślna to AFX_DEFAULT_DOCKING_PANE_STYLE. Aby uzyskać więcej informacji, zobacz uwagi sekcji [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `Create` metody w `CPaneDialog` klasie. W tym przykładzie jest częścią [próbki Set Pane Size](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

## <a name="cpanedialoghandleinitdialog"></a><a name="handleinitdialog"></a>CPaneDialog::HandleInitDialog

Obsługuje komunikat [WM_INITDIALOG.](/windows/win32/dlgbox/wm-initdialog)

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Wparam*<br/>
[w] Dojście do formantu, który ma odbierać domyślny fokus klawiatury.

*Lparam*<br/>
[w] Określa dodatkowe dane inicjowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE. Ponadto funkcja TRUE ustawia fokus klawiatury na formant określony przez parametr *wParam;* FUNKCJA FALSE zapobiega ustawianiu domyślnego fokusu klawiatury.

### <a name="remarks"></a>Uwagi

Struktura używa tej metody do inicjowania formantów i wygląd okna dialogowego. Struktura wywołuje tę metodę, zanim wyświetli okno dialogowe.

## <a name="cpanedialogsetoccdialoginfo"></a><a name="setoccdialoginfo"></a>CPaneDialog::SetOccDialogInfo

Określa szablon okna dialogowego, które jest kontenerem sterowania OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
[w] Wskaźnik do szablonu okna dialogowego używanego do tworzenia obiektu okna dialogowego. Wartość tego parametru jest następnie przekazywana do [metody COccManager::CreateDlgControls.](../../mfc/reference/coccmanager-class.md#createdlgcontrols)

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje [COccManager](../../mfc/reference/coccmanager-class.md) klasy, która zarządza witryn kontroli OLE i formantów ActiveX. Struktura _AFX_OCC_DIALOG_INFO jest zdefiniowana w pliku nagłówka afxocc.h.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles)
