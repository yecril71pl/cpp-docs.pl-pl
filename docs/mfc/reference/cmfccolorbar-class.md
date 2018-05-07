---
title: Klasa CMFCColorBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2083c26943768afff4b3b20a2ba95c709648dd50
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfccolorbar-class"></a>Klasa CMFCColorBar
`CMFCColorBar` Klasa reprezentuje dokujący pasek sterowania, który można wybrać kolory dokumentu lub aplikacji.  
  
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
|[CMFCColorBar::ContextToSize](#contexttosize)|Oblicza marginesy poziome i pionowe, które muszą zawierać przycisków w formancie paska koloru i ustala lokalizację tych przycisków.|  
|[CMFCColorBar::CreateControl](#createcontrol)|Tworzy okno kontrolki paska koloru, dołącza go do `CMFCColorBar` obiektu i zmienia rozmiar kontrolki zawierają określony paletę kolorów.|  
|[CMFCColorBar::Create](#create)|Tworzy okno kontrolki paska koloru i dołącza go do `CMFCColorBar` obiektu.|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Pokazuje lub ukrywa przycisk Automatyczny.|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Włącza lub wyłącza wyświetlanie okna dialogowego, w którym użytkownik może zaznaczyć więcej kolorów.|  
|[CMFCColorBar::GetColor](#getcolor)|Pobiera obecnie wybranego koloru.|  
|[CMFCColorBar::GetCommandID](#getcommandid)|Pobiera identyfikator polecenia bieżącego formantu paska koloru.|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Pobiera kolor, który oznacza, że przycisk koloru ma fokus; Ten przycisk jest *gorących*.|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Pobiera poziomy margines to obszar między po lewej lub prawidłowy kolor komórki a obramowaniem obszaru klienta.|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Pobiera pionowy margines, czyli miejsce między górą lub komórki kolor dolnej i granic obszaru klienta.|  
|[CMFCColorBar::IsTearOff](#istearoff)|Wskazuje, czy bieżący pasek koloru jest zadokowane.|  
|[CMFCColorBar::SetColor](#setcolor)|Ustawia kolor, który jest aktualnie wybrany.|  
|[CMFCColorBar::SetColorName](#setcolorname)|Ustawia nazwę określonego koloru.|  
|[CMFCColorBar::SetCommandID](#setcommandid)|Ustawia nowy identyfikator polecenia dla formantu paska koloru.|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Ustawia listę kolorów, które są używane w bieżącym dokumencie.|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Ustawia poziomy margines to obszar między po lewej lub prawidłowy kolor komórki a obramowaniem obszaru klienta.|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Ustawia margines pionowy, czyli miejsce między komórki kolor górny lub dolny a obramowaniem obszaru klienta.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ustawia położenie kolor przycisków w formancie paska koloru.|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Wskazuje, czy tekst etykiety kolor przycisków może się zmieniać.|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Wskazuje, czy obiekt formantu paska koloru może występować na liście narzędzi w trakcie dostosowywania.|  
|[CMFCColorBar::CalcSize](#calcsize)|Wywoływane przez platformę w ramach procesu obliczania układu.|  
|[CMFCColorBar::CreatePalette](#createpalette)|Initalizes palety kolorów w określonej tablicy kolorów.|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Oblicza liczbę wierszy i kolumn w siatce formantu paska koloru.|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Oblicza dodatkowe wysokość, który bieżącego pasek koloru wymaga, aby wyświetlić elementy interfejsu użytkownika inne takie jak **innych** przycisku, kolory dokumentu i tak dalej.|  
|[CMFCColorBar::InitColors](#initcolors)|Inicjuje tablicę i w określonym palety lub palety domyślny system kolorów.|  
|[CMFCColorBar::OnKey](#onkey)|Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Wywoływane przez platformę, by zamknąć hierarchii kontrolki popup.|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Wywoływane przez platformę, by włączyć lub wyłączyć elementu interfejsu użytkownika formantu paska koloru, przed wyświetleniem elementu.|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Otwiera okno dialogowe kolorów.|  
|[CMFCColorBar::Rebuild](#rebuild)|Całkowicie ponownie rysuje formantu paska kolorów.|  
|[CMFCColorBar::SelectPalette](#selectpalette)|Ustawia logiczną paletę kontekstu określonego urządzenia na palecie przycisku nadrzędnego bieżącego formantu paska koloru.|  
|[CMFCColorBar::SetPropList](#setproplist)|Ustawia `m_pWndPropList` chroniony element członkowski danych na określonym wskaźnik do formantu siatki właściwości.|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Żąda okno ramowe, który jest właścicielem formantu paska koloru można zaktualizować wiersza wiadomości w pasku stanu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`m_bInternal`|Pole logiczna określająca, czy zdarzenia myszy są przetwarzane. Zazwyczaj są przetwarzane zdarzenia myszy, gdy to pole jest `TRUE` i jest Tryb dostosowywania `FALSE`.|  
|`m_bIsEnabled`|Wartość logiczna, która wskazuje, czy formant jest włączony.|  
|`m_bIsTearOff`|Wartość logiczna, która wskazuje, czy formant pasek koloru obsługuje dokowania.|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) obiekt, który określa rozmiar komórki siatki pasek koloru.|  
|`m_bShowDocColorsWhenDocked`|Wartość logiczna wskazująca, czy wyświetlać kolory dokumentu, gdy jest zadokowany pasek koloru. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_bStdColorDlg`|Wartość logiczna wskazująca, czy wyświetlać okno dialogowe kolorów standardowych systemowych lub [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) który przechowuje bieżący kolor automatycznego. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorNames`|[CMap](../../mfc/reference/cmap-class.md) obiekt, który kojarzy zestaw RGB kolory z ich nazw.|  
|`m_colors`|A [carray —](../../mfc/reference/carray-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, które zawiera kolorów, które są wyświetlane w formancie paska koloru.|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość oznacza to kolor, który użytkownik wybrał się aktualnie w formancie paska koloru.|  
|`m_lstDocColors`|A [clist —](../../mfc/reference/clist-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości, które zawiera kolorów, które są obecnie używane w dokumencie.|  
|`m_nCommandID`|Całkowitą bez znaku, który jest Identyfikatorem polecenia przycisk koloru.|  
|`m_nHorzMargin`|Liczba całkowita, która jest poziomy margines między przyciskami kolorów w siatce kolorów.|  
|`m_nHorzOffset`|Liczba całkowita, która jest przesunięcie w poziomie do środka przycisk koloru. Ta wartość jest ważna, jeśli przycisku wyświetlany tekst lub obraz oprócz koloru.|  
|`m_nNumColumns`|Liczba całkowita, która jest liczba kolumn w siatce formantu paska koloru kolorów.|  
|`m_nNumColumnsVert`|Liczba całkowita, która jest liczba kolumn w orientacji pionowej siatki kolorów.|  
|`m_nNumRowsHorz`|Liczba całkowita, która jest liczba kolumn w orientacji poziomej siatki kolorów.|  
|`m_nRowHeight`|Liczba całkowita, która jest wysokość wiersza kolor przycisków w siatce kolorów.|  
|`m_nVertMargin`|Liczba całkowita, która jest pionowego marginesu między przyciskami kolorów w siatce kolorów.|  
|`m_nVertOffset`|Liczba całkowita, która jest przesunięcie w pionie do środka przycisk koloru. Ta wartość jest ważna, jeśli przycisku wyświetlany tekst lub obraz oprócz koloru.|  
|`m_Palette`|A [cpalette —](../../mfc/reference/cpalette-class.md) kolorów, które są używane w formancie paska koloru.|  
|`m_pParentBtn`|Wskaźnik do [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) obiekt, który jest elementem nadrzędnym bieżącego przycisku. Ta wartość jest istotne, przycisk koloru znajduje się w hierarchii formanty paska narzędzi lub jest w kontrolce siatki właściwości kolorów.|  
|`m_pParentRibbonBtn`|Wskaźnik do [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) obiekt, który znajduje się na Wstążce i jest przycisk nadrzędnego bieżącego przycisku. Ta wartość jest istotne, przycisk koloru znajduje się w hierarchii formanty paska narzędzi lub jest w kontrolce siatki właściwości kolorów.|  
|`m_pWndPropList`|Wskaźnik do [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) obiektu.|  
|`m_strAutoColor`|A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na **automatyczne** przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|  
|`m_strDocColors`|A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na przycisku kolory dokumentu. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_strOtherColor`|A [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) oznacza to tekst, który jest wyświetlany na *innych* przycisku. Aby uzyskać więcej informacji, zobacz [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj nie utworzysz `CMFCColorBar` obiekt bezpośrednio. Zamiast tego [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (używana w menu i pasków narzędzi) lub [klasy CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) tworzy `CMFCColorBar` obiektu.  
  
 `CMFCColorBar` Klasa udostępnia następujące funkcje:  
  
-   Automatycznie dostosowuje listę kolorów dokumentu.  
  
-   Zapisuje i przywrócenie stanu oraz stan dokumentu.  
  
-   Zarządza przycisk "Automatyczny".  
  
-   Używa [klasy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) formantu, aby wybrać kolor niestandardowy.  
  
-   Obsługuje stanu "oderwania" (jeśli jest tworzona przy użyciu [CMFCColorMenuButton klasy](../../mfc/reference/cmfccolormenubutton-class.md)).  
  
 Aby włączyć `CMFCColorBar` funkcje do aplikacji:  
  
1.  Przycisk menu regularne tworzenie i przypisać mu identyfikator, na przykład ID_CHAR_COLOR.  
  
2.  W Twojej klasie okien ramowych zastąpienie [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) — metoda i zamiany regularne menu przycisk z [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) obiektu (wywołując [CMFCToolBar: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).  
  
3.  Ustaw wszystkie style i Włącz lub wyłącz funkcje `CMFCColorBar` obiektu podczas [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) tworzenia. `CMFCColorMenuButton` Dynamicznie tworzy obiekt `CMFCColorBar` obiektu po wywołania framework `CreatePopupMenu` metody.  
  
 Gdy użytkownik kliknie przycisk formantu paska koloru, używa platformę `ON_COMMAND` makra, by powiadomić element nadrzędny kontrolki paska koloru. Makra parametr identyfikator polecenia jest wartość przypisana do przycisku paska koloru w kroku 1 (ID_CHAR_COLOR w tym przykładzie). Aby uzyskać więcej informacji, zobacz [klasy CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton klasy](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl klasy](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx—Klasa](../../mfc/reference/cframewndex-class.md), i [klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania pasek koloru przy użyciu różnych metod w `CMFCColorBar` klasy. Metody Ustaw marginesy poziomie i w pionie, Włącz przycisk inne utworzyć okno kontrolki paska koloru i ustawia aktualnie wybranego koloru. Ten przykład jest częścią [próbki nowe formanty](../../visual-cpp-samples.md).  
  
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
 Ustawia położenie kolor przycisków w formancie paska koloru.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez framework podczas `WM_SIZE` przetwarzania komunikatów.  
  
##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels  
 Wskazuje, czy tekst etykiety kolor przycisków może się zmieniać.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość `FALSE`, co oznacza, że tekst etykiety nie może być modyfikowany. Zastępuje tę metodę, aby umożliwić modyfikowanie etykiet tekstowych.  
  
##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList  
 Wskazuje, czy obiekt formantu paska koloru może występować na liście narzędzi w trakcie dostosowywania.  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość `TRUE`, co oznacza, że platformę można wyświetlić formantu paska kolorów w trakcie dostosowywania. Zastępuje tę metodę do zaimplementowania inaczej.  
  
##  <a name="calcsize"></a>  CMFCColorBar::CalcSize  
 Wywoływane przez platformę w ramach procesu obliczania układu.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bVertDock`  
 `TRUE` Aby określić, że formant pasek koloru jest zadokowany pionowo; `FALSE` do określenia, że formantu paska kolorów jest zadokowany poziomo.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar tablicy kolor przycisków w formancie paska koloru.  
  
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
 [in] `colors`  
 Tablica kolorów, które Wyświetla platformę w formancie paska koloru.  
  
 [in] `color`  
 Początkowo wybranego koloru.  
  
 [in] `lpszAutoColor`  
 Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne), lub `NULL`.  
  
 Standardowa etykieta przycisku automatycznego **automatyczne**.  
  
 [in] `lpszOtherColor`  
 Etykieta tekstowa elementu *innych* przycisku, który wyświetla więcej kolorów, lub `NULL`.  
  
 Standardowe Etykieta przycisku innych **więcej kolorów...** .  
  
 [in] `lpszDocColors`  
 Etykieta tekstowa przycisk kolory dokumentu. Palety kolorów dokumentu zawiera listę wszystkich kolorów, które obecnie używane.  
  
 [in] `lstDocColors`  
 Lista kolorów, które są obecnie używane.  
  
 [in] `nColumns`  
 Liczba kolumn, które ma tablicę kolorów.  
  
 [in] `nRowsDockHorz`  
 Liczba wierszy, które pasek koloru ma, gdy jest zadokowany poziomo.  
  
 [in] `nColDockVert`  
 Liczba kolumn, które pasek koloru ma, gdy jest zadokowany w pionie.  
  
 [in] `colorAutomatic`  
 Domyślny kolor platformę stosuje się po kliknięciu przycisku automatycznego.  
  
 [in] `nCommandID`  
 Identyfikator polecenia sterowania pasek koloru.  
  
 [in] `pParentBtn`  
 Wskaźnik do nadrzędnego przycisku.  
  
 [in] `src`  
 Istniejące `CMFCColorBar` obiekt ma zostać skopiowany do nowego `CMFCColorBar` obiektu.  
  
 [in] `uiCommandID`  
 Identyfikator polecenia.  
  
##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize  
 Oblicza poziome i pionowe marginesy muszą zawierać przycisków w formancie paska kolorów, które można dostosować położenie tych przycisków.  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `bSquareButtons`|`TRUE` kształt przycisków w formancie paska koloru są kwadratowe; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.|  
|[in] `bCenterButtons`|`TRUE` Aby określić, że jest wyśrodkowywana zawartości rachunku przycisku paska koloru; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.|  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="create"></a>  CMFCColorBar::Create  
 Tworzy okno kontrolki paska koloru i dołącza go do `CMFCColorBar` obiektu.  
  
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
 [in] `pParentWnd`  
 Wskaźnik do okna nadrzędnego.  
  
 [in] `dwStyle`  
 Bitowe połączenie (lub) [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `nID`  
 Identyfikator polecenia.  
  
 [in] `pPalette`  
 Wskaźnik do palety kolorów. Wartość domyślna to `NULL`.  
  
 [in] `nColumns`  
 Liczba kolumn w formancie paska koloru. Wartość domyślna to 0.  
  
 [in] `nRowsDockHorz`  
 Liczba wierszy w formancie paska koloru, gdy jest zadokowany poziomo. Wartość domyślna to 0.  
  
 [in] `nColDockVert`  
 Liczba kolumn w formancie paska koloru, gdy jest zadokowany w pionie. Wartość domyślna to 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Aby utworzyć `CMFCColorBar` obiekt, należy wywołać konstruktora klasy, a następnie tej metody. `Create` Metoda tworzy kontrolkę systemu Windows i inicjuje listę kolorów.  
  
##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl  
 Tworzy okno kontrolki paska koloru, dołącza go do `CMFCColorBar` obiektu i zmienia rozmiar okna formantu zawiera określony paletę kolorów.  
  
```  
virtual BOOL CreateControl(
    CWnd* pParentWnd,  
    const CRect& rect,  
    UINT nID,  
    int nColumns=-1,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pParentWnd`  
 Wskaźnik do okna nadrzędnego. Nie może być `NULL`.  
  
 [in] `rect`  
 Prostokąt ograniczający Określa, gdzie można narysować kontrolkę paska koloru.  
  
 [in] `nID`  
 Identyfikator formantu.  
  
 [in] `nColumns`  
 Nadaje się doskonale liczba kolumn w formancie paska koloru. Ta metoda modyfikuje ten numer do dopasowania określonej paletę kolorów. Wartość domyślna to -1, co oznacza, że ten parametr nie zostanie określony.  
  
 [in] `pPalette`  
 Wskaźnik do palety kolorów, lub `NULL`. Jeśli ten parametr jest `NULL`, ta metoda oblicza rozmiar formantu paska koloru tak, jakby określono 20 kolorów. Wartość domyślna to `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda używa `rect`, `nColumns`, i `pPalette` parametrów można obliczyć odpowiedniego lub wierszy i kolumn w formantu paska kolorów, a następnie wywołania [CMFCColorBar::Create](#create) metody.  
  
##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette  
 Inicjuje palety kolorów w określonej tablicy kolorów.  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `arColors`|Tablica kolorów.|  
|[in] `palette`|Palety kolorów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton  
 Pokazuje lub ukrywa przycisk Automatyczny.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Etykieta tekstowa elementu *automatyczne* przycisk koloru (ustawienie domyślne), lub `NULL`.  
  
 Standardowa etykieta przycisku automatycznego **automatyczne**.  
  
 [in] `colorAutomatic`  
 Domyślny kolor platformę stosuje się po kliknięciu przycisku automatycznego.  
  
 [in] `bEnable`  
 `TRUE` Aby włączyć automatyczne przycisk; `FALSE` wyłączyć przycisk Automatyczny. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Etykieta tekstowa elementu przycisk Automatyczny zostanie usunięty w przypadku `lpszLabel` parametr jest `NULL` lub `bEnable` parametr jest `FALSE`.  
  
##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton  
 Włącza lub wyłącza wyświetlanie okna dialogowego, w którym użytkownik może zaznaczyć więcej kolorów.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Etykieta tekstowa elementu *innych* przycisku, który wyświetla więcej kolorów, lub `NULL`.  
  
 Standardowa etykieta ten przycisk jest **więcej kolorów...** .  
  
 [in] `bAltColorDlg`  
 `TRUE` Aby wyświetlić [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe; `FALSE` do wyświetlenia standardowego [CColorDialog](../../mfc/reference/ccolordialog-class.md) okno dialogowe. Wartość domyślna to `TRUE`.  
  
 [in] `bEnable`  
 `TRUE` Aby włączyć przycisk; `FALSE` wyłączenie przycisku. Wartość domyślna to `TRUE`.  
  
##  <a name="getcolor"></a>  CMFCColorBar::GetColor  
 Pobiera obecnie wybranego koloru.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obecnie wybranego koloru.  
  
##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize  
 Oblicza liczbę wierszy i kolumn w siatce formantu paska koloru.  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `bVertDock`|`TRUE` do przeprowadzenia obliczeń kontrolkę pionowo zadokowany pasek koloru; w przeciwnym razie wykonuje obliczenia poziomo zadokowanych formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) którego `cx` składnika zawiera liczbę kolumn i których `cy` składnik zawiera liczbę wierszy.  
  
##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID  
 Pobiera identyfikator polecenia bieżącego formantu paska koloru.  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Gdy użytkownik wybierze nowy kolor, platformę wysyła identyfikator polecenia w `WM_COMMAND` wiadomości do powiadamiania elementu nadrzędnego `CMFCColorBar` obiektu.  
  
##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight  
 Oblicza dodatkowe wysokość, który bieżącego pasek koloru wymaga, aby wyświetlić elementy interfejsu użytkownika inne, takie jak **innych** kolory przycisku lub dokumentu.  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `nNumColumns`|Jeśli formant pasek koloru zawiera kolory dokumentu, numer kolumny do wyświetlenia w siatce kolory dokumentu. W przeciwnym razie ta wartość nie jest używana.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Obliczony wysokość dodatkowe wymagane.  
  
##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor  
 Pobiera kolor, który oznacza, że przycisk koloru ma fokus; Ten przycisk jest *gorących*.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin  
 Pobiera poziomy margines to obszar między po lewej lub prawidłowy kolor komórki a obramowaniem obszaru klienta.  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Poziomy margines.  
  
##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin  
 Pobiera pionowy margines, czyli miejsce między górą lub komórki kolor dolnej i granic obszaru klienta.  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pionowego marginesu.  
  
##  <a name="initcolors"></a>  CMFCColorBar::InitColors  
 Inicjuje tablicę kolorów kolorów w palecie określony lub paleta domyślne systemu.  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `pPalette`|Wskaźnik do obiektu palety lub `NULL`. Jeśli ten parametr jest `NULL`, ta metoda korzysta z domyślnej palety systemu operacyjnego.|  
|[in] `arColors`|Tablica kolorów.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w tablicy kolorów.  
  
##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff  
 Wskazuje, czy bieżący pasek koloru jest zadokowane.  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli bieżący formant pasek koloru jest zadokowane; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli formant pasek koloru jest zadokowane, można zerwana pasek sterowania i zadokowane w innej lokalizacji.  
  
##  <a name="onkey"></a>  CMFCColorBar::OnKey  
 Wywoływane przez platformę, gdy użytkownik naciśnie przycisk klawiatury.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nChar`  
 Kod klawisza wirtualnego klucz, który użytkownik nacisnął klawisz.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda przetwarza określony klucz; w przeciwnym razie `FALSE`.  
  
##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand  
 Wywoływane przez platformę, by zamknąć hierarchii wyskakujących kontrolek.  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `pButton`|Wskaźnik do formantu, który znajduje się na pasku narzędzi.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI  
 Wywoływane przez platformę, by włączyć lub wyłączyć elementu interfejsu użytkownika formantu paska koloru, przed wyświetleniem elementu.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pTarget`  
 Wskaźnik do typu window, który zawiera element interfejsu użytkownika do zaktualizowania.  
  
 [in] `bDisableIfNoHndler`  
 `TRUE` Aby wyłączyć elementu interfejsu użytkownika, jeśli bez obsługi jest zdefiniowany w mapy komunikatów; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Kliknięcie aplikacji elementu interfejsu użytkownika, element musi wiedzieć, czy ma być wyświetlany jako włączona lub wyłączona. Element docelowy komunikat polecenia udostępnia te informacje zaimplementowanie `ON_UPDATE_COMMAND_UI` programu obsługi poleceń. Użyj tej metody, aby przetworzyć polecenia. Aby uzyskać więcej informacji, zobacz [ccmdui — klasa](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog  
 Otwiera okno dialogowe kolorów.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `colorDefault`  
 Kolor, który jest domyślnie zaznaczona, gdy zostanie otwarte okno dialogowe kolorów.  
  
 [out] `colorRes`  
 Kolor wybranego użytkownika.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli użytkownik wybrał koloru; `FALSE` Jeśli użytkownik anulował okno dialogowe kolorów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="rebuild"></a>  CMFCColorBar::Rebuild  
 Całkowicie ponownie rysuje formantu paska kolorów.  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette  
 Ustawia logiczną paletę kontekstu określonego urządzenia na palecie przycisku nadrzędnego bieżącego formantu paska koloru.  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `pDC`|Wskaźnik do kontekstu urządzenia przycisku nadrzędnego bieżącego formantu paska koloru.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zastępowany przez palety przycisku nadrzędnego bieżącego formantu paska kolorów palety.  
  
##  <a name="setcolor"></a>  CMFCColorBar::SetColor  
 Ustawia kolor, który jest aktualnie wybrany.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `color`  
 Wartości kolorów RGB.  
  
##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName  
 Ustawia nazwę określonego koloru.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `color`  
 Wartości RGB koloru.  
  
 [in] `strName`  
 Nowa nazwa dla określonego koloru.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zmienia nazwę określonego koloru we wszystkich `CMFCColorBar` obiektów w aplikacji.  
  
##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID  
 Ustawia nowy identyfikator polecenia dla formantu paska koloru.  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nCommandID`  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody do zmiany identyfikator polecenia formantu paska koloru i powiadamia okno nadrzędne formantu, który został zmieniony identyfikator.  
  
##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors  
 Ustawia listę kolorów, które są używane w bieżącym dokumencie.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszCaption`  
 Podpis wyświetlany, gdy nie jest zadokowany formantu paska kolorów.  
  
 [in] `lstDocColors`  
 Lista kolorów zastępuje kolorów bieżącego dokumentu.  
  
 [in] `bShowWhenDocked`  
 `TRUE` Aby wyświetlić kolory dokumentu, gdy jest zadokowany formantu paska koloru; w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 *Dokument kolory* są kolorów, które są obecnie używane w dokumencie. Platformę również automatycznie obsługuje listę kolorów dokumentu, ale ta metoda służy do modyfikowania listy.  
  
##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin  
 Ustawia poziomy margines, czyli miejsce między po lewej lub prawidłowy kolor komórki a obramowaniem obszaru klienckiego.  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nHorzMargin`  
 Poziomy margines w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) Konstruktor Ustawia poziomy margines 4 pikseli.  
  
##  <a name="setproplist"></a>  CMFCColorBar::SetPropList  
 Ustawia `m_pWndPropList` chroniony element członkowski danych na określonym wskaźnik do formantu siatki właściwości.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `pWndList`|Wskaźnik do obiektu formantu siatki właściwości.|  
  
##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin  
 Ustawia margines pionowy, czyli miejsce między komórki kolor górny lub dolny a obramowaniem obszaru klienta.  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nVertMargin`  
 Pionowego marginesu w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie [CMFCColorBar::CMFCColorBar](#cmfccolorbar) Konstruktor ustawia pionowego marginesu 4 pikseli.  
  
##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString  
 Żąda okno ramowe, który jest właścicielem formantu paska koloru można zaktualizować wiersza wiadomości w pasku stanu.  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmdId`  
 Identyfikator polecenia. (Ten parametr jest ignorowany.)  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła `WM_SETMESSAGESTRING` komunikat do właściciela formantu paska kolorów.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)
