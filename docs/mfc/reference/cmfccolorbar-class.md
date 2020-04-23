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
ms.openlocfilehash: 58fddeef9cb0afe930af84b05e6a87871f729da4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752573"
---
# <a name="cmfccolorbar-class"></a>Klasa CMFCColorBar

Klasa `CMFCColorBar` reprezentuje pasek sterowania dokowania, który można wybrać kolory w dokumencie lub aplikacji.

## <a name="syntax"></a>Składnia

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Konstruuje `CMFCColorBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Oblicza pionowe i poziome marginesy, które muszą zawierać przyciski na pasku kolorów, a następnie dostosowuje położenie tych przycisków.|
|[CMFCColorBar::CreateControl](#createcontrol)|Tworzy okno formantu paska kolorów, dołącza je do `CMFCColorBar` obiektu i rozmiaruje formant, aby zawierał określoną paletę kolorów.|
|[CMFCColorBar::Utwórz](#create)|Tworzy okno formantu paska kolorów `CMFCColorBar` i dołącza je do obiektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Pokazuje lub ukrywa przycisk automatyczny.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Włącza lub wyłącza wyświetlanie okna dialogowego, które pozwala użytkownikowi wybrać więcej kolorów.|
|[CMFCColorBar::GetColor](#getcolor)|Pobiera aktualnie zaznaczony kolor.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Pobiera identyfikator polecenia bieżącego paska kolorów.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Pobiera kolor, który oznacza, że przycisk kolor ma fokus; oznacza to, że przycisk jest *gorący*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Pobiera margines poziomy, czyli odstęp między lewą lub prawą komórką kolorów a granicą obszaru klienta.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Pobiera margines pionowy, czyli odstęp między górną lub dolną komórką kolorów a granicą obszaru klienta.|
|[CMFCColorBar::IsTearOff](#istearoff)|Wskazuje, czy bieżący pasek kolorów można dokować.|
|[CMFCColorBar::SetColor](#setcolor)|Ustawia aktualnie zaznaczony kolor.|
|[CMFCColorBar::SetColorName](#setcolorname)|Ustawia nową nazwę dla określonego koloru.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Ustawia nowy identyfikator polecenia dla kontrolki paska kolorów.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Ustawia listę kolorów używanych w bieżącym dokumencie.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Ustawia margines poziomy, czyli odstęp między lewą lub prawą komórką kolorów a granicą obszaru klienta.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Ustawia margines pionowy, czyli odstęp między górną lub dolną komórką kolorów a granicą obszaru klienta.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Dostosowuje położenie przycisków kolorów na pasku kolorów.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Wskazuje, czy etykieta tekstowa przycisków kolorów może ulec zmianie.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Wskazuje, czy obiekt sterujący paska kolorów może pojawić się na liście paska narzędzi podczas procesu dostosowywania.|
|[CMFCColorBar::CalcSize](#calcsize)|Wywoływana przez strukturę w ramach procesu obliczania układu.|
|[CMFCColorBar::Utwórzpalette](#createpalette)|Inicjuje paletę z kolorami w określonej tablicy kolorów.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Oblicza liczbę wierszy i kolumn w siatce formantu paska kolorów.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Oblicza dodatkową wysokość, która wymaga bieżącego paska kolorów do wyświetlania różnych elementów interfejsu użytkownika, takich jak **przycisk Inne,** kolory dokumentu i tak dalej.|
|[CMFCColorBar::InitColors](#initcolors)|Inicjuje tablicę kolorów z kolorami w określonej palecie lub domyślną paletą systemu.|
|[CMFCColorBar::OnKey](#onkey)|Wywoływana przez strukturę, gdy użytkownik naciśnie przycisk klawiatury.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Wywoływane przez strukturę, aby zamknąć hierarchię formantów wyskakujących.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Wywoływane przez strukturę, aby włączyć lub wyłączyć element interfejsu użytkownika formantu paska kolorów przed elementem jest wyświetlany.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otwiera kolorowe okno dialogowe.|
|[CMFCColorBar::Odbuduj](#rebuild)|Całkowicie przerysowuje kontrolki paska kolorów.|
|[CMFCColorBar::Wybierzpalette](#selectpalette)|Ustawia paletę logiczną określonego kontekstu urządzenia na paletę przycisku nadrzędnego bieżącego paska kolorów.|
|[CMFCColorBar::SetPropList](#setproplist)|Ustawia `m_pWndPropList` element członkowski chronionych danych na określony wskaźnik do formantu siatki właściwości.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Żąda okna ramki, które jest właścicielem formantu paska kolorów, aby zaktualizować wiersz komunikatu na pasku stanu.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bInternal`|Pole logiczne określające, czy zdarzenia myszy są przetwarzane. Zazwyczaj zdarzenia myszy są przetwarzane, gdy to pole ma wartość PRAWDA, a tryb dostosowywania jest FALSE.|
|`m_bIsEnabled`|Wartość logiczna wskazująca, czy formant jest włączony.|
|`m_bIsTearOff`|Wartość logiczna wskazująca, czy kontrolka paska kolorów obsługuje dokowanie.|
|`m_BoxSize`|Obiekt [CSize,](../../atl-mfc-shared/reference/csize-class.md) który określa rozmiar komórki w siatce paska kolorów.|
|`m_bShowDocColorsWhenDocked`|Wartość logiczna wskazująca, czy kolory dokumentu mają być wyświetlane, gdy pasek kolorów jest zadokowany. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Wartość logiczna wskazująca, czy ma być wyświetlane okno dialogowe standardowy kolor systemu, czy okno dialogowe [CMFCColorDialog.](../../mfc/reference/cmfccolordialog-class.md) Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[OdNOŚNIK KOLORU,](/windows/win32/gdi/colorref) który przechowuje bieżący kolor automatyczny. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Obiekt [CMap,](../../mfc/reference/cmap-class.md) który kojarzy zestaw kolorów RGB z ich nazwami.|
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) wartości [COLORREF,](/windows/win32/gdi/colorref) który zawiera kolory, które są wyświetlane w formancie paska kolorów.|
|`m_ColorSelected`|Wartość [COLORREF,](/windows/win32/gdi/colorref) która jest kolorem wybranym obecnie przez użytkownika z kontrolki paska kolorów.|
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) of [COLORREF](/windows/win32/gdi/colorref) wartości, który zawiera kolory, które są obecnie używane w dokumencie.|
|`m_nCommandID`|Niepodpisana liczba całkowita, która jest identyfikatorem polecenia przycisku koloru.|
|`m_nHorzMargin`|Liczba całkowita, która jest marginesem poziomym między przyciskami kolorów w siatce kolorów.|
|`m_nHorzOffset`|Liczba całkowita, która jest odsunięciem w poziomie do środka przycisku koloru. Ta wartość jest istotna, jeśli przycisk wyświetla tekst lub obraz oprócz koloru.|
|`m_nNumColumns`|Liczba całkowita, czyli liczba kolumn w siatce sterowania kolorami na pasku kolorów.|
|`m_nNumColumnsVert`|Liczba całkowita, która jest liczbą kolumn w pionowo zorientowanej siatce kolorów.|
|`m_nNumRowsHorz`|Liczba całkowita, która jest liczbą kolumn w poziomo zorientowanej siatce kolorów.|
|`m_nRowHeight`|Liczba całkowita, która jest wysokością wiersza przycisków kolorów w siatce kolorów.|
|`m_nVertMargin`|Liczba całkowita, która jest pionowym marginesem między przyciskami kolorów w siatce kolorów.|
|`m_nVertOffset`|Liczba całkowita, która jest przesunięciem pionowym do środka przycisku koloru. Ta wartość jest istotna, jeśli przycisk wyświetla tekst lub obraz oprócz koloru.|
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md) kolorów, które są używane w formancie paska kolorów.|
|`m_pParentBtn`|Wskaźnik do [OBIEKTU CMFCColorButton,](../../mfc/reference/cmfccolorbutton-class.md) który jest elementem nadrzędnym bieżącego przycisku. Ta wartość jest znacząca, jeśli przycisk koloru znajduje się w hierarchii formantów paska narzędzi lub znajduje się w formancie siatki właściwości koloru.|
|`m_pParentRibbonBtn`|Wskaźnik do [obiektu CMFCRibbonColorButton,](../../mfc/reference/cmfcribboncolorbutton-class.md) który znajduje się na wstążce i jest przyciskiem nadrzędnym bieżącego przycisku. Ta wartość jest znacząca, jeśli przycisk koloru znajduje się w hierarchii formantów paska narzędzi lub znajduje się w formancie siatki właściwości koloru.|
|`m_pWndPropList`|Wskaźnik do [obiektu CMFCPropertyGridCtrl.](../../mfc/reference/cmfcpropertygridctrl-class.md)|
|`m_strAutoColor`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) czyli tekst wyświetlany na przycisku **Automatyczne.** Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) czyli tekst wyświetlany na przycisku kolorów dokumentu. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString,](../../atl-mfc-shared/reference/cstringt-class.md) który jest tekstem wyświetlanym na *drugim* przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Uwagi

Zazwyczaj obiekt nie jest `CMFCColorBar` tworzętny bezpośrednio. Zamiast tego [CMFCColorMenuButton Klasy](../../mfc/reference/cmfccolormenubutton-class.md) (używane w menu i paski narzędzi) lub [CMFCColorButton Klasy](../../mfc/reference/cmfccolorbutton-class.md) tworzy `CMFCColorBar` obiekt.

Klasa `CMFCColorBar` zapewnia następujące funkcje:

- Automatycznie dostosowuje listę kolorów dokumentu.

- Zapisuje i przywraca jego stan wraz ze stanem dokumentu.

- Zarządza przyciskiem "automatyczny".

- Używa [cmfccolorpickerctrl klasy](../../mfc/reference/cmfccolorpickerctrl-class.md) kontroli, aby wybrać kolor niestandardowy.

- Obsługuje stan "tear-off" (jeśli jest tworzony przy użyciu [CMFCColorMenuButton Klasy](../../mfc/reference/cmfccolormenubutton-class.md)).

Aby włączyć `CMFCColorBar` funkcje do aplikacji:

1. Utwórz przycisk menu regularnego i przypisz mu identyfikator, na przykład ID_CHAR_COLOR.

1. W klasie okna ramki należy zastąpić metodę [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) i zastąpić przycisk menu regularnego obiektem [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (wywołując [polecenie CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Ustaw wszystkie style i włączyć lub `CMFCColorBar` wyłączyć funkcje obiektu podczas tworzenia [klasy CMFCColorMenuButton.](../../mfc/reference/cmfccolormenubutton-class.md) Obiekt `CMFCColorMenuButton` dynamicznie tworzy `CMFCColorBar` obiekt po framework `CreatePopupMenu` wywołuje metodę.

Gdy użytkownik kliknie przycisk sterowania paskiem kolorów, struktura używa `ON_COMMAND` makra do powiadamiania nadrzędnego formantu paska kolorów. W makrze parametr identyfikator polecenia jest wartością przypisaną do przycisku sterowania paskiem kolorów w kroku 1 (ID_CHAR_COLOR w tym przykładzie). Aby uzyskać więcej informacji, zobacz [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)i [CMFCToolBar Class.](../../mfc/reference/cmfctoolbar-class.md)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonfigurować pasek `CMFCColorBar` kolorów przy użyciu różnych metod w klasie. Metody ustawiają marginesy poziome i pionowe, włączają drugi przycisk, tworzą okno formantu paska kolorów i ustawiają aktualnie wybrany kolor. W tym przykładzie jest częścią [new controls próbki](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Panel CBasePane](../../mfc/reference/cbasepane-class.md)

[Cpane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[Cmfctoolbar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[Cmfccolorbar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcolorbar.h

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Dostosowuje położenie przycisków kolorów na pasku kolorów.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę podczas przetwarzania komunikatów WM_SIZE.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Wskazuje, czy etykieta tekstowa przycisków kolorów może ulec zmianie.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FAŁSZ, co oznacza, że nie można modyfikować etykiet tekstowych. Zastąd w tej metodzie należy włączyć modyfikowanie etykiet tekstowych.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Wskazuje, czy obiekt sterujący paska kolorów może pojawić się na liście paska narzędzi podczas procesu dostosowywania.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość TRUE, co oznacza, że struktura może wyświetlać kontrolki paska kolorów podczas procesu dostosowywania. Zastąd w tej metodzie należy zaimplementować inne zachowanie.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::CalcSize

Wywoływana przez strukturę w ramach procesu obliczania układu.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock (własówk)*<br/>
[w] PRAWDA, aby określić, że kontrolka paska kolorów jest zadokowana w pionie; FAŁSZ, aby określić, że kontrolka paska kolorów jest zadokowana poziomo.

### <a name="return-value"></a>Wartość zwracana

Rozmiar tablicy przycisków kolorów w formancie paska kolorów.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

Konstruuje `CMFCColorBar` obiekt.

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

*Kolory*<br/>
[w] Tablica kolorów wyświetlanych na pasku kolorów.

*color*<br/>
[w] Początkowo wybrany kolor.

*lpszautoColor*<br/>
[w] Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub NULL.

Standardową etykietą przycisku automatycznego jest **Automatyczna**.

*lpszOtherColor*<br/>
[w] Etykieta tekstowa *drugiego* przycisku, który wyświetla więcej opcji kolorów lub NULL.

Standardową etykietą dla drugiego przycisku jest **Więcej kolorów...**.

*lpszDocKolory*<br/>
[w] Etykieta tekstowa przycisku kolory dokumentu. Paleta kolorów dokumentu zawiera listę wszystkich kolorów używanych obecnie przez dokument.

*lstDocKolory*<br/>
[w] Lista kolorów aktualnie używanych przez dokument.

*nKolumny*<br/>
[w] Liczba kolumn, które ma tablica kolorów.

*nRowsDockHorz*<br/>
[w] Liczba wierszy, które pasek kolorów ma, gdy jest zadokowany poziomo.

*nColDockVert (Wychw.*<br/>
[w] Liczba kolumn, które pasek kolorów ma, gdy jest zadokowany w pionie.

*kolorAutomatyczny*<br/>
[w] Domyślny kolor, który stosuje się po kliknięciu przycisku automatycznego.

*nKommandid*<br/>
[w] Identyfikator polecenia sterowania paska kolorów.

*pParentBtn*<br/>
[w] Wskaźnik do przycisku nadrzędnego.

*src*<br/>
[w] Istniejący `CMFCColorBar` obiekt do skopiowania `CMFCColorBar` do nowego obiektu.

*identyfikator uiCommandID*<br/>
[w] Identyfikator polecenia.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContextToSize

Oblicza pionowe i poziome marginesy, które są wymagane do przechowywania przycisków na pasku kolorów i dostosowuje położenie tych przycisków.

```cpp
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bWzdłebuttony*|[w] PRAWDA, aby określić, że kształt przycisków na formancie paska kolorów jest kwadratowy; w przeciwnym razie FALSE. Wartością domyślną jest PRAWDA.|
|*bNaty centrowe*|[w] PRAWDA, aby określić, że zawartość na ścianie przycisku sterowania paskiem koloru jest wyśrodkowany; w przeciwnym razie FALSE. Wartością domyślną jest PRAWDA.|

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Utwórz

Tworzy okno formantu paska kolorów `CMFCColorBar` i dołącza je do obiektu.

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
[w] Wskaźnik do okna nadrzędnego.

*Dwstyle*<br/>
[w] Bitowa kombinacja (OR) [stylów okien](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*Nid*<br/>
[w] Identyfikator polecenia.

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów. Wartość domyślna to NULL.

*nKolumny*<br/>
[w] Liczba kolumn w formancie paska kolorów. Wartość domyślna to 0.

*nRowsDockHorz*<br/>
[w] Liczba wierszy na pasku kolorów jest kontrolowana, gdy jest zadokowany poziomo. Wartość domyślna to 0.

*nColDockVert (Wychw.*<br/>
[w] Liczba kolumn na pasku kolorów kontroluje, gdy jest zadokowany w pionie. Wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby skonstruować `CMFCColorBar` obiekt, wywołać konstruktora klasy następnie tej metody. Metoda `Create` tworzy formant systemu Windows i inicjuje listę kolorów.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::CreateControl

Tworzy okno formantu paska kolorów, dołącza je do `CMFCColorBar` obiektu i umożliwia zmiana rozmiaru okna formantu w celu umieszczenia określonej palety kolorów.

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
[w] Wskaźnik do okna nadrzędnego. Nie może być null.

*Rect*<br/>
[w] Prostokąt ograniczający, który określa, gdzie ma być rysowany formant paska kolorów.

*Nid*<br/>
[w] Identyfikator sterowania.

*nKolumny*<br/>
[w] Idealna liczba kolumn w formancie paska kolorów. Ta metoda modyfikuje tę liczbę, aby dopasować określoną paletę kolorów. Wartość domyślna to -1, co oznacza, że ten parametr nie jest określony.

*pPalette (ppalette)*<br/>
[w] Wskaźnik do palety kolorów lub NULL. Jeśli ten parametr ma wartość NULL, ta metoda oblicza rozmiar formantu paska kolorów tak, jakby określono 20 kolorów. Wartość domyślna to NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda powiedzie się; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa parametrów *rect*, *nColumns*i *pPalette* do obliczania odpowiedniej liczby lub wierszy i kolumn w formancie paska kolorów, a następnie wywołuje [metodę CMFCColorBar::Create.](#create)

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::Utwórzpalette

Inicjuje paletę z kolorami w określonej tablicy kolorów.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*arKolory*|[w] Tablica kolorów.|
|*Palety*|[w] Paleta kolorów.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Pokazuje lub ukrywa przycisk automatyczny.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub NULL.

Standardową etykietą przycisku automatycznego jest **Automatyczna**.

*kolorAutomatyczny*<br/>
[w] Domyślny kolor, który stosuje się po kliknięciu przycisku automatycznego.

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć przycisk automatyczny; FALSE, aby wyłączyć przycisk automatyczny. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Etykieta tekstowa przycisku automatycznego jest usuwana, jeśli parametr *lpszLabel* ma wartość NULL lub parametr *bEnable* to FALSE.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Włącza lub wyłącza wyświetlanie okna dialogowego, które pozwala użytkownikowi wybrać więcej kolorów.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta tekstowa *drugiego* przycisku, który wyświetla więcej opcji kolorów lub NULL.

Standardową etykietą dla tego przycisku jest **Więcej kolorów...**.

*bAltColorDlg*<br/>
[w] FUNKCJA TRUE, aby wyświetlić okno dialogowe [CMFCColorDialog;](../../mfc/reference/cmfccolordialog-class.md) FALSE, aby wyświetlić standardowe okno dialogowe [CColorDialog.](../../mfc/reference/ccolordialog-class.md) Wartością domyślną jest PRAWDA.

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć przycisk; FALSE, aby wyłączyć przycisk. Wartością domyślną jest PRAWDA.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor

Pobiera aktualnie zaznaczony kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Aktualnie wybrany kolor.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Oblicza liczbę wierszy i kolumn w siatce formantu paska kolorów.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bVertDock (własówk)*|[w] PRAWDA, aby wykonać obliczenia dla formantu paska kolorów zadokowanego pionowo; w przeciwnym razie należy wykonać obliczenia dla formantu zadokowanego poziomo.|

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize,](../../atl-mfc-shared/reference/csize-class.md) którego `cx` komponent zawiera liczbę `cy` kolumn i którego składnik zawiera liczbę wierszy.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID

Pobiera identyfikator polecenia bieżącego paska kolorów.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze nowy kolor, struktura wysyła identyfikator polecenia w WM_COMMAND komunikat, aby `CMFCColorBar` powiadomić rodzica obiektu.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Oblicza dodatkową wysokość, która wymaga bieżącego paska kolorów do wyświetlania różnych elementów interfejsu użytkownika, takich jak **inne** kolory przycisku lub dokumentu.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nNumKolumny*|[w] Jeśli kontrolka paska kolorów zawiera kolory dokumentu, liczba kolumn do wyświetlenia w siatce kolorów dokumentu. W przeciwnym razie ta wartość nie jest używana.|

### <a name="return-value"></a>Wartość zwracana

Obliczona dodatkowa wysokość, która jest wymagana.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Pobiera kolor, który oznacza, że przycisk kolor ma fokus; oznacza to, że przycisk jest *gorący*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Pobiera margines poziomy, czyli odstęp między lewą lub prawą komórką kolorów a granicą obszaru klienta.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Wartość zwracana

Margines poziomy.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Pobiera margines pionowy, czyli odstęp między górną lub dolną komórką kolorów a granicą obszaru klienta.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Margines pionowy.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors

Inicjuje tablicę kolorów z kolorami w określonej palecie lub z domyślną paletą systemu.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pPalette (ppalette)*|[w] Wskaźnik do obiektu palety lub NULL. Jeśli ten parametr ma wartość NULL, ta metoda używa domyślnej palety systemu operacyjnego.|
|*arKolory*|[w] Tablica kolorów.|

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy kolorów.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::IsTearOff

Wskazuje, czy bieżący pasek kolorów można dokować.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżąca kontrolka paska kolorów jest dokowania; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka paska kolorów można dokować, można ją oderwać od paska sterowania i zadokować w innym miejscu.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey

Wywoływana przez strukturę, gdy użytkownik naciśnie przycisk klawiatury.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*Nchar*<br/>
[w] Kod klucza wirtualnego dla klucza, który użytkownik nacisnął.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda przetwarza określony klucz; w przeciwnym razie FALSE.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Wywoływane przez strukturę, aby zamknąć hierarchię wyskakujących formantów.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pButton (przycisk)*|[w] Wskaźnik do formantu, który znajduje się na pasku narzędzi.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Wywoływane przez strukturę, aby włączyć lub wyłączyć element interfejsu użytkownika formantu paska kolorów przed elementem jest wyświetlany.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
[w] Wskaźnik do okna, które zawiera element interfejsu użytkownika do aktualizacji.

*bDisableIfNoHndler*<br/>
[w] TRUE, aby wyłączyć element interfejsu użytkownika, jeśli żaden program obsługi nie jest zdefiniowany na mapie wiadomości; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Gdy użytkownik aplikacji kliknie element interfejsu użytkownika, element musi wiedzieć, czy powinien być wyświetlany jako włączony lub wyłączony. Miejsce docelowe komunikatu polecenia zawiera te informacje, implementując program obsługi ON_UPDATE_COMMAND_UI polecenia. Ta metoda służy do przetwarzania polecenia. Aby uzyskać więcej informacji, zobacz [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Otwiera kolorowe okno dialogowe.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault (Domyślny kolor)*<br/>
[w] Kolor wybrany domyślnie po otwarciu okna dialogowego kolor.

*colorRes*<br/>
[na zewnątrz] Kolor wybrany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli użytkownik wybrał kolor; FAŁSZ, jeśli użytkownik anulował kolorowe okno dialogowe.

### <a name="remarks"></a>Uwagi

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Odbuduj

Całkowicie przerysowuje kontrolki paska kolorów.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::Wybierzpalette

Ustawia paletę logiczną określonego kontekstu urządzenia na paletę przycisku nadrzędnego bieżącego paska kolorów.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pdc*|[w] Wskaźnik do kontekstu urządzenia przycisku nadrzędnego bieżącego paska kolorów.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do palety, która jest zastępowana przez paletę przycisku nadrzędnego bieżącego paska kolorów.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar::SetColor

Ustawia aktualnie zaznaczony kolor.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość koloru RGB.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName

Ustawia nową nazwę dla określonego koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[w] Wartość RGB koloru.

*nazwa strName*<br/>
[w] Nowa nazwa określonego koloru.

### <a name="remarks"></a>Uwagi

Ta metoda zmienia nazwę określonego koloru `CMFCColorBar` we wszystkich obiektach w aplikacji.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID

Ustawia nowy identyfikator polecenia dla kontrolki paska kolorów.

```cpp
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nKommandid*<br/>
[w] Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zmodyfikować identyfikator polecenia formantu paska kolorów i powiadomić okno nadrzędne formantu, że identyfikator został zmieniony.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Ustawia listę kolorów używanych w bieżącym dokumencie.

```cpp
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszCaption (własnowie)*<br/>
[w] Podpis wyświetlany, gdy kontrolka paska kolorów nie jest zadokowana.

*lstDocKolory*<br/>
[w] Lista kolorów, która zastępuje bieżące kolory dokumentu.

*bShowWhenDocked*<br/>
[w] PRAWDA, aby wyświetlić kolory dokumentu, gdy kontrolka paska kolorów jest zadokowana; w przeciwnym razie FALSE. Wartością domyślną jest FAŁSZ.

### <a name="remarks"></a>Uwagi

*Kolory dokumentu* to kolory, które są obecnie używane w dokumencie. Struktura automatycznie przechowuje listę kolorów dokumentu, ale można użyć tej metody, aby zmodyfikować listę.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Ustawia margines poziomy, który jest spacją między lewą lub prawą komórką kolorów a granicą obszaru klienta.

```cpp
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMargin*<br/>
[w] Margines poziomy w pikselach.

### <a name="remarks"></a>Uwagi

Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor ustawia margines poziomy do 4 pikseli.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar::SetPropList

Ustawia `m_pWndPropList` element członkowski chronionych danych na określony wskaźnik do formantu siatki właściwości.

```cpp
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pWndList (Lista pWnd)*|[w] Wskaźnik do obiektu sterującego siatką właściwości.|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Ustawia margines pionowy, czyli odstęp między górną lub dolną komórką kolorów a granicą obszaru klienta.

```cpp
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin (nVertMargin)*<br/>
[w] Margines pionowy w pikselach.

### <a name="remarks"></a>Uwagi

Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) konstruktor ustawia margines pionowy do 4 pikseli.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Żąda okna ramki, które jest właścicielem formantu paska kolorów, aby zaktualizować wiersz komunikatu na pasku stanu.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*identyfikator uiCmdId*<br/>
[w] Identyfikator polecenia. (Ten parametr jest ignorowany).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat WM_SETMESSAGESTRING do właściciela formantu paska kolorów.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
