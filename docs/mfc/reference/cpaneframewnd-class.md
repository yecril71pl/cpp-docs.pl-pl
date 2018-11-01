---
title: Klasa CPaneFrameWnd
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: e31b390d9464b3cbe6babd744e987ce7222e58bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450170"
---
# <a name="cpaneframewnd-class"></a>Klasa CPaneFrameWnd

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

Implementuje okno mini ramki, który zawiera jedno okienko. Okienko wypełnia obszar klienta okna.

## <a name="syntax"></a>Składnia

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::AddPane](#addpane)|Dodaje okienko.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Dodaje lub usuwa okienko z globalnej listy.|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Dostosowuje układ okna mini ramki.|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Oblicza rozmiar obramowania okna mini ramki.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicz oczekiwane prostokąt okno zadokowane.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Określa, czy bieżące okienko może być zadokowane do innego okienka lub ramki okna.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Określa, czy okno mini ramki mogą być zadokowane, do okienka.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje dokument z kartami okienka.|
|[CPaneFrameWnd::Create](#create)|Tworzy okno mini ramki i dołącza je do `CPaneFrameWnd` obiektu.|
|[CPaneFrameWnd::CreateEx](#createex)|Tworzy okno mini ramki i dołącza je do `CPaneFrameWnd` obiektu.|
|[CPaneFrameWnd::DockPane](#dockpane)|Stacje dokujące okienka.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Znajduje okienko o identyfikatorze określoną kontrolkę na globalnej liście okienka zmiennoprzecinkowy.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Wyszukuje okno mini ramki, zawierający punkt dostarczone przez użytkownika.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość tytuł okna mini ramki.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Oblicza prostokąt otaczający tytuł okna mini ramki.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Zwraca tekst podpisu.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Zwraca tryb dokowania.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Zwraca pierwszy widoczne okienko znajdujące się w przypadku okno mini ramki.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|Zwraca okienko, w którym znajduje się w przypadku okno mini ramki.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Zwraca liczbę okienek, które są zawarte w okno mini ramki.|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Zwraca liczbę widocznych okienek, które są zawarte w okno mini ramki.|
|[CPaneFrameWnd::HitTest](#hittest)|Określa, jaka część okna mini ramki jest w danym momencie.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Określa, czy okno mini ramki powinny zostać wycofana w dół.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|Określa, czy okno mini ramki powinny być rzutowana.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zatrzymuje timer dokowania.|
|[CPaneFrameWnd::LoadState](#loadstate)|Ładuje stan okienka z rejestru.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Określa, czy dokowanie jest możliwe.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Dokowane okno mini ramki w jego najbardziej aktualne położenie.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zatrzymuje timer zbiorczy.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Przesuwa okno mini ramki określonego przesunięcia.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Dostosowuje układ zawartej okienka.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Ustawia czasomierza zbiorczy.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Wywoływane przez platformę, gdy okienka w oknie mini ramki jest ukryta lub wyświetlone.|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Zwraca okienko, jeśli zawiera ona punkt dostarczone przez użytkownika wewnątrz okna mini ramki.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows.|
|[CPaneFrameWnd::RedrawAll](#redrawall)|Odrysowuje wszystkie okna mini ramki.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Metoda wywoływana przez platformę, by usunąć okienka nie jest ważna.|
|[CPaneFrameWnd::RemovePane](#removepane)|Usuwa okienko z okna mini ramki.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Zastępuje jedno okienko z inną.|
|[CPaneFrameWnd::SaveState](#savestate)|Zapisuje stan w okienku w rejestrze.|
|`CPaneFrameWnd::Serialize`|Odczytuje lub zapisuje ten obiekt z lub do archiwum.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Ustawia podpis przycisków.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Ustawia czasomierza dokowania.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Ustawia stan dokowania.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Metoda wywoływana przez platformę, by ustawić predocking stanu.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Dopasowuje rozmiar okna mini ramki, tak, że jest to równoważne rozmiar okienka zawarte.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Rysy Wyłącz menu.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Określa, czy okno mini ramki powinny zostać wycofana w górę lub w dół.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Rysuje obramowanie, okna mini ramki.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Określa, czy rejestrowanie klasy okna stylem CS_SAVEBITS klasy.|

## <a name="remarks"></a>Uwagi

Szablon automatycznie tworzy `CPaneFrameWnd` obiektu po przełączeniu okienko ze stanu zadokowany do stanu zmiennoprzecinkowego.

Okno mini ramki mogą być przeciągnięte z jego zawartością widoczne (natychmiastowego dokowanie) lub za pomocą przeciągnij prostokąt (dokowanie standard). Tryb dokowania okienko kontener ramki mini określa mini ramki przez przeciąganie zachowanie. Aby uzyskać więcej informacji, zobacz [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Okno mini ramki są wyświetlane przyciski na podpis zgodnie ze stylu zawartej w okienku. Jeśli okienko można zamknąć ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), wyświetla przycisk Zamknij. Jeśli okienko ma styl AFX_CBRS_AUTO_ROLLUP, wyświetla numer pin.

Jeśli wyprowadzić klasę z `CPaneFrameWnd`, musisz poinformować platformę jak je utworzyć. Utwórz klasy przez zastąpienie [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), lub ustawić `CPane::m_pMiniFrameRTC` elementu członkowskiego, tak że wskazuje informacji o klasie czasu wykonywania dla swojej klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxPaneFrameWnd.h

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

Dodaje okienko.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Okienko do dodania.

##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList

Dodaje lub usuwa okienko z globalnej listy.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Okienko, aby dodać lub usunąć.

*bDodaj*<br/>
[in] Jeśli różna od zera, należy dodać okienka. Jeśli jest to 0, należy usunąć okienka.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout

Dostosowuje układ okna mini ramki.

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>  CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Uwagi

##  <a name="calcbordersize"></a>  CPaneFrameWnd::CalcBorderSize

Oblicza rozmiar obramowania okna pływające.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parametry

*rectBorderSize*<br/>
[out] Zawiera rozmiar w pikselach, obramowania okna pływające.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę w celu obliczania rozmiaru obramowania pływające mini okno. Rozmiar zwróconego zależy od czy pływające mini okno ramowe zawiera pasek narzędzi lub [CDockablePane](../../mfc/reference/cdockablepane-class.md).

##  <a name="calcexpecteddockedrect"></a>  CPaneFrameWnd::CalcExpectedDockedRect

Oblicz oczekiwane prostokąt okno zadokowane.

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

*pWndToDock*<br/>
[in] Wskaźnik do okna, aby zadokować.

*ptMouse*<br/>
[in] Położenie myszy.

*rectResult*<br/>
[out] Obliczony prostokąt.

*bDrawTab*<br/>
[out] W przypadku opcji TRUE narysuj kartę. W przypadku wartości FAŁSZ nie Rysuj kartę.

*ppTargetBar*<br/>
[out] Wskaźnik do okienka docelowego.

### <a name="remarks"></a>Uwagi

Ta metoda oblicza prostokąt, który okna zajmują użytkownika przeciągania okna w punkcie określonym przez *ptMouse* i zadokowane, go.

##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached

Określa, czy bieżące okienko może być zadokowane do innego okienka lub ramki okna.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli zawartość okienka może być zadokowane do innego okienka lub ramki okna; w przeciwnym razie wartość FALSE.

##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane

Określa, czy okno mini ramki mogą być zadokowane, do okienka.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parametry

*pDockingBar*<br/>
[in] Okienko.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli mini ramki mogą być zadokowane, aby *pDockingBar*; w przeciwnym razie 0.

##  <a name="checkgrippervisibility"></a>  CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Uwagi

##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument

Konwertuje dokument z kartami okienka.

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>  CPaneFrameWnd::Create

Tworzy okno pływające i dołącza je do [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) obiektu.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parametry

*lpszWindowName*<br/>
[in] Określa tekst do wyświetlenia w oknie pływające.

*dwStyle*<br/>
[in] Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[in] Określa początkowy rozmiar i położenie okna pływające.

*pParentWnd*<br/>
[out w] Określa nadrzędnej ramki okna pływające. Ta wartość nie może być równa NULL.

*pContext*<br/>
[out w] Określa kontekst użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Pływające mini okno ramowe zostanie utworzona w dwóch krokach. Po pierwsze, szablon tworzy `CPaneFrameWnd` obiektu. Po drugie, wywołuje `Create` tworzenie Windows pływające mini okno ramowe i dołącz ją do `CPaneFrameWnd` obiektu.

##  <a name="createex"></a>  CPaneFrameWnd::CreateEx

Tworzy okno pływające i dołącza je do [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) obiektu.

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parametry

*dwStyleEx*<br/>
[in] Określa styl okna rozszerzonej. Aby uzyskać więcej informacji, zobacz [rozszerzone Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
[in] Określa tekst do wyświetlenia w oknie pływające.

*dwStyle*<br/>
[in] Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[in] Określa początkowy rozmiar i położenie okna pływające.

*pParentWnd*<br/>
[out w] Określa nadrzędnej ramki okna pływające. Ta wartość nie może być równa NULL.

*pContext*<br/>
[out w] Określa kontekst użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Pływające mini okno ramowe zostanie utworzona w dwóch krokach. Po pierwsze, szablon tworzy `CPaneFrameWnd` obiektu. Po drugie, wywołuje `Create` tworzenie Windows pływające mini okno ramowe i dołącz ją do `CPaneFrameWnd` obiektu.

##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane

Stacje dokujące okienka.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parametry

*bWasDocked*<br/>
[out] Wartość TRUE, jeśli już był zadokowany okienka; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się powodzeniem, `CDockablePane` czy okienka zakończyło się; w przeciwnym razie wartość NULL.

##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID

Znajduje okienko o identyfikatorze określoną kontrolkę na globalnej liście okienka zmiennoprzecinkowy.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Reprezentuje identyfikator kontrolki okienka można znaleźć.

### <a name="return-value"></a>Wartość zwracana

Okienko o identyfikatorze określoną kontrolkę; w przeciwnym razie wartość NULL, jeśli okienko nie ma identyfikatora określoną kontrolkę.

##  <a name="framefrompoint"></a>  CPaneFrameWnd::FrameFromPoint

Wyszukuje okno mini ramki, zawierające określony punkt.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*(czas pacyficzny)*<br/>
[in] Punkt w współrzędne ekranu.

*nSensitivity*<br/>
[in] Zwiększ obszar wyszukiwania okna mini ramki, ten rozmiar. Okno mini ramki spełnia kryteria wyszukiwania, jeśli dany punkt mieści się w obszarze zwiększone.

*pFrameToExclude*<br/>
[in] Określa okna mini ramki, które mają zostać wykluczone w wyniku wyszukiwania.

*bFloatMultiOnly*<br/>
[in] W przypadku opcji TRUE tylko wyszukiwania okna mini ramki, które mają stylu CBRS_FLOAT_MULTI. Jeśli ma wartość FAŁSZ, wyszukaj wszystkie okna mini ramki.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna mini ramki, który zawiera *pt*; w przeciwnym razie wartość NULL.

##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight

Zwraca wysokość tytuł okna mini ramki.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach, okno mini ramki.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić wysokość okna mini ramki. Domyślnie wysokość jest równa SM_CYSMCAPTION. Aby uzyskać więcej informacji, zobacz [funkcja GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics).

##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect

Oblicza prostokąt otaczający tytuł okna mini ramki.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parametry

*rectCaption*<br/>
[out] Zawiera rozmiar i położenie tytuł okna mini ramki, w współrzędne ekranu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby obliczyć prostokąt otaczający tytuł okna mini ramki.

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

Zwraca tekst podpisu.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Wartość zwracana

Tekst podpisu okna mini ramki.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy Wyświetla tekst podpisu.

##  <a name="getdockingmanager"></a>  CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode

Zwraca tryb dokowania.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb dokowania. Jeden z następujących wartości:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane

Zwraca pierwszy widoczne okienko znajdujące się w przypadku okno mini ramki.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwszy okienko okna mini ramki, lub wartość NULL, jeśli okno mini ramki nie zawiera żadnych okienka.

##  <a name="gethotpoint"></a>  CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpane"></a>  CPaneFrameWnd::GetPane

Zwraca okienko, w którym znajduje się w przypadku okno mini ramki.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Wartość zwracana

Okienko w którym znajduje się w mini ramki, lub wartość NULL, jeśli nie okienka w oknie mini ramki.

### <a name="remarks"></a>Uwagi

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

Zwraca liczbę okienek, które są zawarte w okno mini ramki.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienka w oknie mini ramki. Wartość ta może wynosić zero.

### <a name="remarks"></a>Uwagi

##  <a name="getparent"></a>  CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getrecentfloatingrect"></a>  CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount

Zwraca liczbę widocznych okienek, które są zawarte w okno mini ramki.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych okienka.

### <a name="remarks"></a>Uwagi

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

Określa, jaka część okna mini ramki jest w danym momencie.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[in] Punkt do testowania.

*bDetectCaption*<br/>
[in] W przypadku opcji TRUE Sprawdź punkt względem podpis. Jeśli ma wartość FAŁSZ, Pomiń podpis.

### <a name="return-value"></a>Wartość zwracana

Jeden z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|HTNOWHERE|Punkt znajduje się poza okna mini ramki.|
|HTCLIENT|Punkt znajduje się w obszarze klienta.|
|HTCAPTION|Punkt znajduje się na podpis.|
|HTTOP|Punkt znajduje się na górze.|
|HTTOPLEFT|Punkt znajduje się w lewym górnym rogu.|
|HTTOPRIGHT|Punkt znajduje się w prawym górnym rogu.|
|HTLEFT|Punkt jest po lewej stronie.|
|HTRIGHT|Punkt jest po prawej stronie.|
|HTBOTTOM|Punkt znajduje się na dole.|
|HTBOTTOMLEFT|Punkt znajduje się w lewym dolnym rogu.|
|HTBOTTOMRIGHT|Punkt znajduje się w prawym dolnym rogu.|

##  <a name="iscaptured"></a>  CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown

Określa, czy okno mini ramki powinny zostać wycofana w dół.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno mini ramki musi zostać wycofana. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby określić, czy okno mini ramki powinny zostać wycofana w dół. Funkcja rollup/rolldown jest włączona dla okna mini ramki, jeśli zawiera on co najmniej jedno okienko, w którym ma flagę AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiona, gdy okienko zostanie utworzony. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się wewnątrz prostokąt otaczający okna mini ramki, aby ustalić, czy okno ma zostać wycofana w dół. Można zastąpić to zachowanie w klasie pochodnej.

##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp

Określa, czy okno mini ramki powinny być rzutowana.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli musi być rzutowana okna mini ramki; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby określić, czy okno mini ramki powinny być rzutowana. Funkcja rollup/rolldown jest włączona dla okna mini ramki, jeśli zawiera on co najmniej jedno okienko, w którym ma flagę AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiona, gdy okienko zostanie utworzony. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się wewnątrz prostokąt otaczający okna mini ramki, aby ustalić, czy okno ma być rzutowana. Można zastąpić to zachowanie w klasie pochodnej.

##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer

Zatrzymuje timer dokowania.

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Nazwa profilu.

*uiID*<br/>
[in] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli stan okienka został załadowany pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits

Określa, czy rejestrowanie klasy okna, którego styl CS_SAVEBITS klasy.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na wartość true, rejestrowanie klasy okna mini ramki, którego styl CS_SAVEBITS. To może pomóc zmniejszyć migotanie, gdy użytkownik przeciągnie okna mini ramki.

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

Określa, czy dokowanie jest możliwe.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli dokowanie jest możliwe; w przeciwnym razie wartość FALSE.

##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState

Określa, czy okno mini ramki powinny zostać wycofana w górę lub w dół.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby określić, czy okno mini ramki powinny zostać wycofana w górę lub w dół.

Domyślnie struktura wywołuje [CPaneFrameWnd::IsRollUp](#isrollup) i [CPaneFrameWnd::IsRollDown](#isrolldown) i po prostu rozciąga lub przywraca okno mini ramki. Można zastąpić tę metodę w klasie pochodnej, aby użyć innego efekt wizualny.

##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos

Dokowane okno mini ramki w jego najbardziej aktualne położenie.

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder

Rysuje obramowanie, okna mini ramki.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia używany do rysowania obramowania.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, by narysować obramowanie, okna mini ramki.

##  <a name="onkillrolluptimer"></a>  CPaneFrameWnd::OnKillRollUpTimer

Zatrzymuje timer zbiorczy.

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane

Przesuwa okno mini ramki określonego przesunięcia.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Wskaźnik do okienka (zignorowany).

*ptOffset*<br/>
[in] Przesunięcie, według którego ma zostać przeniesiona z okienka.

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

Dostosowuje układ okienka wewnątrz okna mini ramki.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy jego należy dostosować układ okienka wewnątrz okna mini ramki.

Domyślnie okienka znajduje się do pokrycia obszaru klienckiego pełne okna mini ramki.

##  <a name="onsetrolluptimer"></a>  CPaneFrameWnd::OnSetRollUpTimer

Ustawia czasomierza zbiorczy.

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane

Wywoływane przez platformę, gdy okienka w oknie mini ramki jest ukryta lub wyświetlone.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Okienko w którym jest widoczny, czy ukryty.

*bShow*<br/>
[in] Wartość TRUE, jeśli wyświetlany jest okienka; Wartość FALSE, jeśli jest on ukryty okienka.

### <a name="remarks"></a>Uwagi

Wywoływane przez platformę, gdy okienka w oknie mini ramki jest widoczny, czy ukryty. Domyślna implementacja nic nie robi.

##  <a name="pin"></a>  CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parametry

[in] *bPin*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="panefrompoint"></a>  CPaneFrameWnd::PaneFromPoint

Zwraca okienko, jeśli zawiera ona punkt dostarczone przez użytkownika wewnątrz okna mini ramki.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[in] Punkt, że użytkownik kliknął we współrzędnych ekranu.

*nSensitivity*<br/>
[in] Ten parametr nie jest używany.

*bCheckVisibility*<br/>
[in] Wartość TRUE, aby określić, czy ma zostać zwrócone tylko widoczne okienka; w przeciwnym razie wartość FALSE.

### <a name="return-value"></a>Wartość zwracana

Okienko w którym użytkownik kliknął element lub wartość NULL, jeśli okienko nie istnieje w tej lokalizacji.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu uzyskania okienko, który zawiera danego punktu.

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

Odrysowuje wszystkie okna mini ramki.

```
static void RedrawAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda aktualizuje wszystkie okna mini ramki, wywołując [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) dla każdego okna.

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

Metoda wywoływana przez platformę, by usunąć okienka nie jest ważna.

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane

Usuwa okienko z okna mini ramki.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[in] Wskaźnik do okienka do usunięcia.

*bDestroy*<br/>
[in] Określa, co się dzieje z okna mini ramki. Jeśli *bDestroy* ma wartość TRUE, ta metoda niszczy okno mini ramki natychmiast. Jeśli jest to wartość FALSE, ta metoda niszczy okno mini ramki z pewnym opóźnieniem.

*bNoDelayedDestroy*<br/>
[in] W przypadku opcji TRUE opóźnione zniszczenia jest wyłączona. W przypadku wartości FAŁSZ opóźnione zniszczenia jest włączona.

### <a name="remarks"></a>Uwagi

Struktura może zniszczyć windows mini ramki, bezpośrednio lub z pewnym opóźnieniem. Jeśli chcesz opóźnienie zniszczenie okna mini ramki, przekazać wartość FALSE w *bNoDelayedDestroy* parametru. Opóźnione zniszczenie występuje, gdy struktura przetwarza komunikat AFX_WM_CHECKEMPTYMINIFRAME.

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

Zastępuje jedno okienko z inną.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parametry

*pBarOrg*<br/>
[in] Wskaźnik do oryginalnego okienka.

*pBarReplaceWith*<br/>
[in] Wskaźnik do okienko w którym zastępuje oryginalny okienka.

##  <a name="savestate"></a>  CPaneFrameWnd::SaveState

Zapisuje stan w okienku w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[in] Nazwa profilu.

*uiID*<br/>
[in] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli stan okienka została zapisana pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

Ustawia podpis przycisków.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parametry

*dwButtons*<br/>
[in] Bitowe OR kombinacją następujących wartości:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parametry

[in] *bDelayShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parametry

[in] *pManager*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

Ustawia czasomierza dokowania.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parametry

*Nlimit*<br/>
[in] Wartość limitu czasu w milisekundach.

##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState

Ustawia stan dokowania.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parametry

*pDockManager*<br/>
[in] Wskaźnik dokowania menedżera.

##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parametry

[in] *ptNew*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpredockstate"></a>  CPaneFrameWnd::SetPreDockState

Metoda wywoływana przez platformę, by ustawić predocking stanu.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parametry

*preDockState*<br/>
[in] Możliwe wartości:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
[in] Wskaźnik do okienka, aby zadokować.

*dockMethod*<br/>
[in] Metoda dokowania. (Ten parametr jest ignorowany).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno mini ramki jest zadokowany; Wartość FALSE, jeśli jest zadokowany.

##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent

Dopasowuje rozmiar okna mini ramki, tak, że jest to równoważne do okienka zawarte.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dostosować rozmiar okna mini ramki do rozmiaru okienka zawarte.

##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff

Rysy Wyłącz menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[in] Wskaźnik do menu.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parametry

[in] *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

[in] *pDockingBar*<br/>
[in] *pTabbedBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
