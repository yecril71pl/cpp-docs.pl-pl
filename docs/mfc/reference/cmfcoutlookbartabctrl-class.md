---
title: Klasa CMFCOutlookBarTabCtrl
ms.date: 10/18/2018
f1_keywords:
- CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::AddControl
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::CanShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::Create
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableInPlaceEdit
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::EnableScrollButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::GetVisiblePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsAnimation
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::IsMode2003
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowFewerPageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowMorePageButtons
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::OnShowOptions
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetActiveTab
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetBorderSize
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetPageButtonTextAlign
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetToolbarImageList
- AFXOUTLOOKBARTABCTRL/CMFCOutlookBarTabCtrl::SetVisiblePageButtons
helpviewer_keywords:
- CMFCOutlookBarTabCtrl [MFC], AddControl
- CMFCOutlookBarTabCtrl [MFC], CanShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], CanShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], Create
- CMFCOutlookBarTabCtrl [MFC], EnableAnimation
- CMFCOutlookBarTabCtrl [MFC], EnableInPlaceEdit
- CMFCOutlookBarTabCtrl [MFC], EnableScrollButtons
- CMFCOutlookBarTabCtrl [MFC], GetBorderSize
- CMFCOutlookBarTabCtrl [MFC], GetVisiblePageButtons
- CMFCOutlookBarTabCtrl [MFC], IsAnimation
- CMFCOutlookBarTabCtrl [MFC], IsMode2003
- CMFCOutlookBarTabCtrl [MFC], OnShowFewerPageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowMorePageButtons
- CMFCOutlookBarTabCtrl [MFC], OnShowOptions
- CMFCOutlookBarTabCtrl [MFC], SetActiveTab
- CMFCOutlookBarTabCtrl [MFC], SetBorderSize
- CMFCOutlookBarTabCtrl [MFC], SetPageButtonTextAlign
- CMFCOutlookBarTabCtrl [MFC], SetToolbarImageList
- CMFCOutlookBarTabCtrl [MFC], SetVisiblePageButtons
ms.assetid: b1f2b3f7-cc59-49a3-99d8-7ff9b37c044b
ms.openlocfilehash: 309b74126f57e76aa6399f57382d88fee4400700
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369661"
---
# <a name="cmfcoutlookbartabctrl-class"></a>Klasa CMFCOutlookBarTabCtrl

Kontrolka karty, która ma wygląd **okienka nawigacji** w programie Microsoft Outlook.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

## <a name="syntax"></a>Składnia

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Domyślny konstruktor.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Dodaje kontrolkę systemu Windows jako nową kartę na pasku programu Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Wywoływane przez strukturę w celu określenia wymiarów pola edycji, które pojawia `CMFCBaseTabCtrl::CalcRectEdit`się, gdy użytkownik zmienia nazwę karty.|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Wywoływane przez strukturę podczas operacji zmiany rozmiaru, aby ustalić, czy można wyświetlić mniej przycisków strony paska programu Outlook, niż są obecnie widoczne.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Wywoływane przez strukturę podczas operacji zmiany rozmiaru, aby ustalić, czy więcej przycisków strony paska programu Outlook może być wyświetlanych, niż są obecnie widoczne.|
|[CMFCOutlookBarTabCtrl::Tworzenie](#create)|Tworzy kontrolkę karty pasek programu Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Określa, czy animacja występująca podczas przełączania między aktywnymi kartami jest włączona.|
|[CMFCOutlookBarTabCtrl::EnableInPlaCeEdit](#enableinplaceedit)|Określa, czy użytkownik może modyfikować etykiety tekstowe na przyciskach kart na pasku programu Outlook. (Zastępuje [CMFCBaseTabCtrl::EnableInPlaCeEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Wywoływane przez strukturę, aby włączyć przyciski, które umożliwiają użytkownikowi przewijanie przycisków w okienku paska programu Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identyfikuje okienko zawierające określony punkt. (Zastępuje [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania kontrolki karty Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Pobiera rozmiar i położenie obszaru karty formantu karty. (Zastępuje [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCOutlookBarTabCtrl::Przycisky Strony GetVisible](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Określa, czy animacja, która występuje podczas przełączania między aktywnymi kartami jest włączona.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Określa, czy kontrolka karty paska programu Outlook jest w trybie emulacji programu Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Określa, czy punkt znajduje się wewnątrz obszaru karty. (Zastępuje [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Określa, czy karta jest odłączany. (Zastępuje [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Wywoływana przez platformę, gdy karta jest wstawiana lub usuwana. (Przesłania `CMFCBaseTabCtrl::OnChangeTabs`).|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Wywoływane przez strukturę, aby zmniejszyć liczbę przycisków strony karty, które są widoczne.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Wywoływane przez strukturę, aby zwiększyć liczbę przycisków strony karty, które są widoczne.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Wyświetla okno dialogowe **Opcje okienka nawigacji.**|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Ponownie oblicza wewnętrzny układ kontrolki karty. (Zastępuje [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Ustawia aktywną kartę(Overrides [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Ustawia rozmiar obramowania kontrolki karty Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Ustawia wyrównanie etykiet tekstowych na przyciskach kart paska programu Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Ustawia mapę bitową zawierającą ikony wyświetlane na dole paska programu Outlook w trybie programu Outlook 2003 (zobacz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Uwagi

Aby utworzyć pasek programu Outlook z obsługą `CMFCOutlookBar` dokowania, użyj obiektu do hostowania kontrolki paska programu Outlook. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, `CMFCOutlookBarTabCtrl` jak zainicjować obiekt `CMFCOutlookBarTabCtrl` i użyć różnych metod w klasie. W przykładzie pokazano, jak włączyć edycję etykiety tekstowej w miejscu na przyciskach strony karty na pasku programu Outlook, włączyć animację, włączyć uchwyty przewijania, które umożliwiają użytkownikowi przewijanie przycisków w okienku paska programu Outlook, ustawić rozmiar obramowania kontrolki karty Outlook i ustawić wyrównanie etykiet tekstowych na przyciskach kart na pasku programu Outlook. Ten fragment kodu jest częścią [przykładu demo programu Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cmfcbasetabctrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[Cmfcoutlookbartabctrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoutlookbartabctrl.h

## <a name="cmfcoutlookbartabctrladdcontrol"></a><a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl

Dodaje kontrolkę systemu Windows jako nową kartę na pasku programu Outlook.

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parametry

*pWndCtrl (właśc.*<br/>
[w] Wskaźnik do formantu, aby dodać.

*Lpszname*<br/>
[w] Określa nazwę karty.

*bDetachable*<br/>
[w] Jeśli true, strona zostanie utworzona jako odłączalne.

*nImageID (obrazek)*<br/>
[w] Indeks obrazu na wewnętrznej liście obrazów dla obrazu, który ma być wyświetlany na nowej karcie.

*styl dwControlBarStyle*<br/>
[w] Określa styl AFX_ CBRS_* dla zawiniętych okienek dokowania.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do dodawania formantu jako nowej strony paska programu outlook.

Ta funkcja wewnętrznie wywołuje [cmfcbasetabctrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Jeśli ustawisz *bDetachable* na TRUE, `AddControl` wewnętrznie tworzy `CDockablePaneAdapter` obiekt i zawija dodany formant. Automatycznie ustawia klasę środowiska uruchomieniowego okna z kartami `CMFCOutlookBar` na klasę środowiska wykonawczego i `CMultiPaneFrameWnd`klasę środowiska wykonawczego ramki przestawnej na .

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `AddControl` metody w `CMFCOutlookBarTabCtrl` klasie. Ten fragment kodu jest częścią [przykładu demo programu Outlook](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

## <a name="cmfcoutlookbartabctrlcanshowfewerpagebuttons"></a><a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Wywoływane przez strukturę podczas operacji zmiany rozmiaru, aby ustalić, czy mniej przycisków strony karty paska programu Outlook mogą być wyświetlane niż są obecnie widoczne.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli istnieje więcej niż jeden przycisk; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Kontrolka karty paska programu Outlook dynamicznie dodaje lub usuwa karty z ekranu w zależności od ilości dostępnego miejsca. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.

## <a name="cmfcoutlookbartabctrlcanshowmorepagebuttons"></a><a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Wywoływane przez strukturę podczas operacji zmiany rozmiaru, aby ustalić, czy więcej przycisków strony paska programu Outlook może być wyświetlanych, niż są obecnie widoczne.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli istnieją przyciski, które nie są obecnie widoczne; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Kontrolka karty paska programu Outlook dynamicznie dodaje lub usuwa karty z ekranu, w zależności od ilości dostępnego miejsca. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.

## <a name="cmfcoutlookbartabctrlcreate"></a><a name="create"></a>CMFCOutlookBarTabCtrl::Tworzenie

Tworzy kontrolkę karty pasek programu Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[w] Określa początkowy rozmiar i położenie w pikselach.

*pParentWnd*<br/>
[w] Wskazuje okno nadrzędne. Nie może być null.

*Nid*<br/>
[w] Identyfikator sterowania.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli formant został utworzony pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zazwyczaj formanty karty paska programu Outlook są tworzone, gdy [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md) kontroluje WM_CREATE komunikat procesu.

## <a name="cmfcoutlookbartabctrlenableanimation"></a><a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation

Określa, czy animacja występująca podczas przełączania między aktywnymi kartami jest włączona.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Określa, czy animacja ma być włączona czy wyłączona.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby włączyć i wyłączyć animację. Gdy użytkownik otworzy stronę karty, podpis strony przesuwa się w górę lub w dół, jeśli animacja jest włączona. Jeśli animacja jest wyłączona, strona staje się natychmiast aktywna.

Domyślnie animacja jest włączona.

## <a name="cmfcoutlookbartabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaCeEdit

Określa, czy użytkownik może modyfikować etykiety tekstowe na przyciskach strony karty na pasku programu Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
Jeśli funkcja TRUE, włącz edycję w miejscu etykiety tekstowej. Jeśli fałsz, wyłącz edycję w miejscu.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby włączyć lub wyłączyć edycję w miejscu etykiet tekstowych na przyciskach strony karty. Domyślnie edycja w miejscu jest wyłączona.

## <a name="cmfcoutlookbartabctrlenablescrollbuttons"></a><a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons

Wywoływane przez strukturę, aby włączyć uchwyty przewijania, które umożliwiają użytkownikowi przewijanie przycisków w okienku paska programu Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Określa, czy przyciski przewijania mają być wyświetlane.

*bIsUp (Nie)*<br/>
[w] Określa, czy górny pasek przewijania jest wyświetlany.

*bIsDown (Dół)*<br/>
[w] Określa, czy dolny pasek przewijania jest wyświetlany.

### <a name="remarks"></a>Uwagi

Włącza wyświetlanie przycisków przewijania. Ta metoda jest wywoływana przez platformę, gdy aktywna karta zmienia się, aby przywrócić przyciski przewijania.

## <a name="cmfcoutlookbartabctrlgetbordersize"></a><a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize

Zwraca rozmiar obramowania kontrolki karty Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar obramowania w pikselach.

## <a name="cmfcoutlookbartabctrlgetvisiblepagebuttons"></a><a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::Przycisky Strony GetVisible

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcoutlookbartabctrlisanimation"></a><a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation

Określa, czy animacja występująca podczas przełączania między aktywnymi kartami jest włączona.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli animacja jest włączona; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie [funkcji CMFCOutlookBarTabCtrl::EnableAnimation,](#enableanimation) aby włączyć lub wyłączyć animację.

## <a name="cmfcoutlookbartabctrlismode2003"></a><a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003

Określa, czy kontrolka karty paska programu Outlook jest w trybie emulacji programu Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli kontrolka karty paska programu Outlook jest w trybie programu Outlook 2003; w przeciwnym razie FALSE;

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana przez [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

## <a name="cmfcoutlookbartabctrlonshowfewerpagebuttons"></a><a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Wywoływane przez strukturę, aby zmniejszyć liczbę przycisków strony karty, które są widoczne.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Uwagi

Ta metoda dostosowuje liczbę widocznych przycisków kart strony po przesiąknięciu jej.

## <a name="cmfcoutlookbartabctrlonshowmorepagebuttons"></a><a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Wywoływane przez strukturę, aby zwiększyć liczbę przycisków strony karty, które są widoczne.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Uwagi

Ta metoda dostosuj liczbę przycisków strony karty, które są widoczne po przesaniu formantu.

## <a name="cmfcoutlookbartabctrlonshowoptions"></a><a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions

Wyświetla okno dialogowe **Opcje okienka nawigacji.**

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Uwagi

Okno dialogowe **Opcje okienka nawigacji** umożliwia użytkownikowi wybranie przycisków strony karty oraz kolejność ich wyświetlania.

Ta metoda jest wywoływana przez platformę, gdy użytkownik **wybierze** element menu Opcje okienka nawigacji z menu dostosowywania formantu.

## <a name="cmfcoutlookbartabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab

Ustawia aktywną kartę. Aktywna karta jest tą, która jest otwarta, z widoczną zawartością.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parametry

*Itab*<br/>
[w] Indeks od zera karty do otwarcia.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określona karta została pomyślnie otwarta; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Efekt wizualny ustawienia aktywnej karty zależy od tego, czy włączono animację. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

## <a name="cmfcoutlookbartabctrlsetbordersize"></a><a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize

Ustawia rozmiar obramowania kontrolki karty Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parametry

*nBorderSize (Rozmiar)*<br/>
[w] Określa nowy rozmiar obramowania w pikselach.

### <a name="remarks"></a>Uwagi

Ustawia nowy rozmiar obramowania i ponownie oblicza układ okna programu Outlook.

## <a name="cmfcoutlookbartabctrlsetpagebuttontextalign"></a><a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Ustawia wyrównanie etykiet tekstowych na przyciskach kart paska programu Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*uiAlign*<br/>
[w] Określa wyrównanie tekstu.

*bRedraw*<br/>
[w] Jeśli true, okno programu Outlook zostanie ponownie narysowane.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do zmiany wyrównania tekstu dla przycisków strony.

*uiAlign* może być jedną z następujących wartości:

|Stały|Znaczenie|
|--------------|-------------|
|TA_LEFT|Wyrównanie w lewo|
|TA_CENTER|Wyrównanie do środka|
|TA_RIGHT|Wyrównanie w prawo|

Wartość domyślna jest TA_CENTER.

## <a name="cmfcoutlookbartabctrlsettoolbarimagelist"></a><a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList

Ustawia mapę bitową zawierającą ikony wyświetlane u dołu paska programu Outlook w trybie programu Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Określa identyfikator zasobu obrazu do załadowania.

*Cx*<br/>
[w] Określa szerokość obrazu na liście obrazów w pikselach.

*clrTransp (tłumaczenie kl./s)*<br/>
[w] Wartość RGB określająca kolor przezroczysty.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli zakończy się pomyślnie; w przeciwnym razie zwraca WARTOŚĆ FAŁSZ.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do dołączania listy obrazów, których obrazy będą wyświetlane na przyciskach paska narzędzi w trybie pakietu Microsoft Office 2003. Indeksy obrazów powinny odpowiadać indeksom stron.

Ta metoda nie powinna być wywoływana, jeśli nie w trybie pakietu Microsoft Office 2003. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="cmfcoutlookbartabctrlsetvisiblepagebuttons"></a><a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parametry

[w] *nVisiblePageButtons (Przyciski strony widoczne)*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
