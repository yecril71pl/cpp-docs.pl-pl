---
title: CMFCToolBarFontSizeComboBox Class
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
ms.openlocfilehash: 43832f6c9b02c43fbe4a05cbea3add8783150113
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767668"
---
# <a name="cmfctoolbarfontsizecombobox-class"></a>CMFCToolBarFontSizeComboBox Class

Przycisk paska narzędzi, który zawiera formant pola kombi, która umożliwia użytkownikowi wybranie rozmiar czcionki.

## <a name="syntax"></a>Składnia

```
class CMFCToolBarFontSizeComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox](#cmfctoolbarfontsizecombobox)|Konstruuje `CMFCToolBarFontSizeComboBox` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize)|Zwraca wartość w twipach wybrany rozmiar czcionki.|
|[CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes)|Wypełnia listy pola kombi wszystkie rozmiary czcionek obsługiwanych dla określonej czcionki.|
|[CMFCToolBarFontSizeComboBox::SetTwipSize](#settwipsize)|Ustawia rozmiar czcionki w twipach.|

## <a name="remarks"></a>Uwagi

Możesz użyć `CMFCToolBarFontSizeComboBox` obiektu wraz z [klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) obiekt, aby umożliwić użytkownikowi wybierz czcionkę i rozmiar czcionki.

Tak, jak dodać przycisk pole kombi czcionki, można dodać przycisk pola kombi rozmiar czcionki na pasku narzędzi. Aby uzyskać więcej informacji, zobacz [klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

Gdy użytkownik wybierze nowy czcionkę w `CMFCToolBarFontComboBox` obiektu, możesz wypełnić pole kombi rozmiaru czcionki obsługiwane rozmiary dla wybranej czcionki przy użyciu [CMFCToolBarFontSizeComboBox::RebuildFontSizes](#rebuildfontsizes) metody.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak korzystać z różnych metod w `CMFCToolBarFontSizeComboBox` klasa umożliwiająca skonfigurowanie `CMFCToolBarFontSizeComboBox` obiektu. W przykładzie pokazano, jak pobrać rozmiar czcionki w twipach, z pola tekstowego, wypełnienie pola kombi rozmiaru czcionki wszystkie prawidłowe rozmiary czcionek danego i określ rozmiar czcionki w twipach. Ten fragment kodu jest częścią [przykład konsola programu Word](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#8](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontsizecombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontSizeComboBox](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontsizecombobox"></a>  CMFCToolBarFontSizeComboBox::CMFCToolBarFontSizeComboBox

Konstruuje `CMFCToolBarFontSizeComboBox` obiektu.

```
CMFCToolBarFontSizeComboBox();
```

##  <a name="gettwipsize"></a>  CMFCToolBarFontSizeComboBox::GetTwipSize

Pobiera rozmiar czcionki w twipach, w polu tekstowym pola kombi rozmiar czcionki.

```
int GetTwipSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość zwracana jest dodatnia, jest rozmiar czcionki w twipach. To -1, jeśli w polu tekstowym pola kombi jest pusty. Jeśli wystąpi błąd, to -2.

##  <a name="rebuildfontsizes"></a>  CMFCToolBarFontSizeComboBox::RebuildFontSizes

Wszystkie prawidłowe rozmiary czcionek danego wypełnia pole kombi rozmiaru czcionki.

```
void RebuildFontSizes(const CString& strFontName);
```

### <a name="parameters"></a>Parametry

*strFontName*<br/>
[in] Określa nazwę czcionki.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby synchronizacja pomiędzy wybór w polu kombi czcionki i rozmiar czcionki kombi, takich jak [klasa CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md).

##  <a name="settwipsize"></a>  CMFCToolBarFontSizeComboBox::SetTwipSize

Zaokrągla liczbę określony rozmiar (w twipach) do najbliższej rozmiaru punktów, a następnie ustawia wybranym rozmiarze w polu kombi na tę wartość.

```
void SetTwipSize(int nSize);
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Określa rozmiar czcionki (w twipach), aby ustawić.

### <a name="remarks"></a>Uwagi

Pobrać poprzedniego rozmiaru poprawną czcionkę później przez wywołanie metody [CMFCToolBarFontSizeComboBox::GetTwipSize](#gettwipsize) metody.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Klasa CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Klasa CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Klasa CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Przewodnik: Umieszczanie formantów na paskach narzędzi](../../mfc/walkthrough-putting-controls-on-toolbars.md)
