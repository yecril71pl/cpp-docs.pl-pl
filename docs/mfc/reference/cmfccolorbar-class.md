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
ms.openlocfilehash: 25bfe3ef67fcca7708179d1a316af05b3ba49dda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505429"
---
# <a name="cmfccolorbar-class"></a>Klasa CMFCColorBar

`CMFCColorBar` Klasa reprezentuje pasek sterowania dokowaniem, który może wybierać kolory w dokumencie lub aplikacji.

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
|[CMFCColorBar::ContextToSize](#contexttosize)|Oblicza marginesy pionowe i poziome, które są wymagane, aby zawierały przyciski w kontrolce pasek koloru, a następnie dostosowuje lokalizację tych przycisków.|
|[CMFCColorBar:: IsControl](#createcontrol)|Tworzy okno kontrolki pasek koloru, dołącza je do `CMFCColorBar` obiektu i zmienia rozmiar kontrolki tak, aby zawierała określoną paletę kolorów.|
|[CMFCColorBar:: Create](#create)|Tworzy okno kontrolki pasek koloru i dołącza je do `CMFCColorBar` obiektu.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Pokazuje lub ukrywa przycisk Automatyczny.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Włącza lub wyłącza wyświetlanie okna dialogowego, które pozwala użytkownikowi wybrać więcej kolorów.|
|[CMFCColorBar:: GetColor](#getcolor)|Pobiera aktualnie wybrany kolor.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Pobiera identyfikator polecenia bieżącej kontrolki paska kolorów.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Pobiera kolor, który oznacza, że przycisk koloru ma fokus. oznacza to, że przycisk jest *aktywny*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Pobiera pionowy margines, czyli odstęp między komórką koloru w lewo lub w prawo i granicą obszaru klienta.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Pobiera pionowy margines, czyli spację między górną lub dolną komórką koloru a granicą obszaru klienta.|
|[CMFCColorBar::IsTearOff](#istearoff)|Wskazuje, czy bieżący pasek kolorów jest było dokować.|
|[CMFCColorBar:: SetColor](#setcolor)|Ustawia kolor, który jest aktualnie wybrany.|
|[CMFCColorBar:: SetColorName](#setcolorname)|Ustawia nową nazwę określonego koloru.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Ustawia nowy identyfikator polecenia dla kontrolki paska kolorów.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Ustawia listę kolorów, które są używane w bieżącym dokumencie.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Ustawia margines poziomy, czyli odstęp między komórką koloru w lewo lub w prawo i granicą obszaru klienta.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Ustawia pionowy margines, czyli spację między górną lub dolną komórką koloru a granicą obszaru klienta.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Dostosowuje położenie przycisków kolorów w formancie paska kolorów.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Wskazuje, czy etykieta tekstowa przycisków kolorów może ulec zmianie.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Wskazuje, czy obiekt kontrolki pasek koloru może być wyświetlany na liście pasków narzędzi podczas procesu dostosowywania.|
|[CMFCColorBar::CalcSize](#calcsize)|Wywoływane przez platformę jako część procesu obliczeń układu.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicjuje paletę z kolorami w określonej tablicy kolorów.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Oblicza liczbę wierszy i kolumn w siatce kontrolki paska kolorów.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Oblicza dodatkową wysokość wymaganą przez bieżący pasek kolorów do wyświetlania różnych elementów interfejsu użytkownika, takich jak **inny** przycisk, kolory dokumentu i tak dalej.|
|[CMFCColorBar::InitColors](#initcolors)|Inicjuje tablicę kolorów z kolorami określonej palety lub domyślną paletą systemu.|
|[CMFCColorBar::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Wywoływane przez platformę, aby zamknąć hierarchię formantów podręcznych.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Wywoływane przez platformę, aby włączyć lub wyłączyć element interfejsu użytkownika kontrolki paska kolorów przed wyświetleniem elementu.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otwiera okno dialogowe koloru.|
|[CMFCColorBar:: Rebuild](#rebuild)|Całkowicie odświeża kontrolkę pasek koloru.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Ustawia logiczną paletę określonego kontekstu urządzenia do palety przycisku nadrzędnego bieżącej kontrolki paska kolorów.|
|[CMFCColorBar::SetPropList](#setproplist)|Ustawia element członkowski danych chronionychnaokreślonywskaźnikdokontrolkisiatkiwłaściwości.`m_pWndPropList`|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Żąda okna ramki, które jest właścicielem kontrolki pasek koloru, aby zaktualizować wiersz komunikatu na pasku stanu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|`m_bInternal`|Pole logiczne, które określa, czy zdarzenia myszy są przetwarzane. Zazwyczaj zdarzenia myszy są przetwarzane, gdy to pole ma wartość TRUE, a tryb dostosowywania ma wartość FALSE.|
|`m_bIsEnabled`|Wartość logiczna wskazująca, czy kontrolka jest włączona.|
|`m_bIsTearOff`|Wartość logiczna wskazująca, czy kontrolka pasek koloru obsługuje dokowanie.|
|`m_BoxSize`|Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , który określa rozmiar komórki w siatce paska kolorów.|
|`m_bShowDocColorsWhenDocked`|Wartość logiczna wskazująca, czy kolory dokumentu mają być wyświetlane, gdy pasek koloru jest zadokowany. Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Wartość logiczna wskazująca, czy ma być wyświetlane okno dialogowe standardowy kolor systemu czy okno dialogowe [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) . Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref) przechowujący bieżący automatyczny kolor. Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Obiekt [CMAP](../../mfc/reference/cmap-class.md) , który kojarzy zestaw kolorów RGB z ich nazwami.|
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) wartości [COLORREF](/windows/win32/gdi/colorref) , które zawierają kolory, które są wyświetlane w kontrolce pasek koloru.|
|`m_ColorSelected`|Wartość [COLORREF](/windows/win32/gdi/colorref) , która jest kolorem aktualnie wybranym przez użytkownika z kontrolki pasek koloru.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) wartości [COLORREF](/windows/win32/gdi/colorref) , które zawierają kolory, które są obecnie używane w dokumencie.|
|`m_nCommandID`|Liczba całkowita bez znaku, która jest IDENTYFIKATORem polecenia przycisku koloru.|
|`m_nHorzMargin`|Liczba całkowita będąca poziomą margines między przyciskami koloru w siatce kolorów.|
|`m_nHorzOffset`|Liczba całkowita, która jest przesunięciem w poziomie do środka przycisku koloru. Ta wartość jest istotna, jeśli przycisk wyświetla tekst lub obraz oprócz koloru.|
|`m_nNumColumns`|Liczba całkowita, która jest liczbą kolumn na pasku koloru kontrolki siatki kolorów.|
|`m_nNumColumnsVert`|Liczba całkowita, która jest liczbą kolumn w siatce zorientowanej w pionie kolorów.|
|`m_nNumRowsHorz`|Liczba całkowita, która jest liczbą kolumn w siatce zorientowanej poziomo kolorów.|
|`m_nRowHeight`|Liczba całkowita, która jest wysokością wiersza przycisków koloru w siatce kolorów.|
|`m_nVertMargin`|Liczba całkowita, która jest pionowym marginesem między przyciskami koloru w siatce kolorów.|
|`m_nVertOffset`|Liczba całkowita, która jest przesunięciem pionowym do środka przycisku koloru. Ta wartość jest istotna, jeśli przycisk wyświetla tekst lub obraz oprócz koloru.|
|`m_Palette`|[CPalette](../../mfc/reference/cpalette-class.md) kolorów, które są używane w kontrolce pasek koloru.|
|`m_pParentBtn`|Wskaźnik do obiektu [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) , który jest elementem nadrzędnym bieżącego przycisku. Ta wartość jest istotna, jeśli przycisk Color znajduje się w hierarchii formantów Toolbar lub znajduje się w kontrolce siatki właściwości koloru.|
|`m_pParentRibbonBtn`|Wskaźnik do obiektu [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) , który znajduje się na Wstążce i jest przyciskiem nadrzędnym bieżącego przycisku. Ta wartość jest istotna, jeśli przycisk Color znajduje się w hierarchii formantów Toolbar lub znajduje się w kontrolce siatki właściwości koloru.|
|`m_pWndPropList`|Wskaźnik do obiektu [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) .|
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , który jest tekstem wyświetlanym na przycisku **automatyczny** . Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , który jest tekstem wyświetlanym na przycisku kolory dokumentu. Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) , który jest tekstem wyświetlanym na *drugim* przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Uwagi

Zazwyczaj nie utworzysz `CMFCColorBar` obiektu bezpośrednio. Zamiast tego [Klasa CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (używana w menu i paskach narzędzi) lub [Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) tworzy `CMFCColorBar` obiekt.

`CMFCColorBar` Klasa zapewnia następujące funkcje:

- Automatycznie dostosowuje listę kolorów dokumentu.

- Zapisuje i przywraca stan wraz ze stanem dokumentu.

- Zarządza przyciskiem "automatyczny".

- Używa kontrolki [klasy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) w celu wybrania koloru niestandardowego.

- Obsługuje stan "Odrywane" (jeśli jest tworzony przy użyciu [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Aby włączyć `CMFCColorBar` funkcje do aplikacji:

1. Utwórz przycisk menu regularnego i przypisz mu identyfikator, na przykład ID_CHAR_COLOR.

1. W klasie okna ramki Zastąp metodę [CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) i Zastąp przycisk menu zwykłego obiektem [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (przez wywołanie [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Ustaw wszystkie style i Włącz lub wyłącz funkcje `CMFCColorBar` obiektu podczas tworzenia [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) . Obiekt dynamicznie tworzy obiekt po wywołaniem `CreatePopupMenu`metodyprzezstrukturę. `CMFCColorBar` `CMFCColorMenuButton`

Gdy użytkownik kliknie przycisk kontrolki pasek koloru, struktura używa `ON_COMMAND` makra, aby powiadomić element nadrzędny kontrolki paska kolorów. W makrze parametr identyfikatora polecenia jest wartością, którą przypisano do przycisku kontrolki pasek koloru w kroku 1 (ID_CHAR_COLOR w tym przykładzie). Aby uzyskać więcej informacji, zobacz klasy [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), Klasa [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md), Klasa [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md), [Klasa CFrameWndEx](../../mfc/reference/cframewndex-class.md)i klasy [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonfigurować pasek koloru przy użyciu różnych metod w `CMFCColorBar` klasie. Metody ustawiają marginesy w poziomie i w pionie, włączają drugi przycisk, tworzą okno kontrolki paska kolorów i ustawia aktualnie wybrany kolor. Ten przykład jest częścią [nowych kontrolek](../../overview/visual-cpp-samples.md).

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

**Nagłówek:** afxcolorbar. h

##  <a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Dostosowuje położenie przycisków kolorów w formancie paska kolorów.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Uwagi

Ta metoda jest wywoływana przez platformę podczas przetwarzania komunikatów WM_SIZE.

##  <a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Wskazuje, czy etykieta tekstowa przycisków kolorów może ulec zmianie.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze FAŁSZ.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FALSE, co oznacza, że nie można modyfikować etykiet tekstu. Zastąp tę metodę, aby włączyć modyfikowanie etykiet tekstowych.

##  <a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Wskazuje, czy obiekt kontrolki pasek koloru może być wyświetlany na liście pasków narzędzi podczas procesu dostosowywania.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze prawda.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość TRUE, co oznacza, że struktura może wyświetlać kontrolkę pasek koloru podczas procesu dostosowywania. Zastąp tę metodę, aby zaimplementować inne zachowanie.

##  <a name="calcsize"></a>CMFCColorBar::CalcSize

Wywoływane przez platformę jako część procesu obliczeń układu.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parametry

*bVertDock*<br/>
podczas PRAWDA, aby określić, że kontrolka pasek koloru jest zadokowana pionowo. Wartość FALSE, aby określić, że kontrolka pasek koloru jest zadokowana w poziomie.

### <a name="return-value"></a>Wartość zwracana

Rozmiar tablicy przycisków kolorów w kontrolce paska kolorów.

##  <a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

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

*świat*<br/>
podczas Tablica kolorów, które są wyświetlane w strukturze na kontrolce paska kolorów.

*Kolor*<br/>
podczas Początkowo wybrany kolor.

*lpszAutoColor*<br/>
podczas Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub wartość null.

Standardowa etykieta przycisku automatycznego jest **Automatyczna**.

*lpszOtherColor*<br/>
podczas Etykieta tekstowa *drugiego* przycisku, która wyświetla więcej opcji kolorów lub wartość null.

Standardowa etykieta dla drugiego przycisku ma **więcej kolorów..** .

*lpszDocColors*<br/>
podczas Etykieta tekstowa przycisku kolory dokumentu. W palecie kolory dokumentu są wyświetlane wszystkie kolory, których aktualnie używa dokument.

*lstDocColors*<br/>
podczas Lista kolorów używanych obecnie przez dokument.

*nColumns*<br/>
podczas Liczba kolumn, które ma Tablica kolorów.

*nRowsDockHorz*<br/>
podczas Liczba wierszy, po których pasek koloru jest zadokowany w poziomie.

*nColDockVert*<br/>
podczas Liczba kolumn, które znajdują się na pasku kolorów, gdy jest zadokowany w pionie.

*colorAutomatic*<br/>
podczas Domyślny kolor stosowany przez platformę po kliknięciu przycisku automatyczne.

*nCommandID*<br/>
podczas Identyfikator polecenia kontrolki paska kolorów.

*pParentBtn*<br/>
podczas Wskaźnik do przycisku nadrzędnego.

*SRC*<br/>
podczas Istniejący `CMFCColorBar` obiekt do skopiowania do nowego `CMFCColorBar` obiektu.

*uiCommandID*<br/>
podczas Identyfikator polecenia.

##  <a name="contexttosize"></a>CMFCColorBar::ContextToSize

Oblicza marginesy pionowe i poziome, które są wymagane do zawiera przyciski w kontrolce pasek koloru i dostosowuje lokalizację tych przycisków.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bSquareButtons*|podczas PRAWDA, aby określić, że kształt przycisków na kontrolce pasek koloru jest kwadratowy; w przeciwnym razie FALSE. Wartość domyślna to TRUE.|
|*bCenterButtons*|podczas Wartość TRUE, aby określić, że zawartość na stronie przycisku kontrolki paska koloru jest wyśrodkowana; w przeciwnym razie FALSE. Wartość domyślna to TRUE.|

### <a name="remarks"></a>Uwagi

##  <a name="create"></a>CMFCColorBar:: Create

Tworzy okno kontrolki pasek koloru i dołącza je do `CMFCColorBar` obiektu.

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
podczas Wskaźnik do okna nadrzędnego.

*dwStyle*<br/>
podczas Bitowa kombinacja (lub) [stylów okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
podczas Identyfikator polecenia.

*pPalette*<br/>
podczas Wskaźnik do palety kolorów. Wartość domyślna to NULL.

*nColumns*<br/>
podczas Liczba kolumn w kontrolce pasek koloru. Wartość domyślna to 0.

*nRowsDockHorz*<br/>
podczas Liczba wierszy w formancie paska kolorów, gdy jest zadokowana w poziomie. Wartość domyślna to 0.

*nColDockVert*<br/>
podczas Liczba kolumn w kontrolce paska kolorów, gdy jest zadokowany w pionie. Wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby skonstruować `CMFCColorBar` obiekt, Wywołaj konstruktora klasy, a następnie tę metodę. `Create` Metoda tworzy formant systemu Windows i inicjuje listę kolorów.

##  <a name="createcontrol"></a>CMFCColorBar:: IsControl

Tworzy okno kontrolki pasek koloru, dołącza je do `CMFCColorBar` obiektu i zmienia rozmiar okna sterowania, aby zawierało określoną paletę kolorów.

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
podczas Wskaźnik do okna nadrzędnego. Nie może mieć wartości NULL.

*cinania*<br/>
podczas Prostokąt ograniczający, który określa, gdzie należy narysować kontrolkę pasek koloru.

*nID*<br/>
podczas Identyfikator formantu.

*nColumns*<br/>
podczas Idealna liczba kolumn w kontrolce pasek koloru. Ta metoda modyfikuje tę liczbę, aby dopasować ją do określonej palety kolorów. Wartość domyślna to-1, co oznacza, że ten parametr nie jest określony.

*pPalette*<br/>
podczas Wskaźnik do palety kolorów lub wartości NULL. Jeśli ten parametr ma wartość NULL, ta metoda oblicza rozmiar kontrolki pasek koloru, tak jakby określono 20 kolorów. Wartość domyślna to NULL.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda używa parametrów *Rect*, *nColumns*i *pPalette* do obliczenia odpowiedniej liczby lub wierszy i kolumn w kontrolce pasek koloru, a następnie wywołuje metodę [CMFCColorBar:: Create](#create) .

##  <a name="createpalette"></a>CMFCColorBar:: ispalette

Inicjuje paletę z kolorami w określonej tablicy kolorów.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*arColors*|podczas Tablica kolorów.|
|*palette*|podczas Paleta kolorów.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

##  <a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Pokazuje lub ukrywa przycisk Automatyczny.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Etykieta tekstowa *automatycznego* (domyślnego) przycisku koloru lub wartość null.

Standardowa etykieta przycisku automatycznego jest **Automatyczna**.

*colorAutomatic*<br/>
podczas Domyślny kolor stosowany przez platformę po kliknięciu przycisku automatyczne.

*bEnable*<br/>
podczas Wartość TRUE, aby włączyć przycisk Automatyczny; Wartość FALSE powoduje wyłączenie przycisku automatycznego. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Etykieta tekstowa przycisku automatycznego jest usuwana, jeśli parametr *lpszLabel* ma wartość null lub parametr *bEnable* ma wartość false.

##  <a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Włącza lub wyłącza wyświetlanie okna dialogowego, które pozwala użytkownikowi wybrać więcej kolorów.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*lpszLabel*<br/>
podczas Etykieta tekstowa *drugiego* przycisku, która wyświetla więcej opcji kolorów lub wartość null.

Etykieta standardowa tego przycisku ma **więcej kolorów..** .

*bAltColorDlg*<br/>
podczas Wartość TRUE, aby wyświetlić okno dialogowe [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; Wartość FALSE powoduje wyświetlenie standardowego okna dialogowego [CColorDialog](../../mfc/reference/ccolordialog-class.md) . Wartość domyślna to TRUE.

*bEnable*<br/>
podczas Wartość TRUE, aby włączyć przycisk; Wartość FALSE powoduje wyłączenie przycisku. Wartość domyślna to TRUE.

##  <a name="getcolor"></a>CMFCColorBar:: GetColor

Pobiera aktualnie wybrany kolor.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Aktualnie wybrany kolor.

##  <a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Oblicza liczbę wierszy i kolumn w siatce kontrolki paska kolorów.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*bVertDock*|podczas Wartość TRUE, aby wykonać obliczenia dla kontrolki zadokowanego paska kolorów w pionie; w przeciwnym razie wykonaj obliczenia dla kontrolki zadokowanej poziomo.|

### <a name="return-value"></a>Wartość zwracana

Obiekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , którego `cx` składnik zawiera liczbę kolumn, których `cy` składnik zawiera liczbę wierszy.

##  <a name="getcommandid"></a>CMFCColorBar::GetCommandID

Pobiera identyfikator polecenia bieżącej kontrolki paska kolorów.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Gdy użytkownik wybierze nowy kolor, struktura wyśle identyfikator polecenia w wiadomości WM_COMMAND, aby powiadomić element nadrzędny `CMFCColorBar` obiektu.

##  <a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Oblicza dodatkową wysokość wymaganą przez bieżący pasek kolorów do wyświetlania różnych elementów interfejsu użytkownika, takich jak **inne** kolory przycisku lub dokumentu.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*nNumColumns*|podczas Jeśli kontrolka pasek koloru zawiera kolory dokumentu, liczba kolumn do wyświetlenia w siatce kolorów dokumentu. W przeciwnym razie ta wartość nie jest używana.|

### <a name="return-value"></a>Wartość zwracana

Obliczona dodatkowa wysokość, która jest wymagana.

##  <a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Pobiera kolor, który oznacza, że przycisk koloru ma fokus. oznacza to, że przycisk jest *aktywny*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość RGB.

### <a name="remarks"></a>Uwagi

##  <a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Pobiera pionowy margines, czyli odstęp między komórką koloru w lewo lub w prawo i granicą obszaru klienta.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Wartość zwracana

Margines poziomy.

##  <a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Pobiera pionowy margines, czyli spację między górną lub dolną komórką koloru a granicą obszaru klienta.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Wartość zwracana

Pionowy margines.

##  <a name="initcolors"></a>CMFCColorBar::InitColors

Inicjuje tablicę kolorów z kolorami z określonej palety lub z domyślną paletą systemu.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pPalette*|podczas Wskaźnik do obiektu palety lub ma wartość NULL. Jeśli ten parametr ma wartość NULL, ta metoda używa domyślnej palety systemu operacyjnego.|
|*arColors*|podczas Tablica kolorów.|

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w tablicy kolorów.

##  <a name="istearoff"></a>CMFCColorBar::IsTearOff

Wskazuje, czy bieżący pasek kolorów jest było dokować.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli bieżącym formantem paska kolorów jest było dokować; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Jeśli kontrolka pasek koloru jest było dokowaća, można ją wycofać z paska sterowania i zadokować w innej lokalizacji.

##  <a name="onkey"></a>CMFCColorBar::OnKey

Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parametry

*nChar*<br/>
podczas Kod klucza wirtualnego dla klawisza naciśniętego przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli ta metoda przetwarza określony klucz; w przeciwnym razie FALSE.

##  <a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Wywoływane przez platformę, aby zamknąć hierarchię wyskakujących kontrolek.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pButton*|podczas Wskaźnik do kontrolki, która znajduje się na pasku narzędzi.|

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli ta metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

##  <a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Wywoływane przez platformę, aby włączyć lub wyłączyć element interfejsu użytkownika kontrolki paska kolorów przed wyświetleniem elementu.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parametry

*pTarget*<br/>
podczas Wskaźnik do okna zawierającego element interfejsu użytkownika do zaktualizowania.

*bDisableIfNoHndler*<br/>
podczas Wartość TRUE powoduje wyłączenie elementu User-Interface, jeśli nie zdefiniowano procedury obsługi w mapie komunikatów; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Gdy użytkownik aplikacji kliknie element interfejs użytkownika, element musi wiedzieć, czy powinien być wyświetlany jako włączony czy wyłączony. Obiekt docelowy komunikatu polecenia dostarcza te informacje przez implementację procedury obsługi poleceń ON_UPDATE_COMMAND_UI. Użyj tej metody, aby pomóc w przetwarzaniu polecenia. Aby uzyskać więcej informacji, zobacz [Klasa CCmdUI](../../mfc/reference/ccmdui-class.md).

##  <a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Otwiera okno dialogowe koloru.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parametry

*colorDefault*<br/>
podczas Kolor wybrany domyślnie, gdy zostanie otwarte okno dialogowe koloru.

*colorRes*<br/>
określoną Kolor wybrany przez użytkownika.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli użytkownik zaznaczył kolor; FAŁSZ, jeśli użytkownik anulował okno dialogowe koloru.

### <a name="remarks"></a>Uwagi

##  <a name="rebuild"></a>CMFCColorBar:: Rebuild

Całkowicie odświeża kontrolkę pasek koloru.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>CMFCColorBar::SelectPalette

Ustawia logiczną paletę określonego kontekstu urządzenia do palety przycisku nadrzędnego bieżącej kontrolki paska kolorów.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pDC*|podczas Wskaźnik do kontekstu urządzenia przycisku nadrzędnego bieżącej kontrolki paska kolorów.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do palety, która jest zastępowana przez paletę przycisku nadrzędnego bieżącej kontrolki paska kolorów.

##  <a name="setcolor"></a>CMFCColorBar:: SetColor

Ustawia kolor, który jest aktualnie wybrany.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Wartość koloru RGB.

##  <a name="setcolorname"></a>CMFCColorBar:: SetColorName

Ustawia nową nazwę określonego koloru.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*Kolor*<br/>
podczas Wartość RGB koloru.

*strName*<br/>
podczas Nowa nazwa określonego koloru.

### <a name="remarks"></a>Uwagi

Ta metoda zmienia nazwę określonego koloru we wszystkich `CMFCColorBar` obiektach w aplikacji.

##  <a name="setcommandid"></a>CMFCColorBar::SetCommandID

Ustawia nowy identyfikator polecenia dla kontrolki paska kolorów.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parametry

*nCommandID*<br/>
podczas Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zmodyfikować identyfikator polecenia kontrolki pasek koloru i powiadomienia okno nadrzędne kontrolki, że identyfikator został zmieniony.

##  <a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Ustawia listę kolorów, które są używane w bieżącym dokumencie.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszCaption*<br/>
podczas Podpis wyświetlany, gdy kontrolka pasek koloru nie jest zadokowany.

*lstDocColors*<br/>
podczas Lista kolorów, które zastępują kolory bieżącego dokumentu.

*bShowWhenDocked*<br/>
podczas PRAWDA, aby pokazać kolory dokumentu, gdy kontrolka pasek koloru jest zadokowany. w przeciwnym razie FALSE. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

*Kolory dokumentu* to kolory, które są obecnie używane w dokumencie. Struktura automatycznie zachowuje listę kolorów dokumentu, ale można użyć tej metody do zmodyfikowania listy.

##  <a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Ustawia margines poziomy, czyli odstęp między komórką koloru w lewo lub w prawo i granicą obszaru klienta.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parametry

*nHorzMargin*<br/>
podczas Margines poziomy w pikselach.

### <a name="remarks"></a>Uwagi

Domyślnie Konstruktor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) ustawia margines poziomy na 4 piksele.

##  <a name="setproplist"></a>CMFCColorBar::SetPropList

Ustawia element członkowski danych chronionychnaokreślonywskaźnikdokontrolkisiatkiwłaściwości.`m_pWndPropList`

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*pWndList*|podczas Wskaźnik do obiektu kontrolki siatki właściwości.|

##  <a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Ustawia pionowy margines, czyli spację między górną lub dolną komórką koloru a granicą obszaru klienta.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parametry

*nVertMargin*<br/>
podczas Pionowy margines (w pikselach).

### <a name="remarks"></a>Uwagi

Domyślnie Konstruktor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) ustawia pionowy margines na 4 piksele.

##  <a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Żąda okna ramki, które jest właścicielem kontrolki pasek koloru, aby zaktualizować wiersz komunikatu na pasku stanu.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parametry

*uiCmdId*<br/>
podczas Identyfikator polecenia. (Ten parametr jest ignorowany).

### <a name="remarks"></a>Uwagi

Ta metoda wysyła komunikat WM_SETMESSAGESTRING do właściciela kontrolki pasek koloru.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
