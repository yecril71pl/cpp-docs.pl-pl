---
title: Klasa CMFCColorMenuButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c19386aeac0d85565ae7834a881d710d9226ef9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370708"
---
# <a name="cmfccolormenubutton-class"></a>Klasa CMFCColorMenuButton
`CMFCColorMenuButton` Klasa obsługuje polecenia menu lub przycisku paska narzędzi, która rozpoczyna się okno dialogowe selektora kolorów.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Konstruuje `CMFCColorMenuButton` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowy system ma oznaczenie **automatyczne**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umożliwia wyświetlanie kolorów specyficznych dla dokumentu, zamiast kolorów systemu.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza "other" przycisku, który znajduje się poniżej przycisków regularne kolorów. (Standardowy system etykietą "other" przycisk **więcej kolorów**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Włącza możliwość wydzielić okienku kolorów.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatycznego.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Pobiera bieżący przycisk koloru.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Pobiera kolor, który odpowiada na identyfikator określonego polecenia.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy zmienia okno nadrzędne.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otwiera okno dialogowe Wybieranie koloru.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Określa kolor przycisku bieżący kolor.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Określa kolor przycisku menu określonego koloru.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Ustawia nazwę określonego koloru.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn, które są wyświetlane przez `CMFCColorBar` obiektu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Kopiuje inny przycisk paska narzędzi do bieżącego przycisku.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Tworzy okno dialogowe selektora kolorów.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Wskazuje, czy menu puste są obsługiwane.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Wywoływane przez platformę, aby obraz był wyświetlany na przycisku.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Metoda wywoływana przez platformę przed `CMFCColorMenuButton` obiekt jest wyświetlany na liście okno dialogowe Dostosowywanie paska narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 Zastąpienie oryginalnej polecenia lub narzędzi przycisk menu z `CMFCColorMenuButton` obiektów, Utwórz `CMFCColorMenuButton` obiektu ustawiona właściwie [klasy CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) style, a następnie wywołania `ReplaceButton` metody [Klasy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) klasy. Jeśli dostosowywanie paska narzędzi, wywołaj [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) metody.  
  
 Okno dialogowe selektora kolorów jest tworzony podczas przetwarzania [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) obsługi zdarzeń. Program obsługi zdarzeń powiadamia ramka nadrzędny z `WM_COMMAND` wiadomości. `CMFCColorMenuButton` Obiekt wysyła identyfikator formantu, przypisane do oryginalnego polecenia lub narzędzi przycisku menu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak utworzyć i skonfigurować przycisk menu kolorów przy użyciu różnych metod w `CMFCColorMenuButton` klasy. W tym przykładzie `CPalette` obiekt jest najpierw utworzyć i następnie użyty do utworzenia obiektu `CMFCColorMenuButton` klasy. `CMFCColorMenuButton` Obiekt jest następnie konfigurowana przez włączenie jej automatyczne i innych przycisków i ustawianie koloru i liczbę kolumn. Ten kod jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcolormenubutton.h  
  
##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton  
 Konstruuje `CMFCColorMenuButton` obiektu.  
  
```  
CMFCColorMenuButton();

 
CMFCColorMenuButton(
    UINT uiCmdID,  
    LPCTSTR lpszText,  
    CPalette* pPalette=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmdID`  
 Identyfikator przycisku polecenia.  
  
 [in] `lpszText`  
 Tekst przycisku.  
  
 [in] `pPalette`  
 Wskaźnik do przycisku paletę kolorów.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor jest konstruktora domyślnego. Kolor bieżącego obiektu i kolorowi automatycznemu są inicjowane na kolor czarny (RGB (0, 0, 0)).  
  
 Drugi Konstruktor inicjuje przycisk kolor, który odpowiada identyfikatorowi określonego polecenia.  
  
##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom  
 Kopiuje jeden [klasy CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)-pochodnych do innego obiektu.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `src`  
 Źródło, aby skopiować.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę do kopiowania obiektów, które są pochodnymi `CMFCColorMenuButton` obiektu.  
  
##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu  
 Tworzy okno dialogowe selektora kolorów.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt reprezentujący okno dialogowe selektora kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik naciśnie przycisk menu koloru.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton  
 Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowy system ma oznaczenie **automatyczne**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Określa tekst przycisku, który jest wyświetlane, gdy przycisk jest automatyczne.  
  
 [in] `colorAutomatic`  
 Określa nowy kolor automatycznego.  
  
 [in] `bEnable`  
 Określa, czy przycisk jest automatycznie.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk Automatyczny stosuje bieżący kolor domyślny.  
  
##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors  
 Umożliwia wyświetlanie kolorów specyficznych dla dokumentu, zamiast kolorów systemu.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Określa tekst przycisku.  
  
 [in] `bEnable`  
 `TRUE` Aby wyświetlić kolory specyficznych dla dokumentu lub `FALSE` do wyświetlania kolorów systemu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wyświetlanie kolorów bieżącego dokumentu lub palety kolorów systemu, gdy użytkownik kliknie przycisk menu koloru.  
  
##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton  
 Włącza i wyłącza "other" przycisku, który znajduje się poniżej przycisków regularne kolorów. (Standardowy system etykietą "other" przycisk **więcej kolorów**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lpszLabel`  
 Określa tekst przycisku.  
  
 [in] `bAltColorDlg`  
 Określ `TRUE` do wyświetlenia `CMFCColorDialog` okno dialogowe, lub `FALSE` Aby wyświetlić okno dialogowe kolorów w standardowym systemie.  
  
 [in] `bEnable`  
 Określ `TRUE` do wyświetlania przycisku "other"; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff  
 Włącza możliwość wydzielić okienku kolorów.  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiID`  
 Określa identyfikator dla tego okienka oderwania.  
  
 [in] `nVertDockColumns`  
 Określa liczbę kolumn w okienku kolor pionowo zadokowanych w stanie oderwania.  
  
 [in] `nHorzDockRows`  
 Określa liczbę wierszy w stanie oderwania okienka poziomo zadokowanych kolor.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby włączyć funkcję "oderwania" dla tego okienka kolorów, które pojawia się w przypadku `CMFCColorMenuButton` przycisk jest naciśnięty.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor  
 Pobiera bieżący kolor automatycznego.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości kolorów RGB reprezentujący bieżący kolor automatycznego.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można uzyskać automatyczne kolor, który jest ustawiony przez [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor  
 Pobiera bieżący przycisk koloru.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID  
 Pobiera kolor, który odpowiada na identyfikator określonego polecenia.  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmdID`  
 Identyfikator polecenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor, który odpowiada identyfikatorowi określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, jeśli masz kilka kolor przycisków w aplikacji. Gdy użytkownik kliknie przycisk koloru, przycisk wysyła jego identyfikator polecenia w `WM_COMMAND` komunikat do elementu nadrzędnego. `GetColorByCmdID` — Metoda używa Identyfikatora polecenia, aby pobrać odpowiedni kolor.  
  
##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed  
 Wskazuje, czy menu puste są obsługiwane.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Menu różną od zera, jeśli puste są dozwolone; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Pusty menu są obsługiwane domyślnie. Zastępuje tę metodę, aby zmienić to zachowanie w klasie pochodnej.  
  
##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy zmienia okno nadrzędne.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pWndParent`  
 Wskaźnik do nowego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw  
 Wywoływane przez platformę, aby obraz był wyświetlany na przycisku.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz=TRUE,  
    BOOL bCustomizeMode=FALSE,  
    BOOL bHighlight=FALSE,  
    BOOL bDrawBorder=TRUE,  
    BOOL bGrayDisabledButtons=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rect`  
 Prostokąt zakresem obszaru do narysowania.  
  
 [in] `pImages`  
 Wskazuje listę narzędzi obrazów.  
  
 [in] `bHorz`  
 `TRUE` Aby określić, czy pasek narzędzi jest w stanie zadokowanych poziome; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
 [in] `bCustomizeMode`  
 `TRUE` Aby określić, że aplikacja jest w trybie dostosowania; w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
 [in] `bHighlight`  
 `TRUE` Aby określić, czy przycisk jest podświetlona; w przeciwnym razie `FALSE`. Wartość domyślna to `FALSE`.  
  
 [in] `bDrawBorder`  
 `TRUE` Aby określić, czy są wyświetlane obramowanie przycisku; w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
 [in] `bGrayDisabledButtons`  
 `TRUE` Aby określić, które wyłączone przyciski są wyszarzony (wygaszone) w przeciwnym razie `FALSE`. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList  
 Metoda wywoływana przez platformę przed `CMFCColorMenuButton` obiekt jest wyświetlany na liście okno dialogowe Dostosowywanie paska narzędzi.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in] `rect`  
 Prostokąt zakresem przycisku do narysowania.  
  
 [in] `bSelected`  
 `TRUE` Określa, czy przycisk jest w stanie zaznaczenia; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy `CMFCColorMenuButton` obiekt jest wyświetlany w polu listy w trakcie dostosowywania paska narzędzi.  
  
##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog  
 Otwiera okno dialogowe Wybieranie koloru.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `colorDefault`  
 Domyślny kolor wybrany w oknie dialogowym koloru.  
  
 [out] `colorRes`  
 Zwraca kolor, który użytkownik wybiera z okna dialogowego kolorów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli użytkownik wybierze nowy kolor; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Po kliknięciu przycisku menu wywołać tę metodę, aby otworzyć okno dialogowe kolorów. Jeśli wartość zwracana jest niezerowa, kolor wybranego przez użytkownika są przechowywane w `colorRes` parametru. Użyj [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) metody do przełączania się między okno dialogowe kolorów standardowe i [klasy CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe.  
  
##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor  
 Określa kolor przycisku bieżący kolor.  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `clr`  
 Wartości kolorów RGB.  
  
 [in] `bNotify`  
 `TRUE` Aby zastosować `clr` parametru kolor przycisku związanych z menu lub przycisku paska narzędzi; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zmienić kolor przycisku bieżący kolor. Jeśli `bNotify` parametr jest różna od zera, kolor odpowiedni przycisk na wszystkie skojarzone podręcznego menu lub pasek narzędzi zostanie zmieniona na kolor określone przez `clr` parametru.  
  
##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID  
 Określa kolor przycisku menu określonego koloru.  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `uiCmdID`  
 Identyfikator zasobu kolor przycisku menu.  
  
 [in] `color`  
 Wartości kolorów RGB.  
  
##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName  
 Ustawia nazwę określonego koloru.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `color`  
 Wartości RGB koloru, którego nazwa zmiany.  
  
 [in] `strName`  
 Nowa nazwa koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber  
 Ustawia liczbę kolumn do wyświetlenia w kontrolkę wyboru koloru ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nColumns`  
 Liczba kolumn do wyświetlenia.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)
