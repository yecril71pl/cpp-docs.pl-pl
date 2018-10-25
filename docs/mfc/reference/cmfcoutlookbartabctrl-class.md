---
title: Klasa CMFCOutlookBarTabCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 19550315f17982e019d1ba6f495dedee6d2f346d
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081017"
---
# <a name="cmfcoutlookbartabctrl-class"></a>Klasa CMFCOutlookBarTabCtrl

Formant karty, która ma wygląd **okienka nawigacji** w programie Microsoft Outlook.
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.
## <a name="syntax"></a>Składnia

```
class CMFCOutlookBarTabCtrl : public CMFCBaseTabCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCOutlookBarTabCtrl::CMFCOutlookBarTabCtrl`|Domyślny konstruktor.|
|`CMFCOutlookBarTabCtrl::~CMFCOutlookBarTabCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Dodaje formant Windows na nowej karcie w pasek programu Outlook.|
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Wywoływane przez platformę, aby określić wymiary pola edycji, który jest wyświetlany, gdy użytkownik zmienia nazwę karty. (Przesłania `CMFCBaseTabCtrl::CalcRectEdit`).|
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Wywoływane przez platformę podczas operacji zmiany rozmiaru w celu określenia, czy mogą być wyświetlane mniej przycisków strony karty pasek programu Outlook, nie są obecnie widoczne.|
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Wywoływane przez platformę podczas operacji zmiany rozmiaru w celu określenia, czy więcej przycisków strony karty pasek programu Outlook mogą być wyświetlane, nie są obecnie widoczne.|
|[CMFCOutlookBarTabCtrl::Create](#create)|Tworzy formant karty pasek programu Outlook.|
|`CMFCOutlookBarTabCtrl::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Określa, czy włączono animacji, który występuje podczas przełączania między kartami active.|
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Określa, czy użytkownik może modyfikować etykiety tekstowe na karcie przycisków paska Outlook. (Przesłania [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Metoda wywoływana przez platformę, by włączyć przycisków, które umożliwiają użytkownikom przechodzenie między przyciskami na okienko paska Outlook.|
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identyfikuje okienko, które zawiera określony punkt. (Przesłania [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania formantu karty programu Outlook.|
|`CMFCOutlookBarTabCtrl::GetTabArea`|Pobiera rozmiar i położenie wartości obszar karty formantu karty. (Przesłania [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|
|`CMFCOutlookBarTabCtrl::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Określa, czy włączono animacji, który występuje podczas przełączania między kartami active.|
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Określa, czy karta kontrolki paska w trybie, który symuluje programu Microsoft Outlook 2003.|
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Określa, czy punkt znajduje się wewnątrz obszaru karty. (Przesłania [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Określa, czy karta jest odłączane. (Przesłania [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Wywoływane przez platformę, gdy karta jest wstawiany lub usunięte. (Przesłania `CMFCBaseTabCtrl::OnChangeTabs`).|
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Metoda wywoływana przez platformę, aby zmniejszyć liczbę przycisków strony karty, które będą widoczne.|
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Metoda wywoływana przez platformę, aby zwiększyć liczbę przycisków strony karty, które będą widoczne.|
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Wyświetla **Opcje panelu nawigacji** okna dialogowego.|
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Ponownie oblicza układ wewnętrznej kontrolki karty. (Przesłania [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Ustawia aktywną kartę. (Przesłania [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Ustawia rozmiar obramowania formantu karty programu Outlook.|
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Ustawia wyrównanie etykiety tekstowe na karcie przycisków paska Outlook.|
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Ustawia mapy bitowej, który zawiera ikony, które są wyświetlane w dolnej części paska Outlook w trybie Outlook 2003 (zobacz [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)).|
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||

## <a name="remarks"></a>Uwagi

Aby utworzyć pasek programu Outlook, zapewniający obsługę dokującej, użyj `CMFCOutlookBar` obiektu do hostowania programu Outlook paska formant karty. Aby uzyskać więcej informacji, zobacz [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zainicjować `CMFCOutlookBarTabCtrl` obiektu i korzystać z różnych metod w `CMFCOutlookBarTabCtrl` klasy. W przykładzie przedstawiono sposób umożliwić edycję w miejscu etykietę tekst na przyciskach kartę strony paska Outlook, włączyć animacji, Włącz uchwyty przewijania, umożliwiające użytkownikom przechodzenie między przyciskami na okienko paska Outlook, rozmiar obramowania CD kartę programu Outlook roli i ustaw wyrównanie etykiety tekstowe na karcie przycisków paska Outlook. Ten fragment kodu jest częścią [próbka Outlook Demo](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)

[CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoutlookbartabctrl.h

##  <a name="addcontrol"></a>  CMFCOutlookBarTabCtrl::AddControl

Dodaje formant Windows na nowej karcie w pasek programu Outlook.

```
void AddControl(
    CWnd* pWndCtrl,
    LPCTSTR lpszName,
    int nImageID=-1,
    BOOL bDetachable=TRUE,
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
[in] Wskaźnik do kontrolki do dodania.

*lpszName*<br/>
[in] Określa nazwę karty.

*bDetachable*<br/>
[in] W przypadku opcji TRUE strony zostanie utworzony jako odłączane.

*nImageID*<br/>
[in] Indeks obrazu z listy obrazów wewnętrznego dla obrazu, które mają być wyświetlane w nowej karcie.

*dwControlBarStyle*<br/>
[in] Określa styl AFX_ CBRS_ * dla opakowana tafli dokowania.

### <a name="remarks"></a>Uwagi

Aby dodać kontrolkę jako nową stronę paska outlook, należy użyć tej funkcji.

Ta funkcja wywołuje wewnętrznie na [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).

Jeśli ustawisz *bDetachable* na wartość TRUE, `AddControl` wewnętrznie tworzy `CDockablePaneAdapter` obiektu i otacza dodanej kontrolki. Automatycznie ustawia klasy środowiska uruchomieniowego okna z kartami klasy środowiska uruchomieniowego `CMFCOutlookBar` i klasy środowiska uruchomieniowego zmiennoprzecinkowy ramki `CMultiPaneFrameWnd`.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `AddControl` method in Class metoda `CMFCOutlookBarTabCtrl` klasy. Ten fragment kodu jest częścią [próbka Outlook Demo](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]

##  <a name="canshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowFewerPageButtons

Wywoływane przez platformę podczas zmiany rozmiaru operacji, aby określić, czy mniej przycisków strony karty pasek programu Outlook mogą być wyświetlane, nie są obecnie widoczne.

```
virtual BOOL CanShowFewerPageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli istnieje więcej niż jeden przycisk. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Kontrolka karty paska Outlook dynamicznie dodaje lub usuwa tabulatory z widoku w zależności od tego, ile miejsca jest dostępna. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.

##  <a name="canshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::CanShowMorePageButtons

Wywoływane przez platformę podczas zmiany rozmiaru operacji, aby określić, czy więcej przycisków strony karty pasek programu Outlook mogą być wyświetlane, nie są obecnie widoczne.

```
virtual BOOL CanShowMorePageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli istnieją przycisków, które nie są obecnie widoczne; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Kontrolka karty paska Outlook dynamicznie dodaje lub usuwa tabulatory z ekranu, w zależności od tego, ile miejsca jest dostępna. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.

##  <a name="create"></a>  CMFCOutlookBarTabCtrl::Create

Tworzy formant karty pasek programu Outlook.

```
virtual BOOL Create(
    const CRect& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Określa początkowy rozmiar i położenie w pikselach.

*pParentWnd*<br/>
[in] Wskazuje okna nadrzędnego. Nie może mieć wartości NULL.

*nID*<br/>
[in] Identyfikator kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli kontrolka została utworzona pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zazwyczaj kontrolki karty pasek programu outlook są tworzone, gdy [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md) kontroluje komunikat WM_CREATE procesu.

##  <a name="enableanimation"></a>  CMFCOutlookBarTabCtrl::EnableAnimation

Określa, czy włączono animacji, który występuje podczas przełączania między kartami active.

```
static void EnableAnimation(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Określa, czy animacja powinna być włączona lub wyłączona.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby włączyć lub wyłączyć animacji. Gdy użytkownik otworzy stronę karty, podpisu strony slajdy w górę lub w dół, jeśli animacji jest włączone. Jeśli animacji jest wyłączone, strona staje się aktywny od razu.

Domyślnie animacji jest włączone.

##  <a name="enableinplaceedit"></a>  CMFCOutlookBarTabCtrl::EnableInPlaceEdit

Określa, czy użytkownik może modyfikować etykiety tekst na przyciskach kartę strony paska Outlook.

```
virtual void EnableInPlaceEdit(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
W przypadku opcji TRUE Włącz edycję w miejscu etykietę tekstową. Jeśli ma wartość FAŁSZ, Wyłącz edycję w miejscu.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby włączyć lub wyłączyć edycji w miejscu etykiet tekst na przyciskach strony karty. Domyślnie edycji w miejscu jest wyłączone.

##  <a name="enablescrollbuttons"></a>  CMFCOutlookBarTabCtrl::EnableScrollButtons

Metoda wywoływana przez platformę, by włączyć uchwyty przewijania, które umożliwiają użytkownikom przechodzenie między przyciskami na okienko paska Outlook.

```
void EnableScrollButtons(
    BOOL bEnable = TRUE,
    BOOL bIsUp = TRUE,
    BOOL bIsDown = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Określa, czy przyciski przewijania są wyświetlane.

*bIsUp*<br/>
[in] Określa, czy górny pasek przewijania jest wyświetlany.

*bIsDown*<br/>
[in] Określa, czy pasek przewijania dołu jest wyświetlana.

### <a name="remarks"></a>Uwagi

Umożliwia wyświetlanie przyciski przewijania. Ta metoda jest wywoływana przez platformę, gdy aktywną kartę zmieni się na przywracania przyciski przewijania.

##  <a name="getbordersize"></a>  CMFCOutlookBarTabCtrl::GetBorderSize

Zwraca rozmiar obramowania formantu karty programu Outlook.

```
int GetBorderSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar obramowania w pikselach.

##  <a name="getvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::GetVisiblePageButtons

```
int GetVisiblePageButtons() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="isanimation"></a>  CMFCOutlookBarTabCtrl::IsAnimation

Określa, czy włączono animacji, który występuje podczas przełączania między kartami active.

```
static BOOL IsAnimation();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli animacji jest włączone; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) funkcję, aby włączyć lub wyłączyć animacji.

##  <a name="ismode2003"></a>  CMFCOutlookBarTabCtrl::IsMode2003

Określa, czy kontrolka karty paska Outlook jest w trybie, który symuluje programu Microsoft Outlook 2003.

```
BOOL IsMode2003() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli paska sterowania kartę Outlook jest w trybie Outlook 2003 w przeciwnym razie wartość FALSE;

### <a name="remarks"></a>Uwagi

Ta wartość jest ustawiana [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).

##  <a name="onshowfewerpagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowFewerPageButtons

Metoda wywoływana przez platformę, aby zmniejszyć liczbę przycisków strony karty, które będą widoczne.

```
virtual void OnShowFewerPageButtons();
```

### <a name="remarks"></a>Uwagi

Ta metoda dostosowuje liczbę przycisków karty widoczną stronę przy zmianie rozmiaru formantu.

##  <a name="onshowmorepagebuttons"></a>  CMFCOutlookBarTabCtrl::OnShowMorePageButtons

Metoda wywoływana przez platformę, aby zwiększyć liczbę przycisków strony karty, które będą widoczne.

```
virtual void OnShowMorePageButtons();
```

### <a name="remarks"></a>Uwagi

Ta metoda dostosować liczbę kartę strony przycisków, które są widoczne, gdy zmieni się rozmiar kontrolki.

##  <a name="onshowoptions"></a>  CMFCOutlookBarTabCtrl::OnShowOptions

Wyświetla **Opcje panelu nawigacji** okno dialogowe.

```
virtual void OnShowOptions();
```

### <a name="remarks"></a>Uwagi

**Opcje panelu nawigacji** okno dialogowe umożliwia użytkownikowi wybranie przycisków strony karty mają być wyświetlane i kolejność, w którym są wyświetlane.

Ta metoda jest wywoływana przez platformę, gdy użytkownik wybierze **Opcje panelu nawigacji** element menu z menu Dostosowywanie formantu.

##  <a name="setactivetab"></a>  CMFCOutlookBarTabCtrl::SetActiveTab

Ustawia aktywną kartę. Karty aktywne jest tą, która jest otwarta i udostępnia jej zawartości, które są widoczne.

```
virtual BOOL SetActiveTab(int iTab);
```

### <a name="parameters"></a>Parametry

*iTab*<br/>
[in] Liczony od zera indeks kartę, aby otworzyć.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli określony karta została otwarta pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Efekt wizualny ustawienia aktywnej karcie zależy od tego, czy włączono animacji. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).

##  <a name="setbordersize"></a>  CMFCOutlookBarTabCtrl::SetBorderSize

Ustawia rozmiar obramowania formantu karty programu Outlook.

```
void SetBorderSize(int nBorderSize);
```

### <a name="parameters"></a>Parametry

*nBorderSize*<br/>
[in] Określa nowy rozmiar obramowania w pikselach.

### <a name="remarks"></a>Uwagi

Określa nowy rozmiar obramowania i ponownie oblicza układ okna programu outlook.

##  <a name="setpagebuttontextalign"></a>  CMFCOutlookBarTabCtrl::SetPageButtonTextAlign

Ustawia wyrównanie etykiety tekstowe na karcie przycisków paska Outlook.

```
void SetPageButtonTextAlign(
    UINT uiAlign,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parametry

*uiAlign*<br/>
[in] Określa wyrównanie tekstu.

*bRedraw*<br/>
[in] W przypadku opcji TRUE okna programu outlook zostanie narysowany ponownie.

### <a name="remarks"></a>Uwagi

Aby zmienić wyrównanie tekstu dla strony przycisków, należy użyć tej funkcji.

*uiAlign* może być jedną z następujących wartości:

|Stała|Znaczenie|
|--------------|-------------|
|TA_LEFT|Wyrównanie do lewej|
|TA_CENTER|Wyrównanie do środka|
|TA_RIGHT|Wyrównanie do prawej|

Wartość domyślna to TA_CENTER.

##  <a name="settoolbarimagelist"></a>  CMFCOutlookBarTabCtrl::SetToolbarImageList

Ustawia mapy bitowej, który zawiera ikony, które są wyświetlane w dolnej części paska Outlook w trybie Outlook 2003.

```
BOOL SetToolbarImageList(
    UINT uiID,
    int cx,
    COLORREF clrTransp=RGB(255, 0, 255));
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[in] Określa identyfikator zasobu obrazu do załadowania.

*CX*<br/>
[in] Określa szerokość obrazu z listy obrazów w pikselach.

*clrTransp*<br/>
[in] Wartości RGB, który określa przezroczysty kolor.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli to się powiedzie; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do dołączania listy obrazów obrazy będą wyświetlane na przycisków paska narzędzi w trybie Microsoft Office 2003. Indeksy obraz powinien odpowiadać indeksy strony.

Ta metoda nie powinna być wywoływana w przypadku nie w trybie Microsoft Office 2003. Aby uzyskać więcej informacji, zobacz [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

##  <a name="setvisiblepagebuttons"></a>  CMFCOutlookBarTabCtrl::SetVisiblePageButtons

```
void SetVisiblePageButtons(int nVisiblePageButtons);
```

### <a name="parameters"></a>Parametry

[in] *nVisiblePageButtons*<br/>

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
