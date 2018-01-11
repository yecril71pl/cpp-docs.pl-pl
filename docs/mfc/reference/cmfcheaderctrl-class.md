---
title: Klasa CMFCHeaderCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d3b8b95b161704d5d5b2ca56e22cfe818e4785d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcheaderctrl-class"></a>Klasa CMFCHeaderCtrl
`CMFCHeaderCtrl` Klasa obsługuje sortowanie wiele kolumn w formancie nagłówka.  
  
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
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Włącza lub wyłącza *wielu sortowanie kolumn* tryb dla bieżącego formantu nagłówka.|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Wskazuje, czy kolumna nie jest posortowana, czy są posortowane w kolejności rosnącej lub malejącej.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Pobiera liczony od zera indeks pierwszego kolumna posortowana w formancie nagłówka.|  
|`CMFCHeaderCtrl::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Wskazuje, czy wszystkie kolumny w formancie nagłówka jest sortowany w kolejności rosnącej.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Wskazuje, czy okno nadrzędne bieżącego formantu nagłówka jest okno dialogowe.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Wskazuje, czy bieżący formantu nagłówka jest *wielu sortowanie kolumn* tryb.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Usuwa określonej kolumny z listy kolumn, sortowania.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Określa porządek sortowania dla określonej kolumny w formancie nagłówka.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Wywoływane przez platformę, by narysować kontrolki nagłówek kolumny.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Wywoływane przez platformę, by narysować strzałkę sortowania.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Wywoływane przez platformę, by wypełnienia tła formantu nagłówka kolumny.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCHeaderCtrl` klasy i jak włączyć *wielu sortowanie kolumn* tryb dla bieżącego formantu nagłówka.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Uwagi  
 `CMFCHeaderCtrl` Klasy Rysuje strzałkę sortowania w nagłówek kolumny formantu, aby wskazać, że będzie sortowana kolumna. Użyj *wielu sortowania kolumn* tryb, jeśli zestaw kolumn w formancie listy nadrzędnej ( [CMFCListCtrl klasy](../../mfc/reference/cmfclistctrl-class.md)) mogą być sortowane w tym samym czasie.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl  
 Konstruuje `CMFCHeaderCtrl` obiektu.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten konstruktor inicjuje następujące zmienne Członkowskie do określonych wartości:  
  
|Zmiennej członkowskiej|Wartość|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort  
 Włącza lub wyłącza *wielu sortowanie kolumn* tryb dla bieżącego formantu nagłówka.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć tryb sortowania kolumny wielu; `FALSE` wyłączyć tryb sortowania kolumny wiele i usunąć kolumn z listy sortowanej kolumny. Wartość domyślna to `TRUE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby włączyć lub wyłączyć wielu Tryb sortowania kolumny. Dwie lub więcej kolumn mogą uczestniczyć w sortowania, jeśli formant nagłówka znajduje się wiele Tryb sortowania kolumny.  
  
##  <a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState  
 Wskazuje, czy kolumna jest posortowany lub są posortowane w kolejności rosnącej lub malejącej.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iColumn`  
 Liczony od zera indeks kolumny.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która wskazuje stan sortowania dla określonej kolumny. W poniższej tabeli przedstawiono możliwe wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|-1|Posortowane w kolejności malejącej.|  
|0|Nie jest posortowana.|  
|1|Posortowane w kolejności rosnącej.|  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn  
 Pobiera liczony od zera indeks pierwszego kolumna posortowana w formancie nagłówka.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks sortowanej kolumny lub wartość -1 w przypadku nieznalezienia nie sortowanej kolumny.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku formantu nagłówka *wielu sortowania kolumn* tryb i skompilować aplikację w trybie debugowania, ta metoda potwierdzeń i informacją o tym, aby użyć [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) metody zamiast tego. Jeśli formantu nagłówka wielu Tryb sortowania kolumny i skompilować aplikację w trybie sprzedaży detalicznej, ta metoda zwraca wartość -1.  
  
##  <a name="isascending"></a>CMFCHeaderCtrl::IsAscending  
 Wskazuje, czy wszystkie kolumny w formancie nagłówka jest sortowany w kolejności rosnącej.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli wszystkie kolumny w formancie nagłówka jest posortowane w kolejności rosnącej kolejności; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wartość jest używana Aby wyświetlić strzałkę odpowiedniego sortowania w elemencie formantu nagłówka. Użyj [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) metodę, aby ustawić kolejność sortowania.  
  
##  <a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl  
 Wskazuje, czy okno nadrzędne bieżącego formantu nagłówka jest okno dialogowe.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli okno nadrzędne bieżącego formantu nagłówka to okno dialogowe; w przeciwnym razie `FALSE`.  
  
##  <a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort  
 Wskazuje, czy bieżący formantu nagłówka jest *wielu sortowanie kolumn* tryb.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli włączono tryb sortowania kolumny wielu; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) metody, aby włączyć lub wyłączyć wielu Tryb sortowania kolumny. Dwie lub więcej kolumn mogą uczestniczyć w sortowania, jeśli formant nagłówka znajduje się wiele Tryb sortowania kolumny.  
  
##  <a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem  
 Wywoływane przez platformę, by narysować kontrolki nagłówek kolumny.  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`iItem`  
 Liczony od zera indeks elementu do rysowania.  
  
 [in]`rect`  
 Prostokąt ograniczający element do rysowania.  
  
 [in]`bIsPressed`  
 `TRUE`do rysowania elementu w stan naciśnięcia; w przeciwnym razie `FALSE`.  
  
 [in]`bIsHighlighted`  
 `TRUE`do rysowania elementu w stanie wyróżnione; w przeciwnym razie `FALSE`.  
  
##  <a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow  
 Wywoływane przez platformę, by narysować strzałkę sortowania.  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
 [in]`rectArrow`  
 Prostokąt ograniczający strzałkę sortowania.  
  
##  <a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground  
 Wywoływane przez platformę, by wypełnienia tła formantu nagłówka kolumny.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Wskaźnik do kontekstu urządzenia.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn  
 Usuwa określonej kolumny z listy kolumn, sortowania.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iColumn`  
 Liczony od zera indeks kolumny do usunięcia.  
  
##  <a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn  
 Określa porządek sortowania dla określonej kolumny w formancie nagłówka.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iColumn`  
 Liczony od zera indeks kolumny formantu nagłówka. Jeśli ten parametr jest mniejsza od zera, ta metoda usuwa wszystkie kolumny z listy kolumn, sortowania.  
  
 [in]`bAscending`  
 Określa porządek sortowania kolumny, która `iColumn` określa parametr. `TRUE`Aby ustawić rosnąco; `FALSE` można ustawić w kolejności malejącej. Wartość domyślna to `TRUE`.  
  
 [in]`bAdd`  
 `TRUE`Aby ustawić kolejność sortowania kolumny `iColumn` określa parametr.  
  
 W przypadku bieżącego formantu nagłówka *wielu sortowanie kolumn* tryb, ta metoda dodaje określonej kolumny do listy kolumn, sortowania. Użyj [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) można ustawić wiele Tryb sortowania kolumny.  
  
 Jeśli nie ustawiono wiele Tryb sortowania kolumny, a ta metoda jest skompilowana w trybie debugowania, potwierdza tej metody. Jeśli nie ustawiono wiele Tryb sortowania kolumny i ta metoda jest skompilowana w trybie sprzedaży detalicznej, ta metoda najpierw usuwa wszystkie kolumny z listy kolumn, sortowania, a następnie dodanie określonej kolumny do listy.  
  
 `FALSE`Aby najpierw usunąć wszystkie kolumny z listy kolumn, sortowania, a następnie dodaj określonej kolumny do listy. Wartość domyślna to `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby ustawić kolejność sortowania kolumny. Jeśli to konieczne, ta metoda dodaje kolumnę do listy kolumn, sortowania. Formant nagłówka używa kolejność sortowania do rysowania sortowania Strzałka w górę lub w dół.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)
