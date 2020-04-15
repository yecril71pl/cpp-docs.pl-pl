---
title: Klasa CMFCRibbonButtonsGroup
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: af5919ff2a72fc2aa1eeeb95fc93afbe9e743582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375285"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>Klasa CMFCRibbonButtonsGroup

Klasa `CMFCRibbonButtonsGroup` umożliwia organizowanie zestawu przycisków wstążki w grupę. Wszystkie przyciski w grupie są bezpośrednio przylegające do siebie poziomo i zamknięte w obramowania.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Konstruuje `CMFCRibbonButtonsGroup` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Dodaje przycisk do grupy.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Dodaje listę przycisków do grupy.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Zwraca wskaźnik do przycisku, który znajduje się w określonym indeksie.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Zwraca liczbę przycisków w grupie.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Zwraca rozmiar obrazu normalnych obrazów w grupie wstążki (zastępuje [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Zwraca regularny rozmiar elementu wstążki (zastępuje [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Informuje, `CMFCRibbonButtonsGroup` czy obiekt zawiera obrazy paska narzędzi.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Rysuje odpowiedni obraz dla określonego przycisku, w zależności od tego, czy przycisk jest normalny, podświetlony czy wyłączony.|
|[CMFCRibbonButtonsGroup::UsuńWszystki](#removeall)|Usuwa wszystkie przyciski `CMFCRibbonButtonsGroup` z obiektu.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Przypisuje obrazy do grupy.|
|[CMFCRibbonButtonsGroup::SetParent Kategoria](#setparentcategory)|Ustawia element `CMFCRibbonCategory` nadrzędny `CMFCRibbonButtonsGroup` obiektu i wszystkie przyciski w nim (zastępuje [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Uwagi

Grupa jest pochodną [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) i mogą być manipulowane jako pojedyncza jednostka. Grupę można umieścić w dowolnym menu panelu lub w menu podręcznym.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonButtonsGroup` używać różnych metod w klasie. W przykładzie pokazano, `CMFCRibbonButtonsGroup` jak skonstruować obiekt, przypisać obrazy do grupy przycisków wstążki i dodać przycisk do grupy przycisków wstążki. Ten fragment kodu jest częścią [próbki Klienta rysowania](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxribbonbuttonsgroup.h

## <a name="cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton

Dodaje przycisk do grupy.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pButton (przycisk)*<br/>
[w] Wskaźnik do przycisku, aby dodać.

## <a name="cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons

Dodaje listę przycisków do grupy.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parametry

*lstButtons (Przycisk)*<br/>
[w] Lista wskaźników do przycisków, które chcesz dodać.

## <a name="cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Konstruuje `CMFCRibbonButtonsGroup` obiekt.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parametry

*pButton (przycisk)*<br/>
[w] Określa przycisk, który ma być `CMFCRibbonButtonsGroup` dodawany do nowo utworzonego obiektu.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton

Zwraca wskaźnik do przycisku, który znajduje się w określonym indeksie.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parametry

*I*<br/>
[w] Indeks od zera przycisku do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przycisku, który znajduje się w określonym indeksie. NULL, jeśli określony indeks jest poza zakresem.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount

Zwraca liczbę przycisków w grupie.

```
int GetCount() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba przycisków w grupie.

## <a name="cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize

Pobiera rozmiar obrazu źródłowego `CMFCToolBarImages` chronionego `m_Images`elementu członkowskiego .

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar obrazu źródłowego obrazów paska narzędzi, jeśli `CSize` istnieją, lub zero, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize

Pobiera maksymalny możliwy rozmiar elementu grupy wstążki.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu urządzenia grupy wstążki.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages

Informuje, `CMFCRibbonButtonsGroup` czy obiekt zawiera obrazy paska narzędzi.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, `CMFCToolBarImages` `m_Images` jeśli chroniony element członkowski zawiera obrazy lub FALSE, jeśli nie.

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage

Rysuje odpowiedni obraz dla określonego przycisku, w zależności od tego, czy przycisk jest normalny, podświetlony czy wyłączony.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[w] Wskaźnik do kontekstu `CMFCRibbonButtonsGroup` urządzenia obiektu.

*rectImage*<br/>
[w] Prostokąt, w którym ma być rysowany obraz.

*pButton (przycisk)*<br/>
[w] Przycisk, dla którego ma być rysowany obraz.

*nImageIndex*<br/>
[w] Indeks obrazu do rysowania na przycisku (w jednej z trzech tablic obrazów dla przycisków normalnych, podświetlonych lub wyłączonych).

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::UsuńWszystki

Usuwa wszystkie przyciski `CMFCRibbonButtonsGroup` z obiektu.

```
void RemoveAll();
```

### <a name="remarks"></a>Uwagi

## <a name="cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages

Przypisuje obrazy do grupy przycisków wstążki.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parametry

*pImages (Zdjęcia)*<br/>
[w] Regularne obrazy.

*pHotImages (pHotImages)*<br/>
[w] Gorące obrazy.

*pDisabledImages (Nieobjawie się)*<br/>
[w] Wyłączone obrazy.

### <a name="remarks"></a>Uwagi

Zadzwoń `SetImages` przed dodaniem przycisków do grupy. Liczba obrazów musi być większa lub równa liczbie przycisków, które mają zostać dodane do grupy.

> [!NOTE]
> Obrazy nagrze, które są wyświetlane, gdy użytkownik najedzie kursorem na przycisk. Wyłączone obrazy to obrazy wyświetlane po wyłączeniu przycisku.

## <a name="cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParent Kategoria

Ustawia element `CMFCRibbonCategory` nadrzędny `CMFCRibbonButtonsGroup` obiektu i wszystkie przyciski w nim.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parametry

*p Kategoria*<br/>
[w] Wskaźnik do kategorii nadrzędnej do ustawionego (grupy z kartami w formanty wstążki są nazywane kategoriami).

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)
