---
title: Klasa CMFCToolBarsCustomizeDialog
ms.date: 11/04/2016
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
ms.openlocfilehash: 026c7392c3eb93b37a712059939683e3e0ab852c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628999"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Klasa CMFCToolBarsCustomizeDialog

Zakładka niemodalne okno dialogowe ( [klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)), który umożliwia użytkownikowi dostosowywanie pasków narzędzi, menu, skrótów klawiaturowych, narzędzi zdefiniowanych przez użytkownika i stylu wizualnego w aplikacji. Zazwyczaj użytkownik uzyskuje dostęp do tego okna dialogowego wybierając **Dostosuj** z **narzędzia** menu.

**Dostosuj** okno dialogowe zawiera sześć kart: **polecenia**, **pasków narzędzi**, **narzędzia**, **klawiatury**,  **Menu**, i **opcje**.

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
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Wstawia listę poleceń przycisku paska narzędzi na **polecenia** strony|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) Aby dodać menu do listy poleceń na **polecenia** strony.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) Aby dodać menu do listy poleceń na **polecenia** strony.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Ładuje pasek narzędzi z zasobów. Następnie dla każdego polecenia w wywołaniach menu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby wstawić przycisk na liście poleceń na **polecenia** strony z określonej kategorii.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::Create](#create)|Wyświetla **dostosowywania** okno dialogowe.|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Zarezerwowane do użytku w przyszłości.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars](#enableuserdefinedtoolbars)|Włącza lub wyłącza tworzenie nowych pasków narzędzi za pomocą **Dostosuj** okno dialogowe.|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Wypełnia podane `CListBox` obiektu za pomocą poleceń w **wszystkie polecenia** kategorii.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Wypełnia podane `CComboBox` obiekt o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Wypełnia podane `CListBox` obiekt o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Pobiera nazwę, który jest skojarzony z identyfikatora polecenia.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Pobiera liczbę elementów na podanej liście, które mają dany tekst etykiety.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Pobiera zestaw flag, które mają wpływ na zachowanie okna dialogowego.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Uruchamia edytora obrazów, dzięki czemu użytkownik może dostosować ikony elementu menu lub przycisku paska narzędzi.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Zastępuje rozszerzyć inicjowanie arkusza właściwości. (Przesłania [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Wywoływane przez platformę po zniszczeniu okna. (Przesłania `CPropertySheet::PostNcDestroy`).|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Usuwa przycisk, polecenie o określonym identyfikatorze z określonej kategorii lub z wszystkich kategorii.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory)|Zmienia nazwę kategorii, w polu listy kategorii na **polecenia** kartę.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Zastępuje przycisku w listę poleceń na **polecenia** karty z nowy obiekt przycisku paska narzędzi.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::SetUserCategory](#setusercategory)|Dodaje kategorię do listy kategorii, które będą wyświetlane na **polecenia** kartę.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Metoda wywoływana przez platformę, aby określić, czy lista narzędzi zdefiniowane przez użytkownika jest prawidłowa.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Wywoływane przez platformę, gdy zmienią się właściwości narzędzia zdefiniowanego przez użytkownika.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Określa, czy określony skrót klawiaturowy można przypisać do akcji.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Określa, czy narzędzia zdefiniowanego przez użytkownika może zostać zmieniony.|
|`CMFCToolBarsCustomizeDialog::` [CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Wywoływane przez platformę, gdy użytkownik wybierze **narzędzia** karty jest wymagane.|

## <a name="remarks"></a>Uwagi

Aby wyświetlić **Dostosuj** okna dialogowego Utwórz `CMFCToolBarsCustomizeDialog` obiektu, a następnie wywołać [CMFCToolBarsCustomizeDialog::Create](#create) metody.

Gdy **Dostosuj** okno dialogowe jest aktywne, aplikacja działa w specjalnym trybie, który ogranicza użytkownikowi zadań dostosowywania.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCToolBarsCustomizeDialog` klasy. W przykładzie pokazano, jak zastąpić przycisku paska narzędzi, w polu listy poleceń na **polecenia** strony, należy włączyć tworzenie nowych pasków narzędzi za pomocą **Dostosuj** okno dialogowe i wyświetlanie  **Dostosowywanie** okno dialogowe. Ten fragment kodu jest częścią [próbka IE Demo](../../visual-cpp-samples.md).

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

Wstawia listę poleceń przycisku paska narzędzi na **polecenia** strony.

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

*uiCategoryId*<br/>
[in] Określa identyfikator kategorii, do której mają zostać wstawione przycisku.

*button*<br/>
[in] Określa przycisk, aby wstawić.

*iInsertBefore*<br/>
[in] Określa liczony od zera indeks przycisku paska narzędzi, przed którym zostanie wstawiony przycisku.

*lpszCategory*<br/>
[in] Określa ciąg kategorii, aby wstawić przycisku.

### <a name="remarks"></a>Uwagi

`AddButton` Metoda ignoruje przycisków, które mają identyfikatory poleceń standardowych (takich jak ID_FILE_MRU_FILE1), polecenia, które nie są dozwolone (zobacz [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) i fikcyjny przycisków.

Ta metoda tworzy nowy obiekt tego samego typu co `button` (zazwyczaj [klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)) za pomocą klasy środowiska uruchomieniowego przycisku. Następnie wywołuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) można skopiować elementów członkowskich danych przycisku i wstawia kopii do określonej kategorii.

Po wstawieniu nowy przycisk odbiera `OnAddToCustomizePage` powiadomień.

Jeśli `iInsertBefore` wynosi -1, ten przycisk jest dołączany do listy kategorii; w przeciwnym razie zostanie ona wstawiona przed elementem o określonym indeksie.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `AddButton` metody `CMFCToolBarsCustomizeDialog` klasy. Ten fragment kodu jest częścią [przykładowe suwaka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>  CMFCToolBarsCustomizeDialog::AddMenu

Ładuje menu z zasobów i wywołania [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands) Aby dodać menu do listy poleceń na **polecenia** strony.

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*uiMenuResId*<br/>
[in] Określa identyfikator zasobu menu do załadowania.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli menu został dodany pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

W wywołaniu `AddMenuCommands`, *bPopup* ma wartość FALSE. W wyniku tej metody nie można dodać elementów menu, które zawierają podmenu do listy poleceń. Ta metoda Dodawanie elementów menu w podmenu, do listy poleceń.

##  <a name="addmenucommands"></a>  CMFCToolBarsCustomizeDialog::AddMenuCommands

Dodaje element do listy poleceń w **polecenia** stronę, aby oznaczyć wszystkie elementy określonego menu.

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[in] Wskaźnik do obiektu CMenu do dodania.

*bPopup*<br/>
[in] Określa, czy do wstawienia elementów menu podręcznego do listy poleceń.

*lpszCategory*<br/>
[in] Nazwa kategorii, aby wstawić menu.

*lpszMenuPath*<br/>
[in] Prefiks, który jest dodawany do nazwy, gdy polecenie jest wyświetlany w **wszystkie kategorie** listy.

### <a name="remarks"></a>Uwagi

`AddMenuCommands` Metoda wykonuje wszystkie elementy menu *pMenu*. Dla każdego elementu menu, który nie zawiera podmenu, ta metoda tworzy [klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektów i wywołuje [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby dodać element menu jako paska narzędzi znajdujący się na liście poleceń na **polecenia** strony. Separatory są ignorowane w ramach tego procesu.

Jeśli *bPopup* ma wartość TRUE, dla każdego elementu menu, który zawiera podmenu ta metoda tworzy [klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu i wstawia ją listę poleceń, wywołując `AddButton`. W przeciwnym razie elementy menu, które zawierają podmenu nie są wyświetlane na liście poleceń. W obu przypadkach gdy `AddMenuCommands` napotka element menu z podmenu wywołuje sam cyklicznie, przekazywania wskaźnika do podmenu jako *pMenu* parametr i dołączanie etykiety podmenu *lpszMenuPath*.

##  <a name="addtoolbar"></a>  CMFCToolBarsCustomizeDialog::AddToolBar

Ładuje pasek narzędzi z zasobów. Następnie dla każdego polecenia w wywołaniach menu [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metodę, aby wstawić przycisk na liście poleceń na **polecenia** strony z określonej kategorii.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Parametry

*uiCategoryId*<br/>
[in] Określa identyfikator zasobu należącego do kategorii narzędzi, aby dodać.

*uiToolbarResId*<br/>
[in] Określa identyfikator zasobu paska narzędzi, w której polecenia są wstawiane do listy poleceń.

*lpszCategory*<br/>
[in] Określa nazwę kategorii, do której mają zostać dodane na pasku narzędzi.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `AddToolBar` method in Class metoda `CMFCToolBarsCustomizeDialog` klasy. Ten fragment kodu jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Uwagi

Formant, który jest używany do reprezentowania każde polecenie jest [klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu. Po dodaniu pasek narzędzi, przycisk można zastąpić za pomocą kontrolki pochodnego typu przez wywołanie metody [CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

##  <a name="checktoolsvalidity"></a>  CMFCToolBarsCustomizeDialog::CheckToolsValidity

Sprawdza poprawność lista narzędzi użytkownika.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parametry

*lstTools*<br/>
[in] Lista narzędzia zdefiniowane przez użytkownika, aby sprawdzić.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista narzędzi zdefiniowane przez użytkownika jest prawidłowy; w przeciwnym razie wartość FALSE. Domyślna implementacja zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby Sprawdź poprawność obiekty reprezentujące narzędzia zdefiniowane przez użytkownika, zwracany przez [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Zastąp `CheckToolsValidity` metodę w klasie pochodnej od `CMFCToolBarsCustomizeDialog` Jeśli chcesz zweryfikować narzędzi użytkownika, zanim użytkownik zamknie okno dialogowe. Jeśli ta metoda zwraca wartość FALSE, gdy użytkownik kliknie albo **Zamknij** przycisk w prawym górnym rogu okna dialogowego lub przycisk **Zamknij** w prawym dolnym rogu okna dialogowego, okno dialogowe Wyświetla **narzędzia** kartę, a nie zamknięcia. Jeśli ta metoda zwraca wartość FALSE, gdy użytkownik kliknie kartę, aby przejść od **narzędzia** karcie nawigacji nie występuje. Powinny pojawić się okno odpowiedni komunikat, aby poinformować użytkownika o problemie, który spowodował niepowodzenie sprawdzania poprawności.

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

*pWndParentFrame*<br/>
[in] Wskaźnik do ramki nadrzędnej. Ten parametr nie może być równa NULL.

*bAutoSetFromMenus*<br/>
[in] Wartość logiczna określająca, czy dodać polecenia menu ze wszystkich menu do listy poleceń na **polecenia** strony. Jeśli ten parametr ma wartość TRUE, polecenia menu są dodawane. W przeciwnym razie nie zostaną dodane poleceń menu.

*uiFlags*<br/>
[in] Kombinacja flag, które mają wpływ na zachowanie okna dialogowego. Ten parametr może być co najmniej jeden z następujących wartości:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
[in] Wskaźnik na listę `CRuntimeClass` obiekty, które określają dodatkowe strony niestandardowe.

### <a name="remarks"></a>Uwagi

*PlistCustomPages* parametr odnosi się do listy `CRuntimeClass` obiekty, które określają dodatkowe strony niestandardowe. Konstruktor dodaje dodatkowe strony do okna dialogowego za pomocą [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) metody. Zobacz przykładową CustomPages, aby uzyskać przykład, który dodaje więcej stron, które mają **Dostosuj** okno dialogowe.

Aby uzyskać więcej informacji na temat wartości, które można przekazać *uiFlags* parametrów, zobacz [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCToolBarsCustomizeDialog` klasy. Ten fragment kodu jest częścią [przykładowe niestandardowych stron](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>  CMFCToolBarsCustomizeDialog::Create

Wyświetla **dostosowywania** okno dialogowe.

```
virtual BOOL Create();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli arkusz właściwości dostosowywania został utworzony pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj `Create` metody tylko wtedy, gdy pełne zainicjowanie klasy.

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

Włącza lub wyłącza tworzenie nowych pasków narzędzi za pomocą **Dostosuj** okno dialogowe.

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby włączyć paskach narzędzi zdefiniowane przez użytkownika; Wartość FALSE umożliwia wyłączenie paski narzędzi.

### <a name="remarks"></a>Uwagi

Jeśli *bWłączenie* ma wartość PRAWDA, **New**, **Zmień nazwę** i **Usuń** przyciski są wyświetlane na **pasków narzędzi** Strona.

Domyślnie lub jeśli *bWłączenie* ma wartość FAŁSZ, przyciski te nie będą wyświetlane, użytkownik nie może definiować nowych pasków narzędzi.

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

Wypełnia podane `CListBox` obiektu za pomocą poleceń w **wszystkie polecenia** kategorii.

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parametry

*wndListOfCommands*<br/>
[out] Odwołanie do `CListBox` obiekt do wypełnienia.

### <a name="remarks"></a>Uwagi

**Wszystkie polecenia** kategoria zawiera polecenia wszystkich kategorii. [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda dodaje polecenia, który jest skojarzony z podanych przycisk, aby **wszystkie polecenia** kategorii dla Ciebie.

Ta metoda usuwa zawartość dostarczonego `CListBox` obiektu przed zapełnianie poleceń w **wszystkie polecenia** kategorii.

`CMFCMousePropertyPage` Klasa używa tej metody do wypełnienia pola listy kliknij dwukrotnie zdarzenie.

##  <a name="fillcategoriescombobox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Wypełnia podane `CComboBox` obiekt o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
[out] Odwołanie do `CComboBox` obiekt do wypełnienia.

*bAddEmpty*<br/>
[in] Wartość logiczna określająca, czy do dodawania kategorii do pola kombi, które nie mają poleceń. Jeśli ten parametr ma wartość TRUE, puste kategorie są dodawane do pola kombi. W przeciwnym razie puste kategorie, nie są dodawane.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) metody z tą różnicą, że ta metoda działa z `CComboBox` obiektu.

Ta metoda nie czyści zawartość `CComboBox` obiekt przed jego wypełnianie. Gwarantuje, że **wszystkie polecenia** kategorii jest ostatnim elementem w polu kombi.

Można dodać nowe kategorie polecenia za pomocą [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Można zmienić nazwę istniejącej kategorii, używając [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.

`CMFCToolBarsKeyboardPropertyPage` i `CMFCKeyMapDialog` klasy ta metoda umożliwia klasyfikowanie mapowania klawiatury.

##  <a name="fillcategorieslistbox"></a>  CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Wypełnia podane `CListBox` obiekt o nazwie każdej kategorii polecenia w **Dostosuj** okno dialogowe.

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wndCategory*<br/>
[out] Odwołanie do `CListBox` obiekt do wypełnienia.

*bAddEmpty*<br/>
[in] Wartość logiczna określająca, czy do dodawania kategorii do pola listy, który nie ma polecenia. Jeśli ten parametr ma wartość TRUE, puste kategorie są dodawane do pola listy. W przeciwnym razie puste kategorie, nie są dodawane.

### <a name="remarks"></a>Uwagi

Ta metoda przypomina [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) metody z tą różnicą, że ta metoda działa z `CListBox` obiektu.

Ta metoda nie czyści zawartość `CListBox` obiekt przed jego wypełnianie. Gwarantuje, że **wszystkie polecenia** kategorii jest ostatnim elementem w polu listy.

Można dodać nowe kategorie polecenia za pomocą [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody. Można zmienić nazwę istniejącej kategorii, używając [CMFCToolBarsCustomizeDialog::RenameCategory](#renamecategory) metody.

`CMFCToolBarsCommandsPropertyPage` Klasa używa tej metody, aby wyświetlić listę poleceń, który jest skojarzony z każdej kategorii polecenia.

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

Pobiera nazwę, który jest skojarzony z identyfikatora polecenia.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Identyfikator polecenia do pobrania.

### <a name="return-value"></a>Wartość zwracana

Nazwa która jest skojarzony z Identyfikatorem polecenia, lub wartość NULL, jeśli polecenie nie istnieje.

##  <a name="getcountincategory"></a>  CMFCToolBarsCustomizeDialog::GetCountInCategory

Pobiera liczbę elementów na podanej liście, które mają dany tekst etykiety.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
[in] Etykieta tekstowa do dopasowania.

*lstCommands*<br/>
[in] Odwołanie do listy, która zawiera `CMFCToolBarButton` obiektów.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w określonych listy którego tekst etykiety equals *lpszItemName*.

### <a name="remarks"></a>Uwagi

Każdy element na liście udostępnionego obiektu musi być typu `CMFCToolBarButton`. Ta metoda porównuje *lpszItemName* z [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) element członkowski danych.

##  <a name="getflags"></a>  CMFCToolBarsCustomizeDialog::GetFlags

Pobiera zestaw flag, które mają wpływ na zachowanie okna dialogowego.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Wartość zwracana

Zestaw flag, które mają wpływ na zachowanie okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera wartość *uiFlags* parametr, który jest przekazywany do konstruktora. Zwracana wartość może być co najmniej jeden z następujących wartości:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Zezwala użytkownikowi na określenie wyglądu w tle menu.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Zezwala użytkownikowi na określenie, czy etykiety tekstowe są wyświetlane poniżej obrazy przycisków paska narzędzi.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Zezwala użytkownikowi na określenie stylu animacji menu.  |
|AFX_CUSTOMIZE_NOHELP|Usuwa przycisk Pomoc w oknie dialogowym dostosowywania.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Umożliwia WS_EX_CONTEXTHELP stylu wizualnego.  |
|AFX_CUSTOMIZE_NOTOOLS|Usuwa **narzędzia** strony w oknie dialogowym dostosowywania. Ta flaga jest prawidłowy, jeśli aplikacja używa `CUserToolsManager` klasy.  |
|AFX_CUSTOMIZE_MENUAMPERS|Zezwala na podpisy przycisk ma zawierać handlowe "i" ( **&**) znaków.  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Usuwa **duże ikony** opcji w oknie dialogowym dostosowywania.  |

Aby uzyskać więcej informacji na temat stylu wizualnego WS_EX_CONTEXTHELP zobacz [rozszerzone Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Reaguje na zmiany w narzędziu do użytkownika, bezpośrednio po jego wystąpieniu.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[out w] Wskaźnik do obiektu narzędzia użytkownika, który został zmieniony.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy użytkownik zmienia właściwości narzędzia zdefiniowanego przez użytkownika. Domyślna implementacja nic nie robi. Należy przesłonić tę metodę w klasie pochodnej od `CMFCToolBarsCustomizeDialog` do wykonywania przetwarzania po wystąpieniu zmiany narzędzie użytkownika.

##  <a name="onassignkey"></a>  CMFCToolBarsCustomizeDialog::OnAssignKey

Weryfikuje skróty klawiaturowe, jak zdefiniowane przez użytkownika.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*pAccel*<br/>
[out w] Wskaźnik do przypisania proponowaną klawiatury, które są jest wyrażone jako [AKCELERACJA](/windows/desktop/api/winuser/ns-winuser-tagaccel) struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli klucz może być przypisane, lub FAŁSZ, jeśli klucz nie może być przypisany. Domyślna implementacja zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę w klasie pochodnej, aby wykonać dodatkowe przetwarzanie, gdy użytkownik przypisuje nowy skrót klawiaturowy, lub do sprawdzania poprawności skróty klawiaturowe, jak użytkownik je definiuje. Aby zapobiec sytuacji, w której skrót jest przypisany, zwróć wartość FALSE. Należy również wyświetlić okno komunikatu lub w przeciwnym razie poinformowania użytkownika o powód, dlaczego skrót klawiaturowy został odrzucony.

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Wykonuje niestandardowe przetwarzanie, gdy zmiana narzędzie użytkownika po użytkownik ma zastosować zmiany.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool*<br/>
[out w] Wskaźnik do obiektu narzędzia użytkownika, który ma zostać zastąpiony.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy właściwości narzędzia zdefiniowanego przez użytkownika ma zostać zmieniona. Domyślna implementacja nic nie robi. Zastąp `OnBeforeChangeTool` metodę w klasie pochodnej od `CMFCToolBarsCustomizeDialog` Jeśli chcesz wykonać przetwarzanie, zanim nastąpi zmiana narzędzie użytkownika, np. przy zwalnianiu zasobów, *pSelTool* używa.

##  <a name="onedittoolbarmenuimage"></a>  CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Uruchamia edytora obrazów, dzięki czemu użytkownik może dostosować ikony elementu menu lub przycisku paska narzędzi.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego.

*Mapy bitowej*<br/>
[in] Odwołanie do obiektu mapy bitowej do edycji.

*nBitsPerPixel*<br/>
[in] Mapa bitowa rozdzielczość koloru, w bitów na piksel.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli Zatwierdzanie zmian; w przeciwnym razie wartość FALSE. Domyślna implementacja wyświetlane jest okno dialogowe i zwraca wartość TRUE, jeśli użytkownik kliknie **OK**, lub FAŁSZ, jeśli użytkownik kliknie **anulować** lub **Zamknij** przycisku.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy użytkownik uruchomi edytora obrazów. Wyświetla implementacji domyślnej [klasa CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md) okno dialogowe. Zastąp `OnEditToolbarMenuImage` w klasie pochodnej, aby użyć edytora obrazu niestandardowego.

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

Zastępuje rozszerzyć inicjowanie arkusza właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Wynik wywołania metody [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) metody.

### <a name="remarks"></a>Uwagi

Ta metoda jest rozszerzeniem implementacji klasy podstawowej [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), wyświetlając **Zamknij** przycisku, upewniając się, że okno dialogowe pasuje do bieżącego rozmiaru ekranu i przenosząc **Pomocy** przycisk, aby w lewym dolnym rogu okna dialogowego.

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

Obsługuje powiadomienia w ramach którego **narzędzia** strona ma być zainicjowany.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Należy przesłonić tę metodę w klasie pochodnej, aby przetworzyć to powiadomienie.

##  <a name="postncdestroy"></a>  CMFCToolBarsCustomizeDialog::PostNcDestroy

Wywoływane przez platformę po zniszczeniu okna.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest rozszerzeniem implementacji klasy podstawowej `CPropertySheet::PostNcDestroy`, przez przywrócenie aplikacji do poprzedniego trybu.

[CMFCToolBarsCustomizeDialog::Create](#create) metoda umieszcza ją w specjalnym trybie, który ogranicza użytkownikowi zadań dostosowywania.

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

Usuwa przycisk, polecenie o określonym identyfikatorze z określonej kategorii lub z wszystkich kategorii.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCategoryId*<br/>
[in] Określa identyfikator kategorii, z którego mają zostać usunięte przycisku.

*uiCmdId*<br/>
[in] Określa identyfikator przycisku polecenia.

*lpszCategory*<br/>
[in] Określa nazwę kategorii, z którego mają zostać usunięte przycisku.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks przycisku usuniętych lub -1, jeśli polecenie o określonym identyfikatorze nie został znaleziony w określonej kategorii. Jeśli *uiCategoryId* wynosi -1, wartość zwracana to 0.

### <a name="remarks"></a>Uwagi

Aby usunąć przycisk z wszystkich kategorii, należy wywołać pierwsze przeciążenie tę metodę i zestaw *uiCategoryId* na -1.

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

Zmienia nazwę kategorii, w polu listy kategorii na **polecenia** strony.

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parametry

*lpszCategoryOld*<br/>
[in] Nazwa kategorii, aby zmienić.

*lpszCategoryNew*<br/>
[in] Nowa nazwa kategorii.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Nazwa kategorii musi być unikatowa.

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

Zastępuje przycisku paska narzędzi, w polu listy poleceń na **polecenia** strony.

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
[in] Określa polecenie przycisku, które ma zostać zastąpione.

*button*<br/>
[in] A **const** odwołanie do obiektu przycisku paska narzędzi, który zastępuje stare przycisku.

### <a name="remarks"></a>Uwagi

Gdy [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands), lub [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) dodaje polecenie **polecenia** strony, że polecenie jest w formie [klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu (lub [klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) obiektu do menu element, który zawiera podmenu dodane przez `AddMenuCommands`). Struktura wywołuje również te trzy metody, aby automatycznie dodać polecenia. Polecenie może być reprezentowana przez typ pochodny, zamiast tego należy wywołać `ReplaceButton` i przekazać przycisku typu pochodnego.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `ReplaceButton` method in Class metoda `CMFCToolBarsCustomizeDialog` klasy. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>  CMFCToolBarsCustomizeDialog::SetUserCategory

Określa, w jakiej kategorii na liście kategorii **polecenia** strona jest kategorii użytkownika. Musisz wywołać tę funkcję, zanim wywołasz [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parametry

*lpszCategory*<br/>
[in] Nazwa kategorii.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ustawienie kategorii użytkownika nie jest obecnie używany przez platformę.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)
