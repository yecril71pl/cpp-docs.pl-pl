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
ms.openlocfilehash: 10d7dda39223e1d6206d2ede96874d9d546c8776
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538505"
---
# <a name="cmfcheaderctrl-class"></a>Klasa CMFCHeaderCtrl

`CMFCHeaderCtrl` Klasa obsługuje sortowanie wielu kolumn w formancie nagłówka.

## <a name="syntax"></a>Składnia

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Konstruuje `CMFCHeaderCtrl` obiektu.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza lub wyłącza *sortowanie wielu kolumn* tryb dla bieżącego kontrolki nagłówka.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Wskazuje, czy kolumna nie jest sortowana lub są posortowane w kolejności rosnącej lub malejącej.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Pobiera liczony od zera indeks pierwszego kolumna posortowana w formancie nagłówka.|
|`CMFCHeaderCtrl::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Wskazuje, czy dowolną kolumnę w formancie nagłówka jest sortowany w kolejności rosnącej.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Wskazuje, czy okno nadrzędne kontrolki nagłówka bieżące okno dialogowe.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Wskazuje, czy bieżący kontrolki nagłówka znajduje się w *sortowanie wielu kolumn* trybu.|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa określonej kolumny z listy kolumn sortowania.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Ustawia kolejność sortowania określona kolumna w formancie nagłówka.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Metoda wywoływana przez platformę, by narysować nagłówka kolumny kontrolki.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Metoda wywoływana przez platformę, by narysować strzałkę sortowania.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Metoda wywoływana przez platformę, by wypełnienia tła formantu nagłówek kolumny.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCHeaderCtrl` klasy oraz jak włączyć *sortowanie wielu kolumn* tryb dla bieżącego kontrolki nagłówka.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Uwagi

`CMFCHeaderCtrl` Klasy Rysuje strzałkę sortowania w kolumnie kontrolki nagłówka, aby wskazać, czy kolumny są sortowane. Użyj *sortowanie wielu kolumn* trybu, jeśli zestaw kolumn w formancie listy nadrzędnej ( [klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)) mogą być sortowane w tym samym czasie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxheaderctrl.h

##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl

Konstruuje `CMFCHeaderCtrl` obiektu.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje następujące zmienne Członkowskie do określonej wartości:

|Zmienna składowa|Wartość|
|---------------------|-----------|
|`m_bIsMousePressed`|FAŁSZ|
|`m_bMultipleSort`|FAŁSZ|
|`m_bAscending`|WARTOŚĆ TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FAŁSZ|
|`m_bIsDlgControl`|FAŁSZ|
|`m_hFont`|NULL|

##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort

Włącza lub wyłącza *sortowanie wielu kolumn* tryb dla bieżącego kontrolki nagłówka.

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość TRUE, aby włączyć tryb sortowanie wielu kolumn; Wartość FALSE, aby wyłączyć tryb sortowanie wielu kolumn i Usuń wszystkie kolumny z listy posortowane kolumny. Wartość domyślna to TRUE.

### <a name="remarks"></a>Uwagi

Aby włączyć lub wyłączyć tryb sortowanie wielu kolumn, należy użyć tej metody. Co najmniej dwóch kolumn mogą uczestniczyć w sortowania, jeśli kontrolki nagłówka znajduje się w wielu Tryb sortowania kolumn.

##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState

Wskazuje, czy kolumna jest posortowana, czy są posortowane w kolejności rosnącej lub malejącej.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Liczony od zera indeks kolumny.

### <a name="return-value"></a>Wartość zwracana

Wartość, która wskazuje stan sortowania dla określonej kolumny. W poniższej tabeli wymieniono możliwe wartości:

|Wartość|Opis|
|-----------|-----------------|
|-1|Posortowane w kolejności malejącej.|
|0|Nie są sortowane.|
|1|Posortowane w kolejności rosnącej.|

### <a name="remarks"></a>Uwagi

##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn

Pobiera liczony od zera indeks pierwszego kolumna posortowana w formancie nagłówka.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks kolumna posortowanego lub -1, jeśli znajduje się żadna kolumna posortowanego.

### <a name="remarks"></a>Uwagi

Jeśli kontrolki nagłówka znajduje się w *sortowanie wielu kolumn* tryb i skompilowanych aplikacji w trybie debugowania, ta metoda potwierdza i informacją o tym, aby użyć [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) metody zamiast tego. Jeśli kontrolki nagłówka znajduje się w wielu Tryb sortowania kolumn i skompilowano aplikację w trybie sprzedaży detalicznej, ta metoda zwraca wartość -1.

##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending

Wskazuje, czy dowolną kolumnę w formancie nagłówka jest sortowany w kolejności rosnącej.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli wszystkie kolumny w formancie nagłówka jest sortowany w kolejności rosnącej kolejności. w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca wartość służy do wyświetlenia strzałki odpowiedniego sortowania na element kontroli nagłówka. Użyj [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) metodę, aby ustawić kolejność sortowania.

##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl

Wskazuje, czy okno nadrzędne kontrolki nagłówka bieżące okno dialogowe.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to okno nadrzędne kontrolki nagłówka bieżące okno dialogowe; w przeciwnym razie wartość FALSE.

##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort

Wskazuje, czy bieżący kontrolki nagłówka znajduje się w *sortowanie wielu kolumn* trybu.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli jest włączony tryb sortowania kolumn wielu; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Użyj [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) metodę, aby włączyć lub wyłączyć tryb sortowanie wielu kolumn. Co najmniej dwóch kolumn mogą uczestniczyć w sortowania, jeśli kontrolki nagłówka znajduje się w wielu Tryb sortowania kolumn.

##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem

Metoda wywoływana przez platformę, by narysować nagłówka kolumny kontrolki.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*Towaru*<br/>
[in] Liczony od zera indeks elementu do rysowania.

*Rect*<br/>
[in] Element, aby narysować prostokąt otaczający.

*bIsPressed*<br/>
[in] Wartość TRUE, aby rysować element w stan naciśnięcia; w przeciwnym razie wartość FALSE.

*bIsHighlighted*<br/>
[in] Wartość TRUE, aby rysować element w stanie wyróżnione; w przeciwnym razie wartość FALSE.

##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow

Metoda wywoływana przez platformę, by narysować strzałkę sortowania.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.

*rectArrow*<br/>
[in] Prostokąt otaczający strzałkę sortowania.

##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground

Metoda wywoływana przez platformę, by wypełnienia tła formantu nagłówek kolumny.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia.

### <a name="remarks"></a>Uwagi

##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn

Usuwa określonej kolumny z listy kolumn sortowania.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Liczony od zera indeks kolumny do usunięcia.

##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn

Ustawia kolejność sortowania określona kolumna w formancie nagłówka.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
[in] Liczony od zera indeks kolumny kontrolki nagłówka. Jeśli ten parametr jest mniejsza niż zero, ta metoda usuwa wszystkie kolumny z listy kolumn sortowania.

*bAscending*<br/>
[in] Określa porządek sortowania kolumny, która *iColumn* określa parametr. Wartość TRUE, aby ustawić rosnąco; Wartość FALSE, aby ustawić w kolejności malejącej. Wartość domyślna to TRUE.

*bDodaj*<br/>
[in] Wartość true, aby ustawić kolejność sortowania dla kolumny, *iColumn* określa parametr.

Jeśli bieżący kontrolki nagłówka znajduje się w *sortowanie wielu kolumn* tryb, ta metoda dodaje określonej kolumny do listy kolumn sortowania. Użyj [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) można ustawić tryb sortowanie wielu kolumn.

Jeśli nie ustawiono wiele Tryb sortowania kolumn, a ta metoda jest skompilowany w trybie debugowania, ta metoda potwierdza. Jeśli nie ustawiono wiele Tryb sortowania kolumn, ta metoda jest skompilowany w trybie handlu detalicznego tej metody najpierw usuwa wszystkie kolumny z listy kolumn, sortowania, a następnie dodaje określonej kolumny do listy.

Wartość FALSE, najpierw usuń wszystkie kolumny z listy kolumn, sortowania, a następnie dodaj określonej kolumny do listy. Wartość domyślna to FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia Sortuj kolumny. Jeśli to konieczne, ta metoda dodaje kolumnę do listy kolumn sortowania. Kontrolki nagłówka używa kolejności sortowania, aby narysować sortowania Strzałka w górę lub w dół.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)
