---
title: Klasa CMFCToolBarComboBoxButton | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffb17f8f38e83399ec32b792338f818cc06215dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703784"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Klasa CMFCToolBarComboBoxButton
Przycisk paska narzędzi, który zawiera formant pola kombi ( [klasa CComboBox](../../mfc/reference/ccombobox-class.md)).  
  
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
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Dodaje element do końca listy pola kombi.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Dodaje element do listy pola kombi. Kolejność elementów na liście jest określona przez `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Porównuje dwa elementy. Wywołuje się, aby posortować elementy `AddSortedItems` dodaje do listy pola kombi.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Tworzy nową kontrolkę edycji dla przycisku pola kombi.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Usuwa element z listy pola kombi.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Zwraca indeks elementu, który zawiera określonego ciągu.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Zwraca wskaźnik do przycisk pola kombi z identyfikatorem określonego polecenia.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Zwraca wskaźnik do kontrolki pola kombi, który jest osadzony w przycisk pola kombi.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Zwraca liczbę elementów w polu kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia. Zwraca liczbę elementów w polu kombi pole listy tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Zwraca indeks zaznaczonego elementu w polu kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia, a następnie zwraca indeks zaznaczonego elementu w kombi pola listy tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Zwraca wskaźnik do kontrolki edycji, który jest osadzony w przycisk pola kombi.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Zwraca ciąg, który jest skojarzony z określonym indeksem kombi pola listy.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia i zwraca ciąg, który jest skojarzony z indeksem w polu kombi tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Zwraca wartość 32-bitowy, który jest skojarzony z określonym indeksem kombi Lista pól.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia i zwraca wartość 32-bitowych, która jest skojarzona z indeksem w polu kombi tego przycisku.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia. Pobiera wartość 32-bitowy, który jest skojarzony indeksu w polu kombi tego przycisku, a następnie zwraca 32-bitową wartość jako wskaźnik.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Zwraca tekst z pola kombi kontrolki edycji.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Umożliwia znalezienie kombi przycisk pola, ma identyfikator określonego polecenia, która zwraca tekst z kontrolki edycji z tego przycisku.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowany, czy wyrównane do górnej krawędzi paska narzędzi.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy z listy pola i edytować kontrolki pola kombi.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Wybiera element w polu kombi zgodnie z jego indeksu, 32-bitową wartość lub ciąg, a następnie powiadamia formant pola kombi o wybór.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Umożliwia znalezienie kombi przycisk pola, który ma identyfikator określonego polecenia. Wywołania `SelectItem` do wybierania elementu w polu kombi tego przycisku, zgodnie z jego ciągu, indeksu lub 32-bitową wartość.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowane w pionie wyrównane do górnej krawędzi paska narzędzi.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Określa wysokość pola listy rozwijanej.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|  
  
## <a name="remarks"></a>Uwagi  
 Aby dodać przycisk pola kombi na pasku narzędzi, wykonaj następujące kroki:  
  
 1. Zarezerwuj identyfikator zasobu fikcyjnego przycisku w nadrzędnej zasób paska narzędzi.  
  
 2. Konstruowania `CMFCToolBarComboBoxButton` obiektu.  
  
 3. Programu obsługi wiadomości, która przetwarza komunikat AFX_WM_RESETTOOLBAR, Zamień zastępczy przycisk Nowy przycisk pola kombi przy użyciu [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Aby uzyskać więcej informacji, zobacz [wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Na przykład przycisk paska narzędzi pole kombi zobacz przykładowy projekt VisualStudioDemo.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCToolBarComboBoxButton` klasy. W przykładzie pokazano, jak włączyć pola edycji i kombi, ustawić położenie w pionie kombi pola w aplikacji, ustawianie wysokości pola listy, po upuszczeniu go w dół, ustaw płaski wygląd przycisków pola kombi w aplikacji i ustawiać tekst w polu edycji kombi przycisk pola. Ten fragment kodu jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem  
 Dołącza element unikatowe pola listy.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem*<br/>
[in] Tekst elementu do dodania do pola listy.  
  
*dwData*<br/>
[in] Dane skojarzone z elementem można dodać do pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks ostatniego elementu w polu listy.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie należy używać w stylu okno Lista jest posortowana.  
  
 Jeśli tekst elementu jest już w polu listy, nowe dane są przechowywane z istniejącego elementu. Wyszukaj element uwzględnia wielkość liter.  
  
##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem  
 Dodaje element do pola listy w kolejności, który jest definiowany przez [porównania](#compare) metody.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem*<br/>
[in] Tekst elementu do dodania do pola listy.  
  
*dwData*<br/>
[in] Dane skojarzone z elementem można dodać do pola listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu, który został dodany do pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta służy do dodawania elementów do pola listy w określonej kolejności.  
  
##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched  
 Wskazuje, czy można zmienić rozmiar przycisku pola kombi.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Konstruuje [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) obiektu.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
*uiID*<br/>
[in] Identyfikator polecenia nowy przycisk.  
  
*iImage*<br/>
[in] Indeks obrazu obrazu skojarzonego z przycisku Nowy.  
  
*dwStyle*<br/>
[in] Styl przycisku Nowy.  
  
*iWidth*<br/>
[in] Szerokość w pikselach, nowy przycisk.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna szerokość jest 150 pikseli.  
  
 Aby uzyskać listę style przycisku paska narzędzi, zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData  
 Usuwa danych użytkownika.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Przesłonić tę metodę w klasie pochodnej, jeśli chcesz usunąć wszystkie dane zdefiniowane przez użytkownika.  
  
##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare  
 Porównuje dwa ciągi.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Parametry  
*lpszItem1*<br/>
[in] Pierwszy ciąg do porównania.  
  
*lpszItem2*<br/>
[in] Drugi ciąg do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość, która wskazuje wielkość liter leksykograficznych relację między ciągi. W poniższej tabeli wymieniono możliwe wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|\<0|Pierwszy ciąg jest mniejszy od drugiego.|  
|0|Pierwszy ciąg jest równa drugiego.|  
|>0|Pierwszy ciąg jest większy od drugiego.|  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby zmienić sposób sortowania elementów na liście.  
  
 W porównaniu jest uwzględniana wielkość liter.  
  
 Ta metoda jest wywoływana tylko z [AddSortedItem](#addsorteditem) metody.  
  
##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom  
 Kopiuje określony stan `CMFCToolBarComboBoxButton` jak bieżący obiekt.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Źródło `CMFCToolBarComboBoxButton` obiektu.  
  
##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo  
 Tworzy nowe pole kombi na przycisk pola kombi.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego przycisku.  
  
*Rect*<br/>
[in] Prostokąt otaczający pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego pola kombi, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.  
  
##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit  
 Tworzy nowe pole edycji dla przycisku pola kombi.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego przycisku.  
  
*Rect*<br/>
[in] Prostokąt otaczający nowe pola edycji.  
  
*dwEditStyle*<br/>
[in] Styl formantu nowe pola edycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowego pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
 Struktura wywołuje tę metodę podczas tworzenia nowego pola edycji dla przycisku kontrolki pola kombi. Przesłonić tę metodę, aby zmienić sposób [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) zostanie utworzony.  
  
##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem  
 Usuwa określony element z listy rozwijanej.  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Liczony od zera indeks elementu do usunięcia.  
  
*dwData*<br/>
[in] Dane skojarzone z elementem do usunięcia.  
  
*lpszText*<br/>
[in] Tekst elementu do usunięcia. Jeśli wiele elementów za pomocą tego samego tekstu, pierwszy element zostanie usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli element został znajduje się i usunięto; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData  
 Duplikaty danych zdefiniowane przez użytkownika.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda nie działa. Przesłonić tę metodę w klasie pochodnej, jeśli chcesz skopiować wszystkie dane zdefiniowane przez użytkownika.  
  
##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow  
 Włącza lub wyłącza pola edycji i kombi.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bWłączenie*<br/>
[in] Wartość TRUE, aby włączyć edytowanie i kombi pól. Wartość FALSE umożliwia wyłączenie pola edycji i kombi.  
  
### <a name="remarks"></a>Uwagi  
 Po wyłączeniu formanty nie może stać się aktywne i nie akceptuje dane wejściowe użytkownika.  
  
##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton  
 Kopiuje identyfikatora ciągu z tabeli ciągów aplikacji określonej w menu za pomocą polecenia przycisk pola kombi.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
*Przycisk menu*<br/>
[out] Odwołanie do przycisku menu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze TRUE.  
  
##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem  
 Zwraca indeks pierwszego elementu w polu listy, który zawiera określonego ciągu.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametry  
*lpszText*<br/>
[in] Tekst do wyszukania w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu; lub CB_ERR, jeśli element nie zostanie znaleziony.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd  
 Pobiera wskaźnik do przycisk pola kombi, która ma identyfikator określonego polecenia.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
*bIsFocus*<br/>
[in] Wartość true tylko wyszukiwanie skupia się przyciski; Wartość FALSE, aby wyszukać wszystkie przyciski.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do przycisku pole kombi; lub wartość NULL, jeśli nie można odnaleźć przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox  
 Zwraca wskaźnik do pola kombi kombi przycisk pola.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [klasa CComboBox](../../mfc/reference/ccombobox-class.md) obiektu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID  
 Pobiera identyfikator zasobu menu skrótów dla przycisk pola kombi.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu menu skrótów  
  
##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount  
 Zwraca liczbę elementów w polu listy.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll  
 Pobiera liczbę elementów w polu listy przycisku pola kombi, który ma identyfikator określonego polecenia.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów w polu listy; w przeciwnym razie nie można odnaleźć CB_ERR Jeśli kombi polu przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel  
 Pobiera indeks aktualnie wybranego elementu w polu listy.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks aktualnie wybranego elementu w polu listy; lub CB_ERR, jeśli nie wybrano elementu.  
  
### <a name="remarks"></a>Uwagi  
 Indeks pola listy jest liczony od zera.  
  
##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll  
 Zwraca indeks aktualnie wybranego elementu w polu listy kombi przycisk pola, który ma identyfikator określonego polecenia.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks aktualnie wybranego elementu w polu listy; w przeciwnym razie nie znaleziono CB_ERR, jeśli nie wybrano elementu, lub przycisk pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Indeks pola listy jest liczony od zera.  
  
##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl  
 Zwraca wskaźnik do pola edycji kombi przycisk pola.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd  
 Zwraca uchwyt okna dla tego pola kombi.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Uchwyt okna lub wartość NULL, jeśli pole kombi nie jest skojarzony z obiektem okna.  
  
##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem  
 Zwraca ciąg skojarzony element z określonym indeksem, w polu listy.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ciągu, który jest skojarzony z elementem; w przeciwnym razie wartość NULL, jeśli parametr indeksu jest nieprawidłowy lub parametr indeksu jest wartość -1, jeśli nie ma żadnych wybranego elementu w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca ciąg elementu, który jest aktualnie wybrany.  
  
##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll  
 Zwraca ciąg skojarzony element z określonym indeksem na liście przycisk pola kombi, która ma identyfikator określonego polecenia.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ciągu elementu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL, jeśli ten indeks jest nieprawidłowy, przycisk pola kombi nie zostanie znaleziony, lub indeks jest wartość -1, jeśli nie ma żadnych wybranego elementu w polu kombi.  
  
### <a name="remarks"></a>Uwagi  
 Wartość indeksu,-1 zwraca ciąg elementu, który jest aktualnie wybrany.  
  
##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData  
 Zwraca dane skojarzone z elementem o określonym indeksie w polu listy.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane skojarzone z elementem; lub 0, jeśli element nie istnieje.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranego elementu.  
  
##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll  
 Zwraca dane skojarzone z elementem o określonym indeksie w polu listy przycisku pola kombi, który ma identyfikator określonego polecenia.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane skojarzone z elementem, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie nie znaleziono 0, jeśli określony indeks jest nieprawidłowy lub CB_ERR Jeśli kombi polu przycisku.  
  
### <a name="remarks"></a>Uwagi  
 Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranego elementu.  
  
##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Zwraca dane skojarzone z elementem o określonym indeksie w polu listy przycisku pola kombi, który ma identyfikator określonego polecenia. Te dane są zwracane jako wskaźnik.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi.  
  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik skojarzone z elementem, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość-1 Jeśli błąd wystąpi lub nie ma wartość NULL, jeśli kombi polu przycisku.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt  
 Zwraca ciąg monitu kombi przycisk pola.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg monitu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda nie jest obecnie zaimplementowana.  
  
##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText  
 Pobiera tekst w polu edycji.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst w polu edycji.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll  
 Pobiera tekst w polu edycji przycisku pola kombi, który ma identyfikator określonego polecenia.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi określone.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tekst w polu edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus  
 Wskazuje, czy pole kombi aktualnie ma fokus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pole kombi aktualnie ma fokus; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda również zwraca wartość PRAWDA, jeśli wszystkie okna podrzędnego pola kombi aktualnie ma fokus.  
  
##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert  
 Zwraca położenie w pionie przyciskami pola kombi w aplikacji.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przyciski są wyśrodkowane; Wartość FALSE, jeśli przyciski są wyrównane u góry.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode  
 Zwraca płaski wygląd przycisków pola kombi w aplikacji.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli przyciski płaski; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny styl płaskie przyciski pola kombi jest FALSE.  
  
##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf  
 Wskazuje, czy określone dojście jest skojarzony z przycisk pola kombi lub jeden z jego elementów podrzędnych.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Parametry  
*hwnd*<br/>
[in] Uchwyt okna.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli dojście jest skojarzonego z przycisk pola kombi lub jednego z jego elementów podrzędnych; w przeciwnym razie wartość FALSE.  
  
##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton  
 Wskazuje, czy przycisk pola kombi znajduje się w panelu wstążki.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zawsze wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie ta metoda zawsze zwraca wartość FALSE, co oznacza, że przycisk pola kombi nigdy nie jest wyświetlane w panelu wstążki.  
  
##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible  
 Zwraca stan widoczności kombi przycisk pola.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan widoczności przycisk pola kombi.  
  
##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand  
 Wskazuje, czy przycisk pola kombi przetwarza wiadomości.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
*iNotifyCode*<br/>
[in] Komunikat powiadomienia, który jest skojarzony z poleceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Czy przycisk pola kombi przetwarza wiadomości.  
  
##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Wywoływane przez platformę, gdy przycisk zostanie dodany do **Dostosuj** okno dialogowe.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize  
 Metoda wywoływana przez platformę, by Oblicz rozmiar przycisku.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które wyświetla przycisk pola kombi.  
  
*sizeDefault*<br/>
[in] Domyślny rozmiar przycisk pola kombi.  
  
*bHorz*<br/>
[in] Stan dokowania paska narzędzi nadrzędnej. Wartość TRUE, gdy pasek narzędzi jest zadokowany w poziomie i wartość FALSE, gdy pasek narzędzi jest zadokowany w pionie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `SIZE` strukturę, która zawiera wymiary przycisk pola kombi, w pikselach.  
  
##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Wywoływane przez platformę, gdy przycisk pola kombi są wstawiane do nowy pasek narzędzi.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik na nowy pasek narzędzi nadrzędnej.  
  
##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick  
 Wywoływane przez platformę, gdy użytkownik kliknie przycisk pola kombi.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*pWnd*<br/>
[in] Wskaźnik do okna nadrzędnego przycisku pola kombi.  
  
*bDelay*<br/>
[in] Zarezerwowany do użytku w klasie pochodnej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda obsługi zdarzeń; w przeciwnym razie wartość FALSE.  
  
##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor  
 Wywoływane przez platformę, gdy użytkownik zmieni kolor narzędzi macierzysty, aby ustawić kolor przycisku pola kombi.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które wyświetla przycisk pola kombi.  
  
*nCtlColor*<br/>
[in] Nieużywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do pędzel framework używa do rysowania tła przycisku pola kombi.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda również ustawia kolor tekstu przycisku w polu kombi.  
  
##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw  
 Metoda wywoływana przez platformę, by narysować przycisk pola kombi przy użyciu określonych stylów i opcje.  
  
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
*Podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które powoduje wyświetlenie przycisku.  
  
*Rect*<br/>
[in] Prostokąt otaczający przycisku.  
  
*pImages*<br/>
[in] Kolekcja obrazów, która jest skojarzona z przyciskiem.  
  
*bHorz*<br/>
[in] Stan dokowania paska narzędzi nadrzędnej. Wartość TRUE, gdy pasek narzędzi jest zadokowany w poziomie i wartość FALSE, gdy pasek narzędzi jest zadokowany w pionie.  
  
*bCustomizeMode*<br/>
[in] Czy aplikacja jest w trybie dostosowywania.  
  
*bHighlight*<br/>
[in] Określa, czy rysowanie z wyróżnionym przyciskiem pola kombi.  
  
*bDrawBorder*<br/>
[in] Określa, czy Rysowanie przycisk pola kombi z obramowaniem.  
  
*bGrayDisabledButtons*<br/>
[in] Wartość true, rysowania cieniowanie przyciski wyłączone; Wartość FAŁSZ, aby użyć kolekcji obrazów wyłączone.  
  
##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Wywoływane przez platformę, by narysować przycisk pola kombi **polecenia** okienku **Dostosuj** okno dialogowe.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
*podstawowego kontrolera domeny*<br/>
[in] Kontekst urządzenia, które wyświetla przycisk pola kombi.  
  
*Rect*<br/>
[in] Prostokąt otaczający przycisk pola kombi.  
  
*bSelected*<br/>
[in] Wartość TRUE, jeśli wybrano przycisk pola kombi; w przeciwnym razie wartość FALSE.  
  
### <a name="return-value"></a>Wartość zwracana  
 Szerokość w pikselach, przycisk pola kombi.  
  
##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Metoda wywoływana przez platformę, by ustawić czcionkę przycisk pola kombi, po zmianie czcionki w aplikacji.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove  
 Metoda wywoływana przez platformę, by zmienić lokalizację przycisk pola kombi, kiedy przesuwa narzędzi nadrzędnej.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow  
 Wywoływane przez platformę, gdy przycisk pola kombi jest ukrywane lub wyświetlane.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
*bShow*<br/>
[in] Określa, czy ukryć lub wyświetlić przycisk pola kombi.  
  
##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize  
 Metoda wywoływana przez platformę, by zmienić rozmiar przycisku pola kombi, gdy narzędzi nadrzędnego zmienia rozmiar.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
*iSize*<br/>
[in] Szerokość nowy przycisk pola kombi.  
  
##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Wywoływane przez platformę, gdy użytkownik zmieni etykietki narzędzia dla przycisku pola kombi.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
*pWndParent*<br/>
[in] Wskaźnik do okna nadrzędnego przycisk pola kombi.  
  
*iButtonIndex*<br/>
[in] Identyfikator przycisk pola kombi.  
  
*wndToolTip*<br/>
[in] Etykietka narzędzia do skojarzenia z przycisk pola kombi.  
  
*str*<br/>
[in] Tekst wskazówki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda obsługi zdarzeń; w przeciwnym razie wartość FALSE.  
  
##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems  
 Usuwa wszystkie elementy z listy i edytowania pól.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie elementy z listy pola i edytować kontrolki pola kombi.  
  
##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem  
 Wybiera element w polu listy.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.  
  
*bNotify*<br/>
[in] Wartość TRUE, aby powiadomić przycisk pola kombi wyboru; w przeciwnym razie wartość FALSE.  
  
*dwData*<br/>
[in] Dane skojarzone z elementem w polu listy.  
  
*lpszText*<br/>
[in] Tekst elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll  
 Wybiera element w polu listy przycisku pola kombi, który ma identyfikator określonego polecenia.  
  
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
*uiCmd*<br/>
[in] Identyfikator polecenia przycisk pola kombi, która zawiera pole listy.  
  
*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy. Wartość -1 usuwa wszystkie bieżące zaznaczenie w polu listy i czyści pole edycji.  
  
*dwData*<br/>
[in] Dane elementu w polu listy.  
  
*lpszText*<br/>
[in] Tekst elementu w polu listy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize  
 Odczytuje obiekt z archiwum lub zapisuje je do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
*ar*<br/>
[out w] `CArchive` Obiektu do zserializowania.  
  
### <a name="remarks"></a>Uwagi  
 Ustawienia w `CArchive` obiektu ustalić, czy ta metoda odczytuje lub zapisuje do archiwum.  
  
##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData  
 Wypełnia określony `CAccessibilityData` obiektu przy użyciu danych ułatwień dostępu z przycisk pola kombi.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parametry  
*pParent*<br/>
[in] Okno nadrzędne przycisk pola kombi.  
  
*Dane*<br/>
[out] A `CAccessibilityData` obiekt, który odbiera dane dostępności z przycisk pola kombi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert  
 Ustawia położenie w pionie przyciskami pola kombi w aplikacji.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bCenterVert*<br/>
[in] Wartość TRUE, aby wyśrodkować przycisk pola kombi na pasku narzędzi; Wartość FALSE, aby wyrównać przycisk pola kombi na górze paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie przyciskami pola kombi są wyrównane do góry.  
  
##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID  
 Określa identyfikator zasobu menu skrótów dla kombi przycisk pola.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parametry  
*uiResID*<br/>
[in] Identyfikator zasobu menu skrótów  
  
##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight  
 Ustawia wysokość pola listy, gdy jest rozwijana.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametry  
*nHeight*<br/>
[in] Wysokość w pikselach, pola listy.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna wysokość jest 150 pikseli.  
  
##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode  
 Ustawia płaski wygląd przycisków pola kombi w aplikacji.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
*bFlat*<br/>
[in] Wartość TRUE dla płaski wygląd; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny styl płaskie przyciski pola kombi jest FALSE.  
  
##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle  
 Ustawia określony styl kombi przycisk pola i ponownie rysuje kontrolki, jeśli nie zostanie wyłączony.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
*nStyle*<br/>
[in] Bitowa kombinacja (lub) style paska narzędzi.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać listę style przycisku paska narzędzi, zobacz [style formantu ToolBar](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText  
 Ustawia tekst w polu edycji kombi przycisk pola.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
*lpszText*<br/>
[in] Wskaźnik do ciągu, który zawiera tekst w polu edycji.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Ccombobox — klasa](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)



