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
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505154"
---
# <a name="cmfcoutlookbarpane-class"></a>Klasa CMFCOutlookBarPane

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

Kontrolka pochodna [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) , którą można wstawić do paska programu Outlook ( [Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)). Okienko pasek programu Outlook zawiera kolumnę dużych przycisków. Użytkownik może przewijać listę przycisków w górę i w dół, jeśli jest większa niż w okienku. Gdy użytkownik odłączy okienko pasek programu Outlook z paska programu Outlook, może przepływać lub zadokować w oknie głównej ramki.

## <a name="syntax"></a>Składnia

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Konstruktor domyślny.|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarPane:: AddButton](#addbutton)|Dodaje przycisk do okienka paska Outlook.|
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Określa, czy okienko może być zadokowane do innego okienka lub okna ramki. (Przesłania [CBasePane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|
|`CMFCOutlookBarPane::CanBeRestored`|Określa, czy system może przywrócić oryginalny stan paska narzędzi po dostosowaniu. (Przesłania [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|
|[CMFCOutlookBarPane:: ClearAll](#clearall)|Zwalnia zasoby używane przez obrazy w okienku paska programu Outlook.|
|[CMFCOutlookBarPane:: Create](#create)|Tworzy okienko paska Outlook.|
|`CMFCOutlookBarPane::CreateObject`|Używane przez platformę do tworzenia wystąpienia dynamicznego tego typu klasy.|
|`CMFCOutlookBarPane::Dock`|Wywoływane przez platformę, aby zadokować okienko paska programu Outlook. (Przesłania `CPane::Dock`).|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Określa, czy strzałki przewijania w okienku Pasek programu Outlook zaawansowaną listę przycisków według strony, czy za pomocą przycisku.|
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Zwraca zwykły (niewybrany) kolor tekstu okienka paska Outlook.|
|`CMFCOutlookBarPane::GetThisClass`|Używane przez platformę do uzyskania wskaźnika do obiektu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który jest skojarzony z tym typem klasy.|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Określa, czy dla okienka paska programu Outlook jest załadowany obraz tła.|
|`CMFCOutlookBarPane::IsChangeState`|Określa, czy okienko przestawne może być zadokowane. (Przesłania `CPane::IsChangeState`).|
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Określa, czy obramowanie przycisku ma zostać zacieniowane, gdy przycisk zostanie wyróżniony i wyświetlany jest obraz tła.|
|`CMFCOutlookBarPane::OnBeforeFloat`|Wywoływane przez platformę, gdy okienko będzie miało wartość zmiennoprzecinkową. (Przesłania [CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Usuwa przycisk, który ma określony identyfikator polecenia.|
|`CMFCOutlookBarPane::RestoreOriginalstate`|Przywraca oryginalny stan paska narzędzi. (Przesłania [CMFCToolBar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Ustawia kolor tła.|
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Ustawia obraz tła.|
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Resetuje okienko paska programu Outlook do oryginalnego zestawu przycisków.|
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Ustawia liczbę pikseli wypełnienia użytą wokół przycisków w okienku paska Outlook.|
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Ustawia kolory regularnego i wyróżnionego tekstu w okienku paska programu Outlook.|
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Ustawia przezroczysty kolor okienka paska programu Outlook.|
|`CMFCOutlookBarPane::SmartUpdate`|Używane wewnętrznie do aktualizowania paska Outlook. (Przesłania `CMFCToolBar::SmartUpdate`).|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Określa, które elementy menu skrótów są wyświetlane w trybie dostosowywania.|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Usuwa wszystkie przyciski z okienka pasek programu Outlook. (Przesłania [CMFCToolBar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|

## <a name="remarks"></a>Uwagi

Aby uzyskać informacje na temat implementowania paska programu Outlook, zobacz [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Przykład paska programu Outlook można znaleźć w przykładowym projekcie OutlookDemo.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać różnych metod `CMFCOutlookBarPane` klasy. W przykładzie pokazano, jak utworzyć okienko paska programu Outlook, włączyć tryb przewijania strony, włączyć dokowanie i ustawić kolor tła paska Outlook. Ten fragment kodu jest częścią [przykładu wiele widoków programu Outlook](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxoutlookbarpane. h

##  <a name="addbutton"></a>CMFCOutlookBarPane:: AddButton

Dodaje przycisk do okienka paska Outlook.

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
podczas Określa identyfikator zasobu mapy bitowej.

*lpszLabel*<br/>
podczas Określa tekst przycisku.

*iIdCommand*<br/>
podczas Określa identyfikator kontrolki przycisku.

*iInsertAt*<br/>
podczas Określa indeks (liczony od zera) na stronie paska programu Outlook, w której ma zostać wstawiony przycisk.

*uiLabel*<br/>
podczas Identyfikator zasobu ciągu.

*szBmpFileName*<br/>
podczas Określa nazwę pliku obrazu dysku do załadowania.

*szLabel*<br/>
podczas Określa tekst przycisku.

*hBmp*<br/>
podczas Uchwyt mapy bitowej przycisku.

*hIcon*<br/>
podczas Uchwyt ikony przycisków.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk został pomyślnie dodany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby wstawić nowy przycisk do strony paska programu Outlook. Obraz przycisku można załadować z zasobów aplikacji lub z pliku dyskowego.

Jeśli identyfikator strony określony przez *uiPageID* ma wartość-1, przycisk zostanie wstawiony do pierwszej strony.

Jeśli indeks określony przez *iInsertAt* ma wartość-1, przycisk zostanie dodany na końcu strony.

##  <a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="clearall"></a>CMFCOutlookBarPane:: ClearAll

Zwalnia zasoby używane przez obrazy w okienku paska programu Outlook.

```
void ClearAll();
```

### <a name="remarks"></a>Uwagi

Ta metoda bezpośrednio wywołuje [CMFCToolBarImages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), który jest wywoływany na obrazach używanych przez okienko paska programu Outlook.

##  <a name="create"></a>CMFCOutlookBarPane:: Create

Tworzy okienko paska Outlook.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
podczas Określa okno nadrzędne kontrolki okienka paska Outlook. Nie może mieć wartości NULL.

*dwStyle*<br/>
podczas Styl okna.  Aby uzyskać listę stylów okna, zobacz [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*uiID*<br/>
podczas Identyfikator formantu. Musi być unikatowa, aby umożliwić zapisanie stanu formantu.

*dwControlBarStyle*<br/>
podczas Określa specjalne style, które definiują zachowanie kontrolki okienka paska Outlook, gdy jest ona odłączona od paska Outlook.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby skonstruować `CMFCOutlookBarPane` obiekt, najpierw Wywołaj konstruktora, a następnie Wywołaj `Create`, który tworzy formant okienka paska programu Outlook i `CMFCOutlookBarPane` dołącza go do obiektu.

Aby uzyskać więcej informacji `dwControlBarStyle` na temat, zobacz [CBasePane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems

Określa, które elementy menu skrótów są wyświetlane w trybie dostosowywania.

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>Parametry

*pButton*<br/>
podczas Wskaźnik do przycisku paska narzędzi, który został kliknięty przez użytkownika.

*pPopup*<br/>
podczas Wskaźnik do menu skrótów.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli menu skrótów powinno być wyświetlane; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zmodyfikować standardowe menu skrótów platformy wyświetlane w trybie dostosowywania.

Domyślna implementacja sprawdza tryb dostosowywania ( [CMFCToolBar::](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)iscustomizationmode) i jeśli ma wartość true, wyłącza wszystkie elementy menu skrótów z wyjątkiem **usuwania**. Następnie po prostu przekazuje parametry wejściowe do `CMFCToolBar::EnableContextMenuItems`programu.

> [!NOTE]
> *Menu kontekstowe* jest synonimem menu skrótów.

##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode

Określa, czy strzałki przewijania w okienku Pasek programu Outlook zaawansowaną listę przycisków na stronie lub przycisk po przycisku.

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>Parametry

*bPageScroll*<br/>
podczas W przypadku wartości TRUE Włącz tryb przewijania strony. W przypadku wartości FALSE Wyłącz tryb przewijania strony.

##  <a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor

Zwraca zwykły kolor tekstu (czyli niewybrany) okienka paska Outlook.

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Bieżący kolor tekstu jako wartość koloru RGB.

### <a name="remarks"></a>Uwagi

Użyj [CMFCOutlookBarPane:: SetTextColor](#settextcolor) , aby ustawić bieżący (normalny i wybrany) kolor tekstu paska Outlook. Możesz uzyskać domyślny kolor tekstu, wywołując funkcję [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) z indeksem COLOR_WINDOW.

##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture

Określa, czy dla okienka paska programu Outlook jest załadowany obraz tła.

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli jest wyświetlany obraz tła; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Obraz tła można dodać, wywołując funkcję [CMFCOutlookBarPane:: SetBackImage](#setbackimage) .

Jeśli nie ma obrazu tła, tło jest rysowane przy użyciu koloru określonego za pomocą [CMFCOutlookBarPane:: SetBackColor](#setbackcolor).

##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight

Określa, czy obramowanie przycisku ma zostać zacieniowane, gdy przycisk zostanie wyróżniony i wyświetlany jest obraz tła.

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli obramowania przycisku są zacieniowane; w przeciwnym razie FALSE.

##  <a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons

Usuwa wszystkie przyciski z okienka pasek programu Outlook.

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton

Usuwa przycisk, który ma określony identyfikator polecenia.

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>Parametry

*iIdCommand*<br/>
podczas Określa identyfikator polecenia przycisku do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli przycisk został pomyślnie usunięty; Wartość FALSE, jeśli określony identyfikator polecenia jest nieprawidłowy.

##  <a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor

Ustawia kolor tła paska Outlook.

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Określa nowy kolor tła.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby ustawić bieżący kolor tła paska Outlook. Kolor tła jest używany tylko wtedy, gdy nie ma obrazu tła.

##  <a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage

Ustawia obraz tła.

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>Parametry

*uiImageID*<br/>
podczas Określa identyfikator zasobu obrazu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ustawić obraz tła paska programu Outlook. Lista obrazów tła jest zarządzana przez osadzony obiekt [klasy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) .

##  <a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState

Resetuje okienko paska programu Outlook do oryginalnego zestawu przycisków.

```
void SetDefaultState();
```

### <a name="remarks"></a>Uwagi

Ta metoda przywraca oryginalny zestaw przycisków paska programu Outlook. Ta metoda jest taka `CMFCOutlookBarPane::RestoreOriginalstate`sama jak, z tą różnicą, że nie wyzwala ponownego rysowania okienka paska programu Outlook.

##  <a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace

Ustawia liczbę pikseli wypełnienia użytą wokół przycisków w okienku paska Outlook.

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor

Ustawia kolory regularnego i wyróżnionego tekstu w okienku paska programu Outlook.

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>Parametry

*clrRegText*<br/>
podczas Określa nowy kolor dla niezaznaczonego tekstu.

*clrSelText*<br/>
podczas Określa nowy kolor zaznaczonego tekstu.

##  <a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor

Ustawia przezroczysty kolor okienka paska programu Outlook.

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
Określa nowy kolor przezroczysty.

### <a name="remarks"></a>Uwagi

Kolor przezroczysty jest wymagany do wyświetlania przezroczystych obrazów. Wszystkie wystąpienia tego koloru w obrazie są rysowane kolorem tła.  Nie istnieje mieszanie obrazów tła i pierwszego planu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[Klasa CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
