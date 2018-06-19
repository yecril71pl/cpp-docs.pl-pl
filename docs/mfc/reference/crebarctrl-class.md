---
title: Crebarctrl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
dev_langs:
- C++
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e595db4e194744ce5d1f1d644a55423c1022fc2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33377590"
---
# <a name="crebarctrl-class"></a>Crebarctrl — klasa
Hermetyzuje funkcjonalność formantu paska pomocniczego, który jest kontenerem dla okna podrzędnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Konstruuje `CReBarCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|Umieszcza formantu paska pomocniczego w trybie przeciągania i upuszczania.|  
|[CReBarCtrl::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza go do `CReBarCtrl` obiektu.|  
|[CReBarCtrl::CreateEx](#createex)|Tworzy kontrolkę paska pomocniczego w określonym stylu rozszerzonej systemu Windows i dołącza go do `CReBarCtrl` obiektu.|  
|[CReBarCtrl::DeleteBand](#deleteband)|Usuwa obiekt band z formantem paska pomocniczego.|  
|[CReBarCtrl::DragMove](#dragmove)|Aktualizuje pozycji przeciągnij w formancie paska pomocniczego po wywołaniu `BeginDrag`.|  
|[CReBarCtrl::EndDrag](#enddrag)|Kończy operację przeciągania i upuszczania formantu paska pomocniczego.|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|Pobiera obramowania grupy.|  
|[CReBarCtrl::GetBandCount](#getbandcount)|Pobiera liczbę przedziałów, w obecnie w formancie paska pomocniczego.|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Pobiera informacje o przedziałów w formancie paska pomocniczego.|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Pobiera marginesy grupy.|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|Pobiera wysokość formantu paska pomocniczego.|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Pobiera informacje o formancie paska pomocniczego i listy obrazów, które są używane.|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|Pobiera domyślny kolor tła formantu paska pomocniczego.|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Pobiera [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury skojarzony z formantem paska pomocniczego.|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Pobiera formantu paska pomocniczego `IDropTarget` wskaźnika interfejsu.|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera styl rozszerzony bieżącego formantu paska pomocniczego.|  
|[CReBarCtrl::GetImageList](#getimagelist)|Pobiera skojarzony z formantem paska pomocniczego listy obrazów.|  
|[CReBarCtrl::GetPalette](#getpalette)|Pobiera bieżący palety formantu paska pomocniczego.|  
|[CReBarCtrl::GetRect](#getrect)|Pobiera prostokąt ograniczający dla danej grupy w formancie paska pomocniczego.|  
|[CReBarCtrl::GetRowCount](#getrowcount)|Pobiera liczbę wierszy poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|Pobiera wysokość wiersza określony w formancie paska pomocniczego.|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|Pobiera domyślny kolor tekstu formantu paska pomocniczego.|  
|[CReBarCtrl::GetToolTips](#gettooltips)|Pobiera dojścia do dowolnego skojarzony z formantem paska pomocniczego formantem etykietki narzędzia.|  
|[CReBarCtrl::HitTest](#hittest)|Określa, która część pasma paska pomocniczego jest w danym punkcie ekranu, jeśli pasmem paska pomocniczego istnieje w tym momencie.|  
|[CReBarCtrl::IDToIndex](#idtoindex)|Indeks poza pasmem w formancie paska pomocniczego konwertuje pasmem identyfikator (ID).|  
|[CReBarCtrl::InsertBand](#insertband)|Wstawia nową grupę w formancie paska pomocniczego.|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|Zmienia rozmiar poza pasmem w formancie paska pomocniczego największy rozmiar.|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|Zmienia rozmiar poza pasmem w formancie paska pomocniczego do najmniejszy.|  
|[CReBarCtrl::MoveBand](#moveband)|Przenosi obiekt band z jednego indeksu.|  
|[CReBarCtrl::PushChevron](#pushchevron)|Programowo wypycha cudzysłów ostrokątny.|  
|[CReBarCtrl::RestoreBand](#restoreband)|Zmienia rozmiar poza pasmem w formancie paska pomocniczego do jego rozmiar idealny.|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Ustawia właściwości istniejącego poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Ustawia szerokość przedziałów zadokowanych w bieżącym formantu paska pomocniczego.|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Ustawia właściwości formantu paska pomocniczego.|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|Ustawia domyślny kolor tła formantu paska pomocniczego.|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Ustawia schemat kolorów przycisków w formancie paska pomocniczego.|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla bieżącego formantu paska pomocniczego.|  
|[CReBarCtrl::SetImageList](#setimagelist)|Ustawia listy obrazów z formantem paska pomocniczego.|  
|[CReBarCtrl::SetOwner](#setowner)|Ustawia okno właściciela formantu paska pomocniczego.|  
|[CReBarCtrl::SetPalette](#setpalette)|Ustawia bieżący palety formantu paska pomocniczego.|  
|[CReBarCtrl::SetTextColor](#settextcolor)|Ustawia domyślny kolor tekstu formantu paska pomocniczego.|  
|[CReBarCtrl::SetToolTips](#settooltips)|Kojarzy formantem etykietki narzędzia z formantem paska pomocniczego.|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny formantu paska pomocniczego.|  
|[CReBarCtrl::ShowBand](#showband)|Pokazuje lub ukrywa danego poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::SizeToRect](#sizetorect)|Pasuje do formantu paska pomocniczego do określonego prostokąta.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja, w której znajduje się kontrolka paska pomocniczego przypisuje okna podrzędnego zawarty w paśmie paska pomocniczego kontrolki paska pomocniczego. Okno podrzędne jest zazwyczaj inny formant wspólnej.  
  
 Formanty paska pomocniczego zawiera jeden lub więcej grup. Każdej grupy może zawierać kombinację pasek uchwytu, mapy bitowej etykietę tekstową i okna podrzędnego. Grupy mogą zawierać tylko jeden z tych elementów.  
  
 Kontrolka paska pomocniczego można wyświetlić okno podrzędne za pośrednictwem określonego tła mapy bitowej. Wszystkie grupy formantu paska pomocniczego można zmieniać, z wyjątkiem tych, które używają **RBBS_FIXEDSIZE** stylu. W przypadku zmiany położenia lub zmieniania rozmiaru grupy formantu paska pomocniczego kontrolki paska pomocniczego zarządza rozmiar i położenie okna podrzędnego przypisane do tej grupy. Aby zmienić rozmiar lub zmiana kolejności paskami w formancie, kliknij i przeciągnij pasek uchwytu poza pasmem.  
  
 Na poniższej ilustracji przedstawiono formantu paska pomocniczego, który ma trzy grupy:  
  
-   Poza pasmem 0 zawiera formantu toolbar płaskiej, przezroczysty.  
  
-   Poza pasmem 1 zawiera przyciski przezroczysty standardowe i przejrzysty listy rozwijanej.  
  
-   Poza pasmem 2 zawiera pole kombi i cztery przyciski standardowe.  
  
     ![Przykład menu paska pomocniczego](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Paska pomocniczego kontrolki  
 Paska pomocniczego kontrolki pomocy technicznej:  
  
-   Listy obrazów.  
  
-   Obsługi wiadomości.  
  
-   Niestandardowy rysunek funkcji.  
  
-   Różnych stylów formantu oprócz standardowego okna Style. Aby uzyskać listę tych stylów, zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [crebarctrl przy użyciu —](../../mfc/using-crebarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag  
 Implementuje zachowanie komunikatu Win32 [RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem, które wpływają na operację przeciągania i upuszczania.  
  
 `dwPos`  
 A `DWORD` wartość, która zawiera początkowy współrzędne myszy. Współrzędna pozioma jest zawarta w LOWORD i pionowy współrzędnych znajduje się w HIWORD. W przypadku przekazania `(DWORD)-1`, formantu paska pomocniczego użyje położenie myszy ostatniego wątku formantu o nazwie **GetMessage** lub **PeekMessage**.  
  
##  <a name="create"></a>  CReBarCtrl::Create  
 Tworzy kontrolkę paska pomocniczego i dołącza go do `CReBarCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa kombinację stylów formantu paska pomocniczego stosowane do formantu. Zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w zestawie SDK systemu Windows, aby uzyskać listę obsługiwanych style.  
  
 `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar formantu paska pomocniczego.  
  
 `pParentWnd`  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki paska pomocniczego. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu paska pomocniczego kontrolki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Tworzenie formantu paska pomocniczego w dwóch krokach:  
  
1.  Wywołanie [crebarctrl —](#crebarctrl) do skonstruowania `CReBarCtrl` obiektu.  
  
2.  Wywołanie funkcji członkowskiej, która tworzy kontrolkę paska pomocniczego systemu Windows i dołącza go do `CReBarCtrl` obiektu.  
  
 Podczas wywoływania **Utwórz**, są inicjowane wspólne kontrolki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CReBarCtrl::CreateEx  
 Tworzy kontrolkę (okno podrzędne) i kojarzy ją z `CReBarCtrl` obiektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Określa styl rozszerzony formantu tworzona. Aby uzyskać listę rozszerzone style systemu Windows, zobacz `dwExStyle` parametr [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) w zestawie Windows SDK.  
  
 `dwStyle`  
 Określa kombinację stylów formantu paska pomocniczego stosowane do formantu. Aby uzyskać listę obsługiwanych style, zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w zestawie Windows SDK.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujące rozmiar i położenie okna, które ma zostać utworzony w współrzędne klienta `pParentWnd`.  
  
 `pParentWnd`  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 `nID`  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) dotyczyć rozszerzone style systemu Windows, określone przez wstępu rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl  
 Tworzy `CReBarCtrl` obiektu.  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CReBarCtrl::Create](#create).  
  
##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand  
 Implementuje zachowanie komunikatu Win32 [RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli paśmie usunięte; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>  CReBarCtrl::DragMove  
 Implementuje zachowanie komunikatu Win32 [RB_DRAGMOVE](https://msdn.microsoft.com/library/bb774433.aspx), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 A `DWORD` wartości, która zawiera nowe współrzędne myszy. Współrzędna pozioma jest zawarta w LOWORD i pionowy współrzędnych znajduje się w HIWORD. W przypadku przekazania `(DWORD)-1`, formantu paska pomocniczego użyje położenie myszy ostatniego wątku formantu o nazwie **GetMessage** lub **PeekMessage**.  
  
##  <a name="enddrag"></a>  CReBarCtrl::EndDrag  
 Implementuje zachowanie komunikatu Win32 [RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders  
 Implementuje zachowanie komunikatu Win32 [RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem, dla którego mają zostać pobrane obramowania.  
  
 `prc`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który otrzyma obramowania poza pasmem. Jeśli z formantem paska pomocniczego **RBS_BANDBORDERS** stylu, każdy członek tej struktury otrzymają liczba pikseli na stronie odpowiedniej grupy, wchodzących w skład obramowania. Jeśli nie ma formantu paska pomocniczego **RBS_BANDBORDERS** styl, tylko po lewej stronie członkiem tej struktury otrzymuje nieprawidłowe informacje. Aby uzyskać opis stylów formantu paska pomocniczego, zobacz [stylów formantu paska pomocniczego](http://msdn.microsoft.com/library/windows/desktop/bb774377) w zestawie Windows SDK.  
  
##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount  
 Implementuje zachowanie komunikatu Win32 [RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba przedziałów przypisany do kontrolki.  
  
##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo  
 Implementuje zachowanie komunikatu Win32 [RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451) zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem, dla którego będą pobierane informacje.  
  
 `prbbi`  
 Wskaźnik do [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktury otrzymywanie informacji poza pasmem. Należy ustawić `cbSize` członkiem tej struktury `sizeof(REBARBANDINFO)` i ustaw **fMask** elementu członkowskiego do elementów do pobrania przed wysłaniem tej wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins  
 Pobiera marginesy grupy.  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>Parametry  
 *pMargins*  
 Wskaźnik do [MARGINESY](http://msdn.microsoft.com/library/windows/desktop/bb773244)strukturę, która będzie odbierać dane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight  
 Pobiera wysokość paska paska pomocniczego.  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która reprezentuje wysokość w pikselach formantu.  
  
##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo  
 Implementuje zachowanie komunikatu Win32 [RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `prbi`  
 Wskaźnik do [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) struktury, która odbierze informacji formantu paska pomocniczego. Należy ustawić `cbSize` członkiem tej struktury `sizeof(REBARINFO)` przed wysłaniem tej wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor  
 Implementuje zachowanie komunikatu Win32 [RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **COLORREF** wartość, która reprezentuje bieżący domyślny kolor tła.  
  
##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme  
 Pobiera [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury formantu paska pomocniczego.  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Wskaźnik do [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 **COLORSCHEME** struktura zawiera przycisk koloru wyróżnienia i kolor cienia przycisku.  
  
##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget  
 Implementuje zachowanie komunikatu Win32 [RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463), zgodnie z opisem w zestawie Windows SDK.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfejsu.  
  
##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle  
 Pobiera rozszerzone style bieżącego formantu paska pomocniczego.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowe połączenie (lub) flag, które wskazują rozszerzone style. Możliwe flagi są `RBS_EX_SPLITTER` i `RBS_EX_TRANSPARENT`. Aby uzyskać więcej informacji, zobacz `dwMask` parametr [CReBarCtrl::SetExtendedStyle](#setextendedstyle) metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList  
 Pobiera `CImageList` obiekt skojarzony z formantem paska pomocniczego.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu. Zwraca **NULL** Jeśli nie listy obrazów formantu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska używa rozmiaru i maska informacji przechowywanych w [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getpalette"></a>  CReBarCtrl::GetPalette  
 Pobiera bieżący palety formantu paska pomocniczego.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [cpalette —](../../mfc/reference/cpalette-class.md) Określanie formantu paska pomocniczego palety bieżącego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że korzysta z funkcji członkowskiej `CPalette` obiektu jako jego wartość zwracaną, zamiast `HPALETTE`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>  CReBarCtrl::GetRect  
 Implementuje zachowanie komunikatu Win32 [RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem w formancie paska pomocniczego.  
  
 `prc`  
 Wskaźnik do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który otrzyma granice pasmem paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount  
 Implementuje zachowanie komunikatu Win32 [RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **UINT** wartość reprezentującą liczbę wierszy poza pasmem w formancie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight  
 Implementuje zachowanie komunikatu Win32 [RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uRow*  
 Liczony od zera indeks grupy mające pobrać wysokość.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **UINT** wartość, która reprezentuje wysokość wierszy w pikselach.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor  
 Implementuje zachowanie komunikatu Win32 [RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A **COLORREF** wartość, która reprezentuje bieżący domyślny kolor tekstu.  
  
##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips  
 Implementuje zachowanie komunikatu Win32 [RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że implementacja MFC `GetToolTips` zwraca wskaźnik do `CToolTipCtrl`, zamiast `HWND`.  
  
##  <a name="hittest"></a>  CReBarCtrl::HitTest  
 Implementuje zachowanie komunikatu Win32 [RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494), zgodnie z opisem w zestawie Windows SDK.  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>Parametry  
 *prbht*  
 Wskaźnik do [RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391) struktury. Przed wysłaniem wiadomości, **pt** członkiem tej struktury musi zostać zainicjowany do punktu, która zostanie przetestowana we współrzędnych klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks poza pasmem w danego punktu, lub wartość -1, jeśli nie pasmem paska pomocniczego nie w punkcie.  
  
##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex  
 Implementuje zachowanie komunikatu Win32 [RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496), zgodnie z opisem w zestawie Windows SDK.  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBandID*  
 Przekazano identyfikator zdefiniowanym przez aplikację określonej grupy **wID** członkiem [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktury po wstawieniu grupy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pasmem liczony od zera indeks w przypadku powodzenia lub -1, w przeciwnym razie. Jeśli istnieją zduplikowane pasmem indeksów, zwracana jest pierwsza z nich.  
  
##  <a name="insertband"></a>  CReBarCtrl::InsertBand  
 Implementuje zachowanie komunikatu Win32 [RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 *uIndex*  
 Liczony od zera indeks lokalizacji, w którym zostanie wstawiony grupy. Jeśli ten parametr jest ustawiony na wartość -1, formantu doda nową grupę w ostatnim miejscu.  
  
 `prbbi`  
 Wskaźnik do [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) strukturę, która definiuje poza pasmem do wstawienia. Należy ustawić `cbSize` członkiem tej struktury `sizeof(REBARBANDINFO)` przed wywołaniem tej funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand  
 Zmienia rozmiar poza pasmem w formancie paska pomocniczego największy rozmiar.  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks grupy, aby być zmaksymalizowane.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatu Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) z `fIdeal` ustawiony na 0, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand  
 Zmienia rozmiar poza pasmem w formancie paska pomocniczego do najmniejszy.  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks pasmem minimalizowanie.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatu Win32 [RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>  CReBarCtrl::MoveBand  
 Implementuje zachowanie komunikatu Win32 [RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>Parametry  
 *uFrom*  
 Liczony od zera indeks poza pasmem do przeniesienia.  
  
 *matyczna*  
 Liczony od zera indeks nowego położenia poza pasmem. Wartość tego parametru nigdy nie może być większa niż liczba przedziałów minus jeden. Aby uzyskać liczbę grup, należy wywołać [GetBandCount](#getbandcount).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron  
 Implementuje zachowanie komunikatu Win32 [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem, których cudzysłów ostrokątny ma zostać przeniesiony.  
  
 `lAppValue`  
 32-bitową wartość zdefiniowanym przez aplikację. Zobacz `lAppValue` w [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506) w systemie Windows SDK.  
  
##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand  
 Zmienia rozmiar poza pasmem w formancie paska pomocniczego do jego rozmiar idealny.  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks grupy, aby być zmaksymalizowane.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatu Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) z `fIdeal` ustawioną wartość 1, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo  
 Implementuje zachowanie komunikatu Win32 [RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks grupy, aby zastosować nowe ustawienia.  
  
 `prbbi`  
 Wskaźnik do [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) strukturę, która definiuje poza pasmem do wstawienia. Należy ustawić `cbSize` członkiem tej struktury `sizeof(REBARBANDINFO)` przed wysłaniem tej wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth  
 Ustawia szerokość przedziałów zadokowanych w bieżącym formantu paska pomocniczego.  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `uBand`|Liczony od zera indeks pasmem paska pomocniczego.|  
|[in] `cxWidth`|Nową szerokość paska pomocniczego poza pasmem, a w pikselach.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_rebar`, która jest używane do dostępu bieżącego formantu paska pomocniczego. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia każdego pasma paska pomocniczego, aby mieć szerokość.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo  
 Implementuje zachowanie komunikatu Win32 [RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>Parametry  
 `prbi`  
 Wskaźnik do [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) strukturę, która zawiera informacje, które ma zostać ustawiona. Należy ustawić `cbSize` członkiem tej struktury `sizeof(REBARINFO)` przed wysłaniem tego komunikatu  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor  
 Implementuje zachowanie komunikatu Win32 [RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 **COLORREF** wartość, która reprezentuje nowy domyślny kolor tła.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość, która reprezentuje poprzedniej domyślny kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz ten temat, aby uzyskać więcej informacji na temat ustawić kolor tła ustawić wartość domyślna.  
  
##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme  
 Ustawia schemat kolorów przycisków w formancie paska pomocniczego.  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Wskaźnik do [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 **COLORSCHEME** struktura zawiera przycisk koloru wyróżnienia i kolor cienia przycisku.  
  
##  <a name="setextendedstyle"></a>  CReBarCtrl::SetExtendedStyle  
 Ustawia rozszerzone style dla bieżącego formantu paska pomocniczego.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in] `dwMask`|Bitowe połączenie (lub) flagi określające flag, które w `dwStyleEx` parametr dotyczy. Należy użyć co najmniej jeden z następujących wartości:<br /><br /> RBS_EX_SPLITTER: Domyślnie zawierają rozdzielacza u dołu w poziomym trybie i w prawo w pionowym trybie.<br /><br /> RBS_EX_TRANSPARENT: Przekazuj [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) wiadomości do okna nadrzędnego.|  
|[in] `dwStyleEx`|Bitowe połączenie (lub) flagi określające, style, które mają zastosowanie. Aby ustawić stylu, należy określić tę samą flagę, która jest używana w `dwMask` parametru. Aby zresetować stylu, określ binarne zero.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni rozszerzone style.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList  
 Przypisuje listy obrazów z formantem paska pomocniczego.  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt, który zawiera listy obrazów, który ma zostać przypisany do formantu paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
##  <a name="setowner"></a>  CReBarCtrl::SetOwner  
 Implementuje zachowanie komunikatu Win32 [RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do `CWnd` obiektu można ustawić jako właściciel formantu paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest bieżącym właścicielem formantu paska pomocniczego.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że ta funkcja członkowska używa wskaźników do `CWnd` obiekty dla bieżącego i wybranych właściciela formantu paska pomocniczego, a nie obsługuje do systemu windows.  
  
> [!NOTE]
>  Ta funkcja członkowska nie zmienia rzeczywiste nadrzędnej, czy została ustawiona, gdy formant został utworzony; zamiast wysyła komunikaty powiadomień do okna, które określisz.  
  
##  <a name="setpalette"></a>  CReBarCtrl::SetPalette  
 Implementuje zachowanie komunikatu Win32 [RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>Parametry  
 *hPal*  
 `HPALETTE` , Który określa paletę nowe, która będzie używać formantu paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [cpalette —](../../mfc/reference/cpalette-class.md) obiekt określający palety poprzedniego formantu paska pomocniczego.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że korzysta z funkcji członkowskiej `CPalette` obiektu jako jego wartość zwracaną, zamiast `HPALETTE`.  
  
##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor  
 Implementuje zachowanie komunikatu Win32 [RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 A **COLORREF** kolor wartość, która reprezentuje nowy tekst `CReBarCtrl` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) wartość reprezentującą poprzedniej kolor tekstu skojarzony z `CReBarCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Znajduje się on do obsługi elastyczność kolor tekstu w formancie paska pomocniczego.  
  
##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips  
 Kojarzy formantem etykietki narzędzia z formantem paska pomocniczego.  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 *pToolTip*  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiektu  
  
### <a name="remarks"></a>Uwagi  
 Należy zniszczyć `CToolTipCtrl` obiektu, gdy wszystko będzie gotowe z nim.  
  
##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme  
 Ustawia styl wizualny formantu paska pomocniczego.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 `pszSubAppName`  
 Wskaźnik do ciąg Unicode, który zawiera styl wizualny paska pomocniczego do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość zwrotna nie jest używany.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcje [RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530) komunikatu, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="showband"></a>  CReBarCtrl::ShowBand  
 Implementuje zachowanie komunikatu Win32 [RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Liczony od zera indeks poza pasmem w formancie paska pomocniczego.  
  
 *fShow*  
 Wskazuje, czy pokazywane lub ukryte grupy. Jeśli ta wartość jest **TRUE**, zostaną wyświetlone grupy. W przeciwnym razie wartość grupy zostanie ukryta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect  
 Implementuje zachowanie komunikatu Win32 [RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który określa prostokąt formantu paska pomocniczego powinny być ustalone na.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że korzysta z funkcji członkowskiej `CRect` obiektu jako parametru, a nie `RECT` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)


