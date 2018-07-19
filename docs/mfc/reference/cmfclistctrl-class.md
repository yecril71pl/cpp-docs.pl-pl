---
title: Klasa CMFCListCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04eccb2d1472afb1c04daac8ab23c2ce6fe97c58
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851448"
---
# <a name="cmfclistctrl-class"></a>Klasa CMFCListCtrl
`CMFCListCtrl` Klasa rozszerza funkcjonalność [klasie CListCtrl](../../mfc/reference/clistctrl-class.md) klasy dzięki obsłudze zaawansowanych funkcji kontroli nagłówka z [klasa CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umożliwia oznaczanie kolumna posortowanego z inny kolor tła.|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza tryb wielu sortowania.|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Zwraca odwołanie do formantu nagłówka podkreślony.|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Sprawdza, czy kontrolka listy występuje w wielu Tryb sortowania.|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Wywoływane przez platformę, gdy jej należy porównać dwa elementy kontrolki listy.|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Wywoływane przez platformę, gdy należy określić, kolor tła pojedyncze komórki.|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Wywoływane przez platformę, gdy musi uzyskać czcionki dla komórki rysowania.|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Wywoływane przez platformę, gdy należy określić, kolor tekstu pojedyncze komórki.|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa kolumnę sortowania z listy posortowane kolumny.|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Ustawia bieżąca kolumna posortowanego i porządek sortowania.|  
|[CMFCListCtrl::Sort](#sort)|Sortuje kontrolki listy.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCListCtrl` oferuje dwa ulepszenia [klasie CListCtrl](../../mfc/reference/clistctrl-class.md) klasy. Po pierwsze wskazuje, że sortowanie kolumn jest dostępną opcją za pomocą automatycznie rysowania strzałką ikona sortowania w nagłówku. Po drugie obsługuje sortowanie na wiele kolumn, w tym samym czasie danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCListCtrl` klasy. W przykładzie pokazano, jak utworzenie kontrolki listy kolumn do wstawienia, wstawić elementów, Ustaw tekst elementu i ustawić czcionkę kontrolki listy. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxlistctrl.h  
  
##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn  
 Oznacza posortowane kolumny z inny kolor tła.  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bMark*  
 Parametrów logiczny, który określa, czy włączyć inny kolor tła.  
  
 [in] *bRedraw*  
 Parametrów logiczny, który określa, czy należy niezwłocznie odświeżyć formantu.  
  
### <a name="remarks"></a>Uwagi  
 `EnableMarkSortedColumn` używa metody `CDrawingManager::PixelAlpha` do obliczania, jaki kolor ma być używany dla sortowane kolumny. Kolor wybrany opiera się na kolor tła regularne.  
  
##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort  
 Włącza funkcję sortowania wierszy danych w formancie listy według wielu kolumn.  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *bWłączenie*  
 Wartość logiczna określająca, czy włączyć tryb sortowanie wielu kolumn.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu sortowania oparte na wielu kolumnach kolumny ma hierarchii. Wiersze danych zostaną najpierw posortowane według kolumny podstawowego. Wszelkie wartości równoważne są posortowane według każdej kolejnej kolumny, na podstawie priorytetu.  
  
##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl  
 Zwraca odwołanie do formantu nagłówka.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bazowej [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Kontrolki nagłówka kontrolki listy jest oknem, które zawiera tytuły kolumn. Zazwyczaj znajduje się bezpośrednio nad kolumn.  
  
##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort  
 Sprawdza, czy kontrolka listy obecnie obsługuje sortowanie wielu kolumn.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli kontrolka listy obsługuje sortowanie wielu; Wartość FALSE w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) obsługuje sortowanie wielu pozwala użytkownikowi sortować dane w kontrolce listy według wielu kolumn. Aby włączyć sortowanie wielu, należy wywołać [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).  
  
##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems  
 Struktura wywołuje tę metodę do porównywania dwóch elementów.  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lParam1*  
 Pierwszy element do porównania.  
  
 [in] *lParam2*  
 Drugi element do porównania.  
  
 [in] *iColumn*  
 Indeks kolumny, która jest sortowanie tej metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, która wskazuje względne położenie tych elementów. Wartość ujemna wskazuje, że pierwszy element powinien poprzedzać drugi, dodatnią wartość wskazuje, że pierwszy element powinien być zgodny z drugiego, a wartość zero oznacza, że dwa elementy są równoważne.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zawsze zwraca wartość 0. Musisz przesłonić tę funkcję, aby zapewnić algorytmu sortowania.  
  
##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor  
 Struktura wywołuje tę metodę, gdy należy określić, kolor tła pojedyncze komórki.  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRow*  
 Wiersz w komórce.  
  
 [in] *nColumn*  
 Kolumna w komórce.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość COLOREF, która określa kolor tła komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja klasy `OnGetCellBkColor` nie używa podane parametry wejściowe, a zamiast tego po prostu wywołuje widok `GetBkColor`. Domyślnie formant całej listy będzie więc ten sam kolor tła. Można zastąpić `OnGetCellBkColor` w klasie pochodnej, aby oznaczyć pojedyncze komórki z kolorem tła oddzielne.  
  
##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont  
 Struktura wywołuje tę metodę podczas uzyskiwania czcionkę pojedyncze komórki.  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRow*  
 Wiersz w komórce.  
  
 [in] *nColumn*  
 Kolumna w komórce.  
  
 [in] *dwData*  
 Dane zdefiniowane przez użytkownika. Domyślna implementacja nie używać tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do czcionki używanej do bieżącej komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zwraca wartość NULL. Wszystkie komórki w formancie listy mają tę samą czcionkę. Zastępuje tę metodę, aby zapewnić różne czcionki dla różnych komórek.  
  
##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor  
 Struktura wywołuje tę metodę, gdy należy określić, kolor tekstu pojedyncze komórki.  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *nRow*  
 Wiersz w komórce.  
  
 [in] *nColumn*  
 Kolumna w komórce.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość COLOREF, która określa kolor tekstu komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda wywołuje `GetTextColor` niezależnie od tego, parametry wejściowe. Kontrolka listy całego mają ten sam kolor tekstu. Można zastąpić `OnGetCellTextColor` w klasie pochodnej, aby oznaczyć pojedyncze komórki z kolorem tekstu oddzielne.  
  
##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn  
 Usuwa kolumnę sortowania z listy posortowane kolumny.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Kolumny do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa kolumnę sortowania w formancie nagłówka. Wywołuje [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).  
  
##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn  
 Ustawia bieżąca kolumna posortowanego i porządek sortowania.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Kolumna sortowania.  
  
 [in] *bAscending*  
 Wartość logiczna, która określa kolejność sortowania.  
  
 [in] *bDodaj*  
 Wartość logiczna określająca, czy metoda dodaje kolumnę wskazywanym przez *iColumn* do listy kolumn sortowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przekazuje parametry wejściowe do formantu nagłówka przy użyciu metody [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).  
  
##  <a name="sort"></a>  CMFCListCtrl::Sort  
 Sortuje kontrolki listy.  
  
```  
virtual void Sort(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iColumn*  
 Kolumna sortowania.  
  
 [in] *bAscending*  
 Wartość logiczna, która określa kolejność sortowania.  
  
 [in] *bDodaj*  
 Wartość logiczna określająca, czy metoda ta umożliwia dodanie kolumny wskazywanym przez *iColumn* do listy kolumn sortowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
