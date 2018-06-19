---
title: CToolTipCtrl — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: de230a82adaaafc149d2ed5a762977205c798b03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377613"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl — klasa
Hermetyzuje funkcjonalność "formantem etykietki narzędzia," małe okno podręczne wyświetlające pojedynczy wiersz tekst opisujący cel narzędzia w aplikacji.  
  
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
|[CToolTipCtrl::AddTool](#addtool)|Rejestruje narzędzie z formantem etykietki narzędzia.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Konwertuje między formantem etykietki narzędzia wyświetlana prostokąt i jego prostokąt okna.|  
|[CToolTipCtrl::Create](#create)|Tworzy formantem etykietki narzędzia i dołącza go do `CToolTipCtrl` obiektu.|  
|[CToolTipCtrl::CreateEx](#createex)|Tworzy formantem etykietki narzędzia w określonym stylu rozszerzonej systemu Windows i dołącza go do `CToolTipCtrl` obiektu.|  
|[CToolTipCtrl::DelTool](#deltool)|Usuwa to narzędzie z formantem etykietki narzędzia.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Pobiera informacje o rozmiarze etykietka narzędzia.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Pobiera informacje, takie jak rozmiar, położenie i tekstu okna etykietki narzędzia wyświetlany bieżącego formantu tooltip.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Pobiera początkowy, podręczne oraz reshow formantu etykietki okresów, które są aktualnie ustawione dla narzędzia.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Pobiera top, lewej strony, dołu i prawego marginesu, które są ustawione dla okna Porada narzędzia.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Pobiera maksymalną szerokość okna Porada narzędzia.|  
|[CToolTipCtrl::GetText](#gettext)|Pobiera tekst, który obsługuje formantem etykietki narzędzia dla narzędzia.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Pobiera kolor tła w oknie Porada narzędzia.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Pobiera kolor tekstu w oknie Porada narzędzia.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Pobiera tytuł bieżącego formantu tooltip.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Pobiera liczbę narzędzia obsługiwanego przez formantem etykietki narzędzia.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Pobiera formantem etykietki narzędzia przechowuje informacje dotyczące narzędzia.|  
|[CToolTipCtrl::HitTest](#hittest)|Testy punktu w celu ustalenia, czy w ramach prostokątem danego narzędzia. Jeśli tak, pobiera informacje o narzędziu.|  
|[CToolTipCtrl::Pop](#pop)|Usuwa wyświetlane okno Porada w widoku.|  
|[CToolTipCtrl::Popup](#popup)|Powoduje, że bieżący formantu ToolTip do wyświetlenia na współrzędne ostatniego komunikatu myszy.|  
|[CToolTipCtrl::RelayEvent](#relayevent)|Przekazuje komunikatu myszy formantem etykietki narzędzia w celu przetworzenia.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Ustawia początkowej wyskakujących i reshow czasy trwania formantem etykietki narzędzia.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Ustawia góry po lewej, dolnej i prawego marginesu Porada okna narzędzia.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Ustawia maksymalną szerokość okna Porada narzędzia.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Ustawia kolor tła w oknie Porada narzędzia.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Ustawia kolor tekstu w oknie Porada narzędzia.|  
|[CToolTipCtrl::SetTitle](#settitle)|Dodaje ciąg standardowy ikony, jak i tytuł etykietka narzędzia.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Ustawia informacje, które obsługuje etykietki narzędzia dla narzędzia.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Ustawia nowy prostokąt ograniczający narzędzia.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny Porada okna narzędzia.|  
|[CToolTipCtrl::Update](#update)|Wymusza bieżącego narzędzia do narysowania.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Ustawia tekst wskazówki dla narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 "Narzędzia" jest albo okna, takich jak kontrolki lub okna podrzędnego albo zdefiniowanym przez aplikację prostokątny obszar wewnątrz obszaru klienckiego okna. Etykietka narzędzia, która jest niewidoczna w większości przypadków pojawiające się tylko po użytkownik umieszcza kursor na narzędzia i drugi pozostawia jej istnieje na około pół. Etykietka narzędzia, która pojawi się w pobliżu kursor i znika, gdy użytkownik kliknie przycisk myszy lub przesuwa kursor poza narzędzie.  
  
 `CToolTipCtrl` udostępnia funkcje umożliwiające kontroli początkowy czas i czas trwania etykietka narzędzia otaczający tekst wskazówki, szerokość okna Porada narzędzia sam i kolor tła i tekstu podpowiedzi szerokości marginesów. Formantem etykietki narzędzia pojedynczego zapewniają informacje o więcej niż jedno narzędzie.  
  
 `CToolTipCtrl` Klasa udostępnia funkcje formantem etykietki narzędzia wspólne systemu Windows. Ten formant (i w związku z tym `CToolTipCtrl` klasy) jest dostępne tylko dla programów w wersji Windows 95/98 i Windows NT 3.51 lub nowszej.  
  
 Aby uzyskać więcej informacji na temat włączania etykietki narzędzi, zobacz [etykietki narzędzi w systemie Windows niepochodzące od obiektu CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Aby uzyskać więcej informacji na temat używania `CToolTipCtrl`, zobacz [formanty](../../mfc/controls-mfc.md) i [przy użyciu CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="activate"></a>  CToolTipCtrl::Activate  
 Wywołanie tej funkcji, aby aktywować lub dezaktywować formantem etykietki narzędzia.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 `bActivate`  
 Określa, czy formantem etykietki narzędzia ma być aktywowany lub dezaktywowany.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bActivate` jest **TRUE**, formant jest uaktywniony; Jeśli **FALSE**, jego jest dezaktywowana.  
  
 Podczas aktywnej jest formantem etykietki narzędzia, gdy kursor znajduje się w zarejestrowany za pomocą formantu; narzędzie pojawia się informacja Porada narzędzia gdy jest nieaktywny, informacje Porada narzędzia nie ma, nawet gdy kursor znajduje się na to narzędzie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>  CToolTipCtrl::AddTool  
 Rejestruje narzędzie z formantem etykietki narzędzia.  
  
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
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDText`  
 Identyfikator zasobu ciągu zawierającego tekst dla narzędzia.  
  
 *lpRectTool*  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury zawierającej współrzędne narzędzia do ograniczenia prostokąta. Współrzędne są podawane względem lewego górnego rogu obszaru klienckiego okna identyfikowane przez `pWnd`.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
 `lpszText`  
 Wskaźnik do tekstu dla tego narzędzia. Jeśli ten parametr ma wartość **LPSTR_TEXTCALLBACK**, **TTN_NEEDTEXT** komunikatów powiadomień przejdź do nadrzędnego okna który `pWnd` wskazuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **LpRectTool** i **nIDTool** parametry muszą być prawidłowe, lub jeśli **lpRectTool** ma wartość NULL, **nIDTool** musi być równa 0.  
  
 Formantem etykietki narzędzia może być skojarzony z więcej niż jednego narzędzia. Wywołanie tej funkcji, aby zarejestrować narzędzia z formantem etykietki narzędzia tak, aby informacje przechowywane w etykietce narzędzia jest wyświetlana, gdy kursor znajduje się w narzędziu.  
  
> [!NOTE]
>  Nie można ustawić etykietka narzędzia, która je przy użyciu statyczną kontrolkę `AddTool`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect  
 Konwertuje między tekstu formantu tooltip wyświetlanie prostokąt i jego prostokąt okna.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) strukturę, która przechowuje prostokąt okna narzędzia porada lub prostokątny obszar wyświetlania tekstu.  
  
 `bLarger`  
 Jeśli **TRUE**, `lprc` służy do określania prostokąt wyświetlania tekstu i otrzymuje prostokąt odpowiednie okna. Jeśli **FALSE**, `lprc` służy do określania prostokąt okna i otrzymuje odpowiedniego prostokątny obszar wyświetlania tekstu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie dostosowania prostokąt; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego oblicza formantem etykietki narzędzia prostokątny obszar wyświetlania tekstu z jego prostokąt okna lub prostokąt okna Porada narzędzia potrzebne do wyświetlenia prostokąt wyświetlania określony tekst.  
  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_ADJUSTRECT](http://msdn.microsoft.com/library/windows/desktop/bb760352), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="create"></a>  CToolTipCtrl::Create  
 Tworzy formantem etykietki narzędzia i dołącza go do `CToolTipCtrl` obiektu.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Określa okno nadrzędne formantem etykietki narzędzia, zwykle `CDialog`. Nie może być **NULL**.  
  
 `dwStyle`  
 Określa styl formantem etykietki narzędzia. Zobacz **uwagi** sekcji, aby uzyskać więcej informacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CToolTipCtrl` obiektu jest pomyślnie utworzony; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Możesz utworzyć `CToolTipCtrl` w dwóch krokach. Najpierw należy wywołać konstruktora, aby utworzyć `CToolTipCtrl` obiekt, a następnie wywołać **Utwórz** utworzyć formantem etykietki narzędzia i dołączenie go do `CToolTipCtrl` obiektu.  
  
 `dwStyle` Parametr może być dowolną kombinacją [Style okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Ponadto formantem etykietki narzędzia ma dwa style właściwe dla klasy: **TTS_ALWAYSTIP** i **TTS_NOPREFIX**.  
  
|Styl|Znaczenie|  
|-----------|-------------|  
|**TTS_ALWAYSTIP**|Określa, czy etykietka narzędzia, która będzie są wyświetlane, gdy kursor znajduje się w narzędzia, niezależnie od tego, czy okno właściciela formantem etykietki narzędzia aktywne lub nieaktywne. Bez tego stylu formantem etykietki narzędzia pojawia się, gdy właściciel okno jest aktywne, a nie jest nieaktywny.|  
|**TTS_NOPREFIX**|Ten styl zapobiega usuwanie ampersand (&) znaków z ciągu. Jeśli nie jest formantem etykietki narzędzia **TTS_NOPREFIX** stylu, system automatycznie usuwa znaki handlowe "i", dzięki czemu aplikacja może używać tych samych parametrach jako element menu i jako tekst w formantem etykietki narzędzia.|  
  
 Formantem etykietki narzędzia ma `WS_POPUP` i **ws_ex_toolwindow —** Style okna, niezależnie od tego, czy zostały określone podczas tworzenia formantu.  
  
 Aby utworzyć formantem etykietki narzędzia z windows rozszerzone style, wywołania [CToolTipCtrl::CreateEx](#createex) zamiast **Utwórz**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>  CToolTipCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i skojarz ją z `CToolTipCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `dwStyle`  
 Określa styl formantem etykietki narzędzia. Zobacz **uwagi** sekcji [Utwórz](#create) Aby uzyskać więcej informacji.  
  
 *dwStyleEx*  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera w razie powodzenia 0 w inny sposób.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast **Utwórz** dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl  
 Konstruuje `CToolTipCtrl` obiektu.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać **Utwórz** po konstruowania obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>  CToolTipCtrl::DelTool  
 Usuwa określony przez narzędzie `pWnd` i `nIDTool` z kolekcji narzędzi dostarczonych przez formantem etykietki narzędzia.  
  
```  
void DelTool(
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize  
 Pobiera informacje o rozmiarze etykietka narzędzia.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lpToolInfo`  
 Wskaźnik do etykietka narzędzia [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktury.  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar etykietka narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETBUBBLESIZE](http://msdn.microsoft.com/library/windows/desktop/bb760387), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool  
 Pobiera informacje, takie jak rozmiar, położenie i tekstu okna etykietki narzędzia wyświetlany przez bieżący formantu tooltip.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] `lpToolInfo`|Wskaźnik do [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktury służącą do odbierania informacji na temat bieżącego okna etykietki narzędzia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli informacje są pobierane pomyślnie; w przeciwnym razie wartość `false.`  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_GETCURRENTTOOL](http://msdn.microsoft.com/library/windows/desktop/bb760389) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera informacje o bieżącym oknie etykietka narzędzia.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime  
 Pobiera początkowy wyskakujących i reshow okresów aktualnie ustawione dla formantem etykietki narzędzia.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `dwDuration`  
 Flaga określająca, które wartości czasu trwania zostaną pobrane. Ten parametr może mieć jedną z następujących wartości:  
  
- `TTDT_AUTOPOP` Pobieranie długości razem, gdy porada okno pozostaje widoczne, gdy wskaźnik pozostaje nieruchomy wewnątrz prostokątem to narzędzie.  
  
- `TTDT_INITIAL` Pobiera długość czasu, jaki wskaźnik musi spędzić w bezruchu wewnątrz prostokątem to narzędzie, zanim pojawi się okno Porada narzędzia.  
  
- `TTDT_RESHOW` Pobierz czas, jaki zajmuje kolejnych narzędzia windows Porada się pojawiać, gdy wskaźnik zostanie przeniesiony z jednego narzędzia do innego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określony okres czasu, w milisekundach  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETDELAYTIME](http://msdn.microsoft.com/library/windows/desktop/bb760390), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin  
 Pobiera góry po lewej, dolnej i prawego marginesu, ustaw dla okna Porada narzędzia.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Adres `RECT` strukturę, która będzie otrzymywać informacje margines. Elementy członkowskie [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury nie definiują prostokąt ograniczający. Na potrzeby tego komunikatu elementy członkowskie struktury interpretowania w następujący sposób:  
  
|Element członkowski|Reprezentacja wartości|  
|------------|--------------------|  
|**Do góry**|Odległości między górnej krawędzi górnej części tekst wskazówki, w pikselach.|  
|**left**|Odległość między lewą krawędzią a lewego końca tekst porady w pikselach.|  
|**bottom**|Odległość między dolną granicę i u dołu tekst porady w pikselach.|  
|**right**|Odległości między prawą krawędź prawego końca tekst porady w pikselach.|  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760391), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth  
 Pobiera maksymalną szerokość okna Porada narzędzia.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna szerokość okna Porada narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760392), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettext"></a>  CToolTipCtrl::GetText  
 Pobiera tekst, który obsługuje formantem etykietki narzędzia dla narzędzia.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Odwołanie do `CString` obiekt, który odbiera narzędzia tekstu.  
  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
### <a name="remarks"></a>Uwagi  
 `pWnd` i `nIDTool` parametry zidentyfikować narzędzie. Jeśli narzędzia został wcześniej zarejestrowany z formantem etykietki narzędzia przez poprzednie wywołanie **CToolTipCtrl::AddTool**, zawiera odwołanie do obiektu `str` parametru przypisano narzędzia tekstu.  
  
##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor  
 Pobiera kolor tła w oknie Porada narzędzia.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która reprezentuje kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760394), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor  
 Pobiera kolor tekstu w oknie Porada narzędzia.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która reprezentuje kolor tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_GETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760395), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle  
 Pobiera tytuł bieżącego formantu tooltip.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out] `pttgt`|Wskaźnik do [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) struktury, który zawiera informacje o formantu ToolTip. Gdy metoda zwróci wartość, `pszTitle` członkiem [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) struktury punkty tekstu tytułu.|  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_GETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760396) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount  
 Pobiera liczbę narzędzia zarejestrowany z formantem etykietki narzędzia.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba narzędzia zarejestrowany z formantem etykietki narzędzia.  
  
##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo  
 Pobiera formantem etykietki narzędzia przechowuje informacje dotyczące narzędzia.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ToolInfo*  
 Odwołanie do `TOOLINFO` obiekt, który odbiera narzędzia tekstu.  
  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 **Hwnd** i **uId** członkami [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktury odwołuje się *CToolInfo* zidentyfikować narzędzie. Jeśli został zarejestrowany z formantem etykietki narzędzia przez poprzednie wywołanie tego narzędzia `AddTool`, `TOOLINFO` struktura jest wypełniony informacji o narzędziu.  
  
##  <a name="hittest"></a>  CToolTipCtrl::HitTest  
 Testy z punktem w celu ustalenia, czy w ramach prostokątem danego narzędzia, a jeśli tak, pobrać informacji o narzędziu.  
  
```  
BOOL HitTest(
    CWnd* pWnd,  
    CPoint pt,  
    LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `pt`  
 Wskaźnik do `CPoint` obiekt zawierający współrzędne punktu do sprawdzenia.  
  
 `lpToolInfo`  
 Wskaźnik do [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktury, który zawiera informacje o narzędziu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli punkt określonym przez test trafień informacji znajduje się w narzędzia prostokąt ograniczający; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta funkcja zwraca wartość niezerową, struktura wskazywana przez `lpToolInfo` informacji o narzędziu, w których prostokąta znajduje się punkt jest wypełnione.  
  
 `TTHITTESTINFO` Struktury jest zdefiniowane w następujący sposób:  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 **Właściwość hwnd**  
 Określa narzędzie dojścia.  
  
 **PT**  
 Określa współrzędne punktu, gdy punkt jest za pomocą narzędzia obwiedni prostokąta.  
  
 **Analizy czasowej**  
 Informacje o narzędziu. Aby uzyskać więcej informacji na temat `TOOLINFO` struktury, zobacz [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>  CToolTipCtrl::Pop  
 Usuwa wyświetlane okno Porada w widoku.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_POP](http://msdn.microsoft.com/library/windows/desktop/bb760401), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="popup"></a>  CToolTipCtrl::Popup  
 Powoduje, że bieżący formantu tooltip do wyświetlenia na współrzędne ostatniego komunikatu myszy.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [TTM_POPUP](http://msdn.microsoft.com/library/windows/desktop/bb760402) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia okna etykietki narzędzia.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent  
 Przekazuje komunikatu myszy formantem etykietki narzędzia w celu przetworzenia.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `lpMsg`  
 Wskaźnik do [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) strukturę, która zawiera do przekazywania wiadomości.  
  
### <a name="remarks"></a>Uwagi  
 Formantem etykietki narzędzia przetwarza tylko następujące komunikaty, które są wysyłane do niej przez `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE|  
|---------------------|-------------------|  
|`WM_LBUTTONUP`|`WM_RBUTTONDOWN`|  
|`WM_MBUTTONDOWN`|`WM_RBUTTONUP`|  
|`WM_MBUTTONUP`||  
  
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
 Określa czas opóźnienia nowe, w milisekundach.  
  
 `dwDuration`  
 Flaga określająca, które wartości czasu trwania zostaną pobrane. Zobacz [CToolTipCtrl::GetDelayTime](#getdelaytime) opis prawidłowych wartości.  
  
 *iTime*  
 Czas określony opóźnienie w milisekundach.  
  
### <a name="remarks"></a>Uwagi  
 Czas opóźnienia jest czas, który kursor musi pozostać na narzędzie przed wyświetleniem okna narzędzia porada. Domyślny czas opóźnienia wynosi 500 milisekund.  
  
##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin  
 Ustawia góry po lewej, dolnej i prawego marginesu Porada okna narzędzia.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Parametry  
 `lprc`  
 Adres `RECT` strukturę, która zawiera informacje margines ma zostać ustawiona. Elementy członkowskie `RECT` struktury nie definiują prostokąt ograniczający. Zobacz [CToolTipCtrl::GetMargin](#getmargin) opis informacji margines.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_SETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760406), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth  
 Ustawia maksymalną szerokość okna Porada narzędzia.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *iWidth*  
 Narzędzie maksymalną szerokość okna Porada można ustawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie szerokość maksymalna porada.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_SETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760408), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor  
 Ustawia kolor tła w oknie Porada narzędzia.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 Nowy kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_SETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760411), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor  
 Ustawia kolor tekstu w oknie Porada narzędzia.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 Na nowy kolor tekstu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_SETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760413), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settitle"></a>  CToolTipCtrl::SetTitle  
 Dodaje ciąg standardowy ikony, jak i tytuł etykietka narzędzia.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Parametry  
 *uIcon*  
 Zobacz *ikona* w [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414) w zestawie Windows SDK.  
  
 *lpstrTitle*  
 Wskaźnik do ciągu tytułu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414), zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo  
 Ustawia informacje, które obsługuje etykietki narzędzia dla narzędzia.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpToolInfo`  
 Wskaźnik do [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) strukturę, która określa informacji do ustawienia.  
  
##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect  
 Ustawia nowy prostokąt ograniczający narzędzia.  
  
```  
void SetToolRect(
    CWnd* pWnd,  
    UINT_PTR nIDTool,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
 `lpRect`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) Określanie prostokąt ograniczający nowe struktury.  
  
##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme  
 Ustawia styl wizualny Porada okna narzędzia.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 `pszSubAppName`  
 Wskaźnik do ciąg Unicode, który zawiera styl wizualny, aby ustawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrotna nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [TTM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb760418) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="update"></a>  CToolTipCtrl::Update  
 Wymusza bieżącego narzędzia do narysowania.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText  
 Aktualizuje tekst wskazówki dla narzędzi tego formantu.  
  
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
 `lpszText`  
 Wskaźnik do tekstu dla tego narzędzia.  
  
 `pWnd`  
 Wskaźnik do okna zawierającego to narzędzie.  
  
 `nIDTool`  
 Identyfikator narzędzia.  
  
 `nIDText`  
 Identyfikator zasobu ciągu zawierającego tekst dla narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CToolBar](../../mfc/reference/ctoolbar-class.md)
