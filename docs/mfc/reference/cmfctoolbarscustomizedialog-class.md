---
title: Klasa CMFCToolBarsCustomizeDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7015e3be189bce8745777ef7353e1f2788a6f6be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33378184"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Klasa CMFCToolBarsCustomizeDialog
Karta niemodalne okno dialogowe ( [cpropertysheet — klasa](../../mfc/reference/cpropertysheet-class.md)), który umożliwia użytkownikowi dostosowywanie pasków narzędzi, menu, skróty klawiaturowe, narzędzia zdefiniowane przez użytkownika i stylu wizualnego w aplikacji. Zazwyczaj użytkownik uzyskuje dostęp do tego okna dialogowego, wybierając **Dostosuj** z **narzędzia** menu.  
  
 **Dostosuj** okno dialogowe ma sześć kart: **polecenia**, **paski narzędzi**, **narzędzia**, **klawiatury**,  **Menu**, i **opcje**.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarsCustomizeDialog : public CPropertySheet  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Konstruuje `CMFCToolBarsCustomizeDialog` obiektu.|  
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Wstawia przycisku paska narzędzi do listy poleceń na **polecenia** strony|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) można dodać tego menu do listy poleceń na **polecenia** strony.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) można dodać tego menu do listy poleceń na **polecenia** strony.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Ładuje paska narzędzi z zasobów. Następnie dla każdego polecenia w wywołaniach menu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby wstawić przycisk listy poleceń na **polecenia** strony z określonej kategorii.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|Wyświetla **dostosowywania** okno dialogowe.|  
|`CMFCToolBarsCustomizeDialog::EnableTools`|Zarezerwowane do użytku w przyszłości.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Włącza lub wyłącza tworzenie nowych pasków narzędzi przy użyciu **Dostosuj** okno dialogowe.|  
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Wypełnia dostarczonych `CListBox` obiektu za pomocą poleceń w **wszystkie polecenia** kategorii.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Wypełnia dostarczonych `CComboBox` obiektu o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.|  
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Wypełnia dostarczonych `CListBox` obiektu o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.|  
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Pobiera nazwę, która jest skojarzona z identyfikatorem danego polecenia.|  
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Pobiera liczbę elementów w podanej listy, etykiety danego tekstu.|  
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Pobiera zestaw flag, które wpływają na zachowanie okna dialogowego.|  
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Zostanie uruchomiony Edytor obrazów, dzięki czemu użytkownik może dostosować ikony elementu menu lub przycisku paska narzędzi.|  
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Zastąpienia, aby rozszerzyć inicjowanie arkusza właściwości. (Przesłania [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|  
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Wywoływane przez platformę po zniszczeniu okna. (Przesłania `CPropertySheet::PostNcDestroy`.)|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Usuwa element button z polecenie o określonym identyfikatorze z określonej kategorii lub z wszystkich kategorii.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Zmienia nazwę kategorii w polu listy kategorii na **polecenia** kartę.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Zastępuje przycisk na liście poleceń na **polecenia** kartę z obiektem przycisku paska narzędzi.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Dodaje do listy Kategorie, które będą wyświetlane na kategorię **polecenia** kartę.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Wywoływane przez platformę, by określić, czy lista narzędzia zdefiniowane przez użytkownika jest nieprawidłowy.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Wywoływane przez platformę, gdy zmiana właściwości narzędzia zdefiniowane przez użytkownika.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Określa, czy określony skrót można przypisać do akcji.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Określa, czy można zmienić narzędzia zdefiniowane przez użytkownika.|  
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Wywoływane przez platformę, gdy użytkownik wybierze **narzędzia** karcie jest wymagane.|  
  
## <a name="remarks"></a>Uwagi  
 Aby wyświetlić **Dostosuj** okna dialogowego Utwórz `CMFCToolBarsCustomizeDialog` obiekt i wywołanie [CMFCToolBarsCustomizeDialog::Create](#create) — metoda.  
  
 Gdy **Dostosuj** okno dialogowe jest aktywne, aplikacja działa w specjalnym trybie, która ogranicza użytkownikowi zadań dostosowania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCToolBarsCustomizeDialog` klasy. W przykładzie pokazano, jak zastąpić przycisku paska narzędzi w polu listy poleceń na **polecenia** pozycję Włącz tworzenie nowych pasków narzędzi przy użyciu **Dostosuj** okno dialogowe i wyświetlanie  **Dostosowywanie** okno dialogowe. Następujący fragment kodu jest częścią [próbka IE Demo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPropertySheet](../../mfc/reference/cpropertysheet-class.md)  
  
 `CMFCToolBarsCustomizeDialog`   
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxToolBarsCustomizeDialog.h  
  
##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton  
 Wstawia przycisku paska narzędzi do listy poleceń na **polecenia** strony.  
  
```  
void AddButton(
    UINT uiCategoryId,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,  
    const CMFCToolBarButton& button,  
    int iInsertBefore=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCategoryId`  
 Określa identyfikator kategorii, do której mają zostać wstawione przycisku.  
  
 [in] `button`  
 Określa przycisk Wstaw.  
  
 [in] `iInsertBefore`  
 Określa liczony od zera indeks przycisku paska narzędzi, przed którym zostanie wstawiony przycisku.  
  
 [in] `lpszCategory`  
 Określa ciąg kategorii przycisk Wstaw.  
  
### <a name="remarks"></a>Uwagi  
 `AddButton` Metoda ignoruje przycisków, które mają identyfikatory poleceń standardowych (takich jak ID_FILE_MRU_FILE1), polecenia, które nie są dozwolone (zobacz [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) i fikcyjny przycisków.  
  
 Ta metoda tworzy nowy obiekt ten sam typ co `button` (zazwyczaj [CMFCToolBarButton klasy](../../mfc/reference/cmfctoolbarbutton-class.md)) przy użyciu klasy środowiska uruchomieniowego przycisku. Następnie wywołuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) Aby skopiować elementy członkowskie danych przycisku i wstawia ją w wybranej kategorii.  
  
 Po wstawieniu przycisku Nowy odbiera `OnAddToCustomizePage` powiadomień.  
  
 Jeśli `iInsertBefore` wynosi -1, przycisk jest dołączany do listy kategorii; w przeciwnym razie zostanie on włożony przed elementem o określonym indeksie.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `AddButton` metody `CMFCToolBarsCustomizeDialog` klasy. Następujący fragment kodu jest częścią [próbki suwaka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]  
  
##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu  
 Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) można dodać tego menu do listy poleceń na **polecenia** strony.  
  
```  
BOOL AddMenu(UINT uiMenuResId);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiMenuResId`  
 Określa identyfikator zasobu menu do załadowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli menu został dodany pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 W wywołaniu `AddMenuCommands`, `bPopup` jest `FALSE`. W związku z tym tej metody nie dodaje elementy menu, które zawiera podmenu do listy poleceń. Ta metoda dodawania elementów menu w podmenu do listy poleceń.  
  
##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands  
 Dodaje elementy do listy poleceń w **polecenia** strony do reprezentowania wszystkich elementów w określonym menu.  
  
```  
void AddMenuCommands(
    const CMenu* pMenu,  
    BOOL bPopup,  
    LPCTSTR lpszCategory=NULL,  
    LPCTSTR lpszMenuPath=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pMenu`  
 Wskaźnik do obiektu cmenu — do dodania.  
  
 [in] `bPopup`  
 Określa, czy można wstawić elementów menu podręcznego do listy poleceń.  
  
 [in] `lpszCategory`  
 Nazwa kategorii, aby wstawić menu.  
  
 [in] `lpszMenuPath`  
 Prefiks, który jest dodawany do nazwy po poleceniu jest wyświetlany w **wszystkie kategorie** listy.  
  
### <a name="remarks"></a>Uwagi  
 `AddMenuCommands` Metody pętle za pośrednictwem wszystkich elementów menu `pMenu`. Dla każdego elementu menu, która nie zawiera podmenu, ta metoda tworzy [klasy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu i wywołania [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby dodać element menu jako pasek narzędzi przycisk do listy poleceń na **polecenia** strony. Separatory są ignorowane w tym procesie.  
  
 Jeśli `bPopup` jest `TRUE`, dla każdego elementu menu, która zawiera podmenu ta metoda tworzy [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu i wstawia go do listy poleceń, wywołując `AddButton`. W przeciwnym razie elementów menu, które zawierają podmenu nie są wyświetlane na liście poleceń. W obu przypadkach gdy `AddMenuCommands` napotkał element menu z podmenu wywołuje sam rekursywnie, przekazywanie do podmenu jako wskaźnik `pMenu` parametru i dołączenie etykiety podmenu `lpszMenuPath`.  
  
##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar  
 Ładuje paska narzędzi z zasobów. Następnie dla każdego polecenia w wywołaniach menu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby wstawić przycisk listy poleceń na **polecenia** strony z określonej kategorii.  
  
```  
BOOL AddToolBar(
    UINT uiCategoryId,  
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,  
    UINT uiToolbarResId);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCategoryId`  
 Określa identyfikator zasobu kategorii narzędzi, aby dodać.  
  
 [in] `uiToolbarResId`  
 Określa identyfikator zasobu narzędzi, w której polecenia są wstawiane do listy poleceń.  
  
 [in] `lpszCategory`  
 Określa nazwę kategorii, do której ma zostać dodany na pasku narzędzi.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `AddToolBar` metoda `CMFCToolBarsCustomizeDialog` klasy. Następujący fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]  
  
### <a name="remarks"></a>Uwagi  
 Formant, który jest używany do reprezentowania każde polecenie jest [klasy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu. Po dodaniu pasku narzędzi, można zastąpić przycisk formantu typu pochodnego wywołując [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).  
  
##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity  
 Sprawdza poprawność listę narzędzi użytkownika.  
  
```  
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lstTools`  
 Z listy zdefiniowanej przez użytkownika narzędzi do sprawdzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` Jeśli lista narzędzia zdefiniowane przez użytkownika jest prawidłowy; w przeciwnym razie `FALSE`. Domyślna implementacja zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę do sprawdzania poprawności obiekty reprezentujące narzędzia zdefiniowane przez użytkownika zwracane przez [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).  
  
 Zastąpienie `CheckToolsValidity` metodę w klasie pochodnej z `CMFCToolBarsCustomizeDialog` Jeśli chcesz zweryfikować narzędzi użytkownika, zanim użytkownik zamyka okno dialogowe. Jeśli ta metoda zwraca `FALSE` kiedy użytkownik kliknie **Zamknij** przycisk w prawym górnym rogu okna dialogowego lub przycisk **Zamknij** w prawym dolnym rogu okna dialogowego Wyświetla okno dialogowe **narzędzia** kartę zamiast zamknięcia. Jeśli ta metoda zwraca `FALSE` kiedy użytkownik kliknie kartę, aby przejść od **narzędzia** karcie nawigacji nie występuje. Powinien być wyświetlany komunikat odpowiednie w celu poinformowania użytkownika o problemie, który spowodował niepowodzenie sprawdzania poprawności.  
  
##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog  
 Konstruuje `CMFCToolBarsCustomizeDialog` obiektu.  
  
```  
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,  
    BOOL bAutoSetFromMenus = FALSE,  
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),  
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pWndParentFrame`  
 Wskaźnik do ramki nadrzędnej. Ten parametr nie może być `NULL`.  
  
 [in] `bAutoSetFromMenus`  
 Wartość logiczna określająca, czy mają zostać dodane do listy poleceń polecenia menu ze wszystkich menu na **polecenia** strony. Jeśli ten parametr ma `TRUE`, są dodawane poleceń menu. W przeciwnym razie nie zostaną dodane poleceń menu.  
  
 [in] `uiFlags`  
 Kombinacja flag, które wpływają na zachowanie okna dialogowego. Ten parametr może mieć co najmniej jeden z następujących wartości:  
  
- `AFX_CUSTOMIZE_MENU_SHADOWS`  
  
- `AFX_CUSTOMIZE_TEXT_LABELS`  
  
- `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
  
- `AFX_CUSTOMIZE_NOHELP`  
  
- `AFX_CUSTOMIZE_CONTEXT_HELP`  
  
- `AFX_CUSTOMIZE_NOTOOLS`  
  
- `AFX_CUSTOMIZE_MENUAMPERS`  
  
- `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
  
 [in] `plistCustomPages`  
 Wskaźnik do listy `CRuntimeClass` obiektów, które określają dodatkowe strony niestandardowe.  
  
### <a name="remarks"></a>Uwagi  
 `plistCustomPages` Parametr odnosi się do listy `CRuntimeClass` obiektów, które określają dodatkowe strony niestandardowe. Konstruktor dodaje więcej stron do okna dialogowego za pomocą [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) metody. Zobacz przykład CustomPages na przykład, który dodaje więcej stron do **Dostosuj** okno dialogowe.  
  
 Aby uzyskać więcej informacji o wartości, które mogą upłynąć w `uiFlags` parametrów, zobacz [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarsCustomizeDialog` klasy. Następujący fragment kodu jest częścią [próbki niestandardowych stron](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]  
  
##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create  
 Wyświetla **dostosowywania** okno dialogowe.  
  
```  
virtual BOOL Create();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli arkusz właściwości dostosowywania został utworzony pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie `Create` metody tylko wtedy, gdy pełne zainicjowanie klasy.  
  
##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars  
 Włącza lub wyłącza tworzenie nowych pasków narzędzi przy użyciu **Dostosuj** okno dialogowe.  
  
```  
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bEnable`  
 `TRUE` Aby włączyć paskach zdefiniowane przez użytkownika; `FALSE` wyłączyć pasków narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bEnable` jest `TRUE`, **nowy**, **zmienić** i **usunąć** przyciski są wyświetlane na **paski narzędzi** strony.  
  
 Domyślnie lub jeśli `bEnable` jest `FALSE`, nie są wyświetlane tych przycisków i użytkownik nie może definiować nowych pasków narzędzi.  
  
##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList  
 Wypełnia dostarczonych `CListBox` obiektu za pomocą poleceń w **wszystkie polecenia** kategorii.  
  
```  
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `wndListOfCommands`  
 Odwołanie do `CListBox` obiektu, aby wypełnić.  
  
### <a name="remarks"></a>Uwagi  
 **Wszystkie polecenia** kategoria zawiera polecenia wszystkich kategorii. [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda dodaje polecenia, które jest skojarzone z podanych przycisk, aby **wszystkie polecenia** kategorii dla Ciebie.  
  
 Ta metoda usuwa zawartość z dostarczonych `CListBox` obiektu przed zapełnianie poleceń w **wszystkie polecenia** kategorii.  
  
 `CMFCMousePropertyPage` Klasy używa tej metody do wypełnienia pola listy kliknij dwukrotnie zdarzenie.  
  
##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox  
 Wypełnia dostarczonych `CComboBox` obiektu o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.  
  
```  
void FillCategoriesComboBox(
    CComboBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `wndCategory`  
 Odwołanie do `CComboBox` obiektu, aby wypełnić.  
  
 [in] `bAddEmpty`  
 Wartość logiczna określająca, czy mają zostać dodane do pola kombi, które nie mają polecenia kategorii. Jeśli ten parametr ma `TRUE`, pusty kategorie są dodawane do pola kombi. W przeciwnym razie wartość pusta kategorii nie zostaną dodane.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) metody z tą różnicą, że ta metoda działa z `CComboBox` obiektu.  
  
 Ta metoda nie czyści zawartość `CComboBox` obiektu przed jego wypełniania. Gwarantuje, że **wszystkie polecenia** kategorii jest ostatnim elementem w polu kombi.  
  
 Możesz dodać nowe kategorie polecenia przy użyciu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Można zmienić nazwę istniejącej kategorii przy użyciu [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.  
  
 `CMFCToolBarsKeyboardPropertyPage` i `CMFCKeyMapDialog` klasy ta metoda służy do przeprowadzania kategoryzacji mapowania klawiatury.  
  
##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox  
 Wypełnia dostarczonych `CListBox` obiektu o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.  
  
```  
void FillCategoriesListBox(
    CListBox& wndCategory,  
    BOOL bAddEmpty = TRUE) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] `wndCategory`  
 Odwołanie do `CListBox` obiektu, aby wypełnić.  
  
 [in] `bAddEmpty`  
 Wartość logiczna określająca, czy mają zostać dodane do pola listy, które nie mają polecenia kategorii. Jeśli ten parametr ma `TRUE`, pusty kategorie są dodawane do pola listy. W przeciwnym razie wartość pusta kategorii nie zostaną dodane.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) metody z tą różnicą, że ta metoda działa z `CListBox` obiektu.  
  
 Ta metoda nie czyści zawartość `CListBox` obiektu przed jego wypełniania. Gwarantuje, że **wszystkie polecenia** kategorii jest ostatnim elementem w polu listy.  
  
 Możesz dodać nowe kategorie polecenia przy użyciu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Można zmienić nazwę istniejącej kategorii przy użyciu [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.  
  
 `CMFCToolBarsCommandsPropertyPage` Klasy używa tej metody, aby wyświetlić listę poleceń, jest skojarzona z każdej kategorii polecenia.  
  
##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName  
 Pobiera nazwę, która jest skojarzona z identyfikatorem danego polecenia.  
  
```  
LPCTSTR GetCommandName(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmd`  
 Identyfikator polecenia do pobrania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwę, która jest skojarzona z Identyfikatorem polecenia lub `NULL` Jeśli polecenie nie istnieje.  
  
##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory  
 Pobiera liczbę elementów w podanej listy, etykiety danego tekstu.  
  
```  
int GetCountInCategory(
    LPCTSTR lpszItemName,  
    const CObList& lstCommands) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszItemName`  
 Etykieta tekstowa do dopasowania.  
  
 [in] `lstCommands`  
 Odwołanie do listy, która zawiera `CMFCToolBarButton` obiektów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w określonych listy którego tekst etykiety equals `lpszItemName`.  
  
### <a name="remarks"></a>Uwagi  
 Każdy element na liście udostępnionego obiektu musi być typu `CMFCToolBarButton`. Ta metoda porównuje `lpszItemName` z [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) element członkowski danych.  
  
##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags  
 Pobiera zestaw flag, które wpływają na zachowanie okna dialogowego.  
  
```  
UINT GetFlags() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zestaw flag, które wpływają na zachowanie okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda pobiera wartość `uiFlags` parametr przekazany do konstruktora. Zwracana wartość może być co najmniej jeden z następujących wartości:  
  
 `AFX_CUSTOMIZE_MENU_SHADOWS`  
 Umożliwia użytkownikowi określenie wyglądu tle menu.  
  
 `AFX_CUSTOMIZE_TEXT_LABELS`  
 Umożliwia użytkownikowi określenie, czy tekst etykiety są pokazywane poniżej obrazy dla przycisków paska narzędzi.  
  
 `AFX_CUSTOMIZE_MENU_ANIMATIONS`  
 Umożliwia użytkownikowi określenie stylu animacji menu.  
  
 `AFX_CUSTOMIZE_NOHELP`  
 Usuwa przycisk Pomoc w oknie dialogowym dostosowywania.  
  
 `AFX_CUSTOMIZE_CONTEXT_HELP`  
 Włącza `WS_EX_CONTEXTHELP` stylu wizualnego.  
  
 `AFX_CUSTOMIZE_NOTOOLS`  
 Usuwa **narzędzia** strony w oknie dialogowym dostosowywania. Ta flaga jest nieprawidłowy, jeśli aplikacja używa `CUserToolsManager` klasy.  
  
 `AFX_CUSTOMIZE_MENUAMPERS`  
 Umożliwia przycisk podpisów zawiera znak ampersand ( **&**) znaków.  
  
 `AFX_CUSTOMIZE_NO_LARGE_ICONS`  
 Usuwa **duże ikony** opcji w oknie dialogowym dostosowywania.  
  
 Aby uzyskać więcej informacji na temat `WS_EX_CONTEXTHELP` stylu wizualnego, zobacz [rozszerzone Style okna](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool  
 Zmiany w narzędziu użytkownika odpowiada bezpośrednio po jego wystąpieniu.  
  
```  
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out] `pSelTool`  
 Wskaźnik do obiektu narzędzia użytkownika, który został zmieniony.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik zmienia właściwości narzędzia zdefiniowane przez użytkownika. Domyślna implementacja nie działa. Należy przesłonić tę metodę w klasie pochodnej z `CMFCToolBarsCustomizeDialog` przeprowadzić przetwarzania po zmianie do narzędzia użytkownika.  
  
##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey  
 Weryfikuje skróty klawiaturowe, jak zdefiniowane przez użytkownika.  
  
```  
virtual BOOL OnAssignKey(ACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out] `pAccel`  
 Wskaźnik do klawiatury proponowanych przypisania Active Directory, które są jest wyrażone jako [AKCELERACJA](http://msdn.microsoft.com/library/windows/desktop/ms646340) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli można przypisywać klucza, lub `FALSE` Jeśli klucz nie może być przypisana. Domyślna implementacja zawsze zwraca `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w klasie pochodnej przeprowadzać dodatkowe przetwarzania, gdy użytkownik przypisuje nowy skrót klawiaturowy, lub do sprawdzania poprawności skróty klawiaturowe w imieniu użytkownika definiuje je. Aby zapobiec przypisywaniu skrót, zwróć `FALSE`. Należy również wyświetlać okno komunikatu lub inny sposób poinformowania użytkownika przyczyny, dlaczego skrót klawiaturowy został odrzucony.  
  
##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool  
 Wykonuje niestandardowych przetwarzania, gdy zmiana narzędzia użytkownika, gdy użytkownik ma zastosować zmiany.  
  
```  
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out] `pSelTool`  
 Wskaźnik do obiektu narzędzia użytkownika, który ma zostać zastąpiony.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy właściwości narzędzia zdefiniowane przez użytkownika ma zostać zmieniona. Domyślna implementacja nie działa. Zastąpienie `OnBeforeChangeTool` metodę w klasie pochodnej z `CMFCToolBarsCustomizeDialog` Jeśli chcesz wykonać przetwarzania, zanim nastąpi zmiana narzędzia użytkownika, takie jak zwolnienie zasobów który `pSelTool` używa.  
  
##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage  
 Zostanie uruchomiony Edytor obrazów, dzięki czemu użytkownik może dostosować ikony elementu menu lub przycisku paska narzędzi.  
  
```  
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,  
    CBitmap& bitmap,  
    int nBitsPerPixel);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pWndParent`  
 Wskaźnik do okna nadrzędnego.  
  
 [in] `bitmap`  
 Odwołanie do obiektu bitmap do edycji.  
  
 [in] `nBitsPerPixel`  
 Bitmap rozdzielczość kolorów w bitów na piksel.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli zmiana zatwierdzania; w przeciwnym razie `FALSE`. Domyślna implementacja Wyświetla okno dialogowe i zwraca `TRUE` gdy użytkownik kliknie **OK**, lub `FALSE` gdy użytkownik kliknie **anulować** lub **Zamknij** przycisk.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik uruchomi edytora obrazów. Wyświetla implementacji domyślnej [klasy CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md) okno dialogowe. Zastąpienie `OnEditToolbarMenuImage` w klasie pochodnej, aby użyć edytora niestandardowego obrazu.  
  
##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog  
 Zastąpienia, aby rozszerzyć inicjowanie arkusza właściwości.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyniku wywołania metody [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), wyświetlając **Zamknij** przycisku, upewniając się, że okno dialogowe pasuje do bieżącego rozmiaru ekranu i przenosząc **Pomocy** przycisk, aby lewym dolnym rogu okna dialogowego.  
  
##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage  
 Obsługuje powiadomienia w ramach którego **narzędzia** strony ma być zainicjowany.  
  
```  
virtual void OnInitToolsPage();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa. Zastępuje tę metodę w klasie pochodnej do przetworzenia tego powiadomienia.  
  
##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy  
 Wywoływane przez platformę po zniszczeniu okna.  
  
```  
virtual void PostNcDestroy();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem implementacji klasy podstawowej `CPropertySheet::PostNcDestroy`, przywracając aplikacji do poprzedniego trybu.  
  
 [CMFCToolBarsCustomizeDialog::Create](#create) metody umieszcza aplikacji w specjalnym trybie, która ogranicza użytkownikowi zadań dostosowania.  
  
##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton  
 Usuwa element button z polecenie o określonym identyfikatorze z określonej kategorii lub z wszystkich kategorii.  
  
```  
int RemoveButton(
    UINT uiCategoryId,  
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,  
    UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCategoryId`  
 Określa identyfikator kategorii, z którego mają zostać usunięte przycisku.  
  
 [in] `uiCmdId`  
 Określa identyfikator polecenia przycisku.  
  
 [in] `lpszCategory`  
 Określa nazwę kategorii, z którego mają zostać usunięte przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks przycisk usunięty lub -1, jeśli polecenie o określonym identyfikatorze nie został znaleziony w wybranej kategorii. Jeśli `uiCategoryId` -1, jest zwracana wartość wynosi 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby usunąć przycisk z wszystkich kategorii, wywołaj metodę pierwszy przeciążenia tej metody lub zestawu `uiCategoryId` -1.  
  
##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory  
 Zmienia nazwę kategorii w polu listy kategorii na **polecenia** strony.  
  
```  
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,  
    LPCTSTR lpszCategoryNew);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszCategoryOld`  
 Nazwa kategorii, aby zmienić.  
  
 [in] `lpszCategoryNew`  
 Nowa nazwa kategorii.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa kategorii musi być unikatowa.  
  
##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton  
 Zastępuje przycisku paska narzędzi w polu listy poleceń na **polecenia** strony.  
  
```  
void ReplaceButton(
    UINT uiCmd,  
    const CMFCToolBarButton& button);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmd`  
 Określa polecenie przycisku mają zostać zastąpione.  
  
 [in] `button`  
 A `const` odwołanie do obiektu przycisku paska narzędzi, który zastępuje stary przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), lub [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) dodaje polecenie **polecenia** strony, że polecenie jest w formie [klasy CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu (lub [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu do menu element zawierający podmenu dodane przez `AddMenuCommands`). Struktura wywołuje również tych trzech metod, aby automatycznie dodać polecenia. Polecenie może być reprezentowana przez typ pochodny zamiast tego należy wywołać `ReplaceButton` i podaj przycisku typu pochodnego.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `ReplaceButton` metoda `CMFCToolBarsCustomizeDialog` klasy. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]  
  
##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory  
 Określa, które kategorii z listy Kategorie na **polecenia** strona jest kategorii użytkownika. Tej funkcji należy wywołać przed wywołaniem [CMFCToolBarsCustomizeDialog::Create](#create).  
  
```  
BOOL SetUserCategory(LPCTSTR lpszCategory);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszCategory`  
 Nazwa kategorii.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienie kategorii użytkownika nie jest obecnie używany przez platformę.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)
