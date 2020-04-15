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
ms.openlocfilehash: 02eee13928979a7d220ce03f9f61c789c6320b6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364096"
---
# <a name="cpaneframewnd-class"></a>Klasa CPaneFrameWnd

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

Implementuje okno mini-ramki, które zawiera jedno okienko. Okienko wypełnia obszar klienta okna.

## <a name="syntax"></a>Składnia

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::Dodajpan](#addpane)|Dodaje okienko.|
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Dodaje lub usuwa okienko z listy globalnej.|
|[CPaneFrameWnd::Dopasujlayout](#adjustlayout)|Dostosowuje układ okna mini-ramki.|
|[CPaneFrameWnd::Dopasuj ramki panelu](#adjustpaneframes)||
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Oblicza rozmiar obramowań dla okna mini-ramki.|
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Oblicz oczekiwany prostokąt zadokowanego okna.|
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Określa, czy bieżące okienko może być zadokowane do innego okienka lub okna ramki.|
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Określa, czy okno miniklatki można zadokować do okienka.|
|[CPaneFrameWnd::CheckGripperWiowalność](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Konwertuje okienko na dokument z kartami.|
|[CPaneFrameWnd::Utwórz](#create)|Tworzy okno mini-ramki i dołącza `CPaneFrameWnd` je do obiektu.|
|[CPaneFrameWnd::CreateEx](#createex)|Tworzy okno mini-ramki i dołącza `CPaneFrameWnd` je do obiektu.|
|[CPaneFrameWnd::DockPane](#dockpane)|Dokuje okienko.|
|[CPaneFrameWnd::ZnajdźFloatingPaneByID](#findfloatingpanebyid)|Znajduje okienko o określonym identyfikatorze formantu na globalnej liście ruchomych okienek.|
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Znajduje okno mini-ramki zawierające punkt dostarczony przez użytkownika.|
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Zwraca wysokość podpisu okna mini-ramki.|
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Oblicza prostokąt ograniczający podpis okna mini-ramki.|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Zwraca tekst podpisu.|
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Zwraca tryb dokowania.|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Zwraca pierwsze widoczne okienko znajdujące się w oknie miniklatki.|
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|Zwraca okienko znajdujące się w oknie miniklatki.|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Zwraca liczbę okienek znajdujących się w oknie miniklatka.|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Zwraca liczbę widocznych okienek znajdujących się w oknie miniklatka.|
|[CPaneFrameWnd::HitTest](#hittest)|Określa, jaka część okna mini-ramki znajduje się w danym punkcie.|
|[CPaneFrameWnd::IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Określa, czy okno mini-ramki powinno zostać zwinięte w dół.|
|[CPaneFrameWnd::IsRollUp](#isrollup)|Określa, czy okno mini-ramki ma być zwinięte.|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Zatrzymuje czasomierz dokowania.|
|[CPaneFrameWnd::Stan obciążenia](#loadstate)|Ładuje stan okienka z rejestru.|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Określa, czy dokowanie jest możliwe.|
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Dokuje okno mini-ramki w ostatniej pozycji.|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Zatrzymuje czasomierz zestawienia.|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Przenosi okno mini-ramki o określone przesunięcie.|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Dostosowuje układ okienka zamkniętego.|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Ustawia czasomierz zestawienia.|
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Wywoływane przez strukturę, gdy okienko w oknie mini-ramki jest ukryte lub wyświetlane.|
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Zwraca okienko, jeśli zawiera ono punkt dostarczony przez użytkownika wewnątrz okna miniklatki.|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do tłumaczenia wiadomości okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows.|
|[CPaneFrameWnd::RedrawAll](#redrawall)|Przerysowuje wszystkie okna mini-frame.|
|[CPaneFrameWnd::Usuń NienavalidPanes](#removenonvalidpanes)|Wywoływane przez platformę, aby usunąć nieważne okienka.|
|[CPaneFrameWnd::Usuńpan](#removepane)|Usuwa okienko z okna mini-ramki.|
|[CPaneFrameWnd::ReplacePane](#replacepane)|Zastępuje jedno okienko innym.|
|[CPaneFrameWnd::Zapisz stan](#savestate)|Zapisuje stan okienka w rejestrze.|
|`CPaneFrameWnd::Serialize`|Odczytuje lub zapisuje ten obiekt z lub do archiwum.|
|[CPaneFrameWnd::Przyciskiskładów](#setcaptionbuttons)|Ustawia przyciski podpisów.|
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Ustawia czasomierz dokowania.|
|[CPaneFrameWnd::SetDockState](#setdockstate)|Ustawia stan dokowania.|
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Wywoływana przez ramy, aby ustawić stan predocking.|
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Dostosowuje rozmiar okna mini-ramki tak, aby był odpowiednikiem rozmiaru okienka zamkniętego.|
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Odrywa menu.|
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Określa, czy okno mini-ramki ma być zwijane w górę czy w dół.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Rysuje obramowania okna mini-ramki.|

### <a name="data-members"></a>Elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Określa, czy klasa okna ma być rejestrowana w stylu klasy CS_SAVEBITS.|

## <a name="remarks"></a>Uwagi

Struktura automatycznie tworzy `CPaneFrameWnd` obiekt, gdy okienko jest przełączane ze stanu zadokowanego do stanu przestawnego.

Okno mini-ramki można przeciągać z widoczną zawartością (natychmiastowe dokowanie) lub za pomocą prostokąta przeciągania (standardowe dokowanie). Tryb dokowania okienka kontenera mini-ramki określa zachowanie przeciągania miniramki. Aby uzyskać więcej informacji, zobacz [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Okno mini-ramki wyświetla przyciski na podpisie zgodnie ze stylem okienka. Jeśli okienko można zamknąć ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), wyświetla przycisk Zamknij. Jeśli okienko ma styl AFX_CBRS_AUTO_ROLLUP, wyświetla pinezkę.

Jeśli pochodzisz klasy `CPaneFrameWnd`z , należy powiedzieć struktury, jak go utworzyć. Utwórz klasę przez zastąpienie [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), lub `CPane::m_pMiniFrameRTC` ustaw element członkowski tak, aby wskazuje informacje o klasie runtime dla klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxPaneFrameWnd.h

## <a name="cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFrameWnd::Dodajpan

Dodaje okienko.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Okienko do dodania.

## <a name="cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList

Dodaje lub usuwa okienko z listy globalnej.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Okienko do dodania lub usunięcia.

*Bdodaj*<br/>
[w] Jeśli nie zero, dodaj okienko. Jeśli 0, usuń okienko.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0.

## <a name="cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFrameWnd::Dopasujlayout

Dostosowuje układ okna mini-ramki.

```
virtual void AdjustLayout();
```

## <a name="cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFrameWnd::Dopasuj ramki panelu

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize

Oblicza rozmiar obramowań dla okna miniframe.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parametry

*rozmiar rectBorderSize*<br/>
[na zewnątrz] Zawiera rozmiar ( w pikselach) obramowania okna miniframe.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez strukturę do obliczania rozmiaru obramowania okna miniframe. Zwrócony rozmiar zależy od tego, czy okno miniframe zawiera pasek narzędzi, czy [CDockablePane](../../mfc/reference/cdockablepane-class.md).

## <a name="cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect

Oblicz oczekiwany prostokąt zadokowanego okna.

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parametry

*pWndToDock (Doł.*<br/>
[w] Wskaźnik do okna do stacji dokującej.

*ptMouse (polski)*<br/>
[w] Lokalizacja myszy.

*reectResult*<br/>
[na zewnątrz] Obliczony prostokąt.

*bNaładka*<br/>
[na zewnątrz] Jeśli wartość PRAWDA, narysuj kartę. Jeśli FAŁD, nie należy rysować kartę.

*ppTargetBar (Pasek celetu)*<br/>
[na zewnątrz] Wskaźnik do okienka docelowego.

### <a name="remarks"></a>Uwagi

Ta metoda oblicza prostokąt, który zajmie okno, jeśli użytkownik przeciągnął okno do punktu określonego przez *ptMouse* i zadokował go tam.

## <a name="cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached

Określa, czy bieżące okienko może być zadokowane do innego okienka lub okna ramki.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okienko można zadokować do innego okienka lub okna ramki; w przeciwnym razie FALSE.

## <a name="cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane

Określa, czy okno miniklatki można zadokować do okienka.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parametry

*pDockingBar (kierownica)*<br/>
[w] Okienko.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli mini-rama może być zadokowany do *pDockingBar;* w przeciwnym razie 0.

## <a name="cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperWiowalność

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument

Konwertuje okienko na dokument z kartami.

```
virtual void ConvertToTabbedDocument();
```

## <a name="cpaneframewndcreate"></a><a name="create"></a>CPaneFrameWnd::Utwórz

Tworzy okno miniframe i dołącza je do obiektu [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

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
[w] Określa tekst wyświetlany w oknie miniframe.

*Dwstyle*<br/>
[w] Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[w] Określa początkowy rozmiar i położenie okna miniframe.

*pParentWnd*<br/>
[w, na zewnątrz] Określa ramkę nadrzędną okna miniframe. Ta wartość nie może być null.

*Pcontext*<br/>
[w, na zewnątrz] Określa kontekst zdefiniowany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno miniframe jest tworzone w dwóch krokach. Po pierwsze, struktura `CPaneFrameWnd` tworzy obiekt. Po drugie, `Create` wywołuje utworzenie okna miniframe systemu `CPaneFrameWnd` Windows i dołączenie go do obiektu.

## <a name="cpaneframewndcreateex"></a><a name="createex"></a>CPaneFrameWnd::CreateEx

Tworzy okno miniframe i dołącza je do obiektu [CPaneFrameWnd.](../../mfc/reference/cpaneframewnd-class.md)

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

*dwStyleEx (np.*<br/>
[w] Określa styl okna rozszerzonego. Aby uzyskać więcej informacji, zobacz [Style okien rozszerzonych](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
[w] Określa tekst wyświetlany w oknie miniframe.

*Dwstyle*<br/>
[w] Określa styl okna. Aby uzyskać więcej informacji, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Rect*<br/>
[w] Określa początkowy rozmiar i położenie okna miniframe.

*pParentWnd*<br/>
[w, na zewnątrz] Określa ramkę nadrzędną okna miniframe. Ta wartość nie może być null.

*Pcontext*<br/>
[w, na zewnątrz] Określa kontekst zdefiniowany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało utworzone pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Okno miniframe jest tworzone w dwóch krokach. Po pierwsze, struktura `CPaneFrameWnd` tworzy obiekt. Po drugie, `Create` wywołuje utworzenie okna miniframe systemu `CPaneFrameWnd` Windows i dołączenie go do obiektu.

## <a name="cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFrameWnd::DockPane

Dokuje okienko.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parametry

*bWasDocked*<br/>
[na zewnątrz] PRAWDA, jeśli okienko było już zadokowane; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Jeśli operacja zakończyła się `CDockablePane` pomyślnie, okienko, do których zadokowano; w przeciwnym razie NULL.

## <a name="cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFrameWnd::ZnajdźFloatingPaneByID

Znajduje okienko o określonym identyfikatorze formantu na globalnej liście ruchomych okienek.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Reprezentuje identyfikator formantu okienka do znalezienia.

### <a name="return-value"></a>Wartość zwracana

Okienko o określonym identyfikatorze formantu; w przeciwnym razie NULL, jeśli żadne okienko nie ma określonego identyfikatora formantu.

## <a name="cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint

Znajduje okno mini-ramki, które zawiera określony punkt.

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
[w] Punkt, we współrzędnych ekranu.

*nWrażliwość*<br/>
[w] Zwiększ obszar wyszukiwania okna mini-ramki o ten rozmiar. Okno z mini ramką spełnia kryteria wyszukiwania, jeśli dany punkt spadnie w powiększonym obszarze.

*pFrameToExclude*<br/>
[w] Określa okno mini-ramki, które ma być wykluczone z wyszukiwania.

*bFloatMultiOnly*<br/>
[w] Jeśli true, tylko wyszukać okna mini-frame, które mają styl CBRS_FLOAT_MULTI. Jeśli fałsz, przeszukaj wszystkie okna mini-ramki.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do okna mini-ramki zawierającej *pt*; w przeciwnym razie NULL.

## <a name="cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight

Zwraca wysokość podpisu okna mini-ramki.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Wartość zwracana

Wysokość okna mini-ramki w pikselach.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić wysokość okna mini-ramki. Domyślnie wysokość jest ustawiona na SM_CYSMCAPTION. Aby uzyskać więcej informacji, zobacz [Funkcja GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

## <a name="cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect

Oblicza prostokąt ograniczający podpis okna mini-ramki.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parametry

*rectCaption (rectCaption)*<br/>
[na zewnątrz] Zawiera rozmiar i położenie podpisu okna mini-ramki we współrzędnych ekranu.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez strukturę do obliczania prostokąta ograniczającego podpis okna mini-ramki.

## <a name="cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText

Zwraca tekst podpisu.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Wartość zwracana

Tekst podpisu okna mini-ramki.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy wyświetla tekst podpisu.

## <a name="cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode

Zwraca tryb dokowania.

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>Wartość zwracana

Tryb dokowania. Jedna z następujących wartości:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

## <a name="cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane

Zwraca pierwsze widoczne okienko znajdujące się w oknie miniklatki.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Wartość zwracana

Pierwsze okienko w oknie mini-ramki lub NULL, jeśli okno mini-ramki nie zawiera okienek.

## <a name="cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFrameWnd::GetPane

Zwraca okienko znajdujące się w oknie miniklatki.

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Wartość zwracana

Okienko, które znajduje się w mini-ramce lub NULL, jeśli okno mini-ramki nie zawiera okienek.

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount

Zwraca liczbę okienek znajdujących się w oknie miniklatka.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba okienek w oknie mini-ramki. Ta wartość może wynosić zero.

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount

Zwraca liczbę widocznych okienek znajdujących się w oknie miniklatka.

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba widocznych okienek.

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndhittest"></a><a name="hittest"></a>CPaneFrameWnd::HitTest

Określa, jaka część okna mini-ramki znajduje się w danym punkcie.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[w] Punkt do przetestowania.

*bDetectCaption (Usuwanie korygów)*<br/>
[w] Jeśli wartość TRUE, sprawdź punkt względem podpisu. Jeśli fałsz, zignoruj podpis.

### <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

|Wartość|Znaczenie|
|-----------|-------------|
|HTNOWHERE|Punkt znajduje się poza oknem mini-ramki.|
|HTCliENT (Ł.|Punkt znajduje się w obszarze klienta.|
|APLIKACJA HTCAPTION|Punkt jest na podpisie.|
|HTTOP ( HTTOP )|Punkt jest na górze.|
|HTTOPLEFT (HTTOPLEFT)|Punkt znajduje się w lewym górnym rogu.|
|HTTOPRIGHT ( HTTOPRIGHT )|Punkt znajduje się w prawym górnym rogu.|
|Okręg wyborczy HTLEFT|Punkt jest po lewej stronie.|
|HTRIGHT ( HTRIGHT )|Punkt jest po prawej stronie.|
|HTBOTTOM ( HTBOTTOM )|Punkt jest na dole.|
|HTBOTTOMLEFT|Punkt znajduje się w lewym dolnym rogu.|
|HTBOTTOMRIGHT ( HTBOTTOMRIGHT )|Punkt znajduje się w prawym dolnym rogu.|

## <a name="cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFrameWnd::IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFrameWnd::IsRollDown

Określa, czy okno mini-ramki powinno zostać zwinięte w dół.

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno mini-ramki musi być zwinięte; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby ustalić, czy okno mini-ramki powinny być zwijane w dół. Funkcja zbiorcza/zbiorcza jest włączona dla okna mini-ramki, jeśli zawiera co najmniej jedno okienko z flagą AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiana podczas tworzenia okienka. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się wewnątrz prostokąta ograniczającego okno mini-ramki, aby określić, czy okno musi zostać zwinięte w dół. To zachowanie można zastąpić w klasie pochodnej.

## <a name="cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFrameWnd::IsRollUp

Określa, czy okno mini-ramki ma być zwinięte.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno mini-ramki musi być zwinięte; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby ustalić, czy okno mini-ramki powinny być rzutowane. Funkcja zbiorcza/zbiorcza jest włączona dla okna mini-ramki, jeśli zawiera co najmniej jedno okienko z flagą AFX_CBRS_AUTO_ROLLUP. Ta flaga jest ustawiana podczas tworzenia okienka. Aby uzyskać więcej informacji, zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

Domyślnie struktura sprawdza, czy wskaźnik myszy znajduje się wewnątrz prostokąta ograniczającego okno mini-ramki, aby określić, czy okno ma zostać zwinięte. To zachowanie można zastąpić w klasie pochodnej.

## <a name="cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer

Zatrzymuje czasomierz dokowania.

```
void KillDockingTimer();
```

## <a name="cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFrameWnd::Stan obciążenia

Ładuje stan okienka z rejestru.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Nazwa profilu.

*Uiid*<br/>
[w] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli stan okienka został pomyślnie załadowany; w przeciwnym razie FALSE.

## <a name="cpaneframewndm_busesavebits"></a><a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits

Określa, czy mają być rejestrowane klasy okna, która ma styl klasy CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Uwagi

Ustaw ten statyczny element członkowski na TRUE, aby zarejestrować klasę okna mini-ramki, która ma styl CS_SAVEBITS. Może to pomóc zmniejszyć migotanie, gdy użytkownik przeciągnie okno mini-ramki.

## <a name="cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock

Określa, czy dokowanie jest możliwe.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli dokowanie jest możliwe; w przeciwnym razie FALSE.

## <a name="cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState

Określa, czy okno mini-ramki ma być zwijane w górę czy w dół.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, aby ustalić, czy okno mini-ramki powinny być rzutowane w górę lub w dół.

Domyślnie struktura wywołuje [CPaneFrameWnd::IsRollUp](#isrollup) i [CPaneFrameWnd::IsRollDown](#isrolldown) i po prostu rozciąga lub przywraca okno mini-ramki. Tę metodę można zastąpić w klasie pochodnej, aby użyć innego efektu wizualnego.

## <a name="cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos

Dokuje okno mini-ramki w ostatniej pozycji.

```
virtual void OnDockToRecentPos();
```

## <a name="cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder

Rysuje obramowania okna mini-ramki.

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia używany do rysowania obramowania.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez strukturę, aby narysować obramowania okna mini-ramki.

## <a name="cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer

Zatrzymuje czasomierz zestawienia.

```
virtual void OnKillRollUpTimer();
```

## <a name="cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFrameWnd::OnMovePane

Przenosi okno mini-ramki o określone przesunięcie.

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w] Wskaźnik do okienka (ignorowane).

*ptOffset (polski)*<br/>
[w] Przesunięcie, o które ma być przesunięte okienko.

## <a name="cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout

Dostosowuje układ okienka wewnątrz okna mini-ramki.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy musi dostosować układ okienka wewnątrz okna mini-ramki.

Domyślnie okienko jest umieszczone w celu pokrycia pełnego obszaru klienta okna mini-ramki.

## <a name="cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer

Ustawia czasomierz zestawienia.

```
virtual void OnSetRollUpTimer();
```

## <a name="cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFrameWnd::OnShowPane

Wywoływane przez strukturę, gdy okienko w oknie mini-ramki jest ukryte lub wyświetlane.

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[w] Okienko, które jest wyświetlane lub ukryte.

*bPokaż*<br/>
[w] PRAWDA, jeśli okienko jest wyświetlane; FAŁSZ, jeśli okienko jest ukryte.

### <a name="remarks"></a>Uwagi

Wywoływana przez strukturę, gdy okienko w oknie mini-ramki jest wyświetlane lub ukryte. Domyślna implementacja nic nie robi.

## <a name="cpaneframewndpin"></a><a name="pin"></a>CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parametry

[w] *bPin (sie.*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint

Zwraca okienko, jeśli zawiera ono punkt dostarczony przez użytkownika wewnątrz okna miniklatki.

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parametry

*Punkt*<br/>
[w] Punkt, który użytkownik kliknął we współrzędnych ekranu.

*nWrażliwość*<br/>
[w] Ten parametr nie jest używany.

*bCzycielność*<br/>
[w] TRUE, aby określić, że powinny być zwracane tylko widoczne okienka; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Okienko, które użytkownik kliknął lub NULL, jeśli w tej lokalizacji nie ma okienka.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby uzyskać okienko, które zawiera dany punkt.

## <a name="cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFrameWnd::RedrawAll

Przerysowuje wszystkie okna mini-frame.

```
static void RedrawAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda aktualizuje wszystkie okna mini-ramki, wywołując [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) dla każdego okna.

## <a name="cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFrameWnd::Usuń NienavalidPanes

Wywoływane przez platformę, aby usunąć nieważne okienka.

```
virtual void RemoveNonValidPanes();
```

## <a name="cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFrameWnd::Usuńpan

Usuwa okienko z okna mini-ramki.

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Wskaźnik do okienka do usunięcia.

*bDestroj*<br/>
[w] Określa, co dzieje się z oknem miniklatki. Jeśli *bDestroy* jest TRUE, ta metoda natychmiast niszczy okno mini-ramki. Jeśli jest false, ta metoda niszczy okno mini-ramki po pewnym opóźnieniu.

*bNoDelayedDestroy*<br/>
[w] Jeśli true, opóźnione zniszczenie jest wyłączone. Jeśli FALSE, opóźnione zniszczenie jest włączone.

### <a name="remarks"></a>Uwagi

Struktura może zniszczyć okna mini-ramki natychmiast lub po pewnym opóźnieniu. Jeśli chcesz opóźnić zniszczenie okien mini-ramki, przekaż FAŁJ w parametrze *bNoDelayedDestroy.* Opóźnione zniszczenie występuje, gdy struktura przetwarza komunikat AFX_WM_CHECKEMPTYMINIFRAME.

## <a name="cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFrameWnd::ReplacePane

Zastępuje jedno okienko innym.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parametry

*pBarOrg (pBarOrg)*<br/>
[w] Wskaźnik do oryginalnego okienka.

*pBarReplaceWith*<br/>
[w] Wskaźnik do okienka, które zastępuje oryginalne okienko.

## <a name="cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFrameWnd::Zapisz stan

Zapisuje stan okienka w rejestrze.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parametry

*lpszProfileName*<br/>
[w] Nazwa profilu.

*Uiid*<br/>
[w] Identyfikator okienka.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli stan okienka został pomyślnie zapisany; w przeciwnym razie FALSE.

## <a name="cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFrameWnd::Przyciskiskładów

Ustawia przyciski podpisów.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parametry

*dwButtons*<br/>
[w] Połączenie bitowe-OR następujących wartości:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

## <a name="cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parametry

[w] *bDelayPokaj*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parametry

[w] *pManager*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer

Ustawia czasomierz dokowania.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parametry

*nCzasout*<br/>
[w] Wartość limitu czasu w milisekundach.

## <a name="cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFrameWnd::SetDockState

Ustawia stan dokowania.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parametry

*pDockManager*<br/>
[w] Wskaźnik do menedżera dokowania.

## <a name="cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parametry

[w] *ptNowy*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState

Wywoływana przez ramy, aby ustawić stan predocking.

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parametry

*stan preDock*<br/>
[w] Możliwe wartości:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock (właskw.*<br/>
[w] Wskaźnik do okienka do stacji dokowania.

*dokMetoda*<br/>
[w] Metoda dokowania. (Ten parametr jest ignorowany).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno mini-ramki jest oddokowane; FAŁSZ, jeśli jest zadokowany.

## <a name="cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent

Dostosowuje rozmiar okna mini-ramki tak, aby odpowiadał okienku zawartej.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby dostosować rozmiar okna mini-ramki do rozmiaru okienka zawarte.

## <a name="cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFrameWnd::StartTearOff

Odrywa menu.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[w] Wskaźnik do menu.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

## <a name="cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parametry

[w] *pBar*<br/>

### <a name="remarks"></a>Uwagi

## <a name="cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parametry

[w] *pDockingBar (kierownica)*<br/>
[w] *pTabbedBar (Bar)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
