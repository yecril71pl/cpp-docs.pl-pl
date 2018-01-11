---
title: Klasa CMFCOutlookBarTabCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d38cfd03c9d4fe192b8c1ee7e235140dba382ddb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcoutlookbartabctrl-class"></a>Klasa CMFCOutlookBarTabCtrl
Formant karty, który ma wygląd **okienka nawigacji** w programie Microsoft Outlook.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
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
|[CMFCOutlookBarTabCtrl::AddControl](#addcontrol)|Dodaje nową kartę w pasku Outlook kontrolki systemu Windows.|  
|`CMFCOutlookBarTabCtrl::CalcRectEdit`|Wywoływane przez platformę, aby określić wymiary pola edycji, który jest wyświetlany, gdy użytkownik zmienia nazwę karty. (Przesłania `CMFCBaseTabCtrl::CalcRectEdit`.)|  
|[CMFCOutlookBarTabCtrl::CanShowFewerPageButtons](#canshowfewerpagebuttons)|Wywoływane przez platformę podczas operacji zmiany rozmiaru w celu określenia, czy można wyświetlić mniej przycisków strony karty pasek Outlook nie są widoczne.|  
|[CMFCOutlookBarTabCtrl::CanShowMorePageButtons](#canshowmorepagebuttons)|Wywoływane przez platformę podczas operacji zmiany rozmiaru w celu określenia, czy można wyświetlić więcej przycisków strony karty pasek Outlook nie są widoczne.|  
|[CMFCOutlookBarTabCtrl::Create](#create)|Tworzy kontrolkę kartę paska programu Outlook.|  
|`CMFCOutlookBarTabCtrl::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation)|Określa, czy włączono animacji, która występuje podczas przełącznika między kartami active.|  
|[CMFCOutlookBarTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Określa, czy użytkownik może modyfikować etykiety tekst na przyciskach kartę paska Outlook. (Przesłania [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|  
|[CMFCOutlookBarTabCtrl::EnableScrollButtons](#enablescrollbuttons)|Wywoływane przez platformę, by włączyć przyciski, który umożliwia użytkownikowi do przycisków w okienku paska przewijania.|  
|`CMFCOutlookBarTabCtrl::FindTargetWnd`|Identyfikuje okienka zawierającego określony punkt. (Przesłania [CMFCBaseTabCtrl::FindTargetWnd](../../mfc/reference/cmfcbasetabctrl-class.md#findtargetwnd).)|  
|[CMFCOutlookBarTabCtrl::GetBorderSize](#getbordersize)|Zwraca rozmiar obramowania formantu programu Outlook.|  
|`CMFCOutlookBarTabCtrl::GetTabArea`|Pobiera rozmiar i położenie wartości obszar karty formantu karty. (Przesłania [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|  
|`CMFCOutlookBarTabCtrl::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCOutlookBarTabCtrl::GetVisiblePageButtons](#getvisiblepagebuttons)||  
|[CMFCOutlookBarTabCtrl::IsAnimation](#isanimation)|Określa, czy włączono animacji, która występuje podczas przełącznika między kartami active.|  
|[CMFCOutlookBarTabCtrl::IsMode2003](#ismode2003)|Określa, czy formant karty pasek Outlook jest w trybie, która emuluje Microsoft Outlook 2003.|  
|`CMFCOutlookBarTabCtrl::IsPtInTabArea`|Określa, czy punkt znajduje się wewnątrz obszaru karty. (Przesłania [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|  
|`CMFCOutlookBarTabCtrl::IsTabDetachable`|Określa, czy karta jest odłączane. (Przesłania [CMFCBaseTabCtrl::IsTabDetachable](../../mfc/reference/cmfcbasetabctrl-class.md#istabdetachable).)|  
|`CMFCOutlookBarTabCtrl::OnChangeTabs`|Wywoływane przez platformę, gdy karta zostanie wstawiony lub usunięty. (Przesłania `CMFCBaseTabCtrl::OnChangeTabs`.)|  
|[CMFCOutlookBarTabCtrl::OnShowFewerPageButtons](#onshowfewerpagebuttons)|Wywoływane przez platformę, aby zmniejszyć liczbę przycisków strony karty, które są widoczne.|  
|[CMFCOutlookBarTabCtrl::OnShowMorePageButtons](#onshowmorepagebuttons)|Wywoływane przez platformę, aby zwiększyć liczbę przycisków strony karty, które są widoczne.|  
|[CMFCOutlookBarTabCtrl::OnShowOptions](#onshowoptions)|Wyświetla **opcje okienka nawigacji** okna dialogowego.|  
|`CMFCOutlookBarTabCtrl::RecalcLayout`|Ponownie oblicza układ wewnętrzny formantu karty. (Przesłania [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|  
|[CMFCOutlookBarTabCtrl::SetActiveTab](#setactivetab)|Ustawia aktywnej karty. (Przesłania [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|  
|[CMFCOutlookBarTabCtrl::SetBorderSize](#setbordersize)|Określa rozmiar obramowania formantu karty programu Outlook.|  
|[CMFCOutlookBarTabCtrl::SetPageButtonTextAlign](#setpagebuttontextalign)|Określa wyrównanie etykiety na karcie przycisków paska Outlook.|  
|[CMFCOutlookBarTabCtrl::SetToolbarImageList](#settoolbarimagelist)|Ustawia mapy bitowej zawierającego ikony, które są wyświetlane w dolnej części paska Outlook w trybie Outlook 2003 (zobacz [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md)).|  
|[CMFCOutlookBarTabCtrl::SetVisiblePageButtons](#setvisiblepagebuttons)||  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć paska Outlook, który obsługuje dokowania, użyj `CMFCOutlookBar` obiektu do obsługi w programie Outlook superpaska formantu karty. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zainicjować `CMFCOutlookBarTabCtrl` obiektu i korzystać z różnych metod w `CMFCOutlookBarTabCtrl` klasy. W przykładzie pokazano, jak włączyć edycji w miejscu tekst etykiety na karcie strony przycisków paska Outlook, Włącz animacji, Włącz dojścia przewijania, które umożliwiają użytkownikowi przycisków w okienku paska przewijania, rozmiar obramowania Pobi kartę programu Outlook Formant Karta i ustaw wyrównanie etykiety tekst na przyciskach kartę paska Outlook. Następujący fragment kodu jest częścią [próbka Outlook Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_1.cpp)]  
[!code-cpp[NVC_MFC_OutlookDemo#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxoutlookbartabctrl.h  
  
##  <a name="addcontrol"></a>CMFCOutlookBarTabCtrl::AddControl  
 Dodaje nową kartę w pasku Outlook kontrolki systemu Windows.  
  
```  
void AddControl(
    CWnd* pWndCtrl,  
    LPCTSTR lpszName,  
    int nImageID=-1,  
    BOOL bDetachable=TRUE,  
    DWORD dwControlBarStyle=AFX_CBRS_FLOAT |  AFX_CBRS_CLOSE | AFX_CBRS_RESIZE |  CBRS_AFX_AUTOHIDE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndCtrl`  
 Wskaźnik do formantu do dodania.  
  
 [in]`lpszName`  
 Określa nazwę karty.  
  
 [in]`bDetachable`  
 Jeśli `TRUE`, strona zostanie utworzona jako odłączane.  
  
 [in]`nImageID`  
 Indeks obrazu na liście wewnętrznych obrazu dla obrazu do wyświetlenia na nowej karcie.  
  
 [in]`dwControlBarStyle`  
 Określa AFX_ `CBRS_`* styl opakowana okienka dokowania.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby dodać kontrolkę jako nową stronę paska programu outlook.  
  
 Ta funkcja wymaga wewnętrznie w sprawie [CMFCBaseTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab).  
  
 Jeśli ustawisz `bDetachable` do `TRUE`, `AddControl` wewnętrznie tworzy `CDockablePaneAdapter` obiektu i opakowuje dodano formantu. Automatycznie ustawia klasa środowiska uruchomieniowego okna z kartami na klasę środowiska uruchomieniowego `CMFCOutlookBar` i klasa czasu wykonywania ramki przestawne `CMultiPaneFrameWnd`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `AddControl` metoda `CMFCOutlookBarTabCtrl` klasy. Następujący fragment kodu jest częścią [próbka Outlook Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbartabctrl-class_3.cpp)]  
  
##  <a name="canshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowFewerPageButtons  
 Wywoływane przez platformę podczas operacji w celu ustalenia, czy można wyświetlić mniej przycisków strony karty pasek Outlook nie są widoczne zmiany rozmiaru.  
  
```  
virtual BOOL CanShowFewerPageButtons() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli istnieje więcej niż jeden przycisk; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Formantu paska Outlook dynamicznie dodaje lub usuwa karty z ekranu w zależności od tego, ile miejsca jest dostępne. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.  
  
##  <a name="canshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::CanShowMorePageButtons  
 Wywoływane przez platformę podczas operacji w celu ustalenia, czy można wyświetlić więcej przycisków strony karty pasek Outlook nie są widoczne zmiany rozmiaru.  
  
```  
virtual BOOL CanShowMorePageButtons() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku przycisków, które nie są widoczne; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Formant karty pasek Outlook dynamicznie dodaje lub usuwa karty z ekranu, w zależności od tego, ile miejsca jest dostępne. Ta metoda jest używana przez platformę, aby pomóc w tym procesie.  
  
##  <a name="create"></a>CMFCOutlookBarTabCtrl::Create  
 Tworzy kontrolkę kartę paska programu Outlook.  
  
```  
virtual BOOL Create(
    const CRect& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`rect`  
 Określa początkowy rozmiar i położenie w pikselach.  
  
 [in]`pParentWnd`  
 Wskazuje okno nadrzędne. Nie może być `NULL`.  
  
 [in]`nID`  
 Identyfikator formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli formant został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zazwyczaj formanty kartę paska programu outlook są tworzone, gdy [klasy CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md) formanty `WM_CREATE` komunikat procesu.  
  
##  <a name="enableanimation"></a>CMFCOutlookBarTabCtrl::EnableAnimation  
 Określa, czy włączono animacji, która występuje podczas przełącznika między kartami active.  
  
```  
static void EnableAnimation(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Określa, czy animacja powinna być włączona lub wyłączona.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby włączyć lub wyłączyć animacji. Po otwarciu strony karty podpisu strony slajdów w górę lub w dół, jeśli animacji jest włączone. Jeśli animacji jest wyłączone, strona staje się aktywne natychmiast.  
  
 Domyślnie program animacji jest włączone.  
  
##  <a name="enableinplaceedit"></a>CMFCOutlookBarTabCtrl::EnableInPlaceEdit  
 Określa, czy użytkownik może modyfikować etykiet tekstowych na karcie strony przycisków paska Outlook.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parametry  
 `bEnable`  
 Jeśli `TRUE`, Włącz edycji w miejscu tekst etykiety. Jeśli `FALSE`, wyłącz edycji w miejscu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby włączyć lub wyłączyć edycji w miejscu etykiet tekst na przyciskach strony karty. Domyślnie edycji w miejscu jest wyłączona.  
  
##  <a name="enablescrollbuttons"></a>CMFCOutlookBarTabCtrl::EnableScrollButtons  
 Wywoływane przez platformę, by włączyć uchwytów przewijania, które umożliwiają użytkownikom przycisków w okienku paska przewijania.  
  
```  
void EnableScrollButtons(
    BOOL bEnable = TRUE,  
    BOOL bIsUp = TRUE,  
    BOOL bIsDown = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 Określa, czy są wyświetlane przyciski przewijania.  
  
 [in]`bIsUp`  
 Określa, czy jest wyświetlany górny pasek przewijania.  
  
 [in]`bIsDown`  
 Określa, czy jest wyświetlany pasek przewijania dolnej.  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia wyświetlanie przyciski przewijania. Ta metoda jest wywoływana przez platformę po zmianie aktywnego kartę do przywrócenia przyciski przewijania.  
  
##  <a name="getbordersize"></a>CMFCOutlookBarTabCtrl::GetBorderSize  
 Zwraca rozmiar obramowania formantu programu Outlook.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar obramowania w pikselach.  
  
##  <a name="getvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::GetVisiblePageButtons  

  
```  
int GetVisiblePageButtons() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isanimation"></a>CMFCOutlookBarTabCtrl::IsAnimation  
 Określa, czy włączono animacji, która występuje podczas przełącznika między kartami active.  
  
```  
static BOOL IsAnimation();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli jest włączona Animacja; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation) funkcji, aby włączyć lub wyłączyć animacji.  
  
##  <a name="ismode2003"></a>CMFCOutlookBarTabCtrl::IsMode2003  
 Określa, czy formant karty pasek Outlook jest w trybie, która emuluje Microsoft Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli paska formantu karty Outlook jest w trybie Outlook 2003; w przeciwnym razie `FALSE`;  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość jest ustawiana przez [CMFCOutlookBar::SetMode2003](../../mfc/reference/cmfcoutlookbar-class.md#setmode2003).  
  
##  <a name="onshowfewerpagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowFewerPageButtons  
 Wywoływane przez platformę, aby zmniejszyć liczbę przycisków strony karty, które są widoczne.  
  
```  
virtual void OnShowFewerPageButtons();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda dostosowuje liczbę przycisków karty strony widoczny, gdy zmieniany jest rozmiar formantu.  
  
##  <a name="onshowmorepagebuttons"></a>CMFCOutlookBarTabCtrl::OnShowMorePageButtons  
 Wywoływane przez platformę, aby zwiększyć liczbę przycisków strony karty, które są widoczne.  
  
```  
virtual void OnShowMorePageButtons();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda Dostosuj liczbę przycisków strony karty, które są widoczne, gdy zmieniany jest rozmiar formantu.  
  
##  <a name="onshowoptions"></a>CMFCOutlookBarTabCtrl::OnShowOptions  
 Wyświetla **opcje okienka nawigacji** okno dialogowe.  
  
```  
virtual void OnShowOptions();
```  
  
### <a name="remarks"></a>Uwagi  
 **Opcje okienka nawigacji** okno dialogowe umożliwia użytkownikowi wybranie przycisków strony karty mają być wyświetlane i kolejność, w którym są wyświetlane.  
  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik wybierze **opcje okienka nawigacji** element menu z menu Dostosowywanie formantu.  
  
##  <a name="setactivetab"></a>CMFCOutlookBarTabCtrl::SetActiveTab  
 Ustawia aktywnej karty. Karta active jest ten, który jest otwarty, wraz z zawartością widoczne.  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iTab`  
 Liczony od zera indeks kartę, aby go otworzyć.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli określony karta została otwarta pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Efekt ustawienia na karcie active zależy od tego, czy włączono animacji. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBarTabCtrl::EnableAnimation](#enableanimation).  
  
##  <a name="setbordersize"></a>CMFCOutlookBarTabCtrl::SetBorderSize  
 Określa rozmiar obramowania formantu karty programu Outlook.  
  
```  
void SetBorderSize(int nBorderSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nBorderSize`  
 Określa nowy rozmiar obramowania w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia nowy rozmiar obramowania i ponownie oblicza układ okna programu outlook.  
  
##  <a name="setpagebuttontextalign"></a>CMFCOutlookBarTabCtrl::SetPageButtonTextAlign  
 Określa wyrównanie etykiety na karcie przycisków paska Outlook.  
  
```  
void SetPageButtonTextAlign(
    UINT uiAlign,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiAlign`  
 Określa wyrównanie tekstu.  
  
 [in]`bRedraw`  
 Jeśli `TRUE`, zostanie narysowany ponownie okno programu outlook.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do zmiany wyrównania tekstu dla strony przycisków.  
  
 `uiAlign`może to być jedna z następujących wartości:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|TA_LEFT|Wyrównanie do lewej|  
|TA_CENTER|Wyśrodkuj|  
|TA_RIGHT|Wyrównanie do prawej|  
  
 Wartość domyślna to TA_CENTER.  
  
##  <a name="settoolbarimagelist"></a>CMFCOutlookBarTabCtrl::SetToolbarImageList  
 Ustawia mapy bitowej zawierającego ikony, które są wyświetlane w dolnej części paska Outlook w trybie 2003 programu Outlook.  
  
```  
BOOL SetToolbarImageList(
    UINT uiID,  
    int cx,  
    COLORREF clrTransp=RGB(255, 0, 255));
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiID`  
 Określa identyfikator zasobu obrazu do załadowania.  
  
 [in]`cx`  
 Określa szerokość obrazu na liście obrazu w pikselach.  
  
 [in]`clrTransp`  
 Wartości RGB, która określa kolor przezroczysty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` w przypadku powodzenia; w przeciwnym razie zwraca `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do dołączenia do listy obrazów, w których obrazy zostaną wyświetlone na przycisków paska narzędzi w trybie Microsoft Office 2003. Indeksy obrazu powinna odpowiadać indeksów strony.  
  
 Nie można wywoływać tej metody nie w trybie Microsoft Office 2003. Aby uzyskać więcej informacji, zobacz [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md).  
  
##  <a name="setvisiblepagebuttons"></a>CMFCOutlookBarTabCtrl::SetVisiblePageButtons  

  
```  
void SetVisiblePageButtons(int nVisiblePageButtons);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nVisiblePageButtons`  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Klasa CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)
