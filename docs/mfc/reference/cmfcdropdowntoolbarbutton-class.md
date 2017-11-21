---
title: Klasa CMFCDropDownToolbarButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs: C++
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1502f2bc315df705f7a135305388277c6d44918e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Klasa CMFCDropDownToolbarButton
Typ przycisku paska narzędzi, który zachowuje się jak zwykły przycisku po kliknięciu. Jednak powoduje otwarcie listy rozwijanej paska narzędzi ( [CMFCDropDownToolbar — klasa](../../mfc/reference/cmfcdropdowntoolbar-class.md) Jeśli użytkownik naciśnie i przechowuje przycisku paska narzędzi w dół.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Konstruuje `CMFCDropDownToolbarButton` obiektu.|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCDropDownToolbarButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otwiera pasek narzędzi listy rozwijanej.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopiuje tekst przycisku paska narzędzi do menu. (Przesłania [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Pobiera pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.|  
|`CMFCDropDownToolbarButton::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Określa, czy pasek narzędzi listy rozwijanej jest obecnie otwarty.|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Określa, czy przycisk mogą być wyświetlane z rozszerzonego obramowania. (Przesłania [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Wywoływane przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|Wywoływane przez platformę, by obsłużyć [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) wiadomości. (Przesłania `CMCToolBarButton::OnCancelMode`.)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy. (Przesłania [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Wywoływane przez platformę, obsługując narzędzi nadrzędnej `WM_HELPHITTEST` wiadomości. (Przesłania [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modyfikuje podana menu, gdy aplikacja wyświetla menu skrótów na pasku narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Odczytuje obiekt z archiwum i zapisuje go do archiwum. (Przesłania [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Ustawia domyślne polecenie używającej platformę, gdy użytkownik kliknie przycisk.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Określa czas, który użytkownik musi przytrzymując przycisk myszy w dół, zanim zostanie wyświetlony pasek narzędzi listy rozwijanej.|  
  
## <a name="remarks"></a>Uwagi  
 A `CMFCDropDownToolBarButton` różni się od zwykłej przycisk, w tym ma małą strzałkę w prawym dolnym rogu przycisku. Po użytkownik wybierze przycisk paska narzędzi z listy rozwijanej, platformę Wyświetla ikonę na pasku narzędzi najwyższego poziomu (przycisk z małą strzałkę w prawym dolnym rogu).  
  
 Aby uzyskać informacje dotyczące implementacji pasek narzędzi listy rozwijanej, zobacz [CMFCDropDownToolbar — klasa](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
 `CMFCDropDownToolBarButton` Obiektu mogą być eksportowane do [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu i wyświetlany jako przycisk menu z menu podręcznego.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom  
 Kopiuje właściwości inny przycisk paska narzędzi do bieżącego przycisku.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
 Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. `src`musi być typu `CMFCDropDownToolbarButton`.  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 Konstruuje `CMFCDropDownToolbarButton` obiektu.  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszName`  
 Domyślny tekst przycisku.  
  
 [in]`pToolBar`  
 Wskaźnik do `CMFCDropDownToolBar` obiekt, który jest wyświetlany, gdy użytkownik naciśnie przycisk.  
  
### <a name="remarks"></a>Uwagi  
 Drugi przeciążenia konstruktora kopiuje do przycisku rozwijanego przycisku pierwszej z paska narzędzi który `pToolBar` określa.  
  
 Zazwyczaj przycisku paska narzędzi z listy rozwijanej używa tekst przycisku ostatnio używane na pasku narzędzi który `pToolBar` określa. Kwerenda ta używa tekstowego określony przez `lpszName` gdy przycisk jest konwertowana na przycisk menu lub jest wyświetlany w **polecenia** karcie **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [CMFCToolBarsCustomizeDialog klasy](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCDropDownToolbarButton` klasy. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar  
 Otwiera pasek narzędzi listy rozwijanej.  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Okno nadrzędne ramki listy rozwijanej lub `NULL` na korzystanie z okna nadrzędnego przycisku paska narzędzi z listy rozwijanej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCDropDownToolbarButton::OnClick](#onclick) metoda wywołuje tę metodę, aby otworzyć pasek narzędzi listy rozwijanej, gdy użytkownik naciśnie i przechowuje przycisku paska narzędzi w dół.  
  
 Ta metoda tworzy pasek narzędzi listy rozwijanej przy użyciu [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) metody. Jeśli narzędzi nadrzędny jest zadokowany w pionie, ta metoda umieszcza pasek narzędzi listy rozwijanej do lewej lub prawej strony paska narzędzi nadrzędnego, w zależności od rozmiaru. W przeciwnym razie ta metoda umieszcza pasek narzędzi listy rozwijanej poniżej paska narzędzi nadrzędnej.  
  
 Ta metoda zakończy się niepowodzeniem, jeśli `pWnd` jest `NULL` i przycisku paska narzędzi listy rozwijanej nie ma okno nadrzędne.  
  
##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton  
 Kopiuje tekst przycisku paska narzędzi do menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`menuButton`  
 Odwołanie do docelowego przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli metoda zakończy się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje implementacji klasy podstawowej ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) i następnie dołącza do przycisku menu docelowego menu podręczne, które zawiera każdego elementu menu paska narzędzi w tym przycisku. Ta metoda nie dołącza podmenu do menu podręczne.  
  
 Ta metoda zakończy się niepowodzeniem, jeśli narzędzi nadrzędnej `m_pToolBar`, jest `NULL` lub klasa podstawowa implementacja zwraca `FALSE`.  
  
##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar  
 Pobiera pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `m_pToolBar` element członkowski danych.  
  
##  <a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown  
 Określa, czy pasek narzędzi listy rozwijanej jest obecnie otwarty.  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pasek narzędzi listy rozwijanej jest obecnie otwarty; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Platformę otwiera pasek narzędzi listy rozwijanej przy użyciu [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Platformę zamyka pasek narzędzi listy rozwijanej, gdy użytkownik naciśnie przycisk myszy po lewej, w obszarze klienta z systemem innym niż pasek narzędzi listy rozwijanej.  
  
##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize  
 Określa, czy przycisk mogą być wyświetlane z rozszerzonego obramowania.  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku paska narzędzi mogą być wyświetlane z rozszerzonego granicy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o rozszerzonych obramowania, zobacz [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).  
  
##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay  
 Określa czas, który użytkownik musi przytrzymując przycisk myszy w dół, zanim zostanie wyświetlony pasek narzędzi listy rozwijanej.  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>Uwagi  
 Czas opóźnienia jest mierzony w milisekundach. Wartość domyślna to 500. Można ustawić opóźnienie innego, zmieniając wartość tego elementu członkowskiego danych udostępnionych.  
  
##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize  
 Wywoływane przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in]`sizeDefault`  
 Domyślny rozmiar przycisku.  
  
 [in]`bHorz`  
 Stan dokowania paska narzędzi nadrzędnej. Ten parametr jest `TRUE` czy pasek narzędzi jest zadokowany poziomo jest zmiennoprzecinkową lub `FALSE` Jeśli pasek narzędzi jest zadokowany w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `SIZE` struktury zawierającego wymiary przycisku w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) przez dodanie szerokość strzałkę listy rozwijanej do płaszczyźnie poziomej rozmiar przycisku.  
  
##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk jest wstawiany do nowego paska narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Nowe okno nadrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementację klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), usuwając zaznaczenie tekstu etykiety ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) i ustawienie [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) i [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) elementy członkowskie danych do `FALSE`.  
  
##  <a name="onclick"></a>CMFCDropDownToolbarButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Okno nadrzędne przycisku paska narzędzi.  
  
 [in]`bDelay`  
 `TRUE`Jeśli komunikat powinien zostać obsłużony z opóźnieniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizując stan pasek narzędzi listy rozwijanej.  
  
 Po kliknięciu przycisku paska narzędzi, ta metoda tworzy czasomierza oczekiwania przez czas określony przez [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) element członkowski danych, a następnie otwiera listy rozwijanej narzędzi przy użyciu [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Ta metoda powoduje zamknięcie pasek narzędzi listy rozwijanej po raz drugi użytkownik kliknie przycisk paska narzędzi.  
  
##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp  
 Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy.  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizując stan pasek narzędzi listy rozwijanej.  
  
 Tej metody zatrzymuje czasomierza pasek narzędzi listy rozwijanej, jeśli jest aktywny. Zamyka pasek narzędzi listy rozwijanej, jeśli jest on otwarty.  
  
 Aby uzyskać więcej informacji na temat narzędzi listy rozwijanej i czasomierza pasek narzędzi listy rozwijanej, zobacz [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp  
 Wywoływane przez platformę, obsługując narzędzi nadrzędnej `WM_HELPHITTEST` wiadomości.  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Okno nadrzędne przycisku paska narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli przycisku przetwarza komunikat pomocy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) przez wywołanie metody [CMFCDropDownToolbarButton::OnClick](#onclick) metody z `bDelay` ustawioną `FALSE` . Ta metoda zwraca wartość, która jest zwracana w wyniku [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
 Aby uzyskać więcej informacji na temat `WM_HELPHITTEST message, see` [TN028: Obsługa pomocy Context-Sensitive](../../mfc/tn028-context-sensitive-help-support.md).  
  
##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu  
 Modyfikuje podana menu, gdy aplikacja wyświetla menu skrótów na pasku narzędzi nadrzędnej.  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pMenu`  
 Aby dostosować menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) przez wyłączenie następujących elementów:  
  
- **Kopiuj obraz przycisku**  
  
- **Wygląd przycisku**  
  
- **Obraz**  
  
- **Tekst**  
  
- **Obraz i tekst**  
  
 Zastępuje tę metodę, aby zmodyfikować menu skrótów, w ramach wyświetlany w trybie dostosowania.  
  
##  <a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw  
 Wywoływane przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku.  
  
 [in]`pImages`  
 Kolekcja obrazy pasków narzędzi, która jest skojarzona z przyciskiem.  
  
 [in]`bHorz`  
 Stan dokowania paska narzędzi nadrzędnej. Ten parametr jest `TRUE` gdy przycisk jest zadokowany poziomo i `FALSE` gdy przycisk jest zadokowany w pionie.  
  
 [in]`bCustomizeMode`  
 Określa, czy pasek narzędzi jest w trybie dostosowania. Ten parametr jest `TRUE` gdy pasek narzędzi jest w trybie dostosowania i `FALSE` gdy pasek narzędzi nie jest w trybie dostosowania.  
  
 [in]`bHighlight`  
 Określa, czy przycisk jest podświetlona. Ten parametr jest `TRUE` gdy przycisk zostanie wyróżniona i `FALSE` gdy nie są wyróżnione przycisku.  
  
 [in]`bDrawBorder`  
 Określa, czy przycisk powinien wyświetlać obramowanie. Ten parametr jest `TRUE` gdy przycisk powinien być wyświetlany obramowania i `FALSE` gdy przycisk powinien być nie wyświetlany obramowania.  
  
 [in]`bGrayDisabledButtons`  
 Określa, czy do cieniowania przycisków wyłączone lub użyć kolekcji obrazów wyłączone. Ten parametr jest `TRUE` po wyłączone przycisków powinna być przyciemnione i `FALSE` po tej metody należy użyć kolekcji obrazów wyłączone.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby dostosować rysowaniem przycisku paska narzędzi.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku.  
  
 [in]`bSelected`  
 Określa, czy przycisk jest zaznaczony. Jeśli ten parametr ma `TRUE`, ten przycisk jest zaznaczony. Jeśli ten parametr ma `FALSE`, nie wybrano przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w pikselach przycisku w kontekście określonego urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w oknie dialogowym dostosowywania ( **polecenia** kartę) gdy przycisk jest wymagany do wyświetlania się na liście rysowania przez właściciela.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)), zmieniając etykietę tekst przycisku do nazwy przycisku (oznacza to, wartość `lpszName` parametr, który został przekazany do konstruktora).  
  
##  <a name="serialize"></a>CMFCDropDownToolbarButton::Serialize  
 Odczytuje obiekt z archiwum i zapisuje go do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`ar`  
 `CArchive` Obiektu, z którego lub do której do serializacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)), szeregując identyfikator zasobu nadrzędnego paska narzędzi. Podczas ładowania archiwum ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) zwraca wartość niezerową), ta metoda ustawia `m_pToolBar` element członkowski danych do paska narzędzi, który zawiera identyfikator zasobu serializacji.  
  
##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand  
 Ustawia domyślne polecenie używającej platformę, gdy użytkownik kliknie przycisk.  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia domyślne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby określić polecenie domyślne wykonujący przez platformę, gdy użytkownik kliknie przycisk. Element o określonym przez identyfikator polecenia `uiCmd` musi znajdować się na pasku narzędzi z listy rozwijanej nadrzędnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolbar — klasa](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Wskazówki: Umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



