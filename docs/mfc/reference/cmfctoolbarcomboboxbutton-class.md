---
title: Klasa CMFCToolBarComboBoxButton | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c7732d58c8e37683f670f6f13bb4df5f49e4ef24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Klasa CMFCToolBarComboBoxButton
Przycisk paska narzędzi, który zawiera kontrolki pola kombi ( [ccombobox — klasa](../../mfc/reference/ccombobox-class.md)).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Konstruuje `CMFCToolBarComboBoxButton`.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Dodaje element na końcu listy pola kombi.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Dodaje element do listy pola kombi. Kolejność elementów na liście jest określona przez `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Porównuje dwa elementy. Wywołuje się, aby posortować elementy `AddSortedItems` dodaje do listy pola kombi.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Tworzy nowy formant edycji dla przycisku pola kombi.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Usuwa element z listy pola kombi.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Zwraca indeks element zawierający określony ciąg.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Zwraca wskaźnik do przycisku pole kombi z identyfikatorem określonego polecenia.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Zwraca wskaźnik do kontrolki pola kombi osadzonym w przycisk pola kombi.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Zwraca liczbę elementów w pole kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Wyszukuje pole kombi pole przycisku, który ma identyfikator określonego polecenia. Zwraca liczbę elementów w pole kombi pole listy tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Zwraca indeks wybranego elementu w pole kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Pole kombi umożliwia znalezienie pole przycisku, który zawiera polecenie o określonym identyfikatorze i zwraca indeks wybranego elementu w pole kombi pole listy tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Zwraca wskaźnik do formantu edycji, który jest osadzony w przycisk pola kombi.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Zwraca ciąg, który jest skojarzony z określonym indeksem w pole kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Pole kombi umożliwia znalezienie pole przycisku, który zawiera polecenie o określonym identyfikatorze i zwraca ciąg, który jest skojarzony z indeksem w polu kombi przycisku.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Zwraca 32-bitową wartość skojarzoną z określonym indeksem w pole kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Pole kombi umożliwia znalezienie pole przycisku, który zawiera polecenie o określonym identyfikatorze i zwraca 32-bitową wartość skojarzoną z indeksem w polu kombi przycisku.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Wyszukuje pole kombi pole przycisku, który ma identyfikator określonego polecenia. Pobiera 32-bitową wartość, która jest skojarzona indeksu w polu kombi przycisk i zwraca 32-bitową wartość jako wskaźnik.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Zwraca tekst w formancie edycyjnym pola kombi.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Pole kombi umożliwia znalezienie pole przycisku, który zawiera polecenie o określonym identyfikatorze i zwraca tekst w formancie edycyjnym przycisku.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Określa, czy przyciski pole kombi w aplikacji są wyśrodkowane czy wyrównane do górnej krawędzi paska narzędzi.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski pole kombi w aplikacji ma wygląd płaski.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy na liście pole i edytować kontrolki pola kombi.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Wybiera element w polu kombi zgodnie z jego indeks, 32-bitową wartość lub ciąg, a następnie powiadamia o wybranym kontrolki pola kombi.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Wyszukuje pole kombi pole przycisku, który ma identyfikator określonego polecenia. Wywołania `SelectItem` do wybierania elementu w polu kombi przycisku zgodnie z jego ciągu, indeksu lub 32-bitową wartość.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Określa, czy przyciski pole kombi w aplikacji są wyśrodkowane w pionie lub wyrównane do górnej krawędzi paska narzędzi.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy rozwijanej.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Określa, czy przyciski pole kombi w aplikacji ma wygląd płaski.|  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać przycisk pola kombi na pasku narzędzi, wykonaj następujące kroki:  
  
 1. Zarezerwować Identyfikatora fikcyjnego zasobu dla przycisku w zasobie nadrzędnym paska narzędzi.  
  
 2. Utworzyć `CMFCToolBarComboBoxButton` obiektu.  
  
 3. Programu obsługi wiadomości, który przetwarza `AFX_WM_RESETTOOLBAR` komunikatów, Zastąp fikcyjny przycisk Nowy przycisk pole kombi za pomocą [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Na przykład przycisku paska narzędzi pole kombi zobacz przykładowy projekt VisualStudioDemo.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia różnych metod w `CMFCToolBarComboBoxButton` klasy. W przykładzie przedstawiono sposób włączyć pola edycji i kombi, Ustaw przyciski pole kombi położenie w pionie w aplikacji, ustawić wysokości pola listy, gdy jest rozwijana, ustaw płaski wygląd przycisków pole kombi w aplikacji i Ustaw tekst w polu edycji w pole kombi przycisk pola. Następujący fragment kodu jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 Dołącza unikatowy element do listy.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszItem`  
 Tekst elementu do dodania do listy.  
  
 [in]`dwData`  
 Dane skojarzone z elementem można dodać do listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatniego elementu w polu listy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie należy używać w stylu okno Lista jest sortowana.  
  
 Jeśli tekst elementu jest już na liście, nowe dane są przechowywane wraz istniejący element. Wyszukaj element uwzględnia wielkość liter.  
  
##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 Dodaje element do listy w kolejności określonej przez [porównania](#compare) metody.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszItem`  
 Tekst elementu do dodania do listy.  
  
 [in]`dwData`  
 Dane skojarzone z elementem można dodać do listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu, który został dodany do listy.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby dodać elementy do listy w określonej kolejności.  
  
##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 Wskazuje, czy można zmienić rozmiar przycisku pola kombi.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE`.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Konstruuje [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) obiektu.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiID`  
 Identyfikator polecenia przycisku Nowy.  
  
 [in]`iImage`  
 Indeks obrazu skojarzonego z przycisku nowego obrazu.  
  
 [in]`dwStyle`  
 Styl przycisku Nowy.  
  
 [in]`iWidth`  
 Szerokość w pikselach przycisku Nowy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna szerokość to 150 pikseli.  
  
 Lista stylów przycisków paska narzędzi [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 Usuwa dane zdefiniowane przez użytkownika.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Przesłania tę metodę w klasie pochodnej, jeśli chcesz usunąć wszystkie dane zdefiniowane przez użytkownika.  
  
##  <a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 Porównuje dwa ciągi.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszItem1`  
 Pierwszy ciąg do porównania.  
  
 [in]`lpszItem2`  
 Drugi ciąg do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która wskazuje wielkość liter lexicographic relacji między ciągi. W poniższej tabeli przedstawiono możliwe wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|\<0|Pierwszy ciąg jest mniejszy od drugiego.|  
|0|Pierwszy ciąg jest równe drugiego.|  
|>0|Pierwszy ciąg jest większy niż drugi.|  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby zmienić sposób sortowania elementów w polu listy.  
  
 Porównanie jest rozróżniana wielkość liter.  
  
 Ta metoda jest wywoływana tylko z [AddSortedItem](#addsorteditem) metody.  
  
##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 Kopiuje określony stan `CMFCToolBarComboBoxButton` jak bieżący obiekt.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
 Źródło `CMFCToolBarComboBoxButton` obiektu.  
  
##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 Tworzy nowe pole kombi dla przycisku pola kombi.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego pola kombi, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL`.  
  
##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 Tworzy nowe pole edycji dla przycisku pola kombi.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający nowego pola edycji.  
  
 [in]`dwEditStyle`  
 Styl formantu nowe pola edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego pola edycji, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę, podczas tworzenia nowego pola edycji dla przycisku pola kombi. Przesłonić tę metodę, aby zmienić sposób [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) jest tworzony.  
  
##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 Usuwa określony element z listy.  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iIndex`  
 Liczony od zera indeks elementu do usunięcia.  
  
 [in]`dwData`  
 Dane skojarzone z elementem, który ma zostać usunięty.  
  
 [in]`lpszText`  
 Tekst elementu do usunięcia. Jeśli istnieje wiele elementów z tego samego tekstu, pierwszy element zostanie usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli element został się i pomyślnie usunięto; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 Dane zdefiniowane przez użytkownika duplikaty.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Należy przesłonić tę metodę w klasie pochodnej, jeśli chcesz skopiować wszystkie dane zdefiniowane przez użytkownika.  
  
##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 Włącza lub wyłącza pola edycji i kombi.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bEnable`  
 `TRUE`Aby włączyć edit- and -kombi pól. `FALSE` wyłączyć pola edycji i kombi.  
  
### <a name="remarks"></a>Uwagi  
 Po wyłączeniu formanty nie stanie się aktywne i nie akceptuje dane wejściowe użytkownika.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 Kopie identyfikator ciągu z tabeli ciągów aplikacji do menu określony za pomocą polecenia przycisk pola kombi.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`menuButton`  
 Odwołanie do przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `TRUE`.  
  
##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 Zwraca indeks pierwszego elementu w polu listy, który zawiera określony ciąg.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszText`  
 Tekst do wyszukania w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu; lub `CB_ERR` Jeśli element nie zostanie znaleziony.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 Pobiera wskaźnik do przycisku pole kombi ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
 [in]`bIsFocus`  
 `TRUE`Aby wyszukać tylko fokus przyciski; `FALSE` do wyszukania wszystkich przycisków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przycisku pole kombi; lub `NULL` Jeżeli nie znaleziono przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 Zwraca wskaźnik do pola kombi w pole kombi przycisk pola.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [ccombobox — klasa](../../mfc/reference/ccombobox-class.md) obiektu, jeśli metoda została pomyślnie; w przeciwnym `NULL`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 Pobiera identyfikator zasobu menu skrótów dla przycisku pola kombi.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu skrótów  
  
##  <a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 Zwraca liczbę elementów w polu listy.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 Pobiera liczbę elementów w polu listy przycisku pole kombi, który ma identyfikator określonego polecenia.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy; w przeciwnym razie `CB_ERR` Jeżeli nie znaleziono przycisku pola kombi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 Pobiera indeks aktualnie zaznaczonego elementu w polu listy.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks aktualnie zaznaczonego elementu w polu listy; lub `CB_ERR` Jeśli nie wybrano elementu.  
  
### <a name="remarks"></a>Uwagi  
 Indeks pola listy jest liczony od zera.  
  
##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 Zwraca indeks aktualnie zaznaczonego elementu w polu listy kombi pole przycisku, który ma identyfikator określonego polecenia.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks aktualnie zaznaczonego elementu w polu listy; w przeciwnym razie `CB_ERR` Jeśli nie wybrano żadnego elementu lub nie znaleziono przycisku pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Indeks pola listy jest liczony od zera.  
  
##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 Zwraca wskaźnik do pola edycji w pole kombi przycisk pola.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pola edycji, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 Zwraca uchwytu okna dla pola kombi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna lub `NULL` Jeśli pole kombi nie jest skojarzony z obiektem okna.  
  
##  <a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 Zwraca ciąg skojarzony z elementem od określonego indeksu w polu listy.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik na ciąg, który jest skojarzony z elementem; w przeciwnym razie `NULL` Jeśli parametr indeks jest nieprawidłowy lub parametr indeksu wynosi -1 i nie ma zaznaczonego elementu w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca ciąg aktualnie wybranego elementu.  
  
##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 Zwraca ciąg skojarzony z elementem od określonego indeksu w polu listy przycisku pole kombi, który ma identyfikator określonego polecenia.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do elementu w ciągu, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL` Jeśli indeks jest nieprawidłowy, przycisk pola kombi nie jest znaleziony, lub jeśli indeks jest wartość -1 i nie ma zaznaczonego elementu w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
 Wartość indeksu,-1 zwraca ciąg aktualnie wybranego elementu.  
  
##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 Zwraca dane skojarzone z elementem pod określonym indeksem w polu listy.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane skojarzone z elementem; lub 0, jeśli element nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranego elementu.  
  
##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 Zwraca dane skojarzone z elementem pod określonym indeksem w polu listy przycisku pole kombi, który ma identyfikator określonego polecenia.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane skojarzone z elementem, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie wartość 0, jeśli określony indeks jest nieprawidłowy lub nie można odnaleźć CB_ERR, jeśli pole kombi polu przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranego elementu.  
  
##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Zwraca dane skojarzone z elementem pod określonym indeksem w polu listy przycisku pole kombi, który ma identyfikator określonego polecenia. Te dane są zwracane jako wskaźnik.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi.  
  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik skojarzone z elementem, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie wartość -1, jeśli wystąpi błąd, lub `NULL` Jeżeli nie znaleziono przycisku pola kombi.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 Zwraca ciąg monitu pole kombi przycisk pola.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg monitu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie jest obecnie zaimplementowana.  
  
##  <a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 Pobiera tekst w polu edycji.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst w polu edycji.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 Pobiera tekst w polu edycji przycisku pole kombi, który ma identyfikator określonego polecenia.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisk pola kombi określone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst w polu edycji, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `NULL`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 Wskazuje, czy pole kombi aktualnie ma fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli pole kombi aktualnie ma fokus; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zwraca również wartość `TRUE` Jeśli wszystkie okna podrzędnego pola kombi aktualnie ma fokus.  
  
##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 Zwraca położenie w pionie przycisków pole kombi w aplikacji.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli jest wyśrodkowywana przycisków; `FALSE` Jeśli przycisków są wyrównane u góry.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 Zwraca płaski wygląd przycisków pole kombi w aplikacji.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli przycisków płaski; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 To domyślne płaski przycisków pola kombi`FALSE.`  
  
##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 Wskazuje, czy określone dojście jest skojarzony z przycisk pola kombi lub jednego z jego elementów podrzędnych.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`hwnd`  
 Uchwyt okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli dojście jest assocated za przycisk pola kombi lub jednej z jego elementów podrzędnych; w przeciwnym razie `FALSE`.  
  
##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 Wskazuje, czy przycisk pola kombi znajduje się na panelu wstążki.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość `FALSE`, co oznacza, że pole kombi przycisk pola nigdy nie jest wyświetlana na panelu wstążki.  
  
##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 Zwraca stan wyświetlania pole kombi przycisk pola.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan widoczności przycisku pola kombi.  
  
##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 Wskazuje, czy przycisk pola kombi przetwarza wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iNotifyCode`  
 Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Określa, czy przycisk pola kombi przetwarza wiadomości.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 Wywoływane przez platformę, by Oblicz rozmiar przycisku.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisk pola kombi.  
  
 [in]`sizeDefault`  
 Rozmiar domyślny przycisk pola kombi.  
  
 [in]`bHorz`  
 Stan dokowania paska narzędzi nadrzędnej. `TRUE`gdy pasek narzędzi jest zadokowany w poziomie i `FALSE` gdy pasek narzędzi jest zadokowany w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `SIZE` struktury zawierającego wymiary pole kombi przycisku w pikselach.  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk pola kombi są wstawiane do nowego paska narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do nowego nadrzędne paska narzędzi.  
  
##  <a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk pola kombi.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWnd`  
 Wskaźnik do okna nadrzędnego przycisku pola kombi.  
  
 [in]`bDelay`  
 Zarezerwowane do użytku w klasie pochodnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda obsługi zdarzeń; w przeciwnym razie `FALSE`.  
  
##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 Wywoływane przez platformę, gdy użytkownik zmieni kolor narzędzi nadrzędny można ustawić kolor przycisku pola kombi.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisk pola kombi.  
  
 [in]`nCtlColor`  
 Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do pędzel używany przez platformę do rysowania tła przycisku pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda także ustawia kolor tekstu przycisku pola kombi.  
  
##  <a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 Wywoływane przez platformę, by narysować przycisk pola kombi przy użyciu określonych stylów i opcje.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`Pdc`  
 Kontekst urządzenia wyświetlającego przycisku.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisku.  
  
 [in]`pImages`  
 Kolekcja obrazów, która jest skojarzona z przyciskiem.  
  
 [in]`bHorz`  
 Stan dokowania paska narzędzi nadrzędnej. `TRUE`gdy pasek narzędzi jest zadokowany w poziomie i `FALSE` gdy pasek narzędzi jest zadokowany w pionie.  
  
 [in]`bCustomizeMode`  
 Określa, czy aplikacja jest w trybie dostosowania.  
  
 [in]`bHighlight`  
 Określa, czy Rysowanie przycisk pola kombi wyróżnione.  
  
 [in]`bDrawBorder`  
 Określa, czy Rysowanie przycisk pola kombi z obramowanie.  
  
 [in]`bGrayDisabledButtons`  
 `TRUE`Rysowanie przyciemnione przyciski wyłączone; `FALSE` do użycia niepełnosprawnych obrazy kolekcji.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Wywoływane przez platformę, by narysować przycisk pola kombi **polecenia** okienku **Dostosuj** okno dialogowe.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pDC`  
 Kontekst urządzenia wyświetlającego przycisk pola kombi.  
  
 [in]`rect`  
 Prostokąt ograniczający przycisk pola kombi.  
  
 [in]`bSelected`  
 `TRUE`Jeśli pole kombi polu przycisk zostanie wybrany; w przeciwnym razie `FALSE`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w pikselach, przycisk pola kombi.  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Wywoływane przez platformę, by ustawić pole kombi czcionki przycisk pola po zmianie czcionki aplikacji.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 Wywoływane przez platformę, by zmienić lokalizację przycisk pola kombi, gdy przesuwa narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 Wywoływane przez platformę, gdy przycisk pola kombi jest ukryte lub wyświetlane.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bShow`  
 Czy mają być wyświetlany przycisk pola kombi.  
  
##  <a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 Wywoływane przez platformę, by zmienić rozmiar przycisku pole kombi, gdy narzędzi nadrzędnego zmienia rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iSize`  
 Szerokość nowy przycisk pola kombi.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Wywoływane przez platformę, gdy użytkownik zmieni etykietka narzędzia dla przycisku pola kombi.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pWndParent`  
 Wskaźnik do okna nadrzędnego przycisk pola kombi.  
  
 [in]`iButtonIndex`  
 Identyfikator przycisk pola kombi.  
  
 [in]`wndToolTip`  
 Etykietka narzędzia do skojarzenia z przycisk pola kombi.  
  
 [in]`str`  
 Tekst wskazówki.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda obsługi zdarzeń; w przeciwnym razie `FALSE`.  
  
##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 Usuwa wszystkie elementy z listy i edytowania pól.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie elementy na liście pole i edytować kontrolki pola kombi.  
  
##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 Wybiera element w polu listy.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy.  
  
 [in]`bNotify`  
 `TRUE`Aby powiadomić przycisk pole kombi wyboru; w przeciwnym razie `FALSE`.  
  
 [in]`dwData`  
 Dane skojarzone z elementu w polu listy.  
  
 [in]`lpszText`  
 Tekst elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 Wybiera element w polu listy przycisku pole kombi, który ma identyfikator określonego polecenia.  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiCmd`  
 Identyfikator polecenia przycisku pole kombi, który zawiera pola listy.  
  
 [in]`iIndex`  
 Liczony od zera indeks elementu w polu listy. Wartość -1 usuwa wszystkie bieżące zaznaczenie w polu listy i czyści pole edycji.  
  
 [in]`dwData`  
 Dane elementu w polu listy.  
  
 [in]`lpszText`  
 Tekst elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 Odczytuje obiekt z archiwum i zapisuje go do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [w, out]`ar`  
 `CArchive` Obiektu do zserializowania.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia w `CArchive` obiektu ustalić, czy ta metoda odczytuje i zapisuje do archiwum.  
  
##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 Wypełnia określony `CAccessibilityData` obiektu przy użyciu danych dostępności z przycisk pola kombi.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`pParent`  
 Okno nadrzędne przycisk pola kombi.  
  
 [out]`data`  
 A `CAccessibilityData` obiekt, który odbiera dane dostępności z przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`Jeśli metoda zakończyło się pomyślnie; w przeciwnym razie `FALSE`.  
  
##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 Ustawia położenie w pionie przycisków pole kombi w aplikacji.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bCenterVert`  
 `TRUE`Aby wyśrodkować przycisk pola kombi na pasku narzędzi; `FALSE` , aby były wyrównane przycisk pola kombi na początku pasku narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie przyciski pola kombi są wyrównane do górnej.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 Ustawia identyfikator zasobu menu skrótów pole kombi przycisk pola.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`uiResID`  
 Identyfikator zasobu menu skrótów  
  
##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 Ustawia wysokość pola listy, gdy jest rozwijana.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nHeight`  
 Wysokość w pikselach pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna wysokość jest 150 pikseli.  
  
##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 Ustawia płaski wygląd przycisków pole kombi w aplikacji.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`bFlat`  
 `TRUE`dla płaski wygląd; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny płaski przycisków pola kombi jest `FALSE`.  
  
##  <a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 Ustawia określony styl pole kombi przycisk pole i ponownie rysuje formantu, jeśli nie zostanie wyłączony.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`nStyle`  
 Bitowe połączenie (lub) style paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Lista stylów przycisków paska narzędzi [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 Ustawia tekst w polu edycji w pole kombi przycisk pola.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszText`  
 Wskaźnik do ciągu, czy zawiera tekst pola edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



