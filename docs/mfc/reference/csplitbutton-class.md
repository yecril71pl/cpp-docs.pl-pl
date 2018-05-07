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
ms.openlocfilehash: ac4241bb19c6abc0fbbf489bf4efb43f56ede72e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csplitbutton-class"></a>Klasa CSplitButton
`CSplitButton` Klasa reprezentuje kontrolkę przycisku podziału. Kontrolka przycisku podziału wykonuje domyślne zachowanie, gdy użytkownik kliknie przycisk głównej części i wyświetla menu rozwijanego, gdy użytkownik kliknie strzałkę listy rozwijanej przycisku.  
  
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
|[CSplitButton::Create](#create)|Tworzy kontrolkę przycisku podziału przy użyciu określonego stylów i dołącza go do bieżącej `CSplitButton` obiektu.|  
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Ustawia menu rozwijanego, która jest wyświetlana, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitButton::OnDropDown](#ondropdown)|Obsługuje `BCN_DROPDOWN` powiadomienie, które wysyła systemu, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.|  
  
## <a name="remarks"></a>Uwagi  
 `CSplitButton` Jest pochodną klasy [CButton](../../mfc/reference/cbutton-class.md) klasy. Kontrolka przycisku podziału jest formantem przycisk o stylu `BS_SPLITBUTTON`. Gdy użytkownik kliknie strzałkę listy rozwijanej on Wyświetla menu niestandardowe. Aby uzyskać więcej informacji, zobacz `BS_SPLITBUTTON` i `BS_DEFSPLITBUTTON` style w [style przycisku](http://msdn.microsoft.com/library/windows/desktop/bb775951).  
  
 Na poniższym rysunku przedstawiono okno dialogowe, który zawiera kontrolkę stronicowania i kontrolkę przycisku podziału (1). Kliknął już strzałkę listy rozwijanej (2) i (3) podmenu jest wyświetlany.  
  
 ![Okno dialogowe z formantu splitbutton i modułu stronicowania. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 `CSplitButton`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
 Ta klasa jest obsługiwana w [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] i nowszych.  
  
 Dodatkowe wymagania dotyczące tej klasy są opisane w [kompilacji wymagania dla formantów systemu Windows Vista wspólnej](../../mfc/build-requirements-for-windows-vista-common-controls.md).  
  
##  <a name="create"></a>  CSplitButton::Create  
 Tworzy kontrolkę przycisku podziału przy użyciu określonego stylów i dołącza go do bieżącej `CSplitButton` obiektu.  
  
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
|[in] `dwStyle`|Bitowe połączenie (lub) style, które mają być stosowane do formantu. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).|  
|[in] `rect`|Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która zawiera położenie i rozmiar formantu.|  
|[in] `pParentWnd`|Wskaźnik inną niż null do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki.|  
|[in] `nID`|Identyfikator formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton  
 Konstruuje `CSplitButton` obiektu. Konstruktor parametry określają podmenu, które jest wyświetlane, gdy użytkownik kliknie strzałkę listy rozwijanej kontrolki przycisku podziału.  
  
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
|[in] `nMenuId`|Identyfikator zasobu paska menu.|  
|[in] `nSubMenuId`|Identyfikator zasobu podmenu.|  
|[in] `pMenu`|Wskaźnik do [cmenu —](../../mfc/reference/cmenu-class.md) obiekt, który określa podmenu. `CSplitButton` Obiekt usuwa `CMenu` obiekt i jego skojarzony `HMENU` podczas `CSplitButton` obiektu wykracza poza zakres.|  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CSplitButton::Create](#create) metody Utwórz kontrolkę przycisku podziału i dołączenie go do `CSplitButton` obiektu.  
  
##  <a name="ondropdown"></a>  CSplitButton::OnDropDown  
 Obsługuje `BCN_DROPDOWN` powiadomienie, które wysyła systemu, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
afx_msg void OnDropDown(
    NMHDR* pNMHDR,   
    LRESULT* pResult);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `pNMHDR`|Wskaźnik do [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) struktury, który zawiera informacje o [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) powiadomień.|  
|[out] `pResult`|(Nie jest używany; zostanie zwrócona wartość nie). Wartość zwracana [BCN_DROPDOWN](http://msdn.microsoft.com/library/windows/desktop/bb775983) powiadomień.|  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik kliknie strzałkę listy rozwijanej w formancie przycisku podziału, system wysyła `BCN_DROPDOWN` powiadomień wiadomości, które `OnDropDown` dojścia metody. Jednak `CSplitButton` nie przekazuje obiekt `BCN_DROPDOWN` powiadomień do formantu, który zawiera kontrolki przycisku podziału. W związku z tym zawierający formant nie obsługuje akcji niestandardowej w odpowiedzi na powiadomienia.  
  
 Do wykonania akcji niestandardowej, która obsługuje formantu zawierającego, należy użyć [CButton](../../mfc/reference/cbutton-class.md) obiektu o styl `BS_SPLITBUTTON` zamiast `CSplitButton` obiektu. Następnie implementacji programu obsługi dla `BCN_DROPDOWN` powiadomień w `CButton` obiektu. Aby uzyskać więcej informacji, zobacz [style przycisku](../../mfc/reference/styles-used-by-mfc.md#button-styles).  
  
 Aby zaimplementować czy przycisku podziału samą kontrolką obsługuje akcji niestandardowej, należy użyć [komunikatu odbicia](../../mfc/tn062-message-reflection-for-windows-controls.md). Pochodzi z klasy z `CSplitButton` klasy i nazwę, na przykład CMySplitButton. Następnie dodaj poniższe mapy komunikatów do aplikacji do obsługi `BCN_DROPDOWN` powiadomień:  
  
```  
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)  
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)  
END_MESSAGE_MAP()  
```  
  
##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu  
 Ustawia menu rozwijanego, która jest wyświetlana, gdy użytkownik kliknie strzałkę listy rozwijanej bieżącego formantu przycisku podziału.  
  
```  
void SetDropDownMenu(
    UINT nMenuId,   
    UINT nSubMenuId);  
  
void SetDropDownMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `nMenuId`|Identyfikator zasobu paska menu.|  
|[in] `nSubMenuId`|Identyfikator zasobu podmenu.|  
|[in] `pMenu`|Wskaźnik do [cmenu —](../../mfc/reference/cmenu-class.md) obiekt, który określa podmenu. `CSplitButton` Obiekt usuwa `CMenu` obiekt i jego skojarzony `HMENU` podczas `CSplitButton` obiektu wykracza poza zakres.|  
  
### <a name="remarks"></a>Uwagi  
 `nMenuId` Parametr identyfikuje paska menu, czyli listę poziome paska menu. `nSubMenuId` Parametr jest liczony od zera numer indeksu, który identyfikuje podmenu, czyli z listy rozwijanej skojarzone z każdym elementem paska menu elementów menu. Na przykład typowa aplikacja ma menu, która zawiera element paska menu "File", "Edytuj" i "Help". Element paska menu "File" ma podmenu, który zawiera elementy menu "Otwieranie", "Zamknij" i "Exit". Po kliknięciu formantu przycisku podziału strzałkę listy rozwijanej kontrolka ma wyświetlać określony podmenu, a nie na pasku menu.  
  
 Na poniższym rysunku przedstawiono okno dialogowe, który zawiera kontrolkę stronicowania i kontrolkę przycisku podziału (1). Kliknął już strzałkę listy rozwijanej (2) i (3) podmenu jest wyświetlany.  
  
 ![Okno dialogowe z formantu splitbutton i modułu stronicowania. ] (../../mfc/reference/media/splitbutton_pager.png "splitbutton_pager")  
  
### <a name="example"></a>Przykład  
 Pierwsza instrukcja w poniższym przykładzie kodu pokazano [CSplitButton::SetDropDownMenu](#setdropdownmenu) metody. Utworzyliśmy menu z programem Visual Studio edytora zasobów, które automatycznie o nazwie identyfikator paska menu, `IDR_MENU1`. `nSubMenuId` Parametr, który wynosi zero, dotyczą tylko podmenu paska menu.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSplitButton](../../mfc/reference/csplitbutton-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CButton](../../mfc/reference/cbutton-class.md)
