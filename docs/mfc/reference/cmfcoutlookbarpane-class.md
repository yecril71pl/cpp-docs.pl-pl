---
title: Klasa CMFCOutlookBarPane | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 394cd0da74171e517086886a5c0c915fc77ba49c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464659"
---
# <a name="cmfcoutlookbarpane-class"></a>Klasa CMFCOutlookBarPane
Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
 Formant pochodzące z [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) który może być wstawiany do paska Outlook ( [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Okienko paska Outlook zawiera kolumnę dużych przycisków. Użytkownik może przewijać listę przycisków w górę i w dół, jeśli jest większa niż okienko. Kiedy użytkownik odłącza okienko paska Outlook od paska Outlook, możesz float lub Zadokuj w oknie głównym ramki.  
  
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
|[CMFCOutlookBarPane::AddButton](#addbutton)|Dodaje przycisk do okienko paska Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Określa, czy okienka może być zadokowane do innego okienka lub ramki okna. (Przesłania [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Określa, czy system można przywrócić pasek narzędzi do pierwotnego stanu po dostosowaniu. (Przesłania [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Zwalnia zasoby używane przez obrazów w okienko paska Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Tworzy okienko paska Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|  
|`CMFCOutlookBarPane::Dock`|Metoda wywoływana przez platformę, aby zadokować okienko paska Outlook. (Przesłania `CPane::Dock`.)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Określa, czy strzałek przewijania na okienko paska Outlook rozwijaj listę przycisków przez stronę lub po kliknięciu przycisku.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Zwraca kolor zwykłego tekstu (niezaznaczone) okienko paska Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Określa, czy jest załadowany na potrzeby okienko paska Outlook obrazu tła.|  
|`CMFCOutlookBarPane::IsChangeState`|Określa, czy może być zadokowane unoszącego. (Przesłania `CPane::IsChangeState`.)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Określa, czy gdy przycisk zostanie wyróżniona i pojawi się obraz tła przyciemnione obramowania przycisku.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Wywoływane przez platformę, gdy okienko jest o na typ zmiennoprzecinkowy. (Przesłania [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Usuwa przycisk, który ma identyfikator określonego polecenia.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Przywraca oryginalny stan paska narzędzi. (Przesłania [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Ustawia kolor tła.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Ustawia obraz tła.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Okienko paska Outlook powoduje przywrócenie oryginalnego zestawu przycisków.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Ustawia liczbę pikseli uzupełnienia używane w całym przycisków w okienko paska Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Ustawia kolorów tekstu, regularne i wyróżnione w okienko paska Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Określa przezroczysty kolor okienko paska Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Używane wewnętrznie, aby zaktualizować pasek programu Outlook. (Przesłania `CMFCToolBar::SmartUpdate`.)|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Określa elementy menu skrótów, które są wyświetlane w trybie dostosowywania.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Usuwa wszystkie przyciski z okienko paska Outlook. (Przesłania [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać informacje o sposobie wdrażania paska Outlook, zobacz [klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Na przykład paska Outlook Zobacz OutlookDemo przykładowy projekt.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia różnych metod `CMFCOutlookBarPane` klasy. W przykładzie pokazano sposób tworzenia okienko paska Outlook, Włącz tryb przewiń stronę, Włącz dokowanie i ustawić kolor tła paska Outlook. Ten fragment kodu jest częścią [przykładowy program Outlook wielu widoków](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxoutlookbarpane.h  
  
##  <a name="addbutton"></a>  CMFCOutlookBarPane::AddButton  
 Dodaje przycisk do okienko paska Outlook.  
  
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
 [in] *uiImage*  
 Określa identyfikator zasobu mapy bitowej.  
  
 [in] *lpszLabel*  
 Określa tekst na przycisku.  
  
 [in] *iIdCommand*  
 Określa identyfikator kontrolki przycisku.  
  
 [in] *iInsertAt*  
 Określa liczony od zera indeks, na stronie pasek programu outlook, w której mają zostać wstawione przycisku.  
  
 [in] *uiLabel*  
 Identyfikator zasobu ciągu.  
  
 [in] *szBmpFileName*  
 Określa nazwę pliku obrazu dysku do załadowania.  
  
 [in] *szLabel*  
 Określa tekst na przycisku.  
  
 [in] *hBmp*  
 Dojście do mapy bitowej przycisku.  
  
 [in] *hIcon*  
 Dojście do ikony przycisków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk został dodany pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wstawienie nowego przycisku paska Outlook strony. Obraz przycisku może zostać załadowany z zasobów aplikacji lub z pliku na dysku.  
  
 Jeśli identyfikator strony określony przez *uiPageID* wynosi -1, ten przycisk jest wstawiany do pierwszej strony.  
  
 Jeśli indeks określony przez *iInsertAt* wynosi -1, zostanie on dodany na końcu strony.  
  
##  <a name="canbeattached"></a>  CMFCOutlookBarPane::CanBeAttached  
 Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="clearall"></a>  CMFCOutlookBarPane::ClearAll  
 Zwalnia zasoby używane przez obrazów na okienko paska Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda bezpośrednio wywołuje [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), która jest wywoływana w obrazach, które są używane przez okienko paska Outlook.  
  
##  <a name="create"></a>  CMFCOutlookBarPane::Create  
 Tworzy okienko paska Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pParentWnd*  
 Określa okno nadrzędne kontrolki okienko paska Outlook. Nie może mieć wartości NULL.  
  
 [in] *dwStyle*  
 Styl okna.  Aby uzyskać listę Style okna zobacz [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *uiID*  
 Identyfikator kontrolki. Musi być unikatowa, aby umożliwić zapisanie stanu formantu.  
  
 [in] *dwControlBarStyle*  
 Określa specjalne style, które definiują zachowania formantu okienko paska Outlook, gdy jest ona odłączona od paska Outlook.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Do konstruowania `CMFCOutlookBarPane` obiektu, należy najpierw wywołać konstruktora, a następnie wywołaj `Create`, który tworzy paska sterowania okienko Outlook i dołącza go do `CMFCOutlookBarPane` obiektu.  
  
 Aby uzyskać więcej informacji na temat `dwControlBarStyle` zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="enablecontextmenuitems"></a>  CMFCOutlookBarPane::EnableContextMenuItems  
 Określa elementy menu skrótów, które są wyświetlane w trybie dostosowywania.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pButton*  
 Wskaźnik na przycisku paska narzędzi, który użytkownik kliknął element.  
  
 [in] *pPopup*  
 Wskaźnik do menu skrótów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli powinien być wyświetlany w menu skrótów; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby zmodyfikować menu skrótów standardowa framework, wyświetlanego w ramach w tryb dostosowywania.  
  
 Domyślna implementacja sprawdza, czy tryb dostosowywania ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) i jeśli jest ustawiona na TRUE uniemożliwi skrótów elementów menu, z wyjątkiem **Usuń**. Następnie, po prostu przekazuje parametry wejściowe, aby `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Menu kontekstowe* jest synonimem dla menu skrótów.  
  
##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode  
 Określa, czy strzałek przewijania na okienko paska Outlook, przejdź na liście przycisków przez strony lub przez przycisk.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bPageScroll*  
 W przypadku opcji TRUE, należy włączyć tryb przewiń stronę. W przypadku wartości FAŁSZ, wyłącz tryb przewijania strony.  
  
##  <a name="getregularcolor"></a>  CMFCOutlookBarPane::GetRegularColor  
 Zwraca zwykłych (czyli niezaznaczone) kolor tekstu okienko paska Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżący kolor tekstu jako wartość koloru RGB.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCOutlookBarPane::SetTextColor](#settextcolor) Aby ustawić bieżący kolor tekstu (zwykły i wybrany) pasek programu Outlook. Domyślny kolor tekstu można uzyskać wywołując [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) funkcji o indeksie COLOR_WINDOW.  
  
##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture  
 Określa, czy jest załadowany na potrzeby okienko paska Outlook obrazu tła.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli obraz tła ma być wyświetlany; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Możesz dodać obraz tła, wywołując [CMFCOutlookBarPane::SetBackImage](#setbackimage) funkcji.  
  
 Jeśli nie ma żadnego obrazu tła, tło jest malowane kolorem określone za pomocą [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="isdrawshadedhighlight"></a>  CMFCOutlookBarPane::IsDrawShadedHighlight  
 Określa, czy gdy przycisk zostanie wyróżniona i pojawi się obraz tła przyciemnione obramowania przycisku.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli jego granicami są zacieniowane; w przeciwnym razie wartość FALSE.  
  
##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons  
 Usuwa wszystkie przyciski z okienko paska Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton  
 Usuwa przycisk, który ma identyfikator określonego polecenia.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iIdCommand*  
 Określa identyfikator polecenia przycisk Usuń.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przycisk został pomyślnie usunięty; Wartość FALSE, jeśli polecenie o określonym identyfikatorze nie jest prawidłowy.  
  
##  <a name="setbackcolor"></a>  CMFCOutlookBarPane::SetBackColor  
 Ustawia kolor tła paska Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *kolorów*  
 Określa nowy kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, aby ustawić bieżący kolor tła paska Outlook. Kolor tła jest używana tylko wtedy, gdy nie ma żadnego obrazu tła.  
  
##  <a name="setbackimage"></a>  CMFCOutlookBarPane::SetBackImage  
 Ustawia obraz tła.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *uiImageID*  
 Określa identyfikator obrazu zasobu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można ustawić w programie Outlook obrazu tła paska. Lista obrazów tła jest zarządzana przez osadzonego [klasa CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) obiektu.  
  
##  <a name="setdefaultstate"></a>  CMFCOutlookBarPane::SetDefaultState  
 Okienko paska Outlook powoduje przywrócenie oryginalnego zestawu przycisków.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przywraca oryginalny zestaw przycisków paska Outlook. Ta metoda przypomina `CMFCOutlookBarPane::RestoreOriginalstate`, z tą różnicą, że nie wyzwala ponownego wystawienia w okienku paska Outlook.  
  
##  <a name="setextraspace"></a>  CMFCOutlookBarPane::SetExtraSpace  
 Ustawia liczbę pikseli uzupełnienia używane w całym przycisków w okienko paska Outlook.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor  
 Ustawia kolorów tekstu, regularne i wyróżnione w okienko paska Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *clrRegText*  
 Określa nowy kolor tekstu niezaznaczone.  
  
 [in] *clrSelText*  
 Określa nowy kolor dla zaznaczonego tekstu.  
  
##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor  
 Określa przezroczysty kolor okienko paska Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 *Kolor*  
 Określa nowy kolor przezroczysty.  
  
### <a name="remarks"></a>Uwagi  
 Przezroczysty kolor jest wymagana, aby wyświetlić obrazy przezroczyste. Dowolne wystąpienie tego koloru na obrazie jest malowane zamiast kolorem tła.  Nie ma żadnych mieszania obrazy tła i pierwszego planu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)   
 [Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
