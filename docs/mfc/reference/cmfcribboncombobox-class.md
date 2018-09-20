---
title: Klasa CMFCRibbonComboBox | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2681d5f54211ac2097dcae410ba69743af4b4690
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446162"
---
# <a name="cmfcribboncombobox-class"></a>Klasa CMFCRibbonComboBox

`CMFCRibbonComboBox` Klasa implementuje formant pola kombi, które można dodać do paska wstążki, panelu Wstążki lub menu podręcznego wstążki.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Tworzy obiekt CMFCRibbonComboBox.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|Dołącza element unikatowe pola listy.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Usuwa określony element z listy rozwijanej.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Określa, czy pole listy można zmienić rozmiar, gdy jest ona rozwinięta.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Zwraca indeks pierwszego elementu w polu listy, która pasuje do określonego ciągu.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Zwraca liczbę elementów w polu listy.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Pobiera indeks aktualnie wybranego elementu w polu listy.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Pobiera wysokość pola listy, po upuszczeniu pole listy.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Zwraca rozmiar pola kombi wyświetlany w trybie pośrednich.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Zwraca ciąg skojarzony element z określonym indeksem, w polu listy.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Zwraca dane skojarzone z elementem z określonym indeksem, w polu listy.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Wskazuje, czy kontrolka zawiera pole edycji.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Wskazuje, czy można zmienić pola listy.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Wywoływane przez platformę, gdy użytkownik wybierze element na liście.|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Usuwa wszystkie elementy z listy rozwijanej i czyści pole edycji.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Wybiera element w polu listy.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Ustawia wysokość pola listy, gdy jest rozwijana.|

## <a name="remarks"></a>Uwagi

Pole kombi wstążki składa się z pola listy, w połączeniu ze statycznych etykietę lub etykiety, które mogą być edytowane przez użytkownika. Należy określić typy, które chcesz, aby podczas tworzenia usługi pola kombi wstążki.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonComboBox` klasy, Dodaj element do pola kombi, zaznacz element w polu kombi i dodać pole kombi do panelu.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribboncombobox.h

##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem

Dołącza element unikatowe pola listy.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parametry

*lpszItem*<br/>
[in] Ciąg element do dodania.

*dwData*<br/>
[in] Dane skojarzone z elementem do dodania.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks elementu dołączonych.

##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox

Konstruuje `CMFCRibbonComboBox` obiektu.

```
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

*nID*<br/>
[in] Identyfikator pola kombi.

*bHasEditBox*<br/>
[in] Wartość TRUE, jeśli chcesz, aby pole edycji w ramach kontroli. Wartość FALSE w przeciwnym razie.

*nWidth*<br/>
[in] Szerokość pola kombi w pikselach; lub wartość -1 dla domyślnej szerokości.

*lpszLabel*<br/>
[in] Wyświetl etykietę pola kombi.

*Nokreślono*<br/>
[in] Indeks mały obraz pola kombi.

### <a name="remarks"></a>Uwagi

Domyślna szerokość to 108 pikseli.

##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem

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
[in] Ciąg elementu do usunięcia. W przypadku wielu elementów przy użyciu tych samych parametrach pierwszy element zostanie usunięty.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli określony element został usunięty; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize

Określa, czy pole listy można zmienić rozmiar, gdy jest ona rozwinięta.

```
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Parametry

*bWłączenie*<br/>
[in] Wartość true, zmiany rozmiaru Włącz; Wartość FALSE, aby wyłączyć zmiany rozmiaru.

### <a name="remarks"></a>Uwagi

Po włączeniu rozmiaru pola listy ulegnie zmianie rozmiaru elementów, które są wyświetlane.

##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem

Zwraca indeks pierwszego elementu w polu listy, która pasuje do określonego ciągu.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
[in] Ciąg, który elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks elementu; lub -1, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount

Zwraca liczbę elementów w polu listy.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w polu listy lub 0, jeśli pole listy nie zawiera elementów.

### <a name="remarks"></a>Uwagi

##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel

Pobiera indeks aktualnie wybranego elementu w polu listy.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczony od zera Indeks aktualnie wybranego elementu w polu listy; lub -1, jeśli nie wybrano elementu.

##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight

Pobiera wysokość pola listy, po upuszczeniu pole listy.

```
int GetDropDownHeight();
```

### <a name="return-value"></a>Wartość zwracana

Wysokość w pikselach, pola listy.

### <a name="remarks"></a>Uwagi

##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize

Zwraca rozmiar pola kombi wyświetlany w trybie pośrednich.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*podstawowego kontrolera domeny*<br/>
[in] Wskaźnik do kontekstu urządzenia dla tego pola kombi.

### <a name="return-value"></a>Wartość zwracana

Rozmiar pola kombi.

### <a name="remarks"></a>Uwagi

Rozmiar zwrócony opiera się na rozmiaru pola kombi, gdy Wyświetla małe obrazy.

##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem

Zwraca ciąg skojarzony element z określonym indeksem, w polu listy.

```
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu, który jest skojarzony z elementem; w przeciwnym razie wartość NULL, jeśli parametr indeksu jest nieprawidłowy lub parametr indeksu jest wartość -1, jeśli nie ma żadnych elementów wybrane w polu kombi.

### <a name="remarks"></a>Uwagi

##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData

Zwraca dane skojarzone z elementem z określonym indeksem, w polu listy.

```
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Dane skojarzone z elementem; lub równa 0, jeśli element nie istnieje lub parametr indeksu jest wartość -1, jeśli nie ma żadnych wybranego elementu w polu listy.

##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox

Wskazuje, czy kontrolka zawiera pole edycji.

```
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli kontrolka zawiera pole edycji; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList

Wskazuje, czy można zmienić pola listy.

```
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pole listy można zmienić rozmiar; w przeciwnym razie wartość FALSE. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Uwagi

Można włączyć listy pola zmiany rozmiaru za pomocą [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) metody.

##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem

Wywoływane przez platformę, gdy użytkownik wybierze element na liście.

```
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Parametry

*nItem*<br/>
[in] Indeks zaznaczonego elementu.

### <a name="remarks"></a>Uwagi

Należy przesłonić tę metodę, aby przetworzyć wybór danych wejściowych użytkownika.

##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems

Usuwa wszystkie elementy z listy rozwijanej i czyści pole edycji.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Uwagi

##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem

Wybiera element w polu listy.

```
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[in] Liczony od zera indeks elementu w polu listy.

*dwData*<br/>
[in] Dane skojarzone z elementem w polu listy.

*lpszText*<br/>
[in] Ciąg, który elementu w polu listy.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight

Ustawia wysokość pola listy, gdy jest rozwijana.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parametry

*nHeight*<br/>
[in] Wysokość w pikselach, pola listy.

### <a name="remarks"></a>Uwagi

Domyślna wysokość jest 150 pikseli.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)
