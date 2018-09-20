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
ms.openlocfilehash: 9783eb0e4468f154591676dc46ed9342082d8512
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396467"
---
# <a name="cpanedialog-class"></a>Klasa CPaneDialog

`CPaneDialog` Klasa obsługuje niemodalne, dokowane okno dialogowe.

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
|[CPaneDialog::Create](#create)|Tworzy dokowane okno dialogowe i dołącza je do `CPaneDialog` obiektu.|
|`CPaneDialog::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CPaneDialog::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|Obsługuje [/ / Złap](/windows/desktop/dlgbox/wm-initdialog) wiadomości. (Redefiniuje `CBasePane::HandleInitDialog`.)|
|`CPaneDialog::OnEraseBkgnd`|Obsługuje [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) wiadomości. (Redefiniuje [CWnd::OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd).)|
|`CPaneDialog::OnLButtonDblClk`|Obsługuje [WM_LBUTTONDBLCLK](/windows/desktop/inputdev/wm-lbuttondblclk) wiadomości. (Redefiniuje [CWnd::OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk).)|
|`CPaneDialog::OnLButtonDown`|Obsługuje [WM_LBUTTONDOWN](/windows/desktop/inputdev/wm-lbuttondown) wiadomości. (Redefiniuje [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown).)|
|`CPaneDialog::OnUpdateCmdUI`|Metoda wywoływana przez platformę, by zaktualizować okno dialogowe. (Przesłania [CDockablePane::OnUpdateCmdUI](cdockablepane-class.md).)|
|`CPaneDialog::OnWindowPosChanging`|Obsługuje [WM_WINDOWPOSCHANGING](/windows/desktop/winmsg/wm-windowposchanging) wiadomości. (Redefiniuje [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging).)|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|Określa szablon dla okna dialogowego, który jest kontenerem sterowania OLE.|

## <a name="remarks"></a>Uwagi

Konstruowania `CPaneDialog` obiektu w dwóch krokach. Najpierw skonstruuj obiekt w kodzie. Po drugie wywołanie [CPaneDialog::Create](#create). Należy określić identyfikator prawidłowego zasobu szablonu lub nazwę szablonu i przekazać wskaźnik do okna nadrzędnego. W przeciwnym razie proces tworzenia kończy się niepowodzeniem. Okno dialogowe, należy określić WS_CHILD i WS_VISIBLE stylu. Firma Microsoft zaleca również określić WS_CLIPCHILDREN i WS_CLIPSIBLINGS style. Aby uzyskać więcej informacji, zobacz [Style okna ramowego](styles-used-by-mfc.md#window-styles).

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

Tworzy dokujące okno dialogowe i dołącza je do `CPaneDialog` obiektu.

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
[in] Nazwa dokujące okno dialogowe.

*pParentWnd*<br/>
[in] Wskazuje okna nadrzędnego.

*bHasGripper*<br/>
[in] Wartość TRUE, aby utworzyć okno dialogowe dokowania z podpisami (uchwyt); w przeciwnym razie wartość FALSE.

*lpszTemplateName*<br/>
[in] Nazwa zasobu szablonu okna dialogowego.

*nStyle*<br/>
[in] Windows style.

*nID*<br/>
[in] Identyfikator kontrolki.

*nIDTemplate*<br/>
[in] Identyfikator zasobu szablonu okna dialogowego.

*dwTabbedStyle*<br/>
[in] Styl okna z kartami, która powstaje, gdy użytkownik przeciągnie okienko sterowania innej na podpis w tym okienku kontroli. Wartość domyślna to AFX_CBRS_REGULAR_TABS. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

*dwControlBarStyle*<br/>
[in] Atrybuty stylu dodatkowe. Wartość domyślna to AFX_DEFAULT_DOCKING_PANE_STYLE. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) metody.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `Create` method in Class metoda `CPaneDialog` klasy. W tym przykładzie jest częścią [przykładowe ustawić rozmiar okienka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

Obsługuje [/ / Złap](/windows/desktop/dlgbox/wm-initdialog) wiadomości.

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*wParam*<br/>
[in] Dojście do formantu, który ma zostać ustawiony fokus klawiatury domyślne.

*lParam*<br/>
[in] Określa dodatkowe inicjowanie danych.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE. Ponadto TRUE Ustawia fokus klawiatury do kontrolki określonej przez *wParam* parameter; FALSE zapobiega ustawienie domyślne fokus klawiatury.

### <a name="remarks"></a>Uwagi

Struktura używa tej metody, aby zainicjować kontrolki i wygląd okna dialogowego. Struktura wywołuje tę metodę, zanim wyświetli okno dialogowe.

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

Określa szablon dla okna dialogowego, który jest kontenerem sterowania OLE.

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>Parametry

*pOccDialogInfo*<br/>
[in] Wskaźnik do szablonu okna dialogowego, który jest używany do tworzenia obiektu okna dialogowego pole. Wartość tego parametru jest następnie przekazywany do [COccManager::CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols) metody.

### <a name="return-value"></a>Wartość zwracana

Zawsze TRUE.

### <a name="remarks"></a>Uwagi

Ta metoda obsługuje [COccManager](../../mfc/reference/coccmanager-class.md) klasy, która umożliwia zarządzanie witrynami kontrolek OLE i formantów ActiveX. Struktura _AFX_OCC_DIALOG_INFO jest definiowana w pliku nagłówkowym afxocc.h.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CDockablePane](../../mfc/reference/cdockablepane-class.md)<br/>
[Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles)



