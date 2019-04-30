---
title: Klasa CMFCColorBar
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 4eee24eb93be446f6b4f2631b70736c13a02f45c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403766"
---
# <a name="cmfccolorbar-class"></a>Klasa CMFCColorBar

`CMFCColorBar` Klasa reprezentuje dokujący pasek sterowania, który może wybrać kolory w dokumencie lub aplikacji.

## <a name="syntax"></a>Składnia

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Konstruuje `CMFCColorBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Oblicza marże poziome i pionowe, które muszą zawierać przycisków w formancie paska koloru i ustala lokalizację tych przycisków.|
|[CMFCColorBar::CreateControl](#createcontrol)|Tworzy okno kontrolki paska koloru, dołącza go do `CMFCColorBar` obiektu i zmienia rozmiar kontrolki zawierają określony palety kolorów.|
|[CMFCColorBar::Create](#create)|Tworzy okno kontrolki paska koloru i dołącza je do `CMFCColorBar` obiektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Pokazuje lub ukrywa przycisk Automatyczny.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Włącza lub wyłącza wyświetlanie okna dialogowego, który umożliwia użytkownikowi wybranie więcej kolorów.|
|[CMFCColorBar::GetColor](#getcolor)|Pobiera obecnie wybrany kolor.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Pobiera identyfikator polecenia bieżącego formantu paska kolorów.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Pobiera kolor, który oznacza, że przycisk koloru ma fokus; Ten przycisk jest *gorąca*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Pobiera poziomy margines, czyli miejsce między po lewej stronie lub prawy kolor komórki a obramowaniem obszaru klienta.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Pobiera pionowego marginesu, czyli miejsce między górą lub dolnej komórki. kolor i obramowanie obszaru klienta.|
|[CMFCColorBar::IsTearOff](#istearoff)|Wskazuje, czy bieżący pasek koloru dokowalnych.|
|[CMFCColorBar::SetColor](#setcolor)|Ustawia kolor, który jest aktualnie wybrany.|
|[CMFCColorBar::SetColorName](#setcolorname)|Określa nową nazwę dla określonego koloru.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Ustawia nowy identyfikator polecenia dla formantu paska kolorów.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Ustawia listę kolorów, które są używane w bieżącym dokumencie.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Ustawia poziomy margines, czyli miejsce między po lewej stronie lub prawy kolor komórki a obramowaniem obszaru klienta.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Ustawia pionowego marginesu, czyli miejsce między komórki color top lub bottom a obramowaniem obszaru klienta.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Dopasowuje pozycji kolor przycisków w formancie paska kolorów.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Wskazuje, czy etykieta tekstowa kolor przycisków można zmienić.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Wskazuje, czy obiekt formantu paska koloru mogą być wyświetlane na liście na pasku narzędzi w trakcie dostosowywania.|
|[CMFCColorBar::CalcSize](#calcsize)|Metoda wywoływana przez framework jako część procesu obliczania układu.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicjuje palety kolorów w określonej macierzy kolorów.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Oblicza liczbę wierszy i kolumn w siatce kontrolkę paska kolorów.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Oblicza wysokość dodatkowe, które bieżącego pasek koloru wymaga, aby wyświetlić elementy interfejsu użytkownika różnych, takich jak **innych** przycisku, kolory dokumentu i tak dalej.|
|[CMFCColorBar::InitColors](#initcolors)|Inicjuje tablicę kolorów kolorów palety określonego lub paleta domyślne systemu.|
|[CMFCColorBar::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Metoda wywoływana przez platformę, by zamknąć hierarchię kontrolek popup.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Metoda wywoływana przez platformę, by włączyć lub wyłączyć elementu interfejsu użytkownika formantu paska koloru, zanim zostanie wyświetlony element.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Zostanie otwarte okno dialogowe kolorów.|
|[CMFCColorBar::Rebuild](#rebuild)|Całkowicie ponownie rysuje kontrolkę paska kolorów.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Ustawia logiczną paletę kontekstu określonego urządzenia do palety przycisk nadrzędny bieżącego formantu paska kolorów.|
|[CMFCColorBar::SetPropList](#setproplist)|Zestawy `m_pWndPropList` chroniony element członkowski danych określony wskaźnik do formantu siatki właściwości.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Żądania w oknie ramki, który jest właścicielem formantu paska koloru, aby zaktualizować wiersz wiadomości w pasku stanu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bInternal`|Pole wartość logiczna określająca, czy są przetwarzane zdarzenia myszy. Zazwyczaj zdarzenia myszy są przetwarzane, gdy to pole ma wartość TRUE, a Tryb dostosowywania ma wartość FALSE.|
|`m_bIsEnabled`|Wartość logiczna, która wskazuje, czy kontrolka jest włączona.|
|`m_bIsTearOff`|Wartość logiczna wskazującą, czy formant paska koloru obsługuje dokowania.|
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który określa rozmiar komórkę w siatce paska kolorów.|
|`m_bShowDocColorsWhenDocked`|Wartość logiczna wskazująca, czy ma być wyświetlana kolory dokumentu, gdy jest zadokowany pasek koloru. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Wartość logiczna wskazująca, czy mają być wyświetlane okno dialogowe kolorów standardowych systemowych lub [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|A [COLORREF](/windows/desktop/gdi/colorref) która przechowuje bieżące kolorowi automatycznemu. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md) obiekt, który kojarzy zbiór RGB kolorów przy użyciu ich nazw.|
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md) z [COLORREF](/windows/desktop/gdi/colorref) wartości, które zawiera kolorów, które są wyświetlane w formancie paska kolorów.|
|`m_ColorSelected`|A [COLORREF](/windows/desktop/gdi/colorref) wartość, która jest kolor, który użytkownik wybrał się aktualnie w formancie paska kolorów.|
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) z [COLORREF](/windows/desktop/gdi/colorref) wartości, które zawierają kolorów, które są obecnie używane w dokumencie.|
|`m_nCommandID`|Liczbą całkowitą bez znaku, który jest Identyfikatorem polecenia przycisku koloru.|
|`m_nHorzMargin`|Liczba całkowita, która jest poziomy margines między przyciskami kolor na siatce kolorów.|
|`m_nHorzOffset`|Liczba całkowita, która jest przesunięcie w poziomie do środka przycisk koloru. Ta wartość jest istotne, jeśli przycisk jest wyświetlany tekst lub obraz oprócz koloru.|
|`m_nNumColumns`|Liczba całkowita, która jest liczbą kolumn w siatce formantu paska koloru kolorów.|
|`m_nNumColumnsVert`|Liczba całkowita, która jest liczbą kolumn w orientacji pionowej siatka kolorów.|
|`m_nNumRowsHorz`|Liczba całkowita, która jest liczbą kolumn w orientacji poziomej siatka kolorów.|
|`m_nRowHeight`|Liczba całkowita, która jest równa wysokości wiersz przycisków kolor na siatce kolorów.|
|`m_nVertMargin`|Liczba całkowita, która jest pionowego marginesu między przyciskami kolor na siatce kolorów.|
|`m_nVertOffset`|Liczba całkowita, która jest przesunięcie w pionie do środka przycisk koloru. Ta wartość jest istotne, jeśli przycisk jest wyświetlany tekst lub obraz oprócz koloru.|
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md) kolorów, które są używane w formancie paska kolorów.|
|`m_pParentBtn`|Wskaźnik do [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) obiektu, który jest elementem nadrzędnym bieżącego przycisku. Ta wartość jest istotne, jeśli przycisk koloru znajduje się w hierarchii kontrolki paska narzędzi lub w formancie siatki właściwości color.|
|`m_pParentRibbonBtn`|Wskaźnik do [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) obiektu, który znajduje się na Wstążce, a następnie przycisk nadrzędny bieżącego przycisku. Ta wartość jest istotne, jeśli przycisk koloru znajduje się w hierarchii kontrolki paska narzędzi lub w formancie siatki właściwości color.|
|`m_pWndPropList`|Wskaźnik do [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) obiektu.|
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na **automatyczne** przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na przycisku kolory dokumentu. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na *innych* przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Uwagi

Zazwyczaj nie tworzysz `CMFCColorBar` obiektu bezpośrednio. Zamiast tego [klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (używane w menu i pasków narzędzi) lub [klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) tworzy `CMFCColorBar` obiektu.

`CMFCColorBar` Klasa oferuje następujące funkcje:

- Automatycznie dostosowuje listę kolory dokumentu.

- Zapisuje i przywraca jej stan oraz stan dokumentu.

- Zarządza przycisk "Automatyczny".

- Używa [klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) formantu, aby wybrać kolor niestandardowy.

- Obsługuje stan "odrywania" (jeśli jest tworzona przy użyciu [klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Aby włączyć usługę `CMFCColorBar` funkcji do aplikacji:

1. Tworzenie przycisku menu regularnych i przypisać mu identyfikator, na przykład ID_CHAR_COLOR.

1. W swojej klasie okien ramowych zastąpić [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) metodę i Zastąp regularne menu przycisku z [klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) obiektu (przez wywołanie metody [CMFCToolBar: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Ustaw wszystkie style i Włącz lub wyłącz funkcje `CMFCColorBar` obiektu podczas [klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) tworzenia. `CMFCColorMenuButton` Dynamicznie tworzy obiekt `CMFCColorBar` obiektu po struktura wywołuje `CreatePopupMenu` metody.

Gdy użytkownik kliknie przycisk formantu paska koloru, środowisko wykorzystuje `ON_COMMAND` makra, by powiadomić element nadrzędny kontrolki paska kolorów. W makrach parametru ID polecenia jest wartość, która została przypisana do paska koloru przycisku sterowania w kroku 1 (ID_CHAR_COLOR w tym przykładzie). Aby uzyskać więcej informacji, zobacz [klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), [klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md), [klasa CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md), [klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md), i [klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) klasy.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować paska kolorów przy użyciu różnych metod w `CMFCColorBar` klasy. Metody ustawić marginesy poziome i pionowe, Włącz przycisk inne, utwórz okno kontrolki paska koloru i ustawia aktualnie wybranego koloru. W tym przykładzie jest częścią [przykładowe nowych formantów](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorbar.h

##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations

Dopasowuje pozycji kolor przycisków w formancie paska kolorów.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę podczas przetwarzania komunikatu WM_SIZE.

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

Wskazuje, czy etykieta tekstowa kolor przycisków można zmienić.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FALSE, co oznacza, że tekst etykiety nie może być modyfikowany. Zastępuje tę metodę, aby umożliwić modyfikowanie tekstu etykiety.

##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList

Wskazuje, czy obiekt formantu paska koloru mogą być wyświetlane na liście na pasku narzędzi w trakcie dostosowywania.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość TRUE, co oznacza, że struktura może wyświetlać formantu paska koloru w trakcie dostosowywania. Zastępuje tę metodę, aby zaimplementować różne zachowanie.

##  <a name="calcsize"></a>  CMFCColorBar::CalcSize

Metoda wywoływana przez framework jako część procesu obliczania układu.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock*<br/>
[in] Wartość TRUE, aby określić, że formant paska kolorów jest zadokowany w pionie; Wartość FALSE, aby określić, że formant paska kolorów jest zadokowany w poziomie.

### <a name="return-value"></a>Wartość zwracana

Rozmiar tablicy kolor przycisków w formancie paska kolorów.

##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar

Konstruuje `CMFCColorBar` obiektu.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>Parametry

*colors*<br/>
[in] Tablica kolorów wyświetlanych w formancie paska kolorów.

*Kolor*<br/>
[in] Początkowo wybrany kolor.

*lpszAutoColor*<br/>
[in] Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne) lub wartość NULL.

Standardowa etykieta przycisku automatycznego **automatyczne**.

*lpszOtherColor*<br/>
[in] Etykieta tekstowa elementu *innych* przycisk wyświetlający więcej opcji koloru, lub wartość NULL.

Standardowa etykieta dla innych przycisku **więcej kolorów...** .

*lpszDocColors*<br/>
[in] Etykieta tekstowa przycisku kolory dokumentu. Paleta kolorów dokumentu zawiera listę kolorów używanych obecnie dokumentu.

*lstDocColors*<br/>
[in] Lista kolorów, które są obecnie używane.

*nColumns*<br/>
[in] Liczba kolumn, które zawiera tablicę kolorów.

*nRowsDockHorz*<br/>
[in] Liczba wierszy, które ma pasek koloru, gdy jest zadokowany w poziomie.

*nColDockVert*<br/>
[in] Liczba kolumn, które ma pasek koloru, gdy jest zadokowany w pionie.

*colorAutomatic*<br/>
[in] Domyślny kolor struktura ma zastosowanie, gdy klikniesz przycisk Automatyczny.

*nCommandID*<br/>
[in] Identyfikator polecenia sterowania paska kolorów.

*pParentBtn*<br/>
[in] Wskaźnik do przycisku nadrzędnej.

*src*<br/>
[in] Istniejące `CMFCColorBar` obiektu do skopiowania w nowe `CMFCColorBar` obiektu.

*uiCommandID*<br/>
[in] Identyfikator polecenia.

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

Oblicza marginesy poziome i pionowe, które muszą zawierać przycisków w formancie paska koloru i dostosowanie położenia tych przycisków.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bSquareButtons*|[in] Wartość TRUE, aby określić, że kształt przycisków w formancie paska kolorów jest kwadratowy; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.|
|*bCenterButtons*|[in] Wartość TRUE, aby określić, czy zawartość rachunku przycisku sterowania paska kolorów jest wyśrodkowywana; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.|

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>  CMFCColorBar::Create

Tworzy okno kontrolki paska koloru i dołącza je do `CMFCColorBar` obiektu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Wskaźnik do okna nadrzędnego.

*dwStyle*<br/>
[in] Bitowa kombinacja (lub) [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] Identyfikator polecenia.

*pPalette*<br/>
[in] Wskaźnik do palety kolorów. Wartość domyślna to NULL.

*nColumns*<br/>
[in] Liczba kolumn w formancie paska kolorów. Wartość domyślna to 0.

*nRowsDockHorz*<br/>
[in] Liczba wierszy w formancie paska koloru, gdy jest zadokowany w poziomie. Wartość domyślna to 0.

*nColDockVert*<br/>
[in] Liczba kolumn w formancie paska koloru, gdy jest zadokowany w pionie. Wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Do konstruowania `CMFCColorBar` obiektu, wywołanie konstruktora klasy, a następnie tej metody. `Create` Metoda tworzy formant Windows i inicjuje Lista kolorów.

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

Tworzy okno kontrolki paska koloru, dołącza go do `CMFCColorBar` obiektu i zmienia rozmiar okno kontrolki, które zawierają określony palety kolorów.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
[in] Wskaźnik do okna nadrzędnego. Nie może mieć wartości NULL.

*Rect*<br/>
[in] Prostokąt otaczający, która określa, gdzie narysuj kontrolkę paska kolorów.

*nID*<br/>
[in] Identyfikator kontrolki.

*nColumns*<br/>
[in] Idealna liczba kolumn w formancie paska kolorów. Ta metoda modyfikuje tę liczbę, aby dopasować określony palety kolorów. Wartość domyślna to -1, co oznacza, że ten parametr nie jest określony.

*pPalette*<br/>
[in] Wskaźnik do palety kolorów lub wartość NULL. Jeśli ten parametr ma wartość NULL, ta metoda oblicza rozmiar formantu paska koloru, tak, jakby określono 20 kolorów. Wartość domyślna to NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa *prostokąt*, *nColumns*, i *pPalette* parametry, aby obliczyć odpowiednia liczba lub wiersze i kolumny w formantu paska koloru, a następnie wywołania [CMFCColorBar::Create](#create) metody.

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

Inicjuje palety kolorów w określonej macierzy kolorów.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*arColors*|[in] Tablica kolorów.|
|*palette*|[in] Palety kolorów.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton

Pokazuje lub ukrywa przycisk Automatyczny.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne) lub wartość NULL.

Standardowa etykieta przycisku automatycznego **automatyczne**.

*colorAutomatic*<br/>
[in] Domyślny kolor struktura ma zastosowanie, gdy klikniesz przycisk Automatyczny.

*bWłączenie*<br/>
[in] Wartość TRUE, aby włączyć przycisk Automatyczny; Wartość FALSE, aby wyłączyć przycisk Automatyczny. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Tekst etykiety przycisku automatycznego zostanie usunięty w przypadku *lpszLabel* parametr ma wartość NULL lub *bWłączenie* parametr ma wartość FAŁSZ.

##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton

Włącza lub wyłącza wyświetlanie okna dialogowego, który umożliwia użytkownikowi wybranie więcej kolorów.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
[in] Etykieta tekstowa elementu *innych* przycisk wyświetlający więcej opcji koloru, lub wartość NULL.

Standardowa etykietę dla tego przycisku jest **więcej kolorów...** .

*bAltColorDlg*<br/>
[in] Wartość true, ekran [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe; Wartość FALSE, aby wyświetlić standardowe [CColorDialog](../../mfc/reference/ccolordialog-class.md) okno dialogowe. Wartość domyślna to TRUE.

*bWłączenie*<br/>
[in] Wartość TRUE powoduje włączenie przycisku; Wartości FALSE spowoduje wyłączenie przycisku. Wartość domyślna to TRUE.

##  <a name="getcolor"></a>  CMFCColorBar::GetColor

Pobiera obecnie wybrany kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Obecnie wybrany kolor.

##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize

Oblicza liczbę wierszy i kolumn w siatce kontrolkę paska kolorów.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bVertDock*|[in] Wartość TRUE, aby wykonać obliczenia dla kontrolki w pionie zadokowany pasek koloru; w przeciwnym razie wykonywania obliczeń poziomo zadokowanych kontrolki.|

### <a name="return-value"></a>Wartość zwracana

A [CSize](../../atl-mfc-shared/reference/csize-class.md) którego `cx` składnik zawiera liczbę kolumn i którego `cy` składnik zawiera liczbę wierszy.

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

Pobiera identyfikator polecenia bieżącego formantu paska kolorów.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze nowy kolor, struktura wysyła identyfikator polecenia komunikatów WM_COMMAND, by powiadomić element nadrzędny `CMFCColorBar` obiektu.

##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight

Oblicza wysokość dodatkowe, które bieżącego pasek koloru wymaga, aby wyświetlić elementy interfejsu użytkownika inne, takie jak **innych** kolory przycisku lub dokumentu.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nNumColumns*|[in] Jeśli formant paska koloru zawiera kolory dokumentu, liczbę kolumn do wyświetlenia w siatce kolory dokumentu. W przeciwnym razie ta wartość nie jest używana.|

### <a name="return-value"></a>Wartość zwracana

Obliczony wysokość dodatkowe, które jest wymagane.

##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor

Pobiera kolor, który oznacza, że przycisk koloru ma fokus; Ten przycisk jest *gorąca*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

Pobiera poziomy margines, czyli miejsce między po lewej stronie lub prawy kolor komórki a obramowaniem obszaru klienta.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Wartość zwracana

Poziomy margines.

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

Pobiera pionowego marginesu, czyli miejsce między górą lub dolnej komórki. kolor i obramowanie obszaru klienta.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Pionowego marginesu.

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

Inicjuje tablicę kolorów kolorów palety określonego lub z palety domyślne systemu.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pPalette*|[in] Wskaźnik do obiektu palety lub wartość NULL. Jeśli ten parametr ma wartość NULL, ta metoda używa domyślnej palety systemu operacyjnego.|
|*arColors*|[in] Tablica kolorów.|

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy kolorów.

##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff

Wskazuje, czy bieżący pasek koloru dokowalnych.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli bieżący formant paska kolorów jest zadokowane; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Jeśli formant paska kolorów jest zadokowane, można zerwana pasek sterowania i zadokowane w innej lokalizacji.

##  <a name="onkey"></a>  CMFCColorBar::OnKey

Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
[in] Kod klawisza wirtualnego klucz, który użytkownik nacisnął klawisz.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda przetwarza określony klucz; w przeciwnym razie wartość FALSE.

##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand

Metoda wywoływana przez platformę, by zamknąć hierarchię formanty wyskakujące.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pButton*|[in] Wskaźnik do formantu, który znajduje się na pasku narzędzi.|

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli ta metoda jest kończy się pomyślnie; w przeciwnym razie wartość FALSE.

##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI

Metoda wywoływana przez platformę, by włączyć lub wyłączyć elementu interfejsu użytkownika formantu paska koloru, zanim zostanie wyświetlony element.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
[in] Wskaźnik do okna, który zawiera element interfejsu użytkownika, aby zaktualizować.

*bDisableIfNoHndler*<br/>
[in] Wartość TRUE, aby wyłączyć elementu interfejsu użytkownika, jeśli żadna procedura obsługi nie jest zdefiniowany w mapie komunikatów; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Gdy użytkownik aplikacji kliknie element interfejsu użytkownika, element musisz wiedzieć, czy ma być wyświetlany jako włączone lub wyłączone. Celem komunikat polecenia zawiera informacje poprzez implementację programu obsługi poleceń ON_UPDATE_COMMAND_UI. Metoda ta jest przydatna w przetwarzania polecenia. Aby uzyskać więcej informacji, zobacz [klasa CCmdUI](../../mfc/reference/ccmdui-class.md).

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

Zostanie otwarte okno dialogowe kolorów.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
[in] Kolor, który jest domyślnie wybierany, gdy zostanie otwarte okno dialogowe kolorów.

*colorRes*<br/>
[out] Kolor wybrany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli użytkownik wybrał kolor. Wartość FALSE, jeśli użytkownik anulował okno dialogowe kolorów.

### <a name="remarks"></a>Uwagi

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

Całkowicie ponownie rysuje kontrolkę paska kolorów.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

Ustawia logiczną paletę kontekstu określonego urządzenia do palety przycisk nadrzędny bieżącego formantu paska kolorów.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pDC*|[in] Wskaźnik do kontekstu urządzenia przycisku nadrzędny bieżącego formantu paska kolorów.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do palety, który zastępuje palety przycisku nadrzędny bieżącego formantu paska koloru.

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

Ustawia kolor, który jest aktualnie wybrany.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Wartość koloru RGB.

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

Określa nową nazwę dla określonego koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
[in] Wartość koloru RGB.

*strName*<br/>
[in] Nowa nazwa dla określonego koloru.

### <a name="remarks"></a>Uwagi

Ta metoda zmienia nazwę określonego koloru we wszystkich `CMFCColorBar` obiektów w aplikacji.

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

Ustawia nowy identyfikator polecenia dla formantu paska kolorów.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nCommandID*<br/>
[in] Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zmodyfikować identyfikator polecenia formantu paska koloru i powiadamia okno nadrzędne kontrolki, którego identyfikator został zmieniony.

##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors

Ustawia listę kolorów, które są używane w bieżącym dokumencie.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
[in] Podpis, który jest wyświetlany, gdy nie jest zadokowany formantu paska kolorów.

*lstDocColors*<br/>
[in] Lista kolorów zastępuje kolorów bieżącego dokumentu.

*bShowWhenDocked*<br/>
[in] Wartość TRUE, aby wyświetlać kolory dokumentu, gdy jest zadokowany formantu paska koloru; w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

*Kolory dokumentu* kolory, które są obecnie używane w dokumencie. Struktura automatycznie przechowuje listę kolory dokumentu, ale ta metoda służy do modyfikowania listy.

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

Ustawia poziomy margines, czyli miejsce między po lewej stronie lub komórki prawy kolor i obramowanie obszaru klienta.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMargin*<br/>
[in] Poziomy margines w pikselach.

### <a name="remarks"></a>Uwagi

Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) Konstruktor Ustawia poziomy margines 4 pikseli.

##  <a name="setproplist"></a>  CMFCColorBar::SetPropList

Zestawy `m_pWndPropList` chroniony element członkowski danych określony wskaźnik do formantu siatki właściwości.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pWndList*|[in] Wskaźnik do obiektu formantu siatki właściwości.|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

Ustawia pionowego marginesu, czyli miejsce między komórki color top lub bottom a obramowaniem obszaru klienta.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin*<br/>
[in] Margines pionowy w pikselach.

### <a name="remarks"></a>Uwagi

Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) Konstruktor ustawia pionowego marginesu 4 pikseli.

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

Żądania w oknie ramki, który jest właścicielem formantu paska koloru, aby zaktualizować wiersz wiadomości w pasku stanu.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
[in] Identyfikator polecenia. (Ten parametr jest ignorowany).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat WM_SETMESSAGESTRING właścicielowi kontrolki paska kolorów.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
