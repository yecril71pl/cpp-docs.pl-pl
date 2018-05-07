---
title: Klasa CSplitterWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 071eaeef6fbdbe4967d184936f5fb7bffb7786b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csplitterwnd-class"></a>Klasa CSplitterWnd
Udostępnia funkcję okna podziału okna, który zawiera wiele okienek.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Wywołanie do skonstruowania `CSplitterWnd` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|Wykonuje polecenie następne okienko lub poprzednie okienko.|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Sprawdza, czy polecenia następne okienko lub poprzednie okienko jest obecnie możliwe.|  
|[CSplitterWnd::Create](#create)|Wywołanie tworzenie dynamiczne okno podziału i dołączenie go do `CSplitterWnd` obiektu.|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Tworzy współdzieloną kontrolkę paska przewijania.|  
|[CSplitterWnd::CreateStatic](#createstatic)|Wywołanie tworzenia okna dzielącego statyczne i dołączenie go do `CSplitterWnd` obiektu.|  
|[CSplitterWnd::CreateView](#createview)|Wywołanie w celu utworzenia okienka w oknie podziału.|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Usuwa kolumnę z okna podziału.|  
|[CSplitterWnd::DeleteRow](#deleterow)|Usuwa wiersz z okna podziału.|  
|[CSplitterWnd::DeleteView](#deleteview)|Usuwa widok z okna podziału.|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Wykonuje polecenie podziału klawiatury, zwykle "podział okna".|  
|[CSplitterWnd::DoScroll](#doscroll)|Wykonuje synchroniczne przewijanie podzielonych okien.|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|Przewija podzielone okna przez daną liczbę pikseli.|  
|[CSplitterWnd::GetActivePane](#getactivepane)|Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Zwraca bieżącą liczbą kolumn w okienku.|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Zwraca informacje o określonej kolumny.|  
|[CSplitterWnd::GetPane](#getpane)|Zwraca okienko na określony wiersz i kolumnę.|  
|[CSplitterWnd::GetRowCount](#getrowcount)|Zwraca liczbę wierszy bieżącego okienka.|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Zwraca informacje na określony wiersz.|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Zwraca styl udostępnionych pasek przewijania.|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Zwraca element podrzędny identyfikator okna okienku na określony wiersz i kolumnę.|  
|[CSplitterWnd::IsChildPane](#ischildpane)|Wywołanie w celu ustalenia, czy okno jest obecnie okienko podrzędne tego okna podziału.|  
|[CSplitterWnd::IsTracking](#istracking)|Określa, czy pasek podziału obecnie jest przenoszony.|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|Wywołanie w celu ponownego wyświetlenia okna podziału po dopasowaniu rozmiar wierszy lub kolumn.|  
|[CSplitterWnd::SetActivePane](#setactivepane)|Ustawia okienko jako aktywne co w ramce.|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Wywołanie ustawiania informacji o określonej kolumny.|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Wywołanie ustawiania informacji określony wiersz.|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Określa, że obsługa paska przewijania udostępnionego w nowy styl pasek przewijania okna podziału.|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|Wskazuje gdzie okno ramowe dzieli się pionowo.|  
|[CSplitterWnd::SplitRow](#splitrow)|Wskazuje gdzie okno ramowe dzieli się poziomo.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|Wywoływane przez platformę, by narysować okna podziału.|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Renderuje Obraz okna podziału.|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Renderuje Obraz okna podziału być tym samym rozmiarze i kształcie co okno ramowe.|  
  
## <a name="remarks"></a>Uwagi  
 Okienko jest zwykle obiektu specyficzne dla aplikacji pochodzące z [CView](../../mfc/reference/cview-class.md), ale może być dowolną [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który ma identyfikator podrzędnych odpowiednie okna.  
  
 A `CSplitterWnd` obiekt zwykle jest osadzony w katalogu nadrzędnym [cframewnd —](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu. Utwórz `CSplitterWnd` obiekt, wykonując następujące czynności:  
  
1.  Osadź `CSplitterWnd` zmiennej członkowskiej w ramce nadrzędnej.  
  
2.  Zastąpienie ramka nadrzędny [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcję elementu członkowskiego.  
  
3.  Z wewnątrz przesłoniętej `OnCreateClient`, wywołaj [Utwórz](#create) lub [CreateStatic](#createstatic) funkcji członkowskiej klasy `CSplitterWnd`.  
  
 Wywołanie **Utwórz** funkcji członkowskiej, aby utworzyć dynamiczne okno podziału. Dynamiczne okno podziału jest zwykle używane do tworzenia i przewiń liczbę pojedynczych okienka lub widoki tego samego dokumentu. Platformę automatycznie tworzy początkowej okienko podziału; następnie platformę tworzy zmienia rozmiar i usuwa dodatkowe okienka jak użytkownik kontrolki okna podziału.  
  
 Podczas wywoływania **Utwórz**, określ wiersz minimalna wysokość i szerokość kolumny stwierdzić, gdy jest za mały do pełni można wyświetlić okienka. Po wywołaniu metody **Utwórz**, można dostosować te wymagania, wywołując [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) funkcji elementów członkowskich.  
  
 Również użyć `SetColumnInfo` i `SetRowInfo` funkcji elementów członkowskich, aby ustawić "idealne" szerokość kolumny i "idealne" wysokość wiersza. Gdy platformę Wyświetla okna podziału, najpierw Wyświetla ramki nadrzędnej, a następnie okna podziału. Następnie platformę układa okienkach kolumn i wierszy, zgodnie z ich idealne wymiarów, Praca z lewego górnego do prawego dolnego rogu obszaru klienckiego okna podziału.  
  
 Wszystkie okienka w oknie dynamiczny rozdzielacz musi być w tej samej klasy. Aplikacje obsługujące dynamiczne okna podziału obejmują Microsoft Word i Microsoft Excel.  
  
 Użyj `CreateStatic` funkcji członkowskiej można utworzyć okna statyczny rozdzielacz. Użytkownik może zmienić rozmiaru okienka w statyczny rozdzielacz okna, nie ich liczbą lub kolejności.  
  
 W szczególności należy utworzyć wszystkie statyczny rozdzielacz tego okienka po utworzeniu statyczny rozdzielacz. Upewnij się, że tworzenie wszystkich okienka przed ramka nadrzędny `OnCreateClient` zwraca funkcja elementu członkowskiego lub zostanie framework wyświetlane nieprawidłowo okna.  
  
 `CreateStatic` Funkcji członkowskiej automatycznie inicjuje statyczny rozdzielacz z minimalną wysokość wiersza i kolumny szerokość 0. Po wywołaniu metody **Utwórz**, Dostosuj te wymagania, wywołując [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) funkcji elementów członkowskich. Również użyć `SetColumnInfo` i `SetRowInfo` po wywołaniu metody `CreateStatic` wskazująca potrzeby wymiary idealne rozwiązanie w okienku.  
  
 Poszczególnych okienek statyczny rozdzielacz jest często należą do różnych klas. Przykłady statyczne okna podziału Zobacz Edytor grafiki i Menedżera plików systemu Windows.  
  
 Okna podziału obsługuje pasków przewijania specjalne (oprócz paski przewijania, które mogą mieć okienka). Elementy podrzędne są pasków przewijania `CSplitterWnd` obiektu i są współużytkowane z okienka.  
  
 Podczas tworzenia okna podziału tworzenia pasków przewijania specjalnych. Na przykład `CSplitterWnd` która ma jeden wiersz, dwóch kolumn i **ws_vscroll —** styl wyświetli pionowy pasek przewijania współużytkowane przez dwa okienka. Gdy użytkownik przesuwa na pasku przewijania `WM_VSCROLL` komunikaty są wysyłane do obu okienka. Okienka ustawianą pozycja paska przewijania na pasku przewijania udostępnionego jest ustawiona.  
  
 Aby uzyskać więcej informacji na okna podziału zobacz:  
  
- [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md)  
  
-   Artykuł bazy wiedzy Q262024: Porada: cpropertysheet — używany jako podrzędny CSplitterWnd  
  
 Aby uzyskać więcej informacji na temat tworzenia dynamiczne okna podziału zobacz:  
  
-   Przykładowe MFC [Bazgroły](../../visual-cpp-samples.md)  
  
-   Przykładowe MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext  
 Wywoływane przez platformę, by wykonuje polecenie następne okienko lub poprzednie okienko.  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bPrev`  
 Wskazuje, które okno, aby aktywować. **Wartość TRUE,** dla poprzedniego; **FALSE** następny.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest polecenie wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasę, aby przekazać `CSplitterWnd` implementacji.  
  
##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext  
 Wywoływane przez platformę, by sprawdzić, czy polecenia następne okienko lub poprzednie okienko jest obecnie możliwe.  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `bPrev`  
 Wskazuje, które okno, aby aktywować. **Wartość TRUE,** dla poprzedniego; **FALSE** następny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest polecenie wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasę, aby przekazać `CSplitterWnd` implementacji.  
  
##  <a name="create"></a>  CSplitterWnd::Create  
 Aby utworzyć dynamiczne okno podziału, należy wywołać **Utwórz** funkcję elementu członkowskiego.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    int nMaxRows,  
    int nMaxCols,  
    SIZE sizeMin,  
    CCreateContext* pContext,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Okno nadrzędne ramki okna podziału.  
  
 *nMaxRows*  
 Maksymalna liczba wierszy w oknie podziału. Ta wartość nie może przekraczać 2.  
  
 *nMaxCols*  
 Maksymalna liczba kolumn w okna podziału. Ta wartość nie może przekraczać 2.  
  
 `sizeMin`  
 Określa minimalny rozmiar okienka mogą być wyświetlane.  
  
 `pContext`  
 Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. W większości przypadków, może to być `pContext` przekazany do ramki okna nadrzędnego.  
  
 `dwStyle`  
 Określa styl okna.  
  
 `nID`  
 Identyfikator okna podrzędnego okna. Identyfikator może być **AFX_IDW_PANE_FIRST** , chyba że okna podziału jest zagnieżdżona w innym oknie podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Można osadzić `CSplitterWnd` w katalogu nadrzędnym [cframewnd —](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu, wykonując następujące czynności:  
  
1.  Osadź `CSplitterWnd` zmiennej członkowskiej w ramce nadrzędnej.  
  
2.  Zastąpienie ramka nadrzędny [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcję elementu członkowskiego.  
  
3.  Wywołanie **Utwórz** funkcji członkowskiej z wewnątrz przesłoniętej `OnCreateClient`.  
  
 Podczas tworzenia okna dzielącego z wewnątrz ramki nadrzędnej przekazać ramka nadrzędny `pContext` parametr okna podziału. W przeciwnym razie ten parametr może być **NULL**.  
  
 Wstępny wiersz minimalna wysokość i szerokość kolumny dynamiczne okno podziału są ustawiane przez `sizeMin` parametru. Te wymagania, które określają, czy okienko jest za mały, który będzie wyświetlany w całości, można zmienić z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji na temat dynamiczne okna podziału, zobacz "Podziału systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 Uwaga techniczna](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` Przegląd klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl  
 Wywoływane przez platformę, by utworzyć udostępnionych pasek przewijania.  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa styl okna.  
  
 `nID`  
 Identyfikator okna podrzędnego okna. Identyfikator może być **AFX_IDW_PANE_FIRST** , chyba że okna podziału jest zagnieżdżona w innym oknie podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie `CreateScrollBarCtrl` uwzględnienie dodatkowych formantów obok paska przewijania. Domyślnym zachowaniem jest utworzyć normalne formanty paska przewijania systemu Windows.  
  
##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic  
 Można utworzyć okna statyczny rozdzielacz, wywołaj `CreateStatic` funkcję elementu członkowskiego.  
  
```  
virtual BOOL CreateStatic(
    CWnd* pParentWnd,  
    int nRows,  
    int nCols,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Okno nadrzędne ramki okna podziału.  
  
 `nRows`  
 Liczba wierszy. Ta wartość nie może przekraczać 16.  
  
 *nCols*  
 Liczba kolumn. Ta wartość nie może przekraczać 16.  
  
 `dwStyle`  
 Określa styl okna.  
  
 `nID`  
 Identyfikator okna podrzędnego okna. Identyfikator może być **AFX_IDW_PANE_FIRST** , chyba że okna podziału jest zagnieżdżona w innym oknie podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 A `CSplitterWnd` zwykle jest osadzony w katalogu nadrzędnym `CFrameWnd` lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu, wykonując następujące czynności:  
  
1.  Osadź `CSplitterWnd` zmiennej członkowskiej w ramce nadrzędnej.  
  
2.  Zastąpienie ramka nadrzędny `OnCreateClient` funkcję elementu członkowskiego.  
  
3.  Wywołanie `CreateStatic` funkcji członkowskiej z wewnątrz przesłoniętej [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).  
  
 Okna podziału statycznych zawiera stała liczba okienka często z różnych klas.  
  
 Podczas tworzenia okna dzielącego statycznych, należy w tym samym czasie utworzyć jego paneli. [CreateView](#createview) funkcja członkowska jest zwykle używany w tym celu, ale można utworzyć innych klas nonview.  
  
 Wstępny wiersz minimalna wysokość i szerokość kolumny okna statyczny rozdzielacz jest równa 0. Te wymagania, które określają, kiedy okienko jest za mały do pokazania w całości, można zmienić z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich.  
  
 Aby dodać paski przewijania okna dzielącego statyczny, Dodaj **ws_hscroll —** i **ws_vscroll —** style do `dwStyle`.  
  
 Zobacz "Podziału systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 Uwaga techniczna](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` Przegląd klasy, aby uzyskać więcej informacji na temat statyczne okna podziału.  
  
##  <a name="createview"></a>  CSplitterWnd::CreateView  
 Tworzy panele dla okna dzielącego statycznych.  
  
```  
virtual BOOL CreateView(
    int row,  
    int col,  
    CRuntimeClass* pViewClass,  
    SIZE sizeInit,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa wiersz okna podziału, w której ma zostać umieszczony nowy widok.  
  
 `col`  
 Określa kolumnę okna podziału, w której ma zostać umieszczony nowy widok.  
  
 `pViewClass`  
 Określa [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nowego widoku.  
  
 *sizeInit*  
 Określa początkowy rozmiar nowego widoku.  
  
 `pContext`  
 Wskaźnik do tworzenia kontekstu używany do tworzenia widoku (zazwyczaj `pContext` przekazany ramka nadrzędny przesłoniętych [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcji członkowskiej, w którym jest tworzona okna podziału).  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie okienka okna statyczny rozdzielacz należy utworzyć przed platformę Wyświetla rozdzielacza.  
  
 Struktura wywołuje również tę funkcję elementu członkowskiego, aby utworzyć nowe okienka, gdy użytkownik dynamiczne okno podziału dzieli okienka, wiersz lub kolumnę.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd  
 Wywołanie do skonstruowania `CSplitterWnd` obiektu.  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć `CSplitterWnd` obiektu w dwóch krokach. Najpierw należy wywołać konstruktora, który tworzy `CSplitterWnd` obiekt, a następnie wywołać [Utwórz](#create) funkcji członkowskiej, która tworzy okno podziału i dołącza go do `CSplitterWnd` obiektu.  
  
##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn  
 Usuwa kolumnę z okna podziału.  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *colDelete*  
 Określa kolumnę do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by implementują logikę dynamiczne okno podziału (to znaczy, jeśli ma okna podziału **SPLS_DYNAMIC_SPLIT** styl). Można ją dostosować, wraz z funkcją wirtualną [CreateView](#createview), aby wdrożyć bardziej zaawansowane rozdzielaczy dynamicznych.  
  
##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow  
 Usuwa wiersz z okna podziału.  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>Parametry  
 *rowDelete*  
 Określa wiersz, który ma zostać usunięty.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by implementują logikę dynamiczne okno podziału (to znaczy, jeśli ma okna podziału **SPLS_DYNAMIC_SPLIT** styl). Można ją dostosować, wraz z funkcją wirtualną [CreateView](#createview), aby wdrożyć bardziej zaawansowane rozdzielaczy dynamicznych.  
  
##  <a name="deleteview"></a>  CSplitterWnd::DeleteView  
 Usuwa widok z okna podziału.  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa wiersz okna podziału na której chcesz usunąć widoku.  
  
 `col`  
 Określa kolumnę okna podziału, w której ma zostać usunięty w widoku.  
  
### <a name="remarks"></a>Uwagi  
 Trwa usuwanie aktywnego widoku, następnego widoku staną się aktywne. Domyślna implementacja zakłada widoku automatycznie usunąć w [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).  
  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by implementują logikę dynamiczne okno podziału (to znaczy, jeśli ma okna podziału **SPLS_DYNAMIC_SPLIT** styl). Można ją dostosować, wraz z funkcją wirtualną [CreateView](#createview), aby wdrożyć bardziej zaawansowane rozdzielaczy dynamicznych.  
  
##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit  
 Wykonuje polecenie podziału klawiatury, zwykle "podział okna".  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest polecenie wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasę, aby przekazać `CSplitterWnd` implementacji.  
  
##  <a name="doscroll"></a>  CSplitterWnd::DoScroll  
 Wykonuje synchroniczne przewijanie podzielonych okien.  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewFrom`  
 Wskaźnik do widoku, z którego pochodzi wiadomość przewijania.  
  
 `nScrollCode`  
 Kod paska przewijania, który wskazuje użytkownika do przewijania żądania. Ten parametr składa się z dwóch części: mniej znaczącego bajtu, który określa typ przewijania występujących w poziomie, a bajt znaczących, który określa typ przewijania występujących w pionie:  
  
- **SB_BOTTOM** Przewija do dołu.  
  
- **SB_LINEDOWN** Przewija jeden wiersz w dół.  
  
- **SB_LINEUP** Przewija jeden wiersz w górę.  
  
- **SB_PAGEDOWN** Przewija jedną stronę w dół.  
  
- **SB_PAGEUP** Przewija jedną stronę w górę.  
  
- **SB_TOP** Przewija do góry.  
  
 `bDoScroll`  
 Określa, czy doszło do określonej akcji przewijania. Jeśli `bDoScroll` jest **TRUE** (to znaczy, jeśli istnieje okno podrzędne i podział systemu windows ma wartości zakresu przewijania), a następnie przewijania określoną akcję można przeprowadzać; Jeśli `bDoScroll` jest **FALSE** (to znaczy, jeśli nie podrzędnego istnieje przedział czasu lub widokami złożonymi ma zakres nie przewijania), a następnie przewijanie nie występuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli występuje Synchroniczne przewijanie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by wykonać Synchroniczne przewijanie podzielonych okien odebrania wiadomości przewijania widoku. Należy przesłonić, aby wymagać akcji przez użytkownika przed Synchroniczne przewijanie jest dozwolone.  
  
##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy  
 Przewija podzielone okna przez daną liczbę pikseli.  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pViewFrom`  
 Wskaźnik do widoku, z którego pochodzi wiadomość przewijania.  
  
 `sizeScroll`  
 Liczba pikseli do być przewijane w poziomie i w pionie.  
  
 bDoScroll  
 Określa, czy doszło do określonej akcji przewijania. Jeśli `bDoScroll` jest **TRUE** (to znaczy, jeśli istnieje okno podrzędne i podział systemu windows ma wartości zakresu przewijania), a następnie przewijania określoną akcję można przeprowadzać; Jeśli `bDoScroll` jest **FALSE** (to znaczy, jeśli nie podrzędnego istnieje przedział czasu lub widokami złożonymi ma zakres nie przewijania), a następnie przewijanie nie występuje.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli występuje Synchroniczne przewijanie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę w odpowiedzi na wiadomość przewijania, do wykonania synchronizowane przewijanie podzielonych okien o wartość w pikselach, wskazane przez `sizeScroll`. Wskazuje liczbę wartości dodatnich przewijania w dół i w prawo; wartości ujemne wskazują przewijania w górę i w lewo.  
  
 Należy przesłonić, aby wymagać akcji przez użytkownika przed zezwoleniem przewijania.  
  
##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane  
 Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pRow`  
 Wskaźnik do **int** można pobrać numer wiersza aktywne okienko.  
  
 `pCol`  
 Wskaźnik do **int** można pobrać numer kolumny aktywne okienko.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do aktywnego okienka. **Wartość NULL** Jeśli istnieje nie aktywne okienko.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by określić aktywne okienko okna podziału. Należy przesłonić, aby wymagać akcji przez użytkownika przed pobraniem aktywne okienko.  
  
##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount  
 Zwraca bieżącą liczbą kolumn w okienku.  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą liczbę kolumn w rozdzielacza. Dla statyczny rozdzielacz będzie to również maksymalną liczbę kolumn.  
  
##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo  
 Zwraca informacje o określonej kolumny.  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `col`  
 Określa kolumnę.  
  
 *cxCur*  
 Odwołanie do `int` ustawioną Bieżąca szerokość kolumny.  
  
 `cxMin`  
 Odwołanie do `int` ustawioną Bieżąca minimalna szerokość kolumny.  
  
##  <a name="getpane"></a>  CSplitterWnd::GetPane  
 Zwraca okienko na określony wiersz i kolumnę.  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa wiersz.  
  
 `col`  
 Określa kolumnę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca okienko na określony wiersz i kolumnę. Okienko zwracane jest zwykle [CView](../../mfc/reference/cview-class.md)-klasy.  
  
##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount  
 Zwraca liczbę wierszy bieżącego okienka.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca bieżącą liczbę wierszy w oknie podziału. Okna podziału statycznych będzie to również maksymalną liczbę wierszy.  
  
##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo  
 Zwraca informacje na określony wiersz.  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa wiersz.  
  
 `cyCur`  
 Odwołanie do `int` ustawioną Bieżąca wysokość wiersza w pikselach.  
  
 `cyMin`  
 Odwołanie do `int` ustawioną Bieżąca minimalna wysokość wierszy w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby uzyskać informacje dotyczące określonego wiersza. `cyCur` Parametru jest wypełniony Bieżąca wysokość wiersza, a `cyMin` jest wypełniony minimalna wysokość wiersza.  
  
##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle  
 Zwraca styl udostępnionych pasek przewijania okna podziału.  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Co najmniej jeden z następujących okien styl flagi, w przypadku powodzenia:  
  
- **Ws_hscroll —** Jeśli rozdzielacz obecnie zarządza udostępnionego poziome paski przewijania.  
  
- **Ws_vscroll —** Jeśli rozdzielacz obecnie zarządza udostępnionego pionowe paski przewijania.  
  
 Jeśli zero, okna podziału nie zarządza aktualnie pasków przewijania udostępnionego.  
  
##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol  
 Pobiera obiekt podrzędny identyfikator okna dla okienka na określony wiersz i kolumnę.  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa okno podziału wiersza.  
  
 `col`  
 Określa kolumnę okna podziału.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator okna podrzędnego dla tego okienka.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska służy do tworzenia nonviews jako okienka i może zostać wywołana przed okienku istnieje.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane  
 Określa, czy `pWnd` jest obecnie okienko podrzędne tego okna podziału.  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt ma zostać przetestowana.  
  
 `pRow`  
 Wskaźnik do `int` do przechowywania numeru wiersza.  
  
 `pCol`  
 Wskaźnik do `int` do przechowywania numeru kolumny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli jest różna od zera, `pWnd` jest obecnie okienko podrzędne tego okna podziału i `pRow` i `pCol` są wypełniane pozycji okienka w oknie podziału. Jeśli `pWnd` nie jest okienko podrzędne tego okna podziału zwracane jest 0.  
  
### <a name="remarks"></a>Uwagi  
 W wersjach programu Visual C++ przed 6.0 ta funkcja została zdefiniowana jako  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 Ta wersja jest już przestarzały i nie powinna być używana.  
  
##  <a name="istracking"></a>  CSplitterWnd::IsTracking  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy pasek podziału w oknie obecnie jest przenoszony.  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli operacja rozdzielacz jest w toku; w przeciwnym razie 0.  
  
##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter  
 Renderuje Obraz okna podziału.  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia do rysowania. Jeśli `pDC` jest **NULL**, następnie [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) jest wywoływana przez platformę i brak podziału rysowane jest okno.  
  
 `nType`  
 Wartość **wyliczenia ESplitType**, który może być jedną z następujących czynności:  
  
- **splitBox** rozdzielacza przeciągnij pole.  
  
- `splitBar` Pasek, który znajduje się między dwoma podzielonych okien.  
  
- **splitIntersection** przecięcie podzielonych okien. Ten element nie zostanie wywołany, gdy uruchomione w systemie Windows 95/98.  
  
- **splitBorder** obramowania okna podziału.  
  
 `rect`  
 Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) obiekt określający wielkość i kształt podzielonych okien.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by narysować i określ dokładnie cechy okna podziału. Zastąpienie `OnDrawSplitter` dla zaawansowane dostosowywanie obrazów dla różnych składników graficznego okna podziału. Obrazów domyślny jest podobny do podziału w programie Microsoft Works dla systemu Windows lub Microsoft Windows 95/98, w tym połączeniu są przecięcia pasków podziału.  
  
 Aby uzyskać więcej informacji na temat dynamiczne okna podziału, zobacz "Podziału systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 Uwaga techniczna](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` Przegląd klasy.  
  
##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker  
 Renderuje Obraz okna podziału być tym samym rozmiarze i kształcie co okno ramowe.  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odwołanie do `CRect` obiektu Określanie prostokąt śledzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę podczas zmiany rozmiaru programu rozdzielaczy. Zastąpienie `OnInvertTracker` dla zaawansowane dostosowywanie obrazów z okna podziału. Obrazów domyślny jest podobny do podziału w programie Microsoft Works dla systemu Windows lub Microsoft Windows 95/98, w tym połączeniu są przecięcia pasków podziału.  
  
 Aby uzyskać więcej informacji na temat dynamiczne okna podziału, zobacz "Podziału systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 Uwaga techniczna](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` Przegląd klasy.  
  
##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout  
 Wywołanie w celu ponownego wyświetlenia okna podziału po dopasowaniu rozmiar wierszy lub kolumn.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby prawidłowo wyświetlić ponownie okna podziału po skorygowano rozmiary wierszy i kolumn z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich. W przypadku zmiany rozmiarów wierszy i kolumn w ramach procesu tworzenia przed udostępnieniem okna podziału nie jest konieczne do wywołania tej funkcji Członkowskich.  
  
 Struktura wywołuje funkcji członkowskiej zawsze, gdy użytkownik zmienia rozmiar okna podziału lub przenosi podziału.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CSplitterWnd::SetColumnInfo](#setcolumninfo).  
  
##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane  
 Ustawia okienko jako aktywne co w ramce.  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Jeśli `pWnd` jest **NULL**, określa wiersz w okienku będzie aktywny.  
  
 `col`  
 Jeśli `pWnd` jest **NULL**, określa kolumnę, w okienku będzie aktywny.  
  
 `pWnd`  
 Wskaźnik do `CWnd` obiektu. Jeśli **NULL**, okienko określony przez `row` i `col` jest ustawione aktywne. Jeśli nie **NULL**, określa okienku jest ustawione aktywne.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by ustawić okienko jako aktywne, gdy użytkownik zmieni fokus do okienka w oknie ramowym. Można jawnie wywołać `SetActivePane` można zmienić fokus na określony widok.  
  
 Określa okienku, podając wiersza i kolumny **lub** zapewniając `pWnd`.  
  
##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo  
 Wywołanie ustawiania informacji o określonej kolumny.  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>Parametry  
 `col`  
 Określa kolumnę okna podziału.  
  
 *cxIdeal*  
 Określa idealne szerokość okna podziału kolumny w pikselach.  
  
 `cxMin`  
 Określa minimalną szerokość okna podziału kolumny w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby ustawić nową szerokość minimalna i nadaje się doskonale szerokość kolumny. Minimalna wartość kolumny określa, kiedy kolumny będą za mały, aby w pełni można wyświetlić.  
  
 Gdy w ramach Wyświetla okna podziału, układa okienkach kolumn i wierszy, zgodnie z ich idealne wymiarów, Praca z lewego górnego do prawego dolnego rogu obszaru klienckiego okna podziału.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo  
 Wywołanie ustawiania informacji określony wiersz.  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>Parametry  
 `row`  
 Określa okno podziału wiersza.  
  
 *cyIdeal*  
 Określa wysokość nadaje się doskonale dla wiersza okna podziału w pikselach.  
  
 `cyMin`  
 Określa minimalną wysokość okna podziału wiersza w pikselach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji Członkowskich, aby ustawić nową wysokość minimalna i nadaje się doskonale wysokość wiersza. Wartość minimalna wiersz określa, gdy wiersz będzie za mały, aby w pełni można wyświetlić.  
  
 Gdy w ramach Wyświetla okna podziału, układa okienkach kolumn i wierszy, zgodnie z ich idealne wymiarów, Praca z lewego górnego do prawego dolnego rogu obszaru klienckiego okna podziału.  
  
##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle  
 Określa, że nowy styl przewijania okna podziału udostępnionych pasek przewijania pomocy technicznej.  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Nowy styl przewijania okna podziału udostępnionych pasek przewijania pomocy technicznej, które może być jedną z następujących wartości:  
  
- **Ws_hscroll —** Utwórz/Pokaż poziome udostępnionych paski przewijania.  
  
- **Ws_vscroll —** pionowego Utwórz/Pokaż udostępnionych paski przewijania.  
  
### <a name="remarks"></a>Uwagi  
 Po utworzeniu paska przewijania nie zostanie on zniszczona nawet wtedy, gdy `SetScrollStyle` jest wywoływana bez tego stylu; zamiast tego są ukryte tych pasków przewijania. Dzięki temu paski przewijania zachować ich stanu, nawet jeśli są ukryte. Po wywołaniu `SetScrollStyle` należy wywołać [RecalcLayout](#recalclayout) wszystkie zmiany zaczęły obowiązywać.  
  
##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn  
 Wskazuje gdzie okno ramowe dzieli się pionowo.  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>Parametry  
 *cxBefore*  
 Pozycja w pikselach, przed którymi nastąpi podział.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana po utworzeniu okna dzielącego pionowej. `SplitColumn` wskazuje domyślną lokalizację, gdzie nastąpi podział.  
  
 `SplitColumn` Metoda jest wywoływana przez platformę, by implementują logikę dynamiczne okno podziału (to znaczy, jeśli ma okna podziału **SPLS_DYNAMIC_SPLIT** styl). Można ją dostosować, wraz z funkcją wirtualną [CreateView](#createview), aby wdrożyć bardziej zaawansowane rozdzielaczy dynamicznych.  
  
##  <a name="splitrow"></a>  CSplitterWnd::SplitRow  
 Wskazuje gdzie okno ramowe dzieli się poziomo.  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>Parametry  
 *cyBefore*  
 Pozycja w pikselach, przed którymi nastąpi podział.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana po utworzeniu okna rozdzielacz poziomy. `SplitRow` wskazuje domyślną lokalizację, gdzie nastąpi podział.  
  
 `SplitRow` Metoda jest wywoływana przez platformę, by implementują logikę dynamiczne okno podziału (to znaczy, jeśli ma okna podziału **SPLS_DYNAMIC_SPLIT** styl). Można ją dostosować, wraz z funkcją wirtualną [CreateView](#createview), aby wdrożyć bardziej zaawansowane rozdzielaczy dynamicznych.  
  
##  <a name="ondraw"></a>  CSplitterWnd::OnDraw  
 Wywoływane przez platformę, by narysować okna podziału.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC VIEWEX](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)
