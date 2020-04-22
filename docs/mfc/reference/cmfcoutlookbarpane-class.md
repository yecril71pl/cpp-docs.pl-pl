---
title: Klasa CMFCOutlookBarPane
ms.date: 11/04/2016
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
ms.openlocfilehash: 97c7edde26bdf13e899d823dcf88d143068d86a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749609"
---
# <a name="cmfcoutlookbarpane-class"></a>Klasa CMFCOutlookBarPane

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

Formant pochodzący z [cmfctoolbar klasy,](../../mfc/reference/cmfctoolbar-class.md) które mogą być wstawiane do paska programu Outlook ( [CMFCOutlookBar Klasy](../../mfc/reference/cmfcoutlookbar-class.md)). Okienko paska programu Outlook zawiera kolumnę dużych przycisków. Użytkownik może przewijać listę przycisków w górę i w dół, jeśli jest on większy niż okienko. Gdy użytkownik odłącza okienko paska programu Outlook od paska programu Outlook, może ono unosić się w powietrzu lub dokować w oknie ramki głównej.

## <a name="syntax"></a>Składnia

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Domyślny konstruktor.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarPane::AddButton](#addbutton)|Dodaje przycisk do okienka paska programu Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Określa, czy okienko można zadokować do innego okienka lub okna ramki. (Zastępuje [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Określa, czy system może przywrócić pasek narzędzi do stanu pierwotnego po dostosowaniu. (Zastępuje [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane::ClearAll](#clearall)|Zwalnia zasoby używane przez obrazy w okienku paska programu Outlook.|
|[CMFCOutlookBarPane::Utwórz](#create)|Tworzy okienko paska programu Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCOutlookBarPane::Dock`|Wywoływane przez platformę do zadokowania okienka paska programu Outlook. (Przesłania `CPane::Dock`).|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Określa, czy strzałki przewijania w okienku paska programu Outlook przesuwają listę przycisków według strony, czy przycisku.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Zwraca zwykły (niewykończalne) kolor tekstu okienka paska programu Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Określa, czy dla okienka paska programu Outlook jest ładowany obraz tła.|
|`CMFCOutlookBarPane::IsChangeState`|Określa, czy okienko przestawne może być zadokowane. (Przesłania `CPane::IsChangeState`).|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Określa, czy obramowanie przycisku jest zacieniowane po podświetleniu przycisku i wyświetleniu obrazu tła.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Wywoływana przez platformę, gdy okienko ma się unosić. (Zastępuje [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::Usuńbutton](#removebutton)|Usuwa przycisk o określonym identyfikatorze polecenia.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Przywraca oryginalny stan paska narzędzi. (Zastępuje [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Ustawia kolor tła.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Ustawia obraz tła.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Resetuje okienko paska programu Outlook do oryginalnego zestawu przycisków.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Ustawia liczbę pikseli dopełnienia używanych wokół przycisków w okienku paska programu Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Ustawia kolory zwykłego i wyróżnionego tekstu w okienku paska programu Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Ustawia kolor przezroczysty okienka paska programu Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Używane wewnętrznie do aktualizowania paska programu Outlook. (Przesłania `CMFCToolBar::SmartUpdate`).|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Określa, które elementy menu skrótów są wyświetlane w trybie dostosowywania.|
|[CMFCOutlookBarPane::Usuń WszystkieButtony](#removeallbuttons)|Usuwa wszystkie przyciski z okienka paska programu Outlook. (Zastępuje [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje dotyczące sposobu zaimplementowania paska programu Outlook, zobacz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Na przykład paska programu Outlook zobacz przykładowy projekt Programu OutlookDemo.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCOutlookBarPane` używać różnych metod klasy. W przykładzie pokazano, jak utworzyć okienko paska programu Outlook, włączyć tryb przewijania strony, włączyć dokowanie i ustawić kolor tła paska programu Outlook. Ten fragment kodu jest częścią [przykładu Outlook Multi Views](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar](../../mfc/reference/cmfctoolbar-class.md)

[Panel CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxoutlookbarpane.h

## <a name="cmfcoutlookbarpaneaddbutton"></a><a name="addbutton"></a>CMFCOutlookBarPane::AddButton

Dodaje przycisk do okienka paska programu Outlook.

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

*uiImage*<br/>
[w] Określa identyfikator zasobu mapy bitowej.

*lpszLabel (lpszLabel)*<br/>
[w] Określa tekst przycisku.

*iIdCommand*<br/>
[w] Określa identyfikator formantu przycisku.

*iInsertAt (Właso)*<br/>
[w] Określa indeks oparty na wartości zero na stronie paska programu Outlook, na którym ma być wstawiony przycisk.

*uiLabel (polski)*<br/>
[w] Identyfikator zasobu ciągu.

*szBmpFileName*<br/>
[w] Określa nazwę pliku obrazu dysku do załadowania.

*SzLabel (szLabel)*<br/>
[w] Określa tekst przycisku.

*hBmp (wł.)*<br/>
[w] Uchwyt do mapy bitowej przycisku.

*hIcon (własówce)*<br/>
[w] Uchwyt do ikony przycisków.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk został dodany pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda służy do wstawiania nowego przycisku do strony paska programu Outlook. Obraz przycisku można załadować z zasobów aplikacji lub z pliku dysku.

Jeśli identyfikator strony określony przez *uiPageID* wynosi -1, przycisk zostanie wstawiony do pierwszej strony.

Jeśli indeks określony przez *iInsertAt* jest -1, przycisk jest dodawany na końcu strony.

## <a name="cmfcoutlookbarpanecanbeattached"></a><a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcoutlookbarpaneclearall"></a><a name="clearall"></a>CMFCOutlookBarPane::ClearAll

Zwalnia zasoby używane przez obrazy w okienku paska programu Outlook.

```cpp
void ClearAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda bezpośrednio wywołuje [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), który jest wywoływany na obrazach, które są używane przez okienko paska programu Outlook.

## <a name="cmfcoutlookbarpanecreate"></a><a name="create"></a>CMFCOutlookBarPane::Utwórz

Tworzy okienko paska programu Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[w] Określa okno nadrzędne formantu paska programu Outlook. Nie może być null.

*Dwstyle*<br/>
[w] Styl okna.  Aby uzyskać listę stylów okien, zobacz [Style okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Uiid*<br/>
[w] Identyfikator sterowania. Musi być unikatowy, aby umożliwić zapisywanie stanu formantu.

*styl dwControlBarStyle*<br/>
[w] Określa specjalne style definiujące zachowanie formantu paska programu Outlook po odłączeniu go od paska programu Outlook.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby skonstruować `CMFCOutlookBarPane` obiekt, najpierw należy wywołać `Create`konstruktora, a następnie wywołać , `CMFCOutlookBarPane` który tworzy kontrolkę okienka paska programu Outlook i dołącza go do obiektu.

Aby uzyskać `dwControlBarStyle` więcej informacji na temat zobacz [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).

## <a name="cmfcoutlookbarpaneenablecontextmenuitems"></a><a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Określa, które elementy menu skrótów są wyświetlane w trybie dostosowywania.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parametry

*pButton (przycisk)*<br/>
[w] Wskaźnik do przycisku paska narzędzi kliknięty przez użytkownika.

*pPopup*<br/>
[w] Wskaźnik do menu skrótów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli powinno być wyświetlane menu skrótów; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąd w tej metodzie należy zmodyfikować standardowe menu skrótów struktury wyświetlane w trybie dostosowywania.

Domyślna implementacja sprawdza tryb dostosowywania ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)), a jeśli jest ustawiona na WARTOŚĆ TRUE, wyłącza wszystkie elementy menu skrótów z wyjątkiem **Usuń**. Następnie po prostu przekazuje parametry `CMFCToolBar::EnableContextMenuItems`wejściowe do .

> [!NOTE]
> *Menu kontekstowe* jest synonimem menu skrótów.

## <a name="cmfcoutlookbarpaneenablepagescrollmode"></a><a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Określa, czy strzałki przewijania w okienku paska programu Outlook przesuwają listę przycisków strona po stronie, czy przycisk po.

```cpp
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parametry

*bPageScroll (StronaScroll)*<br/>
[w] Jeśli true, włącz tryb przewijania strony. Jeśli FAŁSZ, wyłącz tryb przewijania strony.

## <a name="cmfcoutlookbarpanegetregularcolor"></a><a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Zwraca zwykły (czyli nieoczyszty) kolor tekstu okienka paska programu Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący kolor tekstu jako wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Użyj [polecenia CMFCOutlookBarPane::SetTextColor,](#settextcolor) aby ustawić bieżący (zwykły i zaznaczony) kolor tekstu paska programu Outlook. Domyślny kolor tekstu można uzyskać, wywołując funkcję [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) z indeksem COLOR_WINDOW.

## <a name="cmfcoutlookbarpaneisbackgroundtexture"></a><a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Określa, czy dla okienka paska programu Outlook jest ładowany obraz tła.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli do wyświetlenia jest obraz tła; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Obraz tła można dodać, wywołując funkcję [CMFCOutlookBarPane::SetBackImage.](#setbackimage)

Jeśli nie ma obrazu tła, tło jest malowane kolorem określonym przy użyciu [cmfcoutlookBarPane::SetBackColor](#setbackcolor).

## <a name="cmfcoutlookbarpaneisdrawshadedhighlight"></a><a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Określa, czy obramowanie przycisku jest zacieniowane po podświetleniu przycisku i wyświetleniu obrazu tła.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obramowania przycisku są zacieniowane; w przeciwnym razie FALSE.

## <a name="cmfcoutlookbarpaneremoveallbuttons"></a><a name="removeallbuttons"></a>CMFCOutlookBarPane::Usuń WszystkieButtony

Usuwa wszystkie przyciski z okienka paska programu Outlook.

```
virtual void RemoveAllButtons();
```

## <a name="cmfcoutlookbarpaneremovebutton"></a><a name="removebutton"></a>CMFCOutlookBarPane::Usuńbutton

Usuwa przycisk o określonym identyfikatorze polecenia.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parametry

*iIdCommand*<br/>
[w] Określa identyfikator polecenia przycisku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przycisk został pomyślnie usunięty; FAŁSZ, jeśli określony identyfikator polecenia jest nieprawidłowy.

## <a name="cmfcoutlookbarpanesetbackcolor"></a><a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Ustawia kolor tła paska programu Outlook.

```cpp
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Określa nowy kolor tła.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby ustawić bieżący kolor tła dla paska programu Outlook. Kolor tła jest używany tylko wtedy, gdy nie ma obrazu tła.

## <a name="cmfcoutlookbarpanesetbackimage"></a><a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Ustawia obraz tła.

```cpp
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parametry

*uiImageID*<br/>
[w] Określa identyfikator zasobu obrazu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ustawić obraz tła paska programu Outlook. Lista obrazów tła jest zarządzana przez osadzony obiekt [klasy CMFCToolBarImages.](../../mfc/reference/cmfctoolbarimages-class.md)

## <a name="cmfcoutlookbarpanesetdefaultstate"></a><a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Resetuje okienko paska programu Outlook do oryginalnego zestawu przycisków.

```cpp
void SetDefaultState();
```

### <a name="remarks"></a>Uwagi

Ta metoda przywraca przyciski paska programu Outlook do oryginalnego zestawu. Ta metoda `CMFCOutlookBarPane::RestoreOriginalstate`jest podobna , z tą różnicą, że nie wyzwala ponownego rysowania okienka paska programu Outlook.

## <a name="cmfcoutlookbarpanesetextraspace"></a><a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Ustawia liczbę pikseli dopełnienia używanych wokół przycisków w okienku paska programu Outlook.

```cpp
void SetExtraSpace()
```

## <a name="cmfcoutlookbarpanesettextcolor"></a><a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Ustawia kolory zwykłego i wyróżnionego tekstu w okienku paska programu Outlook.

```cpp
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parametry

*clrRegText (tekst clrRegText)*<br/>
[w] Określa nowy kolor nie zaznaczonego tekstu.

*tekst clrSel*<br/>
[w] Określa nowy kolor zaznaczonego tekstu.

## <a name="cmfcoutlookbarpanesettransparentcolor"></a><a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Ustawia kolor przezroczysty okienka paska programu Outlook.

```cpp
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
Określa nowy kolor przezroczysty.

### <a name="remarks"></a>Uwagi

Do wyświetlania przezroczystych obrazów wymagany jest kolor przezroczysty. Każde wystąpienie tego koloru na obrazie jest malowane kolorem tła.  Nie ma mieszania obrazów tła i pierwszego planu.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
