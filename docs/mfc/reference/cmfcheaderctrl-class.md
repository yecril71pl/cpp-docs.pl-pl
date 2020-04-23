---
title: Klasa CMFCHeaderCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 5140d02c5acbbc430c3b4d175da1933c79c702b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752353"
---
# <a name="cmfcheaderctrl-class"></a>Klasa CMFCHeaderCtrl

Klasa `CMFCHeaderCtrl` obsługuje sortowanie wielu kolumn w formancie nagłówka.

## <a name="syntax"></a>Składnia

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Konstruuje `CMFCHeaderCtrl` obiekt.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza lub wyłącza tryb *sortowania wielu kolumn* dla bieżącego formantu nagłówka.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Wskazuje, czy kolumna nie jest sortowana, czy jest sortowana w kolejności rosnącej lub malejącej.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Pobiera indeks od zera pierwszej kolumny posortowane w formancie nagłówka.|
|`CMFCHeaderCtrl::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Wskazuje, czy dowolna kolumna w formancie nagłówka jest sortowana w porządku rosnącym.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Wskazuje, czy okno nadrzędne bieżącego formantu nagłówka jest oknem dialogowym.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Wskazuje, czy bieżący kontrolka nagłówka jest w trybie *sortowania wielu kolumn.*|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa określoną kolumnę z listy kolumn sortowania.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Ustawia kolejność sortowania określonej kolumny w formancie nagłówka.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Wywoływane przez strukturę, aby narysować kolumnę formantu nagłówka.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Wywoływana przez strukturę, aby narysować strzałkę sortowania.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Wywoływane przez strukturę, aby wypełnić tło kolumny formantu nagłówka.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCHeaderCtrl` skonstruować obiekt klasy i jak włączyć tryb *sortowania wielu kolumn* dla bieżącego formantu nagłówka.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Uwagi

Klasa `CMFCHeaderCtrl` rysuje strzałkę sortowania w kolumnie formantu nagłówka, aby wskazać, że kolumna jest sortowana. Użyj trybu *sortowania wielu kolumn,* jeśli zestaw kolumn w formancie listy nadrzędnej [(CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)) można sortować w tym samym czasie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cheaderctrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

Konstruuje `CMFCHeaderCtrl` obiekt.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje następujące zmienne członkowskie do określonych wartości:

|Zmienna elementu członkowskiego|Wartość|
|---------------------|-----------|
|`m_bIsMousePressed`|FAŁSZ|
|`m_bMultipleSort`|FAŁSZ|
|`m_bAscending`|Prawda|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FAŁSZ|
|`m_bIsDlgControl`|FAŁSZ|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort

Włącza lub wyłącza tryb *sortowania wielu kolumn* dla bieżącego formantu nagłówka.

```cpp
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć tryb sortowania wielu kolumn; FALSE, aby wyłączyć tryb sortowania wielu kolumn i usunąć wszystkie kolumny z listy posortowanych kolumn. Wartością domyślną jest PRAWDA.

### <a name="remarks"></a>Uwagi

Ta metoda służy do włączania lub wyłączania trybu sortowania wielu kolumn. Dwie lub więcej kolumn może uczestniczyć w sortowanie, jeśli kontrolka nagłówka jest w trybie sortowania wielu kolumn.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState

Wskazuje, czy kolumna jest niesortowana, czy jest sortowana w kolejności rosnącej lub malejącej.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Indeks od zera kolumny.

### <a name="return-value"></a>Wartość zwracana

Wartość wskazująca stan sortowania określonej kolumny. W poniższej tabeli wymieniono możliwe wartości:

|Wartość|Opis|
|-----------|-----------------|
|-1|Posortowane w porządku malejącym.|
|0|Nie posortowane.|
|1|Posortowane w porządku rosnącym.|

### <a name="remarks"></a>Uwagi

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn

Pobiera indeks od zera pierwszej kolumny posortowane w formancie nagłówka.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks kolumny posortowane lub -1, jeśli nie posortowane kolumny nie jest znaleziony.

### <a name="remarks"></a>Uwagi

Jeśli formant nagłówka jest w trybie *sortowania wielu kolumn* i skompilowano aplikację w trybie debugowania, ta metoda potwierdza i zaleca użycie [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) metody zamiast. Jeśli formant nagłówka jest w trybie sortowania wielu kolumn i skompilowano aplikację w trybie sprzedaży detalicznej, ta metoda zwraca wartość -1.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl::IsAscending

Wskazuje, czy dowolna kolumna w formancie nagłówka jest sortowana w porządku rosnącym.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli dowolna kolumna w formancie nagłówka jest sortowana w porządku rosnącym; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wartość zwracana przez tę metodę jest używana do wyświetlania odpowiedniej strzałki sortowania na elemencie formantu nagłówka. Użyj [METODY CMFCHeaderCtrl::SetSortColumn,](#setsortcolumn) aby ustawić kolejność sortowania.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl

Wskazuje, czy okno nadrzędne bieżącego formantu nagłówka jest oknem dialogowym.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno nadrzędne bieżącego formantu nagłówka jest oknem dialogowym; w przeciwnym razie FALSE.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort

Wskazuje, czy bieżący kontrolka nagłówka jest w trybie *sortowania wielu kolumn.*

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli włączony jest tryb sortowania wielu kolumn; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) metody, aby włączyć lub wyłączyć tryb sortowania wielu kolumn. Dwie lub więcej kolumn może uczestniczyć w sortowanie, jeśli kontrolka nagłówka jest w trybie sortowania wielu kolumn.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem

Wywoływane przez strukturę, aby narysować kolumnę formantu nagłówka.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*Iitem*<br/>
[w] Indeks od zera elementu do rysowania.

*Rect*<br/>
[w] Prostokąt ograniczający elementu do narysowania.

*bIsPressed (Jest onspressed)*<br/>
[w] PRAWDA, aby narysować element w stanie naciśnięcia; w przeciwnym razie FALSE.

*bIsSwyżkowany*<br/>
[w] PRAWDA, aby narysować element w podświetlanym stanie; w przeciwnym razie FALSE.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow

Wywoływana przez strukturę, aby narysować strzałkę sortowania.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

*reectArrow (rectArrow)*<br/>
[w] Prostokąt ograniczający strzałki sortowania.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground

Wywoływane przez strukturę, aby wypełnić tło kolumny formantu nagłówka.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn

Usuwa określoną kolumnę z listy kolumn sortowania.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Indeks od zera kolumny do usunięcia.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn

Ustawia kolejność sortowania określonej kolumny w formancie nagłówka.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Indeks od zera kolumny formantu nagłówka. Jeśli ten parametr jest mniejszy niż zero, ta metoda usuwa wszystkie kolumny z listy kolumn sortowania.

*bZdjęcie*<br/>
[w] Określa kolejność sortowania kolumny określonej przez parametr *iColumn.* PRAWDA, aby ustawić rosnącą kolejność; FALSE, aby ustawić malejącą kolejność. Wartością domyślną jest PRAWDA.

*Bdodaj*<br/>
[w] PRAWDA, aby ustawić kolejność sortowania kolumny określonej przez parametr *iColumn.*

Jeśli bieżący formant nagłówka jest w trybie *sortowania wielu kolumn,* ta metoda dodaje określoną kolumnę do listy kolumn sortowania. Użyj [CMFCHeaderCtrl::EnableMultipleSort,](#enablemultiplesort) aby ustawić tryb sortowania wielu kolumn.

Jeśli tryb sortowania wielu kolumn nie jest ustawiony i ta metoda jest kompilowana w trybie debugowania, ta metoda potwierdza. Jeśli tryb sortowania wielu kolumn nie jest ustawiony i ta metoda jest kompilowana w trybie sprzedaży detalicznej, ta metoda najpierw usuwa wszystkie kolumny z listy kolumn sortowania, a następnie dodaje określoną kolumnę do listy.

FAŁSZ, aby najpierw usunąć wszystkie kolumny z listy kolumn sortowania, a następnie dodać określoną kolumnę do listy. Wartością domyślną jest FAŁSZ.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania kolejności sortowania kolumny. W razie potrzeby ta metoda dodaje kolumnę do listy kolumn sortowania. Formant nagłówka używa kolejności sortowania do rysowania strzałki sortowania, która wskazuje w górę lub w dół.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)
