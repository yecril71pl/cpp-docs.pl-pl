---
title: Klasa CToolTipCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4708f180a1a1f5e936a6b30650a6432d48878d53
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726755"
---
# <a name="ctooltipctrl-class"></a>Ctooltipctrl — klasa
Hermetyzuje funkcjonalność "firmant narzędzia wskazówki" niewielkie okno podręczne, które wyświetla pojedynczy wiersz tekstu opisującego cel narzędzia w aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Konstruuje `CToolTipCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CToolTipCtrl::Activate](#activate)|Aktywuje i dezaktywuje formantem etykietki narzędzia.|  
|[CToolTipCtrl::AddTool](#addtool)|Rejestruje to narzędzie z formantem etykietki narzędzia.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Konwertuje między formantem etykietki narzędzia wyświetlana prostokąt i jego prostokąt okna.|  
|[CToolTipCtrl::Create](#create)|Tworzy formantem etykietki narzędzia i dołącza je do `CToolTipCtrl` obiektu.|  
|[CToolTipCtrl::CreateEx](#createex)|Tworzy formantem etykietki narzędzia w określonym stylu rozszerzonej Windows i dołącza je do `CToolTipCtrl` obiektu.|  
|[CToolTipCtrl::DelTool](#deltool)|Usuwa to narzędzie z formantem etykietki narzędzia.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Pobiera informacje o rozmiarze etykietki narzędzia.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Pobiera informacje, takie jak rozmiar, położenie i tekst w okno etykietki narzędzia, które wyświetla bieżący kontrolki tooltip.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Pobiera początkowy, okno podręczne oraz reshow formantu etykietki czasów trwania, które są aktualnie ustawione dla narzędzia.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Pobiera pierwszych, po lewej stronie, dolnej i prawego marginesu ustawione dla okna narzędzi porada.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Pobiera maksymalną szerokość okna narzędzia porada.|  
|[CToolTipCtrl::GetText](#gettext)|Pobiera tekst, który obsługuje formantem etykietki narzędzia, dla narzędzia.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Pobiera kolor tła w oknie narzędzi porada.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Pobiera kolor tekstu w oknie narzędzi porada.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Pobiera tytuł bieżącego kontrolki tooltip.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Pobiera liczbę narzędzia obsługiwanego przez formantem etykietki narzędzia.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Pobiera informacje, która utrzymuje formantem etykietki narzędzia o narzędziu.|  
|[CToolTipCtrl::HitTest](#hittest)|Testy punktu w celu ustalenia, czy w ramach prostokąt otaczający danego narzędzia. Jeśli tak, pobiera informacje o tym narzędziu.|  
|[CToolTipCtrl::Pop](#pop)|Usuwa okna narzędzi wyświetlanych Porada w widoku.|  
|[CToolTipCtrl::Popup](#popup)|Powoduje, że bieżący formantu etykietki narzędzia, aby wyświetlić współrzędne ostatniego komunikatu myszy.|  
|[CToolTipCtrl::RelayEvent](#relayevent)|Przekazuje komunikatu myszy formantem etykietki narzędzia w celu przetworzenia.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Określa początkowy podręcznym i reshow czasy trwania formantem etykietki narzędzia.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Ustawia top, po lewej stronie, dolnej i prawego marginesu Porada okna narzędzia.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Ustawia maksymalną szerokość okna narzędzia porada.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Ustawia kolor tła w oknie narzędzi porada.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Ustawia kolor tekstu w oknie narzędzi porada.|  
|[CToolTipCtrl::SetTitle](#settitle)|Dodaje ciąg standardowy ikonę i tytuł do etykietki narzędzia.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Ustawia informacje o, zawierającą etykietka narzędzia.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Ustawia nowy prostokąt otaczający narzędzia.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny okna narzędzia porada.|  
|[CToolTipCtrl::Update](#update)|Wymusza narysowania bieżącego narzędzia.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Ustawia tekst wskazówki dla narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 "Narzędzia" jest albo okien, na przykład okno podrzędne lub kontroli lub zdefiniowanych przez aplikację prostokątny obszar w obrębie obszaru klienckiego okna. Etykietka narzędzia jest ukryty w większości przypadków, pojawiają się tylko po użytkownik umieszcza kursor nad narzędziem i drugie pozostawi je istnieje dla około połowie. Etykietka narzędzia która pojawia się obok kursor i znika, gdy użytkownik kliknie przycisk myszy lub przenosi kursor poza narzędzie.  
  
 `CToolTipCtrl` oferuje funkcje w celu sterowania czas wstępnej i czasu trwania etykietka narzędzia szerokości marginesów otaczający tekst wskazówki, szerokość samo okna Narzędzie Porada i kolor tła i tekstu etykietki narzędzia. Pojedynczy firmant narzędzia wskazówki może dostarczyć informacji dla więcej niż jednego narzędzia.  
  
 `CToolTipCtrl` Klasa oferuje funkcje wspólne formantem etykietki narzędzia Windows. Ta kontrolka (i w związku z tym `CToolTipCtrl` klasy) jest dostępna tylko dla programów uruchomionych w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat włączania etykietek narzędzi, zobacz [etykietek narzędzi w Windows niepochodzące od obiektu CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Aby uzyskać więcej informacji na temat korzystania z `CToolTipCtrl`, zobacz [kontrolki](../../mfc/controls-mfc.md) i [przy użyciu CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="activate"></a>  CToolTipCtrl::Activate  
 Wywołaj tę funkcję, aby aktywować lub dezaktywować formantem etykietki narzędzia.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *bActivate*  
 Określa, czy formantem etykietki narzędzia ma zostać aktywowane lub dezaktywowane.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bActivate* ma wartość PRAWDA, formant jest uaktywniony; Jeśli jest to wartość FAŁSZ, jest nieaktywny.  
  
 Podczas formantem etykietki narzędzia jest aktywna, pojawia się informacja Porada narzędzia, gdy kursor znajduje się nad narzędziem, które jest zarejestrowane w usłudze kontroli. gdy jest nieaktywny, informacje Porada narzędzie jest niewidoczny, nawet gdy kursor znajduje się nad narzędziem.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>  CToolTipCtrl::AddTool  
 Rejestruje to narzędzie z formantem etykietki narzędzia.  
  
```  
BOOL AddTool(
    CWnd* pWnd,  
    UINT nIDText,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);

 
BOOL AddTool(
    CWnd* pWnd,  
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDText*  
 Identyfikator zasobu ciągu zawierający tekst dla narzędzia.  
  
 *lpRectTool*  
 Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury zawierającego współrzędne narzędzie użytkownika prostokąt ograniczający. Współrzędne są podawane względem lewego górnego rogu obszaru klienckiego okna identyfikowane przez *pWnd*.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
 *lpszText*  
 Wskaźnik do tekstu dla narzędzia. Jeśli ten parametr zawiera wartość LPSTR_TEXTCALLBACK, powiadomienia TTN_NEEDTEXT przejdź do nadrzędnego okna, *pWnd* wskazuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 *LpRectTool* i *nIDTool* parametry muszą być prawidłowe, lub jeśli *lpRectTool* ma wartość NULL, *nIDTool* musi mieć wartość 0.  
  
 Formantem etykietki narzędzia może być skojarzony z więcej niż jednego narzędzia. Wywołaj tę funkcję, aby zarejestrować narzędzia z formantem etykietki narzędzia, aby informacje przechowywane w etykietce narzędzia jest wyświetlana, gdy kursor znajduje się w narzędziu.  
  
> [!NOTE]
>  Etykietka narzędzia nie można ustawić statyczną kontrolkę za pomocą `AddTool`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect  
 Konwertuje między tekstem w kontrolce etykietka narzędzia wyświetlana prostokąt i jego prostokąt okna.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która posiada prostokąt okna narzędzia porada lub prostokąt wyświetlania tekstu.  
  
 *bLarger*  
 W przypadku opcji TRUE *lprc* służy do określania prostokąt wyświetlania tekstu i odbiera prostokąt odpowiednie okna. W przypadku wartości FAŁSZ *lprc* służy do określania prostokąt okna i odbiera odpowiedniego prostokątny obszar wyświetlania tekstu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli pomyślnie jest dopasowane prostokątem; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego oblicza formantem etykietki narzędzia prostokątny obszar wyświetlania tekstu z jego prostokąt okna lub prostokąt okna Porada narzędzia potrzebne do wyświetlenia prostokąt wyświetlania określony tekst.  
  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="create"></a>  CToolTipCtrl::Create  
 Tworzy formantem etykietki narzędzia i dołącza je do `CToolTipCtrl` obiektu.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Określa okno nadrzędne formantem etykietki narzędzia, zwykle `CDialog`. Nie może być równa NULL.  
  
 *dwStyle*  
 Określa styl formantem etykietki narzędzia. Zobacz **uwagi** sekcji, aby uzyskać więcej informacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość różną od zera `CToolTipCtrl` obiekt jest pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Konstruowanie `CToolTipCtrl` w dwóch krokach. Po pierwsze wywołanie konstruktora do konstruowania `CToolTipCtrl` obiektu, a następnie wywołaj `Create` tworzenie formantem etykietki narzędzia i dołącz ją do `CToolTipCtrl` obiektu.  
  
 *DwStyle* parametr może być dowolną kombinacją [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles). Ponadto formantem etykietki narzędzia ma dwa style swoiste dla klas: TTS_ALWAYSTIP i TTS_NOPREFIX.  
  
|Styl|Znaczenie|  
|-----------|-------------|  
|TTS_ALWAYSTIP|Określa, czy etykietka narzędzia która pojawi się gdy kursor znajduje się nad narzędziem, niezależnie od tego, czy okno właściciela formantem etykietki narzędzia jest aktywne lub nieaktywne. Bez tego stylu formantem etykietki narzędzia jest wyświetlana po uaktywnieniu okna właściciela tego narzędzia, ale nie w przypadku, gdy jest nieaktywny.|  
|TTS_NOPREFIX|Ten styl zapobiega obcięcie handlowe "i" (&) znaków z ciągu. Jeśli formantem etykietki narzędzia ma styl TTS_NOPREFIX, system automatycznie usuwa znaki handlowego "i", dzięki czemu aplikacja może używać tego samego ciągu jako element menu i jako tekstu w formantem etykietki narzędzia.|  
  
 Formantem etykietki narzędzia ma WS_POPUP i WS_EX_TOOLWINDOW Style okna, niezależnie od tego, czy zostaną one określone podczas tworzenia kontrolki.  
  
 Aby utworzyć formantem etykietki narzędzia windows rozszerzone style, wywołania [CToolTipCtrl::CreateEx](#createex) zamiast `Create`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>  CToolTipCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i powiąż ją z `CToolTipCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *dwStyle*  
 Określa styl formantem etykietki narzędzia. Zobacz **uwagi** części [Utwórz](#create) Aby uzyskać więcej informacji.  
  
 *dwStyleEx*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast `Create` do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl  
 Konstruuje `CToolTipCtrl` obiektu.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `Create` po konstruowanie obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>  CToolTipCtrl::DelTool  
 Usuwa narzędzie określone przez *pWnd* i *nIDTool* z kolekcji narzędzi dostarczonych przez formantem etykietki narzędzia.  
  
```  
void DelTool(
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize  
 Pobiera informacje o rozmiarze etykietki narzędzia.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Wskaźnik do etykietki narzędzia [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar etykietki narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool  
 Pobiera informacje, takie jak rozmiar, położenie i tekst wyświetlany przez kontrolkę tooltip bieżącego okna etykiety narzędzi.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*lpToolInfo*|[out] Wskaźnik do [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) strukturę, która otrzymuje informacje o bieżącym oknie etykietki narzędzia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli informacje są pobierane pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera informacje o bieżącym oknie etykietki narzędzia.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime  
 Pobiera początkowy wyskakujące, a reshow czasów trwania aktualnie ustawione dla formantem etykietki narzędzia.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDuration*  
 Flaga określająca wartość czasu trwania, która zostanie pobrana. Ten parametr może być jedną z następujących wartości:  
  
- Pobrać TTDT_AUTOPOP czas etykietka narzędzia okna pozostają widoczne, jeśli wskaźnik jest nieruchomy w ramach narzędzia prostokąt otaczający.  
  
- Pobieranie TTDT_INITIAL długość czasu, jaki wskaźnik musi pozostać stacjonarnych w ramach narzędzia prostokąt otaczający przed okno porad narzędzia pojawi się.  
  
- Pobieranie TTDT_RESHOW długość czasu potrzebnego dla kolejnych Porada okna są wyświetlane jako wskaźnik jest przenoszony z jednego narzędzia do innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony okres czasu, w milisekundach  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin  
 Pobiera pierwszych, po lewej stronie, dolnej i prawego marginesu dla okna narzędzi porada.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adres `RECT` struktury, który będzie otrzymywać informacje margines. Elementy członkowskie [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury nie definiują prostokąt otaczający. Na potrzeby tego komunikatu elementy członkowskie struktury jest interpretowany w następujący sposób:  
  
|Element członkowski|Reprezentacja|  
|------------|--------------------|  
|`top`|Odległość między górną krawędź i od góry tekst wskazówki, w pikselach.|  
|`left`|Odległość między lewą krawędź lewego końca tekst porady, w pikselach.|  
|`bottom`|Odległość między dolną krawędź i u dołu tekst porady, w pikselach.|  
|`right`|Odległość między prawą krawędź prawego końca tekst porady, w pikselach.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth  
 Pobiera maksymalną szerokość okna narzędzia porada.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna szerokość okna narzędzi porada.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettext"></a>  CToolTipCtrl::GetText  
 Pobiera tekst, który obsługuje formantem etykietki narzędzia, dla narzędzia.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Odwołanie do `CString` obiekt, który odbiera tekst tego narzędzia.  
  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 *PWnd* i *nIDTool* parametry zidentyfikować narzędzie. Jeśli został wcześniej zarejestrowany tego narzędzia z formantem etykietki narzędzia, za pomocą poprzedniego wywołania `CToolTipCtrl::AddTool`, zawiera odwołanie do obiektu *str* parametr jest przypisany tekst tego narzędzia.  
  
##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor  
 Pobiera kolor tła w oknie narzędzi porada.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](/windows/desktop/gdi/colorref) wartość, która reprezentuje kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor  
 Pobiera kolor tekstu w oknie narzędzi porada.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](/windows/desktop/gdi/colorref) wartość, która reprezentuje kolor tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle  
 Pobiera tytuł bieżącego kontrolki tooltip.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*pttgt*|[out] Wskaźnik do [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) strukturę, która zawiera informacje o formancie ToolTip. Po powrocie z tej metody *pszTitle* członkiem [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) struktury wskazuje tekst tytułu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount  
 Pobiera liczbę narzędzia zarejestrowany z formantem etykietki narzędzia.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba narzędzia zarejestrowana z formantem etykietki narzędzia.  
  
##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo  
 Pobiera informacje, która utrzymuje formantem etykietki narzędzia o narzędziu.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ToolInfo*  
 Odwołanie do `TOOLINFO` obiekt, który odbiera tekst tego narzędzia.  
  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `hwnd` i `uId` członkowie [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktury odwołuje się *CToolInfo* zidentyfikować narzędzie. Jeśli zarejestrowano tego narzędzia, z formantem etykietki narzędzia, za pomocą poprzedniego wywołania `AddTool`, `TOOLINFO` struktury jest wypełniony przy użyciu informacji o tym narzędziu.  
  
##  <a name="hittest"></a>  CToolTipCtrl::HitTest  
 Testy punktu w celu ustalenia, czy w ramach prostokąt otaczający danego narzędzia, a jeśli tak, należy pobrać informacji o tym narzędziu.  
  
```  
BOOL HitTest(
    CWnd* pWnd,  
    CPoint pt,  
    LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *(czas pacyficzny)*  
 Wskaźnik do `CPoint` obiekt, który zawiera współrzędne punktu ma zostać przetestowana.  
  
 *lpToolInfo*  
 Wskaźnik do [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) strukturę, która zawiera informacje o tym narzędziu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli określony przez informacji testowania trafienia punkt znajduje się w narzędzia prostokąt otaczający; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta funkcja zwraca wartość różną od zera, struktury, wskazywana przez *lpToolInfo* jest wypełniony informacjami na temat narzędzia w ramach którego prostokąta znajduje się punkt.  
  
 `TTHITTESTINFO` Struktura jest zdefiniowana w następujący sposób:  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 `hwnd`  
 Określa dojście do tego narzędzia.  
  
 `pt`  
 Określa współrzędne punktu, gdy punkt jest za pomocą narzędzia prostokąt ograniczający.  
  
 `ti`  
 Informacje o tym narzędziu. Aby uzyskać więcej informacji na temat `TOOLINFO` struktury, zobacz [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>  CToolTipCtrl::Pop  
 Okno porad wyświetlanych narzędzie usuwa z widoku.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_POP](/windows/desktop/Controls/ttm-pop), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="popup"></a>  CToolTipCtrl::Popup  
 Powoduje, że bieżący formantu etykietki narzędzia, aby wyświetlić współrzędne ostatniego komunikatu myszy.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_POPUP](/windows/desktop/Controls/ttm-popup) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu wyświetla się okno etykiety narzędzi.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent  
 Przekazuje komunikatu myszy formantem etykietki narzędzia w celu przetworzenia.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMsg*  
 Wskaźnik do [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958) strukturę, która zawiera do przekazywania wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Formantem etykietki narzędzia przetwarza tylko następujące komunikaty, które są wysyłane do niej przez `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE|  
|---------------------|-------------------|  
|WM_LBUTTONUP|WM_RBUTTONDOWN|  
|WM_MBUTTONDOWN|WM_RBUTTONUP|  
|WM_MBUTTONUP||  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime  
 Ustawia czas opóźnienia dla formantem etykietki narzędzia.  
  
```  
void SetDelayTime(UINT nDelay);

 
void SetDelayTime(
    DWORD dwDuration,  
    int iTime);
```  
  
### <a name="parameters"></a>Parametry  
 *nDelay*  
 Określa nową wartość czasu opóźnienia, w milisekundach.  
  
 *dwDuration*  
 Flaga określająca wartość czasu trwania, która zostanie pobrana. Zobacz [CToolTipCtrl::GetDelayTime](#getdelaytime) opis prawidłowych wartości.  
  
 *iTime*  
 Czas określony opóźnienie w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Czas opóźnienia jest długością razem, gdy kursor musi pozostawać nad narzędziem, zanim zostanie wyświetlone okno Porada narzędzia. Domyślny czas opóźnienia wynosi 500 milisekund.  
  
##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin  
 Ustawia top, po lewej stronie, dolnej i prawego marginesu Porada okna narzędzia.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adres `RECT` strukturę, która zawiera informacje o margines do ustawienia. Elementy członkowskie `RECT` struktury nie definiują prostokąt otaczający. Zobacz [CToolTipCtrl::GetMargin](#getmargin) opis informacji margines.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth  
 Ustawia maksymalną szerokość okna narzędzia porada.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *iWidth*  
 Narzędzie maksymalną szerokość okna Porada można ustawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie szerokość maksymalna porada.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor  
 Ustawia kolor tła w oknie narzędzi porada.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Nowy kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor  
 Ustawia kolor tekstu w oknie narzędzi porada.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Nowy kolor tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settitle"></a>  CToolTipCtrl::SetTitle  
 Dodaje ciąg standardowy ikonę i tytuł do etykietki narzędzia.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Parametry  
 *uIcon*  
 Zobacz *ikonę* w [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) w zestawie Windows SDK.  
  
 *lpstrTitle*  
 Wskaźnik na ciąg tytułu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego implementuje zachowanie komunikatu Win32 [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo  
 Ustawia informacje o, zawierającą etykietka narzędzia.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Wskaźnik do [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) strukturę, która określa informacje, które można ustawić.  
  
##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect  
 Ustawia nowy prostokąt otaczający narzędzia.  
  
```  
void SetToolRect(
    CWnd* pWnd,  
    UINT_PTR nIDTool,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
 *lprect —*  
 Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, określając nowy prostokąt otaczający.  
  
##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme  
 Ustawia styl wizualny okna narzędzia porada.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 *pszSubAppName*  
 Wskaźnik na ciąg Unicode, który zawiera styl wizualny do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość nie jest używana.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność [TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme) komunikat, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="update"></a>  CToolTipCtrl::Update  
 Wymusza narysowania bieżącego narzędzia.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText  
 Aktualizuje tekst wskazówki dla narzędzi tej kontrolki.  
  
```  
void UpdateTipText(
    LPCTSTR lpszText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);

 
void UpdateTipText(
    UINT nIDText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Wskaźnik do tekstu dla narzędzia.  
  
 *pWnd*  
 Wskaźnik do okna, które zawiera narzędzia.  
  
 *nIDTool*  
 Identyfikator narzędzia.  
  
 *nIDText*  
 Identyfikator zasobu ciągu zawierający tekst dla narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)
