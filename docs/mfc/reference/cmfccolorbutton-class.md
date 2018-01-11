---
title: Klasa CMFCColorButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
dev_langs: C++
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e49cec1c34af066d6f30cf70003252f28e2bb8dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolorbutton-class"></a>Klasa CMFCColorButton
`CMFCColorButton` i [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) klasy są używane razem aby wdrażanie kontroli próbnika kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Tworzy nową `CMFCColorButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowy system ma oznaczenie **automatyczne**.)|  
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza "other" przycisku, który znajduje się poniżej przycisków regularne kolorów. (Standardowy system etykietą "other" przycisk **więcej kolorów**.)|  
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatycznego.|  
|[CMFCColorButton::GetColor](#getcolor)|Pobiera kolor przycisku.|  
|[CMFCColorButton::SetColor](#setcolor)|Określa kolor przycisku.|  
|[CMFCColorButton::SetColorName](#setcolorname)|Ustawia nazwę koloru.|  
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn w oknie dialogowym próbnika kolorów.|  
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Określa listę kolorów specyficznych dla dokumentu, które są wyświetlane w oknie dialogowym próbnika kolorów.|  
|[CMFCColorButton::SetPalette](#setpalette)|Określa paletę kolorów standardowego.|  
|[CMFCColorButton::SizeToContent](#sizetocontent)|Zmienia rozmiar kontrolki przycisku, w zależności od rozmiaru tekstu i obrazów.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Wskazuje, czy przycisk bieżący kolor jest wyświetlany w stylu wizualnego systemu Windows XP.|  
|[CMFCColorButton::OnDraw](#ondraw)|Wywoływane przez platformę, by wyświetlić obrazu przycisku.|  
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Wywoływane przez platformę, by wyświetlić obramowania przycisku.|  
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Wywoływane przez platformę, by wyświetlić prostokąt fokusu, gdy przycisk ma fokus.|  
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Wywoływane przez platformę, gdy okno dialogowe selektora kolorów ma być wyświetlany.|  
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicjuje `m_pPalette` chroniony element członkowski danych do określonego palety lub domyślnej palety systemu.|  
|[CMFCColorButton::UpdateColor](#updatecolor)|Wywoływane przez platformę, gdy użytkownik zaznaczy kolor z okna dialogowego selektora kolorów palety.|  
  
### <a name="data-members"></a>Elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`m_bAltColorDlg`|Wartość logiczna. Jeśli `TRUE`, wyświetla w ramach [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okna dialogowego kolorów, kiedy *innych* przycisk zostanie kliknięty, lub jeśli `FALSE`, okno dialogowe kolorów systemu. Wartość domyślna to `TRUE`. Aby uzyskać więcej informacji, zobacz [CMFCColorButton::EnableOtherButton](#enableotherbutton).|  
|`m_bAutoSetFocus`|Wartość logiczna. Jeśli `TRUE`, platformę Ustawia fokus menu Kolor, gdy zostanie wyświetlone menu lub `FALSE`, nie powoduje zmiany fokusu. Wartość domyślna to `TRUE`.|  
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Wskazuje, czy włączono tryb dostosowywania przycisk koloru.|  
|`m_Color`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości. Zawiera obecnie wybranego koloru.|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości. Zawiera aktualnie zaznaczonego domyślny kolor.|  
|`m_Colors`|A [carray —](../../mfc/reference/carray-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości. Zawiera obecnie dostępne kolory.|  
|`m_lstDocColors`|A [clist —](../../mfc/reference/clist-class.md) z [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartości. Zawiera kolorów bieżącego dokumentu.|  
|`m_nColumns`|Liczba całkowita. Zawiera liczbę kolumn do wyświetlenia w siatce kolorów w menu wyboru koloru.|  
|`m_pPalette`|Wskaźnik do [cpalette —](../../mfc/reference/cpalette-class.md). Zawiera kolorów, które są dostępne w menu wyboru bieżący kolor.|  
|`m_pPopup`|Wskaźnik do [klasy CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) obiektu. Menu wyboru kolor jest wyświetlany po kliknięciu przycisku kolorów.|  
|`m_strAutoColorText`|Ciąg. Etykieta przycisku "Automatyczny" w menu wyboru koloru.|  
|`m_strDocColorsText`|Ciąg. Etykieta przycisku w menu Wybór kolorów, która wyświetla kolory dokumentu.|  
|`m_strOtherText`|Ciąg. Etykieta przycisku "other" w menu wyboru koloru.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie `CMFCColorButton` klasy zachowuje się jak przycisk polecenia, które otwiera okno dialogowe selektora kolorów. Okno dialogowe selektora kolorów zawiera tablicę kolorów przycisków i "other" przycisku, który wyświetla próbnika kolorów niestandardowych. (Standardowy system etykietą "other" przycisk **więcej kolorów**.) Gdy użytkownik wybierze nowy kolor `CMFCColorButton` obiekt odzwierciedla zmianę i wyświetla wybranego koloru.  
  
 Tworzenie formantu przycisku kolor bezpośrednio w kodzie, lub za pomocą **ClassWizard** narzędzie i szablon okno dialogowe. W przypadku utworzenia kontrolkę przycisku kolor bezpośrednio dodać `CMFCColorButton` zmienną do aplikacji, a następnie wywołania konstruktora i `Create` metody `CMFCColorButton` obiektu. Jeśli używasz **ClassWizard**, Dodaj `CButton` zmienną do aplikacji, a następnie zmień typ zmiennej z `CButton` do `CMFCColorButton`.  
  
 Okno dialogowe selektora kolorów ( [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) jest wyświetlany za [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) metody, gdy struktura wywołuje `OnLButtonDown` obsługi zdarzeń. [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) — metoda może zostać zastąpiona w celu obsługi wybór koloru niestandardowego.  
  
 `CMFCColorButton` Obiektu powiadamia jego elementu nadrzędnego, który zmienia kolor przez wysłanie ich `WM_COMMAND | BN_CLICKED` powiadomień. Element nadrzędny używa [CMFCColorButton::GetColor](#getcolor) metoda pobierania bieżący kolor.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób konfigurowania przycisk koloru przy użyciu różnych metod w `CMFCColorButton` klasy. Metody kolor przycisk koloru oraz jego numer kolumny, a następnie Włącz automatyczne i innych przycisków. Ten przykład jest częścią [próbka Demo paska stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcolorbutton.h  
  
##  <a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton  
 Tworzy nową `CMFCColorButton` obiektu.  
  
```  
CMFCColorButton();
```  
  
##  <a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton  
 Włącz lub Wyłącz przycisk "Automatyczny" formantu selektora kolorów i kolor automatyczne (ustawienie domyślne).  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Określa tekst przycisku automatycznego.  
  
 [in]`colorAutomatic`  
 Wartości RGB, która określa kolor domyślny przycisk Automatyczny.  
  
 [in]`bEnable`  
 Określa, czy przycisk Automatyczny jest włączone.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton  
 Włączanie lub wyłączanie "other" przycisku, który pojawia się poniżej regularne kolor przycisków.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Określa tekst przycisku.  
  
 [in]`bAltColorDlg`  
 Określa, czy [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) dialogowego lub okna dialogowego kolorów systemu jest otwierany, gdy użytkownik kliknie przycisk.  
  
 [in]`bEnable`  
 Określa, czy przycisk "other" jest włączona.  
  
### <a name="remarks"></a>Uwagi  
 Kliknij przycisk "other", aby wyświetlić okno dialogowe kolorów. Jeśli *bAltColorDlg* parametr jest `TRUE`, [CMFCColorDialog klasy](../../mfc/reference/cmfccolordialog-class.md) jest wyświetlana; w przeciwnym razie zostanie wyświetlone okno dialogowe kolorów systemu.  
  
##  <a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor  
 Pobiera bieżący kolor automatyczne (ustawienie domyślne).  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości RGB reprezentujący bieżący kolor automatycznego.  
  
### <a name="remarks"></a>Uwagi  
 Bieżący kolor automatycznego jest ustawiana przez [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) metody.  
  
##  <a name="getcolor"></a>CMFCColorButton::GetColor  
 Pobiera obecnie wybranego koloru.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme  
 Wskazuje, czy przycisk bieżący kolor jest wyświetlany w stylu wizualnego systemu Windows XP.  
  
```  
BOOL IsDrawXPTheme() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeżeli style wizualne są obsługiwane i przycisku bieżący kolor jest wyświetlany w stylu wizualnego systemu Windows XP; w przeciwnym razie `FALSE`.  
  
##  <a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode  
 Ustawia tryb dostosowywania przycisk koloru.  
  
```  
BOOL m_bEnabledInCustomizeMode;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli trzeba dodać do strony w oknie dialogowym dostosowywania przycisk koloru (lub Zezwalaj użytkownikowi na inne opcje kolorów w trakcie dostosowywania realizowanego), Włącz przycisk przez ustawienie `m_bEnabledInCustomizeMode` członka `TRUE`. Domyślnie ten element członkowski ma ustawioną wartość `FALSE`.  
  
##  <a name="ondraw"></a>CMFCColorButton::OnDraw  
 Wywoływane przez platformę, by renderować obraz przycisku.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskazuje kontekst urządzenia, który jest używany do renderowania obrazu przycisku.  
  
 [in]`rect`  
 Prostokąt zakresem przycisku.  
  
 [in]`uiState`  
 Określa stan wizualny przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę w celu dostosowania procesu renderowania.  
  
##  <a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder  
 Wywoływane przez platformę, by wyświetlić obramowania przycisku.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskazuje kontekstu urządzenia używany do rysowania obramowania.  
  
 [in]`rectClient`  
 Prostokąt w kontekście urządzenia określonego przez `pDC` parametr, który definiuje granice przycisku do narysowania.  
  
 [in]`uiState`  
 Określa stan wizualny przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Należy przesłonić tę funkcję, aby dostosować wygląd obramowania przycisk koloru.  
  
##  <a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect  
 Wywoływane przez platformę, by wyświetlić prostokąt fokusu, gdy przycisk ma fokus.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskazuje kontekstu urządzenia używany do rysowania prostokąt fokusu.  
  
 [in]`rectClient`  
 Prostokąt w kontekście urządzenia określonego przez `pDC` parametr, który definiuje granice przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby dostosować wygląd prostokąt fokusu.  
  
##  <a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup  
 Metoda wywoływana przed wyświetleniem podręczny pasek koloru.  
  
```  
virtual void OnShowColorPopup();
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette  
 Inicjuje `m_pPalette` chroniony element członkowski danych do określonego palety lub domyślnej palety systemu.  
  
```  
void RebuildPalette(CPalette* pPal);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`pPal`|Wskaźnik do logiczną paletę lub `NULL`. Jeśli `NULL`, jest używany z domyślnej palety systemu.|  
  
##  <a name="setcolor"></a>CMFCColorButton::SetColor  
 Określa kolor przycisku.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolorname"></a>CMFCColorButton::SetColorName  
 Określa nazwę koloru.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Kolor RGB wartość.  
  
 [in]`strName`  
 Nazwa koloru.  
  
### <a name="remarks"></a>Uwagi  
 Lista nazw kolorów jest globalna na aplikację. W rezultacie tej metody przesyłania jej parametrów [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).  
  
##  <a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber  
 Określa liczbę kolumn, które są wyświetlane w tabeli kolorów, która jest wyświetlana podczas procesu wyboru koloru użytkownika.  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nColumns`  
 Określa liczbę kolumn.  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik może wybrać kolor z podręczny pasek koloru zawiera wstępnie zdefiniowane kolory. Ta metoda umożliwia zdefiniowanie liczby kolumn w tabeli.  
  
##  <a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors  
 Określa zestaw kolorów i nazwa zestawu. Wyświetlany jest zestaw kolorów, za pomocą [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszLabel`  
 Określa etykietę do wyświetlenia przy użyciu zestawu kolorów dokumentu.  
  
 [in]`lstColors`  
 Odwołanie do listy wartości RGB.  
  
### <a name="remarks"></a>Uwagi  
 A `CMFCColorButton` obiekt przechowuje listę wartości RGB, które są przenoszone do [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu. Po wyświetleniu paska koloru kolorów te są wyświetlane w sekcji specjalne, których etykiety jest określona przez `lpszLabel` parametru.  
  
##  <a name="setpalette"></a>CMFCColorButton::SetPalette  
 Określa standardowe kolory do wyświetlenia w podręcznym pasku koloru.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pPalette`  
 Wskaźnik do paletę kolorów.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="sizetocontent"></a>CMFCColorButton::SizeToContent  
 Zmienia rozmiar kontrolki przycisku do jego tekstu i obrazów.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bCalcOnly`  
 Jeśli jest różna od zera, nowy rozmiar kontrolki przycisku jest obliczane, ale rzeczywisty rozmiar nie ulega zmianie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CSize` obiekt, który określa nowy rozmiar kontrolki przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="updatecolor"></a>CMFCColorButton::UpdateColor  
 Wywoływane przez platformę, gdy użytkownik zaznaczy kolor na pasku kolorów wyświetlany, gdy użytkownik kliknie przycisk koloru.  
  
```  
virtual void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`color`  
 Kolor wybrany przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 `UpdateColor` Funkcji zmienia kolor aktualnie wybrany przycisk i powiadamia jego element nadrzędny, wysyłając `WM_COMMAND` komunikatów z `BN_CLICKED` powiadomień w wersji standard. Użyj [CMFCColorButton::GetColor](#getcolor) metoda pobierania wybranego koloru.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCButton](../../mfc/reference/cmfcbutton-class.md)   
 [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [Cpalette — klasa](../../mfc/reference/cpalette-class.md)   
 [Carray — klasa](../../mfc/reference/carray-class.md)   
 [Clist — klasa](../../mfc/reference/clist-class.md)   
 [Cstring —](../../atl-mfc-shared/reference/cstringt-class.md)
