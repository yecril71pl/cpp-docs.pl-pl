---
title: Klasa CMFCOutlookBarPane | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs: C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 737cf083eeca60cd0d6ac95cccbe570c56968fd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcoutlookbarpane-class"></a>Klasa CMFCOutlookBarPane
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Formant pochodzi od [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) mogą być wstawiane do paska Outlook ( [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md)). W okienku paska Outlook zawiera kolumnę duże przyciski. Użytkownika można przewijać listę przycisków w górę i w dół, jeśli jest większy niż okienka. Gdy użytkownik odłącza okienku paska Outlook na pasku programu Outlook, możesz float lub dokowany głównego okna ramowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Domyślny konstruktor.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|Dodaje przycisk w okienku paska programu Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Określa, czy okienko może być zadokowany do innego okienka lub ramki okna. (Przesłania [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Określa, czy system można przywrócić pasek narzędzi do stanu pierwotnego po dostosowaniu. (Przesłania [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Zwalnia zasoby używane przez obrazów w okienku paska programu Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Tworzy w okienku paska programu Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCOutlookBarPane::Dock`|Wywoływane przez platformę, by dock w okienku paska programu Outlook. (Przesłania `CPane::Dock`.)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Określa, czy strzałki przewijania w okienku paska wcześniejszego listy przycisków przez stronę lub po kliknięciu przycisku.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Zwraca kolor zwykłego tekstu (niezaznaczone) w okienku paska programu Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Określa, czy załadowano dla programu Outlook okienku paska obrazu tła.|  
|`CMFCOutlookBarPane::IsChangeState`|Określa, czy okienko przestawne może być zadokowany. (Przesłania `CPane::IsChangeState`.)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Określa, czy obramowania przycisku jest przyciemnione, gdy przycisk zostanie wyróżniona i nie jest wyświetlany obraz tła.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Wywoływane przez platformę, gdy nastąpi okienko float. (Przesłania [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Usuwa przycisku, który ma identyfikator określonego polecenia.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Przywraca oryginalny stan paska narzędzi. (Przesłania [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Ustawia kolor tła.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Ustawia obraz tła.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|W okienku paska Outlook powoduje przywrócenie oryginalnego zestawu przycisków.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Ustawia uzupełnienia używany wokół przycisków w okienku paska w pikselach.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Ustawia kolory regularne i wyróżnionego tekstu w okienku paska programu Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Określa kolor przezroczysty okienku paska programu Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Używana wewnętrznie w celu aktualizacji paska Outlook. (Przesłania `CMFCToolBar::SmartUpdate`.)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Określa elementy menu skrótów, które są wyświetlane w trybie dostosowania.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Usuwa wszystkie przyciski w okienku paska programu Outlook. (Przesłania [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje dotyczące implementacji paska Outlook, zobacz [CMFCOutlookBar klasy](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Na przykład paska Outlook Zobacz OutlookDemo przykładowy projekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod `CMFCOutlookBarPane` klasy. W przykładzie przedstawiono sposób tworzenia okienku paska programu Outlook, Włącz trybu przewijania strony, Włącz dokowanie i kolor tła paska Outlook. Następujący fragment kodu jest częścią [próbki Outlook wielu widoków](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxoutlookbarpane.h  
  
##  <a name="addbutton"></a>CMFCOutlookBarPane::AddButton  
 Dodaje przycisk w okienku paska programu Outlook.  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiImage`  
 Określa identyfikator zasobu mapy bitowej.  
  
 [in]`lpszLabel`  
 Określa tekst przycisku.  
  
 [in]`iIdCommand`  
 Określa identyfikator formantu przycisku.  
  
 [in]`iInsertAt`  
 Określa liczony od zera indeks na stronie paska outlook w celu wstawienia przycisku.  
  
 [in]`uiLabel`  
 Identyfikator zasobu ciągu.  
  
 [in]`szBmpFileName`  
 Określa nazwę pliku obrazu dysku do załadowania.  
  
 [in]`szLabel`  
 Określa tekst przycisku.  
  
 [in]`hBmp`  
 Dojście do mapy bitowej przycisku.  
  
 [in]`hIcon`  
 Dojście do ikony przycisków.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli przycisk został dodany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wstawienie nowego przycisku paska Outlook strony. Obraz przycisku mogą być ładowane z zasobów aplikacji lub pliku na dysku.  
  
 Jeśli określony identyfikator strony przez `uiPageID` wynosi -1, przycisk zostaną wstawione do pierwszej strony.  
  
 Jeśli indeks określony przez `iInsertAt` wynosi -1, zostanie dodany na końcu strony.  
  
##  <a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="clearall"></a>CMFCOutlookBarPane::ClearAll  
 Zwalnia zasoby używane przez obrazy w okienku paska programu Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda bezpośrednio wywołuje [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), nazywany na obrazy, które są używane w okienku paska programu Outlook.  
  
##  <a name="create"></a>CMFCOutlookBarPane::Create  
 Tworzy w okienku paska programu Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParentWnd`  
 Określa okno nadrzędne kontrolki okienku paska programu Outlook. Nie może być `NULL`.  
  
 [in]`dwStyle`  
 Styl okna.  Aby uzyskać listę Style okna, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in]`uiID`  
 Identyfikator formantu. Musi być unikatowa, aby umożliwić zapisanie stanu formantu.  
  
 [in]`dwControlBarStyle`  
 Określa style specjalne, definiujące zachowanie formantu okienku paska Outlook odłączeniem z paska Outlook.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Do utworzenia `CMFCOutlookBarPane` obiektów, pierwsze wywołanie konstruktora, a następnie wywołać `Create`, która tworzy paska formant okienka Outlook i dołącza go do `CMFCOutlookBarPane` obiektu.  
  
 Aby uzyskać więcej informacji na temat `dwControlBarStyle` zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems  
 Określa elementy menu skrótów, które są wyświetlane w trybie dostosowania.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pButton`  
 Wskaźnik, że użytkownik kliknął przycisk paska narzędzi.  
  
 [in]`pPopup`  
 Wskaźnik do menu skrótów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` menu skrótów będą wyświetlane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, aby zmodyfikować menu skrótów standardowe framework wyświetlanych w ramach w tryb dostosowywania.  
  
 Domyślna implementacja sprawdza Tryb dostosowywania ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) i jeśli jest ustawiona na `TRUE`, wyłącza wszystkie elementy menu skrótów z wyjątkiem **usunąć**. Następnie, po prostu przekazuje parametry wejściowe `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Menu kontekstowe* jest synonimem menu skrótów.  
  
##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode  
 Określa, czy strzałki przewijania w okienku paska wcześniejszego listy przycisków przez strony, lub przycisk przez przycisku.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bPageScroll`  
 Jeśli `TRUE`, Włącz tryb przewijania strony. Jeśli `FALSE`, wyłącz tryb przewijania strony.  
  
##  <a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor  
 Zwraca zwykłej (to znaczy niezaznaczone) kolor tekstu w okienku paska programu Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący kolor tekstu jako wartości kolorów RGB.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCOutlookBarPane::SetTextColor](#settextcolor) można ustawić bieżący kolor tekstu (zwykły i wybranych) paska Outlook. Kolor tekstu domyślne można uzyskać przez wywołanie metody [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) działać z `COLOR_WINDOW` indeksu.  
  
##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture  
 Określa, czy załadowano dla programu Outlook okienku paska obrazu tła.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli obraz tła ma być wyświetlany; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Możesz dodać obraz tła, wywołując [CMFCOutlookBarPane::SetBackImage](#setbackimage) funkcji.  
  
 Jeśli nie ma żadnego obrazu tła, tło jest rysowane kolorem określony za pomocą [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight  
 Określa, czy obramowania przycisku jest przyciemnione, gdy przycisk zostanie wyróżniona i nie jest wyświetlany obraz tła.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli obramowania przycisku są przyciemnione; w przeciwnym razie `FALSE`.  
  
##  <a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons  
 Usuwa wszystkie przyciski w okienku paska programu Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton  
 Usuwa przycisku, który ma identyfikator określonego polecenia.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iIdCommand`  
 Określa identyfikator polecenia przycisk Usuń.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli przycisk został pomyślnie usunięty; `FALSE` Jeśli identyfikator określonego polecenia jest nieprawidłowy.  
  
##  <a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor  
 Ustawia kolor tła paska Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Określa nowy kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby ustawić bieżący kolor tła paska programu Outlook. Kolor tła jest używany tylko wtedy, gdy nie ma żadnego obrazu tła.  
  
##  <a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage  
 Ustawia obraz tła.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiImageID`  
 Określa identyfikator zasobu obrazu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można ustawić w programie Outlook obrazu tła paska. Lista obrazów tła jest zarządzana przez osadzonego [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiektu.  
  
##  <a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState  
 W okienku paska Outlook powoduje przywrócenie oryginalnego zestawu przycisków.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przywraca oryginalny zestaw przycisków paska programu Outlook. Ta metoda jest podobna `CMFCOutlookBarPane::RestoreOriginalstate`, ale nie wyzwala ponownego rysowania w okienku paska programu Outlook.  
  
##  <a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace  
 Ustawia uzupełnienia używany wokół przycisków w okienku paska w pikselach.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor  
 Ustawia kolory regularne i wyróżnionego tekstu w okienku paska programu Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`clrRegText`  
 Określa nowy kolor tekstu niezaznaczone.  
  
 [in]`clrSelText`  
 Określa nowy kolor dla zaznaczonego tekstu.  
  
##  <a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor  
 Określa kolor przezroczysty okienku paska programu Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Określa kolor przezroczysty.  
  
### <a name="remarks"></a>Uwagi  
 Przezroczysty kolor jest wymagany do wyświetlania obrazów przezroczysty. Każde zdarzenie kolor ten obraz jest rysowane zamiast tego kolorem tła.  Nie ma żadnych mieszania obrazy tła i pierwszego planu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
