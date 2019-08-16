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
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502971"
---
# <a name="cpaneframewnd-class"></a>Klasa CPaneFrameWnd

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

Implementuje okno mini-frame, które zawiera jedno okienko. Okienko wypełnia obszar klienta okna.

## <a name="syntax"></a>Składnia

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd:: Add— okienko](#addpane)|Dodaje okienko.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Dodaje lub usuwa okienko z globalnej listy.|
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Dostosowuje układ okna mini-frame.|
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Oblicza rozmiar obramowania dla okna z ramką minimalną.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicz oczekiwany prostokąt okna zadokowanego.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Określa, czy bieżące okienko może być zadokowane do innego okienka lub okna ramki.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Określa, czy okno mini-frame można zadokować w okienku.|
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje okienko na dokument z kartami.|
|[CPaneFrameWnd:: Create](#create)|Tworzy okno mini-frame i dołącza je do `CPaneFrameWnd` obiektu.|
|[CPaneFrameWnd::CreateEx](#createex)|Tworzy okno mini-frame i dołącza je do `CPaneFrameWnd` obiektu.|
|[CPaneFrameWnd::DockPane](#dockpane)|Dokowanie okienka.|
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Znajduje okienko o określonym IDENTYFIKATORze kontrolki na globalnej liście okienek zmiennoprzecinkowych.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Znajduje okno mini-frame zawierające punkt dostarczony przez użytkownika.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość nagłówka okna mini-frame.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Oblicza prostokąt związany z napisem w oknie mini-frame.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Zwraca tekst podpisu.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Zwraca tryb dokowania.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Zwraca pierwsze widoczne okienko, które jest zawarte w oknie mini-frame.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd:: getokienk](#getpane)|Zwraca okienko zawarte w oknie mini-frame.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Zwraca liczbę okienek, które są zawarte w oknie mini frame.|
|[CPaneFrameWnd:: GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Zwraca liczbę widocznych okienek, które są zawarte w oknie mini frame.|
|[CPaneFrameWnd::HitTest](#hittest)|Określa, która część okna mini frame znajduje się w danym punkcie.|
|[CPaneFrameWnd:: iscaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Określa, czy okno mini-frame powinno być rzutowane.|
|[CPaneFrameWnd:: isrollup](#isrollup)|Określa, czy okno mini-frame powinno być rzutowane.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zamyka czasomierz dokowania.|
|[CPaneFrameWnd:: LoadState](#loadstate)|Ładuje stan okienka z rejestru.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Określa, czy jest możliwe dokowanie.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Dockuje okno mini-frame na jego ostatniej pozycji.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Kończy czasomierz zestawienia.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Przenosi okno mini-frame według określonego przesunięcia.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Dostosowuje układ zawartego okienka.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Ustawia czasomierz zestawienia.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Wywoływane przez platformę, gdy okienko w oknie mini-frame jest ukryte lub wyświetlone.|
|[CPaneFrameWnd::P aneFromPoint](#panefrompoint)|Zwraca okienko, jeśli zawiera punkt dostarczony przez użytkownika wewnątrz okna mini-frame.|
|[CPaneFrameWnd::P w](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okna przed ich wysłaniem do funkcji [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows.|
|[CPaneFrameWnd::RedrawAll](#redrawall)|Ponownie rysuje wszystkie okna z systemem Windows.|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Wywoływane przez platformę w celu usunięcia nieprawidłowych okienek.|
|[CPaneFrameWnd::RemovePane](#removepane)|Usuwa okienko z okna mini-frame.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Zamienia jedno okienko na inne.|
|[CPaneFrameWnd:: SaveState](#savestate)|Zapisuje stan okienka w rejestrze.|
|`CPaneFrameWnd::Serialize`|Odczytuje lub zapisuje ten obiekt z lub do archiwum.|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Ustawia przyciski podpisu.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Ustawia czasomierz dokowania.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Ustawia stan dokowania.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Wywoływane przez platformę w celu ustawienia stanu zadokowania.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Dostosowuje rozmiar okna mini-frame w taki sposób, aby był on równy rozmiarowi zawartemu w okienku.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Oddziel menu.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Określa, czy okno mini-frame powinno być rzutowane w górę czy w dół.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Rysuje obramowanie okna mini-frame.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Określa, czy Klasa okna ma być zarejestrowana przy użyciu stylu klasy CS_SAVEBITS.|

## <a name="remarks"></a>Uwagi

Struktura automatycznie tworzy `CPaneFrameWnd` obiekt, gdy okienko jest przełączane ze stanu zadokowanego do stanu zmiennoprzecinkowego.

Okno mini-frame można przeciągnąć z widoczną zawartością (natychmiastowe dokowanie) lub przy użyciu prostokąta przeciągania (dokowanie standardowe). Tryb dokowania okienka kontenera mini-frame określa zachowanie przeciągania w ramce mini. Aby uzyskać więcej informacji, zobacz [CBasePane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Okno mini-frame Wyświetla przyciski na podpisie zgodnie z stylem zawartego okienka. Jeśli okienko można zamknąć ( [CBasePane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), zostanie wyświetlony przycisk Zamknij. Jeśli okienko ma styl AFX_CBRS_AUTO_ROLLUP, zostanie wyświetlony kod PIN.

W przypadku wyprowadzania klasy z `CPaneFrameWnd`, musisz popowiedzieć strukturę jak ją utworzyć. Utwórz klasę, zastępując [CPane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), lub ustaw `CPane::m_pMiniFrameRTC` element członkowski tak, aby wskazywał na informacje o klasie środowiska uruchomieniowego klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxPaneFrameWnd. h

##  <a name="addpane"></a>CPaneFrameWnd:: Add— okienko

Dodaje okienko.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Okienko do dodania.

##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList

Dodaje lub usuwa okienko z globalnej listy.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Okienko do dodania lub usunięcia.

*bDodaj*<br/>
podczas Jeśli wartość jest różna od zera, Dodaj okienko. Jeśli wartość jest równa 0, Usuń okienko.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

##  <a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout

Dostosowuje układ okna mini-frame.

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Uwagi

##  <a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize

Oblicza rozmiar obramowań dla okna mini.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parametry

*rectBorderSize*<br/>
określoną Zawiera rozmiar obramowania okna mini w pikselach.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę w celu obliczenia rozmiaru obramowania okna mini. Zwrócony rozmiar zależy od tego, czy okno mini zawiera pasek narzędzi lub [CDockablePane](../../mfc/reference/cdockablepane-class.md).

##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect

Oblicz oczekiwany prostokąt okna zadokowanego.

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
podczas Wskaźnik do okna, które ma zostać zadokowane.

*ptMouse*<br/>
podczas Lokalizacja myszy.

*rectResult*<br/>
określoną Obliczony prostokąt.

*bDrawTab*<br/>
określoną Jeśli wartość jest równa TRUE, narysuj kartę. W przypadku wartości FALSE nie Rysuj karty.

*ppTargetBar*<br/>
określoną Wskaźnik do okienka Target.

### <a name="remarks"></a>Uwagi

Ta metoda oblicza prostokąt, który zostanie zajmowany przez okno, gdy użytkownik przeciągnięcie okna do punktu określonego przez *ptMouse* i zadokuje go.

##  <a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached

Określa, czy bieżące okienko może być zadokowane do innego okienka lub okna ramki.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okienko może być zadokowane do innego okienka lub okna ramki; w przeciwnym razie FALSE.

##  <a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane

Określa, czy okno mini-frame można zadokować w okienku.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parametry

*pDockingBar*<br/>
podczas Okienko.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli mini-frame można zadokować do *pDockingBar*; w przeciwnym razie 0.

##  <a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Uwagi

##  <a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument

Konwertuje okienko na dokument z kartami.

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>CPaneFrameWnd:: Create

Tworzy okno mini i dołącza je do obiektu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

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
podczas Określa tekst, który ma być wyświetlany w oknie mini.

*dwStyle*<br/>
podczas Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*cinania*<br/>
podczas Określa początkowy rozmiar i położenie okna mini.

*pParentWnd*<br/>
[in. out] Określa ramkę nadrzędną okna mini. Ta wartość nie może być RÓWNa NULL.

*pContext*<br/>
[in. out] Określa kontekst zdefiniowany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okno zostało utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno mini jest tworzone w dwóch krokach. Po pierwsze, struktura tworzy `CPaneFrameWnd` obiekt. Drugi wywołuje `Create` , aby utworzyć okno mini systemu Windows i dołączyć je `CPaneFrameWnd` do obiektu.

##  <a name="createex"></a>CPaneFrameWnd::CreateEx

Tworzy okno mini i dołącza je do obiektu [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

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
podczas Określa styl okna rozszerzonego. Aby uzyskać więcej informacji, zobacz [Style okna rozszerzonego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
podczas Określa tekst, który ma być wyświetlany w oknie mini.

*dwStyle*<br/>
podczas Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*cinania*<br/>
podczas Określa początkowy rozmiar i położenie okna mini.

*pParentWnd*<br/>
[in. out] Określa ramkę nadrzędną okna mini. Ta wartość nie może być RÓWNa NULL.

*pContext*<br/>
[in. out] Określa kontekst zdefiniowany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okno zostało utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno mini jest tworzone w dwóch krokach. Po pierwsze, struktura tworzy `CPaneFrameWnd` obiekt. Drugi wywołuje `Create` , aby utworzyć okno mini systemu Windows i dołączyć je `CPaneFrameWnd` do obiektu.

##  <a name="dockpane"></a>CPaneFrameWnd::D ockPane

Dokowanie okienka.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parametry

*bWasDocked*<br/>
określoną Ma wartość TRUE, jeśli okienko zostało już zadokowane; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się pomyślnie `CDockablePane` , to okienko zostało zadokowane; w przeciwnym razie wartość null.

##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID

Znajduje okienko o określonym IDENTYFIKATORze kontrolki na globalnej liście okienek zmiennoprzecinkowych.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
podczas Reprezentuje identyfikator kontrolki okienka do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Okienko z określonym IDENTYFIKATORem kontrolki; w przeciwnym razie wartość NULL, jeśli żadne okienko nie ma określonego identyfikatora formantu.

##  <a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint

Znajduje okno mini-frame zawierające określony punkt.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*zmiennoprzecinkow*<br/>
podczas Punkt, we współrzędnych ekranu.

*nSensitivity*<br/>
podczas Zwiększ obszar wyszukiwania okna mini frame o ten rozmiar. Okno mini-frame spełnia kryteria wyszukiwania, jeśli dany punkt znajduje się w większym obszarze.

*pFrameToExclude*<br/>
podczas Określa okno mini-frame do wykluczenia z wyszukiwania.

*bFloatMultiOnly*<br/>
podczas W przypadku wartości TRUE należy przeszukać tylko okna z systemem Windows, które mają styl CBRS_FLOAT_MULTI. W przypadku wartości FALSE Wyszukaj wszystkie okna z systemem Windows.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna mini-frame zawierającego *pt*; w przeciwnym razie wartość NULL.

##  <a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight

Zwraca wysokość nagłówka okna mini-frame.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość okna mini frame w pikselach.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić wysokość okna mini-frame. Domyślnie wysokość jest równa SM_CYSMCAPTION. Aby uzyskać więcej informacji, zobacz [Funkcja GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

##  <a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect

Oblicza prostokąt związany z napisem w oknie mini-frame.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parametry

*rectCaption*<br/>
określoną Zawiera rozmiar i położenie podpisu okna mini-frame, we współrzędnych ekranu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby obliczyć prostokąt związany z napisem w oknie mini-frame.

##  <a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText

Zwraca tekst podpisu.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Wartość zwracana

Tekst podpisu okna mini-frame.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy wyświetla tekst podpisu.

##  <a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode

Zwraca tryb dokowania.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb dokowania. Jedna z następujących wartości:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane

Zwraca pierwsze widoczne okienko, które jest zawarte w oknie mini-frame.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze okienko w oknie mini-frame lub wartość NULL, jeśli okno mini-frame nie zawiera żadnych okienek.

##  <a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpane"></a>CPaneFrameWnd:: getokienk

Zwraca okienko zawarte w oknie mini-frame.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Wartość zwracana

Okienko, które znajduje się w tej samej ramce, lub ma wartość NULL, jeśli okno mini-frame nie zawiera żadnych okienek.

### <a name="remarks"></a>Uwagi

##  <a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount

Zwraca liczbę okienek, które są zawarte w oknie mini frame.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienek w oknie mini-frame. Ta wartość może być równa zero.

### <a name="remarks"></a>Uwagi

##  <a name="getparent"></a>CPaneFrameWnd:: GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getpinstate"></a>CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount

Zwraca liczbę widocznych okienek, które są zawarte w oknie mini frame.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych okienek.

### <a name="remarks"></a>Uwagi

##  <a name="hittest"></a>CPaneFrameWnd::HitTest

Określa, która część okna mini frame znajduje się w danym punkcie.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parametry

*moment*<br/>
podczas Punkt do przetestowania.

*bDetectCaption*<br/>
podczas W przypadku opcji TRUE Sprawdź, czy punkt znajduje się na podpisie. W przypadku wartości FALSE zignoruj napis.

### <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|HTNOWHERE|Punkt znajduje się poza oknem mini-frame.|
|HTCLIENT|Punkt znajduje się w obszarze klienta.|
|HTCAPTION|Punkt znajduje się na podpisie.|
|HTTOP|Punkt znajduje się u góry.|
|HTTOPLEFT|Punkt znajduje się w lewym górnym rogu.|
|HTTOPRIGHT|Punkt znajduje się w prawym górnym rogu.|
|HTLEFT|Punkt znajduje się po lewej stronie.|
|HTRIGHT|Punkt znajduje się po prawej stronie.|
|HTBOTTOM|Punkt znajduje się u dołu.|
|HTBOTTOMLEFT|Punkt znajduje się w lewym dolnym rogu.|
|HTBOTTOMRIGHT|Punkt znajduje się w prawym dolnym rogu.|

##  <a name="iscaptured"></a>CPaneFrameWnd:: iscaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isrolldown"></a>CPaneFrameWnd::IsRollDown

Określa, czy okno mini-frame powinno być rzutowane.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno mini-frame musi być rzutowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę w celu ustalenia, czy okno mini-frame powinno być rzutowane. Funkcja ROLLUP/rolldown jest włączona dla okna mini-frame, jeśli zawiera co najmniej jedno okienko, które ma flagę AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiana podczas tworzenia okienka. Aby uzyskać więcej informacji, zobacz [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się w obrębie prostokąta ograniczonego okna mini frame, aby określić, czy okno ma być rzutowane. To zachowanie można zastąpić w klasie pochodnej.

##  <a name="isrollup"></a>CPaneFrameWnd:: isrollup

Określa, czy okno mini-frame powinno być rzutowane.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno mini-frame musi być rzutowane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę w celu ustalenia, czy okno mini-frame powinno być rzutowane. Funkcja ROLLUP/rolldown jest włączona dla okna mini-frame, jeśli zawiera co najmniej jedno okienko, które ma flagę AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiana podczas tworzenia okienka. Aby uzyskać więcej informacji, zobacz [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się w obrębie prostokąta ograniczonego okna mini frame, aby określić, czy okno ma zostać rzutowane. To zachowanie można zastąpić w klasie pochodnej.

##  <a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer

Zamyka czasomierz dokowania.

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>CPaneFrameWnd:: LoadState

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Nazwa profilu.

*uiID*<br/>
podczas Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli stan okienka został pomyślnie załadowany; w przeciwnym razie FALSE.

##  <a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits

Określa, czy ma zostać zarejestrowana Klasa okna, która ma styl klasy CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na wartość TRUE, aby zarejestrować klasę okna mini-frame, która ma styl CS_SAVEBITS. Może to pomóc w zmniejszeniu migotania, gdy użytkownik przeciągnie okno z ramką minimalną.

##  <a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock

Określa, czy jest możliwe dokowanie.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli jest możliwe dokowanie; w przeciwnym razie FALSE.

##  <a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState

Określa, czy okno mini-frame powinno być rzutowane w górę czy w dół.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę w celu ustalenia, czy okno mini-frame powinno być rzutowane lub wyłączone.

Domyślnie architektura wywołuje [CPaneFrameWnd:: isrollup](#isrollup) i [CPaneFrameWnd:: IsRollDown](#isrolldown) i po prostu rozciąga lub przywraca okno mini-frame. Można zastąpić tę metodę w klasie pochodnej, aby użyć innego efektu wizualnego.

##  <a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos

Dockuje okno mini-frame na jego ostatniej pozycji.

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder

Rysuje obramowanie okna mini-frame.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia używany do rysowania obramowania.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę do rysowania obramowań okna mini-frame.

##  <a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer

Kończy czasomierz zestawienia.

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>CPaneFrameWnd::OnMovePane

Przenosi okno mini-frame według określonego przesunięcia.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
podczas Wskaźnik do okienka (zignorowane).

*ptOffset*<br/>
podczas Przesunięcie, według którego ma zostać przeniesione okienko.

##  <a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout

Dostosowuje układ okienka wewnątrz okna mini-frame.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy musi dostosować układ okienka wewnątrz okna mini-frame.

Domyślnie okienko jest umieszczane w celu pokrycia całego obszaru klienta okna mini-frame.

##  <a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer

Ustawia czasomierz zestawienia.

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>CPaneFrameWnd::OnShowPane

Wywoływane przez platformę, gdy okienko w oknie mini-frame jest ukryte lub wyświetlone.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
podczas Okienko, które jest wyświetlane lub ukryte.

*bShow*<br/>
podczas PRAWDA, jeśli okienko jest wyświetlane; Wartość FALSE, jeśli okienko jest ukrywane.

### <a name="remarks"></a>Uwagi

Wywoływane przez platformę, gdy okienko w oknie mini-frame jest wyświetlane lub ukryte. Domyślna implementacja nie robi nic.

##  <a name="pin"></a>CPaneFrameWnd::P w

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parametry

podczas *bPin*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="panefrompoint"></a>CPaneFrameWnd::P aneFromPoint

Zwraca okienko, jeśli zawiera punkt dostarczony przez użytkownika wewnątrz okna mini-frame.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parametry

*moment*<br/>
podczas Punkt kliknięty przez użytkownika w obszarze Współrzędne ekranu.

*nSensitivity*<br/>
podczas Ten parametr nie jest używany.

*bCheckVisibility*<br/>
podczas PRAWDA, aby określić, że mają być zwracane tylko widoczne okienka; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Okienko kliknięte przez użytkownika lub wartość NULL, jeśli w tej lokalizacji nie ma żadnego okienka.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby uzyskać okienko zawierające dany punkt.

##  <a name="redrawall"></a>CPaneFrameWnd::RedrawAll

Ponownie rysuje wszystkie okna z systemem Windows.

```
static void RedrawAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda aktualizuje wszystkie okna z systemem Windows przez wywołanie [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) dla każdego z nich.

##  <a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes

Wywoływane przez platformę w celu usunięcia nieprawidłowych okienek.

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>CPaneFrameWnd::RemovePane

Usuwa okienko z okna mini-frame.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do okienka do usunięcia.

*bDestroy*<br/>
podczas Określa, co się dzieje z oknem mini-frame. Jeśli *bDestroy* ma wartość true, ta metoda natychmiast niszczy okno mini-frame. Jeśli ma wartość FALSE, ta metoda niszczy okno mini-frame po określonym opóźnieniu.

*bNoDelayedDestroy*<br/>
podczas Jeśli wartość jest równa TRUE, opóźnione zniszczenie jest wyłączone. W przypadku wartości FALSE jest włączone niszczenie opóźnione.

### <a name="remarks"></a>Uwagi

Platforma może zniszczyć okna z ramkami mini natychmiast lub po pewnym opóźnieniu. Aby opóźnić zniszczenie okien z systemem Windows, w parametrze *bNoDelayedDestroy* należy przekazać wartość false. Opóźnione zniszczenie występuje, gdy struktura przetwarza komunikat AFX_WM_CHECKEMPTYMINIFRAME.

##  <a name="replacepane"></a>CPaneFrameWnd::ReplacePane

Zamienia jedno okienko na inne.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parametry

*pBarOrg*<br/>
podczas Wskaźnik do oryginalnego okienka.

*pBarReplaceWith*<br/>
podczas Wskaźnik do okienka, które zastępuje oryginalne okienko.

##  <a name="savestate"></a>CPaneFrameWnd:: SaveState

Zapisuje stan okienka w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
podczas Nazwa profilu.

*uiID*<br/>
podczas Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli stan okienka został pomyślnie zapisany; w przeciwnym razie FALSE.

##  <a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons

Ustawia przyciski podpisu.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parametry

*dwButtons*<br/>
podczas Bitowe lub kombinacje następujących wartości:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parametry

podczas *bDelayShow*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parametry

podczas *pManager*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer

Ustawia czasomierz dokowania.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parametry

*nTimeOut*<br/>
podczas Wartość limitu czasu (w milisekundach).

##  <a name="setdockstate"></a>CPaneFrameWnd::SetDockState

Ustawia stan dokowania.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parametry

*pDockManager*<br/>
podczas Wskaźnik do Menedżera dokowania.

##  <a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parametry

podczas *ptNew*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState

Wywoływane przez platformę w celu ustawienia stanu zadokowania.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parametry

*preDockState*<br/>
podczas Możliwe wartości:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
podczas Wskaźnik do okienka, które ma zostać zadokowane.

*dockMethod*<br/>
podczas Metoda dokowania. (Ten parametr jest ignorowany).

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli okno mini-frame nie jest zadokowane. Wartość FALSE, jeśli jest zadokowany.

##  <a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent

Dostosowuje rozmiar okna mini-frame w taki sposób, aby był on równoważny z zawartym okienkiem.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dostosować rozmiar okna mini-frame do rozmiaru zawartego okienka.

##  <a name="starttearoff"></a>CPaneFrameWnd::StartTearOff

Oddziel menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
podczas Wskaźnik do menu.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

##  <a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parametry

podczas *pBar*<br/>

### <a name="remarks"></a>Uwagi

##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

podczas *pDockingBar*<br/>
podczas *pTabbedBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
