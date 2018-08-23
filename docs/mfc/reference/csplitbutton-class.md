---
title: Klasa CSplitButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
dev_langs:
- C++
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7fd35c351639d4b7b5f3b9dbbbce1c5e7cbcb79
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465525"
---
# <a name="csplitbutton-class"></a>Klasa CSplitButton
`CSplitButton` Klasa reprezentuje formant przycisku podziału. Kontrolka przycisku podziału wykonuje domyślne zachowanie kiedy użytkownik klika na główną część przycisku oraz wyświetla menu rozwijane, gdy użytkownik kliknie strzałkę listy rozwijanej przycisku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSplitButton : public CButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitButton::CSplitButton](#csplitbutton)|Konstruuje `CSplitButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitButton::Create](#create)|Tworzy formant przycisku podziału z określonych stylów i dołącza go do bieżącego `CSplitButton` obiektu.|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Ustawia menu rozwijane, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|Obsługuje powiadomienie BCN_DROPDOWN, które wysyła system, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.|  
  
## <a name="remarks"></a>Uwagi  
 `CSplitButton` Klasa pochodzi od [CButton](../../mfc/reference/cbutton-class.md) klasy. Kontrolka przycisku podziału jest formant przycisku, którego styl jest BS_SPLITBUTTON. Wyświetla menu niestandardowe, gdy użytkownik kliknie strzałkę listy rozwijanej. Aby uzyskać więcej informacji, zobacz BS_SPLITBUTTON i BS_DEFSPLITBUTTON style w [style przycisku](http://msdn.microsoft.com/library/windows/desktop/bb775951).  
  
 Poniższa ilustracja przedstawia okno dialogowe, który zawiera kontrolkę pagera i formant przycisku podziału (1). (2) strzałkę listy rozwijanej już został kliknięty i pojawi się podmenu (3).  
  
 ![Okno dialogowe z kontrolki splitbutton i pager. ](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
 Ta klasa jest obsługiwana w Windows Vista i nowszych wersjach.  
  
 Dodatkowe wymagania dla tej klasy są opisane w [tworzenie wymagania dla Windows Vista wspólnych formantów](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="create"></a>  CSplitButton::Create  
 Tworzy formant przycisku podziału z określonych stylów i dołącza go do bieżącego `CSplitButton` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *dwStyle*|Bitowa kombinacja (lub) style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
|[in] *rect*|Odwołanie do [Prostokąt](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która zawiera położenie i rozmiar kontrolki.|  
|[in] *pParentWnd*|Wskaźnik zerowy [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|  
|[in] *nID*|Identyfikator kontrolki.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton  
 Konstruuje `CSplitButton` obiektu. Parametry Konstruktor określają podmenu, który jest wyświetlany, gdy użytkownik kliknie strzałkę listy rozwijanej kontrolki przycisku podziału.  
  
```  
CSplitButton();

 
CSplitButton(
    UINT nMenuId,   
    UINT nSubMenuId)  
CSplitButton(CMenu* pMenu)  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *nMenuId*|Identyfikator zasobu paska menu.|  
|[in] *nSubMenuId*|Identyfikator zasobu podmenu.|  
|[in] *pMenu*|Wskaźnik do [CMenu](../../mfc/reference/cmenu-class.md) obiektu, który określa podmenu. `CSplitButton` Obiektu usuwa `CMenu` obiekt i jego skojarzone HMENU podczas `CSplitButton` obiekt wykracza poza zakres.|  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CSplitButton::Create](#create) metodę, aby utworzyć formant przycisku podziału i dołączyć go do `CSplitButton` obiektu.  
  
##  <a name="ondropdown"></a>  CSplitButton::OnDropDown  
 Obsługuje powiadomienie BCN_DROPDOWN, które wysyła system, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *pNMHDR*|Wskaźnik do [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) struktury, który zawiera informacje o [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) powiadomień.|  
|[out] *pResult*|(Nie jest używany; jest zwracana żadna wartość). Zwraca wartość [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) powiadomień.|  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik kliknie strzałkę listy rozwijanej na formant przycisku podziału, system wysyła powiadomienie BCN_DROPDOWN komunikat, który `OnDropDown` metodę uchwytów. Jednak `CSplitButton` obiektu nie przekazuje powiadomień BCN_DROPDOWN do formantu, który zawiera formant przycisku podziału. W związku z tym zawierającą formant nie może obsługiwać niestandardową akcję w odpowiedzi na powiadomienia.  
  
 Aby zaimplementować niestandardową akcję, która obsługuje zawierający kontrolki, należy użyć [CButton](../../mfc/reference/cbutton-class.md) obiektu przy użyciu stylu BS_SPLITBUTTON zamiast `CSplitButton` obiektu. Następnie implementacji programu obsługi dla powiadomień BCN_DROPDOWN w `CButton` obiektu. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 Aby zaimplementować, przycisk podziału samej kontrolki obsługuje akcję niestandardową, należy użyć [komunikatu odbicia](../../mfc/tn062-message-reflection-for-windows-controls.md). Pochodną klasy z `CSplitButton` klasy i nadaj mu, na przykład CMySplitButton. Następnie dodaj poniższe mapy wiadomości do aplikacji do obsługi powiadomień BCN_DROPDOWN:  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu  
 Ustawia menu rozwijane, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] *nMenuId*|Identyfikator zasobu paska menu.|  
|[in] *nSubMenuId*|Identyfikator zasobu podmenu.|  
|[in] *pMenu*|Wskaźnik do [CMenu](../../mfc/reference/cmenu-class.md) obiektu, który określa podmenu. `CSplitButton` Obiektu usuwa `CMenu` obiekt i jego skojarzone HMENU podczas `CSplitButton` obiekt wykracza poza zakres.|  
  
### <a name="remarks"></a>Uwagi  
 *NMenuId* parametr identyfikuje paska menu, czyli Pozioma lista paska menu. *NSubMenuId* parametr jest liczony od zera numer indeksu, który identyfikuje podmenu, czyli z listy rozwijanej elementów menu związane z każdym elementem paska menu. Na przykład typowa aplikacja ma menu, które zawiera element paska menu "File", "Edit" i "Help". Element paska menu "File" ma podmenu, który zawiera elementy menu "Otwórz", "Zamknij" i "Zamknij". Po kliknięciu strzałki listy rozwijanej kontrolki przycisku podziału kontrolka ma wyświetlać określonego podmenu, a nie na pasku menu.  
  
 Poniższa ilustracja przedstawia okno dialogowe, który zawiera kontrolkę pagera i formant przycisku podziału (1). (2) strzałkę listy rozwijanej już został kliknięty i pojawi się podmenu (3).  
  
 ![Okno dialogowe z kontrolki splitbutton i pager. ](../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>Przykład  
 Pierwsza instrukcja w poniższym przykładzie kodu pokazano [CSplitButton::SetDropDownMenu](#setdropdownmenu) metody. Utworzyliśmy menu przy użyciu zasobów programu Visual Studio edytor, który automatycznie nadawaną nazwę Identyfikatora paska menu, IDR_MENU1. *NSubMenuId* parametr, który wynosi zero, dotyczy tylko podmenu paska menu.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSplitButton](../../mfc/reference/csplitbutton-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)
