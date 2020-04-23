---
title: Klasa CMFCListCtrl
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 099ec086bd95a1180af4cf5a8f6a9fa7f1d099ea
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754233"
---
# <a name="cmfclistctrl-class"></a>Klasa CMFCListCtrl

Klasa `CMFCListCtrl` rozszerza funkcjonalność klasy [CListCtrl,](../../mfc/reference/clistctrl-class.md) obsługując zaawansowane funkcje sterowania nagłówkiem [klasy CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Składnia

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umożliwia znakowanie posortowanej kolumny innym kolorem tła.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza tryb wielokrotnego sortowania.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Zwraca odwołanie do kontrolki podkreślonego nagłówka.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Sprawdza, czy formant listy jest w trybie wielokrotnego sortowania.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Wywoływana przez platformę, gdy musi porównać dwa elementy kontroli listy.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Wywoływana przez strukturę, gdy musi określić kolor tła pojedynczej komórki.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Wywoływana przez strukturę, gdy musi uzyskać czcionkę dla rysowanej komórki.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Wywoływana przez strukturę, gdy musi określić kolor tekstu pojedynczej komórki.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa kolumnę sortowania z listy posortowanych kolumn.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Ustawia bieżącą posortowane kolumny i kolejność sortowania.|
|[CMFCListCtrl::Sortowanie](#sort)|Sortuje kontrolki listy.|

## <a name="remarks"></a>Uwagi

`CMFCListCtrl`oferuje dwa ulepszenia klasy [CListCtrl.](../../mfc/reference/clistctrl-class.md) Po pierwsze, wskazuje, że sortowanie kolumn jest opcją dostępną, automatycznie rysując strzałkę sortowania w nagłówku. Po drugie obsługuje sortowanie danych na wielu kolumnach w tym samym czasie.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCListCtrl` używać różnych metod w klasie. W przykładzie pokazano, jak utworzyć formant listy, wstawić kolumny, wstawić elementy, ustawić tekst elementu i ustawić czcionkę formantu listy. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Clistctrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlistctrl.h

## <a name="cmfclistctrlenablemarksortedcolumn"></a><a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Oznacza posortowane kolumny innym kolorem tła.

```cpp
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*bMark (mark)*<br/>
[w] Parametr logiczny, który określa, czy włączyć inny kolor tła.

*bRedraw*<br/>
[w] Parametr logiczny, który określa, czy natychmiast przerysować formant.

### <a name="remarks"></a>Uwagi

`EnableMarkSortedColumn`używa tej `CDrawingManager::PixelAlpha` metody do obliczania, jaki kolor ma być używany dla posortowanych kolumn. Wybrany kolor jest oparty na zwykłym kolorze tła.

## <a name="cmfclistctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Umożliwia sortowanie wierszy danych w formancie listy za pomocą wielu kolumn.

```cpp
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] Wartość logiczna określająca, czy włączyć tryb sortowania wielu kolumn.

### <a name="remarks"></a>Uwagi

Po włączeniu sortowania na podstawie wielu kolumn kolumny mają hierarchię. Wiersze danych zostaną najpierw posortowane według kolumny podstawowej. Wszystkie równoważne wartości są następnie sortowane według każdej kolejnej kolumny na podstawie priorytetu.

## <a name="cmfclistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Zwraca odwołanie do formantu nagłówka.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do podstawowego [obiektu CMFCHeaderCtrl.](../../mfc/reference/cmfcheaderctrl-class.md)

### <a name="remarks"></a>Uwagi

Formant nagłówka formantu listy jest oknem zawierającym tytuły kolumn. Zwykle znajduje się bezpośrednio nad kolumnami.

## <a name="cmfclistctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Sprawdza, czy formant listy obsługuje obecnie sortowanie w wielu kolumnach.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli formant listy obsługuje wiele sortowania; FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

Gdy [KLASA CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) obsługuje wiele sortowania, użytkownik może sortować dane w formancie listy za pomocą wielu kolumn. Aby włączyć wielokrotne sortowanie, zadzwoń do [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

## <a name="cmfclistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Struktura wywołuje tę metodę, gdy porównuje dwa elementy.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

*lParam1*<br/>
[w] Pierwszy element do porównania.

*lParam2*<br/>
[w] Drugi element do porównania.

*Icolumn*<br/>
[w] Indeks kolumny, która jest sortowana przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita wskazująca względną pozycję dwóch elementów. Wartość ujemna wskazuje, że pierwszy element powinien poprzedzać drugi, wartość dodatnia wskazuje, że pierwszy element powinien następować po drugim, a zero oznacza, że dwa elementy są równoważne.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zawsze zwraca wartość 0. Zastąd w tej funkcji należy podać własny algorytm sortowania.

## <a name="cmfclistctrlongetcellbkcolor"></a><a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Struktura wywołuje tę metodę, gdy musi określić kolor tła pojedynczej komórki.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow (właz nRow*<br/>
[w] Wiersz danej komórki.

*nKolumn*<br/>
[w] Kolumna danej komórki.

### <a name="return-value"></a>Wartość zwracana

Wartość COLOREF określająca kolor tła komórki.

### <a name="remarks"></a>Uwagi

Domyślna implementacja `OnGetCellBkColor` nie używa podanych parametrów `GetBkColor`wejściowych, a zamiast tego po prostu wywołuje . W związku z tym domyślnie cały formant listy będzie miał ten sam kolor tła. Można zastąpić `OnGetCellBkColor` w klasie pochodnej, aby oznaczyć poszczególne komórki oddzielnym kolorem tła.

## <a name="cmfclistctrlongetcellfont"></a><a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Struktura wywołuje tę metodę, gdy uzyskuje czcionkę dla pojedynczej komórki.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parametry

*nRow (właz nRow*<br/>
[w] Wiersz danej komórki.

*nKolumn*<br/>
[w] Kolumna danej komórki.

*dwData (dane)*<br/>
[w] Dane zdefiniowane przez użytkownika. Domyślna implementacja nie używa tego parametru.

### <a name="return-value"></a>Wartość zwracana

Dojście do czcionki używanej dla bieżącej komórki.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zwraca wartość NULL. Wszystkie komórki w formancie listy mają tę samą czcionkę. Zastądeń tę metodę, aby zapewnić różne czcionki dla różnych komórek.

## <a name="cmfclistctrlongetcelltextcolor"></a><a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Struktura wywołuje tę metodę, gdy musi określić kolor tekstu pojedynczej komórki.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow (właz nRow*<br/>
[w] Wiersz danej komórki.

*nKolumn*<br/>
[w] Kolumna danej komórki.

### <a name="return-value"></a>Wartość zwracana

Wartość COLOREF określająca kolor tekstu komórki.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda `GetTextColor` wywołuje niezależnie od parametrów wejściowych. Formant całej listy będzie miał ten sam kolor tekstu. Można zastąpić `OnGetCellTextColor` w klasie pochodnej, aby oznaczyć poszczególne komórki oddzielnym kolorem tekstu.

## <a name="cmfclistctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Usuwa kolumnę sortowania z listy posortowanych kolumn.

```cpp
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Kolumna do usunięcia.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa kolumnę sortowania z formantu nagłówka. Wywołuje [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

## <a name="cmfclistctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Ustawia bieżącą posortowane kolumny i kolejność sortowania.

```cpp
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Kolumna do sortowania.

*bZdjęcie*<br/>
[w] Wartość logiczna określająca kolejność sortowania.

*Bdodaj*<br/>
[w] Wartość logiczna określająca, czy metoda dodaje kolumnę wskazaną przez *iColumn* do listy kolumn sortowania.

### <a name="remarks"></a>Uwagi

Ta metoda przekazuje parametry wejściowe do formantu nagłówka przy użyciu metody [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

## <a name="cmfclistctrlsort"></a><a name="sort"></a>CMFCListCtrl::Sortowanie

Sortuje kontrolki listy.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*Icolumn*<br/>
[w] Kolumna do sortowania.

*bZdjęcie*<br/>
[w] Wartość logiczna określająca kolejność sortowania.

*Bdodaj*<br/>
[w] Wartość logiczna określająca, czy ta metoda dodaje kolumnę wskazaną przez *iColumn* do listy kolumn sortowania.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
