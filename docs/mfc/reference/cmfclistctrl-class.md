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
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682345"
---
# <a name="cmfclistctrl-class"></a>Klasa CMFCListCtrl

Klasa rozszerza funkcjonalność klasy [klasy CListCtrl](../../mfc/reference/clistctrl-class.md) przez obsługę funkcji zaawansowanej kontrolki nagłówka [klasy CMFCHeaderCtrl.](../../mfc/reference/cmfcheaderctrl-class.md) `CMFCListCtrl`

## <a name="syntax"></a>Składnia

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umożliwia oznaczenie posortowanej kolumny z innym kolorem tła.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza wiele trybów sortowania.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Zwraca odwołanie do podkreślenia kontrolki nagłówka.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Sprawdza, czy kontrolka listy ma wiele trybu sortowania.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Wywoływane przez platformę, gdy musi on porównać dwa elementy kontrolki listy.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Wywoływane przez platformę, gdy musi określić kolor tła pojedynczej komórki.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Wywoływane przez platformę, gdy musi uzyskać czcionkę rysowanej komórki.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Wywoływane przez platformę, gdy musi określić kolor tekstu pojedynczej komórki.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa kolumnę sortowania z listy posortowanych kolumn.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Ustawia bieżącą posortowaną kolumnę i kolejność sortowania.|
|[CMFCListCtrl::Sort](#sort)|Sortuje formant listy.|

## <a name="remarks"></a>Uwagi

`CMFCListCtrl`oferuje dwa usprawnienia klasy [klasy CListCtrl](../../mfc/reference/clistctrl-class.md) . Najpierw wskazuje, że sortowanie kolumn jest dostępną opcją przez automatyczne rysowanie strzałki sortowania w nagłówku. Ponadto obsługuje sortowanie danych na wielu kolumnach w tym samym czasie.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia różnych metod w `CMFCListCtrl` klasie. W przykładzie pokazano, jak utworzyć kontrolkę listy, wstawić kolumny, wstawić elementy, ustawić tekst elementu i ustawić czcionkę kontrolki listy. Ten fragment kodu jest częścią [przykładu demonstracyjnego Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxlistctrl. h

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Oznacza posortowane kolumny z innym kolorem tła.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parametry

*bMark*<br/>
podczas Parametr logiczny, który określa, czy należy włączyć inny kolor tła.

*bRedraw*<br/>
podczas Parametr logiczny, który określa, czy natychmiast narysować kontrolkę.

### <a name="remarks"></a>Uwagi

`EnableMarkSortedColumn`używa metody `CDrawingManager::PixelAlpha` do obliczenia koloru, który ma być używany dla posortowanych kolumn. Wybrany kolor jest oparty na normalnym kolorze tła.

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Umożliwia sortowanie wierszy danych w kontrolce listy przez wiele kolumn.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas Wartość logiczna określająca, czy ma być włączony tryb sortowania wielu kolumn.

### <a name="remarks"></a>Uwagi

Po włączeniu sortowania na podstawie wielu kolumn kolumny mają hierarchię. Wiersze danych zostaną najpierw posortowane według kolumny podstawowej. Wszelkie równoważne wartości są następnie sortowane według każdej kolejnej kolumny na podstawie priorytetu.

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Zwraca odwołanie do kontrolki nagłówka.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bazowego obiektu [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) .

### <a name="remarks"></a>Uwagi

Formant nagłówka kontrolki listy jest oknem zawierającym tytuły kolumn. Zwykle jest umieszczony bezpośrednio nad kolumnami.

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Sprawdza, czy formant listy obsługuje obecnie sortowanie dla wielu kolumn.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, Jeśli kontrolka listy obsługuje wiele sortowania; W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Gdy [Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) obsługuje wiele sortowania, użytkownik może sortować dane w kontrolce listy według wielu kolumn. Aby włączyć wiele sortowania, wywołaj [CMFCListCtrl:: EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

Struktura wywołuje tę metodę, gdy porównuje dwa elementy.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parametry

*lParam1*<br/>
podczas Pierwszy element do porównania.

*lParam2*<br/>
podczas Drugi element do porównania.

*iColumn*<br/>
podczas Indeks kolumny, która jest sortowana przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która wskazuje względną pozycję dwóch elementów. Wartość ujemna wskazuje, że pierwszy element powinien poprzedzać sekundy, wartość dodatnia wskazuje, że pierwszy element powinien występować po drugim, a zero oznacza, że dwa elementy są równoważne.

### <a name="remarks"></a>Uwagi

Domyślna implementacja zawsze zwraca wartość 0. Zastąp tę funkcję, aby zapewnić własny algorytm sortowania.

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

Struktura wywołuje tę metodę, gdy musi określić kolor tła pojedynczej komórki.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
podczas Wiersz w danej komórce.

*nColumn*<br/>
podczas Kolumna w podanej komórce.

### <a name="return-value"></a>Wartość zwracana

Wartość COLOREF, która określa kolor tła komórki.

### <a name="remarks"></a>Uwagi

Domyślna implementacja programu `OnGetCellBkColor` nie używa dostarczonych parametrów wejściowych, a zamiast tego po prostu wywołuje `GetBkColor`metodę. W związku z tym domyślnie cały formant listy będzie miał ten sam kolor tła. Można przesłonić `OnGetCellBkColor` w klasie pochodnej, aby oznaczyć poszczególne komórki osobnym kolorem tła.

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

Struktura wywołuje tę metodę, gdy pobiera czcionkę pojedynczej komórki.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
podczas Wiersz w danej komórce.

*nColumn*<br/>
podczas Kolumna w podanej komórce.

*dwData*<br/>
podczas Dane zdefiniowane przez użytkownika. Domyślna implementacja nie używa tego parametru.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do czcionki używanej w bieżącej komórce.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zwraca wartość NULL. Wszystkie komórki w kontrolce listy mają tę samą czcionkę. Zastąp tę metodę, aby udostępnić różne czcionki dla różnych komórek.

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

Struktura wywołuje tę metodę, gdy musi określić kolor tekstu pojedynczej komórki.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parametry

*nRow*<br/>
podczas Wiersz w danej komórce.

*nColumn*<br/>
podczas Kolumna w podanej komórce.

### <a name="return-value"></a>Wartość zwracana

Wartość COLOREF, która określa kolor tekstu komórki.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda wywołuje `GetTextColor` niezależnie od parametrów wejściowych. Cała kontrolka listy będzie mieć ten sam kolor tekstu. Można przesłonić `OnGetCellTextColor` w klasie pochodnej, aby oznaczyć poszczególne komórki osobnym kolorem tekstu.

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Usuwa kolumnę sortowania z listy posortowanych kolumn.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
podczas Kolumna, która ma zostać usunięta.

### <a name="remarks"></a>Uwagi

Ta metoda usuwa kolumnę sortowania z kontrolki nagłówek. Wywołuje [CMFCHeaderCtrl:: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Ustawia bieżącą posortowaną kolumnę i kolejność sortowania.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
podczas Kolumna, która ma zostać posortowana.

*bAscending*<br/>
podczas Wartość logiczna określająca kolejność sortowania.

*bDodaj*<br/>
podczas Wartość logiczna określająca, czy Metoda dodaje kolumnę wskazującą *IColumn* do listy kolumn sortowania.

### <a name="remarks"></a>Uwagi

Ta metoda przekazuje parametry wejściowe do kontrolki nagłówka przy użyciu metody [CMFCHeaderCtrl:: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>CMFCListCtrl:: Sort

Sortuje formant listy.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parametry

*iColumn*<br/>
podczas Kolumna, która ma zostać posortowana.

*bAscending*<br/>
podczas Wartość logiczna określająca kolejność sortowania.

*bDodaj*<br/>
podczas Wartość logiczna określająca, czy ta metoda dodaje kolumnę wskazującą *IColumn* do listy kolumn sortowania.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
