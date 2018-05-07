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
ms.openlocfilehash: 495bf2a3eab9ceee4ca0bab337d590c1820905e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmfclistctrl-class"></a>Klasa CMFCListCtrl
`CMFCListCtrl` Klasa rozszerza funkcjonalność [clistctrl — klasa](../../mfc/reference/clistctrl-class.md) klasy dzięki obsłudze nagłówka zaawansowane funkcje sterowania [CMFCHeaderCtrl klasy](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Umożliwia oznaczanie sortowanej kolumny z inny kolor tła.|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Umożliwia wielu Tryb sortowania.|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Zwraca odwołanie do formantu nagłówka podkreślony.|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Sprawdza, czy formant listy jest w trybie wielu sortowania.|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Wywoływane przez platformę, gdy należy porównać dwóch elementów kontrolki listy.|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Wywoływane przez platformę, gdy musisz określić kolor tła pojedynczych komórek.|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Wywoływane przez platformę, gdy musi uzyskać czcionkę dla komórki rysowania.|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Wywoływane przez platformę, gdy należy określić kolor tekstu pojedynczych komórek.|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa kolumny sortowania z listy sortowanej kolumny.|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Ustawia bieżący sortowanej kolumny i kolejność sortowania.|  
|[CMFCListCtrl::Sort](#sort)|Sortuje kontrolki listy.|  
  
## <a name="remarks"></a>Uwagi  
 `CMFCListCtrl` oferuje dwa rozszerzenia [clistctrl — klasa](../../mfc/reference/clistctrl-class.md) klasy. Po pierwsze wskazuje, że sortowania kolumn jest dostępną opcją za pomocą automatycznie rysowania strzałkę sortowania w nagłówku. Po drugie obsługuje on dane, sortowanie na wiele kolumn w tym samym czasie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCListCtrl` klasy. W przykładzie przedstawiono sposób tworzenia kontrolki listy kolumn do wstawienia, wstawić elementów, ustawić tekst elementu i ustaw czcionkę kontrolki listy. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
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
 Oznacza sortowanej kolumny za pomocą inny kolor tła.  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bMark`  
 Wartość logiczna parametr, który określa, czy włączyć inny kolor tła.  
  
 [in] `bRedraw`  
 Wartość logiczna parametr, który określa, czy natychmiast odświeżyć formantu.  
  
### <a name="remarks"></a>Uwagi  
 `EnableMarkSortedColumn` używa metody `CDrawingManager::PixelAlpha` do obliczenia, jaki kolor ma być używany dla sortowania kolumn. Kolor pobrane opiera się na kolor tła regularne.  
  
##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort  
 Umożliwia sortowanie wierszy danych w formancie listy według wielu kolumn.  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bEnable`  
 Wartość logiczna określająca, czy włączyć wiele Tryb sortowania kolumny.  
  
### <a name="remarks"></a>Uwagi  
 Po włączeniu sortowania na podstawie wielu kolumn, kolumny ma hierarchię. Wiersze danych zostanie najpierw można sortować według kolumny podstawowego. Odpowiednik wartości są posortowane według każdej kolumny kolejnych na podstawie priorytetu.  
  
##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl  
 Zwraca odwołanie do formantu nagłówka.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do odpowiadającego [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Formant nagłówka formantu listy jest okna zawierającego tytuły kolumn. Zazwyczaj znajduje się bezpośrednio powyżej kolumn.  
  
##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort  
 Sprawdza, czy formant listy obecnie obsługuje sortowanie na wiele kolumn.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE` Jeśli formant listy obsługuje wiele sortowania; `FALSE` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Gdy [klasy CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) obsługuje wiele sortowanie, użytkownik może sortować danych w formancie listy według wielu kolumn. Aby włączyć sortowanie wiele, należy wywołać [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).  
  
##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems  
 Struktura wywołuje tę metodę do porównywania dwóch elementów.  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `lParam1`  
 Pierwszy element do porównania.  
  
 [in] `lParam2`  
 Drugi element do porównania.  
  
 [in] `iColumn`  
 Indeks kolumny, która jest sortowania tej metody.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba całkowita, która określa względne położenie tych elementów. Wartość ujemna wskazuje, że pierwszy element należy poprzedzać drugi dodatnią wartość wskazuje, że pierwszy element należy wykonać, druga i zero oznacza, że dwa elementy są równoważne.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja zawsze zwraca wartość 0. Konieczne jest przesłonięcie tej funkcji w celu zapewnienia algorytm sortowania.  
  
##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor  
 Struktura wywołuje tej metody, gdy musisz określić kolor tła pojedynczych komórek.  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nRow`  
 Wiersz w komórce.  
  
 [in] `nColumn`  
 Kolumna w komórce.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `COLOREF` wartość, która określa kolor tła komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja `OnGetCellBkColor` nie używa podanych parametrów wejściowych, a zamiast tego po prostu wywołuje `GetBkColor`. W związku z tym domyślnie całą listę kontrolka będzie miała ten sam kolor tła. Można zastąpić `OnGetCellBkColor` w klasie pochodnej, aby oznaczyć pojedynczych komórek kolorem tła oddzielne.  
  
##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont  
 Struktura wywołuje tę metodę podczas uzyskiwania czcionkę dla pojedynczych komórek.  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nRow`  
 Wiersz w komórce.  
  
 [in] `nColumn`  
 Kolumna w komórce.  
  
 [in] `dwData`  
 Dane zdefiniowane przez użytkownika. Domyślna implementacja nie korzysta z tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do czcionki używanej do bieżącej komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zwraca `NULL`. Wszystkie komórki w formancie listy mają tę samą czcionkę. Przesłonić tę metodę w celu zapewnienia czcionek dla różnych komórek.  
  
##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor  
 Platformę wywołuje tę metodę, gdy należy określić kolor tekstu pojedynczych komórek.  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `nRow`  
 Wiersz w komórce.  
  
 [in] `nColumn`  
 Kolumna w komórce.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `COLOREF` wartość, która określa kolor tekstu komórki.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda wywołuje `GetTextColor` niezależnie od parametrów wejściowych. Formant listy całego ma ten sam kolor tekstu. Można zastąpić `OnGetCellTextColor` w klasie pochodnej, aby oznaczyć pojedynczych komórek kolorem Separator tekstu.  
  
##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn  
 Usuwa kolumny sortowania z listy sortowanej kolumny.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iColumn`  
 Kolumna usunąć.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda usuwa formantu nagłówka kolumny sortowania. Wywołuje [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).  
  
##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn  
 Ustawia bieżący sortowanej kolumny i kolejność sortowania.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `iColumn`  
 Kolumna sortowania.  
  
 [in] `bAscending`  
 Wartość logiczna, która określa porządek sortowania.  
  
 [in] `bAdd`  
 Wartość logiczna określająca, czy metoda dodaje kolumnę wskazywanym przez `iColumn` do listy kolumn, sortowania.  
  
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
 [in] `iColumn`  
 Kolumna sortowania.  
  
 [in] `bAscending`  
 Wartość logiczna, która określa porządek sortowania.  
  
 [in] `bAdd`  
 Wartość logiczna określająca, czy ta metoda dodaje kolumnę wskazywanym przez `iColumn` do listy kolumn, sortowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CListCtrl](../../mfc/reference/clistctrl-class.md)
