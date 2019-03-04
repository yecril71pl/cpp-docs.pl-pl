---
title: Klasa CSplitterWnd
ms.date: 11/04/2016
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
ms.openlocfilehash: 42913ddea7818636dce8d630ed2d79d13c19ce81
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302107"
---
# <a name="csplitterwnd-class"></a>Klasa CSplitterWnd

Oferuje funkcje okna dzielącego, która jest oknem, które zawiera wiele okienek.

## <a name="syntax"></a>Składnia

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Wywołania do konstruowania `CSplitterWnd` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Wykonuje polecenie następne okienko lub poprzednie okienko.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Sprawdza, czy polecenia następne okienko lub poprzednie okienko jest obecnie możliwe.|
|[CSplitterWnd::Create](#create)|Wywołanie, aby utworzyć dynamiczne okno rozdzielacza i dołączyć go do `CSplitterWnd` obiektu.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Tworzy współdzieloną kontrolkę paska przewijania.|
|[CSplitterWnd::CreateStatic](#createstatic)|Wywołanie, aby utworzyć okno rozdzielacza statycznego i dołączyć go do `CSplitterWnd` obiektu.|
|[CSplitterWnd::CreateView](#createview)|Wywołanie w celu utworzenia okienko w okno rozdzielacza.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Usuwa kolumnę z okna rozdzielacza.|
|[CSplitterWnd::DeleteRow](#deleterow)|Usuwa wiersz z okna rozdzielacza.|
|[CSplitterWnd::DeleteView](#deleteview)|Usuwa widok z okna rozdzielacza.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Wykonuje polecenie podziału klawiatury, zwykle "podział okna".|
|[CSplitterWnd::DoScroll](#doscroll)|Wykonuje synchroniczne przewijanie podzielonych okien.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Przewija podzielone okna daną liczbę pikseli.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Zwraca bieżącą liczbą kolumn w okienku.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Zwraca informacje o określonej kolumny.|
|[CSplitterWnd::GetPane](#getpane)|Zwraca okienko w określonych wiersza i kolumny.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Zwraca bieżącą liczbę wierszy w okienku.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Zwraca informacje na określony wiersz.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Zwraca wartość stylu udostępnionego paska przewijania.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Zwraca element podrzędny identyfikator okna okienka w określonych wiersza i kolumny.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Wywołanie w celu określenia, czy okno jest obecnie okienko podrzędne tego okna rozdzielacza.|
|[CSplitterWnd::IsTracking](#istracking)|Określa, jeśli obecnie Trwa przenoszenie pasek podziału.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Wywołanie, aby ponownie wyświetlić okno rozdzielacza po dopasowaniu rozmiar wiersza lub kolumny.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Ustawia okienko jako aktywna w ramce.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Wywołanie, aby ustawić informacje o określonej kolumny.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Wywołanie, aby ustawić informacje o określony wiersz.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Określa, że nowy styl paska przewijania, okna rozdzielacza udostępnione obsługi paska przewijania.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Wskazuje gdzie okno ramowe dzieli się pionowo.|
|[CSplitterWnd::SplitRow](#splitrow)|Wskazuje gdzie okno ramowe dzieli się poziomo.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Metoda wywoływana przez platformę, by narysować okno rozdzielacza.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Renderuje Obraz okna podziału.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Renderuje Obraz okna podziału, w tym samym rozmiarze i kształcie co okno ramowe.|

## <a name="remarks"></a>Uwagi

Okienko jest zazwyczaj obiektu specyficzne dla aplikacji pochodzące z [CView](../../mfc/reference/cview-class.md), ale może być dowolną [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który ma identyfikator podrzędny odpowiednie okna.

A `CSplitterWnd` obiekt zwykle jest osadzony w obiekcie nadrzędnym [CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu. Utwórz `CSplitterWnd` obiektu, wykonując następujące czynności:

1. Osadzanie `CSplitterWnd` zmiennej składowej w nadrzędnej ramki.

2. Zastąp nadrzędnej ramki [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcja elementu członkowskiego.

3. Od w terminie zgodnym z przesłoniętą `OnCreateClient`, wywołaj [Utwórz](#create) lub [CreateStatic](#createstatic) funkcji składowej typu `CSplitterWnd`.

Wywołaj `Create` funkcji elementu członkowskiego, aby utworzyć dynamiczne okno rozdzielacza. Dynamiczne okno rozdzielacza zwykle jest używana do tworzenia i przewiń liczba poszczególnych okienkach lub widoki tego samego dokumentu. Szablon tworzy automatycznie początkowej okienka rozdzielacza; następnie ramach tworzy, zmienia rozmiar i usuwa dodatkowe okienek, jak użytkownik działa kontrolki okna rozdzielacza.

Gdy wywołujesz `Create`, należy określić wiersz minimalna wysokość i szerokość kolumny które określają, kiedy są zbyt mała, aby w pełni wyświetlane okienka. Po wywołaniu metody `Create`, można dostosować te wymagania, wywołując [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) funkcji elementów członkowskich.

Również użyć `SetColumnInfo` i `SetRowInfo` funkcji elementów członkowskich do zestawu "idealnym rozwiązaniem" szerokość kolumny i "idealnym rozwiązaniem" wysokość wiersza. Kiedy struktura wyświetli okno rozdzielacza, po raz pierwszy wyświetli ramki nadrzędnej, a następnie okno rozdzielacza. Struktura następnie decydujących o okienkach kolumn i wierszy, zgodnie z wymiarami idealne rozwiązanie w lewym górnym rogu nad prawym dolnym rogu okna rozdzielacza obszaru klienta.

Okienka wszystkich w dynamiczne okno rozdzielacza muszą należeć do tej samej klasy. Aplikacje, które obsługują dynamiczne okna podziału obejmują programu Microsoft Word i Microsoft Excel.

Użyj `CreateStatic` funkcja elementu członkowskiego, aby utworzyć okno rozdzielacza statycznego. Użytkownik może zmienić rozmiar okienka w statyczny rozdzielacz okna nie ich cyfrą lub zamówienia.

Specjalnie należy utworzyć okienka wszystkich statyczny rozdzielacz firmy, tworząc statyczny rozdzielacz. Upewnij się, tworzenie wszystkich okienek przed nadrzędnej ramki `OnCreateClient` zwraca funkcja elementu członkowskiego lub będą framework nie poprawnie wyświetlić okno.

`CreateStatic` Funkcja elementu członkowskiego automatycznie inicjuje statyczny rozdzielacz z minimalną wysokość wiersza i kolumny szerokość 0. Po wywołaniu metody `Create`, dostosować te wymagania, wywołując [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) funkcji elementów członkowskich. Również użyć `SetColumnInfo` i `SetRowInfo` po wywołaniu metody `CreateStatic` do wskazania żądanego idealne okienko wymiarów.

Poszczególnych okienek statyczny rozdzielacz często należą do różnych klas. Przykłady statyczne okna podziału Zobacz Edytor grafiki i Menedżer plików Windows.

Okno rozdzielacza obsługuje pasków przewijania specjalne (oprócz paski przewijania, które mogą mieć okienka). Te paski przewijania są elementami podrzędnymi `CSplitterWnd` obiektu i są współużytkowane z okienka.

Możesz utworzyć te paski przewijania specjalne, podczas tworzenia okna rozdzielacza. Na przykład `CSplitterWnd` zawierający jeden wiersz, dwóch kolumn, a styl WS_VSCROLL wyświetli pasek przewijania pionowego, który jest współużytkowany przez dwa okienka. Gdy użytkownik przesuwa paska przewijania, WM_VSCROLL komunikaty są wysyłane do obu okienka. Podczas okienka ustawić położenie paska przewijania, zostaje ustawiony na pasku przewijania udostępnionych.

Aby uzyskać więcej informacji na temat okna podziału, zobacz [techniczne 29 Uwaga](../../mfc/tn029-splitter-windows.md).

Aby uzyskać więcej informacji na temat tworzenia dynamiczne okna podziału zobacz:

- Próbki MFC [Bazgroły](../../visual-cpp-samples.md)

- Próbki MFC [VIEWEX](../../visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext

Metoda wywoływana przez platformę, by wykonać polecenie następne okienko lub poprzednie okienko.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Wskazuje, które okno, aby aktywować. **Wartość TRUE,** dla poprzedniego; **FALSE** następny.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest polecenia wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasy, aby delegować do `CSplitterWnd` implementacji.

##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext

Metoda wywoływana przez platformę, by sprawdzić, czy polecenia następne okienko lub poprzednie okienko jest obecnie możliwe.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Wskazuje, które okno, aby aktywować. **Wartość TRUE,** dla poprzedniego; **FALSE** następny.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest polecenia wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasy, aby delegować do `CSplitterWnd` implementacji.

##  <a name="create"></a>  CSplitterWnd::Create

Aby utworzyć dynamiczne okno rozdzielacza, wywołaj `Create` funkcja elementu członkowskiego.

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

*pParentWnd*<br/>
Okno nadrzędne ramki okna rozdzielacza.

*nMaxRows*<br/>
Maksymalna liczba wierszy w okno rozdzielacza. Ta wartość nie może przekraczać 2.

*nMaxCols*<br/>
Maksymalna liczba kolumn w okno rozdzielacza. Ta wartość nie może przekraczać 2.

*sizeMin*<br/>
Określa minimalny rozmiar okienka mogą być wyświetlane.

*pContext*<br/>
Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. W większości przypadków, może to być *pContext* przekazany do nadrzędnej ramki okna.

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędne okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza zagnieżdżonej w inne okno rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Możesz osadzić `CSplitterWnd` w obiekcie nadrzędnym [CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu, wykonując następujące czynności:

1. Osadzanie `CSplitterWnd` zmiennej składowej w nadrzędnej ramki.

1. Zastąp nadrzędnej ramki [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcja elementu członkowskiego.

1. Wywołaj `Create` funkcji składowej z w terminie zgodnym z przesłoniętą `OnCreateClient`.

Podczas tworzenia okna rozdzielacza z wewnątrz ramki nadrzędnej, należy przekazać nadrzędnej ramki *pContext* parametr okno rozdzielacza. W przeciwnym razie ten parametr może mieć wartości NULL.

Wstępny wiersz minimalna wysokość i szerokość kolumny dynamiczne okno rozdzielacza są ustawiane przez *sizeMin* parametru. Te wymagania, które określają, czy okienko jest zbyt mały, który będzie wyświetlany w całości, mogą być zmieniane z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich.

Aby uzyskać więcej informacji o dynamiczne okna podziału, zobacz "Rozdzielacz Windows" w artykule [wiele typów dokumentów, widoków i ramek Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [techniczne 29 Uwaga](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` klasa — Przegląd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl

Metoda wywoływana przez strukturę w celu utworzenia współdzieloną kontrolkę paska przewijania.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędne okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza zagnieżdżonej w inne okno rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąp `CreateScrollBarCtrl` obejmujący dodatkowe kontrolki obok paska przewijania. Zachowanie domyślne jest do utworzenia normalne formanty paska przewijania Windows.

##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic

Aby utworzyć okno statyczny rozdzielacz, należy wywołać `CreateStatic` funkcja elementu członkowskiego.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Okno nadrzędne ramki okna rozdzielacza.

*nRows*<br/>
Liczba wierszy. Ta wartość nie może przekraczać 16.

*nCols*<br/>
Liczba kolumn. Ta wartość nie może przekraczać 16.

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędne okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza zagnieżdżonej w inne okno rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

A `CSplitterWnd` zwykle jest osadzony w obiekcie nadrzędnym `CFrameWnd` lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) obiektu, wykonując następujące czynności:

1. Osadzanie `CSplitterWnd` zmiennej składowej w nadrzędnej ramki.

1. Zastąp nadrzędnej ramki `OnCreateClient` funkcja elementu członkowskiego.

1. Wywołaj `CreateStatic` funkcji składowej z w terminie zgodnym z przesłoniętą [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Okno statyczny rozdzielacz zawiera stałą liczbą okienek, często z różnych klas.

Podczas tworzenia okna statyczny rozdzielacz, należy w tym samym czasie utworzyć jego paneli. [Utwórz widok](#createview) funkcja członkowska jest zwykle używany w tym celu, ale można tworzyć innych klas nonview.

Początkowy wiersz minimalna wysokość i szerokość kolumny w oknie statyczny rozdzielacz jest równa 0. Te wymagania, które określają, kiedy okienko jest zbyt mały, mają być wyświetlane w całości, mogą być zmieniane z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich.

Aby dodać paski przewijania, okna statyczny rozdzielacz, Dodaj style WS_HSCROLL i WS_VSCROLL *dwStyle*.

Zobacz "Rozdzielacz Windows" w artykule [wiele typów dokumentów, widoków i ramek Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [techniczne 29 Uwaga](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` klasa — Przegląd, aby uzyskać więcej informacji na temat statyczne okna podziału.

##  <a name="createview"></a>  CSplitterWnd::CreateView

Tworzy panele dla okna rozdzielacza statycznego.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz okno rozdzielacza, w której chcesz umieścić nowy widok.

*col*<br/>
Określa kolumnę okno rozdzielacza, w której chcesz umieścić nowy widok.

*pViewClass*<br/>
Określa [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nowego widoku.

*sizeInit*<br/>
Określa początkowy rozmiar nowego widoku.

*pContext*<br/>
Wskaźnik do tworzenia kontekst użyty do utworzenia widoku (zazwyczaj *pContext* przekazany do nadrzędnej ramki zgodnym z przesłoniętą [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcja elementu członkowskiego, w którym jest okna rozdzielacza Trwa tworzenie).

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie okienka okna statyczny rozdzielacz musi zostać utworzona przed ramach Wyświetla rozdzielacza.

Struktura wywołuje również tej funkcji elementu członkowskiego, aby utworzyć nowe okienka po użytkownik dynamiczne okno rozdzielacza dzieli okienko, wiersz lub kolumnę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd

Wywołania do konstruowania `CSplitterWnd` obiektu.

```
CSplitterWnd();
```

### <a name="remarks"></a>Uwagi

Konstruowania `CSplitterWnd` obiektu w dwóch krokach. Po pierwsze wywołanie konstruktora, który tworzy `CSplitterWnd` obiektu, a następnie wywołaj [Utwórz](#create) funkcji elementu członkowskiego, która tworzy okno rozdzielacza i dołącza je do `CSplitterWnd` obiektu.

##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn

Usuwa kolumnę z okna rozdzielacza.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Określa kolumny do usunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, by zaimplementować logikę dynamiczne okno rozdzielacza (to znaczy, jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można ją dostosować, wraz z funkcją wirtualną [Utwórz widok](#createview), aby zaimplementować bardziej zaawansowane rozdzielaczy dynamicznych.

##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow

Usuwa wiersz z okna rozdzielacza.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*rowDelete*<br/>
Określa wiersz do usunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, by zaimplementować logikę dynamiczne okno rozdzielacza (to znaczy, jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można ją dostosować, wraz z funkcją wirtualną [Utwórz widok](#createview), aby zaimplementować bardziej zaawansowane rozdzielaczy dynamicznych.

##  <a name="deleteview"></a>  CSplitterWnd::DeleteView

Usuwa widok z okna rozdzielacza.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz okna rozdzielacza, od którego należy usunąć widoku.

*col*<br/>
Określa kolumnę okno rozdzielacza, od którego należy usunąć widoku.

### <a name="remarks"></a>Uwagi

Jeśli widok aktywny jest usuwany, stanie się aktywny następnego widoku. Domyślna implementacja przyjęto założenie, automatycznie widoku usunąć [postncdestroy —](../../mfc/reference/cwnd-class.md#postncdestroy).

Ta funkcja członkowska jest wywoływana przez platformę, by zaimplementować logikę dynamiczne okno rozdzielacza (to znaczy, jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można ją dostosować, wraz z funkcją wirtualną [Utwórz widok](#createview), aby zaimplementować bardziej zaawansowane rozdzielaczy dynamicznych.

##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit

Wykonuje polecenie podziału klawiatury, zwykle "podział okna".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest polecenia wysokiego poziomu, który jest używany przez [CView](../../mfc/reference/cview-class.md) klasy, aby delegować do `CSplitterWnd` implementacji.

##  <a name="doscroll"></a>  CSplitterWnd::DoScroll

Wykonuje synchroniczne przewijanie podzielonych okien.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi przewijania wiadomości.

*nScrollCode*<br/>
Kod paska przewijania, który wskazuje użytkownika przewijanym żądania. Ten parametr składa się z dwóch części: mniej znaczący bajt, określający typ przewijania pojawiają się poziome i bajt wyższego rzędu, który określa typ przewijania występujących w pionie:

    - Przewija SB_BOTTOM do dołu.

    - Przewija SB_LINEDOWN jeden wiersz w dół.

    - Przewija SB_LINEUP jeden wiersz w górę.

    - Przewija SB_PAGEDOWN jedną stronę w dół.

    - Przewija SB_PAGEUP jedną stronę w górę.

    - Przewija SB_TOP do góry.

*bDoScroll*<br/>
Określa, czy występuje w określonej akcji przewijania. Jeśli *bDoScroll* jest wartość TRUE, (to znaczy, jeśli istnieje okno podrzędne i okna podziału mają zakres przewijania), a następnie określoną akcję przewijania mogą być wykonywane; Jeśli *bDoScroll* ma wartość FAŁSZ (to znaczy, jeśli nie okna podrzędnego istnieje, lub Brak zakresu przewijania widokami złożonymi), a następnie przewijając nie występuje.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wystąpi Synchroniczne przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, by wykonać Synchroniczne przewijanie podzielonych okien, gdy widok odbiera komunikat przewijania. Należy przesłonić, aby wymagać akcji przez użytkownika, przed Synchroniczne przewijanie jest dozwolone.

##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy

Przewija podzielone okna daną liczbę pikseli.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi przewijania wiadomości.

*sizeScroll*<br/>
Liczba pikseli do być przewijane w poziomie i w pionie.

*bDoScroll*<br/>
Określa, czy występuje w określonej akcji przewijania. Jeśli *bDoScroll* jest wartość TRUE, (to znaczy, jeśli istnieje okno podrzędne i okna podziału mają zakres przewijania), a następnie określoną akcję przewijania mogą być wykonywane; Jeśli *bDoScroll* ma wartość FAŁSZ (to znaczy, jeśli nie okna podrzędnego istnieje, lub Brak zakresu przewijania widokami złożonymi), a następnie przewijając nie występuje.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wystąpi Synchroniczne przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez strukturę w odpowiedzi na wiadomość przewijania, aby wykonać synchronizację przewijanie podzielonych okien o kwotę, w pikselach, wskazywanym przez *sizeScroll*. Dodatnie wartości wskazują, przewijając w dół i w prawo; wartości ujemne wskazują przewijanie w górę i w lewo.

Należy przesłonić, aby wymagać akcji przez użytkownika przed zezwoleniem na przewijania.

##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane

Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pRow*<br/>
Wskaźnik do **int** można pobrać numer wiersza aktywne okienko.

*pCol*<br/>
Wskaźnik do **int** można pobrać numer kolumny w okienku aktywnych.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywne okienko. Wartość NULL, jeśli istnieje nie aktywne okienko.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, aby określić aktywne okienko w okno rozdzielacza. Należy przesłonić, aby wymagać akcji przez użytkownika przed pobraniem aktywne okienko.

##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount

Zwraca bieżącą liczbą kolumn w okienku.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę kolumn w rozdzielacza. Aby uzyskać statyczny rozdzielacz będzie to również maksymalna liczba kolumn.

##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo

Zwraca informacje o określonej kolumny.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*col*<br/>
Określa kolumnę.

*cxCur*<br/>
Odwołanie do **int** należy ustawić do bieżącej szerokość kolumny.

*cxMin*<br/>
Odwołanie do **int** należy ustawić do bieżącej minimalną szerokość kolumny.

##  <a name="getpane"></a>  CSplitterWnd::GetPane

Zwraca okienko w określonych wiersza i kolumny.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz.

*col*<br/>
Określa kolumnę.

### <a name="return-value"></a>Wartość zwracana

Zwraca okienko w określonych wiersza i kolumny. Okienko zwracany jest zwykle [CView](../../mfc/reference/cview-class.md)-klasy pochodnej.

##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount

Zwraca bieżącą liczbę wierszy w okienku.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę wierszy w okno rozdzielacza. W oknie statyczny rozdzielacz będzie to również maksymalna liczba wierszy.

##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo

Zwraca informacje na określony wiersz.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz.

*cyCur*<br/>
Odwołanie do **int** należy ustawić do bieżącej wysokość wiersza w pikselach.

*cyMin*<br/>
Odwołanie do **int** należy ustawić do bieżącej minimalną wysokość wiersza w pikselach.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje na temat określonego wiersza. *CyCur* parametru jest wypełniany bieżącego wysokość określony wiersz i *cyMin* jest wypełniany minimalną wysokość wiersza.

##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle

Zwraca styl udostępnionego paska przewijania okno rozdzielacza.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Co najmniej jeden z następujących okien stylu flagi, jeśli to się powiedzie:

    - WS_HSCROLL Jeśli rozdzielacz jest obecnie zarządzane przez udostępniane poziomych pasków przewijania.

    - WS_VSCROLL Jeśli rozdzielacz jest obecnie zarządzane przez udostępniane pionowe paski przewijania.

Jeśli zero, okno rozdzielacza nie zarządza aktualnie pasków przewijania udostępnionych.

##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol

Pobiera element podrzędny identyfikator okna dla okienka w określonych wiersza i kolumny.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz okno rozdzielacza.

*col*<br/>
Określa kolumnę okno rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Identyfikator okna podrzędnego dla tego okienka.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest używana do tworzenia nonviews jako okienka i może zostać wywołana przed istnieje okienka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane

Określa, czy *pWnd* jest obecnie okienko podrzędne tego okna rozdzielacza.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt ma zostać przetestowana.

*pRow*<br/>
Wskaźnik do **int** w którym będzie przechowywany numer wiersza.

*pCol*<br/>
Wskaźnik do **int** do przechowywania numeru kolumny.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość jest niezerowa, *pWnd* jest obecnie okienko podrzędne tego okna rozdzielacza i *pRow* i *pCol* są wypełniane położenie okienka Okno rozdzielacza. Jeśli *pWnd* nie jest okienko podrzędne tego okna rozdzielacza, zwracany jest 0.

### <a name="remarks"></a>Uwagi

W wersjach Visual C++ przed 6.0 ta funkcja została zdefiniowana jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Ta wersja jest obecnie przestarzała i nie powinna być używana.

##  <a name="istracking"></a>  CSplitterWnd::IsTracking

Wywołaj tę funkcję elementu członkowskiego, aby określić, jeśli obecnie Trwa przenoszenie pasek podziału w oknie.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli operacja rozdzielacz jest w toku; w przeciwnym razie 0.

##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter

Renderuje Obraz okna podziału.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia do rysowania. Jeśli *kontrolera pDC* ma wartość NULL, następnie [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) jest wywoływana przez platformę i nie podział okna jest rysowany.

*nType*<br/>
Wartość `enum ESplitType`, który może być jedną z następujących czynności:

    - `splitBox` Przeciągnij pole rozdzielacza.

    - `splitBar` Pasek, który pojawia się między dwoma podzielonych okien.

    - `splitIntersection` Przecięcie podzielonych okien. Ten element nie zostanie wywołany, gdy w systemie Windows 95/98.

    - `splitBorder` Obramowanie okna podziału.

*Rect*<br/>
Odwołanie do [CRect](../../atl-mfc-shared/reference/crect-class.md) określający rozmiar i kształt podzielonych okien.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, by narysować i określ dokładnie cechy okno rozdzielacza. Zastąp `OnDrawSplitter` dla zaawansowane dostosowywanie obrazów dla różnych składników graficznego okno rozdzielacza. Obraz domyślny jest podobny do podziału w programie Microsoft Works dla Windows lub Microsoft Windows 95/98, w tym rezultatem przecięcia paski podziału.

Aby uzyskać więcej informacji o dynamiczne okna podziału, zobacz "Rozdzielacz Windows" w artykule [wiele typów dokumentów, widoków i ramek Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [techniczne 29 Uwaga](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` klasa — Przegląd.

##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker

Renderuje Obraz okna podziału, w tym samym rozmiarze i kształcie co okno ramowe.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odwołanie do `CRect` określający prostokąt śledzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę podczas zmiany rozmiaru z rozdzielaczy. Zastąp `OnInvertTracker` dla zaawansowane dostosowywanie Obraz okna podziału. Obraz domyślny jest podobny do podziału w programie Microsoft Works dla Windows lub Microsoft Windows 95/98, w tym rezultatem przecięcia paski podziału.

Aby uzyskać więcej informacji o dynamiczne okna podziału, zobacz "Rozdzielacz Windows" w artykule [wiele typów dokumentów, widoków i ramek Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [techniczne 29 Uwaga](../../mfc/tn029-splitter-windows.md)i `CSplitterWnd` klasa — Przegląd.

##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout

Wywołanie, aby ponownie wyświetlić okno rozdzielacza po dopasowaniu rozmiar wiersza lub kolumny.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby poprawnie ponownie wyświetlić okno rozdzielacza po skorygowano rozmiary wierszy i kolumn z [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) funkcji elementów członkowskich. Zmiana rozmiaru wierszy i kolumn jako część procesu tworzenia przed okno rozdzielacza jest widoczna, nie jest wymagane do wywołania tej funkcji elementu członkowskiego.

Struktura wywołuje tej funkcji elementu członkowskiego, zawsze wtedy, gdy użytkownik zmienia rozmiar okna rozdzielacza lub przenosi podziału.

### <a name="example"></a>Przykład

  Zobacz przykład [CSplitterWnd::SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane

Ustawia okienko jako aktywna w ramce.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Jeśli *pWnd* ma wartość NULL, określa wiersz w okienku, które będą aktywne.

*col*<br/>
Jeśli *pWnd* ma wartość NULL, określa kolumnę w okienku, które będą aktywne.

*pWnd*<br/>
Wskaźnik do `CWnd` obiektu. Jeśli ma wartość NULL, okienka określony przez *wiersz* i *kolumna* jest ustawiony na aktywny. Jeśli nie ma wartość NULL, określa okienko w którym jest ustawiony na aktywny.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, by ustawić okienko jako aktywne, gdy użytkownik zmieni fokus do okienka w oknie ramki. Można jawnie wywołać `SetActivePane` można zmienić fokus na określonym widoku.

Określ okienko, zapewniając wiersza i kolumny **lub** , zapewniając *pWnd*.

##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo

Wywołanie, aby ustawić informacje o określonej kolumny.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*col*<br/>
Określa kolumnę okno rozdzielacza.

*cxIdeal*<br/>
Idealna szerokość kolumny okno rozdzielacza określa w pikselach.

*cxMin*<br/>
Określa minimalną szerokość kolumny okna podziału w pikselach.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nową szerokość minimalna i doskonale szerokość kolumny. Minimalna wartość kolumny określa, kiedy będzie zbyt mała, aby w pełni wyświetlane kolumny.

Kiedy struktura wyświetli okno rozdzielacza, układa okienkach kolumn i wierszy, zgodnie z wymiarami idealne rozwiązanie w lewym górnym rogu nad prawym dolnym rogu okna rozdzielacza obszaru klienta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo

Wywołanie, aby ustawić informacje o określony wiersz.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*wiersz*<br/>
Określa wiersz okno rozdzielacza.

*cyIdeal*<br/>
Określa wysokość idealne rozwiązanie dla wiersza okno rozdzielacza w pikselach.

*cyMin*<br/>
Minimalna wysokość wiersza okno rozdzielacza określa w pikselach.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nową wysokość minimalna i doskonale wysokość wiersza. Wartość minimalna wiersz określa, kiedy wiersza będzie zbyt mała, aby w pełni można wyświetlić.

Kiedy struktura wyświetli okno rozdzielacza, układa okienkach kolumn i wierszy, zgodnie z wymiarami idealne rozwiązanie w lewym górnym rogu nad prawym dolnym rogu okna rozdzielacza obszaru klienta.

##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle

Określa, że nowy styl przewiń okno rozdzielacza udostępnione obsługi paska przewijania.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Nowy styl przewiń okno rozdzielacza udostępnione obsługi paska przewijania, który może być jednym z następujących wartości:

- WS_HSCROLL Utwórz/Pokaż poziome udostępnionego paski przewijania.

- WS_VSCROLL Utwórz/Pokaż pionowy udostępnionego paski przewijania.

### <a name="remarks"></a>Uwagi

Po utworzeniu paska przewijania nie zostanie on zniszczona nawet wtedy, gdy `SetScrollStyle` jest wywoływana bez stylu; zamiast tego te paski przewijania są ukryte. Dzięki temu paski przewijania zachować ich stanu, nawet jeśli są ukryte. Po wywołaniu `SetScrollStyle` należy wywołać [recalclayout —](#recalclayout) wszystkie zmiany zostały wprowadzone.

##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn

Wskazuje gdzie okno ramowe dzieli się pionowo.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxBefore*<br/>
Pozycja w pikselach, przed którymi nastąpi podział.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana, gdy stworzono okno rozdzielacza pionowy. `SplitColumn` wskazuje domyślną lokalizację, gdzie nastąpi podział.

`SplitColumn` jest wywoływana przez platformę, by zaimplementować logikę dynamiczne okno rozdzielacza (to znaczy, jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można ją dostosować, wraz z funkcją wirtualną [Utwórz widok](#createview), aby zaimplementować bardziej zaawansowane rozdzielaczy dynamicznych.

##  <a name="splitrow"></a>  CSplitterWnd::SplitRow

Wskazuje gdzie okno ramowe dzieli się poziomo.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyBefore*<br/>
Pozycja w pikselach, przed którymi nastąpi podział.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana, gdy stworzono okno rozdzielacz poziomy. `SplitRow` wskazuje domyślną lokalizację, gdzie nastąpi podział.

`SplitRow` jest wywoływana przez platformę, by zaimplementować logikę dynamiczne okno rozdzielacza (to znaczy, jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można ją dostosować, wraz z funkcją wirtualną [Utwórz widok](#createview), aby zaimplementować bardziej zaawansowane rozdzielaczy dynamicznych.

##  <a name="ondraw"></a>  CSplitterWnd::OnDraw

Metoda wywoływana przez platformę, by narysować okno rozdzielacza.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Próbki MFC VIEWEX](../../visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
