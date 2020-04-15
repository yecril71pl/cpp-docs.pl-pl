---
title: Klasa CMFCRibbonComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375226"
---
# <a name="cmfcribboncombobox-class"></a>Klasa CMFCRibbonComboBox

Klasa `CMFCRibbonComboBox` implementuje formant pola kombi, który można dodać do paska wstążki, panelu wstążki lub menu podręcznego wstążki.

## <a name="syntax"></a>Składnia

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Konstruuje OBIEKT CMFCRibbonComboBox.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|Dołącza unikatowy element do pola listy.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Usuwa określony element z pola listy.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Określa, czy pole listy może zmieniać rozmiar po jego spadku.|
|[CMFCRibbonComboBox::ZnajdźItem](#finditem)|Zwraca indeks pierwszego elementu w polu listy, który pasuje do określonego ciągu.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Zwraca liczbę elementów w polu listy.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie zaznaczonego elementu w polu listy.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Pobiera wysokość pola listy, gdy pole listy jest upuszczony w dół.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Zwraca rozmiar pola kombi wyświetlany w trybie pośrednim.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Zwraca ciąg skojarzony z elementem przy określonym indeksie w polu listy.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Zwraca dane skojarzone z elementem przy określonym indeksie w polu listy.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Wskazuje, czy formant zawiera pole edycji.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Wskazuje, czy można zwymiarować pole listy.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Wywoływane przez strukturę, gdy użytkownik wybiera element w polu listy.|
|[CMFCRibbonComboBox::UsuńWszystkie](#removeallitems)|Usuwa wszystkie elementy z pola listy i czyści pole edycji.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Wybiera element w polu listy.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy po jego upuszczeniu.|

## <a name="remarks"></a>Uwagi

Pole kombi wstążki składa się z pola listy połączonego z etykietą statyczną lub etykietą, które mogą być edytowane przez użytkownika. Podczas tworzenia pola kombi wstążki należy określić typ, który ma zostać utworzony.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonComboBox` skonstruować obiekt klasy, dodać element do pola kombi, zaznacz element w polu kombi i dodać pole kombi do panelu.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[Cmfcribbonedit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncombobox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::AddItem

Dołącza unikatowy element do pola listy.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
[w] Ciąg elementu do dodania.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem do dodania.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera dołączonego towaru.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox

Konstruuje `CMFCRibbonComboBox` obiekt.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[w] Identyfikator pola kombi.

*bHasEditBox*<br/>
[w] PRAWDA, jeśli chcesz, aby pole edycji w formancie; FAŁSZ inaczej.

*nWidth (ww.*<br/>
[w] Szerokość pola kombi w pikselach; lub -1 dla domyślnej szerokości.

*lpszLabel (lpszLabel)*<br/>
[w] Etykieta wyświetlana pola kombi.

*nImage (Obraz)*<br/>
[w] Mały indeks obrazu pola kombi.

### <a name="remarks"></a>Uwagi

Domyślna szerokość to 108 pikseli.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem

Usuwa określony element z pola listy.

```cpp
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
[w] Ciąg elementu, który ma zostać usunięty. Jeśli istnieje wiele elementów z tym samym ciągiem, pierwszy element jest usuwany.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli określony element został usunięty; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize

Określa, czy pole listy może zmieniać rozmiar po jego spadku.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Parametry

*bWłaszą*<br/>
[w] PRAWDA, aby włączyć zmiany rozmiaru; FALSE, aby wyłączyć zmiany rozmiaru.

### <a name="remarks"></a>Uwagi

Gdy zmiana rozmiaru jest włączona, pole listy zmieni rozmiar, aby dopasować je do wyświetlanych elementów.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::ZnajdźItem

Zwraca indeks pierwszego elementu w polu listy, który pasuje do określonego ciągu.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
[w] Ciąg elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera towaru; lub -1, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount

Zwraca liczbę elementów w polu listy.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy lub 0, jeśli pole listy nie zawiera żadnych elementów.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel

Pobiera indeks aktualnie zaznaczonego elementu w polu listy.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Indeks od zera aktualnie zaznaczonego elementu w polu listy; lub -1, jeśli nie wybrano żadnego elementu.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight

Pobiera wysokość pola listy, gdy pole listy jest upuszczony w dół.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach pola listy.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize

Zwraca rozmiar pola kombi wyświetlany w trybie pośrednim.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia dla pola kombi.

### <a name="return-value"></a>Wartość zwracana

Rozmiar pola kombi.

### <a name="remarks"></a>Uwagi

Zwrócony rozmiar zależy od rozmiaru pola kombi, gdy wyświetla małe obrazy.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem

Zwraca ciąg skojarzony z elementem przy określonym indeksie w polu listy.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który jest skojarzony z elementem; w przeciwnym razie NULL, jeśli parametr indeksu jest nieprawidłowy lub jeśli parametr indeksu wynosi -1 i nie ma żadnego elementu wybranego w polu kombi.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData

Zwraca dane skojarzone z elementem przy określonym indeksie w polu listy.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem; lub 0, jeśli element nie istnieje lub jeśli parametr indeksu wynosi -1 i nie ma zaznaczonego elementu w polu listy.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox

Wskazuje, czy formant zawiera pole edycji.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli formant zawiera pole edycji; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList

Wskazuje, czy można zwymiarować pole listy.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli można zwymiarować pole listy; w przeciwnym razie FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Uwagi

Zmiana rozmiaru pola listy można włączyć przy użyciu [metody CMFCRibbonComboBox::EnableDropDownListResize.](#enabledropdownlistresize)

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem

Wywoływane przez strukturę, gdy użytkownik wybiera element w polu listy.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nJejsza*<br/>
[w] Indeks wybranego elementu.

### <a name="remarks"></a>Uwagi

Zastąd w tej metodzie należy zastążać, jeśli chcesz przetworzyć wybór danych wejściowych użytkownika.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::UsuńWszystkie

Usuwa wszystkie elementy z pola listy i czyści pole edycji.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem

Wybiera element w polu listy.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
[w] Indeks od zera elementu w polu listy.

*dwData (dane)*<br/>
[w] Dane skojarzone z elementem w polu listy.

*lpszText (tekst)*<br/>
[w] Ciąg elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight

Ustawia wysokość pola listy po jego upuszczeniu.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nFeksja*<br/>
[w] Wysokość w pikselach pola listy.

### <a name="remarks"></a>Uwagi

Domyślna wysokość to 150 pikseli.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)
