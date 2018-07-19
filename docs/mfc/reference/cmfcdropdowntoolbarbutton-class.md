---
title: Klasa CMFCDropDownToolbarButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42ea64180a9f7abf37f379e3e8feccc4ee41fd44
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850199"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>Klasa CMFCDropDownToolbarButton
Typ przycisku paska narzędzi, który zachowuje się jak zwykły przycisk po kliknięciu. Jednak otwiera rozwijany pasek narzędzi ( [klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md) Jeśli naciśnięciu i przytrzymaniu przycisku paska narzędzi w dół.  
  
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
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi. (Przesłania [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCDropDownToolbarButton::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otwiera rozwijany pasek narzędzi.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Kopiuje tekst na przycisku paska narzędzi do menu. (Przesłania [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Pobiera rozwijany pasek narzędzi, który jest skojarzony z przyciskiem.|  
|`CMFCDropDownToolbarButton::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Określa, czy rozwijany pasek narzędzi jest obecnie otwarty.|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Określa, czy przycisk mogą być wyświetlane w rozszerzonej obramowania. (Przesłania [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Metoda wywoływana przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania. (Przesłania [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|Wywoływane przez platformę, by obsłużyć [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) wiadomości. (Przesłania `CMCToolBarButton::OnCancelMode`.)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi. (Przesłania [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy. (Przesłania [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy. (Przesłania [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Wywoływane przez platformę, obsługując komunikat WM_HELPHITTEST narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Modyfikuje podana menu, gdy aplikacja wyświetli menu skrótów na pasku narzędzi nadrzędnej. (Przesłania [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje. (Przesłania [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe. (Przesłania [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Odczytuje obiekt z archiwum lub zapisuje je do archiwum. (Przesłania [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Określa polecenie domyślne, które używa platformę, gdy użytkownik kliknie przycisk.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Określa długość czasu, który użytkownik musi przytrzymując przycisk myszy w dół, przed wyświetleniem rozwijany pasek narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 A `CMFCDropDownToolBarButton` różni się od zwykłej przycisku, że ma ona małą strzałkę w prawym dolnym rogu przycisk. Po użytkownik wybierze przycisk na pasku narzędzi listy rozwijanej, struktura wyświetla jego ikonę na pasku narzędzi najwyższego poziomu (przycisk z małą strzałkę w prawym dolnym rogu).  
  
 Aby uzyskać informacje o sposobie wdrażania rozwijany pasek narzędzi, zobacz [klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
 `CMFCDropDownToolBarButton` Obiektu można wyeksportować do [klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu i wyświetlane jako przycisk menu z menu podręcznego.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>  CMFCDropDownToolbarButton::CopyFrom  
 Kopiuje bieżącego przycisku Właściwości inny przycisk paska narzędzi.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *src*  
 Odwołanie do przycisku źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby skopiować inny przycisk paska narzędzi do tego przycisku paska narzędzi. *SRC* musi być typu `CMFCDropDownToolbarButton`.  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>  CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 Konstruuje `CMFCDropDownToolbarButton` obiektu.  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszName*  
 Domyślny tekst przycisku.  
  
 [in] *pToolBar*  
 Wskaźnik do `CMFCDropDownToolBar` obiekt, który jest wyświetlany, gdy użytkownik naciśnie przycisk.  
  
### <a name="remarks"></a>Uwagi  
 Drugie przeciążenie konstruktora kopiuje do przycisku rozwijanego pierwszy przycisk na pasku narzędzi, *pToolBar* określa.  
  
 Zazwyczaj przycisku paska narzędzi z listy rozwijanej używa tekst z ostatnio używanych przycisk na pasku narzędzi, *pToolBar* określa. Używa ona tekstu określonego przez *lpszName* po przycisku jest konwertowany na przycisk menu lub jest wyświetlany w **poleceń** karcie **Dostosuj** okno dialogowe. Aby uzyskać więcej informacji na temat **Dostosuj** okno dialogowe, zobacz [klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCDropDownToolbarButton` klasy. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>  CMFCDropDownToolbarButton::DropDownToolbar  
 Otwiera rozwijany pasek narzędzi.  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
 Okno nadrzędne ramkę z listy rozwijanej lub wartości NULL na korzystanie z okna nadrzędnego przycisku paska narzędzi z listy rozwijanej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [CMFCDropDownToolbarButton::OnClick](#onclick) metoda wywołuje tę metodę, aby otworzyć pasek narzędzi listy rozwijanej, po naciśnięciu i przytrzymaniu przycisku paska narzędzi w dół.  
  
 Ta metoda tworzy rozwijany pasek narzędzi przy użyciu [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) metody. Jeśli pasek narzędzi nadrzędnego jest zadokowany w pionie, ta metoda powoduje umieszczenie rozwijany pasek narzędzi albo po lewej stronie lub po prawej stronie strony nadrzędne paska narzędzi, w zależności od rozmiaru. W przeciwnym razie ta metoda powoduje umieszczenie rozwijany pasek narzędzi poniżej paska narzędzi nadrzędnej.  
  
 Ta metoda kończy się niepowodzeniem, jeśli *pWnd* ma wartość NULL, a przycisk na pasku narzędzi listy rozwijanej nie ma okno nadrzędne.  
  
##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton  
 Kopiuje tekst na przycisku paska narzędzi do menu.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *przycisk menu*  
 Odwołanie do docelowego przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli metoda się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje implementacji klasy podstawowej ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) i następnie dołącza do docelowego przycisk menu wyskakujących menu, które zawiera każdy element menu narzędzi tego przycisku. Ta metoda dołącza podmenu do menu podręcznego.  
  
 Ta metoda kończy się niepowodzeniem, jeśli narzędzi nadrzędnego `m_pToolBar`, ma wartość NULL lub implementacji klasy podstawowej, zwraca wartość FALSE.  
  
##  <a name="getdropdowntoolbar"></a>  CMFCDropDownToolbarButton::GetDropDownToolBar  
 Pobiera rozwijany pasek narzędzi, który jest skojarzony z przyciskiem.  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasek narzędzi listy rozwijanej, który jest skojarzony z przyciskiem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca `m_pToolBar` element członkowski danych.  
  
##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown  
 Określa, czy rozwijany pasek narzędzi jest obecnie otwarty.  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli rozwijany pasek narzędzi jest obecnie otwarty; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Struktura otwiera rozwijany pasek narzędzi za pomocą [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Struktura zamyka rozwijany pasek narzędzi, gdy użytkownik naciśnie przycisk myszy po lewej stronie w obszarze nieklienckiego rozwijany pasek narzędzi.  
  
##  <a name="isextrasize"></a>  CMFCDropDownToolbarButton::IsExtraSize  
 Określa, czy przycisk mogą być wyświetlane w rozszerzonej obramowania.  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisku paska narzędzi mogą być wyświetlane z obramowaniem rozszerzone; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat rozszerzonej obramowania zobacz [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).  
  
##  <a name="m_uishowbardelay"></a>  CMFCDropDownToolbarButton::m_uiShowBarDelay  
 Określa długość czasu, który użytkownik musi przytrzymując przycisk myszy w dół, przed wyświetleniem rozwijany pasek narzędzi.  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>Uwagi  
 Czas opóźnienia jest mierzony w milisekundach. Wartość domyślna to 500. Możesz ustawić opóźnienie innego, zmieniając wartość ten element członkowski danych udostępnionych.  
  
##  <a name="oncalculatesize"></a>  CMFCDropDownToolbarButton::OnCalculateSize  
 Metoda wywoływana przez platformę, by Oblicz rozmiar przycisku dla kontekstu określonego urządzenia i stan dokowania.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
 [in] *sizeDefault*  
 Domyślny rozmiar przycisku.  
  
 [in] *bHorz*  
 Stan dokowania paska narzędzi nadrzędnej. Ten parametr jest wartość TRUE, jeśli pasek narzędzi jest zadokowany poziomo lub jest liczb zmiennoprzecinkowych, lub FAŁSZ, jeśli pasek narzędzi jest zadokowany w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `SIZE` strukturę, która zawiera wymiary przycisku w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)), dodając szerokość strzałkę listy rozwijanej do poziomy wymiar rozmiar przycisku.  
  
##  <a name="onchangeparentwnd"></a>  CMFCDropDownToolbarButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk znajduje się nowy pasek narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWndParent*  
 Nowe okno nadrzędne.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zastępuje implementacji klasy podstawowej ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)), czyszcząc Etykieta tekstowa ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) i ustawienie [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) i [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) elementy członkowskie danych na wartość FALSE.  
  
##  <a name="onclick"></a>  CMFCDropDownToolbarButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk myszy.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
 Okno nadrzędne przycisku paska narzędzi.  
  
 [in] *bDelay*  
 Wartość TRUE, jeśli komunikat powinien zostać obsłużony z opóźnieniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), aktualizując stan rozwijany pasek narzędzi.  
  
 Gdy użytkownik kliknie przycisk na pasku narzędzi, ta metoda tworzy czasomierz, który oczekuje na czas określony przez [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) element członkowski danych, a następnie otwiera listę rozwijaną paska narzędzi, za pomocą [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metody. Ta metoda powoduje zamknięcie rozwijany pasek narzędzi po raz drugi użytkownik kliknie przycisk na pasku narzędzi.  
  
##  <a name="onclickup"></a>  CMFCDropDownToolbarButton::OnClickUp  
 Wywoływane przez platformę, gdy użytkownik zwolni przycisk myszy.  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk przetwarza wiadomości kliknij; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), aktualizując stan rozwijany pasek narzędzi.  
  
 Ta metoda zatrzymuje czasomierz rozwijany pasek narzędzi, jeśli jest aktywny. Jeśli jest otwarty, zamyka rozwijany pasek narzędzi.  
  
 Aby uzyskać więcej informacji na temat rozwijany pasek narzędzi oraz czasomierzem rozwijany pasek narzędzi, zobacz [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
##  <a name="oncontexthelp"></a>  CMFCDropDownToolbarButton::OnContextHelp  
 Wywoływane przez platformę, obsługując komunikat WM_HELPHITTEST narzędzi nadrzędnej.  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pWnd*  
 Okno nadrzędne przycisku paska narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli przycisk przetwarza komunikat pomocy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) przez wywołanie metody [CMFCDropDownToolbarButton::OnClick](#onclick) metody z *bDelay*ustawiony na wartość FALSE. Ta metoda zwraca wartość, która jest zwracana przez [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
 Aby uzyskać więcej informacji na temat wiadomości WM_HELPHITTEST zobacz [TN028: Obsługa pomocy Context-Sensitive](../../mfc/tn028-context-sensitive-help-support.md).  
  
##  <a name="oncustomizemenu"></a>  CMFCDropDownToolbarButton::OnCustomizeMenu  
 Modyfikuje podana menu, gdy aplikacja wyświetli menu skrótów na pasku narzędzi nadrzędnej.  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pMenu*  
 Menu aby dostosować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca wartość TRUE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)), wyłączając następujących elementów:  
  
- **Kopiuj obraz przycisku**  
  
- **Wyglądu przycisku**  
  
- **Obraz**  
  
- **Tekst**  
  
- **Obraz i tekst**  
  
 Zastępuje tę metodę, aby zmodyfikować menu skrótów, w ramach wyświetlany w trybie dostosowywania.  
  
##  <a name="ondraw"></a>  CMFCDropDownToolbarButton::OnDraw  
 Metoda wywoływana przez platformę, by narysować przycisku przy użyciu określonych stylów i opcje.  
  
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
 [in] *podstawowego kontrolera domeny*  
 Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
 [in] *rect*  
 Prostokąt otaczający przycisku.  
  
 [in] *pImages*  
 Kolekcja paska narzędzi obrazów, która jest skojarzona z przyciskiem.  
  
 [in] *bHorz*  
 Stan dokowania paska narzędzi nadrzędnej. Ten parametr ma wartość TRUE, gdy przycisk jest zadokowany w poziomie i wartość FALSE, gdy przycisk jest zadokowany w pionie.  
  
 [in] *bCustomizeMode*  
 Określa, czy pasek narzędzi jest w trybie dostosowywania. Ten parametr ma wartość TRUE, gdy pasek narzędzi jest w trybie dostosowywania i wartość FALSE, gdy pasek narzędzi nie jest w trybie dostosowywania.  
  
 [in] *bHighlight*  
 Określa, czy przycisk jest wyróżniona. Ten parametr jest wartość PRAWDA, jeśli przycisk jest wyróżniona i wartość FALSE, gdy przycisk nie jest wyróżniona.  
  
 [in] *bDrawBorder*  
 Określa, czy przycisk powinien być wyświetlany jego obramowania. Ten parametr ma wartość TRUE, gdy przycisk powinien być wyświetlany jego krawędzi i wartość FALSE, gdy przycisk nie powinien być wyświetlany jego obramowania.  
  
 [in] *bGrayDisabledButtons*  
 Określa, czy Cieniuj przyciski wyłączone lub użyć kolekcji obrazów wyłączone. Ten parametr ma wartość TRUE, gdy wyłączone przyciski powinny być przyciemnione i wartość FALSE w przypadku tej metody należy użyć kolekcji obrazów wyłączone.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby dostosować rysowaniem przycisku paska narzędzi.  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 Wywoływane przez platformę, by narysować przycisku **polecenia** okienku **Dostosuj** okno dialogowe.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *podstawowego kontrolera domeny*  
 Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
 [in] *rect*  
 Prostokąt otaczający przycisku.  
  
 [in] *bSelected*  
 Czy przycisk jest zaznaczony. Jeśli ten parametr ma wartość TRUE, zostanie wybrany przycisk. Jeśli ten parametr ma wartość FALSE, przycisk nie jest zaznaczone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w pikselach, przycisk w kontekście określonego urządzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez okno dialogowe dostosowywania ( **polecenia** kartę) po przycisku jest wymagany, aby wyświetlić się pole listy rysowane przez właściciela.  
  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)), zmieniając nazwę przycisku tekst etykiety przycisku (czyli wartość *lpszName* parametr, który został przekazany do konstruktora).  
  
##  <a name="serialize"></a>  CMFCDropDownToolbarButton::Serialize  
 Odczytuje obiekt z archiwum lub zapisuje je do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *ar*  
 `CArchive` Obiektu, z którego lub do którego ma zostać serializacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)), szeregując identyfikator zasobu nadrzędnego paska narzędzi. Podczas ładowania archiwum ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) zwraca wartość różną od zera), ta metoda ustawia `m_pToolBar` element członkowski danych do paska narzędzi, który zawiera identyfikator zasobu serializacji.  
  
##  <a name="setdefaultcommand"></a>  CMFCDropDownToolbarButton::SetDefaultCommand  
 Określa polecenie domyślne, które używa platformę, gdy użytkownik kliknie przycisk.  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiCmd*  
 Identyfikator polecenia domyślne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby określić polecenie domyślne, które wykonuje szablon, gdy użytkownik kliknie przycisk. Element o identyfikatorze polecenie określone przez *uiCmd* musi znajdować się na pasku narzędzi listy rozwijanej nadrzędnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



