---
title: Klasa CReBarCtrl | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0b88e53d7f5cfdd03728f8d1a474ee5171ca5daa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717590"
---
# <a name="crebarctrl-class"></a>Klasa CReBarCtrl
Hermetyzuje funkcje sterowania formantu rebar, który jest kontenerem dla okna podrzędnego.  
  
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
|[CReBarCtrl::BeginDrag](#begindrag)|Umieszcza formantu paska pomocniczego w trybie przeciągnij i upuść.|  
|[CReBarCtrl::Create](#create)|Tworzy kontrolkę paska pomocniczego i dołącza je do `CReBarCtrl` obiektu.|  
|[CReBarCtrl::CreateEx](#createex)|Tworzy kontrolkę paska pomocniczego przy użyciu określonego stylów rozszerzonej Windows i dołącza je do `CReBarCtrl` obiektu.|  
|[CReBarCtrl::DeleteBand](#deleteband)|Usuwa obiekt band z formantem paska pomocniczego.|  
|[CReBarCtrl::DragMove](#dragmove)|Aktualizuje pozycji przeciągnij w formancie paska pomocniczego po wywołaniu `BeginDrag`.|  
|[CReBarCtrl::EndDrag](#enddrag)|Kończy operację przeciągania i upuszczania kontrolki paska pomocniczego.|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|Pobiera obramowania grupy.|  
|[CReBarCtrl::GetBandCount](#getbandcount)|Pobiera liczbę paskami aktualnie w formancie paska pomocniczego.|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Pobiera informacje o określonym poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Pobiera marginesy poza pasmem.|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|Pobiera wysokość formantu paska pomocniczego.|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Pobiera informacje o formancie paska pomocniczego i listy obrazów, które są używane.|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|Pobiera formantu paska pomocniczego domyślny kolor tła.|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Pobiera [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktury skojarzonego z kontrolką paska pomocniczego.|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Pobiera z formantem paska pomocniczego `IDropTarget` wskaźnika interfejsu.|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Pobiera styl rozszerzony bieżącego formantu paska pomocniczego.|  
|[CReBarCtrl::GetImageList](#getimagelist)|Pobiera listę obrazu skojarzonego z kontrolką paska pomocniczego.|  
|[CReBarCtrl::GetPalette](#getpalette)|Pobiera bieżącej palecie kontrolki paska pomocniczego.|  
|[CReBarCtrl::GetRect](#getrect)|Pobiera prostokąt otaczający dla danego urządzenia band w formancie paska pomocniczego.|  
|[CReBarCtrl::GetRowCount](#getrowcount)|Pobiera liczbę wierszy poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|Pobiera wysokość określony wiersz w kontrolce paska pomocniczego.|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|Pobiera formantu paska pomocniczego domyślny kolor tekstu.|  
|[CReBarCtrl::GetToolTips](#gettooltips)|Pobranie dojścia do dowolnego z formantem etykietki narzędzia skojarzonego z kontrolką paska pomocniczego.|  
|[CReBarCtrl::HitTest](#hittest)|Określa, która część pasma paska pomocniczego jest w danym momencie na ekranie, jeśli obiekt band paska pomocniczego istnieje w tym momencie.|  
|[CReBarCtrl::IDToIndex](#idtoindex)|Konwertuje poza pasmem identyfikator (ID) na indeks poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::InsertBand](#insertband)|Wstawia nową grupę w formancie paska pomocniczego.|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|Zmienia rozmiar przedziału w formancie paska pomocniczego do największego rozmiaru.|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|Zmienia rozmiar pasma w formancie paska pomocniczego do najmniejszego rozmiaru.|  
|[CReBarCtrl::MoveBand](#moveband)|Przenosi obiekt band z jednego indeksu.|  
|[CReBarCtrl::PushChevron](#pushchevron)|Programowe wypycha strzałki.|  
|[CReBarCtrl::RestoreBand](#restoreband)|Zmienia rozmiar pasma w formancie paska pomocniczego, jego rozmiar idealny.|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Ustawia właściwości istniejącego poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Ustawia szerokość określoną zadokowany poza pasmem w bieżącego formantu paska pomocniczego.|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Ustawia właściwości formantu paska pomocniczego.|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|Ustawia formantu paska pomocniczego domyślny kolor tła.|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Ustawia schemat kolorów dla przycisków w formancie paska pomocniczego.|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Ustawia rozszerzone style dla bieżącego formantu paska pomocniczego.|  
|[CReBarCtrl::SetImageList](#setimagelist)|Ustawia listy obrazów z formantem paska pomocniczego.|  
|[CReBarCtrl::SetOwner](#setowner)|Ustawia okno właściciela z formantem paska pomocniczego.|  
|[CReBarCtrl::SetPalette](#setpalette)|Ustawia bieżącej palecie kontrolki paska pomocniczego.|  
|[CReBarCtrl::SetTextColor](#settextcolor)|Ustawia formantu paska pomocniczego domyślny kolor tekstu.|  
|[CReBarCtrl::SetToolTips](#settooltips)|Tworzy skojarzenia między formantem etykietki narzędzia, za pomocą kontrolki paska pomocniczego.|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Ustawia styl wizualny formantu paska pomocniczego.|  
|[CReBarCtrl::ShowBand](#showband)|Pokazuje lub ukrywa danego poza pasmem w formancie paska pomocniczego.|  
|[CReBarCtrl::SizeToRect](#sizetorect)|Pasuje do formantu paska pomocniczego do określonego prostokąta.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja, w której znajduje się w formancie paska pomocniczego przypisuje okna podrzędnego zawarty w formancie paska pomocniczego do grupy paska pomocniczego. Okno podrzędne jest zazwyczaj inny wspólnej kontroli.  
  
 Formanty paska pomocniczego zawiera jeden lub więcej grup. Każdego pasma może zawierać kombinację pasek uchwytu, mapy bitowej, etykietę tekstową i okna podrzędnego. Pasmo może zawierać tylko jeden z tych elementów.  
  
 Kontrolki paska pomocniczego, można wyświetlić okno podrzędne za pośrednictwem określonego tła mapy bitowej. Wszystkie kontrolki paskami pomocniczymi rozmiar można zmieniać, z wyjątkiem tych, które używają stylu RBBS_FIXEDSIZE. Zmienianie położenia lub zmieniania rozmiaru grupy kontrolki paska pomocniczego, formantu paska pomocniczego zarządza, rozmiar i położenie okna podrzędnego, przypisany do tej grupy. Aby zmienić rozmiar lub zmiana kolejności paskami w kontrolce, kliknij i przeciągnij pasek uchwytu poza pasmem.  
  
 Poniższa ilustracja przedstawia kontrolkę paska pomocniczego, zawierającej trzy przedziały:  
  
-   Poza pasmem 0 zawiera formant narzędzi stałą, przejrzysty.  
  
-   Poza pasmem 1 zawiera przyciski przezroczyste listy rozwijanej standardowe i przejrzystości.  
  
-   Poza pasmem 2 zawiera pola kombi i cztery przyciski standardowe.  
  
     ![Przykład menu paska pomocniczego](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Paska pomocniczego kontrolki  
 Paska pomocniczego kontrolki pomocy technicznej:  
  
-   Listy obrazów.  
  
-   Obsługa komunikatów.  
  
-   Funkcja niestandardowego rysowania.  
  
-   Różne style kontrolki oprócz standardowego okna Style. Aby uzyskać listę tych stylów, zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [korzystanie z CReBarCtrl](../../mfc/using-crebarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcmn.h  
  
##  <a name="begindrag"></a>  CReBarCtrl::BeginDrag  
 Implementuje zachowanie komunikatów Win32 [RB_BEGINDRAG](/windows/desktop/Controls/rb-begindrag), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, którego będzie dotyczyć operacji przeciągania i upuszczania.  
  
 *dwPos*  
 Wartość DWORD, zawierającą początkowy myszy współrzędnych. Pozioma współrzędne znajduje się w LOWORD i pionowy współrzędnych znajduje się w HIWORD. Jeśli przekażesz (DWORD) -1, formantu paska pomocniczego użyje położenie myszy ostatniego wątku formantu o nazwie `GetMessage` lub `PeekMessage`.  
  
##  <a name="create"></a>  CReBarCtrl::Create  
 Tworzy kontrolkę paska pomocniczego i dołącza je do `CReBarCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Określa kombinację style kontrolki paska pomocniczego stosowane do formantu. Zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w zestawie SDK Windows, aby uzyskać listę obsługiwanych style.  
  
 *Rect*  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiektu lub [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar formantu paska pomocniczego.  
  
 *pParentWnd*  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne kontrolki paska pomocniczego. Nie może być równa NULL.  
  
 *nID*  
 Określa identyfikator kontrolki paska pomocniczego kontrolki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli obiekt został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Tworzenie formantu paska pomocniczego w dwóch etapach:  
  
1.  Wywołaj [z CReBarCtrl](#crebarctrl) do konstruowania `CReBarCtrl` obiektu.  
  
2.  Wywołanie tej funkcji elementu członkowskiego, która tworzy kontrolkę paska pomocniczego Windows i dołącza go do `CReBarCtrl` obiektu.  
  
 Gdy wywołujesz `Create`, typowe formanty są inicjowane.  
  
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
 *dwExStyle*  
 Określa styl rozszerzony kontrolki tworzona. Aby uzyskać listę rozszerzone style Windows, zobacz *dwExStyle* parametr [elementu CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) w zestawie Windows SDK.  
  
 *dwStyle*  
 Określa kombinację style kontrolki paska pomocniczego stosowane do formantu. Aby uzyskać listę obsługiwanych style, zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w zestawie Windows SDK.  
  
 *Rect*  
 Odwołanie do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury opisujących rozmiar i położenie okna, można utworzyć klienta współrzędne *pParentWnd*.  
  
 *pParentWnd*  
 Wskaźnik do okna, które jest elementem nadrzędnym formantu.  
  
 *nID*  
 Identyfikator formantu okna podrzędnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Użyj `CreateEx` zamiast [Utwórz](#create) do zastosowania rozszerzone style Windows, określonego przez tekst wstępny rozszerzonego stylu Windows **WS_EX_**.  
  
##  <a name="crebarctrl"></a>  CReBarCtrl::CReBarCtrl  
 Tworzy `CReBarCtrl` obiektu.  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CReBarCtrl::Create](#create).  
  
##  <a name="deleteband"></a>  CReBarCtrl::DeleteBand  
 Implementuje zachowanie komunikatów Win32 [RB_DELETEBAND](/windows/desktop/Controls/rb-deleteband), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem do usunięcia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli urządzenia band pomyślnie usunięte, w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>  CReBarCtrl::DragMove  
 Implementuje zachowanie komunikatów Win32 [RB_DRAGMOVE](/windows/desktop/Controls/rb-dragmove), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 *dwPos*  
 Wartość DWORD, który zawiera nowe współrzędne myszy. Pozioma współrzędne znajduje się w LOWORD i pionowy współrzędnych znajduje się w HIWORD. Jeśli przekażesz (DWORD) -1, formantu paska pomocniczego użyje położenie myszy ostatniego wątku formantu o nazwie `GetMessage` lub `PeekMessage`.  
  
##  <a name="enddrag"></a>  CReBarCtrl::EndDrag  
 Implementuje zachowanie komunikatów Win32 [RB_ENDDRAG](/windows/desktop/Controls/rb-enddrag), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>  CReBarCtrl::GetBandBorders  
 Implementuje zachowanie komunikatów Win32 [RB_GETBANDBORDERS](/windows/desktop/Controls/rb-getbandborders), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks pasmo, dla którego będą pobierane obramowania.  
  
 *Chińska Republika Ludowa*  
 Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który będzie otrzymywał obramowania poza pasmem. Jeśli do formantu paska pomocniczego jest styl RBS_BANDBORDERS, każdy członek tej struktury otrzyma liczbę pikseli odpowiedniego stronie poza pasmem, wchodzących w skład obramowania. Jeśli formantu paska pomocniczego nie ma stylu RBS_BANDBORDERS, po lewej stronie członkiem tej struktury odbiera prawidłowe informacje. Aby uzyskać opis style kontrolki paska pomocniczego, zobacz [style kontrolki paska pomocniczego](/windows/desktop/Controls/rebar-control-styles) w zestawie Windows SDK.  
  
##  <a name="getbandcount"></a>  CReBarCtrl::GetBandCount  
 Implementuje zachowanie komunikatów Win32 [RB_GETBANDCOUNT](/windows/desktop/Controls/rb-getbandcount), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba grup przypisany do kontrolki.  
  
##  <a name="getbandinfo"></a>  CReBarCtrl::GetBandInfo  
 Implementuje zachowanie komunikatów Win32 [RB_GETBANDINFO](/windows/desktop/Controls/rb-getbandinfo) zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks pasmo, dla którego będą pobierane informacje.  
  
 *prbbi*  
 Wskaźnik do [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktury do odbierania informacji poza pasmem. Należy ustawić `cbSize` członkiem tej struktury, aby `sizeof(REBARBANDINFO)` i ustaw `fMask` elementu członkowskiego do elementów do pobrania przed wysłaniem tego komunikatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
##  <a name="getbandmargins"></a>  CReBarCtrl::GetBandMargins  
 Pobiera marginesy pasmo.  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>Parametry  
 *pMargins*  
 Wskaźnik do [MARGINESY](/windows/desktop/api/uxtheme/ns-uxtheme-_margins)struktury, który będzie otrzymywać informacje.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność [RB_GETBANDMARGINS](/windows/desktop/Controls/rb-getbandmargins) komunikat, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getbarheight"></a>  CReBarCtrl::GetBarHeight  
 Pobiera wysokość paska paska pomocniczego.  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość reprezentująca wysokość w pikselach formantu.  
  
##  <a name="getbarinfo"></a>  CReBarCtrl::GetBarInfo  
 Implementuje zachowanie komunikatów Win32 [RB_GETBARINFO](/windows/desktop/Controls/rb-getbarinfo), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *prbi*  
 Wskaźnik do [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) struktury, który będzie otrzymywać informacje kontrolki paska pomocniczego. Należy ustawić *elementu cbSize* członkiem tej struktury, aby `sizeof(REBARINFO)` przed wysłaniem tego komunikatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
##  <a name="getbkcolor"></a>  CReBarCtrl::GetBkColor  
 Implementuje zachowanie komunikatów Win32 [RB_GETBKCOLOR](/windows/desktop/Controls/rb-getbkcolor), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość COLORREF, która reprezentuje bieżący domyślny kolor tła.  
  
##  <a name="getcolorscheme"></a>  CReBarCtrl::GetColorScheme  
 Pobiera [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) strukturę dla formantu paska pomocniczego.  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 *LPC*  
 Wskaźnik do [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 `COLORSCHEME` Struktura zawiera kolor wyróżnienia przycisku i kolor cienia przycisku.  
  
##  <a name="getdroptarget"></a>  CReBarCtrl::GetDropTarget  
 Implementuje zachowanie komunikatów Win32 [RB_GETDROPTARGET](/windows/desktop/Controls/rb-getdroptarget), zgodnie z opisem w zestawie Windows SDK.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget) interfejsu.  
  
##  <a name="getextendedstyle"></a>  CReBarCtrl::GetExtendedStyle  
 Pobiera rozszerzone style bieżącego formantu paska pomocniczego.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bitowa kombinacja (lub) flagi wskazujące rozszerzone style. Możliwe flagi są RBS_EX_SPLITTER i RBS_EX_TRANSPARENT. Aby uzyskać więcej informacji, zobacz *dwMask* parametru [CReBarCtrl::SetExtendedStyle](#setextendedstyle) metody.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_GETEXTENDEDSTYLE](/windows/desktop/Controls/rb-dragmove) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="getimagelist"></a>  CReBarCtrl::GetImageList  
 Pobiera `CImageList` obiekt skojarzony z formantem paska pomocniczego.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiektu. Zwraca wartość NULL, jeśli nie listy obrazów kontrolki.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska używa rozmiaru i maska informacji przechowywanych w [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="getpalette"></a>  CReBarCtrl::GetPalette  
 Pobiera bieżącej palecie kontrolki paska pomocniczego.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CPalette](../../mfc/reference/cpalette-class.md) obiektu określenie bieżącej palecie kontrolki paska pomocniczego.  
  
### <a name="remarks"></a>Uwagi  
 Należy zauważyć, że ta funkcja członkowska używa `CPalette` obiektu jako jego wartość zwracana zamiast HPALETTE.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>  CReBarCtrl::GetRect  
 Implementuje zachowanie komunikatów Win32 [RB_GETRECT](/windows/desktop/Controls/rb-getrect), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem w formancie paska pomocniczego.  
  
 *Chińska Republika Ludowa*  
 Wskaźnik do [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, który będzie otrzymywał granice poza pasmem paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>  CReBarCtrl::GetRowCount  
 Implementuje zachowanie komunikatów Win32 [RB_GETROWCOUNT](/windows/desktop/Controls/rb-getrowcount), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartości UINT, który reprezentuje liczbę wierszy poza pasmem w formancie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>  CReBarCtrl::GetRowHeight  
 Implementuje zachowanie komunikatów Win32 [RB_GETROWHEIGHT](/windows/desktop/Controls/rb-getrowheight), zgodnie z opisem w zestawie Windows SDK.  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uRow*  
 Liczony od zera indeks zespół, który będzie miał wysokość pobierane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość UINT, która przedstawia wysokość wiersza, w pikselach.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>  CReBarCtrl::GetTextColor  
 Implementuje zachowanie komunikatów Win32 [RB_GETTEXTCOLOR](/windows/desktop/Controls/rb-gettextcolor), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość COLORREF, która reprezentuje bieżący domyślny kolor tekstu.  
  
##  <a name="gettooltips"></a>  CReBarCtrl::GetToolTips  
 Implementuje zachowanie komunikatów Win32 [RB_GETTOOLTIPS](/windows/desktop/Controls/rb-gettooltips), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że implementacja MFC `GetToolTips` zwraca wskaźnik do `CToolTipCtrl`, a nie właściwością HWND.  
  
##  <a name="hittest"></a>  CReBarCtrl::HitTest  
 Implementuje zachowanie komunikatów Win32 [RB_HITTEST](/windows/desktop/Controls/rb-hittest), zgodnie z opisem w zestawie Windows SDK.  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>Parametry  
 *prbht*  
 Wskaźnik do [RBHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_rb_hittestinfo) struktury. Przed wysłaniem wiadomości, `pt` członkiem tej struktury, musi zostać zainicjowany do punktu, który będzie testowany w sposób współrzędne klienta.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks poza pasmem danego punktu lub -1, jeśli w momencie poza pasmem nie paska pomocniczego.  
  
##  <a name="idtoindex"></a>  CReBarCtrl::IDToIndex  
 Implementuje zachowanie komunikatów Win32 [RB_IDTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb774496), zgodnie z opisem w zestawie Windows SDK.  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBandID*  
 Przekazany identyfikator zdefiniowanych przez aplikację określoną pasmo `wID` członkiem [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) struktury, gdy znajduje się poza pasmem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks przedziału liczony od zera, jeśli kończy się pomyślnie lub -1, w przeciwnym razie. Jeśli istnieją zduplikowane poza pasmem indeksów, zwracany jest pierwszy z nich.  
  
##  <a name="insertband"></a>  CReBarCtrl::InsertBand  
 Implementuje zachowanie komunikatów Win32 [RB_INSERTBAND](/windows/desktop/Controls/rb-insertband), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 *uIndex*  
 Liczony od zera indeks lokalizacji, w którym zostanie wstawiony poza pasmem. Jeśli ten parametr jest ustawiony na wartość -1, formant doda nową grupę w ostatnich lokalizacji.  
  
 *prbbi*  
 Wskaźnik do [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) strukturę, która definiuje poza pasmem do wstawienia. Należy ustawić *elementu cbSize* członkiem tej struktury, aby `sizeof(REBARBANDINFO)` przed wywołaniem tej funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>  CReBarCtrl::MaximizeBand  
 Zmienia rozmiar przedziału w formancie paska pomocniczego do największego rozmiaru.  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, aby zmaksymalizować.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatów Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) z `fIdeal` ustawiona na 0, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>  CReBarCtrl::MinimizeBand  
 Zmienia rozmiar pasma w formancie paska pomocniczego do najmniejszego rozmiaru.  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, minimalizowanie.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatów Win32 [RB_MINIMIZEBAND](/windows/desktop/Controls/rb-minimizeband), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>  CReBarCtrl::MoveBand  
 Implementuje zachowanie komunikatów Win32 [RB_MOVEBAND](/windows/desktop/Controls/rb-moveband), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>Parametry  
 *uFrom*  
 Liczony od zera indeks poza pasmem do przeniesienia.  
  
 *utomatyczna zmiana*  
 Liczony od zera indeks w nowe miejsce poza pasmem. Wartości tego parametru nigdy nie może być większa niż liczba grup minus jeden. Aby uzyskać liczbę grup, należy wywołać [GetBandCount](#getbandcount).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
##  <a name="pushchevron"></a>  CReBarCtrl::PushChevron  
 Implementuje zachowanie komunikatów Win32 [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron), zgodnie z opisem w zestawie Windows SDK.  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, których cudzysłów ostrokątny jest ma zostać wypchnięty.  
  
 *lAppValue*  
 Zdefiniowana wartość 32-bitowych aplikacji. Zobacz *lAppValue* w [RB_PUSHCHEVRON](/windows/desktop/Controls/rb-pushchevron) w zestawie Windows SDK.  
  
##  <a name="restoreband"></a>  CReBarCtrl::RestoreBand  
 Zmienia rozmiar pasma w formancie paska pomocniczego, jego rozmiar idealny.  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, aby zmaksymalizować.  
  
### <a name="remarks"></a>Uwagi  
 Implementuje zachowanie komunikatów Win32 [RB_MAXIMIZEBAND](/windows/desktop/Controls/rb-maximizeband) z `fIdeal` ustawiona na 1, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>  CReBarCtrl::SetBandInfo  
 Implementuje zachowanie komunikatów Win32 [RB_SETBANDINFO](/windows/desktop/Controls/rb-setbandinfo), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem, aby zastosować nowe ustawienia.  
  
 *prbbi*  
 Wskaźnik do [REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa) strukturę, która definiuje poza pasmem do wstawienia. Należy ustawić `cbSize` członkiem tej struktury, aby `sizeof(REBARBANDINFO)` przed wysłaniem tego komunikatu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>  CReBarCtrl::SetBandWidth  
 Ustawia szerokość określoną zadokowany poza pasmem w bieżącego formantu paska pomocniczego.  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*uBand*|[in] Liczony od zera indeks pasma paska pomocniczego.|  
|*cxWidth*|[in] Nową szerokość paska pomocniczego poza pasmem, a w pikselach.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_SETBANDWIDTH](/windows/desktop/Controls/rb-setbandwidth) komunikat, który jest opisany w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 Poniższy kod definiuje zmienną, `m_rebar`, to znaczy umożliwiają dostęp do bieżącego formantu paska pomocniczego. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu ustawia każdego pasma paska pomocniczego, aby mieć taką samą szerokość.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>  CReBarCtrl::SetBarInfo  
 Implementuje zachowanie komunikatów Win32 [RB_SETBARINFO](/windows/desktop/Controls/rb-setbarinfo), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>Parametry  
 *prbi*  
 Wskaźnik do [REBARINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarinfo) strukturę, która zawiera informacje, należy ustawić. Należy ustawić `cbSize` członkiem tej struktury, aby `sizeof(REBARINFO)` przed wysłaniem tego komunikatu  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>  CReBarCtrl::SetBkColor  
 Implementuje zachowanie komunikatów Win32 [RB_SETBKCOLOR](/windows/desktop/Controls/rb-setbkcolor), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Wartość COLORREF, który reprezentuje nowy domyślny kolor tła.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [COLORREF](/windows/desktop/gdi/colorref) wartość, która reprezentuje poprzedniego domyślny kolor tła.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz ten temat, aby uzyskać więcej informacji na temat ustawić kolor tła ustawić wartości domyślne.  
  
##  <a name="setcolorscheme"></a>  CReBarCtrl::SetColorScheme  
 Ustawia schemat kolorów dla przycisków w formancie paska pomocniczego.  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 *LPC*  
 Wskaźnik do [COLORSCHEME](/windows/desktop/api/commctrl/ns-commctrl-tagcolorscheme) struktury, zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 `COLORSCHEME` Struktura zawiera kolor wyróżnienia przycisku i kolor cienia przycisku.  
  
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
|*dwMask*|[in] Bitowa kombinacja (lub) flagi określające flag, które w *dwStyleEx* zastosować parametr. Użyj co najmniej jeden z następujących wartości:<br /><br /> RBS_EX_SPLITTER: Domyślnie pokazuj rozdzielacza na dole w poziomym trybie, a po prawej stronie w pionowym trybie.<br /><br /> RBS_EX_TRANSPARENT: Przekazuj [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd) wiadomości do okna nadrzędnego.|  
|*dwStyleEx*|[in] Bitowa kombinacja (lub) flagi określające, style, które mają zastosowanie. Aby ustawić stylu, podaj tę samą flagę, która jest używana w *dwMask* parametru. Aby zresetować stylu, należy określić binarne zero.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzedni rozszerzone style.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [RB_SETEXTENDEDSTYLE](/windows/desktop/Controls/rb-setextendedstyle) komunikat, który jest opisany w zestawie Windows SDK.  
  
##  <a name="setimagelist"></a>  CReBarCtrl::SetImageList  
 Przypisuje listy obrazów z formantem paska pomocniczego.  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 *pImageList*  
 Wskaźnik do [CImageList](../../mfc/reference/cimagelist-class.md) obiekt, który zawiera listy obrazów do przypisania do formantu paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
##  <a name="setowner"></a>  CReBarCtrl::SetOwner  
 Implementuje zachowanie komunikatów Win32 [RB_SETPARENT](/windows/desktop/Controls/rb-setparent), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskaźnik do `CWnd` obiekt, aby ustawić jako właściciela formantu paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest bieżącym właścicielem formantu paska pomocniczego.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że ta funkcja członkowska używa wskaźników do `CWnd` obiekty dla bieżącego i wybranego właściciela formantu paska pomocniczego, a nie obsługuje systemu Windows.  
  
> [!NOTE]
>  Ta funkcja elementu członkowskiego nie powoduje zmiany rzeczywistego obiektu nadrzędnego, który został ustawiony podczas tworzenia kontrolki; zamiast wysyła powiadomienia do okna, które określisz.  
  
##  <a name="setpalette"></a>  CReBarCtrl::SetPalette  
 Implementuje zachowanie komunikatów Win32 [RB_SETPALETTE](/windows/desktop/Controls/rb-setpalette), zgodnie z opisem w zestawie Windows SDK.  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>Parametry  
 *hPal*  
 Hpalette — określający nowe palety, używanego przez formant paska pomocniczego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CPalette](../../mfc/reference/cpalette-class.md) określający palecie poprzedniej kontrolki paska pomocniczego.  
  
### <a name="remarks"></a>Uwagi  
 Należy zauważyć, że ta funkcja członkowska używa `CPalette` obiektu jako jego wartość zwracana zamiast HPALETTE.  
  
##  <a name="settextcolor"></a>  CReBarCtrl::SetTextColor  
 Implementuje zachowanie komunikatów Win32 [RB_SETTEXTCOLOR](/windows/desktop/Controls/rb-settextcolor), zgodnie z opisem w zestawie Windows SDK.  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Wartość COLORREF, który reprezentuje nowy tekst koloru `CReBarCtrl` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 [COLORREF](/windows/desktop/gdi/colorref) reprezentującą na poprzedni kolor tekstu skojarzony z `CReBarCtrl` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jest ona udostępniana do obsługi elastyczność kolor tekstu w formancie paska pomocniczego.  
  
##  <a name="settooltips"></a>  CReBarCtrl::SetToolTips  
 Tworzy skojarzenia między formantem etykietki narzędzia, z formantem paska pomocniczego.  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 *pToolTip*  
 Wskaźnik do [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) obiektu  
  
### <a name="remarks"></a>Uwagi  
 Użytkownik musi zniszczyć `CToolTipCtrl` obiektu, kiedy są z nią zrobić.  
  
##  <a name="setwindowtheme"></a>  CReBarCtrl::SetWindowTheme  
 Ustawia styl wizualny formantu paska pomocniczego.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 *pszSubAppName*  
 Wskaźnik do ciągu Unicode, który zawiera stylu wizualnego paska pomocniczego, aby ustawić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość nie jest używana.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska emuluje funkcjonalność [RB_SETWINDOWTHEME](/windows/desktop/Controls/rb-setwindowtheme) komunikat, zgodnie z opisem w zestawie Windows SDK.  
  
##  <a name="showband"></a>  CReBarCtrl::ShowBand  
 Implementuje zachowanie komunikatów Win32 [RB_SHOWBAND](/windows/desktop/Controls/rb-showband), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *uBand*  
 Liczony od zera indeks poza pasmem w formancie paska pomocniczego.  
  
 *fShow*  
 Wskazuje, jeśli pokazane lub ukryte pasmo. Jeśli ta wartość wynosi TRUE, będą wyświetlane pasmo. W przeciwnym razie pasmo zostanie ukryte.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
##  <a name="sizetorect"></a>  CReBarCtrl::SizeToRect  
 Implementuje zachowanie komunikatów Win32 [RB_SIZETORECT](/windows/desktop/Controls/rb-sizetorect), zgodnie z opisem w zestawie Windows SDK.  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 *Rect*  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt, który określa prostokąt, który formantu paska pomocniczego powinny być ustalone na poziomie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie wartość zero.  
  
### <a name="remarks"></a>Uwagi  
 Należy zauważyć, że ta funkcja członkowska używa `CRect` obiektu jako parametr, a nie `RECT` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)


