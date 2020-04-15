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
ms.openlocfilehash: 0d003bdacf13403ad8dc4be4ec7e6f71ea57d156
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372190"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Klasa CMFCToolBarComboBoxButton

Przycisk paska narzędzi zawierający kontrolkę pola kombi [(klasa CComboBox).](../../mfc/reference/ccombobox-class.md)

## <a name="syntax"></a>Składnia

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Konstruuje `CMFCToolBarComboBoxButton`plik .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Dodaje element na końcu listy pól kombi.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Dodaje element do listy pól kombi. Kolejność elementów na liście jest `Compare`określona przez .|
|[CMFCToolBarComboBoxButton::Porównaj](#compare)|Porównuje dwa elementy. Wywoływana do `AddSortedItems` sortowania elementów, które dodaje się do listy pól kombi.|
|[CMFCToolBarComboBoxButton::UtwórzEdytuj](#createedit)|Tworzy nową kontrolkę edycji dla przycisku pola kombi.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Usuwa element z listy pól kombi.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Zwraca indeks elementu zawierającego określony ciąg.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Zwraca wskaźnik do przycisku pola kombi o określonym identyfikatorze polecenia.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Zwraca wskaźnik do formantu pola kombi osadzonego w przycisku pola kombi.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Zwraca liczbę elementów na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia. Zwraca liczbę elementów na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Zwraca indeks zaznaczonego elementu na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia i zwraca indeks zaznaczonego elementu na liście pola kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Zwraca wskaźnik do formantu edycji osadzonego w przycisku pola kombi.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Zwraca ciąg skojarzony z określonym indeksem na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia i zwraca ciąg skojarzony z indeksem na liście pola kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Zwraca wartość 32-bitową skojarzoną z określonym indeksem na liście pól kombi.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia i zwraca wartość 32-bitową skojarzoną z indeksem na liście pól kombi tego przycisku.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia. Pobiera wartość 32-bitową, która jest skojarzona z indeksem na liście pól kombi tego przycisku i zwraca wartość 32-bitową jako wskaźnik.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Zwraca tekst z formantu edycji pola kombi.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Wyszukuje przycisk pola kombi o określonym identyfikatorze polecenia i zwraca tekst z kontrolki edycji tego przycisku.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowane lub wyrównane z górną częścią paska narzędzi.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy z pola listy i edytuj kontrolkę pola kombi.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Wybiera element w polu kombi zgodnie z jego indeksem, wartością 32-bitową lub ciągiem znaków i powiadamia kontrolkę pola kombi o zaznaczeniu.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Znajduje przycisk pola kombi, który ma określony identyfikator polecenia. Wywołania, `SelectItem` aby wybrać element w polu kombi tego przycisku zgodnie z jego ciąg, indeks lub wartość 32-bitową.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Określa, czy przyciski pola kombi w aplikacji są wyśrodkowane pionowo, czy wyrównane z górną częścią paska narzędzi.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy rozwijanej.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Określa, czy przyciski pola kombi w aplikacji mają płaski wygląd.|

## <a name="remarks"></a>Uwagi

Aby dodać przycisk pola kombi do paska narzędzi, wykonaj następujące czynności:

1. Zarezerwuj fikcyjny identyfikator zasobu dla przycisku w zasobie nadrzędnego paska narzędzi.

2. Konstruuj `CMFCToolBarComboBoxButton` obiekt.

3. W programie obsługi wiadomości, który przetwarza komunikat AFX_WM_RESETTOOLBAR, zastąp przycisk manekina nowym przyciskiem pola kombi za pomocą [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Aby uzyskać więcej informacji, zobacz [Przewodnik: Umieszczanie kontrolek na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md). Na przykład przycisk paska narzędzi pola kombi, zobacz przykładowy projekt VisualStudioDemo.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarComboBoxButton` używać różnych metod w klasie. W przykładzie pokazano, jak włączyć pola edycji i kombi, ustawić pionową pozycję przycisków pola kombi w aplikacji, ustawić wysokość pola listy, gdy zostanie upuszczony, ustawić wygląd pola kombi w stylu płaskim w aplikacji i ustawić tekst w polu edycji przycisku pola kombi. Ten fragment kodu jest częścią [przykładu demo programu Visual Studio.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarcomboboxbutton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::AddItem

Dołącza unikatowy element do pola listy.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
[w] Tekst elementu, który ma być dodawany do pola listy.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem, który ma być dodawany do pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks ostatniego elementu w polu listy.

### <a name="remarks"></a>Uwagi

Nie należy używać tej metody, gdy styl pola listy jest sortowany.

Jeśli tekst elementu znajduje się już w polu listy, nowe dane są przechowywane z istniejącym elementem. W wyszukiwaniu elementu rozróżniana jest wielkość liter.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Dodaje element do pola listy w kolejności zdefiniowanej przez [metodę Porównaj.](#compare)

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
[w] Tekst elementu, który ma być dodawany do pola listy.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem, który ma być dodawany do pola listy.

### <a name="return-value"></a>Wartość zwracana

Indeks elementu, który został dodany do pola listy.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do dodawania elementów do pola listy w określonej kolejności.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

Wskazuje, czy rozmiar przycisku pola kombi może ulec zmianie.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Konstruuje [OBIEKT CMFCToolBarComboBoxButton.](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parametry

*Uiid*<br/>
[w] Identyfikator polecenia nowego przycisku.

*Iimage*<br/>
[w] Indeks obrazu skojarzony z nowym przyciskiem.

*Dwstyle*<br/>
[w] Styl nowego przycisku.

*iWidth ( iWidth )*<br/>
[w] Szerokość nowego przycisku w pikselach.

### <a name="remarks"></a>Uwagi

Domyślna szerokość to 150 pikseli.

Aby uzyskać listę stylów przycisków paska narzędzi, zobacz [Style sterowania paska narzędzi](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Usuwa dane zdefiniowane przez użytkownika.

```
virtual void ClearData();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nic nie robi. Zastąpi tę metodę w klasie pochodnej, jeśli chcesz usunąć wszystkie dane zdefiniowane przez użytkownika.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Porównaj

Porównuje dwa ciągi.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parametry

*lpszItem1*<br/>
[w] Pierwszy ciąg do porównania.

*lpszItem2*<br/>
[w] Drugi ciąg do porównania.

### <a name="return-value"></a>Wartość zwracana

Wartość, która wskazuje relację leksykograficzną z uwzględnieniem wielkości liter między ciągami. W poniższej tabeli wymieniono możliwe wartości:

|Wartość|Opis|
|-----------|-----------------|
|\<0|Pierwszy ciąg jest mniejszy niż drugi.|
|0|Pierwszy ciąg jest równy drugi.|
|>0|Pierwszy ciąg jest większy niż drugi.|

### <a name="remarks"></a>Uwagi

Zastąpaj tę metodę, aby zmienić sposób sortowania elementów w polu listy.

W porównaniu jest rozróżniana wielkość liter.

Ta metoda jest wywoływana tylko z [AddSortedItem](#addsorteditem) metody.

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom

Kopiuje stan określonego `CMFCToolBarComboBoxButton` do bieżącego obiektu.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] Obiekt `CMFCToolBarComboBoxButton` źródłowy.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Tworzy nowe pole kombi dla przycisku pola kombi.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego przycisku.

*Rect*<br/>
[w] Prostokąt ograniczający pola kombi.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola kombi, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::UtwórzEdytuj

Tworzy nowe pole edycji dla przycisku pola kombi.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego przycisku.

*Rect*<br/>
[w] Prostokąt ograniczający nowego pola edycji.

*dwEdytStyle*<br/>
[w] Styl sterowania nowego pola edycji.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę metodę, gdy tworzy nowe pole edycji dla przycisku pola kombi. Zastąpokaj tę metodę, aby zmienić sposób [tworzenia CMFCToolBarComboBoxEdit.](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem

Usuwa określony element z pola listy.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu do usunięcia.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem do usunięcia.

*lpszText (tekst)*<br/>
[w] Tekst elementu, który ma zostać usunięty. Jeśli istnieje wiele elementów o tym samym tekście, pierwszy element zostanie usunięty.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli element został zlokalizowany i pomyślnie usunięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData

Powiela dane zdefiniowane przez użytkownika.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda nic nie robi. Zastąpi tę metodę w klasie pochodnej, jeśli chcesz skopiować wszystkie dane zdefiniowane przez użytkownika.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Włącza lub wyłącza pola edycji i kombi.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć pola edycji i kombi; FALSE, aby wyłączyć pola edycji i kombi.

### <a name="remarks"></a>Uwagi

Po wyłączeniu formanty nie mogą stać się aktywne i nie można zaakceptować danych wejściowych użytkownika.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Kopiuje ciąg z tabeli ciągów aplikacji do określonego menu przy użyciu identyfikatora polecenia polecenia pola kombi.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parametry

*menuButton*<br/>
[na zewnątrz] Odwołanie do przycisku menu.

### <a name="return-value"></a>Wartość zwracana

Zawsze wartość TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Zwraca indeks pierwszego elementu w polu listy zawierający określony ciąg.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[w] Tekst, który ma być wyszukiwany w polu listy.

### <a name="return-value"></a>Wartość zwracana

Indeks towaru; lub CB_ERR, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Pobiera wskaźnik do przycisku pola kombi, który ma określony identyfikator polecenia.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

*bCzys.)-afocus*<br/>
[w] PRAWDA, aby wyszukać tylko przyciski skupione; FAŁSZ, aby przeszukać wszystkie przyciski.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przycisku pola kombi; null, jeśli przycisk nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

Zwraca wskaźnik do pola kombi w przycisku pola kombi.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CComboBox Class](../../mfc/reference/ccombobox-class.md) obiektu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Pobiera identyfikator zasobu menu skrótów dla przycisku pola kombi.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Wartość zwracana

Identyfikator zasobu menu skrótów.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount

Zwraca liczbę elementów w polu listy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Pobiera liczbę elementów w polu listy przycisku pola kombi, który ma określony identyfikator polecenia.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy; w przeciwnym razie CB_ERR, jeśli nie zostanie znaleziony przycisk pola kombi.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Pobiera indeks aktualnie zaznaczonego elementu w polu listy.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks aktualnie wybranego elementu w polu listy; lub CB_ERR, jeśli nie wybrano żadnego elementu.

### <a name="remarks"></a>Uwagi

Indeks pola listy jest od zera.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Zwraca indeks aktualnie zaznaczonego elementu w polu listy przycisku pola kombi o określonym identyfikatorze polecenia.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

Indeks aktualnie wybranego elementu w polu listy; w przeciwnym razie CB_ERR, jeśli nie wybrano żadnego elementu lub nie zostanie znaleziony przycisk pola kombi.

### <a name="remarks"></a>Uwagi

Indeks pola listy jest od zera.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Zwraca wskaźnik do pola edycji w przycisku pola kombi.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do pola edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

Zwraca uchwyt okna dla pola kombi.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Wartość zwracana

Uchwyt okna lub NULL, jeśli pole kombi nie jest skojarzone z obiektem okna.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem

Zwraca ciąg skojarzony z elementem przy określonym indeksie w polu listy.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który jest skojarzony z elementem; w przeciwnym razie NULL, jeśli parametr indeksu jest nieprawidłowy lub jeśli parametr indeksu wynosi -1 i nie ma zaznaczonego elementu w polu kombi.

### <a name="remarks"></a>Uwagi

Parametr indeksu o wartości -1 zwraca ciąg aktualnie wybranego elementu.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Zwraca ciąg skojarzony z elementem przy określonym indeksie w polu listy przycisku pola kombi, który ma określony identyfikator polecenia.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu elementu, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL, jeśli indeks jest nieprawidłowy, nie znaleziono przycisku pola kombi lub jeśli indeks ma wartość -1 i w polu kombi nie ma zaznaczonego elementu.

### <a name="remarks"></a>Uwagi

Wartość indeksu o wartości -1 zwraca ciąg aktualnie wybranego elementu.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem; lub 0, jeśli element nie istnieje.

### <a name="remarks"></a>Uwagi

Parametr indeksu o wartości -1 zwraca dane skojarzone z aktualnie wybranym elementem.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy przycisku pola kombi, który ma określony identyfikator polecenia.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie 0, jeśli określony indeks jest nieprawidłowy, lub CB_ERR, jeśli nie zostanie znaleziony przycisk pola kombi.

### <a name="remarks"></a>Uwagi

Parametr indeksu o wartości -1 zwraca dane skojarzone z aktualnie wybranym elementem.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Zwraca dane skojarzone z elementem w określonym indeksie w polu listy przycisku pola kombi, który ma określony identyfikator polecenia. Te dane są zwracane jako wskaźnik.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi.

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik skojarzony z elementem, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie -1, jeśli wystąpi błąd, lub NULL, jeśli nie znaleziono przycisku pola kombi.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

Zwraca ciąg monitu dla przycisku pola kombi.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Wartość zwracana

Ciąg monitu.

### <a name="remarks"></a>Uwagi

Ta metoda nie jest obecnie zaimplementowana.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText

Pobiera tekst w polu edycji.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Wartość zwracana

Tekst w polu edycji.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Pobiera tekst w polu edycji przycisku pola kombi, który ma określony identyfikator polecenia.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parametry

*Uicmd*<br/>
[w] Identyfikator polecenia określonego przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

Tekst w polu edycji, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Wskazuje, czy pole kombi ma obecnie fokus.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli pole kombi ma obecnie fokus; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda zwraca również wartość PRAWDA, jeśli w dowolnym oknie podrzędnym pola kombi aktualnie znajduje się fokus.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Zwraca położenie pionowe przycisków pola kombi w aplikacji.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przyciski są wyśrodkowane; FAŁSZ, jeśli przyciski są wyrównane u góry.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

Zwraca wygląd płaskiego stylu przycisków pola kombi w aplikacji.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli przyciski mają płaski styl; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślnym stylem płaskim dla przycisków pola kombi jest FAŁSZ.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

Wskazuje, czy określony uchwyt jest skojarzony z przyciskiem pola kombi, czy z jednym z jego wiązek powiązanych.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt okna.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli uchwyt jest assocated z przyciskiem pola kombi, lub jeden z jego obrażeń podrzędnych; w przeciwnym razie FALSE.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Wskazuje, czy przycisk pola kombi znajduje się na panelu wstążki.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Wartość zwracana

Zawsze FALSE.

### <a name="remarks"></a>Uwagi

Domyślnie ta metoda zawsze zwraca wartość FAŁSZ, co oznacza, że przycisk pola kombi nigdy nie jest wyświetlany na panelu wstążki.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Zwraca stan widoczności przycisku pola kombi.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Wartość zwracana

Stan widoczności przycisku pola kombi.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Wskazuje, czy przycisk pola kombi przetwarza komunikat.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parametry

*Kod iNotifyCode*<br/>
[w] Komunikat powiadomienia skojarzony z poleceniem.

### <a name="return-value"></a>Wartość zwracana

Czy przycisk pola kombi przetwarza wiadomość.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Wywoływane przez strukturę, gdy przycisk jest dodawany do **dostosowywania** okna dialogowego.

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Wywoływana przez strukturę, aby obliczyć rozmiar przycisku.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk pola kombi.

*rozmiarDefault*<br/>
[w] Domyślny rozmiar przycisku pola kombi.

*Bhorz*<br/>
[w] Stan dokującej nadrzędnego paska narzędzi. PRAWDA, gdy pasek narzędzi jest zadokowany poziomo i FAŁSZ, gdy pasek narzędzi jest zadokowany w pionie.

### <a name="return-value"></a>Wartość zwracana

Struktura `SIZE` zawierająca wymiary przycisku pola kombi w pikselach.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Wywoływana przez strukturę, gdy przycisk pola kombi jest wstawiany do nowego paska narzędzi.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do nowego nadrzędnego paska narzędzi.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick

Wywoływane przez strukturę, gdy użytkownik kliknie przycisk pola kombi.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parametry

*Pwnd*<br/>
[w] Wskaźnik do okna nadrzędnego przycisku pola kombi.

*bDelay (własówce)*<br/>
[w] Zarezerwowane do użycia w klasie pochodnej.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda obsługuje zdarzenie; w przeciwnym razie FALSE.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Wywoływane przez strukturę, gdy użytkownik zmienia kolor nadrzędnego paska narzędzi, aby ustawić kolor przycisku pola kombi.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk pola kombi.

*nCtlColor ( nCtlColor )*<br/>
[w] Nieużywane.

### <a name="return-value"></a>Wartość zwracana

Dojrzyj do pędzla, który służy do malowania tła przycisku pola kombi.

### <a name="remarks"></a>Uwagi

Ta metoda ustawia również kolor tekstu przycisku pola kombi.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw

Wywoływane przez strukturę, aby narysować przycisk pola kombi przy użyciu określonych stylów i opcji.

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

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku.

*pImages (Zdjęcia)*<br/>
[w] Kolekcja obrazów skojarzonych z przyciskiem.

*Bhorz*<br/>
[w] Stan dokującej nadrzędnego paska narzędzi. PRAWDA, gdy pasek narzędzi jest zadokowany poziomo i FAŁSZ, gdy pasek narzędzi jest zadokowany w pionie.

*b Tryb dokuczowania*<br/>
[w] Czy aplikacja jest w trybie dostosowywania.

*bWyświetlenie*<br/>
[w] Czy narysować przycisk pola kombi podświetlony.

*bDrawBorder*<br/>
[w] Czy narysować przycisk pola kombi obramowaniem.

*bGrayDisabledButtons*<br/>
[w] PRAWDA, aby narysować zacieniowane wyłączone przyciski; FALSE, aby użyć kolekcji obrazów wyłączonych.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Wywoływane przez strukturę, aby narysować przycisk pola kombi w okienku **Polecenia** okna dialogowego **Dostosowywanie.**

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Kontekst urządzenia, który wyświetla przycisk pola kombi.

*Rect*<br/>
[w] Prostokąt ograniczający przycisku pola kombi.

*bWybrany*<br/>
[w] PRAWDA, jeśli zaznaczony jest przycisk pola kombi; w przeciwnym razie FALSE.

### <a name="return-value"></a>Wartość zwracana

Szerokość przycisku pola kombi w pikselach.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsZmienił

Wywoływane przez strukturę, aby ustawić czcionkę przycisku pola kombi po zmianie czcionki aplikacji.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

Wywoływane przez strukturę, aby zmienić lokalizację przycisku pola kombi, gdy nadrzędny pasek narzędzi zostanie przeniesiony.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

Wywoływane przez strukturę, gdy przycisk pola kombi jest ukryty lub wyświetlany.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parametry

*bPokaż*<br/>
[w] Czy chcesz ukryć lub wyświetlić przycisk pola kombi.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize

Wywoływane przez strukturę, aby zmienić rozmiar przycisku pola kombi, gdy nadrzędny pasek narzędzi zmienia rozmiar.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parametry

*rozmiar iSize*<br/>
[w] Nowa szerokość przycisku pola kombi.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

Wywoływana przez strukturę, gdy użytkownik zmienia etykietkę narzędzia dla przycisku pola kombi.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parametry

*pWndRodziciela*<br/>
[w] Wskaźnik do okna nadrzędnego dla przycisku pola kombi.

*iButtonIndex*<br/>
[w] Identyfikator przycisku pola kombi.

*wndToolTip*<br/>
[w] Etykietka narzędzia, aby skojarzyć z przyciskiem pola kombi.

*Str*<br/>
[w] Tekst etykietki narzędzia.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda obsługuje zdarzenie; w przeciwnym razie FALSE.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Usuwa wszystkie elementy z listy i edytuj pola.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Uwagi

Usuwa wszystkie elementy z pola listy i edytuj kontrolkę pola kombi.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

Wybiera element w polu listy.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

*bNotuj*<br/>
[w] PRAWDA, aby powiadomić przycisk pola kombi o wyborze; w przeciwnym razie FALSE.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem w polu listy.

*lpszText (tekst)*<br/>
[w] Tekst elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

Wybiera element w polu listy przycisku pola kombi o określonym identyfikatorze polecenia.

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

*Uicmd*<br/>
[w] Identyfikator polecenia przycisku pola kombi zawierającego pole listy.

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy. Wartość -1 usuwa bieżące zaznaczenie w polu listy i czyści pole edycji.

*dwData (dane)*<br/>
[w] Dane elementu w polu listy.

*lpszText (tekst)*<br/>
[w] Tekst elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize

Odczytuje ten obiekt z archiwum lub zapisuje go w archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
[w, na zewnątrz] Obiekt `CArchive` do serializacji.

### <a name="remarks"></a>Uwagi

Ustawienia w `CArchive` obiekcie określają, czy ta metoda odczytuje lub zapisuje w archiwum.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Wypełnia określony `CAccessibilityData` obiekt przy użyciu danych ułatwień dostępu z przycisku pola kombi.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parametry

*pRoczysz*<br/>
[w] Okno nadrzędne przycisku pola kombi.

*Danych*<br/>
[na zewnątrz] Obiekt, `CAccessibilityData` który odbiera dane ułatwień dostępu z przycisku pola kombi.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Ustawia pozycję pionową przycisków pola kombi w aplikacji.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parametry

*bCenterVert (Werwercyjna)*<br/>
[w] PRAWDA, aby wyśrodkować przycisk pola kombi na pasku narzędzi; FAŁSZ, aby wyrównać przycisk pola kombi do górnej części paska narzędzi.

### <a name="remarks"></a>Uwagi

Domyślnie przyciski pola kombi są wyrównane do góry.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Ustawia identyfikator zasobu menu skrótów dla przycisku pola kombi.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiResID*<br/>
[w] Identyfikator zasobu menu skrótów.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Ustawia wysokość pola listy po jego upuszczeniu.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nFeksja*<br/>
[w] Wysokość w pikselach pola listy.

### <a name="remarks"></a>Uwagi

Domyślna wysokość to 150 pikseli.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Ustawia wygląd płaskiego stylu przycisków pola kombi w aplikacji.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parametry

*bFlat (ur.*<br/>
[w] PRAWDA dla wyglądu w stylu płaskim; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Domyślnym stylem płaskim dla przycisków pola kombi jest FAŁSZ.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle

Ustawia określony styl przycisku pola kombi i ponownie rysuje formant, jeśli nie jest wyłączony.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*styl nStyle*<br/>
[w] Kombinacja bitowa (OR) stylów paska narzędzi.

### <a name="remarks"></a>Uwagi

Aby uzyskać listę stylów przycisków paska narzędzi, zobacz [Style sterowania paska narzędzi](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Ustawia tekst w polu edycji przycisku pola kombi.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[w] Wskaźnik do ciągu zawierającego tekst pola edycji.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
