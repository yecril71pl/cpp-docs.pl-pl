---
title: Klasa CMFCToolBarComboBoxButton
ms.date: 11/04/2016
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
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915965"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Klasa CMFCToolBarComboBoxButton

Przycisk paska narzędzi, który zawiera kontrolkę pola kombi ( [Klasa CComboBox](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Składnia

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Konstruuje `CMFCToolBarComboBoxButton`a.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton:: AddItem](#additem)|Dodaje element na końcu listy pola kombi.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Dodaje element do listy pól kombi. Kolejność elementów na liście jest określana przez `Compare`.|
|[CMFCToolBarComboBoxButton:: Compare](#compare)|Porównuje dwa elementy. Wywołuje się, by sortować `AddSortedItems` elementy, które dodaje do listy pól kombi.|
|[CMFCToolBarComboBoxButton:: SetEdit](#createedit)|Tworzy nową kontrolkę edycji dla przycisku pola kombi.|
|[CMFCToolBarComboBoxButton::D eleteItem](#deleteitem)|Usuwa element z listy pól kombi.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Zwraca indeks elementu, który zawiera określony ciąg.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Zwraca wskaźnik do przycisku pola kombi o określonym IDENTYFIKATORze polecenia.|
|[CMFCToolBarComboBoxButton:: getcombobox](#getcombobox)|Zwraca wskaźnik do kontrolki pola kombi osadzonej w przycisku pola kombi.|
|[CMFCToolBarComboBoxButton:: GetCount](#getcount)|Zwraca liczbę elementów na liście pola kombi.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia. Zwraca liczbę elementów na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Zwraca indeks zaznaczonego elementu na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia i zwraca indeks zaznaczonego elementu na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Zwraca wskaźnik do kontrolki edycji osadzonej w przycisku pola kombi.|
|[CMFCToolBarComboBoxButton:: GetItem](#getitem)|Zwraca ciąg, który jest skojarzony z określonym indeksem na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia i zwraca ciąg, który jest skojarzony z indeksem na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Zwraca wartość 32-bitową, która jest skojarzona z określonym indeksem na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia i zwraca wartość 32-bitową skojarzoną z indeksem na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia. Pobiera wartość 32-bitową, która jest skojarzona z indeksem na liście pól kombi tego przycisku i zwraca wartość 32-bitową jako wskaźnik.|
|[CMFCToolBarComboBoxButton:: gettext](#gettext)|Zwraca tekst z kontrolki edycji pola kombi.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia i zwraca tekst z kontrolki edycji tego przycisku.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowane lub wyrównane w górnej części paska narzędzi.|
|[CMFCToolBarComboBoxButton:: IsFlatMode](#isflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy z pola listy i kontrolki edycji pola kombi.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Wybiera element w polu kombi, zgodnie z jego indeksem, 32-bitową wartością lub ciągiem, i powiadamia formant pola kombi o zaznaczeniu.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Znajduje przycisk pola kombi o określonym IDENTYFIKATORze polecenia. Wywołuje `SelectItem` , aby wybrać element w polu kombi tego przycisku zgodnie z jego ciągiem, indeksem lub wartością 32-bitową.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowane w pionie czy wyrównane do góry paska narzędzi.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy rozwijanej.|
|[CMFCToolBarComboBoxButton:: SetFlatMode](#setflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola kombi do paska narzędzi, wykonaj następujące kroki:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

2. Konstruowanie `CMFCToolBarComboBoxButton` obiektu.

3. W programie obsługi komunikatów, który przetwarza komunikat AFX_WM_RESETTOOLBAR, Zastąp przycisk fikcyjny nowym przyciskiem pola kombi, używając [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji, [zobacz Przewodnik: Umieszczanie formantów na](../../mfc/walkthrough-putting-controls-on-toolbars.md)paskach narzędzi. Przykład przycisku paska narzędzi pola kombi można znaleźć w przykładowym projekcie VisualStudioDemo.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia różnych metod w `CMFCToolBarComboBoxButton` klasie. W przykładzie pokazano, jak włączyć pola edycji i kombi, ustawić pionowe położenie przycisków kombi w aplikacji, ustawić wysokość pola listy po jego porzucenia, ustawić wygląd płaskiego stylu przycisków kombi w aplikacji i Ustaw tekst w polu edycji przycisku pola kombi. Ten fragment kodu jest częścią [przykładu demonstracyjnego Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarcomboboxbutton. h

##  <a name="additem"></a>CMFCToolBarComboBoxButton:: AddItem

Dołącza unikatowy element do pola listy.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
podczas Tekst elementu, który ma zostać dodany do pola listy.

*dwData*<br/>
podczas Dane skojarzone z elementem do dodania do pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego elementu w polu listy.

### <a name="remarks"></a>Uwagi

Nie używaj tej metody, gdy styl pola listy jest sortowany.

Jeśli tekst elementu znajduje się już w polu listy, nowe dane są przechowywane z istniejącym elementem. W wyszukiwaniu dla elementu jest uwzględniana wielkość liter.

##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Dodaje element do pola listy w kolejności zdefiniowanej za pomocą metody [Compare](#compare) .

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
podczas Tekst elementu, który ma zostać dodany do pola listy.

*dwData*<br/>
podczas Dane skojarzone z elementem do dodania do pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu, który został dodany do pola listy.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby dodać elementy do pola listy w określonej kolejności.

##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Wskazuje, czy rozmiar przycisku pola kombi można zmienić.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE.

##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Konstruuje obiekt [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
podczas Identyfikator polecenia nowego przycisku.

*iImage*<br/>
podczas Indeks obrazu obrazu skojarzonego z przyciskiem nowy.

*dwStyle*<br/>
podczas Styl przycisku Nowy.

*iWidth*<br/>
podczas Szerokość przycisku New w pikselach.

### <a name="remarks"></a>Uwagi

Domyślna szerokość to 150 pikseli.

Aby uzyskać listę stylów przycisków paska narzędzi, zobacz [Style formantów Toolbar](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Usuwa dane zdefiniowane przez użytkownika.

```
virtual void ClearData();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie wykonuje żadnych operacji. Zastąp tę metodę w klasie pochodnej, jeśli chcesz usunąć wszystkie dane zdefiniowane przez użytkownika.

##  <a name="compare"></a>CMFCToolBarComboBoxButton:: Compare

Porównuje dwa ciągi.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parametry

*lpszItem1*<br/>
podczas Pierwszy ciąg do porównania.

*lpszItem2*<br/>
podczas Drugi ciąg do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość, która wskazuje zależność leksykograficznych z uwzględnieniem wielkości liter między ciągami. Poniższa tabela zawiera listę możliwych wartości:

|Wartość|Opis|
|-----------|-----------------|
|\<0|Pierwszy ciąg jest mniejszy od drugiego.|
|0|Pierwszy ciąg jest równy drugiemu.|
|>0|Pierwszy ciąg jest większy niż drugi.|

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zmienić sposób sortowania elementów w polu listy.

W porównaniu z rozróżnianiem wielkości liter.

Ta metoda jest wywoływana tylko z metody [AddSortedItem](#addsorteditem) .

##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom

Kopiuje stan określonego `CMFCToolBarComboBoxButton` elementu do bieżącego obiektu.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Obiekt źródłowy `CMFCToolBarComboBoxButton` .

##  <a name="createcombo"></a>CMFCToolBarComboBoxButton:: oncombo

Tworzy nowe pole kombi dla przycisku pola kombi.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do okna nadrzędnego przycisku.

*cinania*<br/>
podczas Prostokąt ograniczający pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola kombi, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie wartość NULL.

##  <a name="createedit"></a>CMFCToolBarComboBoxButton:: SetEdit

Tworzy nowe pole edycji dla przycisku pola kombi.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do okna nadrzędnego przycisku.

*cinania*<br/>
podczas Prostokąt związany z nowym polem edycji.

*dwEditStyle*<br/>
podczas Styl formantu nowego pola edycji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tworzy nowe pole edycji dla przycisku pola kombi. Zastąp tę metodę, aby zmienić sposób tworzenia [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) .

##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::D eleteItem

Usuwa określony element z pola listy.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu, który ma zostać usunięty.

*dwData*<br/>
podczas Dane skojarzone z elementem, który ma zostać usunięty.

*lpszText*<br/>
podczas Tekst elementu, który ma zostać usunięty. Jeśli istnieje wiele elementów z tym samym tekstem, pierwszy element zostanie usunięty.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli element został znaleziony i pomyślnie usunięty. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

Duplikuje dane zdefiniowane przez użytkownika.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nie wykonuje żadnych operacji. Zastąp tę metodę w klasie pochodnej, jeśli chcesz skopiować dowolne dane zdefiniowane przez użytkownika.

##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Włącza lub wyłącza pola edycji i kombi.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
podczas PRAWDA, aby włączyć pola edycji i kombi; Wartość FALSE powoduje wyłączenie pól edycji i kombi.

### <a name="remarks"></a>Uwagi

Po wyłączeniu formanty nie mogą stać się aktywne i nie mogą akceptować danych wejściowych użytkownika.

##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Kopiuje ciąg z tabeli ciągów aplikacji do określonego menu przy użyciu przycisku pola kombi.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
określoną Odwołanie do przycisku menu.

### <a name="return-value"></a>Wartość zwracana

Zawsze prawda.

##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Zwraca indeks pierwszego elementu w polu listy, który zawiera określony ciąg.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
podczas Tekst, który ma być wyszukiwany w polu listy.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu; lub CB_ERR, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Pobiera wskaźnik do przycisku pola kombi, który ma określony identyfikator polecenia.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

*bIsFocus*<br/>
podczas TRUE, aby przeszukać tylko przyciski ukierunkowane; Wartość FALSE, aby przeszukać wszystkie przyciski.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przycisku pola kombi; lub wartość NULL, jeśli przycisk nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton:: getcombobox

Zwraca wskaźnik do pola kombi w polu kombi.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu [klasy CComboBox](../../mfc/reference/ccombobox-class.md) , jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Pobiera identyfikator zasobu menu skrótów dla przycisku pola kombi.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu skrótów.

##  <a name="getcount"></a>CMFCToolBarComboBoxButton:: GetCount

Zwraca liczbę elementów w polu listy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy.

### <a name="remarks"></a>Uwagi

##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Pobiera liczbę elementów w polu listy przycisku kombi, który ma określony identyfikator polecenia.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy; w przeciwnym razie, CB_ERR, jeśli przycisk pola kombi nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Pobiera indeks aktualnie wybranego elementu w polu listy.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks aktualnie zaznaczonego elementu w polu listy; lub CB_ERR, jeśli nie wybrano żadnego elementu.

### <a name="remarks"></a>Uwagi

Indeks pola listy jest liczony od zera.

##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Zwraca indeks aktualnie zaznaczonego elementu w polu listy przycisku kombi, który ma określony identyfikator polecenia.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

### <a name="return-value"></a>Wartość zwracana

Indeks aktualnie zaznaczonego elementu w polu listy; w przeciwnym razie, CB_ERR, jeśli nie wybrano żadnego elementu lub nie znaleziono przycisku pola kombi.

### <a name="remarks"></a>Uwagi

Indeks pola listy jest liczony od zera.

##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Zwraca wskaźnik do pola edycji w polu kombi.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton:: GetHwnd

Zwraca uchwyt okna pola kombi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna lub wartość NULL, jeśli pole kombi nie jest skojarzone z obiektem okna.

##  <a name="getitem"></a>CMFCToolBarComboBoxButton:: GetItem

Zwraca ciąg skojarzony z elementem w określonym indeksie w polu listy.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks elementu w polu listy liczony od zera.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który jest skojarzony z elementem; w przeciwnym razie wartość NULL, jeśli parametr index jest nieprawidłowy, lub jeśli parametr index to-1, a w polu kombi nie ma wybranego elementu.

### <a name="remarks"></a>Uwagi

Parametr indeksu-1 zwraca ciąg elementu, który jest aktualnie wybrany.

##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Zwraca ciąg skojarzony z elementem w określonym indeksie w polu listy przycisku kombi, który ma określony identyfikator polecenia.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu elementu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość NULL, jeśli indeks jest nieprawidłowy, przycisk pola kombi nie zostanie znaleziony lub jeśli indeks ma wartość-1, a w polu kombi nie ma wybranego elementu.

### <a name="remarks"></a>Uwagi

Wartość indeksu-1 zwraca ciąg elementu, który jest aktualnie wybrany.

##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem; lub 0, jeśli element nie istnieje.

### <a name="remarks"></a>Uwagi

Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranym elementem.

##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy przycisku kombi, który ma określony identyfikator polecenia.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość 0, jeśli określony indeks jest nieprawidłowy, lub CB_ERR, jeśli nie znaleziono przycisku pola kombi.

### <a name="remarks"></a>Uwagi

Parametr indeksu-1 zwraca dane skojarzone z aktualnie wybranym elementem.

##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy przycisku kombi, który ma określony identyfikator polecenia. Te dane są zwracane jako wskaźnik.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia pola kombi.

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik skojarzony z elementem, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie-1, jeśli wystąpi błąd, lub wartość NULL, jeśli nie znaleziono przycisku pola kombi.

### <a name="remarks"></a>Uwagi

##  <a name="getprompt"></a>CMFCToolBarComboBoxButton:: GetPrompt

Zwraca ciąg monitu dla przycisku pola kombi.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg monitu.

### <a name="remarks"></a>Uwagi

Ta metoda nie jest obecnie zaimplementowana.

##  <a name="gettext"></a>CMFCToolBarComboBoxButton:: gettext

Pobiera tekst w polu edycji.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Wartość zwracana

Tekst w polu edycji.

### <a name="remarks"></a>Uwagi

##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Pobiera tekst w polu edycji przycisku pola kombi o określonym IDENTYFIKATORze polecenia.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*uiCmd*<br/>
podczas Identyfikator polecenia określonego przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

Tekst w polu edycji, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Wskazuje, czy pole kombi ma aktualnie fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli pole kombi ma aktualnie fokus; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca również wartość TRUE, Jeśli dowolne okno podrzędne pola kombi ma aktualnie fokus.

##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Zwraca pionową pozycję przycisków kombi w aplikacji.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przyciski są wyśrodkowane; FAŁSZ, jeśli przyciski są wyrównane do góry.

### <a name="remarks"></a>Uwagi

##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton:: IsFlatMode

Zwraca wygląd płaskiego stylu przycisków kombi w aplikacji.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przyciski mają styl płaski; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślny styl płaski dla przycisków kombi ma wartość FALSE.

##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

Wskazuje, czy określone dojście jest skojarzone z przyciskiem pola kombi, czy jednym z jego elementów podrzędnych.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Uchwyt okna.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli uchwyt jest assocated z przyciskiem pola kombi lub jednym z jego elementów podrzędnych; w przeciwnym razie FALSE.

##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Wskazuje, czy przycisk pola kombi znajduje się na panelu wstążki.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze FAŁSZ.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FALSE, co oznacza, że przycisk pola kombi nigdy nie jest wyświetlany na panelu wstążki.

##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Zwraca stan widoczności przycisku pola kombi.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Wartość zwracana

Stan widoczności przycisku pola kombi.

##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Wskazuje, czy przycisk pola kombi przetwarza komunikat.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*iNotifyCode*<br/>
podczas Komunikat z powiadomieniem, który jest skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

Czy przycisk pola kombi przetwarza komunikat.

##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Wywoływane przez platformę po dodaniu przycisku do okna dialogowego **Dostosowywanie** .

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Wywoływane przez platformę, by obliczyć rozmiar przycisku.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, w którym jest wyświetlany przycisk pola kombi.

*sizeDefault*<br/>
podczas Domyślny rozmiar przycisku pola kombi.

*bHorz*<br/>
podczas Stan dokowania nadrzędnego paska narzędzi. Ma wartość TRUE, jeśli pasek narzędzi jest zadokowany w poziomie i FAŁSZ, gdy pasek narzędzi jest zadokowany w pionie.

### <a name="return-value"></a>Wartość zwracana

`SIZE` Struktura, która zawiera wymiary przycisku pola kombi (w pikselach).

##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Wywoływane przez platformę, gdy przycisk pola kombi zostanie wstawiony do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do nowego nadrzędnego paska narzędzi.

##  <a name="onclick"></a>CMFCToolBarComboBoxButton:: onkliknięcia

Wywoływane przez platformę, gdy użytkownik kliknie przycisk pola kombi.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
podczas Wskaźnik do okna nadrzędnego przycisku kombi.

*bDelay*<br/>
podczas Zarezerwowane do użycia w klasie pochodnej.

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli metoda obsługuje zdarzenie; w przeciwnym razie FALSE.

##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Wywoływane przez platformę, gdy użytkownik zmienia kolor nadrzędnego paska narzędzi, aby ustawić kolor przycisku pola kombi.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, w którym jest wyświetlany przycisk pola kombi.

*nCtlColor*<br/>
podczas Przestrzeń.

### <a name="return-value"></a>Wartość zwracana

Dojście do pędzla używanego przez platformę do rysowania tła przycisku pola kombi.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia również kolor tekstu przycisku pola kombi.

##  <a name="ondraw"></a>CMFCToolBarComboBoxButton:: OnDraw

Wywoływane przez platformę, aby narysować przycisk pola kombi przy użyciu określonych stylów i opcji.

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

*Domeny*<br/>
podczas Kontekst urządzenia, który wyświetla przycisk.

*cinania*<br/>
podczas Prostokąt ograniczający przycisku.

*pImages*<br/>
podczas Kolekcja obrazów skojarzonych z przyciskiem.

*bHorz*<br/>
podczas Stan dokowania nadrzędnego paska narzędzi. Ma wartość TRUE, jeśli pasek narzędzi jest zadokowany w poziomie i FAŁSZ, gdy pasek narzędzi jest zadokowany w pionie.

*bCustomizeMode*<br/>
podczas Czy aplikacja działa w trybie dostosowywania.

*bHighlight*<br/>
podczas Określa, czy ma zostać wyróżniony przycisk pola kombi.

*bDrawBorder*<br/>
podczas Czy rysować przycisk pola kombi z obramowaniem.

*bGrayDisabledButtons*<br/>
podczas TRUE, aby narysować wyszarzone przyciski wyłączone; Wartość FALSE, aby użyć kolekcji disabled images.

##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Wywoływane przez platformę, aby narysować przycisk pola kombi w okienku **polecenia** okna dialogowego **Dostosowywanie** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
podczas Kontekst urządzenia, w którym jest wyświetlany przycisk pola kombi.

*cinania*<br/>
podczas Prostokąt ograniczający przycisku pola kombi.

*bSelected*<br/>
podczas Ma wartość TRUE, jeśli wybrano przycisk pola kombi; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Szerokość przycisku pola kombi (w pikselach).

##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Wywoływane przez platformę, aby ustawić czcionkę przycisku pola kombi, gdy zmienia się czcionka aplikacji.

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>CMFCToolBarComboBoxButton:: OnMove

Wywoływane przez platformę, aby zmienić lokalizację przycisku pola kombi po przesunięciu nadrzędnego paska narzędzi.

```
virtual void OnMove();
```

##  <a name="onshow"></a>CMFCToolBarComboBoxButton:: OnShow

Wywoływane przez platformę, gdy przycisk pola kombi jest ukryty lub wyświetlany.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bShow*<br/>
podczas Czy ukryć lub wyświetlić przycisk pola kombi.

##  <a name="onsize"></a>CMFCToolBarComboBoxButton:: OnSize

Wywoływane przez platformę, aby zmienić rozmiar przycisku pola kombi, gdy zmieni się rozmiar paska narzędzi nadrzędnych.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*iSize*<br/>
podczas Nowa szerokość przycisku pola kombi.

##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

Wywoływane przez platformę, gdy użytkownik zmieni etykietkę narzędzia dla przycisku pola kombi.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
podczas Wskaźnik do okna nadrzędnego dla przycisku pola kombi.

*iButtonIndex*<br/>
podczas Identyfikator przycisku pola kombi.

*wndToolTip*<br/>
podczas Etykietka narzędzia do skojarzenia z przyciskiem pola kombi.

*str*<br/>
podczas Tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

TRUE, jeśli metoda obsługuje zdarzenie; w przeciwnym razie FALSE.

##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Usuwa wszystkie elementy z listy i pól edycji.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie elementy z pola listy i kontrolki edycji pola kombi.

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

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy.

*bNotify*<br/>
podczas Wartość TRUE, aby powiadomić przycisk pola kombi o zaznaczeniu; w przeciwnym razie FALSE.

*dwData*<br/>
podczas Dane skojarzone z elementem w polu listy.

*lpszText*<br/>
podczas Tekst elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Wybiera element w polu listy przycisku pola kombi, który ma określony identyfikator polecenia.

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
podczas Identyfikator polecenia pola kombi, które zawiera pole listy.

*iIndex*<br/>
podczas Indeks (liczony od zera) elementu w polu listy. Wartość-1 usuwa wszystkie bieżące zaznaczenie w polu listy i czyści pole edycji.

*dwData*<br/>
podczas Dane elementu w polu listy.

*lpszText*<br/>
podczas Tekst elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="serialize"></a>CMFCToolBarComboBoxButton:: serializować

Odczytuje ten obiekt z archiwum lub zapisuje je w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
[in. out] `CArchive` Obiekt do serializacji.

### <a name="remarks"></a>Uwagi

Ustawienia w `CArchive` obiekcie określają, czy ta metoda odczytuje lub zapisuje dane w archiwum.

##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Wypełnia określony `CAccessibilityData` obiekt za pomocą danych ułatwień dostępu w polu kombi.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pParent*<br/>
podczas Okno nadrzędne przycisku kombi.

*Data*<br/>
określoną `CAccessibilityData` Obiekt, który odbiera dane dostępności z przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli metoda zakończyła się pomyślnie. w przeciwnym razie FALSE.

##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Ustawia pionowe położenie przycisków kombi w aplikacji.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parametry

*bCenterVert*<br/>
podczas Wartość TRUE, aby wyśrodkować przycisk pola kombi na pasku narzędzi. Wartość FALSE, aby wyrównać przycisk pola kombi w górnej części paska narzędzi.

### <a name="remarks"></a>Uwagi

Domyślnie przyciski pola kombi są wyrównane do góry.

##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Ustawia identyfikator zasobu menu skrótów dla przycisku pola kombi.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*uiResID*<br/>
podczas Identyfikator zasobu menu skrótów.

##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Ustawia wysokość pola listy, gdy zostanie ono usunięte.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nHeight*<br/>
podczas Wysokość pola listy w pikselach.

### <a name="remarks"></a>Uwagi

Domyślna wysokość to 150 pikseli.

##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton:: SetFlatMode

Ustawia płaski wygląd przycisków kombi w aplikacji.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat*<br/>
podczas TRUE dla wyglądu stylu prostego; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślny styl płaski dla przycisków kombi ma wartość FALSE.

##  <a name="setstyle"></a>CMFCToolBarComboBoxButton:: SetStyle

Ustawia określony styl dla przycisku pola kombi i ponownie Rysuje formant, jeśli nie jest wyłączony.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
podczas Kombinacja bitowa (lub) stylów paska narzędzi.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę stylów przycisków paska narzędzi, zobacz [Style formantów Toolbar](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Ustawia tekst w polu edycji przycisku pola kombi.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
podczas Wskaźnik na ciąg, który zawiera tekst dla pola edycji.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Przewodnik: umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
