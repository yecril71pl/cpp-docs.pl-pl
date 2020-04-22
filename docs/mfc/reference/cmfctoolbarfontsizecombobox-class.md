---
title: Klasa CMFCToolBarFontSizeComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::GetTwipSize
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::RebuildFontSizes
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontSizeComboBox::SetTwipSize
helpviewer_keywords:
- CMFCToolBarFontSizeComboBox [MFC], CMFCToolBarFontSizeComboBox
- CMFCToolBarFontSizeComboBox [MFC], GetTwipSize
- CMFCToolBarFontSizeComboBox [MFC], RebuildFontSizes
- CMFCToolBarFontSizeComboBox [MFC], SetTwipSize
ms.assetid: 72e0c44c-6a0e-4194-a71f-ab64e3afb9b5
ms.openlocfilehash: 6c90bb1ce464a90295e7edb933d87594444c3648
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745321"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>Klasa CMFCToolBarFontSizeComboBox

Przycisk paska narzędzi zawierający formant pola kombi, który umożliwia użytkownikowi wybranie rozmiaru czcionki.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Konstruuje `CMFCToolBarFontSizeComboBox` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Zwraca wybrany rozmiar czcionki w twips.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Wypełnia listę pól kombi wszystkimi obsługiwanymi rozmiarami czcionek dla określonej czcionki.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Ustawia rozmiar czcionki w twips.|

## <a name="remarks"></a>Uwagi

Można użyć `CMFCToolBarFontSizeComboBox` obiektu wraz z [CMFCToolBarFontComboBox class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) obiektu, aby umożliwić użytkownikowi zaznaczenie czcionki i rozmiaru czcionki.

Przycisk pola kombi o rozmiarze czcionki można dodać do paska narzędzi, podobnie jak przycisk pola kombi czcionki. Aby uzyskać więcej informacji, zobacz [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Gdy użytkownik wybierze nową czcionkę `CMFCToolBarFontComboBox` w obiekcie, można wypełnić pole kombi rozmiaru czcionki za pomocą obsługiwanych rozmiarów dla tej czcionki przy użyciu metody [CMFCToolBarFontSizeComboBox::RebuildFontSizes.](#rebuildfontsizes)

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCToolBarFontSizeComboBox` używać różnych `CMFCToolBarFontSizeComboBox` metod w klasie, aby skonfigurować obiekt. Przykład ilustruje, jak pobrać rozmiar czcionki w twips, z pola tekstowego, wypełnić pole kombi rozmiar czcionki ze wszystkimi prawidłowymi rozmiarami danej czcionki i określić rozmiar czcionki w twips. Ten fragment kodu jest częścią [przykładu word pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cmfctoolbarbutton](../../mfc/reference/cmfctoolbarbutton-class.md)

[Cmfctoolbarcomboboxbutton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontsizecomboboxcmfctoolbarfontsizecombobox"></a><a name="cmfctoolbarfontsizecombobox"></a>CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Konstruuje `CMFCToolBarFontSizeComboBox` obiekt.

```
CMFCToolBarFontSizeComboBox();
```

## <a name="cmfctoolbarfontsizecomboboxgettwipsize"></a><a name="gettwipsize"></a>CMFCToolBarFontSizeComboBox::GetTwipSize

Pobiera rozmiar czcionki w twips z pola tekstowego pola kombi o rozmiarze czcionki.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli zwracana wartość jest dodatnia, jest to rozmiar czcionki w twips. Jest to -1, jeśli pole tekstowe pola kombi jest puste. Jest -2, jeśli wystąpi błąd.

## <a name="cmfctoolbarfontsizecomboboxrebuildfontsizes"></a><a name="rebuildfontsizes"></a>CMFCToolBarFontSizeComboBox::RebuildFontSizes

Wypełnia pole kombi o rozmiarze czcionki wszystkimi prawidłowymi rozmiarami danej czcionki.

```cpp
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parametry

*strFontName (Nazwa strFontname)*<br/>
[w] Określa nazwę czcionki.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, jeśli chcesz zsynchronizować wybór między zaznaczeniem w polu kombi czcionki a polem kombi o rozmiarze czcionki, takim jak [klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

## <a name="cmfctoolbarfontsizecomboboxsettwipsize"></a><a name="settwipsize"></a>CMFCToolBarFontSizeComboBox::SetTwipSize

Zaokrągla określony rozmiar (w twips) do najbliższego rozmiaru w punktach, a następnie ustawia wybrany rozmiar w polu kombi na tę wartość.

```cpp
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize (rozmiar)*<br/>
[w] Określa rozmiar czcionki (w twips), który ma być ustawiony.

### <a name="remarks"></a>Uwagi

Poprzedni prawidłowy rozmiar czcionki można pobrać później, wywołując metodę [CMFCToolBarFontSizeComboBox::GetTwipSize.](#gettwipsize)

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Wskazówki: umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
