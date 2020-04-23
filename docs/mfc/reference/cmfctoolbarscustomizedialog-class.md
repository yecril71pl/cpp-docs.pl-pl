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
ms.openlocfilehash: 29e2c3d0238ac5a084ea916d95ad953f8c4aedce
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753400"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>Klasa CMFCToolBarsCustomizeDialog

Okno dialogowe karty trybu [(CPropertySheet Class),](../../mfc/reference/cpropertysheet-class.md)które umożliwia użytkownikowi dostosowanie pasków narzędzi, menu, skrótów klawiaturowych, narzędzi zdefiniowanych przez użytkownika i stylu wizualnego w aplikacji. Zazwyczaj użytkownik uzyskuje dostęp do tego okna dialogowego, wybierając **polecenie Dostosuj** z menu **Narzędzia.**

Okno dialogowe **Dostosowywanie** zawiera sześć kart: **Polecenia,** **Paski narzędzi,** **Narzędzia,** **Klawiatura,** **Menu**i **Opcje**.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|Konstruuje `CMFCToolBarsCustomizeDialog` obiekt.|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::AddButton](#addbutton)|Wstawia przycisk paska narzędzi do listy poleceń na stronie **Polecenia**|
|[CMFCToolBarsCustomizeDialog::AddMenu](#addmenu)|Ładuje menu z zasobów i wywołuje [CMFCToolBarsCustomizeDialog::AddMenuCommands,](#addmenucommands) aby dodać to menu do listy poleceń na stronie **Polecenia.**|
|[CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)|Ładuje menu z zasobów i wywołuje [CMFCToolBarsCustomizeDialog::AddMenuCommands,](#addmenucommands) aby dodać to menu do listy poleceń na stronie **Polecenia.**|
|[CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar)|Ładuje pasek narzędzi z zasobów. Następnie dla każdego polecenia w menu wywołuje [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody wstawić przycisk na liście poleceń na polecenia **strony** w określonej kategorii.|
|[CMFCToolBarsCustomizeDialog::Tworzenie](#create)|Wyświetla okno dialogowe **Dostosowywanie.**|
|`CMFCToolBarsCustomizeDialog::EnableTools`|Zarezerwowane do użytku w przyszłości.|
|[CMFCToolBarsCustomizeDialog::EnableUserDedefdefdefedToolbars](#enableuserdefinedtoolbars)|Włącza lub wyłącza tworzenie nowych pasków narzędzi za pomocą okna dialogowego **Dostosowywanie.**|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|Wypełnia podany `CListBox` obiekt poleceniami w kategorii **Wszystkie polecenia.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox)|Wypełnia podany `CComboBox` obiekt nazwą każdej kategorii poleceń w oknie dialogowym **Dostosowywanie.**|
|[CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox)|Wypełnia podany `CListBox` obiekt nazwą każdej kategorii poleceń w oknie dialogowym **Dostosowywanie.**|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|Pobiera nazwę skojarzoną z podanym identyfikatorem polecenia.|
|[CMFCToolBarsCustomizeDialog::GetCountInCategory](#getcountincategory)|Pobiera liczbę elementów na podanej liście, które mają daną etykietę tekstową.|
|[CMFCToolBarsCustomizeDialog::GetFlags](#getflags)|Pobiera zestaw flag, które wpływają na zachowanie okna dialogowego.|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage](#onedittoolbarmenuimage)|Uruchamia edytor obrazów, aby użytkownik mógł dostosować przycisk paska narzędzi lub ikonę elementu menu.|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|Zastępuje, aby zwiększyć inicjowanie arkusza właściwości. (Zastępuje [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCToolBarsCustomizeDialog::PostNcDestroy](#postncdestroy)|Wywoływana przez ramy po okno zostało zniszczone. (Przesłania `CPropertySheet::PostNcDestroy`).|
|[CMFCToolBarsCustomizeDialog::RemoveButton](#removebutton)|Usuwa przycisk o określonym identyfikatorze polecenia z określonej kategorii lub ze wszystkich kategorii.|
|[CMFCToolBarsCustomizeDialog::Zmień nazwę kategorii](#renamecategory)|Zmienia nazwę kategorii w polu listy kategorii na karcie **Polecenia.**|
|[CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton)|Zastępuje przycisk na liście poleceń na karcie **Polecenia** nowym obiektem przycisku paska narzędzi.|
|[CMFCToolBarsCustomizeDialog::SetUser Kategoria](#setusercategory)|Dodaje kategorię do listy kategorii, które będą wyświetlane na karcie **Polecenia.**|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity)|Wywoływane przez strukturę, aby ustalić, czy lista narzędzi zdefiniowanych przez użytkownika jest prawidłowa.|
|[CMFCToolBarsCustomizeDialog::OnAfterChangeTool](#onafterchangetool)|Wywoływane przez strukturę, gdy właściwości narzędzia zdefiniowane przez użytkownika zmiany.|
|[CMFCToolBarsCustomizeDialog::OnAssignKey](#onassignkey)|Określa, czy określony skrót klawiaturowy może być przypisany do akcji.|
|[CMFCToolBarsCustomizeDialog::OnBeforeChangeTool](#onbeforechangetool)|Określa, czy narzędzie zdefiniowane przez użytkownika można zmienić.|
|[CMFCToolBarsCustomizeDialog::OnInitToolsPage](#oninittoolspage)|Wywoływane przez platformę, gdy użytkownik wybiera **narzędzia** karty jest wymagane.|

## <a name="remarks"></a>Uwagi

Aby wyświetlić okno dialogowe `CMFCToolBarsCustomizeDialog` **Dostosowywanie,** utwórz obiekt i wywołaj metodę [CMFCToolBarsCustomizeDialog::Create.](#create)

Gdy okno dialogowe **Dostosowywanie** jest aktywne, aplikacja działa w trybie specjalnym, który ogranicza użytkownika do zadań dostosowywania.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarsCustomizeDialog` używać różnych metod w klasie. W przykładzie pokazano, jak zastąpić przycisk paska narzędzi w polu listy poleceń na stronie **Polecenia,** włączyć tworzenie nowych pasków narzędzi za pomocą okna dialogowego **Dostosowywanie** i wyświetlić okno dialogowe **Dostosowywanie.** Ten fragment kodu jest częścią [przykładu IE Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cpropertysheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxToolBarsCustomizeDialog.h

## <a name="cmfctoolbarscustomizedialogaddbutton"></a><a name="addbutton"></a>CMFCToolBarsCustomizeDialog::AddButton

Wstawia przycisk paska narzędzi do listy poleceń na stronie **Polecenia.**

```cpp
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

*identyfikator kategorii ui*<br/>
[w] Określa identyfikator kategorii, do której ma być wstawiony przycisk.

*Przycisk*<br/>
[w] Określa przycisk do wstawienia.

*iInsertPrzed*<br/>
[w] Określa indeks od zera przycisku paska narzędzi, przed którym jest wstawiany przycisk.

*Kategoria lpsz*<br/>
[w] Określa ciąg kategorii, który ma być wstawiany.

### <a name="remarks"></a>Uwagi

Metoda `AddButton` ignoruje przyciski, które mają standardowe identyfikatory poleceń (takie jak ID_FILE_MRU_FILE1), polecenia, które nie są dozwolone (zobacz [CMFCToolBar::IsCommandPermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted)) i przyciski manekina.

Ta metoda tworzy nowy obiekt tego `button` samego typu co (zwykle [CMFCToolBarButton Klasy)](../../mfc/reference/cmfctoolbarbutton-class.md)przy użyciu klasy runtime przycisku. Następnie wywołuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom) skopiować elementy członkowskie danych przycisku i wstawia kopię do określonej kategorii.

Po włożeniu nowego przycisku otrzymuje `OnAddToCustomizePage` powiadomienie.

Jeśli `iInsertBefore` jest -1, przycisk jest dołączany do listy kategorii; w przeciwnym razie jest wstawiany przed elementem z określonym indeksem.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `AddButton` metody `CMFCToolBarsCustomizeDialog` klasy. Ten fragment kodu jest częścią [slider próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

## <a name="cmfctoolbarscustomizedialogaddmenu"></a><a name="addmenu"></a>CMFCToolBarsCustomizeDialog::AddMenu

Ładuje menu z zasobów i wywołuje [CMFCToolBarsCustomizeDialog::AddMenuCommands,](#addmenucommands) aby dodać to menu do listy poleceń na stronie **Polecenia.**

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiMenuResId*<br/>
[w] Określa identyfikator zasobu menu do załadowania.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli menu zostało dodane pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

W wywołaniu `AddMenuCommands`do , *bPopup* jest FALSE. W rezultacie ta metoda nie dodaje elementów menu, które zawierają podmenu do listy poleceń. Ta metoda dodaje elementy menu w podmenu do listy poleceń.

## <a name="cmfctoolbarscustomizedialogaddmenucommands"></a><a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog::AddMenuCommands

Dodaje elementy do listy poleceń na stronie **Polecenia,** aby reprezentować wszystkie elementy w określonym menu.

```cpp
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>Parametry

*pMenu*<br/>
[w] Wskaźnik do obiektu CMenu do dodania.

*bPopup*<br/>
[w] Określa, czy elementy menu podręcznego mają być wstawiane do listy poleceń.

*Kategoria lpsz*<br/>
[w] Nazwa kategorii, aby wstawić menu.

*lpszMenuPath*<br/>
[w] Prefiks, który jest dodawany do nazwy, gdy polecenie jest wyświetlane na liście **Wszystkie kategorie.**

### <a name="remarks"></a>Uwagi

Metoda `AddMenuCommands` pętli na wszystkich elementów menu *pMenu*. Dla każdego elementu menu, który nie zawiera podmenu, ta metoda tworzy [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu i wywołuje [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody, aby dodać element menu jako przycisk paska narzędzi do listy poleceń na stronie **Polecenia.** Separatory są ignorowane w tym procesie.

Jeśli *bPopup* ma wartość PRAWDA, dla każdego elementu menu zawierającego podmenu ta metoda tworzy obiekt [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) i wstawia go do listy poleceń, wywołując `AddButton`polecenie . W przeciwnym razie elementy menu zawierające podmenu nie są wyświetlane na liście poleceń. W obu przypadkach, `AddMenuCommands` gdy napotka element menu z podmenu wywołuje się cyklicznie, przekazując wskaźnik do podmenu jako parametr *pMenu* i dołączając etykietę podmenu do *lpszMenuPath*.

## <a name="cmfctoolbarscustomizedialogaddtoolbar"></a><a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog::AddToolBar

Ładuje pasek narzędzi z zasobów. Następnie dla każdego polecenia w menu wywołuje [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metody wstawić przycisk na liście poleceń na polecenia **strony** w określonej kategorii.

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>Parametry

*identyfikator kategorii ui*<br/>
[w] Określa identyfikator zasobu kategorii, do który ma być dodawany pasek narzędzi.

*uiToolbarResId*<br/>
[w] Określa identyfikator zasobu paska narzędzi, którego polecenia są wstawiane do listy poleceń.

*Kategoria lpsz*<br/>
[w] Określa nazwę kategorii, do której ma być dodawany pasek narzędzi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `AddToolBar` metody w `CMFCToolBarsCustomizeDialog` klasie. Ten fragment kodu jest częścią [przykładu word pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Uwagi

Formant, który jest używany do reprezentowania każdego polecenia jest [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu. Po dodaniu paska narzędzi można zastąpić przycisk formantem typu pochodnego, wywołując [POLECENIE CMFCToolBarsCustomizeDialog::ReplaceButton](#replacebutton).

## <a name="cmfctoolbarscustomizedialogchecktoolsvalidity"></a><a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog::CheckToolsValidity

Weryfikuje ważność listy narzędzi użytkownika.

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>Parametry

*lstTools*<br/>
[w] Lista narzędzi zdefiniowanych przez użytkownika do sprawdzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli lista narzędzi zdefiniowanych przez użytkownika jest prawidłowa; w przeciwnym razie FALSE. Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, aby sprawdzić ważność obiektów, które reprezentują narzędzia zdefiniowane przez użytkownika zwrócone przez [CMFCToolBarsCustomizeDialog::CheckToolsValidity](#checktoolsvalidity).

Zastąpić `CheckToolsValidity` metodę w klasie `CMFCToolBarsCustomizeDialog` pochodzące z, jeśli chcesz sprawdzić poprawność narzędzi użytkownika, zanim użytkownik zamknie okno dialogowe. Jeśli ta metoda zwraca wartość FAŁSZ, gdy użytkownik kliknie przycisk **Zamknij** w prawym górnym rogu okna dialogowego lub przycisk **Zamknij** w prawym dolnym rogu okna dialogowego, w oknie dialogowym zostanie wyświetlona karta **Narzędzia** zamiast zamykania. Jeśli ta metoda zwraca wartość FAŁSZ, gdy użytkownik kliknie kartę, aby przejść z dala od **narzędzia** kartę, nawigacja nie występuje. Należy wyświetlić odpowiednie okno komunikatu, aby poinformować użytkownika o problemie, który spowodował niepowodzenie sprawdzania poprawności.

## <a name="cmfctoolbarscustomizedialogcmfctoolbarscustomizedialog"></a><a name="cmfctoolbarscustomizedialog"></a>CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

Konstruuje `CMFCToolBarsCustomizeDialog` obiekt.

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>Parametry

*pWndParentFrame*<br/>
[w] Wskaźnik do ramki nadrzędnej. Ten parametr nie może być null.

*bAutoSetFromMenus*<br/>
[w] Wartość logiczna określająca, czy polecenia menu mają być dodane ze wszystkich menu do listy poleceń na stronie **Polecenia.** Jeśli ten parametr ma wartość PRAWDA, dodawane są polecenia menu. W przeciwnym razie polecenia menu nie są dodawane.

*żużle uiFlags*<br/>
[w] Kombinacja flag, które wpływają na zachowanie okna dialogowego. Ten parametr może być jedną lub kilkoma z następujących wartości:

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages (PlistCustomPages)*<br/>
[w] Wskaźnik do listy `CRuntimeClass` obiektów określających dodatkowe strony niestandardowe.

### <a name="remarks"></a>Uwagi

Parametr *plistCustomPages* odnosi się do `CRuntimeClass` listy obiektów, które określają dodatkowe strony niestandardowe. Konstruktor dodaje więcej stron do okna dialogowego przy użyciu [CRuntimeClass::CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject) metody. Zobacz przykład strony niestandardowe, na przykład, który dodaje więcej stron do okna dialogowego **Dostosowywanie.**

Aby uzyskać więcej informacji na temat wartości, które można przekazać w parametrze *uiFlags,* zobacz [CMFCToolBarsCustomizeDialog::GetFlags](#getflags).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarsCustomizeDialog` skonstruować obiekt klasy. Ten fragment kodu jest częścią [przykładu Strony niestandardowe](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

## <a name="cmfctoolbarscustomizedialogcreate"></a><a name="create"></a>CMFCToolBarsCustomizeDialog::Tworzenie

Wyświetla okno dialogowe **Dostosowywanie.**

```
virtual BOOL Create();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli arkusz właściwości dostosowywania został utworzony pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie `Create` metody tylko po pełnym zainicjowaniu klasy.

## <a name="cmfctoolbarscustomizedialogenableuserdefinedtoolbars"></a><a name="enableuserdefinedtoolbars"></a>CMFCToolBarsCustomizeDialog::EnableUserDedefdefdefedToolbars

Włącza lub wyłącza tworzenie nowych pasków narzędzi za pomocą okna dialogowego **Dostosowywanie.**

```cpp
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć paski narzędzi zdefiniowane przez użytkownika; FALSE, aby wyłączyć paski narzędzi.

### <a name="remarks"></a>Uwagi

Jeśli *bEnable* ma wartość PRAWDA, przyciski **Nowy,** **Zmień nazwę** i **Usuń** są wyświetlane na stronie **Paski narzędzi.**

Domyślnie lub jeśli *bEnable* jest FALSE, przyciski te nie są wyświetlane i użytkownik nie może zdefiniować nowe paski narzędzi.

## <a name="cmfctoolbarscustomizedialogfillallcommandslist"></a><a name="fillallcommandslist"></a>CMFCToolBarsCustomizeDialog::FillAllCommandsList

Wypełnia podany `CListBox` obiekt poleceniami w kategorii **Wszystkie polecenia.**

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>Parametry

*wndListOfCommands*<br/>
[na zewnątrz] Odwołanie do `CListBox` obiektu do zapełnienia.

### <a name="remarks"></a>Uwagi

Kategoria **Wszystkie polecenia** zawiera polecenia wszystkich kategorii. [CMFCToolBarsCustomizeDialog::AddButton](#addbutton) metoda dodaje polecenie, które jest skojarzone z podanym przyciskiem do **wszystkich poleceń** kategorii dla Ciebie.

Ta metoda czyści zawartość `CListBox` podanego obiektu przed zapełnieniem go poleceniami w kategorii **Wszystkie polecenia.**

Klasa `CMFCMousePropertyPage` używa tej metody do wypełniania pola listy zdarzeń dwukrotnie.

## <a name="cmfctoolbarscustomizedialogfillcategoriescombobox"></a><a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesComboBox

Wypełnia podany `CComboBox` obiekt nazwą każdej kategorii poleceń w oknie dialogowym **Dostosowywanie.**

```cpp
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wnd Kategoria*<br/>
[na zewnątrz] Odwołanie do `CComboBox` obiektu do zapełnienia.

*bAddEmpty*<br/>
[w] Wartość logiczna określająca, czy do pola kombi mają być dodawanymi kategorie, które nie mają poleceń. Jeśli ten parametr ma wartość PRAWDA, puste kategorie są dodawane do pola kombi. W przeciwnym razie puste kategorie nie są dodawane.

### <a name="remarks"></a>Uwagi

Ta metoda jest jak [CMFCToolBarsCustomizeDialog::FillCategoriesListBox](#fillcategorieslistbox) metody, z `CComboBox` tą różnicą, że ta metoda działa z obiektem.

Ta metoda nie czyści `CComboBox` zawartości obiektu przed jego zapełnieniem. Gwarantuje, że kategoria **Wszystkie polecenia** jest ostatnim elementem w polu kombi.

Nowe kategorie poleceń można dodać za pomocą [metody CMFCToolBarsCustomizeDialog::AddButton.](#addbutton) Nazwę istniejącej kategorii można zmienić za pomocą [metody CMFCToolBarsCustomizeDialog::RenameCategory.](#renamecategory)

Klasy `CMFCToolBarsKeyboardPropertyPage` `CMFCKeyMapDialog` i używają tej metody do kategoryzowania mapowań klawiatury.

## <a name="cmfctoolbarscustomizedialogfillcategorieslistbox"></a><a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog::FillCategoriesListBox

Wypełnia podany `CListBox` obiekt nazwą każdej kategorii poleceń w oknie dialogowym **Dostosowywanie.**

```cpp
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>Parametry

*wnd Kategoria*<br/>
[na zewnątrz] Odwołanie do `CListBox` obiektu do zapełnienia.

*bAddEmpty*<br/>
[w] Wartość logiczna określająca, czy do pola listy mają być dodawanymi kategorie, które nie mają poleceń. Jeśli ten parametr ma wartość PRAWDA, do pola listy są dodawane puste kategorie. W przeciwnym razie puste kategorie nie są dodawane.

### <a name="remarks"></a>Uwagi

Ta metoda jest jak [CMFCToolBarsCustomizeDialog::FillCategoriesComboBox](#fillcategoriescombobox) metody, z `CListBox` tą różnicą, że ta metoda działa z obiektem.

Ta metoda nie czyści `CListBox` zawartości obiektu przed jego zapełnieniem. Gwarantuje, że kategoria **Wszystkie polecenia** jest ostatnim elementem w polu listy.

Nowe kategorie poleceń można dodać za pomocą [metody CMFCToolBarsCustomizeDialog::AddButton.](#addbutton) Nazwę istniejącej kategorii można zmienić za pomocą [metody CMFCToolBarsCustomizeDialog::RenameCategory.](#renamecategory)

Klasa `CMFCToolBarsCommandsPropertyPage` używa tej metody, aby wyświetlić listę poleceń, które są skojarzone z każdej kategorii polecenia.

## <a name="cmfctoolbarscustomizedialoggetcommandname"></a><a name="getcommandname"></a>CMFCToolBarsCustomizeDialog::GetCommandName

Pobiera nazwę skojarzoną z podanym identyfikatorem polecenia.

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia do pobrania.

### <a name="return-value"></a>Wartość zwracana

Nazwa skojarzona z podanym identyfikatorem polecenia lub null, jeśli polecenie nie istnieje.

## <a name="cmfctoolbarscustomizedialoggetcountincategory"></a><a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog::GetCountInCategory

Pobiera liczbę elementów na podanej liście, które mają daną etykietę tekstową.

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
[w] Etykieta tekstowa do dopasowania.

*lstCommands ( lstCommands )*<br/>
[w] Odwołanie do listy zawierającej `CMFCToolBarButton` obiekty.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów na podanej liście, których etykieta tekstowa jest równa *lpszItemName*.

### <a name="remarks"></a>Uwagi

Każdy element na podanej liście `CMFCToolBarButton`obiektów musi być typu . Ta metoda porównuje *lpszItemName* z [cmfctoolbarbutton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext) element członkowski danych.

## <a name="cmfctoolbarscustomizedialoggetflags"></a><a name="getflags"></a>CMFCToolBarsCustomizeDialog::GetFlags

Pobiera zestaw flag, które wpływają na zachowanie okna dialogowego.

```
UINT GetFlags() const;
```

### <a name="return-value"></a>Wartość zwracana

Zestaw flag, które wpływają na zachowanie okna dialogowego.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera wartość *parametru uiFlags,* który jest przekazywany do konstruktora. Zwracana wartość może być jedną lub kilkoma z następujących wartości:

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|Umożliwia użytkownikowi określenie wyglądu cienia menu.  |
|AFX_CUSTOMIZE_TEXT_LABELS|Umożliwia użytkownikowi określenie, czy etykiety tekstowe są wyświetlane pod obrazami przycisków paska narzędzi.  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|Umożliwia użytkownikowi określenie stylu animacji menu.  |
|AFX_CUSTOMIZE_NOHELP|Usuwa przycisk pomocy z okna dialogowego dostosowywania.  |
|AFX_CUSTOMIZE_CONTEXT_HELP|Włącza WS_EX_CONTEXTHELP styl wizualny.  |
|AFX_CUSTOMIZE_NOTOOLS|Usuwa stronę **Narzędzia** z okna dialogowego dostosowywania. Ta flaga jest prawidłowa, `CUserToolsManager` jeśli aplikacja używa klasy.  |
|AFX_CUSTOMIZE_MENUAMPERS|Umożliwia podpisy przycisków zawierają znak **&** ampersand ( ) .  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|Usuwa opcję **Duże ikony** z okna dialogowego dostosowywania.  |

Aby uzyskać więcej informacji na temat WS_EX_CONTEXTHELP stylu wizualnego, zobacz [Style okien rozszerzonych](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="cmfctoolbarscustomizedialogonafterchangetool"></a><a name="onafterchangetool"></a>CMFCToolBarsCustomizeDialog::OnAfterChangeTool

Odpowiada na zmianę w narzędziu użytkownika natychmiast po jej wystąpieniu.

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool (Wesztoko)*<br/>
[w, na zewnątrz] Wskaźnik do obiektu narzędzia użytkownika, który został zmieniony.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy użytkownik zmienia właściwości narzędzia zdefiniowanego przez użytkownika. Domyślna implementacja nic nie robi. Zastąpić tę metodę w `CMFCToolBarsCustomizeDialog` klasie pochodną do wykonywania przetwarzania po zmianie narzędzia użytkownika występuje.

## <a name="cmfctoolbarscustomizedialogonassignkey"></a><a name="onassignkey"></a>CMFCToolBarsCustomizeDialog::OnAssignKey

Sprawdza poprawność skrótów klawiaturowych, gdy użytkownik je definiuje.

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>Parametry

*pAccel (własówce)*<br/>
[w, na zewnątrz] Wskaźnik do proponowanego assigment klawiatury, który jest wyrażony jako struktury [ACCEL.](/windows/win32/api/winuser/ns-winuser-accel)

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli można przypisać klucz, lub FALSE, jeśli nie można przypisać klucza. Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Zastąpić tę metodę w klasie pochodnej, aby wykonać dodatkowe przetwarzanie, gdy użytkownik przypisuje nowy skrót klawiaturowy lub sprawdzić poprawność skrótów klawiaturowych, jak użytkownik je definiuje. Aby zapobiec przypisywaniu skrótu, zwróć fałsz. Należy również wyświetlić okno komunikatu lub w inny sposób poinformować użytkownika o przyczynie, dla której skrót klawiaturowy został odrzucony.

## <a name="cmfctoolbarscustomizedialogonbeforechangetool"></a><a name="onbeforechangetool"></a>CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

Wykonuje przetwarzanie niestandardowe, gdy zmiana w narzędziu użytkownika, gdy użytkownik ma zamiar zastosować zmianę.

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>Parametry

*pSelTool (Wesztoko)*<br/>
[w, na zewnątrz] Wskaźnik do obiektu narzędzia użytkownika, który ma zostać zastąpiony.

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy właściwości narzędzia zdefiniowanego przez użytkownika ma się zmienić. Domyślna implementacja nic nie robi. Zastąpić `OnBeforeChangeTool` metodę w klasie `CMFCToolBarsCustomizeDialog` pochodną, jeśli chcesz wykonać przetwarzanie przed zmianą w narzędziu użytkownika, takich jak zwalnianie zasobów, które *pSelTool* używa.

## <a name="cmfctoolbarscustomizedialogonedittoolbarmenuimage"></a><a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog::OnEditToolbarMenuImage

Uruchamia edytor obrazów, aby użytkownik mógł dostosować przycisk paska narzędzi lub ikonę elementu menu.

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego.

*Bitmapy*<br/>
[w] Odwołanie do obiektu mapy bitowej, który ma być edytowany.

*nBitsPerPixel*<br/>
[w] Rozdzielczość kolorów bitmapy w bitach na piksel.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli zmiana jest zatwierdzona; w przeciwnym razie FALSE. Domyślna implementacja wyświetla okno dialogowe i zwraca wartość TRUE, jeśli użytkownik kliknie **przycisk OK**lub FALSE, jeśli użytkownik kliknie **przycisk Anuluj** lub **Zamknij.**

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę, gdy użytkownik uruchamia edytor obrazów. Domyślna implementacja wyświetla okno dialogowe [CMFCImageEditorDialog Class.](../../mfc/reference/cmfcimageeditordialog-class.md) Zastąpić `OnEditToolbarMenuImage` w klasie pochodnej, aby użyć niestandardowego edytora obrazów.

## <a name="cmfctoolbarscustomizedialogoninitdialog"></a><a name="oninitdialog"></a>CMFCToolBarsCustomizeDialog::OnInitDialog

Zastępuje, aby zwiększyć inicjowanie arkusza właściwości.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Wartość zwracana

Wynik wywołania [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog) metody.

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementację klasy podstawowej [CPropertySheet::OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog), wyświetlając przycisk **Zamknij,** upewniając się, że okno dialogowe pasuje do bieżącego rozmiaru ekranu, i przesuwając przycisk **Pomoc** do lewego dolnego rogu okna dialogowego.

## <a name="cmfctoolbarscustomizedialogoninittoolspage"></a><a name="oninittoolspage"></a>CMFCToolBarsCustomizeDialog::OnInitToolsPage

Obsługuje powiadomienie z platformy, że **narzędzia** strona ma zostać zainicjowana.

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Uwagi

Domyślna implementacja nic nie robi. Zastąpi tę metodę w klasie pochodnej, aby przetworzyć to powiadomienie.

## <a name="cmfctoolbarscustomizedialogpostncdestroy"></a><a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::PostNcDestroy

Wywoływana przez ramy po okno zostało zniszczone.

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Uwagi

Ta metoda rozszerza implementacji `CPropertySheet::PostNcDestroy`klasy podstawowej, przywracając aplikację do poprzedniego trybu.

[CMFCToolBarsCustomizeDialog::Create](#create) metoda stawia aplikację w trybie specjalnym, który ogranicza użytkownika do zadań dostosowywania.

## <a name="cmfctoolbarscustomizedialogremovebutton"></a><a name="removebutton"></a>CMFCToolBarsCustomizeDialog::RemoveButton

Usuwa przycisk o określonym identyfikatorze polecenia z określonej kategorii lub ze wszystkich kategorii.

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*identyfikator kategorii ui*<br/>
[w] Określa identyfikator kategorii, z której ma być usuwany przycisk.

*identyfikator uiCmdId*<br/>
[w] Określa identyfikator polecenia przycisku.

*Kategoria lpsz*<br/>
[w] Określa nazwę kategorii, z której ma być usuwany przycisk.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera usuniętego przycisku lub -1, jeśli określony identyfikator polecenia nie został znaleziony w określonej kategorii. Jeśli *identyfikator uiCategoryId* wynosi -1, zwracana wartość wynosi 0.

### <a name="remarks"></a>Uwagi

Aby usunąć przycisk ze wszystkich kategorii, wywołaj pierwsze przeciążenie tej metody i ustaw *identyfikator uiCategoryId* na -1.

## <a name="cmfctoolbarscustomizedialogrenamecategory"></a><a name="renamecategory"></a>CMFCToolBarsCustomizeDialog::Zmień nazwę kategorii

Zmienia nazwę kategorii w polu listy kategorii na stronie **Polecenia.**

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>Parametry

*kategoria lpszStar*<br/>
[w] Nazwa kategorii do zmiany.

*kategoria lpszNowa*<br/>
[w] Nowa nazwa kategorii.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Nazwa kategorii musi być unikatowa.

## <a name="cmfctoolbarscustomizedialogreplacebutton"></a><a name="replacebutton"></a>CMFCToolBarsCustomizeDialog::ReplaceButton

Zastępuje przycisk paska narzędzi w polu listy poleceń na stronie **Polecenia.**

```cpp
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Określa polecenie przycisku, który ma zostać zastąpiony.

*Przycisk*<br/>
[w] Odwołanie **do** obiektu przycisku paska narzędzi, który zastępuje stary przycisk.

### <a name="remarks"></a>Uwagi

Gdy [CMFCToolBarsCustomizeDialog::AddMenu](#addmenu), [CMFCToolBarsCustomizeDialog::AddMenuCommands](#addmenucommands)lub [CMFCToolBarsCustomizeDialog::AddToolBar](#addtoolbar) dodaje polecenie do strony **Polecenia,** to polecenie jest w postaci [cmfctoolbarbutton klasy](../../mfc/reference/cmfctoolbarbutton-class.md) obiektu (lub [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) Class `AddMenuCommands`obiektu dla elementu menu, który zawiera podmenu dodane przez ). Struktura wywołuje również te trzy metody, aby dodać polecenia automatycznie. Jeśli chcesz, aby polecenie było reprezentowane przez typ `ReplaceButton` pochodny, zamiast tego zadzwoń i przekaż przycisk typu pochodnego.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać `ReplaceButton` metody w `CMFCToolBarsCustomizeDialog` klasie. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

## <a name="cmfctoolbarscustomizedialogsetusercategory"></a><a name="setusercategory"></a>CMFCToolBarsCustomizeDialog::SetUser Kategoria

Określa, która kategoria na liście kategorii na stronie **Polecenia** jest kategorią użytkownika. Należy wywołać tę funkcję przed wywołaniem [CMFCToolBarsCustomizeDialog::Create](#create).

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>Parametry

*Kategoria lpsz*<br/>
[w] Nazwa kategorii.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ustawienie kategorii użytkownika nie jest obecnie używane przez platformę.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CPropertySheet](../../mfc/reference/cpropertysheet-class.md)
