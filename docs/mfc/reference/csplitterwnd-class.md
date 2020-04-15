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
ms.openlocfilehash: 8c8ce90f5e36d6cdc2592233588bc3bd7bf2c9d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371699"
---
# <a name="csplitterwnd-class"></a>Klasa CSplitterWnd

Udostępnia funkcje okna rozdzielacza, które jest oknem zawierającym wiele okienek.

## <a name="syntax"></a>Składnia

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Wywołanie do `CSplitterWnd` konstruowania obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Wykonuje polecenie Następne okienko lub Poprzednie okienko.|
|[CSplitterWnd::CanActivateNastępna](#canactivatenext)|Sprawdza, czy polecenie Następne okienko lub Poprzednie okienko jest obecnie możliwe.|
|[CSplitterWnd::Tworzenie](#create)|Wywołanie utworzenia dynamicznego okna rozdzielacza i dołączenie go do `CSplitterWnd` obiektu.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Tworzy kontrolkę udostępnionego paska przewijania.|
|[CSplitterWnd::CreateStatic](#createstatic)|Wywołanie utworzenia statycznego okna rozdzielacza i dołączenie go do `CSplitterWnd` obiektu.|
|[CSplitterWnd::CreateView](#createview)|Wywołanie, aby utworzyć okienko w oknie rozdzielacza.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Usuwa kolumnę z okna rozdzielacza.|
|[CSplitterWnd::DeleteRow](#deleterow)|Usuwa wiersz z okna rozdzielacza.|
|[CSplitterWnd::DeleteView](#deleteview)|Usuwa widok z okna rozdzielacza.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Wykonuje polecenie podziału klawiatury, zwykle "Podział okna".|
|[CSplitterWnd::DoScroll](#doscroll)|Wykonuje zsynchronizowane przewijanie podzielonych okien.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Przewija podzielone okna przez daną liczbę pikseli.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Zwraca bieżącą liczbę kolumn okienka.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Zwraca informacje w określonej kolumnie.|
|[CSplitterWnd::GetPane](#getpane)|Zwraca okienko w określonym wierszu i kolumnie.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Zwraca bieżącą liczbę wierszy okienka.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Zwraca informacje w określonym wierszu.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Zwraca styl udostępnionego paska przewijania.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Zwraca identyfikator okna podrzędnego okienka w określonym wierszu i kolumnie.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Wywołanie, aby ustalić, czy okno jest obecnie okienko podrzędne tego okna rozdzielacza.|
|[CSplitterWnd::IsTracking](#istracking)|Określa, czy pasek rozdzielacza jest obecnie przenoszony.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Wywołanie ponownego wykańczania okna rozdzielacza po dostosowaniu rozmiaru wiersza lub kolumny.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Ustawia okienko aktywne w ramce.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Wywołanie, aby ustawić określone informacje o kolumnie.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Wywołanie, aby ustawić określone informacje o wierszu.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Określa nowy styl paska przewijania dla udostępnionej obsługi paska przewijania okna rozdzielacza.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Wskazuje, gdzie okno ramki dzieli się pionowo.|
|[CSplitterWnd::SplitRow](#splitrow)|Wskazuje, gdzie okno ramki dzieli się poziomo.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Wywoływana przez strukturę do rysowania okna rozdzielacza.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Renderuje obraz podzielonego okna.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Renderuje obraz podzielonego okna o tym samym rozmiarze i kształcie co okno ramki.|

## <a name="remarks"></a>Uwagi

Okienko jest zwykle obiektem specyficznym dla aplikacji pochodzącym z [CView](../../mfc/reference/cview-class.md), ale może to być dowolny obiekt [CWnd,](../../mfc/reference/cwnd-class.md) który ma odpowiedni identyfikator okna podrzędnego.

Obiekt `CSplitterWnd` jest zwykle osadzony w nadrzędnym [obiekcie CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd.](../../mfc/reference/cmdichildwnd-class.md) Utwórz `CSplitterWnd` obiekt, wykonując następujące czynności:

1. Osadź zmienną `CSplitterWnd` elementu członkowskiego w ramce nadrzędnej.

2. Zastąp [cframewnodd ramki nadrzędnej::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcji elementu członkowskiego.

3. `OnCreateClient`Z poziomu zastąpionego wywołaj funkcję elementu członkowskiego `CSplitterWnd` [Utwórz](#create) lub [UtwórzStatyczną](#createstatic) .

Wywołanie `Create` funkcji elementu członkowskiego, aby utworzyć okno podziału dynamicznego. Dynamiczne okno rozdzielacza jest zwykle używane do tworzenia i przewijania liczby pojedynczych okienek lub widoków tego samego dokumentu. Struktura automatycznie tworzy okienko początkowe dla rozdzielacza; następnie struktura tworzy, rozmiar i usuwa dodatkowe okienka, jak użytkownik obsługuje formanty okna rozdzielacza.

Podczas wywoływania `Create`określa się minimalną wysokość wiersza i szerokość kolumny, które określają, kiedy okienka są zbyt małe, aby były w pełni wyświetlane. Po wywołaniu `Create`, można dostosować te minimum, wywołując Funkcje członkowskie [SetColumnInfo](#setcolumninfo) i [SetRowInfo.](#setrowinfo)

Użyj również `SetColumnInfo` `SetRowInfo` funkcji i prętów, aby ustawić "idealną" szerokość dla kolumny i "idealną" wysokość dla rzędu. Gdy struktura wyświetla okno rozdzielacza, najpierw wyświetla ramkę nadrzędną, a następnie okno rozdzielacza. Struktura następnie układa okienka w kolumnach i wierszach zgodnie z ich własnymi wymiarami, pracując od lewego górnego do prawego dolnego rogu obszaru klienta okna rozdzielacza.

Wszystkie okienka w oknie rozdzielacza dynamicznego muszą być tej samej klasy. Znane aplikacje obsługujące dynamiczne rozdzielacz okien obejmują programy Microsoft Word i Microsoft Excel.

Funkcja `CreateStatic` elementu członkowskiego służy do tworzenia statycznego okna rozdzielacza. Użytkownik może zmienić tylko rozmiar okienek w statycznym oknie rozdzielacza, a nie ich numer lub kolejność.

Podczas tworzenia podziału statycznego należy w szczególności utworzyć wszystkie okienka podziału statycznego. Upewnij się, że wszystkie okienka przed `OnCreateClient` zwraca funkcję elementu członkowskiego ramki nadrzędnej lub struktura nie wyświetli okna poprawnie.

Funkcja `CreateStatic` elementu członkowskiego automatycznie inicjuje rozdzielacz statyczny o minimalnej wysokości wiersza i szerokości kolumny 0. Po wywołaniu `Create`, dostosować te minimum, wywołując [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) funkcji członkowskich. Należy `SetColumnInfo` również `SetRowInfo` użyć `CreateStatic` i po wywołaniu, aby wskazać żądane idealne wymiary okienka.

Poszczególne okienka rozdzielacza statycznego często należą do różnych klas. Przykłady okien podziału statycznego można znaleźć w edytorze grafiki i Menedżerze plików systemu Windows.

Okno rozdzielacza obsługuje specjalne paski przewijania (oprócz pasków przewijania, które mogą mieć okienka). Te paski przewijania `CSplitterWnd` są częściami podrzędnymi obiektu i są współużytkowane w okienkach.

Te specjalne paski przewijania są tworzone podczas tworzenia okna rozdzielacza. Na przykład, `CSplitterWnd` który ma jeden wiersz, dwie kolumny i styl WS_VSCROLL wyświetli pionowy pasek przewijania, który jest współużytkowane przez dwa okienka. Gdy użytkownik przesuwa pasek przewijania, WM_VSCROLL wiadomości są wysyłane do obu okienek. Gdy okienka ustawiają pozycję paska przewijania, zostanie ustawiony udostępniony pasek przewijania.

Aby uzyskać więcej informacji na temat okien rozdzielacza, zobacz [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md).

Aby uzyskać więcej informacji na temat tworzenia okien rozdzielacza dynamicznego, zobacz:

- Przykład MFC [Bazgroły](../../overview/visual-cpp-samples.md)

- Przykład MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::ActivateNext

Wywoływane przez strukturę do wykonywania następnego okienka lub poprzedniego okienka polecenia.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev (niem.*<br/>
Wskazuje, które okno ma być aktywowane. **PRAWDA** dla poprzedniego; **FAŁSZ** dla następnego.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest poleceniem wysokiego poziomu, które `CSplitterWnd` jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do implementacji.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNastępna

Wywoływane przez platformę, aby sprawdzić, czy następne okienko lub poprzednie okienko polecenia jest obecnie możliwe.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev (niem.*<br/>
Wskazuje, które okno ma być aktywowane. **PRAWDA** dla poprzedniego; **FAŁSZ** dla następnego.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest poleceniem wysokiego poziomu, które `CSplitterWnd` jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do implementacji.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd::Tworzenie

Aby utworzyć okno podziału dynamicznego, należy wywołać `Create` funkcję elementu członkowskiego.

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
Okno ramki nadrzędnej okna rozdzielacza.

*nMaxRows ( nMaxRows )*<br/>
Maksymalna liczba wierszy w oknie rozdzielacza. Wartość ta nie może przekraczać 2.

*nMaxCols*<br/>
Maksymalna liczba kolumn w oknie rozdzielacza. Wartość ta nie może przekraczać 2.

*sizeMin*<br/>
Określa minimalny rozmiar, w którym może być wyświetlane okienko.

*Pcontext*<br/>
Wskaźnik do [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) struktury. W większości przypadków może to być *pContext* przekazywane do okna ramki nadrzędnej.

*Dwstyle*<br/>
Określa styl okna.

*Nid*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone wewnątrz innego okna rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można osadzić `CSplitterWnd` w nadrzędnym [obiekcie CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd,](../../mfc/reference/cmdichildwnd-class.md) wykonując następujące kroki:

1. Osadź zmienną `CSplitterWnd` elementu członkowskiego w ramce nadrzędnej.

1. Zastąp [cframewnodd ramki nadrzędnej::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcji elementu członkowskiego.

1. Wywołanie `Create` funkcji elementu członkowskiego z `OnCreateClient`poziomu nadpisanych .

Podczas tworzenia okna rozdzielacza z wewnątrz ramki nadrzędnej należy przekazać parametr *pContext* ramki nadrzędnej do okna rozdzielacza. W przeciwnym razie ten parametr może mieć wartość NULL.

Początkowa minimalna wysokość wiersza i szerokość kolumny dynamicznego okna rozdzielacza są ustawiane przez parametr *sizeMin.* Te wartości minimalne, które określają, czy okienko jest zbyt małe, aby można było pokazać w całości, można zmienić za pomocą funkcji elementów członkowskich [SetRowInfo](#setrowinfo) i [SetColumnInfo.](#setcolumninfo)

Aby uzyskać więcej informacji na temat dynamicznych okien rozdzielacza, zobacz "Rozdzielacz systemu Windows" w artykule [Wiele typów dokumentów, widoków i ramek okna](../../mfc/multiple-document-types-views-and-frame-windows.md), Uwaga [techniczna 29](../../mfc/tn029-splitter-windows.md)i omówienie `CSplitterWnd` klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl

Wywoływana przez platformę do tworzenia udostępnionego paska przewijania formantu.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Określa styl okna.

*Nid*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone wewnątrz innego okna rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Zastąd, `CreateScrollBarCtrl` aby dołączyć dodatkowe kontrolki obok paska przewijania. Domyślnym zachowaniem jest tworzenie normalnych formantów paska przewijania systemu Windows.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd::CreateStatic

Aby utworzyć okno podziału statycznego, `CreateStatic` należy wywołać funkcję elementu członkowskiego.

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
Okno ramki nadrzędnej okna rozdzielacza.

*Nrows*<br/>
Liczba wierszy. Wartość ta nie może przekraczać 16.

*nKosy*<br/>
Liczba kolumn Wartość ta nie może przekraczać 16.

*Dwstyle*<br/>
Określa styl okna.

*Nid*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone wewnątrz innego okna rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

A `CSplitterWnd` jest zwykle osadzony `CFrameWnd` w obiekcie nadrzędnym lub [CMDIChildWnd,](../../mfc/reference/cmdichildwnd-class.md) wykonując następujące kroki:

1. Osadź zmienną `CSplitterWnd` elementu członkowskiego w ramce nadrzędnej.

1. Zastąpokaj funkcję `OnCreateClient` elementu członkowskiego ramki nadrzędnej.

1. Wywołanie `CreateStatic` funkcji elementu członkowskiego z poziomu nadpisanych [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Okno podziału statycznego zawiera stałą liczbę okienek, często z różnych klas.

Podczas tworzenia okna podziału statycznego należy jednocześnie utworzyć wszystkie jego okienka. [CreateView](#createview) funkcji elementu członkowskiego jest zwykle używany w tym celu, ale można utworzyć inne klasy nonview, jak również.

Początkowa minimalna wysokość wiersza i szerokość kolumny dla statycznego okna rozdzielacza wynosi 0. Te wartości minimalne, które określają, kiedy okienko jest zbyt małe, aby można było je pokazać w całości, można zmienić za pomocą funkcji elementów członkowskich [SetRowInfo](#setrowinfo) i [SetColumnInfo.](#setcolumninfo)

Aby dodać paski przewijania do statycznego okna rozdzielacza, dodaj style WS_HSCROLL i WS_VSCROLL do *dwStyle*.

Zobacz "Rozdzielacz systemu Windows" w artykule [Wiele typów dokumentów, widoków i ramek Okna](../../mfc/multiple-document-types-views-and-frame-windows.md), Uwaga [techniczna 29](../../mfc/tn029-splitter-windows.md)i omówienie `CSplitterWnd` klasy, aby uzyskać więcej informacji na temat statycznych okien rozdzielaczy.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd::CreateView

Tworzy okienka dla statycznego okna rozdzielacza.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz okna rozdzielacza, w którym ma być umieszczany nowy widok.

*Płk*<br/>
Określa kolumnę okna rozdzielacza, w której ma być umieszczany nowy widok.

*pViewClass (Klasa widoków)*<br/>
Określa [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nowego widoku.

*rozmiarJjednost*<br/>
Określa początkowy rozmiar nowego widoku.

*Pcontext*<br/>
Wskaźnik do kontekstu tworzenia używane do tworzenia widoku (zwykle *pContext* przekazywane do ramki nadrzędnej nadpisane [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) funkcji elementu członkowskiego, w którym jest tworzone okno podziału).

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie okienka okna podziału statycznego muszą zostać utworzone, zanim struktura wyświetli rozdzielacz.

Struktura wywołuje również tę funkcję elementu członkowskiego, aby utworzyć nowe okienka, gdy użytkownik okna podziału dynamicznego dzieli okienko, wiersz lub kolumnę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd

Wywołanie do `CSplitterWnd` konstruowania obiektu.

```
CSplitterWnd();
```

### <a name="remarks"></a>Uwagi

Konstruuj `CSplitterWnd` obiekt w dwóch krokach. Najpierw wywołać konstruktora, `CSplitterWnd` który tworzy obiekt, a następnie [wywołać Create](#create) funkcji elementu członkowskiego, który tworzy okno rozdzielacza i dołącza go do `CSplitterWnd` obiektu.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteColumn

Usuwa kolumnę z okna rozdzielacza.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Określa kolumnę, która ma zostać usunięta.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do implementacji logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować, wraz z wirtualną funkcją [CreateView,](#createview)aby zaimplementować bardziej zaawansowane dynamiczne rozdzielaczy.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow

Usuwa wiersz z okna rozdzielacza.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*rowDelete*<br/>
Określa wiersz do usunięcia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do implementacji logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować, wraz z wirtualną funkcją [CreateView,](#createview)aby zaimplementować bardziej zaawansowane dynamiczne rozdzielaczy.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DeleteView

Usuwa widok z okna rozdzielacza.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz okna rozdzielacza, w którym ma być usuwany widok.

*Płk*<br/>
Określa kolumnę okna rozdzielacza, w której ma być usuwany widok.

### <a name="remarks"></a>Uwagi

Jeśli aktywny widok jest usuwany, następny widok stanie się aktywny. Domyślna implementacja zakłada, że widok zostanie automatycznie usunięty w [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Ta funkcja elementu członkowskiego jest wywoływana przez platformę do implementacji logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować, wraz z wirtualną funkcją [CreateView,](#createview)aby zaimplementować bardziej zaawansowane dynamiczne rozdzielaczy.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit

Wykonuje polecenie podziału klawiatury, zwykle "Podział okna".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest poleceniem wysokiego poziomu, które `CSplitterWnd` jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do implementacji.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll

Wykonuje zsynchronizowane przewijanie podzielonych okien.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi przewijająca wiadomość.

*nScrollCode (Kod dostępu do NScrollCode)*<br/>
Kod kreskowy przewijania, który wskazuje żądanie przewijania użytkownika. Ten parametr składa się z dwóch części: bajtu niskiego rzędu, który określa typ przewijania występującego w poziomie oraz bajtu wysokiego rzędu, który określa typ przewijania występującego w pionie:

- SB_BOTTOM Przewiń do dołu.

- SB_LINEDOWN przewija jeden wiersz w dół.

- SB_LINEUP Przewija jedną linię w górę.

- SB_PAGEDOWN przewija jedną stronę w dół.

- SB_PAGEUP przewija jedną stronę w górę.

- SB_TOP Przewija się do góry.

*Bdoscroll*<br/>
Określa, czy występuje określona akcja przewijania. Jeśli *bDoScroll* jest TRUE (to jest, jeśli istnieje okno podrzędne i jeśli podzielone okna mają zakres przewijania), a następnie określona akcja przewijania może mieć miejsce; jeśli *bDoScroll* jest FALSE (oznacza to, że jeśli nie istnieje okno podrzędne lub widoki podziału nie mają zakresu przewijania), przewijanie nie występuje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli występuje zsynchronizowane przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę do wykonywania zsynchronizowanego przewijania podzielonych okien, gdy widok odbiera komunikat przewijania. Zastąpuj, aby wymagać akcji przez użytkownika, zanim zsynchronizowane przewijanie jest dozwolone.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy

Przewija podzielone okna przez daną liczbę pikseli.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi przewijająca wiadomość.

*rozmiarScroll*<br/>
Liczba pikseli do przewijania w poziomie i w pionie.

*Bdoscroll*<br/>
Określa, czy występuje określona akcja przewijania. Jeśli *bDoScroll* jest TRUE (to jest, jeśli istnieje okno podrzędne i jeśli podzielone okna mają zakres przewijania), a następnie określona akcja przewijania może mieć miejsce; jeśli *bDoScroll* jest FALSE (oznacza to, że jeśli nie istnieje okno podrzędne lub widoki podziału nie mają zakresu przewijania), przewijanie nie występuje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli występuje zsynchronizowane przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę w odpowiedzi na komunikat przewijania, aby wykonać zsynchronizowane przewijanie podzielonych okien przez ilość, w pikselach, wskazywanych przez *sizeScroll*. Wartości dodatnie wskazują przewijanie w dół i w prawo; wartości ujemne wskazują przewijanie w górę i w lewo.

Zastąpuj, aby wymagać akcji przez użytkownika przed zezwoleniem na przewijanie.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane

Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pRow (pRow)*<br/>
Wskaźnik do **int,** aby pobrać numer wiersza aktywnego okienka.

*pCol (właso)*<br/>
Wskaźnik do **int,** aby pobrać numer kolumny aktywnego okienka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okienka. NULL, jeśli nie istnieje aktywne okienko.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę, aby określić aktywne okienko w oknie rozdzielacza. Zastądń, aby wymagać akcji przez użytkownika przed uzyskaniem aktywnego okienka.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount

Zwraca bieżącą liczbę kolumn okienka.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę kolumn w rozdzielaczu. W przypadku rozdzielacza statycznego będzie to również maksymalna liczba kolumn.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo

Zwraca informacje w określonej kolumnie.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*Płk*<br/>
Określa kolumnę.

*cxCur (polski)*<br/>
Odwołanie do **int, które** ma być ustawione na bieżącą szerokość kolumny.

*cxMin (polski)*<br/>
Odwołanie do **int, które** ma być ustawione na bieżącą minimalną szerokość kolumny.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane

Zwraca okienko w określonym wierszu i kolumnie.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz.

*Płk*<br/>
Określa kolumnę.

### <a name="return-value"></a>Wartość zwracana

Zwraca okienko w określonym wierszu i kolumnie. Zwrócone okienko jest zwykle [CView](../../mfc/reference/cview-class.md)-pochodna klasy.

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount

Zwraca bieżącą liczbę wierszy okienka.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę wierszy w oknie rozdzielacza. W przypadku okna podziału statycznego będzie to również maksymalna liczba wierszy.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo

Zwraca informacje w określonym wierszu.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz.

*cyCur (cyCur)*<br/>
Odwołanie do **int,** które ma być ustawione na bieżącą wysokość wiersza w pikselach.

*cyMin*<br/>
Odwołanie do **int,** które ma być ustawione na bieżącą minimalną wysokość wiersza w pikselach.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby uzyskać informacje o określonym wierszu. Parametr *cyCur* jest wypełniony bieżącą wysokością określonego wiersza, a *cyMin* jest wypełniony minimalną wysokością wiersza.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle

Zwraca styl udostępnionego paska przewijania dla okna rozdzielacza.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Co najmniej jedna z następujących flag w stylu systemu Windows, jeśli zakończy się pomyślnie:

- WS_HSCROLL Jeśli rozdzielacz zarządza obecnie udostępnionymi poziomymi paskami przewijania.

- WS_VSCROLL Jeśli rozdzielacz obecnie zarządza udostępnionymi pionowymi paskami przewijania.

Jeśli zero, okno rozdzielacza nie zarządza obecnie żadnych udostępnionych pasków przewijania.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol

Uzyskuje identyfikator okna podrzędnego dla okienka w określonym wierszu i kolumnie.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz okna rozdzielacza.

*Płk*<br/>
Określa kolumnę okna rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Identyfikator okna podrzędnego okienka.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego służy do tworzenia niewiękjonych widoków jako okienek i może być wywoływana przed istnieniem okienka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd::IsChildPane

Określa, czy *pWnd* jest obecnie okienkiem podrzędnym tego okna rozdzielacza.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu do testowania.

*pRow (pRow)*<br/>
Wskaźnik do **int,** w którym ma być przechowywane numer wiersza.

*pCol (właso)*<br/>
Wskaźnik do **int,** w którym ma być przechowywane numer kolumny.

### <a name="return-value"></a>Wartość zwracana

Jeśli niezerowe, *pWnd* jest obecnie okienkiem podrzędnym tego okna rozdzielacza, a *pRow* i *pCol* są wypełniane położeniem okienka w oknie rozdzielacza. Jeśli *pWnd* nie jest okienkiem podrzędnym tego okna rozdzielacza, zwracana jest 0.

### <a name="remarks"></a>Uwagi

W wersjach programu Visual C++ przed wersją 6.0 funkcja ta została zdefiniowana jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Ta wersja jest teraz przestarzała i nie powinna być używana.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::IsTracking

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy pasek rozdzielacza w oknie jest obecnie przenoszony.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli operacja rozdzielacza jest w toku; w przeciwnym razie 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter

Renderuje obraz podzielonego okna.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia, w którym można rysować. Jeśli *pDC* ma wartość NULL, [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) jest wywoływana przez platformę i nie jest rysowane żadne okno podziału.

*nTyp*<br/>
Wartość `enum ESplitType`, która może być jedną z następujących wartości:

- `splitBox`Pole przeciągania rozdzielacza.

- `splitBar`Pasek wyświetlany między dwoma podzielonymi oknami.

- `splitIntersection`Przecięcie dzielonych okien. Ten element nie zostanie wywołany podczas uruchamiania w systemie Windows 95/98.

- `splitBorder`Obramowanie okna podzielonego.

*Rect*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) określające rozmiar i kształt podzielonych okien.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę do rysowania i określania dokładnych cech okna rozdzielacza. Zastąpić `OnDrawSplitter` dla zaawansowanego dostosowywania obrazów dla różnych składników graficznych okna rozdzielacza. Domyślne obrazy są podobne do rozdzielacza w programie Microsoft Works dla systemu Windows lub microsoft windows 95/98, ponieważ przecięcia pasków rozdzielacza są ze sobą mieszane.

Aby uzyskać więcej informacji na temat dynamicznych okien rozdzielacza, zobacz "Rozdzielacz systemu Windows" w artykule [Wiele typów dokumentów, widoków i ramek okna](../../mfc/multiple-document-types-views-and-frame-windows.md), Uwaga [techniczna 29](../../mfc/tn029-splitter-windows.md)i omówienie `CSplitterWnd` klasy.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker

Renderuje obraz podzielonego okna o tym samym rozmiarze i kształcie co okno ramki.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
Odwołanie do `CRect` obiektu określającego prostokąt śledzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez strukturę podczas zmiany rozmiaru rozdzielaczy. Zastępowanie `OnInvertTracker` zaawansowanego dostosowywania obrazów okna rozdzielacza. Domyślne obrazy są podobne do rozdzielacza w programie Microsoft Works dla systemu Windows lub microsoft windows 95/98, ponieważ przecięcia pasków rozdzielacza są ze sobą mieszane.

Aby uzyskać więcej informacji na temat dynamicznych okien rozdzielacza, zobacz "Rozdzielacz systemu Windows" w artykule [Wiele typów dokumentów, widoków i ramek okna](../../mfc/multiple-document-types-views-and-frame-windows.md), Uwaga [techniczna 29](../../mfc/tn029-splitter-windows.md)i omówienie `CSplitterWnd` klasy.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::RecalcLayout

Wywołanie ponownego wykańczania okna rozdzielacza po dostosowaniu rozmiaru wiersza lub kolumny.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby poprawnie ponownie wyświetlić okno rozdzielacza po dostosowaniu rozmiarów wierszy i kolumn za pomocą funkcji elementów członkowskich [SetRowInfo](#setrowinfo) i [SetColumnInfo.](#setcolumninfo) Jeśli zmienisz rozmiary wierszy i kolumn jako część procesu tworzenia, zanim okno rozdzielacza jest widoczne, nie jest konieczne wywołanie tej funkcji elementu członkowskiego.

Struktura wywołuje tę funkcję elementu członkowskiego za każdym razem, gdy użytkownik zmienić rozmiar okna rozdzielacza lub przenosi podział.

### <a name="example"></a>Przykład

  Zobacz przykład [CSplitterWnd::SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane

Ustawia okienko aktywne w ramce.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Jeśli *pWnd* ma wartość NULL, określa wiersz w okienku, który będzie aktywny.

*Płk*<br/>
Jeśli *pWnd* ma wartość NULL, określa kolumnę w okienku, która będzie aktywna.

*Pwnd*<br/>
Wskaźnik do `CWnd` obiektu. Jeśli null, okienko określone przez *wiersz* i *col* jest ustawiony aktywny. Jeśli nie null, określa okienko, które jest aktywne.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez platformę, aby ustawić okienko jako aktywne, gdy użytkownik zmieni fokus na okienko w oknie ramki. Można jawnie `SetActivePane` wywołać, aby zmienić fokus do określonego widoku.

Określ okienko, udostępniając wiersz i kolumnę **lub** udostępniając *polecenie pWnd*.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo

Wywołanie, aby ustawić określone informacje o kolumnie.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*Płk*<br/>
Określa kolumnę okna rozdzielacza.

*cxIdeal*<br/>
Określa idealną szerokość kolumny okna rozdzielacza w pikselach.

*cxMin (polski)*<br/>
Określa minimalną szerokość kolumny okna rozdzielacza w pikselach.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby ustawić nową minimalną szerokość i idealną szerokość dla kolumny. Minimalna wartość kolumny określa, kiedy kolumna będzie zbyt mała, aby była w pełni wyświetlana.

Gdy struktura wyświetla okno rozdzielacza, układa okienka w kolumnach i wierszach zgodnie z ich własnymi wymiarami, pracując od lewego górnego do prawego dolnego rogu obszaru klienta okna rozdzielacza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo

Wywołanie, aby ustawić określone informacje o wierszu.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*Wiersza*<br/>
Określa wiersz okna rozdzielacza.

*cyIdealny*<br/>
Określa idealną wysokość dla wiersza okna rozdzielacza w pikselach.

*cyMin*<br/>
Określa minimalną wysokość wiersza okna rozdzielacza w pikselach.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji elementu członkowskiego, aby ustawić nową minimalną wysokość i idealną wysokość dla wiersza. Minimalna wartość wiersza określa, kiedy wiersz będzie zbyt mały, aby można było go w pełni wyświetlić.

Gdy struktura wyświetla okno rozdzielacza, układa okienka w kolumnach i wierszach zgodnie z ich własnymi wymiarami, pracując od lewego górnego do prawego dolnego rogu obszaru klienta okna rozdzielacza.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle

Określa nowy styl przewijania dla udostępnionej obsługi paska przewijania okna rozdzielacza.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*Dwstyle*<br/>
Nowy styl przewijania dla udostępnionej obsługi paska przewijania okna rozdzielacza, który może być jedną z następujących wartości:

- WS_HSCROLL Utwórz/pokaż poziome udostępnione paski przewijania.

- WS_VSCROLL Utwórz/pokaż pionowe udostępnione paski przewijania.

### <a name="remarks"></a>Uwagi

Po utworzeniu paska przewijania nie zostanie `SetScrollStyle` on zniszczony, nawet jeśli jest wywoływany bez tego stylu; zamiast tego te paski przewijania są ukryte. Dzięki temu paski przewijania zachować ich stan, nawet jeśli są one ukryte. Po `SetScrollStyle` wywołaniu należy wywołać [RecalcLayout](#recalclayout) dla wszystkich zmian, które mają wejść w życie.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn

Wskazuje, gdzie okno ramki dzieli się pionowo.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxPrzed*<br/>
Pozycja w pikselach, przed którym następuje podział.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana podczas tworzenia okna rozdzielacza pionowego. `SplitColumn`wskazuje domyślną lokalizację, w której występuje podział.

`SplitColumn`jest wywoływana przez platformę do implementacji logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować, wraz z wirtualną funkcją [CreateView,](#createview)aby zaimplementować bardziej zaawansowane dynamiczne rozdzielaczy.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow

Wskazuje, gdzie okno ramki dzieli się poziomo.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyBefore*<br/>
Pozycja w pikselach, przed którym następuje podział.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana podczas tworzenia okna rozdzielacza poziomego. `SplitRow`wskazuje domyślną lokalizację, w której występuje podział.

`SplitRow`jest wywoływana przez platformę do implementacji logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować, wraz z wirtualną funkcją [CreateView,](#createview)aby zaimplementować bardziej zaawansowane dynamiczne rozdzielaczy.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd::OnDraw

Wywoływana przez strukturę do rysowania okna rozdzielacza.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Przykładowy viewex MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
