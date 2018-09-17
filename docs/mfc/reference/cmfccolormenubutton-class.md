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
ms.openlocfilehash: ab793b8c758b95c259c717a794436b59057d4273
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712988"
---
# <a name="cmfccolormenubutton-class"></a>Klasa CMFCColorMenuButton
`CMFCColorMenuButton` Klasa obsługuje polecenie menu lub przycisku paska narzędzi, który uruchamia okno dialogowe próbnika kolorów.  
  
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
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowych systemowych jest oznaczona etykietą **automatyczne**.)|  
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Umożliwia wyświetlanie kolorów specyficzne dla dokumentu zamiast kolory systemowe.|  
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Włącza i wyłącza "other" przycisk, który znajduje się poniżej regularne kolor przycisków. (Standardowy system "other" przycisk ma etykietę **więcej kolorów**.)|  
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Włącza możliwość wydzielić okienko kolorów.|  
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Pobiera bieżący kolor automatyczne.|  
|[CMFCColorMenuButton::GetColor](#getcolor)|Pobiera kolor bieżącego przycisku.|  
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Pobiera kolor, który odnosi się do identyfikatora dla określonego polecenia.|  
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Wywoływane przez platformę, gdy zmienia się okna nadrzędnego.|  
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Otwiera okno dialogowe wyboru kolorów.|  
|[CMFCColorMenuButton::SetColor](#setcolor)|Określa kolor przycisku bieżący kolor.|  
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Określa kolor przycisku menu określony kolor.|  
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Określa nową nazwę dla określonego koloru.|  
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Ustawia liczbę kolumn, które są wyświetlane przez `CMFCColorBar` obiektu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Kopiuje bieżącego przycisku inny przycisk paska narzędzi.|  
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Tworzy okno dialogowe próbnika kolorów.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Wskazuje, czy puste menu są obsługiwane.|  
|[CMFCColorMenuButton::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by wyświetlić obrazu na przycisku.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Metoda wywoływana przez platformę przed `CMFCColorMenuButton` obiekt jest wyświetlany na liście dialogowego Dostosowywanie paska narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 Aby zastąpić oryginalny polecenie menu lub paska narzędzi przycisk za pomocą `CMFCColorMenuButton` obiektu, Utwórz `CMFCColorMenuButton` obiektu, ustawić wszystkie odpowiednie [klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) style, a następnie wywołania `ReplaceButton` metoda [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) klasy. W przypadku dostosowania paska narzędzi wywołać [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) metody.  
  
 Okno dialogowe próbnika kolorów jest tworzony podczas przetwarzania [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) programu obsługi zdarzeń. Program obsługi zdarzeń powiadamia nadrzędnej ramki za pomocą komunikatów WM_COMMAND. `CMFCColorMenuButton` Obiektu wysyła identyfikator kontrolki, przypisany do oryginalnego polecenie menu lub paska narzędzi przycisk.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć i skonfigurować przycisk menu Kolor przy użyciu różnych metod w `CMFCColorMenuButton` klasy. W tym przykładzie `CPalette` obiekt jest najpierw jest tworzony i następnie używane do konstruowania obiektu `CMFCColorMenuButton` klasy. `CMFCColorMenuButton` Obiekt jest następnie konfigurowana przez włączenie jej automatyczne i inne przyciski i ustawianie jego kolor i liczbę kolumn. Ten kod jest częścią [przykład konsola programu Word](../../visual-cpp-samples.md).  
  
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
*uiCmdID*<br/>
[in] Identyfikator przycisku polecenia.  
  
*lpszText*<br/>
[in] Tekst przycisku.  
  
*pPalette*<br/>
[in] Wskaźnik do palety kolorów przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor jest konstruktor domyślny. Kolor bieżącego obiektu i kolorowi automatycznemu są inicjowane na czarny (RGB (0, 0, 0)).  
  
 Drugi Konstruktor inicjuje przycisku na kolor, który odpowiada identyfikator określonego polecenia.  
  
##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom  
 Kopiuje jeden [klasa CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)-pochodnych obiektu do drugiego.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Przycisk źródła do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej metody kopiuje obiekty, które są uzyskiwane z `CMFCColorMenuButton` obiektu.  
  
##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu  
 Tworzy okno dialogowe próbnika kolorów.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt reprezentujący okno dialogowe próbnika kolorów.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy użytkownik naciśnie przycisk menu Kolor.  
  
##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton  
 Włącza i wyłącza przycisk "Automatyczny", który znajduje się powyżej regularne kolor przycisków. (Przycisk Automatyczny standardowych systemowych jest oznaczona etykietą **automatyczne**.)  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*lpszLabel*<br/>
[in] Określa tekst przycisku, który jest wyświetlany, gdy przycisk staje się automatyczne.  
  
*colorAutomatic*<br/>
[in] Określa nowe kolorowi automatycznemu.  
  
*bWłączenie*<br/>
[in] Określa, czy przycisk jest automatyczna.  
  
### <a name="remarks"></a>Uwagi  
 Przycisk Automatyczny dotyczy bieżący kolor domyślny.  
  
##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors  
 Umożliwia wyświetlanie kolorów specyficzne dla dokumentu zamiast kolory systemowe.  
  
```  
void EnableDocumentColors(
    LPCTSTR lpszLabel,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*lpszLabel*<br/>
[in] Określa tekst przycisku.  
  
*bWłączenie*<br/>
[in] Prawda w celu wyświetlania kolorów specyficzne dla dokumentu lub wartość FALSE, aby wyświetlić kolory systemowe.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia wyświetlanie kolorów bieżącego dokumentu lub palety kolorów systemu, gdy użytkownik kliknie przycisk menu Kolor.  
  
##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton  
 Włącza i wyłącza "other" przycisk, który znajduje się poniżej regularne kolor przycisków. (Standardowy system "other" przycisk ma etykietę **więcej kolorów**.)  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*lpszLabel*<br/>
[in] Określa tekst przycisku.  
  
*bAltColorDlg*<br/>
[in] Określ wartość TRUE, aby wyświetlić `CMFCColorDialog` okno dialogowe, lub wartość FALSE, aby wyświetlić okno dialogowe Kolor standardowy system.  
  
*bWłączenie*<br/>
[in] Określ wartość PRAWDA, aby wyświetlić przycisk "other"; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff  
 Włącza możliwość wydzielić okienko kolorów.  
  
```  
void EnableTearOff(
    UINT uiID,  
    int nVertDockColumns=-1,  
    int nHorzDockRows=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiID*<br/>
[in] Określa identyfikator dla tego okienka odrywania.  
  
*nVertDockColumns*<br/>
[in] Określa liczbę kolumn w okienku kolorów w pionie zadokowany w stanie odrywania.  
  
*nHorzDockRows*<br/>
[in] Określa liczbę wierszy dla okienko poziomo zadokowanych kolorów w stanie odrywania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby włączyć funkcję "odrywania" dla tego okienka kolorów, które pojawia się po `CMFCColorMenuButton` naciśnięciu przycisku.  
  
##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor  
 Pobiera bieżący kolor automatyczne.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość koloru RGB, który reprezentuje bieżący kolor automatyczne.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby uzyskać automatyczne kolor, który jest ustawiony przez [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).  
  
##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor  
 Pobiera kolor bieżącego przycisku.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID  
 Pobiera kolor, który odnosi się do identyfikatora dla określonego polecenia.  
  
```  
static COLORREF GetColorByCmdID(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmdID*<br/>
[in] Identyfikator polecenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kolor, który odpowiada identyfikator określonego polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, gdy masz kilka kolor przycisków w aplikacji. Gdy użytkownik kliknie przycisk koloru, przycisk wysyła jego identyfikator polecenia w komunikacie WM_COMMAND do elementu nadrzędnego. `GetColorByCmdID` Metoda używa Identyfikatora polecenia, aby pobrać odpowiedni kolor.  
  
##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed  
 Wskazuje, czy puste menu są obsługiwane.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli puste menu są dozwolone w przeciwnym razie, wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Pusty menu są obsługiwane przez domyślny. Zastępuje tę metodę, aby zmienić to zachowanie w klasie pochodnej.  
  
##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy zmienia się okna nadrzędnego.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik do nowego okna nadrzędnego.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw  
 Metoda wywoływana przez platformę, by wyświetlić obrazu na przycisku.  
  
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
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*Rect*<br/>
[in] Prostokąt, który zakresem obszaru do narysowania.  
  
*pImages*<br/>
[in] Przejść do listy obrazami paska narzędzi.  
  
*bHorz*<br/>
[in] Wartość TRUE, aby określić, że pasek narzędzi jest w stanie zadokowania poziomy; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
*bCustomizeMode*<br/>
[in] Wartość TRUE, aby określić, że aplikacja jest w trybie dostosowywania; w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.  
  
*bHighlight*<br/>
[in] Wartość TRUE, aby określić, czy przycisk jest wyróżniony; w przeciwnym razie wartość FALSE. Wartość domyślna to FALSE.  
  
*bDrawBorder*<br/>
[in] Wartość TRUE, aby określić, czy jest wyświetlany obramowanie przycisku; w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
*bGrayDisabledButtons*<br/>
[in] Wartość TRUE Określa, czy wyłączone przyciski są wygaszone (wyszarzony). w przeciwnym razie wartość FALSE. Wartość domyślna to TRUE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList  
 Metoda wywoływana przez platformę przed `CMFCColorMenuButton` obiekt jest wyświetlany na liście dialogowego Dostosowywanie paska narzędzi.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.  
  
*Rect*<br/>
[in] Prostokąt, który granic przycisku do narysowania.  
  
*bSelected*<br/>
[in] Wartość TRUE Określa, czy przycisk jest w stanie wybrania.; w przeciwnym razie wartość FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez platformę, gdy `CMFCColorMenuButton` obiekt jest wyświetlany w polu listy, w trakcie dostosowywania paska narzędzi.  
  
##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog  
 Otwiera okno dialogowe wyboru kolorów.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parametry  
*colorDefault*<br/>
[in] Domyślny kolor, który wybrano w oknie dialogowym koloru.  
  
*colorRes*<br/>
[out] Zwraca kolor, który użytkownik wybiera z okna dialogowego kolorów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli użytkownik wybierze nowy kolor; w przeciwnym razie, wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Po kliknięciu przycisku menu, należy wywołać tę metodę, aby otworzyć okno dialogowe kolorów. Jeśli wartość zwracana jest wartość różną od zera, kolorów, wybierany przez użytkownika jest przechowywana w *colorRes* parametru. Użyj [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) metodę, aby przełączać się między standardowe okno dialogowe i [klasa CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) okno dialogowe.  
  
##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor  
 Określa kolor przycisku bieżący kolor.  
  
```  
virtual void SetColor(
    COLORREF clr,  
    BOOL bNotify=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*CLR*<br/>
[in] Wartość koloru RGB.  
  
*bNotify*<br/>
[in] Wartość TRUE, aby zastosować *clr* parametru kolor przycisku związanych z menu lub przycisku paska narzędzi; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zmienić kolor przycisku bieżący kolor. Jeśli *bNotify* parametr ma wartość różną od zera, kolor odpowiedni przycisk na wszelkie skojarzone okno podręczne menu lub pasek narzędzi zostanie zmieniona na kolor określony przez *clr* parametru.  
  
##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID  
 Określa kolor przycisku menu określony kolor.  
  
```  
static void SetColorByCmdID(
    UINT uiCmdID,  
    COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmdID*<br/>
[in] Identyfikator zasobu przycisk menu Kolor.  
  
*Kolor*<br/>
[in] Wartość koloru RGB.  
  
##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName  
 Określa nową nazwę dla określonego koloru.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parametry  
*Kolor*<br/>
[in] Wartość RGB kolorów, których nazwa zmienia się.  
  
*strName*<br/>
[in] Nowa nazwa koloru.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber  
 Ustawia liczbę kolumn do wyświetlenia w kontrolkę wyboru koloru ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) obiektu).  
  
```  
void SetColumnsNumber(int nColumns);
```  
  
### <a name="parameters"></a>Parametry  
*nColumns*<br/>
[in] Liczba kolumn do wyświetlenia.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)   
 [Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Klasa CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [Klasa CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)
