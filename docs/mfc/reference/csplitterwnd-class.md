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
ms.openlocfilehash: 0f6d940ca123483f381231e6d34d98eebe101bf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212387"
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
|[CSplitterWnd:: CSplitterWnd](#csplitterwnd)|Wywołanie metody konstruowania `CSplitterWnd` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd:: ActivateNext](#activatenext)|Wykonuje Następne okienko lub poprzednie okienko.|
|[CSplitterWnd:: CanActivateNext](#canactivatenext)|Sprawdza, czy polecenie Następne okienko lub poprzednie okienko jest obecnie możliwe.|
|[CSplitterWnd:: Create](#create)|Wywołaj, aby utworzyć dynamiczne okno rozdzielacza i dołączyć je do `CSplitterWnd` obiektu.|
|[CSplitterWnd:: CreateScrollBarCtrl](#createscrollbarctrl)|Tworzy współdzieloną kontrolkę paska przewijania.|
|[CSplitterWnd:: IsStatic](#createstatic)|Wywołaj, aby utworzyć statyczne okno rozdzielacza i dołączyć je do `CSplitterWnd` obiektu.|
|[CSplitterWnd:: isView](#createview)|Wywołaj, aby utworzyć okienko w oknie rozdzielacza.|
|[CSplitterWnd::D eleteColumn](#deletecolumn)|Usuwa kolumnę z okna rozdzielacza.|
|[CSplitterWnd::D eleteRow](#deleterow)|Usuwa wiersz z okna rozdzielacza.|
|[CSplitterWnd::D eleteView](#deleteview)|Usuwa widok z okna rozdzielacza.|
|[CSplitterWnd::D oKeyboardSplit](#dokeyboardsplit)|Wykonuje polecenie podziału klawiatury, zwykle "podział okna".|
|[CSplitterWnd::D oScroll](#doscroll)|Wykonuje zsynchronizowane przewijanie okien z podziałem.|
|[CSplitterWnd::D oScrollBy](#doscrollby)|Przewija podzielone okna o daną liczbę pikseli.|
|[CSplitterWnd:: GetActivePane](#getactivepane)|Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.|
|[CSplitterWnd:: GetColumnCount](#getcolumncount)|Zwraca liczbę kolumn bieżącego okienka.|
|[CSplitterWnd:: GetColumnInfo](#getcolumninfo)|Zwraca informacje o określonej kolumnie.|
|[CSplitterWnd:: getokienk](#getpane)|Zwraca okienko w określonym wierszu i kolumnie.|
|[CSplitterWnd:: GetRowCount](#getrowcount)|Zwraca liczbę wierszy bieżącego okienka.|
|[CSplitterWnd:: GetRowInfo](#getrowinfo)|Zwraca informacje w określonym wierszu.|
|[CSplitterWnd:: getscrolls](#getscrollstyle)|Zwraca współużytkowany styl paska przewijania.|
|[CSplitterWnd:: IdFromRowCol](#idfromrowcol)|Zwraca identyfikator okna podrzędnego okienka w określonym wierszu i kolumnie.|
|[CSplitterWnd:: IsChildPane](#ischildpane)|Wywołaj, aby określić, czy okno jest obecnie okienkiem podrzędnym tego okna rozdzielacza.|
|[CSplitterWnd:: istracking](#istracking)|Określa, czy pasek rozdzielacza jest aktualnie przenoszony.|
|[CSplitterWnd:: RecalcLayout](#recalclayout)|Wywołaj, aby ponownie wyświetlić okno rozdzielacza po dopasowaniu rozmiaru wiersza lub kolumny.|
|[CSplitterWnd:: SetActivePane](#setactivepane)|Ustawia okienko jako aktywne w ramce.|
|[CSplitterWnd:: SetColumnInfo](#setcolumninfo)|Wywołaj, aby ustawić określone informacje o kolumnie.|
|[CSplitterWnd:: SetRowInfo](#setrowinfo)|Wywołaj, aby ustawić informacje o określonym wierszu.|
|[CSplitterWnd:: setscrolls](#setscrollstyle)|Określa nowy styl paska przewijania dla współdzielonej obsługi paska przewijania okna rozdzielacza.|
|[CSplitterWnd:: SplitColumn](#splitcolumn)|Wskazuje, gdzie okno ramowe dzieli się pionowo.|
|[CSplitterWnd:: SplitRow](#splitrow)|Wskazuje, gdzie okno ramowe dzieli się poziomo.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CSplitterWnd:: OnDraw](#ondraw)|Wywoływane przez platformę, by narysować okno rozdzielacza.|
|[CSplitterWnd:: OnDrawSplitter](#ondrawsplitter)|Renderuje obraz okna podzielonego.|
|[CSplitterWnd:: OnInvertTracker](#oninverttracker)|Renderuje obraz okna podziału tak samo jak rozmiar i kształt, jak okno ramki.|

## <a name="remarks"></a>Uwagi

Okienko to zwykle obiekt specyficzny dla aplikacji pochodzący z [CView](../../mfc/reference/cview-class.md), ale może to być dowolny obiekt [CWnd](../../mfc/reference/cwnd-class.md) , który ma odpowiedni identyfikator okna podrzędnego.

`CSplitterWnd`Obiekt jest zwykle osadzony w obiekcie nadrzędnym [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) . Utwórz `CSplitterWnd` obiekt, wykonując następujące czynności:

1. Osadź `CSplitterWnd` zmienną członkowską w ramce nadrzędnej.

2. Zastąp funkcję członkowską [obiektu CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) ramki nadrzędnej.

3. W ramach przesłoniętego `OnCreateClient` wywołania funkcji [Create](#create) lub [xmlstatic](#createstatic) członkowskiego elementu `CSplitterWnd` .

Wywołaj `Create` funkcję członkowską, aby utworzyć dynamiczne okno rozdzielacza. Dynamiczne okno rozdzielacza jest zwykle używane do tworzenia i przewijania wielu pojedynczych okienek lub widoków tego samego dokumentu. Struktura automatycznie tworzy początkowe okienko dla rozdzielacza; następnie struktura tworzy, zmienia rozmiar i usuwa dodatkowe okienka, gdy użytkownik będzie operować kontrolkami okna rozdzielacza.

Po wywołaniu należy `Create` określić minimalną wysokość wiersza i szerokość kolumny, która określa, kiedy okienka są za małe, aby były w pełni wyświetlane. Po wywołaniu `Create` , można dostosować te minimum, wywołując funkcje członkowskie [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) .

Używaj również `SetColumnInfo` funkcji i, `SetRowInfo` Aby ustawić "idealny" szerokość kolumny i "idealna" wysokość dla wiersza. Gdy struktura wyświetla okno rozdzielacza, najpierw wyświetla ramkę nadrzędną, a następnie okno rozdzielacza. Struktura następnie układa okienka w kolumnach i wierszach zgodnie z ich idealnymi wymiarami, pracując od lewego górnego rogu obszaru klienckiego okna rozdzielacza.

Wszystkie okienka w dynamicznym oknie rozdzielacza muszą się znajdować w tej samej klasie. Znane aplikacje obsługujące dynamiczne okna rozdzielacza obejmują programy Microsoft Word i Microsoft Excel.

Użyj `CreateStatic` funkcji członkowskiej, aby utworzyć statyczne okno rozdzielacza. Użytkownik może zmienić tylko rozmiar okienek w statycznym oknie rozdzielacza, a nie ich numer lub kolejność.

Podczas tworzenia rozdzielacza statycznego należy jawnie utworzyć wszystkie okienka statycznego rozdzielacza. Upewnij się, że wszystkie okienka zostały utworzone przed `OnCreateClient` zwróceniem przez funkcję elementu członkowskiego ramki nadrzędnej, lub środowisko nie wyświetli prawidłowo okna.

`CreateStatic`Funkcja członkowska automatycznie inicjuje statyczny rozdzielacz o minimalnej wysokości wiersza i szerokości kolumny równej 0. Po wywołaniu `Create` , Dostosuj te minimum przez wywołanie funkcji składowych [SetColumnInfo](#setcolumninfo) i [SetRowInfo](#setrowinfo) . Należy również użyć `SetColumnInfo` i `SetRowInfo` po wywołaniu, `CreateStatic` Aby wskazać żądane wymiary idealnego okienka.

Poszczególne okienka rozdzielacza statycznego często należą do różnych klas. Przykłady statycznych okien rozdzielacza można znaleźć w edytorze grafiki i w Menedżerze plików systemu Windows.

Okno rozdzielacza obsługuje specjalne paski przewijania (poza paskami przewijania, które mogą znajdować się w okienkach). Te paski przewijania są elementami podrzędnymi `CSplitterWnd` obiektu i są współdzielone z okienkami.

Te specjalne paski przewijania są tworzone podczas tworzenia okna rozdzielacza. Na przykład, `CSplitterWnd` który ma jeden wiersz, dwie kolumny i styl WS_VSCROLL będzie wyświetlał pionowy pasek przewijania, który jest współużytkowany przez dwa okienka. Gdy użytkownik przesunie pasek przewijania, WM_VSCROLL komunikaty są wysyłane do obu okienek. Gdy okienka ustawią położenie paska przewijania, zostanie ustawiony współużytkowany pasek przewijania.

Aby uzyskać więcej informacji o rozdzielaczu systemu Windows, zobacz [Uwagi techniczne 29](../../mfc/tn029-splitter-windows.md).

Aby uzyskać więcej informacji na temat tworzenia dynamicznych okien rozdzielacza, zobacz:

- Przykładowy [Bazgroły](../../overview/visual-cpp-samples.md) MFC

- Przykładowa [VIEWEX](../../overview/visual-cpp-samples.md)MFC.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext. h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd:: ActivateNext

Wywoływane przez platformę, by wykonać następne okienko lub poprzednie okienko.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Wskazuje, które okno ma zostać aktywowane. **Wartość true** dla poprzedniego elementu; **Wartość false** dla następnego.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest poleceniem wysokiego poziomu, które jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do `CSplitterWnd` implementacji.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd:: CanActivateNext

Wywoływane przez platformę, aby sprawdzić, czy polecenie Next lub poprzednie okienko jest obecnie możliwe.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parametry

*bPrev*<br/>
Wskazuje, które okno ma zostać aktywowane. **Wartość true** dla poprzedniego elementu; **Wartość false** dla następnego.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest poleceniem wysokiego poziomu, które jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do `CSplitterWnd` implementacji.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd:: Create

Aby utworzyć dynamiczne okno rozdzielacza, wywołaj `Create` funkcję członkowską.

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
Maksymalna liczba wierszy w oknie rozdzielacza. Ta wartość nie może przekraczać 2.

*nMaxCols*<br/>
Maksymalna liczba kolumn w oknie rozdzielacza. Ta wartość nie może przekraczać 2.

*sizeMin*<br/>
Określa minimalny rozmiar wyświetlania okienka.

*pContext*<br/>
Wskaźnik do struktury [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . W większości przypadków może to być *pContext* przekazanie do okna ramki nadrzędnej.

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone w innym oknie rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Można osadzić `CSplitterWnd` obiekt w obiekcie nadrzędnym [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md) lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) , wykonując następujące czynności:

1. Osadź `CSplitterWnd` zmienną członkowską w ramce nadrzędnej.

1. Zastąp funkcję członkowską [obiektu CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) ramki nadrzędnej.

1. Wywołaj `Create` funkcję członkowską z poziomu przesłonięte `OnCreateClient` .

Po utworzeniu okna rozdzielacza z poziomu ramki nadrzędnej, Przekaż parametr *pContext* ramki nadrzędnej do okna rozdzielacza. W przeciwnym razie ten parametr może mieć wartość NULL.

Początkowa minimalna wysokość wiersza i szerokość kolumny dynamicznego okna rozdzielacza są ustawiane za pomocą parametru *sizeMin* . Te minimum, które określają, czy okienko jest zbyt małe, aby było wyświetlane w całości, można je zmienić za pomocą funkcji Członkowskich [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) .

Aby uzyskać więcej informacji na temat dynamicznych rozdzielaczy systemu Windows, zobacz "rozdzielacz systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md)oraz `CSplitterWnd` Przegląd klas.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd:: CreateScrollBarCtrl

Wywoływane przez platformę, aby utworzyć współdzieloną kontrolkę paska przewijania.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone w innym oknie rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Przesłoń `CreateScrollBarCtrl` , aby dołączyć dodatkowe kontrolki obok paska przewijania. Domyślnym zachowaniem jest tworzenie normalnych kontrolek paska przewijania systemu Windows.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd:: IsStatic

Aby utworzyć statyczne okno rozdzielacza, wywołaj `CreateStatic` funkcję członkowską.

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
Liczba kolumn Ta wartość nie może przekraczać 16.

*dwStyle*<br/>
Określa styl okna.

*nID*<br/>
Identyfikator okna podrzędnego okna. Identyfikator może być AFX_IDW_PANE_FIRST, chyba że okno rozdzielacza jest zagnieżdżone w innym oknie rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

A `CSplitterWnd` jest zwykle osadzony w obiekcie nadrzędnym `CFrameWnd` lub [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) , wykonując następujące czynności:

1. Osadź `CSplitterWnd` zmienną członkowską w ramce nadrzędnej.

1. Przesłoń `OnCreateClient` funkcję członkowską ramki nadrzędnej.

1. Wywołaj `CreateStatic` funkcję członkowską z poziomu przesłoniętego [obiektu CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Statyczne okno rozdzielacza zawiera stałą liczbę okienek, często z różnych klas.

Po utworzeniu statycznego okna rozdzielacza należy w tym samym czasie utworzyć wszystkie jego okienka. Funkcja elementu członkowskiego "Create [View](#createview) " jest zwykle używana do tego celu, ale można również utworzyć inne klasy, które nie są wyświetlane.

Początkowa minimalna wysokość wiersza i szerokość kolumny dla statycznego okna rozdzielacza to 0. Te minimum, które określają, kiedy okienko jest zbyt małe, aby było wyświetlane w całości, można je zmienić za pomocą funkcji Członkowskich [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) .

Aby dodać paski przewijania do statycznego okna rozdzielacza, Dodaj WS_HSCROLL i WS_VSCROLL style do *dwStyle*.

Zobacz "rozdzielacz systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md)oraz `CSplitterWnd` Omówienie klasy, aby uzyskać więcej informacji na temat statycznych okien rozdzielacza.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd:: isView

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

*wiersza*<br/>
Określa wiersz okna rozdzielacza, w którym ma zostać umieszczony nowy widok.

*kolumna*<br/>
Określa kolumnę okna rozdzielacza, w której ma zostać umieszczony nowy widok.

*pViewClass*<br/>
Określa [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) nowego widoku.

*sizeInit*<br/>
Określa początkowy rozmiar nowego widoku.

*pContext*<br/>
Wskaźnik do kontekstu tworzenia używany do tworzenia widoku (zazwyczaj *pContext* przesłonięty do [obiektu CFrameWnd](../../mfc/reference/cframewnd-class.md#oncreateclient) ramki nadrzędnej, w którym jest tworzone okno rozdzielacza).

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wszystkie okienka statycznego okna rozdzielacza muszą zostać utworzone przed wyświetleniem rozdzielacza przez strukturę.

Struktura wywołuje również tę funkcję członkowską, aby utworzyć nowe okienka, gdy użytkownik dynamicznego okna rozdzielacza dzieli okienko, wiersz lub kolumnę.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd:: CSplitterWnd

Wywołanie metody konstruowania `CSplitterWnd` obiektu.

```
CSplitterWnd();
```

### <a name="remarks"></a>Uwagi

Utwórz `CSplitterWnd` obiekt w dwóch krokach. Najpierw Wywołaj konstruktora, który tworzy `CSplitterWnd` obiekt, a następnie wywołaj funkcję [Create](#create) member, która tworzy okno rozdzielacza i dołącza go do `CSplitterWnd` obiektu.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::D eleteColumn

Usuwa kolumnę z okna rozdzielacza.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parametry

*colDelete*<br/>
Określa kolumnę, która ma zostać usunięta.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w celu zaimplementowania logiki dynamicznego okna rozdzielacza (oznacza to, że okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować wraz z funkcją wirtualną [isView](#createview), aby zaimplementować bardziej zaawansowane dynamiczne rozdzielacze.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::D eleteRow

Usuwa wiersz z okna rozdzielacza.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parametry

*rowDelete*<br/>
Określa wiersz, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w celu zaimplementowania logiki dynamicznego okna rozdzielacza (oznacza to, że okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować wraz z funkcją wirtualną [isView](#createview), aby zaimplementować bardziej zaawansowane dynamiczne rozdzielacze.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::D eleteView

Usuwa widok z okna rozdzielacza.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Określa wiersz okna rozdzielacza, w którym ma zostać usunięty widok.

*kolumna*<br/>
Określa kolumnę okna rozdzielacza, w której ma zostać usunięty widok.

### <a name="remarks"></a>Uwagi

Jeśli aktywny widok jest usuwany, następny widok stanie się aktywny. Domyślna implementacja zakłada, że widok zostanie usunięty z [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Ta funkcja członkowska jest wywoływana przez platformę w celu zaimplementowania logiki dynamicznego okna rozdzielacza (oznacza to, że okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować wraz z funkcją wirtualną [isView](#createview), aby zaimplementować bardziej zaawansowane dynamiczne rozdzielacze.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::D oKeyboardSplit

Wykonuje polecenie podziału klawiatury, zwykle "podział okna".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest poleceniem wysokiego poziomu, które jest używane przez klasę [CView](../../mfc/reference/cview-class.md) do delegowania do `CSplitterWnd` implementacji.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::D oScroll

Wykonuje zsynchronizowane przewijanie okien z podziałem.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi wiadomość przewijania.

*nScrollCode*<br/>
Kod paska przewijania wskazujący żądanie przewijania użytkownika. Ten parametr składa się z dwóch części: bajt o niskiej kolejności, który określa typ przewijania w poziomie i bajt o dużej kolejności, który określa typ przewijania w pionie:

- SB_BOTTOM przewija do dołu.

- SB_LINEDOWN przewija jeden wiersz w dół.

- SB_LINEUP przewija jeden wiersz w górę.

- SB_PAGEDOWN Przewija jedną stronę w dół.

- SB_PAGEUP Przewija jedną stronę w górę.

- SB_TOP przewija do góry.

*bDoScroll*<br/>
Określa, czy występuje określona akcja przewijania. Jeśli *bDoScroll* ma wartość true (oznacza to, że jeśli istnieje okno podrzędne, a jeśli rozdzielone okna mają zakres przewijania), można wykonać określoną akcję przewijania. Jeśli *bDoScroll* ma wartość false (oznacza to, że jeśli nie istnieje okno podrzędne lub widok podzielony nie ma zakresu przewijania), przewijanie nie następuje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli występuje synchroniczne przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w celu przeprowadzenia zsynchronizowanego przewijania okien podziału, gdy widok odbierze komunikat przewijania. Przesłoń, aby wymagać akcji przez użytkownika przed zezwoleniem na przewijanie zsynchronizowane.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::D oScrollBy

Przewija podzielone okna o daną liczbę pikseli.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parametry

*pViewFrom*<br/>
Wskaźnik do widoku, z którego pochodzi wiadomość przewijania.

*sizeScroll*<br/>
Liczba pikseli, które mają być przewijane w poziomie i w pionie.

*bDoScroll*<br/>
Określa, czy występuje określona akcja przewijania. Jeśli *bDoScroll* ma wartość true (oznacza to, że jeśli istnieje okno podrzędne, a jeśli rozdzielone okna mają zakres przewijania), można wykonać określoną akcję przewijania. Jeśli *bDoScroll* ma wartość false (oznacza to, że jeśli nie istnieje okno podrzędne lub widok podzielony nie ma zakresu przewijania), przewijanie nie następuje.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli występuje synchroniczne przewijanie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w odpowiedzi na komunikat przewijania, aby wykonać zsynchronizowane przewijanie okna podziału przez ilość w pikselach wskazywanych przez *sizeScroll*. Wartości dodatnie oznaczają przewijanie w dół i w prawo; wartości ujemne oznaczają przewijanie w górę i w lewo.

Przesłoń, aby wymagać akcji przez użytkownika przed zezwoleniem na przewijanie.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd:: GetActivePane

Określa aktywne okienko na podstawie fokusu lub aktywnego widoku w ramce.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parametry

*pRow*<br/>
Wskaźnik do elementu **`int`** w celu pobrania numeru wiersza aktywnego okienka.

*pCol*<br/>
Wskaźnik do elementu **`int`** w celu pobrania numeru kolumny aktywnego okienka.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktywnego okienka. Wartość NULL, jeśli nie istnieje aktywne okienko.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę w celu określenia aktywnego okienka w oknie rozdzielacza. Przesłoń, aby wymagać akcji przez użytkownika przed pobraniem aktywnego okienka.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd:: GetColumnCount

Zwraca liczbę kolumn bieżącego okienka.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę kolumn w rozdzielaczu. W przypadku rozdzielacza statycznego będzie to również Maksymalna liczba kolumn.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd:: GetColumnInfo

Zwraca informacje o określonej kolumnie.

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parametry

*kolumna*<br/>
Określa kolumnę.

*cxCur*<br/>
Odwołanie do elementu, **`int`** który ma zostać ustawiony na bieżącą szerokość kolumny.

*cxMin*<br/>
Odwołanie do elementu, **`int`** który ma zostać ustawiony na bieżącą minimalną szerokość kolumny.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd:: getokienk

Zwraca okienko w określonym wierszu i kolumnie.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Określa wiersz.

*kolumna*<br/>
Określa kolumnę.

### <a name="return-value"></a>Wartość zwracana

Zwraca okienko w określonym wierszu i kolumnie. Zwracane okienko jest zwykle klasą pochodną [CView](../../mfc/reference/cview-class.md).

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd:: GetRowCount

Zwraca liczbę wierszy bieżącego okienka.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca bieżącą liczbę wierszy w oknie rozdzielacza. W przypadku statycznego okna rozdzielacza będzie to również Maksymalna liczba wierszy.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd:: GetRowInfo

Zwraca informacje w określonym wierszu.

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Określa wiersz.

*cyCur*<br/>
Odwołanie do, aby **`int`** ustawić na bieżącą wysokość wiersza (w pikselach).

*cyMin*<br/>
Odwołanie do, aby **`int`** ustawić na bieżącą minimalną wysokość wiersza (w pikselach).

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby uzyskać informacje o określonym wierszu. Parametr *cyCur* jest wypełniony bieżącą wysokością określonego wiersza, a *cyMin* jest wypełniony minimalną wysokością wiersza.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd:: getscrolls

Zwraca udostępniony styl paska przewijania okna rozdzielacza.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Wartość zwracana

Jedno lub więcej z następujących flag stylu systemu Windows, jeśli się powiedzie:

- WS_HSCROLL, jeśli rozdzielacz aktualnie zarządza udostępnionymi poziomy paski przewijania.

- WS_VSCROLL, jeśli rozdzielacz aktualnie zarządza udostępnionymi pionowymi paskami przewijania.

Jeśli wartość jest równa zero, okno rozdzielacza nie zarządza obecnie żadnymi udostępnionymi paskami przewijania.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd:: IdFromRowCol

Uzyskuje identyfikator okna podrzędnego dla okienka w określonym wierszu i kolumnie.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Określa wiersz okna rozdzielacza.

*kolumna*<br/>
Określa kolumnę okna rozdzielacza.

### <a name="return-value"></a>Wartość zwracana

Identyfikator okna podrzędnego okienka.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska służy do tworzenia niewidoków jako okienek i może być wywoływana przed istniejącym okienkiem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd:: IsChildPane

Określa, czy *pWnd* jest obecnie okienkiem podrzędnym tego okna rozdzielacza.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Wskaźnik do obiektu [CWnd](../../mfc/reference/cwnd-class.md) do przetestowania.

*pRow*<br/>
Wskaźnik do elementu, **`int`** w którym ma być przechowywany numer wiersza.

*pCol*<br/>
Wskaźnik do elementu, **`int`** w którym ma być przechowywany numer kolumny.

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość jest różna od zera, *pWnd* jest obecnie okienkiem podrzędnym tego okna rozdzielacza, a *PROW* i *pCol* są wypełniane pozycją okienka w oknie rozdzielacza. Jeśli *pWnd* nie jest okienkiem podrzędnym tego okna rozdzielacza, zwracana jest wartość 0.

### <a name="remarks"></a>Uwagi

W wersjach Visual C++ wcześniejszych niż 6,0 funkcja ta została zdefiniowana jako

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Ta wersja jest obecnie przestarzała i nie powinna być używana.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd:: istracking

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy pasek rozdzielacza w oknie jest aktualnie przenoszony.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli operacja rozdzielacza jest w toku; w przeciwnym razie 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd:: OnDrawSplitter

Renderuje obraz okna podzielonego.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskaźnik do kontekstu urządzenia, który ma zostać narysowany. Jeśli *podstawowy kontroler domeny* ma wartość null, wówczas [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) jest wywoływany przez platformę i nie jest rysowane okno podziału.

*Npowiadomienia*<br/>
Wartość `enum ESplitType` , która może być jedną z następujących wartości:

- `splitBox`Pole przeciągania rozdzielacza.

- `splitBar`Pasek, który pojawia się między dwoma rozdzielonymi oknami.

- `splitIntersection`Część wspólna okna podzielonego. Ten element nie zostanie wywołany w przypadku uruchomienia w systemie Windows 95/98.

- `splitBorder`Obramowanie okna podziału.

*cinania*<br/>
Odwołanie do obiektu [CRect](../../atl-mfc-shared/reference/crect-class.md) określającego rozmiar i kształt okna podziału.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę do rysowania i określania dokładnej charakterystyki okna rozdzielacza. Przesłoń `OnDrawSplitter` Zaawansowane dostosowywanie obrazów dla różnych składników graficznych okna rozdzielacza. Domyślny obraz jest podobny do rozdzielacza w programie Microsoft Works dla systemu Windows lub Microsoft Windows 95/98, w tym, że przedziały pasków podziału są połączone razem.

Aby uzyskać więcej informacji na temat dynamicznych rozdzielaczy systemu Windows, zobacz "rozdzielacz systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md)oraz `CSplitterWnd` Przegląd klas.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd:: OnInvertTracker

Renderuje obraz okna podziału tak samo jak rozmiar i kształt, jak okno ramki.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parametry

*cinania*<br/>
Odwołanie do `CRect` obiektu określającego prostokąt śledzenia.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę podczas zmiany rozmiarów rozdzielaczy. Przesłoń `OnInvertTracker` Zaawansowane dostosowywanie obrazów okna rozdzielacza. Domyślny obraz jest podobny do rozdzielacza w programie Microsoft Works dla systemu Windows lub Microsoft Windows 95/98, w tym, że przedziały pasków podziału są połączone razem.

Aby uzyskać więcej informacji na temat dynamicznych rozdzielaczy systemu Windows, zobacz "rozdzielacz systemu Windows" w artykule [wiele typów dokumentów, widoków i okien ramowych](../../mfc/multiple-document-types-views-and-frame-windows.md), [Uwaga techniczna 29](../../mfc/tn029-splitter-windows.md)oraz `CSplitterWnd` Przegląd klas.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd:: RecalcLayout

Wywołaj, aby ponownie wyświetlić okno rozdzielacza po dopasowaniu rozmiaru wiersza lub kolumny.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby prawidłowo ponownie wyświetlić okno rozdzielacza po dopasowaniu rozmiarów wierszy i kolumn za pomocą funkcji składowych [SetRowInfo](#setrowinfo) i [SetColumnInfo](#setcolumninfo) . W przypadku zmiany rozmiarów wierszy i kolumn w ramach procesu tworzenia przed wyświetleniem okna rozdzielacza nie jest konieczne Wywołaj tę funkcję elementu członkowskiego.

Struktura wywołuje tę funkcję elementu członkowskiego za każdym razem, gdy użytkownik zmienia rozmiar okna rozdzielacza lub przenosi podział.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CSplitterWnd:: SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd:: SetActivePane

Ustawia okienko jako aktywne w ramce.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Jeśli *pWnd* ma wartość null, określa wiersz w okienku, który będzie aktywny.

*kolumna*<br/>
Jeśli *pWnd* ma wartość null, określa kolumnę w okienku, która będzie aktywna.

*pWnd*<br/>
Wskaźnik do `CWnd` obiektu. Jeśli wartość jest równa NULL, okienko określone przez *wiersz* i *kolumnę* ma ustawioną wartość aktywne. Jeśli wartość nie jest równa NULL, określa okienko, które jest ustawione jako aktywne.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez platformę, aby ustawić okienko jako aktywne, gdy użytkownik zmieni fokus w okienku w oknie ramek. Można jawnie wywołać, `SetActivePane` Aby zmienić fokus do określonego widoku.

Określ okienko, podając wiersz i kolumnę **lub** dostarczając *pWnd*.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd:: SetColumnInfo

Wywołaj, aby ustawić określone informacje o kolumnie.

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parametry

*kolumna*<br/>
Określa kolumnę okna rozdzielacza.

*cxIdeal*<br/>
Określa idealną szerokość kolumny okna rozdzielacza (w pikselach).

*cxMin*<br/>
Określa minimalną szerokość kolumny okna rozdzielacza (w pikselach).

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nową minimalną szerokość i idealną szerokość kolumny. Minimalna wartość kolumny określa, kiedy kolumna będzie zbyt mała, aby była w pełni wyświetlana.

Gdy struktura wyświetla okno rozdzielacza, układa okienka w kolumnach i wierszach zgodnie z ich idealnymi wymiarami, pracując od lewego górnego rogu obszaru klienckiego okna rozdzielacza.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd:: SetRowInfo

Wywołaj, aby ustawić informacje o określonym wierszu.

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parametry

*wiersza*<br/>
Określa wiersz okna rozdzielacza.

*cyIdeal*<br/>
Określa idealną wysokość wiersza okna rozdzielacza (w pikselach).

*cyMin*<br/>
Określa minimalną wysokość wiersza okna rozdzielacza (w pikselach).

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nową minimalną wysokość i idealną wysokość wiersza. Minimalna wartość wiersza określa, kiedy wiersz będzie zbyt mały, aby był w pełni wyświetlany.

Gdy struktura wyświetla okno rozdzielacza, układa okienka w kolumnach i wierszach zgodnie z ich idealnymi wymiarami, pracując od lewego górnego rogu obszaru klienckiego okna rozdzielacza.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd:: setscrolls

Określa nowy styl przewijania dla współdzielonego paska przewijania okna rozdzielacza.

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Nowy styl przewijania dla współdzielonej obsługi paska przewijania okna rozdzielacza, który może mieć jedną z następujących wartości:

- WS_HSCROLL utworzyć/pokazać poziomy udostępnione paski przewijania.

- WS_VSCROLL utworzyć/pokazać pionowe, udostępnione paski przewijania.

### <a name="remarks"></a>Uwagi

Po utworzeniu paska przewijania nie zostanie on zniszczony, nawet jeśli `SetScrollStyle` jest wywoływany bez tego stylu; zamiast tego paski przewijania są ukryte. Dzięki temu paski przewijania są zachowywane, nawet jeśli są ukryte. Po wywołaniu `SetScrollStyle` należy wywołać [RecalcLayout](#recalclayout) , aby wszystkie zmiany zaczęły obowiązywać.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd:: SplitColumn

Wskazuje, gdzie okno ramowe dzieli się pionowo.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parametry

*cxBefore*<br/>
Pozycja w pikselach, przed którą występuje podział.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana po utworzeniu pionowego okna rozdzielacza. `SplitColumn`wskazuje domyślną lokalizację, w której występuje podział.

`SplitColumn`jest wywoływana przez platformę w celu zaimplementowania logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować wraz z funkcją wirtualną [isView](#createview), aby zaimplementować bardziej zaawansowane dynamiczne rozdzielacze.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd:: SplitRow

Wskazuje, gdzie okno ramowe dzieli się poziomo.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parametry

*cyBefore*<br/>
Pozycja w pikselach, przed którą występuje podział.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana, gdy zostanie utworzone poziome okno podziału. `SplitRow`wskazuje domyślną lokalizację, w której występuje podział.

`SplitRow`jest wywoływana przez platformę w celu zaimplementowania logiki dynamicznego okna rozdzielacza (oznacza to, że jeśli okno rozdzielacza ma styl SPLS_DYNAMIC_SPLIT). Można go dostosować wraz z funkcją wirtualną [isView](#createview), aby zaimplementować bardziej zaawansowane dynamiczne rozdzielacze.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd:: OnDraw

Wywoływane przez platformę, by narysować okno rozdzielacza.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Domeny*<br/>
Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Przykład VIEWEX MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CWnd](../../mfc/reference/cwnd-class.md)
